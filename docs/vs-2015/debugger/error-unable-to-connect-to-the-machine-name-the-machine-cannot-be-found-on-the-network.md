---
title: 'Erreur : Impossible de se connecter à la machine &lt;nom&gt;. L’ordinateur est introuvable sur le réseau. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b1cef49425540980938b4d84a1825c171b271b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045692"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erreur : Impossible de se connecter à la machine &lt;nom&gt;. L’ordinateur est introuvable sur le réseau.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce problème se produit si l'une des conditions suivantes est remplie :  
  
- Votre connexion à l'ordinateur distant a été interrompue.  
  
- Votre compte d'utilisateur sur l'ordinateur distant est désactivé.  
  
- Votre mot de passe sur l'ordinateur distant a expiré.  
  
### <a name="to-resolve-this-behavior"></a>Pour résoudre ce problème  
  
- Assurez-vous que l'ordinateur local et l'ordinateur distant se trouvent dans le même réseau. Pour cela, à l'aide de l'Explorateur Microsoft Windows (ou de l'Explorateur de fichiers), tentez d'accéder à l'ordinateur distant.  
  
     — et —  
  
- Assurez-vous que le compte d'utilisateur que vous utilisez pour vous connecter à l'ordinateur distant est activé.  
  
     — et —  
  
- Assurez-vous que le mot de passe que vous utilisez pour vous connecter à l'ordinateur distant est valide et n'a pas expiré.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les outils à distance sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
