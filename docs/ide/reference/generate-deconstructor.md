---
title: Action rapide Générer un constructeur
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2ca2d3a0c174fa4c7d0f66d3abc440b8c9aa93cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790315"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Générer un constructeur dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** Permet de générer immédiatement le stub de méthode pour un nouveau déconstructeur.

**Quand :** Vous souhaitez déconstruire votre type correctement et automatiquement.

**Pourquoi :** Vous pouvez taper manuellement un déconstructeur, mais cette fonctionnalité génère le stub pour vous avec les paramètres de sortie appropriés.

## <a name="generate-a-deconstructor"></a>Générer un déconstructeur

1. Déclarez un nouveau type en spécifiant les paramètres de sortie de votre choix. Cette déclaration provoque une erreur si aucune instance de déconstruction correspondante n’est trouvée.

   ![Erreur liée à un déconstructeur manquant](media/deconstruct.png)

2. Effectuez l’une des étapes suivantes :

   - **Clavier**
      - Placez le curseur dans votre déclaration, puis sélectionnez Ctrl+. pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Sélectionnez ![Tournevis](media/screwdriver.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

      ![Générer un déconstructeur (correctif de code)](media/deconstruct-codefix.png)

3. Sélectionnez **Générer la méthode 'MyInternalClass.Deconstruct'** pour générer le déconstructeur.

   ![Code de déconstructeur résultant](media/deconstruct-result.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des changements](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)