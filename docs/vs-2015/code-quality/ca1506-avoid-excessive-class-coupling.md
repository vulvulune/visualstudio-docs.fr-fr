---
title: 'CA1506 : Éviter les couplages de classe excessifs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c5a5e070892f7efc096b0f8e24952bb9d139969
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950611"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506 : Éviter les couplages de classe excessifs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type ou une méthode est associée à d’autres types.

## <a name="rule-description"></a>Description de la règle
 Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.

 Types et méthodes qui présentent un degré élevé de couplage de classe peuvent être difficiles à gérer. Il est judicieux d’avoir des types et méthodes qui présentent un couplage faible et une forte cohésion.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, essayez de redéfinir le type ou la méthode pour réduire le nombre de types auquel il est associé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Exclure cet avertissement lors de la méthode ou le type est considéré comme plus facile à gérer en dépit de son grand nombre de dépendances sur d’autres types.

## <a name="see-also"></a>Voir aussi
 [Avertissements de la facilité de maintenance](../code-quality/maintainability-warnings.md) [mesure la complexité et la maintenabilité du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
