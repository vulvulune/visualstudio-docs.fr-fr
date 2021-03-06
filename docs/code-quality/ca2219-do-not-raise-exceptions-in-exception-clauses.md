---
title: "CA2219 : Ne pas lever d'exceptions dans les clauses d'exception"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a644cf3dc934676a14f1c5c59a6582fcd45ae7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806652"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219 : Ne pas lever d'exceptions dans les clauses d'exception

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture, rupture|

## <a name="cause"></a>Cause
 Une exception est levée à partir d’un `finally`, filtre ou une clause fault.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’une exception est déclenchée dans une clause d’exception, elle augmente considérablement la difficulté du débogage.

 Lorsqu’une exception est levée dans un `finally` ou une clause fault, la nouvelle exception masque l’exception active, le cas échéant. Cela rend l’erreur d’origine difficile à détecter et à déboguer.

 Lorsqu’une exception est déclenchée dans une clause de filtre, le runtime en mode silencieux intercepte l’exception et provoque le filtre doit évaluer sur false. Il n’existe aucun moyen de faire la différence entre l’évaluation de filtre false et une exception soit levée à partir d’un filtre. Cela rend difficiles à détecter et à déboguer les erreurs dans la logique du filtre.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation de cette règle, ne levez pas explicitement d’exception à partir d’un `finally`, filtre ou une clause fault.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas d’avertissement pour cette règle. Il n’existe aucun scénario dans lequel une exception levée dans une clause d’exception confère un avantage pour l’exécution de code.

## <a name="related-rules"></a>Règles associées
 [CA1065 : Ne pas lever d’exceptions dans des emplacements inattendus](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Voir aussi
 [Avertissements liés à la conception](../code-quality/design-warnings.md)