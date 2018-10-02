---
title: 'CA1717 : Seules les énumérations FlagsAttribute doivent être des noms au pluriel | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fbaa220d39f72900dbf03d238a45fc988b65e6b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590288"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717 : Seuls les noms des enums FlagsAttribute doivent être au pluriel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1717 : enums uniquement FlagsAttribute doivent être des noms au pluriel](https://docs.microsoft.com/visualstudio/code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names).

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’une énumération extérieurement visible se termine par un mot au pluriel et l’énumération n’est pas marquée avec le <xref:System.FlagsAttribute?displayProperty=fullName> attribut.

## <a name="rule-description"></a>Description de la règle
 Selon les conventions d’affectation de noms qu’un nom au pluriel pour une énumération indique que plusieurs valeurs de l’énumération peuvent être spécifiées simultanément. La <xref:System.FlagsAttribute> indique aux compilateurs que l’énumération doit être traitée comme un champ de bits qui autorise des opérations au niveau du bit sur l’énumération.

 Si seulement une valeur d’une énumération peut être spécifiée à la fois, le nom de l’énumération doit être un mot au singulier. Par exemple, une énumération qui définit les jours de la semaine peut être conçue pour une utilisation dans une application dans laquelle vous pouvez spécifier plusieurs jours. Cette énumération doit avoir le <xref:System.FlagsAttribute> et peut être appelée 'Jours'. Une énumération semblable qui permet uniquement à un jour d’être spécifié n’a pas l’attribut et peut être appelée « Day ».

 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Rendre le nom de l’énumération un mot au singulier ou ajoutez le <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement à partir de la règle si le nom se termine par un mot au singulier.

## <a name="related-rules"></a>Règles associées
 [CA1714 : Les énumérations d’indicateurs doivent avoir des noms au pluriel](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.FlagsAttribute?displayProperty=fullName> [Conception d’énumérations](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)


