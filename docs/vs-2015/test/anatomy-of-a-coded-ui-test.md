---
title: Anatomie d’un test codé de l’interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 25
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 46226d241db04cad0f4859650dc2aff855b72f08
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102027"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomie d'un test codé de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous créez un test codé de l'interface utilisateur dans un projet de test codé de l'interface utilisateur, plusieurs fichiers sont ajoutés à votre solution. Dans cette rubrique, nous allons utiliser un exemple de test codé de l'interface utilisateur pour examiner ces fichiers.  
  
 **Spécifications**  
  
- Visual Studio Enterprise  
  
## <a name="contents-of-a-coded-ui-test"></a>Contenu d'un test codé de l'interface utilisateur  
 Quand vous créez un test codé de l’interface utilisateur, le **Générateur de test codé de l’interface utilisateur** crée un mappage de l’interface utilisateur testée, ainsi que les méthodes de test, les paramètres et les assertions de tous les tests. Il crée également un fichier de classe pour chaque test.  
  
|Fichier|Sommaire|Modifiable ?|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Section Déclarations](#UIMapDesignerFile)<br /><br /> [Classe UIMap](#UIMapClass) (partielle, générée automatiquement)<br /><br /> [Méthodes](#UIMapMethods)<br /><br /> [Propriétés](#UIMapProperties)|Non|  
|[UIMap.cs](#UIMapCS)|[Classe UIMap](#UIMapCS) (partielle)|Oui|  
|[CodedUITest1.cs](#CodedUITestCS)|[Classe CodedUITest1](#CodedUITestCS)<br /><br /> [Méthodes](#CodedUITestMethods)<br /><br /> [Propriétés](#CodedUITestProperties)|Oui|  
|[UIMap.uitest](#UIMapuitest)|Mappage XML de l'interface utilisateur pour le test.|Non|  
  
### <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Ce fichier contient le code qui est créé automatiquement par le **Générateur de test codé de l’interface utilisateur** lors de la création d’un test. Ce fichier est recréé chaque fois qu'un test change, afin qu'il ne soit pas un fichier dans lequel vous pouvez ajouter ou modifier du code.  
  
#### <a name="declarations-section"></a>Section Déclarations  
 Cette section inclut les déclarations suivantes pour une interface utilisateur Windows.  
  
```csharp  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 L'espace de noms <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> est inclus pour une interface utilisateur Windows. Pour une interface utilisateur de page Web, l'espace de noms serait <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls> ; pour une interface utilisateur Windows Presentation Foundation, l'espace de noms serait <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.  
  
#### <a name="UIMapClass"></a> Classe UIMap  
 La section suivante du fichier est la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>.  
  
```  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```  
  
 Le code de la classe démarre avec un <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> qui est appliqué à la classe, qui est déclarée en tant que classe partielle. Vous remarquerez que l'attribut est également appliqué à toutes les classes dans ce fichier. L'autre fichier pouvant contenir plus de code pour cette classe est `UIMap.cs`, décrit plus loin.  
  
 La classe `UIMap` générée inclut du code pour chaque méthode qui a été spécifiée quand le test a été enregistré.  
  
```  
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```  
  
 Cette partie de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> inclut également le code généré pour chaque propriété requise par les méthodes.  
  
```  
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```  
  
##### <a name="UIMapMethods"></a> Méthodes UIMap  
 Chaque méthode a une structure semblable à la méthode `AddItems()`. Celle-ci est est expliquée en détail sous le code, qui est présenté avec des sauts de ligne à des fins de clarté.  
  
```  
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}  
```  
  
 Le commentaire récapitulatif de chaque définition de méthode indique la classe à utiliser pour les valeurs de paramètre de cette méthode. Dans cet exemple, il s'agit de la classe `AddItemsParams`, qui est définie ultérieurement dans le fichier `UIMap.cs` et qui correspond également au type de valeur retourné par la propriété `AddItemsParams`.  
  
 En haut du code de la méthode se trouve une région `Variable Declarations` qui définit des variables locales pour les objets de l'interface utilisateur que la méthode va utiliser.  
  
 Dans cette méthode, `UIItemWindow` et `UIItemEdit` sont des propriétés accessibles à l'aide de la classe `UICalculatorWindow`, définie ultérieurement dans le fichier `UIMap.cs`.  
  
 Ensuite figurent des lignes qui envoient du texte depuis le clavier vers l'application Calculatrice à l'aide des propriétés de l'objet `AddItemsParams`.  
  
 La méthode `VerifyTotal()` a une structure très similaire et elle inclut le code d'assertion suivant.  
  
```  
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```  
  
 Le nom de la zone de texte est répertorié comme étant inconnu car le développeur de l'application Windows Calculatrice n'a pas fourni de nom publiquement disponible pour le contrôle. La méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> échoue quand la valeur réelle n'est pas égale à la valeur attendue, ce qui entraîne l'échec du test. Notez également que la valeur attendue inclut une virgule suivie d'un espace. Si vous devez modifier les fonctionnalités de ce test particulier, vous devez tenir compte de cette virgule et de cet espace.  
  
##### <a name="UIMapProperties"></a> Propriétés UIMap  
 Le code de chaque propriété est également très standard dans toute la classe. Le code suivant pour la propriété `AddItemsParams` est utilisé dans la méthode `AddItems()`.  
  
```  
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}  
```  
  
 Notez que la propriété utilise une variable locale privée nommée `mAddItemsParams` pour retenir la valeur avant de la retourner. Le nom de la propriété et le nom de la classe pour l'objet retourné sont identiques. La classe est définie ultérieurement dans le fichier `UIMap.cs`.  
  
 Chaque classe retournée par une propriété est structurée de la même façon. La classe suivante est `AddItemsParams`.  
  
```  
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}  
```  
  
 Comme avec toutes les classes incluses dans le fichier `UIMap.cs`, cette classe démarre avec <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. Dans cette petite classe se trouve une région `Fields` qui définit les chaînes à utiliser en tant que paramètres pour la méthode <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> qui est utilisée dans la méthode `UIMap.AddItems()` décrite précédemment. Vous pouvez écrire du code pour remplacer les valeurs dans ces champs de chaîne avant l'appel de la méthode dans laquelle ces paramètres sont utilisés.  
  
### <a name="UIMapCS"></a> UIMap.cs  
 Par défaut, ce fichier contient une classe `UIMap` partielle dépourvue de méthode ou de propriété.  
  
#### <a name="uimap-class"></a>Classe UIMap  
 C'est là que vous pouvez créer du code personnalisé pour étendre les fonctionnalités de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>. Le code que vous créez dans ce fichier n’est pas regénéré par le **Générateur de test codé de l’interface utilisateur** chaque fois qu’un test est modifié.  
  
 Toutes les parties de <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> peuvent utiliser les méthodes et propriétés de toute autre partie de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>.  
  
### <a name="CodedUITestCS"></a> CodedUITest1.cs  
 Ce fichier est généré par le **Générateur de test codé de l’interface utilisateur**, mais il n’est pas recréé chaque fois que le test est modifié, donc vous pouvez modifier le code dans ce fichier. Le nom du fichier est généré à partir du nom que vous avez spécifié pour le test lors de sa création.  
  
#### <a name="codeduitest1-class"></a>Classe CodedUITest1  
 Par défaut, ce fichier contient la définition d'une seule classe.  
  
```  
[CodedUITest]  
public class CodedUITest1  
```  
  
 T:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute est appliqué automatiquement à la classe, ce qui permet au framework de test de le reconnaître en tant qu'extension de test. Notez également qu'il ne s'agit pas d'une classe partielle. Tout le code de la classe est contenu dans ce fichier.  
  
##### <a name="CodedUITestProperties"></a> Propriétés CodedUITest1  
 La classe contient deux propriétés par défaut qui se trouvent au bas du fichier. Elles ne doivent pas être modifiées.  
  
```  
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```  
  
##### <a name="CodedUITestMethods"></a> Méthodes CodedUITest1  
 Par défaut, la classe contient une seule méthode.  
  
```  
public void CodedUITestMethod1()  
```  
  
 Cette méthode appelle chaque méthode `UIMap` que vous avez spécifiée quand vous avez enregistré votre test, ce qui est décrit dans la section [Classe UIMap](#UIMapClass).  
  
 Une région intitulée `Additional test attributes`, si elle n'est pas commentée, contient deux méthodes facultatives.  
  
```  
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> est appliqué à la méthode `MyTestInitialize()`, ce qui indique à l'infrastructure de test d'appeler cette méthode avant toutes les autres méthodes de test. De même, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> est appliqué à la méthode `MyTestCleanup()`, ce qui indique à l'infrastructure de test d'appeler cette méthode une fois que toutes les autres méthodes de test ont été appelées. L'utilisation de ces méthodes est facultative. Pour ce test, la méthode `UIMap.LaunchCalculator()` aurait pu être appelée à partir de `MyTestInitialize()` et la méthode `UIMap.CloseCalculator()` à partir de `MyTestCleanup()` au lieu de `CodedUITest1Method1()`.  
  
 Si vous ajoutez d'autres méthodes à cette classe à l'aide de <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, l'infrastructure de test appelle chaque méthode dans le cadre du test.  
  
### <a name="UIMapuitest"></a> UIMap.uitest  
 Il s'agit d'un fichier XML qui représente la structure de l'enregistrement du test codé de l'interface utilisateur et toutes ses parties. Celles-ci incluent les actions et les classes en plus des méthodes et propriétés de ces classes. Le fichier [UIMap.Designer.cs](#UIMapDesignerFile) contient le code généré par le Générateur de test codé de l’interface utilisateur pour reproduire la structure du test et fournir la connexion au framework de test.  
  
 Le fichier `UIMap.uitest` n'est pas directement modifiable. Toutefois, vous pouvez utiliser le Générateur de test codé de l’interface utilisateur pour modifier le test, ce qui modifie automatiquement le fichier `UIMap.uitest` et le fichier [UIMap.Designer.cs](#UIMapDesignerFile).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)   
 [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Bonnes pratiques pour les tests codés de l’interface utilisateur](../test/best-practices-for-coded-ui-tests.md)   
 [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
