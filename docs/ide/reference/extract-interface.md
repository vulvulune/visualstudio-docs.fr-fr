---
title: Extraire une interface (refactorisation)
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 261ddf457ad117812be9971b630c2fcd3b75b550
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62791234"
---
# <a name="extract-an-interface-refactoring"></a>Extraire une interface (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Permet de créer une interface en utilisant les membres existants d’une classe, d’un struct ou d’une interface.

**Quand :** Vous avez des membres dans une classe, un struct ou une interface qui peuvent être hérités par d’autres classes, structs ou interfaces.

**Pourquoi :** Les interfaces sont d’excellentes constructions pour les conceptions orientées objet. Imaginez des classes représentant différents animaux (chien, chat, oiseau) pouvant être associées à des méthodes courantes, par exemple Manger, Boire et Dormir. Une interface comme IAnimal permettrait aux éléments Chien, Chat et Oiseai d’avoir la même « signature » pour ces méthodes.

## <a name="extract-an-interface-refactoring"></a>Extraire une interface (refactorisation)

1. Placez votre curseur dans le nom de la classe.

   - C# :

       ![Code mis en surbrillance (C#)](media/extractinterface-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/extractinterface-highlight-vb.png)

2. Effectuez ensuite l’une des actions suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+I**. (Le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Extraire l’interface**.
      - Cliquez avec le bouton droit sur le nom de la classe et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.

3. Dans la boîte de dialogue **Extraire l’interface** qui s’affiche, entrez les informations demandées :

   ![Extraire l'interface](media/extractinterface-dialog-same-file.png)

   | Champ | Description |
   | - | - |
   | **Nouveau nom d’interface** | Nom de l'interface à créer. Ce nom a par défaut la valeur I*ClassName*, où *ClassName* correspond au nom de la classe que vous avez sélectionné ci-dessus. |
   | **Nouveau nom de fichier** | Nom du fichier généré qui contiendra l’interface. Comme pour le nom de l’interface, ce nom a par défaut la valeur I*ClassName*, où *ClassName* correspond au nom de la classe que vous avez sélectionné ci-dessus. Vous pouvez également sélectionner l’option **Ajouter au fichier actuel**. |
   | **Sélectionner les membres publics pour former l'interface** | Les éléments à extraire dans l’interface. Vous pouvez sélectionner autant d’éléments que vous le souhaitez. |

4. Cliquez sur **OK**.

   L’interface est créée dans le fichier portant le nom spécifié. De plus, la classe que vous avez sélectionnée implémente cette interface.

   - C# :

      ![Classe résultante - C#](media/extractinterface-class-cs.png)

      ![Interface résultante - C#](media/extractinterface-interface-cs.png)

   - Visual Basic :

      ![Classe résultante - Visual Basic](media/extractinterface-class-vb.png)

      ![Interface résultante - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
