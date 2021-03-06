---
title: Boîte de dialogue Éditeur de Collection de type | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66cd861fcf92c400e1499834ea6255df4d5cf0fa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432356"
---
# <a name="type-collection-editor-dialog-box"></a>Boîte de dialogue Éditeur de collections de types
Le **éditeur de collections de Type** boîte de dialogue est utilisée pour ajouter des types connus le **envoyer** et **réception** activités. Cette boîte de dialogue est également utilisé pour ajouter des arguments de type générique pour le **InvokeMethod** activité. Lorsqu’il est utilisé pour le **envoyer** et **réception** activités à ajouter des types connus, le **éditeur de collections de Type** boîte de dialogue nécessite les ajouts de type unique. Si un type en double est ajouté et la modification est validée en cliquant sur **OK**, un message d’erreur est retourné. Lorsqu’il est utilisé pour le **InvokeMethod** activité pour ajouter des arguments de type générique, le **éditeur de collections de Type** boîte de dialogue permet l’ajout de types en double.  
  
> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] les types connus, consultez [Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **Type Collection** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Liste de types**|Liste des types qui ont été ajoutés ou supprimés.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Pour afficher l’Éditeur de collections de types  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Pour afficher l'Éditeur de collections de types pour les activités Send et Receive  
  
1. Sélectionnez le **envoyer** ou **réception** activité en mode design.  
  
2. Appuyez sur **F4** pour faire apparaître le **propriétés** fenêtre.  
  
3. Dans le **propriétés** , cliquez sur le bouton de sélection en regard du **KnownTypes** propriété.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Pour afficher l'Éditeur de collections de types pour l'activité InvokeMethod  
  
1. Sélectionnez le **InvokeMethod** activité en mode design.  
  
2. Appuyez sur **F4** pour faire apparaître le **propriétés** fenêtre.  
  
3. Dans le **propriétés** , cliquez sur le bouton de sélection en regard du **GenericTypeArguments** propriété.