---
title: Boîte de dialogue Pages de propriété de Source des fichiers, les propriétés communes, Solution de débogage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83bed0588a0959ab85906d949e1b0752396223ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852915"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Fichiers sources pour le débogage, Propriétés communes, boîte de dialogue Pages de propriétés de Solution
Cette page de propriétés spécifie à quel endroit le débogueur recherchera les fichiers sources lors du débogage de la solution.

 Pour accéder à la page de propriétés **Fichiers sources pour le débogage**, cliquez avec le bouton droit sur votre solution dans l’**Explorateur de solutions**, puis sélectionnez **Propriétés** dans le menu contextuel. Développez le dossier **Propriétés communes**, puis cliquez sur la page **Fichiers sources pour le débogage**.

 **Répertoires contenant du code source** contient une liste de répertoires dans lesquels le débogueur recherche les fichiers sources lors du débogage de la solution. Les sous-répertoires des dossiers spécifiés sont également récupérés.

 **Ne pas rechercher ces fichiers sources** Entrez les noms de tous les fichiers que vous ne souhaitez pas que le débogueur à lire. Si le débogueur trouve un de ces fichiers dans un des répertoires spécifiés précédemment, il l'ignore. Si la boîte de dialogue **Rechercher la source** s’affiche pendant que vous déboguez et que vous cliquez sur **Annuler**, le fichier que vous recherchiez se trouve ajouté à cette liste, de sorte que le débogueur ne continue pas à rechercher ce fichier.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)