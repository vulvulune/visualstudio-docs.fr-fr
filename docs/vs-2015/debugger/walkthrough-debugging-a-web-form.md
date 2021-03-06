---
title: 'Procédure pas à pas : Débogage d’un formulaire Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56a11c24ad8a38cc837659ac063987573c0ba492
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444306"
---
# <a name="walkthrough-debugging-a-web-form"></a>Procédure pas à pas : Débogage d’un formulaire web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas vous expliquent comment déboguer une application Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], également connue sous le nom de Web Form. Elle vous explique également comment démarrer et arrêter l’exécution, définir des points d’arrêt et examiner des variables dans la fenêtre **Espion**.  
  
> [!NOTE]
> Pour exécuter cette procédure pas à pas, vous devez avoir des privilèges d'administrateur de l'ordinateur serveur. Par défaut, le processus [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], aspnet_wp.exe ou w3wp.exe, s'exécute comme un processus [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Pour déboguer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], vous devez avoir des privilèges d'administrateur sur l'ordinateur où [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] s'exécute. Pour plus d'informations, voir [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
 Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Pour créer le Web Form  
  
1. Si une solution est déjà ouverte, fermez-la.  
  
2. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Site web**.  
  
     La boîte de dialogue **Nouveau site web** s’affiche.  
  
3. Dans le volet **Modèles**, cliquez sur **Site web ASP.NET**.  
  
4. Sur le **emplacement** ligne, cliquez sur **HTTP** dans la liste et dans la zone de texte, tapez **http://localhost/WebSite**.  
  
5. Dans la liste **Langage**, cliquez sur **Visual C#** ou sur **Visual Basic**.  
  
6. Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crée un projet et affiche le code source HTML par défaut. Il crée également un répertoire virtuel nommé **WebSite** sous **Site web par défaut** dans IIS.  
  
7. Cliquez sur l’onglet **Conception** dans la marge inférieure.  
  
8. Cliquez sur l’onglet **Boîte à outils** dans la marge gauche ou sélectionnez-le dans le menu **Affichage**.  
  
     La **Boîte à outils** s'ouvre.  
  
9. Dans la **Boîte à outils**, cliquez sur le contrôle **Bouton** et ajoutez-le à l’aire de conception principale, Default.aspx.  
  
10. Dans la **Boîte à outils**, cliquez sur le contrôle **Zone de texte** et faites-le glisser sur l’aire de conception principale, Default.aspx.  
  
11. Double-cliquez sur le contrôle Button que vous avez déposé.  
  
     Vous accédez alors à la page de codes : Default.aspx.cs pour C# ou Default.aspx.vb pour [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Le curseur doit se trouver dans la fonction `Button1_Click`.  
  
12. Dans la fonction `Button1_Click`, ajoutez le code suivant :  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Le projet doit être généré sans erreur.  
  
     Vous pouvez maintenant commencer le débogage.  
  
### <a name="to-debug-the-web-form"></a>Pour déboguer le Web FOrm  
  
1. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez sur la marge gauche de la ligne sur laquelle vous avez ajouté le texte :  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Un point rouge s'affiche et le texte de la ligne est surligné en rouge. Le point rouge représente un point d'arrêt. Lorsque vous exécutez l'application dans le débogueur, le débogueur interrompt l'exécution à l'emplacement du code où se trouve ce point d'arrêt. Vous pouvez afficher l'état de votre application et la déboguer. Pour plus d’informations, consultez [Points d’arrêt](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Dans le menu **Déboguer**, cliquez sur **Démarrer le débogage**.  
  
3. La boîte de dialogue **Débogage non activé** s’affiche. Sélectionnez l’option **Modifier le fichier Web.config pour activer le débogage**, puis cliquez sur **OK**.  
  
     Internet Explorer démarre et affiche la page que vous venez de créer.  
  
4. Dans Internet Explorer, cliquez sur le bouton.  
  
     Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cette opération vous permet d'atteindre la ligne où vous définissez votre point d'arrêt sur la page de codes Default.aspx.cs ou Default.aspx.vb. Cette ligne doit être surlignée en jaune. Vous pouvez à présent afficher les variables de votre application et contrôler son exécution. Votre application s'arrête et attend une commande de votre part.  
  
5. Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Espion**, puis sur **Espion1**.  
  
6. Dans la fenêtre **Espion**, tapez **TextBox1.Text**.  
  
     La fenêtre **Espion** affiche la valeur de la variable `TextBox1.Text` :  
  
    ```  
    ""  
    ```  
  
7. Dans le menu **Déboguer**, cliquez sur **Pas à pas principal**.  
  
     La valeur de `TextBox1.Text` change dans la fenêtre **Espion** et devient :  
  
    ```  
    "Button was clicked!"  
    ```  
  
8. Dans le menu **Déboguer**, cliquez sur **Continuer**.  
  
9. Dans Internet Explorer, cliquez de nouveau sur le bouton.  
  
     L'exécution s'arrête de nouveau sur le point d'arrêt.  
  
10. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez sur le point rouge dans la marge de gauche.  
  
     Cela supprime le point d'arrêt.  
  
11. Dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Pour attacher au Web Form pour le débogage  
  
1. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous pouvez attacher le débogueur à un processus en cours d'exécution. Pour un débogage plus efficace, compilez le fichier exécutable sous forme de version Debug avec des fichiers de symboles (PDB).  
  
2. Dans la fenêtre Default.aspx.cs ou Default.aspx.vb, cliquez dans la marge de gauche pour définir à nouveau un point d'arrêt à la ligne que vous avez ajoutée :  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3. Dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage**.  
  
     Le Web Form commence à s'exécuter sous Internet Explorer, mais le débogueur n'est pas attaché.  
  
4. Attachez-le au processus [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Pour plus d’informations, consultez [débogage des Applications Web déployées](../debugger/debugging-deployed-web-applications.md).  
  
5. Dans Internet Explorer, cliquez sur le bouton sur votre formulaire.  
  
     Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous devez atteindre le point d'arrêt dans Default.aspx.cs, Default.aspx.vb ou Default.aspx.  
  
6. Quand vous avez fini de déboguer, dans le menu **Déboguer**, cliquez sur **Arrêter le débogage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)
