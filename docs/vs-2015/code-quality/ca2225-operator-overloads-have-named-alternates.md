---
title: 'CA2225 : Surcharges d’opérateur ont d’autres méthodes nommées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa90a1e97b563ef549cb3f628fcf9130a364c50a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951773"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée.

## <a name="rule-description"></a>Description de la règle
 Surcharge d’opérateur autorise l’utilisation de symboles pour représenter des calculs pour un type. Par exemple, un type qui surcharge le symbole plus (+) pour l’addition aurait en général, un membre de substitution nommé 'Add'. Le membre de substitution nommé donne accès à la même fonctionnalité que l’opérateur et est fourni pour les développeurs qui programment dans les langages qui ne prennent pas en charge les opérateurs surchargés.

 Cette règle examine les opérateurs répertoriés dans le tableau suivant.

|C#|Visual Basic|C++|Autre nom|
|---------|------------------|-----------|--------------------|
|+ (binaire)|+|+ (binaire)|Ajouter|
|+=|+=|+=|Ajouter|
|&|and|&|BitwiseAnd|
|&=|Et =|&=|BitwiseAnd|
|&#124;|Ou|&#124;|BitwiseOr|
|&#124;=|Ou =|&#124;=|BitwiseOr|
|--|N/A|--|Décrémentation|
|/|/|/|Diviser|
|/=|/=|/=|Diviser|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|Xor=|^=|Xor|
|>|>|>|Comparer|
|>=|>=|>=|Comparer|
|++|N/A|++|Incrémentation|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Comparer|
|<=|<=|\<=|Comparer|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|
|!|N/A|!|LogicalNot|
|%|Mod|%|Mod ou reste|
|%=|N/A|%=|Mod|
|* (binaire)|*|*|Multiplication|
|*=|N/A|*=|Multiplication|
|~|Ne convient pas|~|OnesComplement|
|>>|>>|>>|MAJ droite|
=|N/A|>>=|MAJ droite|
|-(binaire)|-(binaire)|-(binaire)|Soustraire|
|-=|N/A|-=|Soustraire|
|true|IsTrue|N/A|IsTrue (propriété)|
|-(unaire)|N/A|-|Negate|
|+ (unaire)|N/A|+|Signe plus|
|False|IsFalse|False|IsTrue (propriété)|

 N/a == ne peut pas être surchargé dans la langue sélectionnée.

 La règle vérifie également les opérateurs de cast implicites et explicites dans un type (`SomeType`) en recherchant les méthodes nommées `ToSomeType` et `FromSomeType`.

 En C#, lorsqu’un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est aussi implicitement surchargé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez la méthode alternative pour l’opérateur. Nommez-le à l’aide de l’autre nom recommandé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle si vous implémentez une bibliothèque partagée. Les applications peuvent ignorer un avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant définit une structure qui enfreint cette règle. Pour corriger l’exemple, ajoutez un public `Add(int x, int y)` méthode à la structure.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1046 : Ne pas surcharger l’opérateur égal sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224 : Remplacez equals lors de la surcharge l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218 : Remplacez GetHashCode au moment de remplacer Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
