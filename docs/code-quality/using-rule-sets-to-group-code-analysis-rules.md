---
title: Ensembles de règles d'analyse du code
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c95b442835289265d197b6806c6d87fa051f2c1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825082"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Utiliser la règle définit pour les règles d’analyse de code de groupe

Lorsque vous configurez l’analyse du code dans Visual Studio, vous pouvez choisir parmi une liste des intégré *ensembles de règles*. Un ensemble de règles est un regroupement de règles d’analyse du code qui identifient les problèmes ciblés et des conditions spécifiques pour ce projet. Par exemple, vous pouvez appliquer un ensemble de règles qui a conçu pour analyser le code des API disponibles publiquement. Vous pouvez également appliquer un ensemble de règles qui inclut toutes les règles disponibles.

Vous pouvez personnaliser un ensemble de règles en ajoutant ou supprimant des règles ou en modifiant les niveaux de gravité de règle apparaissent comme des avertissements ou erreurs dans le **liste d’erreurs**. Ensembles de règles personnalisés peuvent répondre à un besoin pour votre environnement de développement particulier. Lorsque vous personnalisez un ensemble de règles, l’éditeur d’ensemble de règles fournit la recherche et des outils pour vous aider dans le processus de filtrage.

Ensembles de règles sont disponibles pour [analyse statique du code managé](how-to-configure-code-analysis-for-a-managed-code-project.md), [analyse du code C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md), et [analyseurs de Roslyn](analyzer-rule-sets.md).

## <a name="rule-set-format"></a>Format d’ensemble de règles

Un ensemble de règles est spécifié au format XML dans un *.ruleset* fichier. Les règles, qui se composent d’un ID et un *action*, sont regroupés par ID de l’analyseur et l’espace de noms dans le fichier.

Le contenu d’un *.ruleset* fichier ressemble à ce document XML :

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Il est plus facile à [modifier un ensemble de règles](../code-quality/working-in-the-code-analysis-rule-set-editor.md) dans le graphique **Éditeur d’ensemble de règles** que manuellement.

## <a name="specify-a-rule-set-for-a-project"></a>Spécifiez un ensemble de règles pour un projet

La règle définie pour un projet est spécifié par le **CodeAnalysisRuleSet** propriété dans le fichier de projet Visual Studio. Exemple :

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/rule-set-reference.md)