---
title: Notification du Port | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 910b4bcb0a3258a6e661421c225121b8f888fcef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409675"
---
# <a name="notify-the-port"></a>Notifier le port
Après avoir lancé un programme, le port doit être averti, comme suit :

1. Lorsqu’un port reçoit un nouveau nœud de programme, il renvoie un événement de création de programme à la session de débogage. L’événement s’accompagne d’une interface qui représente le programme.

2. La session de débogage interroge le programme pour l’identificateur d’un moteur de débogage (dé) qui permettre attacher à.

3. La session de débogage vérifie si le DE figure dans la liste DEs autorisée pour ce programme. La session de débogage obtient cette liste à partir des paramètres de programme actif de la solution, à l’origine passés par le package de débogage.

    Le DE doit se trouver sur la liste autorisée, sans quoi le DE ne sera pas attaché au programme.

   Par programmation, lorsqu’un port reçoit tout d’abord un nouveau nœud de programme, il crée un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface pour représenter le programme.

> [!NOTE]
> Il ne faut pas confondre avec le `IDebugProgram2` interface créée ultérieurement par le moteur de débogage (dé).

 Le port envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événement de création de programme au Gestionnaire de débogage de session (SDM) au moyen d’un COM `IConnectionPoint` interface.

> [!NOTE]
> Il ne faut pas confondre avec le `IDebugProgramCreateEvent2` interface, qui est envoyée plus tard par l’Allemagne.

 Avec l’interface d’événement proprement dit, le port envoie le [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), et [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces qui représentent le port, traitement, et programmer, respectivement. Les appels SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) pour obtenir le GUID de l’Allemagne qui peut déboguer le programme. Le GUID a été obtenu à l’origine à partir de la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.

 Le SDM vérifie si le DE figure dans la liste DEs autorisée. Le SDM obtient cette liste à partir des paramètres de programme actif de la solution, à l’origine passés par le package de débogage. Le DE doit se trouver sur la liste autorisée, sans quoi il ne sera pas attaché au programme.

 Une fois que l’identité de l’Allemagne est connue, le SDM est prêt à attacher au programme.

## <a name="see-also"></a>Voir aussi
- [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
- [Attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md)
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)