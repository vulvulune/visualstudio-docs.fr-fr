---
title: Lorsque j'appelle une fonction des centaines de fois, comment puis-je savoir quel appel a échoué ? | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2655205c3e0c34d1063ce54793f49330ab7ccc2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501691"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Lorsque j'appelle une fonction des centaines de fois, comment puis-je savoir quel appel a échoué ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [lorsque vous appelez une fonction des centaines de fois, comment puis-je savoir quel appel a échoué ?](https://docs.microsoft.com/visualstudio/debugger/when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed-q).  
  
Description du problème  
 Mon programme échoue lors de l'appel à une certaine fonction, `CnvtV`. Mais cet échec survient probablement après plusieurs centaines d'appels à la fonction par le programme. Si je définis un point d'arrêt d'emplacement sur `CnvtV`, le programme s'arrête à chaque appel de cette fonction, ce que je veux éviter. J'ignore quelles conditions ont provoqué l'échec de l'appel et je ne peux donc pas définir un point d'arrêt conditionnel. Que puis-je faire ?  
  
## <a name="solution"></a>Solution  
 Vous pouvez définir un point d’arrêt sur la fonction avec le **nombre d’accès** champ à une valeur très élevée qu’il ne sera jamais atteint. Dans ce cas, étant donné que vous estimez que la fonction `CnvtV` est appelée plusieurs centaines de fois, vous pouvez définir **nombre d’accès** au moins 1 000. Exécutez ensuite le programme et patientez jusqu'à l'échec de l'appel. Lorsqu'il échoue, ouvrez la fenêtre Points d'arrêt et examinez la liste des points d'arrêt. Le point d'arrêt que vous avez défini sur `CnvtV` apparaît, suivi du nombre d'accès et du nombre d'itérations restantes :  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Vous savez à présent que la fonction a échoué au 101e appel. Si vous réinitialisez le point d'arrêt avec un nombre d'accès égal à 101, puis que vous réexécutez le programme, ce dernier s'arrête au niveau de l'appel à `CnvtV` qui a provoqué son échec.  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Définition des points d’arrêt](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Débogage du code natif](../debugger/debugging-native-code.md)


