---
title: 'Procédure : Sérialiser les informations de symboles | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b88268ba0ed8b1c324eda08ec3db969e088f279
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539247"
---
# <a name="how-to-serialize-symbol-information"></a>Procédure : Sérialiser les informations de symbole
Vous pouvez sérialiser les symboles nécessaires à l’analyse de votre application. La sérialisation de symboles permet d’ajouter des symboles au fichier .*vsp*. L’ajout d’informations de symboles au fichier .*vsp* permet aux autres utilisateurs d’analyser un rapport de performances sans avoir accès aux symboles d’origine. Si les symboles ne sont pas sérialisés, vous devez disposer des fichiers .*exe* et .*pdb* instrumentés d’origine pour analyser le fichier .*vsp*.

### <a name="to-automatically-serialize-symbol-information"></a>Pour sérialiser automatiquement les informations de symboles

1. Dans le menu **Outils** , cliquez sur **Options**.

     La boîte de dialogue **Options** s’affiche.

2. Cliquez sur **Outils d’analyse des performances**.

3. Sous **Paramètres généraux**, sélectionnez **Sérialiser automatiquement les informations de symboles**.

## <a name="see-also"></a>Voir aussi
- [Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)
- [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Guide pratique pour Enregistrer des fichiers de rapports analysés](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))