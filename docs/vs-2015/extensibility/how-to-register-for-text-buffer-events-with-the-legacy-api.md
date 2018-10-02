---
title: 'Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b98c6a084e8d77b9c85d56da95ec9abdcd469192
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502658"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](https://docs.microsoft.com/visualstudio/extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api).  
  
Si vous accédez à la mémoire tampon de texte à l’aide de l’API héritée, vous devez vous inscrire pour les événements de mémoire tampon de texte comme indiqué dans la procédure suivante.  
  
### <a name="to-advise-text-buffer-events"></a>Pour signaler des événements de mémoire tampon de texte  
  
1.  À partir d’un pointeur vers une des interfaces sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, appelez `QueryInterface` pour un pointeur vers <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> (méthode) et passez l’ID d’interface des événements pour lesquels vous souhaitez inscrire.  
  
     Par exemple, si vous souhaitez inscrire pour <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, puis passer dans une interface ID de IID_IVsTextLinesEvents.  
  
     La mémoire tampon de texte retourne un pointeur vers le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour l’objet de point de connexion approprié.  
  
3.  À l’aide de ce pointeur, appelez le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> méthode, en passant un pointeur à votre implémentation de l’interface d’événements pour lequel vous souhaitez enregistrer, par exemple, le `IVsTextLinesEvents` interface.  
  
     L’environnement retourne un cookie que vous pouvez ensuite utiliser pour cesser d’écouter les événements en appelant le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de mémoire tampon de texte dans l’API héritée](../extensibility/text-buffer-events-in-the-legacy-api.md)
