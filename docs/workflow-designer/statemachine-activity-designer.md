---
title: Concepteur de flux de travail - Concepteur d’activités StateMachine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 59b1a194f4f301bd3080820b56c89044315c66e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809391"
---
# <a name="statemachine-activity-designer"></a>Concepteur d'activités StateMachine

L'activité <xref:System.Activities.Statements.StateMachine> contient une collection d'états et modélise les workflows à l'aide du modèle familier de machine à états.

## <a name="using-the-statemachine-activity-designer"></a>Utilisation du concepteur d'activités StateMachine

Pour ajouter un <xref:System.Activities.Statements.StateMachine> activité, faites glisser le **StateMachine** Concepteur d’activités à partir de la **Machine à états** section de la **boîte à outils** glisser vers le Concepteur de flux de travail surface. Pour ajouter un état de l’enfant à cette <xref:System.Activities.Statements.StateMachine> activité, faites glisser un <xref:System.Activities.Statements.State> ou <xref:System.Activities.Core.Presentation.FinalState> à partir de la **boîte à outils** et déposez-le sur le **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité StateMachine dans le concepteur de workflow

Le tableau suivant indique les propriétés  <xref:System.Activities.Statements.StateMachine> qui peuvent être définies à l'aide du concepteur de workflow et explique comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.StateMachine> dans l'en-tête. La valeur par défaut est **StateMachine**. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités. <xref:System.Activities.Activity.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)