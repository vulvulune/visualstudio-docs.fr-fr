---
title: Comment puis-je utiliser les fenêtres du débogueur pendant le débogage d'un programme d'avant-plan ? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8ab8427c144d56461aa52a535acbe618b68d9994
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953943"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Comment puis-je utiliser les fenêtres du débogueur pendant le débogage d'un programme d'avant-plan ?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Description du problème  
 J'essaie de corriger un problème de peinture de l'écran. Pour observer ce problème, je dois conserver mon programme au premier plan. Autrement dit, je n'ai pas accès aux fenêtres de débogage. Que puis-je faire ?  
  
## <a name="solution"></a>Solution  
 Si vous disposez d'un autre ordinateur, vous pouvez recourir au débogage distant. Dans une installation comportant deux ordinateurs, vous pouvez observer la peinture de l'écran sur l'ordinateur distant, tout en utilisant le débogueur sur l'hôte. Pour plus d’informations sur le débogage à distance, consultez [configuration du débogage distant](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
## <a name="see-also"></a>Voir aussi  
 [Questions fréquentes (FAQ) sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
