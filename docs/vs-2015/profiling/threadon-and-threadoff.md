---
title: ThreadOn et ThreadOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77868ea7082c1b9118b70062f19195d94b4ca20a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780784"
---
# <a name="threadon-and-threadoff"></a>ThreadOn et ThreadOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les sous-commandes **ThreadOff** et **ThreadOn** de VSPerfCmd.exe sont disponibles seulement dans les sessions de profilage en ligne de commande qui utilisent la méthode d’instrumentation. **ThreadOff** et **ThreadOn** suspendent et reprennent le profilage du thread spécifié. **ThreadOff** arrête le profilage du thread et **ThreadOn** démarre le profilage du thread.  
  
 Dans la plupart des cas, vous spécifiez **ThreadOn** ou **ThreadOff** comme seule option d’une ligne de commande VSPerfCmd.exe, mais elles peuvent aussi être combinées avec les sous-commandes **GlobalOn**, **GlobalOff**, **ProcessOn** et **ProcessOff**.  
  
 Les sous-commandes **ThreadOn** et **ThreadOff** interagissent avec les sous-commandes **GlobalOn** et **GlobalOff**, qui contrôlent la collecte de données de tous les processus d’une session de profilage en ligne de commande, et avec les sous-commandes **ProcessOn** et **ProcessOff**, qui contrôlent la collecte de données d’un processus spécifié.  
  
 Les sous-commandes **ThreadOff** et **ThreadOn** affectent également le nombre de Start/Stop du thread qui est manipulé par les fonctions d’API du profileur.  
  
- **ThreadOff** affecte immédiatement la valeur 0 au nombre de Start/Stop global et suspend ainsi le profilage.  
  
- **ThreadOn** affecte immédiatement la valeur 1 au nombre de Start/Stop du thread et reprend ainsi le profilage.  
  
  Pour plus d’informations, consultez [API des outils de profilage](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TID`  
 Identificateur sous forme d’entier du processus à démarrer ou à arrêter.  
  
## <a name="valid-options"></a>Options valides  
 Vous pouvez spécifier **ThreadOn** et **ThreadOff** sur des lignes de commande qui contiennent également les sous-commandes suivantes.  
  
 **Start:** `Method`  
 Initialise la session de profilage en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Arrête ou démarre le profilage de tous les processus d’une session de profilage en ligne de commande.  
  
 {**ProcessOff**&#124;**ProcessOn**}  **:**`TID`  
 Arrête ou démarre le profilage du processus spécifié.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la sous-commande **ThreadOff** est utilisée pour arrêter la collecte de données de profilage et collecter seulement les données de démarrage de l’application.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)
