---
title: Fonction attendue | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4442143b2766ed3608a852d0f811a6b943fd19df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007104"
---
# <a name="function-expected"></a>Fonction attendue
Soit vous avez tenté d’appeler une de la **prototype de fonction** méthodes sur un objet qui n’était pas un `Function` objet, ou utilisé un objet dans un contexte d’appel de fonction. Par exemple, le code suivant génère cette erreur, car **exemple** n’est pas une fonction.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Appelez uniquement **prototype de fonction** méthodes sur `Function` objets.  
  
- Vérifiez que vous utilisez l’opérateur d’appel de fonction `()` pour appeler les fonctions uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)