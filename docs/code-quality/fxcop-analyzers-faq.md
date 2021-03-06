---
title: Analyse de code FxCop et analyseurs FxCop
ms.date: 09/06/2018
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6d8e3f3288c6a64b35a1de59fe0f317b6283b805
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816421"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Questions fréquentes (FAQ) sur FxCop et les analyseurs FxCop

Il peut être un peu difficile de comprendre les différences entre les analyseurs FxCop et FxCop hérité. Cet article vise à répondre à certaines des questions que vous pouvez vous poser.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Quelle est la différence entre les analyseurs FxCop et FxCop hérité ?

FxCop hérité exécute une analyse post-build sur un assembly compilé. Il s’exécute en tant qu’exécutable distinct appelé **FxCopCmd.exe**. FxCopCmd.exe charge l’assembly compilé, exécute l’analyse du code, puis signale les résultats (ou *diagnostics*).

Les analyseurs FxCop sont basés sur .NET Compiler Platform (« Roslyn »). Vous [les installez comme package NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) référencé par le projet ou la solution. Les analyseurs FxCop exécutent une analyse basée sur le code source pendant l’exécution du compilateur. Les analyseurs FxCop sont hébergés dans le processus du compilateur, **csc.exe** ou **vbc.exe**, et exécutent l’analyse quand le projet est généré. Les résultats des analyseurs sont signalés en même temps que les résultats du compilateur.

> [!NOTE]
> Vous pouvez également [installer des analyseurs FxCop en tant qu’extension Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). Dans ce cas, les analyseurs s’exécutent quand vous tapez dans l’éditeur de code, mais pas au moment de la génération. Si vous voulez exécuter des analyseurs FxCop dans le cadre de l’intégration continue (CI), installez-les en tant que package NuGet à la place.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>La commande Exécuter l’analyse du Code exécute-t-elle les analyseurs FxCop ?

Non. Quand vous sélectionnez **Analyser** > **Exécuter l’analyse du code**, elle exécute l’analyse statique du code ou FxCop hérité. L’option **Exécuter l’analyse du Code** n’a aucun effet sur les analyseurs basés sur Roslyn, notamment les analyseurs FxCop basés sur Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>La propriété de projet msbuild RunCodeAnalysis exécute-t-elle des analyseurs ?

Non. La propriété **RunCodeAnalysis** dans un fichier projet (par exemple, *.csproj*) est utilisée uniquement pour exécuter FxCop hérité. Elle s’exécute une tâche msbuild post-build qui appelle **FxCopCmd.exe**. Cela revient à sélectionner **Analyser** > **Exécuter l’analyse du code** dans Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Alors, comment exécuter des analyseurs FxCop ?

Pour exécuter des analyseurs FxCop, commencez par [installer le package NuGet](install-fxcop-analyzers.md) correspondant à ces derniers. Générez ensuite votre projet ou solution à partir de Visual Studio ou à l’aide de msbuild. Les avertissements et erreurs que génèrent les analyseurs FxCop s’affichent dans la **liste d’erreurs** ou la fenêtre Commande.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Je reçois l’avertissement CA0507 même après avoir installé le package NuGet d’analyseurs FxCop

Si vous avez installé les analyseurs FxCop, mais que vous recevez toujours l’avertissement CA0507 **« Exécuter l’analyse du code » a été déprécié en faveur des analyseurs FxCop, qui s’exécutent pendant la phase de build**, il peut être nécessaire de définir la propriété msbuild **RunCodeAnalysis** de votre fichier projet sur **false**. Sinon, l’analyse statique du code s’exécute après chaque phase de build.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Bien démarrer avec les analyseurs](fxcop-analyzers.yml)
- [Installer des analyseurs FxCop](install-fxcop-analyzers.md)
