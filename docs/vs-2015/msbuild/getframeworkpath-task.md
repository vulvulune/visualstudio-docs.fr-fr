---
title: GetFrameworkPath, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663126"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Récupère le chemin aux assemblys [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 1.1, s’ils existent. Sinon, retourne `null`.|  
|`FrameworkVersion20Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 2.0, s’ils existent. Sinon, retourne `null`.|  
|`FrameworkVersion30Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 3.0, s’ils existent. Sinon, retourne `null`.|  
|`FrameworkVersion35Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 3.5, s’ils existent. Sinon, retourne `null`.|  
|`FrameworkVersion40Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 4.0, s’ils existent. Sinon, retourne `null`.|  
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys de la version la plus récente du .NET Framework, s’ils sont disponibles. Sinon, retourne `null`.|  
  
## <a name="remarks"></a>Remarques  
 Si plusieurs versions du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sont installées, cette tâche retourne la version sur laquelle [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] est conçu pour s’exécuter.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `GetFrameworkPath` pour stocker le chemin du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] dans la propriété `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
