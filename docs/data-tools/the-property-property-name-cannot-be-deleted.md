---
title: Impossible de supprimer la propriété
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c03ba87a7ae7f2321550179ae6354eb473c81465
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460572"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Impossible de supprimer la propriété \<nom de la propriété>

La propriété \<nom de la propriété> ne peut pas être supprimée parce qu’elle est définie en tant que **Propriété de discriminateur** pour l’héritage entre \<nom de la classe> et \<nom de la classe>

La propriété sélectionnée est définie comme **Propriété de discriminateur** pour l’héritage entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à la configuration d'héritage entre des classes de données.

Affectez à **Propriété de discriminateur** une propriété différente de la classe de données pour permettre la suppression de la propriété voulue.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le **Concepteur O/R**, sélectionnez la ligne d’héritage qui connecte les classes de données indiquées dans le message d’erreur.

2. Affectez à **Propriété de discriminateur** une propriété différente.

3. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)