---
title: Informations de référence sur les tâches MSBuild WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 785e3960148d627e437d15e8662dfd76dccc53c0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659330"
---
# <a name="wpf-msbuild-task-reference"></a>Référence des tâches MSBuild WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le processus de génération de Windows Presentation Foundation (WPF) étend Microsoft Build Engine (MSBuild) avec un ensemble de tâches de génération supplémentaires, notamment des tâches pour compiler le balisage et traiter les ressources.  
  
## <a name="in-this-section"></a>Dans cette section  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classifie un ensemble de ressources sources comme devant être incorporées dans un assembly. Si une ressource n’est pas localisable, elle est incorporée dans l’assembly principal de l’application ; autrement, elle est incorporée dans un assembly satellite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Génère un assembly si au moins une page [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] dans un projet référence un type déclaré localement dans ce projet. L’assembly généré est supprimé une fois le processus de génération terminé, ou en cas d’échec du processus de génération.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Retourne le répertoire du runtime [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] actif.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Convertit des fichiers projet [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] non localisables au format binaire compilé.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Effectue la première passe de compilation du balisage sur les fichiers [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] qui référencent des types dans le même projet.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Fusionne les attributs de localisation et les commentaires d’un ou plusieurs fichiers binaires [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en un seul fichier pour tout l’assembly.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incorpore une ou plusieurs ressources (.jpg, .ico, .bmp,[!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] au format binaire et d’autres types d’extensions) dans un fichier .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Vérifie, met à jour ou supprime les identificateurs uniques (UID) pour localiser tous les éléments [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] inclus dans les fichiers [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] sources.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Ajoute l’élément **\<hostInBrowser />** au manifeste d’application (*nom_projet*.exe.manifest) quand un projet [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] est généré.  
  
## <a name="see-also"></a>Voir aussi  
 [MSBuild](http://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
