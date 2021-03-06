---
title: 'CA1816 : Appelez GC. SuppressFinalize correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 50375390b3a09ec18fcccd45e4eaee7e9fe102e2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094786"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816 : Appeler GC.SuppressFinalize correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilisation|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

- Une méthode qui est une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Une méthode qui n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appels <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Appelle une méthode <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> et passe un élément autre que cette (Me en Visual Basic).

## <a name="rule-description"></a>Description de la règle
 Le <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> méthode permet aux utilisateurs de libérer des ressources à tout moment avant l’objet devienne disponible pour le garbage collection. Si le <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> est appelée, elle libère les ressources de l’objet. Cela rend la finalisation inutile. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> doit appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> afin du garbage collector n’appelle pas le finaliseur de l’objet.

 Pour empêcher les types avec finaliseurs dérivés de devoir réimplémenter () [System.IDisposable]<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) et pour l’appeler, les types unsealed sans les finaliseurs doivent toujours appeler <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle :

 Si la méthode est une implémentation de <xref:System.IDisposable.Dispose%2A>, ajoutez un appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Si la méthode n’est pas une implémentation de <xref:System.IDisposable.Dispose%2A>, supprimez l’appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou déplacez-le vers le type <xref:System.IDisposable.Dispose%2A> implémentation.

 Modifier tous les appels à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> à passer ce (Me en Visual Basic).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez uniquement un avertissement de cette règle si vous utilisez délibérément <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour contrôler la durée de vie d’autres objets. Ne supprimez pas un avertissement de cette règle si une implémentation de <xref:System.IDisposable.Dispose%2A> n’appelle pas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. Dans ce cas, ne parvient pas à supprimer la finalisation dégrade les performances et n’apporte aucun avantage.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui incorrectement appels <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui correctement appels <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2215 : Méthodes Dispose doivent appeler dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Voir aussi
 [Dispose, modèle](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
