---
title: Boîte de dialogue de CorrelationInitializers ajouter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c90a2d0e0297a00454e38f428093a2f2db1e46d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977474"
---
# <a name="add-correlationinitializers-dialog-box"></a>Boîte de dialogue Ajouter des initialiseurs de corrélation
Le **ajouter des initialiseurs de corrélation** boîte de dialogue est utilisée dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] pour configurer le **CorrelationInitializers** propriétés de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, et <xref:System.ServiceModel.Activities.ReceiveReply> activités. [!INCLUDE[crabout](../includes/crabout-md.md)] les concepteurs d’activités qui utilisent cette zone, consultez la [envoyer](../workflow-designer/send-activity-designer.md), [réception](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), et [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) rubriques.  
  
 Les initialiseurs de corrélation dans la collection spécifiée avec cette boîte de dialogue peuvent initialiser des corrélations basées sur une requête, de contexte, de contexte de rappel ou de demande-réponse entre les activités de messagerie.  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **ajouter des initialiseurs de corrélation** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Ajouter un initialiseur**|Cliquez sur le **ajouter initialize** case pour ajouter un initialiseur supplémentaire à la collection.|  
|**Type de corrélation**|Spécifie le type d'initialiseur de corrélation. Quatre types sont disponibles :<br /><br /> 1.  Initialiseur de corrélation de rappel pour spécifier un <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Initialiseur de corrélation de contexte pour spécifier un <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Initialiseur de corrélation demande-réponse pour spécifier un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Initialiseur de corrélation de requête pour spécifier un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Pour modifier le **type de corrélation**<br /><br /> 1.  Onglet à la ligne spécifique dans le **ajouter un initialiseur** DataGrid.<br />2.  Appuyez sur Ctrl + Tab pour définir le focus sur **CorrelationTypeComboBox**<br />3.  Appuyez sur Alt + flèche bas pour afficher le **ComboBox** et le modifier.|  
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation de messages entrants et sortants. Cette liste est valide uniquement lors de l'utilisation de types <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Pour lancer la boîte de dialogue Ajouter des initialiseurs de corrélation  
 Le **ajouter des initialiseurs de corrélation** boîte de dialogue est utilisée par le **envoyer**, **réception**, **ReceiveAndSendReply**, et  **SendAndReceiveReply** concepteurs. L’accès à celles-ci est similaire dans chaque cas et le cas qui implique la **réception** concepteur est utilisé ici pour illustrer la procédure.  
  
 Le **réception** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le **réception** Concepteur d’activités et cliquez sur le bouton de sélection en regard du texte (Collection) pour le **CorrelationInitializers** propriété dans la grille des propriétés pour le **ajouter Initialiseurs de corrélation** la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser la corrélation, boîte de dialogue](../workflow-designer/initialize-correlation-dialog-box.md)