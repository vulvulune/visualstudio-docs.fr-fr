---
title: 'Comment : afficher des Documents de Script | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc24c5e9c2332516cbf939e14581a2df7bea44eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505255"
---
# <a name="how-to-view-script-documents"></a>Comment : afficher les documents de script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : afficher les Documents de Script](https://docs.microsoft.com/visualstudio/debugger/how-to-view-script-documents).  
  
Dans les versions antérieures de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], les fichiers de script côté client générés depuis un script côté serveur s'affichaient dans la fenêtre Explorateur de scripts. La fenêtre Explorateur de scripts était souvent masquée et la disponibilité du script côté client n'était pas toujours évidente.  
  
 Dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], les fichiers de script côté client générés depuis un script côté serveur s'affichent dans l'Explorateur de solutions visible par défaut. La fenêtre Explorateur de scripts a été supprimée.  
  
 Les fichiers de script côté client sont visibles uniquement lorsque vous êtes en mode débogage ou en mode arrêt. Ils apparaissent dans le **Documents de Script** nœud.  
  
 Les fichiers de script côté serveur sont toujours visibles. Ils apparaissent dans le  **\<chemin du site Web >** nœud. Le nom du nœud ressemble à cet exemple : `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Pour afficher un document de script côté serveur  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le  **\<chemin du site Web >** nœud.  
  
2.  Double-cliquez sur le fichier de script que vous souhaitez afficher.  
  
     Le fichier de script côté serveur s'ouvre dans une fenêtre source.  
  
### <a name="to-view-a-client-side-script-document"></a>Pour afficher un document de script côté client  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le **Documents de Script** nœud.  
  
2.  Double-cliquez sur le fichier de script que vous souhaitez afficher.  
  
     Le fichier de script côté client s'ouvre dans une fenêtre source.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)


