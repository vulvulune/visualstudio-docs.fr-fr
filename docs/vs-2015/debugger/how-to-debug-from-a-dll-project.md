---
title: 'Procédure : Déboguer à partir d’un projet de DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438489"
---
# <a name="how-to-debug-from-a-dll-project"></a>Procédure : Déboguer à partir d’un projet de DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour démarrer le débogage d'un projet de DLL, vous devez spécifier l'application appelante dans les propriétés du projet. Les pages de propriétés C++ diffèrent dans la disposition et le contenu par rapport aux pages de propriétés C# et Visual Basic.  
  
 Si une DLL managée est appelée par du code natif et que vous voulez déboguer les deux, vous pouvez le spécifier dans les propriétés du projet. Pour plus d'informations, voir [Procédure : Déboguer en Mode mixte](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> Vous ne pouvez pas spécifier une application appelante externe dans les éditions Express de Visual Studio. Au lieu de cela, vous devez ajouter un projet exécutable à la solution, le définir comme projet de démarrage et appeler les méthodes de votre DLL depuis le projet exécutable.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Pour spécifier l'application appelante dans un projet C++  
  
1. Cliquez sur le nœud de projet dans le **l’Explorateur de solutions** et sélectionnez **propriétés**. Accédez à la **déboguer** onglet.  
  
2. Vérifiez que le champ **Configuration** en haut de la fenêtre est défini sur **Débogage**.  
  
3. Accédez à **propriétés de Configuration / débogage**.  
  
4. Dans le **débogueur à lancer** , choisissez **débogueur Windows Local** ou **débogueur Windows distant**.  
  
5. Dans le **commande** ou **commande à distance** zone, ajoutez le nom de chemin complet de l’application.  
  
6. Ajoutez les arguments nécessaires du programme à la zone **Arguments de la commande**.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Pour spécifier l'application appelante dans un projet C# ou Visual Basic  
  
1. Cliquez sur le nœud de projet dans le **l’Explorateur de solutions** et sélectionnez **propriétés**. Accédez à la **déboguer** onglet.  
  
     Sélectionnez **démarrer le programme externe**et ajoutez le nom de chemin complet du programme à exécuter.  
  
     Si vous avez besoin ajouter des arguments de ligne de commande du programme externe, ajoutez-les dans le **arguments de ligne de commande** champ.  
  
2. Vous pouvez également appeler une application via une URL. (Vous pouvez procéder ainsi si vous déboguez une DLL managée utilisée par une application ASP.NET locale.)  
  
     Sous **Action de démarrage**, sélectionnez le **démarrer le navigateur dans l’URL :** case d’option et entrez l’URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Pour démarrer le débogage à partir du projet de DLL  
  
1. Définissez des points d'arrêt selon vos besoins.  
  
2. Démarrer le débogage (appuyez sur F5, cliquez sur la flèche verte ou cliquez sur **déboguer / démarrer le débogage**).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de projets DLL](../debugger/debugging-dll-projects.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
