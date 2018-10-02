---
title: Vue Résumé - Données d’échantillonnage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdfa43dab60268eb428c2affbc6ad072e04b45cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501386"
---
# <a name="summary-view---sampling-data"></a>Vue Résumé - Données d’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue Résumé - données d’échantillonnage](https://docs.microsoft.com/visualstudio/profiling/summary-view-sampling-data).  
  
La vue Résumé affiche des informations sur les fonctions dont le coût est le plus élevé quant aux performances dans une exécution du profilage. Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [Vue Résumé](../profiling/summary-view.md).  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Graphique chronologique  
 Le graphique chronologique de la vue Résumé montre le pourcentage d’utilisation du processeur (UC) de l’application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d’informations, consultez [Guide pratique pour filtrer les vues de rapport à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Chemin réactif  
 Le **chemin réactif** montre le chemin d’exécution dans lequel la plupart des échantillons ont été collectés. Vous pouvez cliquer sur une fonction pour afficher la vue Détails de la fonction pour celle-ci. Pour afficher d’autres vues pour la fonction, cliquez avec le bouton droit sur la fonction puis cliquez sur une vue de la liste.  
  
 Le **chemin réactif** inclut les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom de la fonction.|  
|**% d’échantillons inclusifs**|Pourcentage de tous les échantillons collectés quand cette fonction ou une fonction appelée par cette fonction s’exécutait.|  
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons collectés quand la fonction exécutait du code du corps de la fonction. Ce pourcentage n’inclut pas les échantillons collectés dans les fonctions appelées par cette fonction.|  
  
## <a name="functions-doing-most-individual-work"></a>Fonctions faisant le plus de travail individuel  
 La liste **Fonctions faisant le plus de travail individuel** montre les fonctions qui ont le plus grand nombre d’échantillons exclusifs dans l’exécution du profilage. Un échantillon exclusif est affecté à une fonction si la fonction exécutait son propre code quand l’échantillon a été collecté. Un échantillon exclusif n’est pas affecté à une fonction si la fonction appelait une autre fonction quand l’échantillon a été collecté. Un grand nombre d’échantillons exclusifs indique qu’un temps considérable a été passé dans la fonction elle-même.  
  
 Vous pouvez cliquer sur une fonction pour afficher la vue Détails de la fonction pour celle-ci. Pour afficher d’autres vues pour la fonction, cliquez avec le bouton droit sur la fonction, puis cliquez sur une vue de la liste.  
  
 **Fonctions faisant plus de travail individuel** inclut les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|------------|-----------------|  
|**Name**|Nom de la fonction.|  
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution de la fonction collectés quand la fonction exécutait du code du corps de la fonction. Le pourcentage ne comprend pas les échantillons collectés quand des fonctions appelées par cette fonction étaient en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Résumé](../profiling/summary-view-dotnet-memory-data.md)   
 [Vue Résumé](../profiling/summary-view-instrumentation-data.md)


