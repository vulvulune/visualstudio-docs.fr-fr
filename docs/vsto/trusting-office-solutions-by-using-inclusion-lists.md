---
title: Approuver des solutions Office à l’aide de listes d’inclusion
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 34b4ed5dbc0996239e73db38f1d6bea9e43d6de4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978300"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Approuver des solutions Office à l’aide de listes d’inclusion
  Les listes d’inclusion permettent aux utilisateurs d’approuver des solutions Office signées avec un certificat qui identifie l’éditeur. Elles sont propres à l’utilisateur et elles peuvent servir aux personnalisations au niveau du document et aux compléments VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Quand un utilisateur démarre une solution Office qui n’a pas été approuvée pour lui, il est invité à prendre une décision en matière de sécurité avec une invite d’approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Si l’utilisateur décide d’approuver la solution, la personnalisation s’exécute et il ne reçoit plus d’invite au prochain démarrage de la solution.

## <a name="inclusion-list-and-windows-installer"></a>Liste d’inclusion et le programme d’installation de Windows
 Installation des solutions Office dans le *Program Files* directory à l’aide du programme d’installation de Windows requiert des droits d’administrateur. Pour les solutions Office dans le *Program Files* répertoire, Visual Studio Tools pour Office runtime ne vérifie plus la liste d’inclusion car les solutions Office ont déjà été accordées l’autorisation FullTrust.

## <a name="clickonce-trust-prompt"></a>Invite d’approbation ClickOnce
 À l’aide de l’implémentation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] des solutions Office, les administrateurs peuvent configurer le niveau d’invite d’approbation pour autoriser les invites, désactiver les invites ou exiger un certificat de confiance. Cette configuration s’effectue à l’aide d’une clé de Registre qui contrôle l’accès à la liste d’inclusion.

 Si l’invite est désactivée, seules les solutions qui possèdent un certificat de confiance connu peuvent être installées. Si le niveau d’invite défini est Authenticode requis, la solution doit être signée avec un certificat émis par une autorité connue, mais elle ne requiert pas un certificat lié à une autorité racine approuvée (un certificat de confiance). Si l’invite est autorisée, la solution peut être signée avec un certificat dont l’identité est inconnue. Dans ce scénario, la décision d’approbation est soumise à l’utilisateur final et un certificat temporaire suffit pour installer une solution.

 Pour plus d'informations, voir [Procédure : Configurer la sécurité de liste d’inclusion](../vsto/how-to-configure-inclusion-list-security.md) et le tableau 2, intitulé invitant au niveau du Registre clé valeur effets du lancement, dans [éditeurs dignes de confiance ClickOnce configurer](http://go.microsoft.com/fwlink/?LinkId=94774).

## <a name="structure-of-the-inclusion-list"></a>Structure de la liste d’inclusion
 Une entrée de liste d’inclusion valide comporte deux parties : un chemin vers le manifeste de déploiement et la clé publique utilisée pour signer la solution. Une fois qu’une solution est ajoutée à la liste d’inclusion, elle est considérée comme approuvée. Quand la solution Office s’exécute, l’application Office compare la clé publique figurant dans la liste d’inclusion à la clé de signature figurant dans le manifeste de déploiement pour vérifier que la solution qui est en cours d’exécution est identique à la version d’origine approuvée.

## <a name="see-also"></a>Voir aussi
- [Accorder votre confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)
- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)
