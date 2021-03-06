---
title: Utiliser un corps d’expression ou un corps de bloc pour les expressions lambda
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1f055925a4da916bf88da802e7a4991b0362b057
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789426"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Utiliser un corps d’expression ou un corps de bloc pour les expressions lambda

Cette refactorisation s’applique à :

- C#

**Quoi :** Permet de refactoriser une expression lambda afin d’utiliser un corps d’expression ou un corps de bloc.

**Quand :** Vous souhaitez que vos expressions lambda utilisent un corps d’expression ou un corps de bloc. 

**Pourquoi :** Vous pouvez refactoriser des expressions lambda pour améliorer la lisibilité selon les préférences de l’utilisateur.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Corps d’expression ou corps de bloc pour les expressions lambda (refactorisation)

1. Placez votre curseur à droite d’un opérateur lambda.
2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

  ![Utiliser un corps d’expression/de bloc pour les expressions lambda](media/block-body-lambda.png)

3. Sélectionnez **Utiliser un corps de bloc pour les expressions lambda** ou **Utiliser un corps d’expression pour les expressions lambda**.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)