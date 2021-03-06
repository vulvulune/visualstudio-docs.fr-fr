---
title: 'Erreur : Le service débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e828d0150e3519e588702be95111126fd1e2c04
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069235"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Erreur : Le service de débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur signifie que le service Débogueur distant Visual Studio s'exécute sous un compte d'utilisateur qui ne peut pas être authentifié lorsqu'il se connecte à l'ordinateur à partir duquel vous déboguez.  
  
 Le tableau suivant répertorie les comptes autorisés à accéder à l'ordinateur:  
  
|||||  
|-|-|-|-|  
||Compte LocalSystem|Compte de domaine|Comptes locaux avec les mêmes nom d'utilisateur et mot de passe sur les deux ordinateurs|  
|Deux ordinateurs sur le même domaine|Oui|Oui|Oui|  
|Deux ordinateurs sur des domaines qui ont un niveau de confiance bidirectionnel|Non|Non|Oui|  
|Un ordinateur, ou les deux, dans un groupe de travail|Non|Non|Oui|  
|Ordinateurs sur des domaines différents|Non|Non|Oui|  
  
 En outre :  
  
- Le compte sous lequel vous exécutez le service Débogueur distant Visual Studio doit être un administrateur sur l'ordinateur distant afin qu'il puisse déboguer tout processus.  
  
- Le privilège `Log on as a service` doit également être accordé au compte sur l’ordinateur distant qui utilise l’outil d’administration **Stratégie de sécurité locale**.  
  
- Si vous utilisez un compte local pour accéder à l'ordinateur, vous devez exécuter le service Débogueur distant Visual Studio sous un compte local.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que le service Débogueur distant Visual Studio est correctement installé sur l'ordinateur distant. Pour plus d’informations, consultez [définir Up the Remote Tools sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2. Exécutez le service Débogueur distant sous un compte qui peut accéder à l'ordinateur hôte du débogueur, comme indiqué dans le tableau précédent.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Pour ajouter le privilège « Ouvrir une session en tant que service »  
  
1. Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.  
  
2. Dans le Panneau de configuration, cliquez sur **Affichage classique**, si nécessaire.  
  
3. Double-cliquez sur **Outils d'administration**.  
  
4. Dans la fenêtre Outils d’administration, double-cliquez sur **Stratégie de sécurité locale**.  
  
5. Dans la fenêtre **Paramètres de sécurité locaux**, développez le dossier **Stratégies locales**.  
  
6. Cliquez sur **Attribution des droits utilisateur**.  
  
7. Dans la colonne **Stratégie**, double-cliquez sur **Ouvrir une session en tant que service** pour afficher les affectations de la stratégie de groupe locale dans la boîte de dialogue **Ouvrir une session en tant que service**.  
  
8. Pour ajouter de nouveaux utilisateurs, cliquez sur le bouton **Ajouter un utilisateur ou un groupe**.  
  
9. Après avoir ajouté les utilisateurs de votre choix, cliquez sur **OK**.  
  
### <a name="to-work-around-this-error"></a>Pour contourner cette erreur  
  
- Exécutez le Remote Debugging Monitor comme une application au lieu d'un service.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage à distance et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
