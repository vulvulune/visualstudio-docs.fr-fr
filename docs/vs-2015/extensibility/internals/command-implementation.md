---
title: Implémentation de commandes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067831"
---
# <a name="command-implementation"></a>Implémentation de commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour implémenter une commande dans un VSPackage, vous devez effectuer les tâches suivantes :  
  
1. Dans le fichier .vsct, configurer un groupe de commandes, puis ajoutez la commande à celui-ci. Pour plus d’informations, consultez [Visual Studio Command Table (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Inscrire la commande avec Visual Studio.  
  
3. Implémenter la commande.  
  
   Les sections suivantes expliquent comment inscrire et implémenter des commandes.  
  
## <a name="registering-commands-with-visual-studio"></a>L’enregistrement de commandes avec Visual Studio  
 Si votre commande doit apparaître dans un menu, vous devez ajouter le <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> à votre VSPackage et les utiliser en tant que valeur le nom du menu ou son ID de ressource.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 En outre, vous devez inscrire la commande avec le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Vous pouvez obtenir ce service à l’aide de la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode si votre VSPackage est dérivée de <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implémentation de commandes  
 Il existe plusieurs manières d’implémenter des commandes. Si vous souhaitez une commande de menu statique, qui est une commande qui s’affiche toujours la même façon et dans le même menu, créer la commande à l’aide de <xref:System.ComponentModel.Design.MenuCommand> comme indiqué dans les exemples dans la section précédente. Pour créer une commande statique, vous devez fournir un gestionnaire d’événements qui est chargé d’exécuter la commande. Étant donné que la commande est toujours activée et visible, il est inutile de fournir son état à Visual Studio. Si vous souhaitez modifier l’état d’une commande selon certaines conditions, vous pouvez créer la commande comme une instance de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe et, dans son constructeur, fournissez un gestionnaire d’événements pour exécuter la commande et un gestionnaire d’état de la requête pour notifier Visual Studio lorsque l’état de la commande change. Vous pouvez également implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comme partie d’une classe de commande ou, vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si vous fournissez une commande en tant que partie d’un projet. Les deux interfaces et la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe tous les avoir des méthodes de notification de Visual Studio d’un changement de l’état d’une commande et d’autres méthodes qui fournissent l’exécution de la commande.  
  
 Lorsqu’une commande est ajoutée au service de commande, il est une chaîne de commandes. Lorsque vous implémentez les méthodes de notification et l’exécution de statut de la commande, veillez à fournir uniquement cette commande particulière et pour transmettre tous les autres cas, une session sur les autres commandes dans la chaîne. Si vous ne parvenez pas à passer la commande (généralement en retournant <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio peut cesser de fonctionner correctement.  
  
## <a name="query-status-methods"></a>Méthodes d’état de requête  
 Si vous implémentez soit le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> (méthode), recherchez le GUID de la commande jeu auquel appartient la commande et l’ID de la commande. Respectez les règles ci-dessous.  
  
- Si le GUID n’est pas reconnu, votre implémentation de soit la méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Si votre implémentation de deux méthodes reconnaît le GUID mais n’a pas réellement implémenté la commande, la méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Si votre implémentation de deux méthodes reconnaît le GUID et la commande, la méthode doit définir le champ Indicateurs de commande de chaque commande (dans le `prgCmds` paramètre) en utilisant les indicateurs suivants :  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si la commande est prise en charge.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si la commande ne doit pas être visible.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si la commande est activée et qu’il semble avoir été archivé.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si la commande est activée.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si la commande doit être masquée s’il apparaît dans un menu contextuel.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si la commande est un contrôleur de menu et n’est pas activée, mais sa liste déroulante n’est pas vide et qu’il est toujours disponible. (Cet indicateur est rarement utilisé.)  
  
- Si la commande a été définie dans le fichier .vsct avec le `TextChanges` indicateur, définissez les paramètres suivants :  
  
  - Définir le `rgwz` élément de la `pCmdText` paramètre vers le nouveau texte de la commande.  
  
  - Définir le `cwActual` élément de la `pCmdText` paramètre à la taille de la chaîne de commande.  
  
  Également vous assurer que le contexte actuel n’est pas une fonction d’automatisation, sauf si votre commande est conçu spécifiquement pour gérer les fonctions d’automatisation.  
  
  Pour indiquer que vous prenez en charge une commande particulière, retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Pour toutes les autres commandes, retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
  Dans l’exemple suivant, la méthode de l’état de la requête tout d’abord permet de s’assurer que le contexte n’est pas une fonction d’automation, puis recherche le bon GUID du jeu de commandes et l’ID de commande. La commande elle-même est définie sur activé et la prise en charge. Aucune autre commande n’est pris en charge.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Méthodes d’exécution  
 Implémentation de la méthode execute est similaire à l’implémentation de la méthode de l’état de la requête. Tout d’abord, assurez-vous que le contexte n’est pas une fonction d’automatisation. Ensuite tester le GUID et ID de commande. Si le GUID ou ID de commande n’est pas reconnu, retournez <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Pour gérer la commande, exécuter et retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> si l’exécution réussit. Votre commande est responsable de la détection d’erreur et de notification ; Par conséquent, retourner un code d’erreur si l’exécution échoue. L’exemple suivant montre comment la méthode d’exécution doit être implémentée.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
