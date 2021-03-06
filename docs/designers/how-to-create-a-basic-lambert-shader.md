---
title: 'Procédure : Créer un nuanceur Lambert de base'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 595f44403d5dc8062bea86504a74ed0d7e0ee565
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893960"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Procédure : Créer un nuanceur Lambert de base

Cet article indique comment utiliser le concepteur Shader et DGSL (Directed Graph Shader Language) pour créer un nuanceur d’éclairage implémentant le modèle d’éclairage Lambert classique.

## <a name="the-lambert-lighting-model"></a>Modèle d’éclairage Lambert

Le modèle d’éclairage Lambert intègre un éclairage ambiant et directionnel pour ombrer des objets dans une scène 3D. Les composants ambiants fournissent un niveau de base d’éclairage de la scène 3D. Les composants directionnels fournissent un éclairage supplémentaire provenant de sources de lumière (éloignées) directionnelles. L’éclairage ambiant affecte également toutes les surfaces de la scène, quelle que soit leur orientation. Pour une surface donnée, il s’agit d’un produit de la couleur ambiante de la surface et de la couleur et de l’intensité de l’éclairage ambiant de la scène. L’éclairage directionnel affecte différemment chaque surface de la scène, selon l’orientation de la surface par rapport à la direction de la source de lumière. Il s’agit d’un produit de la couleur diffuse et de l’orientation de la surface, et de la couleur, de l’intensité et de la direction des sources de lumière. Les surfaces qui font directement face à la source de lumière reçoivent la contribution maximale tandis que celles qui lui tournent le dos ne reçoivent aucune contribution. Dans le modèle d’éclairage Lambert, le composant ambiant et un ou plusieurs composants directionnels sont combinés pour déterminer la contribution de couleur diffuse totale pour chaque point de l’objet.

Avant de commencer, assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.

1. Créez un nuanceur DGSL à utiliser. Pour plus d’informations sur l’ajout d’un nuanceur DGSL à votre projet, consultez la section Prise en main de l’article [Concepteur de nuanceur](../designers/shader-designer.md).

2. Déconnectez le nœud **Couleur du point** du nœud **Couleur finale**. Choisissez le terminal **RVB** du nœud **Couleur du point**, puis choisissez **Rompre les liaisons**. Laissez le terminal **Alpha** connecté.

3. Ajoutez un nœud **Lambert** au graphique. Dans la **Boîte à outils**, sous **Utilitaire**, sélectionnez **Lambert** et déplacez-le vers l’aire de conception. Le nœud lambert calcule la contribution de couleur diffuse totale du pixel, en fonction des paramètres d’éclairage ambiant et diffus.

4. Connectez le nœud **Couleur du point** au nœud **Lambert**. En mode **Sélection**, déplacez le terminal **RVB** du nœud **Couleur du point** vers le terminal **Couleur diffuse** du nœud **Lambert**. Cette connexion fournit au nœud lambert la couleur diffuse interpolée du pixel.

5. Connectez la valeur de couleur calculée à la couleur finale. Déplacez le terminal **Sortie** du nœud **Lambert** vers le terminal **RVB** du nœud **Couleur finale**.

   L’illustration suivante présente le graphique du nuanceur terminé ainsi qu’un aperçu du nuanceur appliqué à un modèle de théière.

> [!NOTE]
> Pour mettre en évidence l’effet du nuanceur dans cette illustration, la couleur orange a été spécifiée à l’aide du paramètre **MaterialDiffuse** du nuanceur. Un jeu ou une application peuvent utiliser ce paramètre pour fournir une valeur de couleur unique pour chaque objet. Pour plus d’informations sur les paramètres de matériau, consultez la section Aperçu des nuanceurs de l’article [Concepteur de nuanceur](../designers/shader-designer.md).

 ![Graphique du nuanceur et un aperçu de ses effets.](../designers/media/digit-lambert-effect-graph.png)

 Certaines formes peuvent fournir de meilleurs aperçus pour certains nuanceurs. Pour plus d’informations sur l’aperçu des nuanceurs dans le concepteur de nuanceur, consultez la section Aperçu des nuanceurs de l’article [Concepteur de nuanceur](../designers/shader-designer.md).

 L’illustration suivante montre le nuanceur décrit dans ce document appliqué à un modèle 3D.

 ![Éclairage Lambert appliqué à un modèle.](../designers/media/digit-lambert-effect-result.png)

 Pour plus d’informations sur l’application d’un nuanceur à un modèle 3D, consultez [Guide pratique pour appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour appliquer un nuanceur à un modèle 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Guide pratique pour exporter un nuanceur](../designers/how-to-export-a-shader.md)
- [Guide pratique pour créer un nuanceur Phong de base](../designers/how-to-create-a-basic-phong-shader.md)
- [Concepteur Shader](../designers/shader-designer.md)
- [Nœuds du concepteur Shader](../designers/shader-designer-nodes.md)