---
title: IDebugPortEvents2::Event | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: beb1181fc792733a122f6e2df02a6c1811a9a681
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501684"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugPortEvents2::Event](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportevents2-event).  
  
Cette méthode envoie les événements qui signifient l’existence la création et la destruction des processus et des programmes sur un port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMachine`  
 [in] Un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) objet qui représente le serveur de débogage (il en existe un pour chaque instance de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]) dans laquelle l’événement s’est produit.  
  
 `pPort`  
 [in] Un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objet qui représente le port dans lequel l’événement s’est produite.  
  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objet qui représente le processus dans lequel l’événement s’est produite.  
  
 `pProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme dans lequel l’événement s’est produite.  
  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objet qui identifie l’événement. Les événements possibles sont les suivantes :  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 [in] Le GUID de l’événement. Étant donné que l’événement est casté en [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) avant d’appeler cette méthode, cet identificateur rend plus facile de déterminer l’événement qui est envoyé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
