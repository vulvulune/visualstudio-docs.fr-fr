---
title: Suivi des événements pour Windows (ETW), rapport | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc0e139644a0b3df29109c1543140e57c5378f31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444012"
---
# <a name="event-tracing-for-windows-etw-report"></a>Suivi d'événements pour Windows (ETW), rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le rapport Suivi des événements pour Windows (ETW) liste les événements ETW enregistrés dans une session de performances des Outils de profilage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Les données de suivi d’événements pour Windows sont collectées dans un fichier binaire (.etl).  
  
> [!NOTE]
> Vous ne pouvez pas afficher les rapports de suivi des événements pour Windows dans l’interface de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Pour plus d’informations sur la collecte de données ETW en utilisant les Outils de profilage de l’interface [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Guide pratique pour Collecter le suivi d’événements pour Windows (ETW) données](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Pour plus d’informations sur la collecte des données de suivi des événements pour Windows en utilisant les outils de ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), consultez [Événements](../profiling/events-vsperfcmd.md).  
  
- Vous générez le rapport de suivi d’événements pour Windows en utilisant la commande **VSReport/Summary:ETW**. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
|Colonne|Description|  
|------------|-----------------|  
|**Horodatage**|Identifie quand l’événement s’est produit.|  
|**ID du processus**|Identifie le processus qui a généré l’événement.|  
|**ID de thread**|Identifie le thread qui a généré l’événement.|  
|**Description**|Identifie le fournisseur d’événements.|  
|**Type**|Identifie le type d’événement.|  
|**Propriétés**|Propriétés de l’événement. Chaque événement est une paire nom-valeur avec la virgule comme séparateur, qui est placée entre des crochets.|
