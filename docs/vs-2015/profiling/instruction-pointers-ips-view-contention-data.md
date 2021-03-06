---
title: Pointeurs d’instructions (IP), vue - Données de conflit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b27b185e659fc3a1f0adca4379896543a1eb87ea
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54834584"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Pointeurs d’instructions (IP), vue - Données de conflit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue IP des données de conflit répertorie les données des instructions d’assembly dont l’exécution a été bloquée dans le cadre de l’exécution du profilage.  
  
 Le tableau suivant explique les valeurs des colonnes dans la vue Pointeurs d’instruction.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Temps bloqué exclusif**|Temps bloqué dans cette fonction.|  
|**% de temps bloqué exclusif**|Pourcentage de temps bloqué pendant l’exécution de l’instruction.|  
|**Conflits exclusifs**|Nombre de conflits qui se sont produits pendant l’exécution de l’instruction.|  
|**% de conflits exclusifs**|Pourcentage de tous les conflits survenus pendant l’exécution de l’instruction dans le cadre de l’exécution du profilage.|  
|**Adresse de la fonction**|Adresse mémoire de départ de la fonction dans le fichier binaire chargé.|  
|**Nom de la fonction**|Nom de la fonction qui contient l’instruction.|  
|**Adresse d’instruction**|Adresse mémoire de l’instruction dans le fichier binaire chargé.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Nom du module**|Nom du module qui contient l’instruction.|  
|**Chemin du module**|Chemin du module qui contient l’instruction.|  
|**ID du processus**|ID de processus (PID) du processus profilé.|  
|**Nom du processus**|Nom du processus.|  
|**Début caractère source**|Décalage du caractère dans la ligne de fichier source au niveau duquel cette instruction commence.|  
|**Fin du caractère source**|Décalage du caractère dans la ligne de fichier source au niveau duquel cette instruction se termine.|  
|**Fichier source**|Fichier source qui contient l’instruction.|  
|**Début ligne source**|Numéro de ligne dans le fichier source au niveau duquel cette instruction commence.|  
|**Fin ligne source**|Numéro de ligne dans le fichier source au niveau duquel cette instruction se termine.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Pointeurs d’instruction (IP), vue](../profiling/instruction-pointers-ips-view.md)   
 [Vue Pointeurs d’instructions (IP) - Données d’échantillonnage de mémoire .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Vue Pointeurs d’instruction (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
