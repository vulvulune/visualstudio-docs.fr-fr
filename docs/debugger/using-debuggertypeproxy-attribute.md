---
title: Afficher le type personnalisé à l’aide de DebuggerTypeProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c379fbeb9d17f92dcc7067424ea06bb1a2805ed1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929640"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Demander au débogueur le type à afficher à l’aide de l’attribut DebuggerTypeProxy (C#, Visual Basic, C++/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> spécifie un proxy (ou remplaçant) pour un type et modifie la façon dont le type est affiché dans les fenêtres du débogueur. Quand vous visualisez une variable possédant un proxy, ce dernier remplace le type d’origine dans l’**affichage**. La fenêtre de variables du débogueur   n'affiche que les membres publics du type du proxy. Les membres privés ne sont pas affichés.

Cet attribut peut s'appliquer aux éléments suivants :

- Structures
- Classes
- Assemblys

> [!NOTE]
> Pour le code natif, cet attribut est pris en charge uniquement dans C++code /CLI.

Une classe proxy de type doit avoir un constructeur pouvant prendre un argument du type que le proxy remplacera. Le débogueur crée une nouvelle instance de la classe proxy de type chaque fois qu'il doit afficher une variable du type cible. Cela peut avoir des conséquences sur les performances. Par conséquent, vous ne devez pas effectuer d'autres tâches dans le constructeur que celles qui sont absolument nécessaires.

Pour éviter de trop handicaper les performances, l’évaluateur d’expression n’examine pas les attributs sur le proxy d’affichage du type à moins que le type ne soit développé par l’utilisateur en cliquant sur le symbole + dans la fenêtre de débogage, ou par l’utilisation de <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Vous ne devez donc pas placer d'attributs sur le type d'affichage lui-même. Les attributs peuvent et doivent être utilisés dans le corps du type d'affichage.

Il sera judicieux de faire du proxy de type une classe privée imbriquée dans la classe ciblée par l'attribut. Cela lui permettra d'accéder facilement aux membres internes.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> peuvent être héritées, donc si un proxy de type est spécifié sur une classe de base il s’applique à toutes les classes dérivées, à moins que ces classes dérivées spécifient leur propre proxy de type.

Si <xref:System.Diagnostics.DebuggerTypeProxyAttribute> est utilisé au niveau de l'assembly, le paramètre `Target` spécifie le type que le proxy remplacera.

Pour obtenir un exemple montrant comment utiliser cet attribut avec <xref:System.Diagnostics.DebuggerDisplayAttribute> et <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, consultez[à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Utilisation de génériques avec DebuggerTypeProxy

La prise en charge des génériques est limitée. Pour C#, `DebuggerTypeProxy` prend en charge uniquement les types ouverts. Un type ouvert, également appelé type non construit, est un type générique qui n’a pas été instancié avec des arguments pour ses paramètres de type. Les types fermés, également appelés types construits, ne sont pas pris en charge.

La syntaxe pour un type ouvert a l'aspect suivant :

`Namespace.TypeName<,>`

Si vous utilisez un type générique comme cible dans `DebuggerTypeProxy`, vous devez utiliser cette syntaxe. Le mécanisme `DebuggerTypeProxy` déduit les paramètres de type.

Pour plus d’informations sur les types ouverts et fermés en c#, consultez le [spécification du langage c#](/dotnet/csharp/language-reference/language-specification), section 20.5.2 Open et fermé de types.

Visual Basic n'ayant pas de syntaxe de type ouvert, vous ne pouvez pas faire la même chose en Visual Basic. À la place, vous devez utiliser une représentation sous forme de chaîne du nom de type ouvert.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Voir aussi

- [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Amélioration du débogage avec les attributs d’affichage de débogueur](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
