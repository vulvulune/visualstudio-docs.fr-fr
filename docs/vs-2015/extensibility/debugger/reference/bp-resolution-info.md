---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ba3f95372774b811030244a20208edd6f226981
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952106"
---
# <a name="bpresolutioninfo"></a>BP_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Décrit les informations de point d’arrêt lié pour un point d’arrêt de code ou un point d’arrêt de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct _BP_RESOLUTION_INFO {   
   BPRESI_FIELDS          dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
} BP_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
};  
```  
  
## <a name="members"></a>Membres  
 `dwFields`  
 Une collection d’indicateurs de la [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) énumérations qui spécifie quels champs sont remplies.  
  
 `bpResLocation`  
 Le [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) structure qui spécifie l’emplacement du point d’arrêt dans le code ou de données.  
  
 `pProgram`  
 Le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente l’application dans laquelle l’erreur de point d’arrêt s’est produite.  
  
 `pThread`  
 Le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objet qui représente le thread dans lequel l’application qui contient l’erreur de point d’arrêt est en cours d’exécution.  
  
## <a name="remarks"></a>Notes  
 Cette structure est retournée par [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
