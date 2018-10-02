---
title: Propriétés d’éléments des diagrammes d’activités UML | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
- activity diagrams, properties
ms.assetid: 9849d45e-65d5-46bd-a319-757e90b7c748
caps.latest.revision: 19
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c50a84f9e3c5425459ea458c3f6bbc282d64b0b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494131"
---
# <a name="properties-of-elements-on-uml-activity-diagrams"></a>Propriétés d'éléments sur les diagrammes d'activités UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [propriétés d’éléments des diagrammes d’activités UML](https://docs.microsoft.com/visualstudio/modeling/properties-of-elements-on-uml-activity-diagrams).  
  
Sur un diagramme d'activités UML, chaque élément du diagramme possède des propriétés. Pour afficher les propriétés d’un élément, cliquez sur l’élément sur le diagramme ou dans **Explorateur de modèles UML** puis cliquez sur **propriétés**. Les propriétés s’affichent dans le **propriétés** fenêtre.  
  
> [!NOTE]
>  Cette rubrique traite des propriétés d'éléments sur les diagrammes d'activités UML. Pour plus d’informations sur la lecture des diagrammes d’activités UML, consultez [diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md). Pour plus d’informations sur la façon de dessiner des diagrammes d’activités UML, consultez [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propriétés des éléments  
  
|Propriété|Par défaut|Élément|Description|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nom par défaut|Tous|Identifie l'élément.|  
|**Nom qualifié**|Package :: Nom|Tous|Identifie l'élément de manière unique. A pour préfixe le nom qualifié du package qui le contient.|  
|**Éléments de travail**|{0} associé|Tous|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|  
|**Description**|(aucune)|Tous|Vous pouvez consigner des remarques générales concernant l'élément.|  
|**Couleur**|(valeur par défaut pour le type)|Tous|Couleur de la forme.|  
|**Corps**|(aucune)|Action|Spécifie l'action de manière détaillée.|  
|**Language**|(aucune)|Action|Langage de l'expression dans le corps.|  
|**Post-conditions locales**|(aucune)|Action, Envoyer, Accepter, Appeler un comportement, Appeler une opération|Contraintes qui doivent être satisfaites à la fin de l'exécution. Objectif atteint par l'action.|  
|**Conditions préalables locales**|(aucune)|Action, Envoyer, Accepter, Appeler un comportement, Appeler une opération|Contraintes qui doivent être satisfaites avant le début de l'exécution.|  
|**Est synchrone**|True|Appeler un comportement, Appeler une opération|-Si la valeur est true, l’action patiente jusqu'à ce que l’activité se termine.|  
|**Comportement**|(aucune)|Appeler un comportement|-L’activité appelée.|  
|**Opération**|(aucune)|Appeler une opération|-L’opération appelée.|  
|**Est désorganiser**|False|Accepter un événement|-Si la valeur est true, il peut y avoir plusieurs broches de sortie typées et les données sont démarshalées dessus. Si la valeur est false, toutes les données apparaissent sur une seule broche.|  
|**Limite supérieure**|**\***|Nœud d'objet, Paramètre d'activité|**0** indique que les données doivent passer directement le long du flux.<br /><br /> **\*** Indique que les données peuvent être stockées dans le flux.|  
|**Sélection**|(aucune)|Nœud d'objet, Paramètre d'activité, Broche d'entrée, Broche de sortie, Flux d'objet|Appelle un processus qui filtre les données. Ce processus peut être défini dans un autre diagramme.|  
|**Classement**|(aucune)|Nœud d'objet, Paramètre d'activité, Broche d'entrée, Broche de sortie|-Comment plusieurs jetons sont stockés.|  
|**Est le contrôle**|False|Broche d'entrée, broche de sortie|-Si la valeur est true, le flux sur cette broche est un flux de contrôle. Si la valeur est false, il s'agit d'un flux d'objet.|  
|**Type**|(aucune)|Broche d'entrée, Broche de sortie, Nœud d'objet, Paramètre d'activité|-Le type des objets transmis.<br />-Le type peut être un type primitif tel qu’Integer ou un classifieur défini ailleurs dans le modèle. Si vous entrez le nom d’un type qui n’est pas défini, il apparaît dans le **Types non spécifiés** section de l’Explorateur de modèles UML.|  
|**Multiplicité**|1|Broche d'entrée, broche de sortie|-Peut être une valeur unique ou une plage `[n..m]`.<br />-Limite inférieure `n` -l’action ne peut pas démarrer (pour une broche d’entrée) ou arrêter (pour une broche de sortie) jusqu'à ce qu’il existe `n` objets en attente sur le code confidentiel.<br />-Limite supérieure `m` -l’action ne peut pas consommer, ni produire plus de `m` objets en une seule exécution. * signifie qu'il n'y a aucune limite.|  
|**transformation**|(aucune)|Flux d'objet|-Appelle un processus qui transforme les données. Ce processus peut être défini dans un autre diagramme.|  
|**Est de multidiffusion**|False|Flux d'objet|-Indique qu’il peut exister plusieurs objets ou composants destinataires.|  
|**Est MultiReceive**|False|Flux d'objet|-Indique qu’il peut exister plusieurs objets ou composants destinataires.|  
|**Is Single Execution**|False|Diagramme d'activités|-If définie, il existe au plus une exécution de ce diagramme à la fois.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes d’activités UML : référence](../modeling/uml-activity-diagrams-reference.md)   
 [Diagrammes d’activités UML : conseils](../modeling/uml-activity-diagrams-guidelines.md)


