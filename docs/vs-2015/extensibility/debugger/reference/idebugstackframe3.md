---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43c5b3b9bbc5e09b41f346949c4ec788c3784786
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438164"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface étend [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour gérer les exceptions interceptées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface sur le même objet qui implémente le [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interface pour prendre en charge les exceptions interceptées.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un `IDebugStackFrame2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gère une exception pour le frame de pile actuel avant que la gestion des exceptions ordinaire.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retourne un contexte de code si un déroulement de pile se produit.|  
  
## <a name="remarks"></a>Notes  
 Une exception interceptée signifie qu’un débogueur peut traiter une exception avant que les routines de gestion des exceptions normales sont appelées par la durée d’exécution. Intercepter une exception essentiellement : la mise à l’heure d’exécution de prétendre qu’il existe un gestionnaire d’exceptions présent même quand il n’est pas.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) est appelée au cours de tous les événements de rappel d’exception normale (la seule exception à cela est que si vous déboguez du code en mode mixte (managé et code non managé), auquel cas l’exception ne peut pas être interceptée pendant le dernière chance rappel). Si le dé n’implémente pas `IDebugStackFrame3`, ou le DE renvoie une erreur à partir de IDebugStackFrame3 ::`InterceptCurrentException` (tel que `E_NOTIMPL`), puis le débogueur gère l’exception normalement.  
  
 En interceptant une exception, le débogueur peut autoriser l’utilisateur d’apporter des modifications à l’état du programme en cours de débogage et de reprendre l’exécution au point où l’exception a été levée.  
  
> [!NOTE]
> Exceptions interceptées sont autorisées uniquement dans le code managé, autrement dit, dans un programme qui s’exécute sous le Common Language Runtime (CLR).  
  
 Un moteur de débogage indique qu’il prend en charge interception des exceptions en définissant « metricExceptions » à la valeur 1 au moment de l’exécution à l’aide de la `SetMetric` (fonction). Pour plus d’informations, consultez [aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
