---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf84711b6f87d055bb37f47c259306fb55e0f77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875175"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Cette interface fournit la prise en charge du débogage multithread.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un moteur de débogage implémente cette interface pour prendre en charge le débogage simultané de plusieurs threads. Cette interface est implémentée sur le même objet qui implémente le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir d’un `IDebugProgram2` interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEngineProgram2`.

|Méthode|Description|
|------------|-----------------|
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arrête tous les threads en cours d’exécution dans ce programme.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Surveille l’exécution (ou arrêter de surveiller l’exécution) se produise sur le thread donné.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Autorise (ou interdit) d’évaluation d’expression se produise sur le thread donné, même si le programme est arrêté.|

## <a name="remarks"></a>Notes
 Visual Studio appelle cette interface en réponse à une [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événements et définir les États « Watch pour Thread Step » et « Watch pour Expression d’évaluation sur Thread » du programme. [Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée chaque fois que le programme doit être arrêtée ; cette méthode permet du programme pour mettre fin à tous les threads.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)