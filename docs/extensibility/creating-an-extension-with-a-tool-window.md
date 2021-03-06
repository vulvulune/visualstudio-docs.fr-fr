---
title: Création d’une Extension avec une fenêtre outil | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2741a7f9d27c303981ed4b179e3fe3d7cd63f020
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926456"
---
# <a name="create-an-extension-with-a-tool-window"></a>Créer une extension avec une fenêtre outil

Dans cette procédure, vous allez apprendre à utiliser le modèle de projet VSIX et le **fenêtre d’outil personnalisé** modèle d’élément pour créer une extension avec une fenêtre outil.

## <a name="prerequisites"></a>Prérequis

 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Créer une fenêtre outil

1. Créez un projet VSIX nommé **FirstWindow**. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue en recherchant « vsix ».

2. Quand le projet s’ouvre, ajoutez un modèle d’élément de fenêtre outil nommé **MyWindow**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C#** > **extensibilité** et sélectionnez **fenêtre d’outil personnalisé**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de fenêtre outil à *MyWindow.cs*.

3. Générez le projet et commencez le débogage.

   L’instance expérimentale de Visual Studio s’affiche. Pour plus d’informations sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).

4. Dans l’instance expérimentale, accédez à **vue** > **Windows autres**.

   Vous devez voir un élément de menu pour **MyWindow**. Cliquez dessus.

   Vous devez voir une fenêtre outil avec le titre **MyWindow** et un message de bouton **Click Me !.**