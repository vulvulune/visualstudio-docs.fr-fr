---
title: 'Procédure : Étendre le concepteur Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c02dbf550ca1621a17d2b674a522e1e4f4bcc1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546939"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Procédure : Étendre le Concepteur Domain-Specific Language
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer des extensions au concepteur qui vous permet de modifier des définitions DSL. Types d’extensions que vous pouvez apporter comprennent l’ajout de commandes de menu, ajout de gestionnaires pour faire glisser et double-cliquez sur les mouvements et règles qui sont déclenchées quand modifier des types particuliers de valeurs ou des relations. Les extensions peuvent empaquetées en tant qu’une Extension d’intégration Visual Studio (VSIX) et distribuées aux autres utilisateurs.  
  
 Pour des exemples de code et plus d’informations sur cette fonctionnalité, consultez Visual Studio [site Web de visualisation et modélisation de kit de développement logiciel (SDK) VISUALIZATION](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
## <a name="setting-up-the-solution"></a>Configuration de la Solution  
 Configurer un projet qui contient le code de votre extension et un projet VSIX qui exporte le projet. Votre solution peut contenir d’autres projets qui sont incorporés dans la même extension VSIX.  
  
#### <a name="to-create-a-dsl-designer-extension-solution"></a>Pour créer une Solution d’Extension concepteur DSL  
  
1. Créer un nouveau projet à l’aide du modèle de projet bibliothèque de classes. Dans le **nouveau projet** boîte de dialogue, cliquez sur **Visual C#** et, dans la fenêtre du milieu, cliquez sur **bibliothèque de classes**.  
  
     Ce projet contiendra le code de vos extensions.  
  
2. Créer un nouveau projet à l’aide du modèle de projet VSIX. Dans le **nouveau projet** boîte de dialogue, développez **Visual C#**, cliquez sur **extensibilité**et puis dans la fenêtre du milieu, sélectionnez **projet VSIX**.  
  
     Sélectionnez **ajouter à la Solution**.  
  
     Source.extension.vsixmanifest s’ouvre dans l’éditeur de manifeste VSIX.  
  
3. Au-dessus du champ de contenu, cliquez sur **ajouter du contenu**.  
  
4. Dans le **ajouter du contenu** boîte de dialogue, définissez **sélectionner un Type de contenu** à **composant MEF**et définissez **projet** à votre projet de bibliothèque de classes.  
  
5. Cliquez sur **sélectionner des éditions** et assurez-vous que l’option **Visual Studio Enterprise** est activée.  
  
6. Assurez-vous que le projet VSIX est le projet de démarrage de la solution.  
  
7. Dans le projet de bibliothèque de classes, ajoutez des références aux assemblys suivants :  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## <a name="testing-and-deployment"></a>Tests et déploiement  
 Pour tester les extensions dans cette rubrique, générer et exécuter la solution. Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] s’ouvre. Dans cette instance, ouvrez une solution DSL. Modifier le diagramme DslDefinition. Le comportement d’extension peut être consulté.  
  
 Pour déployer les extensions vers les principaux [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]et à d’autres ordinateurs, procédez comme suit :  
  
1. Rechercher le fichier d’installation de VSIX dans votre projet VSIX dans emplacement\\*\*\\\*.vsix  
  
2. Copiez ce fichier à l’ordinateur cible et dans l’Explorateur Windows (ou Explorateur de fichiers), double-cliquez dessus.  
  
    Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Gestionnaire d’extensions s’ouvre pour vérifier que l’extension a été installée.  
  
   Pour désinstaller l’extension, procédez comme suit :  
  
3. dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dans le **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
4. Sélectionnez l’extension et supprimez-le.  
  
## <a name="adding-a-shortcut-menu-command"></a>Ajout d’une commande de Menu contextuel  
 Pour afficher une commande de menu contextuel sur l’aire du concepteur DSL ou dans la fenêtre de l’Explorateur DSL, écrire une classe qui ressemble à ce qui suit.  
  
 La classe doit implémenter `ICommandExtension` et doit avoir l’attribut `DslDefinitionModelCommandExtension`.  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## <a name="handling-mouse-gestures"></a>Gestion des mouvements de la souris  
 Le code est similaire au code de la commande de menu.  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## <a name="responding-to-value-changes"></a>Répondre aux modifications de valeur  
 Ce gestionnaire a besoin d’un modèle de domaine fonctionne correctement. Nous fournissons un modèle de domaine simple.  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 Le code suivant implémente un modèle simple. Créer un nouveau GUID pour remplacer l’espace réservé.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```
