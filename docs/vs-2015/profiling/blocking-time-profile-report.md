---
title: Rapport sur les profils de temps de blocage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae0c4f34f0d3447f63afbf08e9d788304b2d353f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493400"
---
# <a name="blocking-time-profile-report"></a>Profil de temps de blocage, rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [rapport de profil de temps de blocage](https://docs.microsoft.com/visualstudio/profiling/blocking-time-profile-report).  
  
Les rapports de profil rassemblent des données relatives au temps de blocage pour les piles d’appels qui sont spécifiques à chaque catégorie de blocage (par exemple « E/S » ou « Synchronisation »). Le rapport Anticipation répertorie les processus qui ont anticipé le processus en cours, ainsi que le nombre d’instances d’anticipations. Pour générer le rapport de profil de blocage, l’outil collecte des appels d’API bloquants et les rassemble au sein d’une arborescence de piles d’appels. Les données figurant dans ces rapports varient selon la plage horaire, les threads masqués et les deux filtres suivants qui peuvent être appliqués :  
  
-   Si l’option Uniquement mon code est activée, seuls les frames de pile contenant du code utilisateur sont présentés, ainsi que le premier niveau situé sous le code utilisateur.  
  
-   Si la valeur Réduction du bruit est définie, les piles assemblées dont la fréquence est inférieure à celle spécifiée sont ignorées.  
  
 Développez une entrée de l’arborescence des appels pour rechercher la ligne de code où du temps de blocage a été passé. Pour localiser la ligne de code source d’une entrée, dans le menu contextuel, sélectionnez **Afficher la source**. Pour localiser la ligne de code ayant appelé l’entrée, dans le menu contextuel, sélectionnez **Afficher les sites d’appel**. Si un seul site d’appel est disponible, la commande se connecte à la ligne de code du site d’appel qui est mise en surbrillance. Si plusieurs sites d’appel sont disponibles, la commande ouvre une boîte de dialogue dans laquelle vous pouvez sélectionnez une entrée, puis cliquer sur le bouton **Atteindre la source** pour rechercher le site d’appel mis en surbrillance. Il est souvent très utile d’afficher le code source du site d’appel ayant le plus grand nombre d’instances et/ou la plus longue durée.  
  
## <a name="blocking-time-report-columns"></a>Colonnes du rapport de temps de blocage  
 Le tableau suivant montre les colonnes de chaque rapport de temps de blocage.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|Name|Nom de la fonction pour chaque niveau de la pile des appels.|  
|Instances|Nombre d’instances de l’appel bloquant pendant la période visible.|  
|Durée de blocage inclusif|Durée totale de blocage pour toutes les piles qui atteignent ce niveau de l’arborescence de la pile des appels. Le nombre inclusif correspond à la somme du temps de blocage exclusif de cette fonction et de celui de tous ses nœuds enfants.|  
|Durée de blocage exclusif|Durée totale de blocage au cours de laquelle cette fonction se trouve au niveau le plus bas de la pile des appels. Une entrée de pile d’appels unique dont le temps de blocage exclusif est élevé peut être une fonction intéressante.|  
|API /Catégorie d’attente|S’affiche uniquement pour les fonctions situées au niveau le plus bas de la pile des appels. Lorsque la signature de l’appel bloquant est reconnue, le nom de l’API bloquante est fourni. Si la signature n’est pas reconnue, les informations indiquées par le noyau sont fournies.|  
|Détails|Nom complet de la fonction. Peut contenir le nombre de lignes lorsque celui-ci est disponible.|  
  
### <a name="synchronization"></a>Synchronisation  
 Le rapport Synchronisation affiche les appels responsables des segments qui se bloquent lors de la synchronisation, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Durée de synchronisation](../profiling/synchronization-time.md).  
  
### <a name="sleep"></a>Sleep  
 Le rapport Veille affiche les appels responsables du temps de blocage attribué à du temps passé en veille, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Durée de veille](../profiling/sleep-time.md).  
  
### <a name="io"></a>E/S  
 Le rapport E/S affiche les appels responsables des segments qui se bloquent lors d’une opération d’E/S, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Temps d’E/S (vue Threads)](../profiling/i-o-time-threads-view.md).  
  
### <a name="memory-management"></a>Gestion de la mémoire  
 Le rapport Gestion de la mémoire affiche les appels responsables des segments qui se bloquent lors d’une opération de gestion de la mémoire, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Période de gestion de la mémoire](../profiling/memory-management-time.md).  
  
### <a name="preemption"></a>Anticipation  
 Le rapport Anticipation répertorie les processus qui ont anticipé le processus en cours, ainsi que le nombre d’instances.  Vous pouvez développer chaque processus pour afficher les threads qui ont remplacé ceux du processus en cours, et pour afficher le détail des instances d’anticipation de chaque thread. Ce rapport de blocage est moins exploitable, car l’anticipation est généralement imposée à votre processus par le système d’exploitation, et non par un problème dans votre code. Pour plus d’informations, consultez [Durée de préemption](../profiling/preemption-time.md).  
  
### <a name="ui-processing"></a>Traitement de l'interface utilisateur  
 Le rapport Traitement de l’interface utilisateur affiche les appels responsables des segments qui se bloquent lors d’un blocage d’interface utilisateur, ainsi que les durées totales de blocage pour chaque pile des appels. Pour plus d’informations, consultez [Temps de traitement UI](../profiling/ui-processing-time.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)


