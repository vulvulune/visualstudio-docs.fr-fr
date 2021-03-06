---
title: Attachement après un lancement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437436"
---
# <a name="attaching-after-a-launch"></a>Attachement après un lancement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une fois un programme a été lancé, la session de débogage est prête à attacher le moteur de débogage (dé) dudit programme.  
  
## <a name="design-decisions"></a>Décisions de conception  
 Étant donné que la communication est plus facile au sein d’un espace d’adressage partagé, vous devez décider s’il est plus logique pour faciliter la communication entre la session de débogage et l’Allemagne, ou entre l’Allemagne et le programme. Le choix entre les éléments suivants :  
  
- S’il est plus logique pour faciliter la communication entre la session de débogage et l’Allemagne, la session de débogage crée l’Allemagne et vous demande de l’Allemagne à joindre au programme. Cela laisse la session de débogage et DE ensemble dans un espace d’adressage et l’environnement d’exécution et le programme dans un autre.  
  
- S’il est plus logique pour faciliter la communication entre l’Allemagne et le programme, puis l’environnement d’exécution crée l’Allemagne. Cela laisse le SDM dans un espace d’adressage et l’Allemagne, environnement d’exécution et programme ensemble dans un autre. Ceci est typique d’un dé est implémentée avec un interpréteur pour exécuter des langages de script.  
  
    > [!NOTE]
    > Comment le D’attache au programme est dépend de l’implémentation. Communication entre l’Allemagne et le programme est également dépend de l’implémentation.  
  
## <a name="implementation"></a>Implémentation  
 Par programmation, lorsque le Gestionnaire de session de débogage (SDM) reçoit d’abord le [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme doit être lancé, il appelle le [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) méthode, en lui transmettant un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objet, qui est ultérieur utilisé pour transmettre des événements de débogage vers le SDM. Le `IDebugProgram2::Attach` méthode appelle ensuite la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode). Pour plus d’informations sur la façon dont le SDM reçoit le `IDebugProgram2` l’interface, consultez [notification du Port](../../extensibility/debugger/notifying-the-port.md).  
  
 Si votre dé doit s’exécuter dans le même espace d’adressage que le programme en cours de débogage, en règle générale, car le DE fait partie d’un interpréteur exécutant un script, le `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_FALSE`, indiquant qu’il terminé le processus d’attachement.  
  
 Si, en revanche, l’Allemagne s’exécute dans l’espace d’adressage du SDM, la `IDebugProgramNodeAttach2::OnAttach` méthode retourne `S_OK` ou [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface n’est pas implémentée tout en la [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) objet associée au programme en cours de débogage. Dans ce cas, le [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée par la suite pour terminer l’opération d’attachement.  
  
 Dans ce cas, vous devez appeler le [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) méthode sur le `IDebugProgram2` objet qui a été passé à la `IDebugEngine2::Attach` (méthode), le magasin de la `GUID` dans le programme local de l’objet et retournez cette `GUID` lorsque le `IDebugProgram2::GetProgramId` méthode est appelée par la suite sur cet objet. Le `GUID` est utilisé pour identifier de manière unique le programme entre les différents composants de débogage.  
  
 Notez que dans le cas de la `IDebugProgramNodeAttach2::OnAttach` méthode retournant `S_FALSE`, le `GUID` à utiliser pour le programme est passé à cette méthode, il le `IDebugProgramNodeAttach2::OnAttach` méthode qui définit la `GUID` sur l’objet de programme local.  
  
 L’Allemagne est maintenant attaché au programme et prêt à envoyer les événements de démarrage.  
  
## <a name="see-also"></a>Voir aussi  
 [Attachement directement à un programme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notification du Port](../../extensibility/debugger/notifying-the-port.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attacher](../../extensibility/debugger/reference/idebugengine2-attach.md)
