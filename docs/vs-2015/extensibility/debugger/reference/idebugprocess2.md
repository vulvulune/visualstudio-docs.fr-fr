---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68f1693bbbda9bbf7622c2378799db4a342be7a5
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58951096"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un processus en cours d’exécution sur un port. Si le port est le port local, puis `IDebugProcess2` représente généralement un processus physique sur l’ordinateur local.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par un fournisseur de port personnalisé pour gérer des programmes en tant que groupe. Cette interface doit être implémentée par le fournisseur de port.  
  
 Un moteur de débogage implémente également cette interface si elle prend en charge le lancement d’un programme via [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est appelée principalement par le Gestionnaire de session de débogage (SDM) pour interagir avec un groupe de programmes identifiée dans ce processus.  
  
 Appelez [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) pour obtenir cette interface. Cette interface est également retournée en appelant `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProcess2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtient une description du processus.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Énumère les programmes qui sont contenus dans ce processus.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtient le titre, le nom convivial ou le nom de fichier du processus.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtient l’instance d’un serveur de l’ordinateur que ce processus est en cours d’exécution.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Met fin au processus.|  
|[Attacher](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Attache au processus.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Détermine si le SDM pouvez détacher le processus.|  
|[Détacher](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Détache le débogueur à partir du processus.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtient l’identificateur de processus système.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtient un identificateur global unique pour ce processus.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATED]|Obtient le nom de la session qui est le processus de débogage.<br /><br /> [DÉCONSEILLÉ. DOIT TOUJOURS RETOURNER `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Énumère les threads en cours d’exécution dans le processus.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Demande que le programme suivant, l’exécution de code dans cet arrêt de processus.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtient le port que ce processus est en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
 Un `IDebugProcess2` contient un ou plusieurs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaces.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
