---
title: 'CA1301 : Éviter les accélérateurs en double'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f82163b1c377df4c8c7fcbba07672312153dad9b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797477"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301 : Éviter les accélérateurs en double

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Category|Microsoft.Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type étend <xref:System.Windows.Forms.Control?displayProperty=fullName> et contient deux ou plusieurs contrôles de niveau supérieur qui ont des clés d’accès identiques qui sont stockés dans un fichier de ressources.

## <a name="rule-description"></a>Description de la règle

Une clé d’accès, également appelé un accélérateur, Active l’accès clavier à un contrôle à l’aide de la **Alt** clé. Lorsque plusieurs contrôles présentent la même clé d’accès, le comportement de la clé d’accès n’est pas bien défini. L’utilisateur ne peut pas être en mesure d’accéder au contrôle prévu à l’aide de la clé d’accès et un contrôle autre que celui qui est prévu peut être activé.

L’implémentation actuelle de cette règle ignore les éléments de menu. Toutefois, les éléments de menu dans le même sous-menu ne doivent pas avoir les clés d’accès identiques.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, définissez les clés d’accès unique pour tous les contrôles.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant présente un formulaire minimal qui contient deux contrôles qui ont des clés d’accès identiques. Les clés sont stockées dans un fichier de ressources, ce qui n’est pas affiché. Toutefois, leurs valeurs s’affichent dans les out `checkBox.Text` lignes. Le comportement d’accélérateurs en doublon peut être examiné en échangeant les `checkBox.Text` lignes avec leurs équivalents commentés. Toutefois, dans ce cas, l’exemple ne génère pas un avertissement à partir de la règle.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ressources dans des applications de bureau](/dotnet/framework/resources/index)