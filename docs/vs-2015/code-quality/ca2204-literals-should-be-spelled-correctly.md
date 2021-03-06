---
title: 'CA2204 : Les littéraux doivent être correctement orthographiés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a08cb7cee2af51ade4b94dbf675ff83d7da456e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951770"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204 : Les littéraux doivent être orthographiés correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode passe une chaîne littérale qui est utilisée dans un paramètre ou une propriété qui nécessite une chaîne localisée et la chaîne littérale contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d’orthographe Microsoft.

## <a name="rule-description"></a>Description de la règle
 Cette règle recherche une chaîne littérale qui est passée en tant que valeur à un paramètre ou une propriété lorsqu’un ou plusieurs des cas suivants est vrai :

- Le <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de propriété est définie sur true.

- Le nom de paramètre ou une propriété contient « Text », « Message » ou « Caption ».

- Le nom du paramètre de chaîne qui est passé à une méthode Console.Write ou Console.WriteLine est « value » ou « format ».

  Cette règle analyse la chaîne littérale en mots, jetons de mots composés et vérifie l’orthographe de chaque mot/jeton. Pour plus d’informations sur l’algorithme d’analyse, consultez [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Par défaut, la version anglaise (en) du vérificateur d’orthographe est utilisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez l’orthographe du mot ou ajoutez le mot au dictionnaire personnalisé. Pour plus d’informations sur l’utilisation des dictionnaires personnalisés, consultez [Comment : Personnaliser le dictionnaire d’analyse du Code](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Mots épelés correctement réduisent la courbe d’apprentissage nécessaire pour les nouvelles bibliothèques de logiciels.

## <a name="related-rules"></a>Règles associées
 [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703 : Chaînes de ressources doivent être correcte](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
