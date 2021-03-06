---
title: Directive d'importation T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49ab8d3462877a28cf40aed519b71615b23f8d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856348"
---
# <a name="t4-import-directive"></a>Directive d'importation T4

Dans les blocs de code d’un modèle de texte Visual Studio T4, le `import` directive vous permet de faire référence aux éléments dans un autre espace de noms sans fournir un nom qualifié complet. Cela équivaut à `using` en C# ou à `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Pour obtenir une vue d’ensemble de l’écriture de modèles de texte T4, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-import-directive"></a>Utilisation de la directive d'importation

```
<#@ import namespace="namespace" #>
```

 Dans cet exemple, le code du modèle peut omettre un espace de noms explicite pour les membres de System.IO :

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Importations standard
 L'espace de noms suivant est importé automatiquement, afin que vous n'ayez pas besoin d'écrire une directive d'importation pour lui :

- `System`

  De plus, si vous utilisez une directive personnalisée, le processeur de directive peut importer automatiquement des espaces de noms.

  Par exemple, si vous écrivez des modèles pour un langage spécifique à un domaine (DSL), vous n’avez pas besoin d’importer des directives pour les espaces de noms suivants :

- `Microsoft.VisualStudio.Modeling`

- Espace de noms de votre solution DSL

## <a name="see-also"></a>Voir aussi

- [Directive d’assembly T4](../modeling/t4-assembly-directive.md)