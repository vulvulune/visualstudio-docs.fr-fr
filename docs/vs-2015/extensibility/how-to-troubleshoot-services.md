---
title: 'Comment : résoudre les problèmes des Services | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0cbad73fe5be46c7371356a0a3746b7e58315ef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495326"
---
# <a name="how-to-troubleshoot-services"></a>Comment : résoudre les problèmes des Services
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : résoudre les problèmes des Services](https://docs.microsoft.com/visualstudio/extensibility/how-to-troubleshoot-services).  
  
Il existe plusieurs problèmes courants qui peuvent se produire lorsque vous essayez d’obtenir un service :  
  
-   Le service n’est pas inscrit avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Le service est demandé par type d’interface et non par type de service.  
  
-   Le VSPackage demandant le service n’a pas été placé.  
  
-   Le fournisseur de service incorrect est utilisé.  
  
 Si le service demandé n’aboutit pas, l’appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> retourne la valeur null. Vous devez toujours vérifier les valeurs null après la demande d’un service :  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Pour résoudre les problèmes d’un service  
  
1.  Examinez le Registre système pour voir si le service a été correctement inscrit. Pour plus d’informations, consultez [enregistrement des Services](../misc/registering-services.md).  
  
     Le fragment de fichier .reg suivant montre comment le service de SVsTextManager peut être inscrit :  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], telles que 12.0 ou 14.0, la clé {F5E7E71D-1401-11d1-883B-0000F87579D2} est l’identificateur de service (SID) du service, SVsTextManager et la {valeur par défaut F5E7E720-1401-11D1-883B-0000F87579D2} est le GUID du package le VSPackage, qui fournit le service de gestionnaire de texte.  
  
2.  Lorsque vous appelez la méthode GetService, utilisez le type de service et pas le type d’interface. Lors de la demande d’un service à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrait le GUID du type. Un service sera introuvable si les conditions suivantes sont réunies :  
  
    1.  Un type d’interface est passé à la méthode GetService au lieu du type de service.  
  
    2.  Aucun GUID n’est explicitement affectée à l’interface. Par conséquent, le système crée un GUID par défaut pour un objet en fonction des besoins.  
  
3.  Assurez-vous que le VSPackage demandant le service a été placé. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sites d’un VSPackage après la construction et avant d’appeler <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Si vous avez le code dans un constructeur de VSPackage qui a besoin d’un service, déplacez-le vers la méthode Initialize.  
  
4.  N’oubliez pas que vous utilisez le fournisseur de service approprié.  
  
     Pas tous les fournisseurs de services sont similaires. Le fournisseur de services qui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] transmet à une fenêtre outil diffère de celui qu’il transmet à un VSPackage. Le fournisseur de services de fenêtre outil connaît <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, mais ne connaît ne pas <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour accéder à un fournisseur de services de package Visual Studio à partir de dans une fenêtre outil.  
  
     Si une fenêtre outil héberge un contrôle utilisateur ou tout autre conteneur de contrôle, le conteneur doit se trouver par le modèle de composant de Windows et qu’il n’aura pas accès à tout [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] services. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour obtenir un fournisseur de services de VSPackage à partir d’un conteneur de contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des Services disponibles](../extensibility/internals/list-of-available-services.md)   
 [À l’aide et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)
