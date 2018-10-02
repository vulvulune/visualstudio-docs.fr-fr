---
title: Persistance de projet | Microsoft Docs
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
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5c44fde30720fe17f4b9f3a5d679750ccb78ee6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507963"
---
# <a name="project-persistence"></a>Persistance d’un projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [persistance d’un projet](https://docs.microsoft.com/visualstudio/extensibility/internals/project-persistence).  
  
La persistance est une considération de conception clés pour votre projet. La plupart des projets utilisent des éléments de projet qui représentent des fichiers ; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prend également en charge les projets dont les données sont non basée sur un fichier. Les deux fichiers détenus par le projet et le fichier projet doivent être persistante. L’IDE indique le projet pour enregistrer lui-même ou un élément de projet.  
  
 Modèles de projets sont transmises à la fabrique de projets. Les modèles doivent prendre en charge l’initialisation de tous les éléments de projet en fonction des spécifications du type de projet spécifique. Ces modèles ultérieurement peuvent être enregistrés en tant que fichiers de projet et gérés par l’IDE à travers la solution. Pour plus d’informations, consultez [création projet Instances par à l’aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) et [Solutions](../../extensibility/internals/solutions.md).  
  
 Éléments de projet peuvent être basée sur le fichier ou non basée sur un fichier :  
  
-   Éléments basés sur le fichier peuvent être local ou distant. Dans les projets Web en c#, par exemple, les connexions aux fichiers sur un système distant conservent localement, tandis que les fichiers eux-mêmes sont conservées sur le système distant.  
  
-   Éléments non basés sur des fichiers peuvent enregistrer des éléments dans une base de données ou le référentiel.  
  
## <a name="commit-models"></a>Valider des modèles  
 Après avoir décidé où se trouvent les éléments de projet, vous devez choisir le modèle de validation approprié. Par exemple, dans un modèle basé sur fichier avec des fichiers locaux, chaque projet peut être enregistré autonome. Dans un modèle de référentiel, vous pouvez enregistrer plusieurs éléments dans une seule transaction. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
 Pour déterminer les extensions de nom de fichier, implémentent des projets le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface, qui fournit des informations permettant au client d’un objet d’implémenter le **Enregistrer sous** boîte de dialogue, autrement dit, pour renseigner le **enregistrer en tant que Type**  déroulante Lister et gérer l’extension de nom de fichier initial.  
  
 Les appels de l’IDE le `IPersistFileFormat` interface sur le projet pour indiquer que le projet doit conserver son projet éléments selon les besoins. Par conséquent, l’objet propriétaire de tous les aspects de son format et le format de fichier. Cela inclut le nom du format de l’objet.  
  
 Dans le cas où les éléments ne sont pas des fichiers, `IPersistFileFormat` est toujours comment non fichier basé sur les éléments sont conservés. Fichiers, tels que les fichiers .vbp pour projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projets ou .vcproj fichiers pour [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projets, doit également être conservé.  
  
 Pour enregistrer les actions, l’IDE examine la table de document en cours d’exécution (RDT) et la hiérarchie transmet les commandes pour le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> méthode est implémentée pour déterminer si l’élément a été modifiée. Si l’élément a, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> méthode est implémentée pour enregistrer l’élément modifié.  
  
 Les méthodes sur le `IVsPersistHierarchyItem2` interface servent à déterminer si un élément peut être rechargé et, si l’élément peut être, à le recharger. En outre, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> méthode peut être implémentée pour les éléments modifiés sont ignorés sans être enregistré.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
