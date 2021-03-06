---
title: 'Procédure : Ouvrir un modèle depuis un fichier dans le code du programme'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 092af518cc6c6fb1d98025cda54a6a1d491940c9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445125"
---
# <a name="how-to-open-a-model-from-file-in-program-code"></a>Procédure : Ouvrir un modèle depuis un fichier dans le code du programme
Vous pouvez ouvrir les modèles DSL dans n’importe quelle application.

 À partir d’une extension Visual Studio, vous pouvez utiliser ModelBus à cet effet. ModelBus fournit un mécanisme standard pour faire référence à un modèle ou éléments dans un modèle et pour rechercher le modèle si elle a été déplacé. Pour plus d’informations, consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="target-framework"></a>Framework cible
 Définir le **framework cible** de votre projet d’application pour **.NET Framework 4**.

#### <a name="to-set-the-target-framework"></a>Pour définir le framework cible

1. Ouvrez le projet Visual Studio pour l’application dans laquelle vous souhaitez lire un modèle DSL.

2. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis cliquez sur **propriétés**.

3. Dans la fenêtre de propriétés de projet, sur le **Application** onglet, définissez la **framework cible** champ **.NET Framework 4**.

> [!NOTE]
> Vous devrez peut-être effectuer cette opération même si vous avez sélectionné **.NET Framework 4** dans la boîte de dialogue de création de projet. Le framework cible ne doit pas être **.NET Framework 4 Client Profile**.

## <a name="references"></a>Références
 Vous devez ajouter ces références à votre projet d’application Visual Studio :

- `Microsoft.VisualStudio.Modeling.Sdk.11.0`

    - Si vous ne voyez pas cette opération sous le **.NET** onglet dans le **ajouter des références** boîte de dialogue, cliquez sur le **Parcourir** onglet et accédez à `%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies\`.

- Votre assembly DSL, vous trouverez sous le dossier bin de votre projet DSL. Son nom est généralement sous la forme : *Votresociété*. *VotreProjet*`.Dsl.dll`.

## <a name="important-classes-in-the-dsl"></a>Classes importantes dans la solution DSL
 Avant de pouvoir écrire le code qui lit votre DSL, vous devez savoir les noms de certaines des classes générées par votre DSL. Dans votre solution DSL, ouvrez le **Dsl** de projet, puis examinez le **GeneratedCode** dossier. Vous pouvez également, double-cliquez sur l’assembly DSL dans votre projet **références**et ouvrez l’espace de noms DSL dans **Explorateur d’objets**.

 Ce sont les classes que vous devez identifier :

- *YourDslRootClass* -il s’agit du nom de la classe de racine dans votre `DslDefinition.dsl`.

- *Nom_de_votre_solution_dsl* `SerializationHelper` -cette classe est définie dans `SerializationHelper.cs` dans votre projet DSL.

- *Nom_de_votre_solution_dsl* `DomainModel` -cette classe est définie dans `DomainModel.cs` dans votre projet DSL.

## <a name="reading-from-a-file"></a>Lecture à partir d’un fichier
 L’exemple suivant est conçu pour lire un DSL dans lequel les classes importantes sont les suivantes :

- FamilyTreeModel

- FamilyTreeSerializationHelper

- FamilyTreeDomainModel

  La classe de domaine dans cette solution DSL est la personne.

```csharp
using System;
using Microsoft.VisualStudio.Modeling;
using Company.FamilyTree; // Your DSL namespace

namespace StandaloneReadDslConsole
{ class Program
  { static void Main(string[] args)
    {
      // The path of a DSL model file:
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";
      // Set up the Store to read your type of model:
      Store store = new Store(
        typeof(Company.FamilyTree.FamilyTreeDomainModel));
      // The Model type generated by the DSL:
      FamilyTreeModel familyTree;
      // All Store changes must be in a Transaction:
      using (Transaction t =
        store.TransactionManager.BeginTransaction("Load model"))
      {
        familyTree =
           FamilyTreeSerializationHelper.Instance.
              LoadModel(store, dslModel, null, null, null);
        t.Commit(); // Don't forget this!
      }
      // Now we can read the model:
      foreach (Person p in familyTree.People)
      {
        Console.WriteLine(p.Name);
        foreach (Person child in p.Children)
        {
          Console.WriteLine("    " + child.Name);
        }
} } } }
```

## <a name="saving-to-a-file"></a>Enregistrement dans un fichier
 Les configurations suivantes au code précédent apporte une modification au modèle, puis l’enregistre dans un fichier.

```csharp
using (Transaction t =
  store.TransactionManager.BeginTransaction("update model"))
{
  // Create a new model element:
  Person p = new Person(store);
  // Set its embedding relationship:
  p.FamilyTreeModel = familyTree;
  // - same as: familyTree.People.Add(p);
  // Set its properties:
  p.Name = "Edward VI";
  t.Commit(); // Don't forget this!
}
// Save the model:
try
{
  SerializationResult result = new SerializationResult();
  FamilyTreeSerializationHelper.Instance
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");
  // Report any error:
  if (result.Failed)
  {
    foreach (SerializationMessage message in result)
    {
      Console.WriteLine(message);
    }
  }
}
catch (System.IO.IOException ex)
{ ... }
```