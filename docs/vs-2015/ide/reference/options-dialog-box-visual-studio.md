---
title: Options, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bf656ed94b232e2ce19986696f4155dc225c8ad0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433635"
---
# <a name="options-dialog-box-visual-studio"></a>Options, boîte de dialogue (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La boîte de dialogue **Options** vous permet de configurer l’environnement de développement intégré (IDE) selon vos besoins. Par exemple, vous pouvez établir un emplacement d’enregistrement par défaut pour vos projets, modifier l’apparence et le comportement par défaut des fenêtres et créer des raccourcis pour les commandes fréquemment utilisées. Il existe également des options spécifiques à vos plateforme et langage de développement. Vous pouvez accéder aux **Options** à partir du menu **Outils**.

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Présentation de la boîte de dialogue Options
 La boîte de dialogue **Options** est divisée en deux parties : un volet de navigation à gauche et une zone d’affichage à droite. Le contrôle d’arborescence dans le volet de navigation comprend des nœuds de dossier, tels qu’Environnement, Éditeur de texte, Projets et solutions et Contrôle de code source. Développez un nœud de dossier pour afficher les pages d’options qu’il contient. Quand vous sélectionnez le nœud pour une page particulière, ses options apparaissent dans la zone d’affichage.

 Les options d’une fonctionnalité IDE n’apparaissent pas dans le volet de navigation tant que cette fonctionnalité n’est pas chargée en mémoire. Ainsi, les options affichées peuvent différer d’une session à l’autre. Quand vous créez un projet ou exécutez une commande qui utilise une application particulière, les nœuds correspondant aux options appropriées sont ajoutés à la boîte de dialogue Options. Ces options ajoutées sont disponibles tant que la fonctionnalité IDE demeure en mémoire.

> [!NOTE]
> Certaines collections de paramètres déterminent la quantité de pages qui s’affichent dans le volet de navigation de la boîte de dialogue Options. Vous pouvez choisir d’afficher toutes les pages possibles en sélectionnant **Afficher tous les paramètres**.

## <a name="how-options-are-applied"></a>Application des options
 Cliquer sur OK dans la boîte de dialogue **Options** enregistre tous les paramètres de toutes les pages. Cliquer sur Annuler dans n’importe quelle page annule toutes les demandes de modification, y compris celles effectuées dans les autres pages **Options**. Certaines modifications apportées aux paramètres d’options, telles que celles effectuées dans [Polices et couleurs (section Environnement de la boîte de dialogue Options)](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), ne prennent effet qu’une fois que vous fermez et rouvrez Visual Studio.

### <a name="show-all-settings"></a>Show all settings
 Sélectionner ou désélectionner **Afficher tous les paramètres** applique toutes les modifications apportées dans la boîte de dialogue **Options**, même si vous n’avez pas encore cliqué sur **OK**.

## <a name="see-also"></a>Voir aussi
 [Personnalisation de l’éditeur](../../ide/customizing-the-editor.md)
