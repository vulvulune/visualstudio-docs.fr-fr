---
title: Espion express, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a4bc73046ca32645ffcdc8c3f2978c9245aaec6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668065"
---
# <a name="quick-watch-command"></a>Espion express, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Affiche le texte sélectionné ou spécifié dans le champ Expression de la boîte de dialogue [Espion express](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Vous pouvez utiliser cette boîte de dialogue pour calculer la valeur actuelle d’une variable ou d’une expression reconnue par le débogueur, ou le contenu d’un Registre. Vous pouvez aussi modifier la valeur de toute variable non constante ou le contenu de tout Registre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Optionnel. Texte à ajouter à la boîte de dialogue **Espion express**.  
  
## <a name="remarks"></a>Remarques  
 Si l’argument `text` est omis, le texte ou mot sélectionné au niveau du curseur est ajouté dans la fenêtre Espion.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la boîte de dialogue Espion express](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
