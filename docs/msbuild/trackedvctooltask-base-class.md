---
title: Classe TrackedVCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938867"
---
# <a name="trackedvctooltask-base-class"></a>Classe de base TrackedVCToolTask

De nombreuses tâches héritent au final de la classe <xref:Microsoft.Build.Utilities.Task> et de la classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Cette classe ajoute plusieurs paramètres aux tâches qui dérivent de [VCToolTask](../msbuild/vctooltask-base-class.md). Ces paramètres sont répertoriés dans ce document.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la classe de base **TrackedVCToolTask**.

|Paramètre|Description|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Paramètre **booléen** facultatif.|
|**EnableExecuteTool**|Paramètre **booléen** facultatif.|
|**ExcludedInputPaths**|Paramètre **ITaskItem[]** facultatif.|
|**MinimalRebuildFromTracking**|Paramètre **booléen** facultatif.|
|**PathOverride**|Paramètre de **chaîne** facultatif.|
|**PostBuildTrackingCleanup**|Paramètre **booléen** facultatif.|
|**RootSource**|Paramètre de **chaîne** facultatif.|
|**SkippedExecution**|Paramètre de sortie **booléen** facultatif.|
|**SourcesCompiled**|Paramètre de sortie **ITaskItem[]** facultatif.|
|**TLogCommandFile**|Paramètre **ITaskItem** facultatif.|
|**TLogReadFiles**|Paramètre **ITaskItem[]** facultatif.|
|**TLogWriteFiles**|Paramètre **ITaskItem[]** facultatif.|
|**ToolArchitecture**|Paramètre de **chaîne** facultatif.|
|**TrackCommandLines**|Paramètre **booléen** facultatif.|
|**TrackFileAccess**|Paramètre **booléen** facultatif.|
|**TrackedInputFilesToIgnore**|Paramètre **ITaskItem[]** facultatif.|
|**TrackedInputFilesToIgnore**|Paramètre **ITaskItem[]** facultatif.|
|**TrackerFrameworkPath**|Paramètre de **chaîne** facultatif.|
|**TrackerSdkPath**|Paramètre de **chaîne** facultatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)<br/>
[Tâches](../msbuild/msbuild-tasks.md)