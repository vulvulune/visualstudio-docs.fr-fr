---
title: Débogage LINQ | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7a58b2c8f14f1dff241b7f3c7d783460a83b7bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852371"
---
# <a name="debugging-linq"></a>Débogage LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prend en charge le débogage du code LINQ (Language Integrated Query) avec certaines restrictions. La plupart des fonctionnalités de débogage sont compatibles avec les instructions LINQ, notamment l'exécution pas à pas, la définition de points d'arrêt et la consultation des résultats dans les fenêtres du débogueur. Cette rubrique décrit les principales restrictions liées au débogage de LINQ.

## <a name="BKMK_ViewingLINQResults"></a> Affichage des résultats LINQ
 Vous pouvez consulter le résultat d'une instruction LINQ à l'aide des DataTips, de la fenêtre Espion et de la boîte de dialogue Espion express. Lorsque vous utilisez une fenêtre source, vous pouvez suspendre le pointeur sur une requête dans la fenêtre source pour afficher un DataTip. Vous pouvez copier une variable LINQ et la coller dans la fenêtre Espion ou dans la boîte de dialogue Espion express.

 Dans LINQ, une requête n'est pas évaluée lorsqu'elle est créée ou déclarée, mais uniquement lors de son utilisation. Par conséquent, la requête ne possède de valeur que lorsqu'elle est évaluée. Pour obtenir une description complète de la création de requête et d’évaluation, consultez [Introduction aux requêtes LINQ (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) ou [écrire votre première requête LINQ](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Pour afficher le résultat d'une requête, le débogueur doit l'évaluer. Cette évaluation implicite, qui se produit lorsque vous consultez le résultat d'une requête LINQ dans le débogueur, entraîne quelques effets dont vous devez tenir compte :

- Chaque évaluation de la requête prend du temps. Le développement du nœud de résultats est long. Ainsi, pour certaines requêtes, une évaluation répétée peut diminuer considérablement les performances.

- L'évaluation d'une requête peut provoquer des effets secondaires, à savoir des modifications de la valeur des données ou de l'état du programme. Toutefois, les requêtes ne présentent pas toutes des effets secondaires. Pour savoir si une requête peut être évaluée sans risque et sans effets secondaires, vous devez comprendre le code qui implémente la requête.

## <a name="BKMK_SteppingAndLinq"></a> Exécution pas à pas et LINQ
 Lorsque vous déboguez du code LINQ, l'exécution pas à pas présente des différences de comportement que vous devez connaître.

### <a name="linq-to-sql"></a>LINQ to SQL
 Dans les requêtes LINQ to SQL, le code de prédicat n’est pas contrôlé par le débogueur. Par conséquent, vous ne pouvez pas effectuer d’exécution pas à pas du code de prédicat. Toute requête compilée en une arborescence de l’expression génère du code qui n’est pas contrôlé par le débogueur.

### <a name="stepping-in-visual-basic"></a>Exécution pas à pas dans Visual Basic
 Lorsque vous exécutez un programme Visual Basic pas à pas, si le débogueur rencontre une déclaration de requête, il n'effectue pas de pas à pas détaillé dans la déclaration, mais met en surbrillance la déclaration entière en tant qu'instruction unique. Ce comportement se produit car la requête n'est évaluée que lorsqu'elle est appelée. Pour plus d’informations, consultez [Introduction à LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 Si vous effectuez un pas à pas dans l'exemple de code suivant, le débogueur met en surbrillance la déclaration de requête (Query creation) en tant qu'instruction unique.

```vb
Function MyFunction(ByVal x As Char)
    Return True
End Function

Sub Main()
    'Query creation
    Dim x = From it In "faoaoeua" _
            Where MyFunction(it) _
            Select New With {.a = it}

    ' Query execution
    For Each cur In x
        Console.WriteLine(cur.ToString())
    Next
End Sub
```

 Lors de la prochaine exécution pas à pas, le débogueur met en surbrillance `For Each cur In x`. À l'étape suivante, il effectue un pas à pas détaillé dans la fonction `MyFunction`. Après la fonction `MyFunction`, il revient à `Console.WriteLine(cur.ToSting())`. À aucun moment, le débogueur n'effectue de pas à pas détaillé dans le code de prédicat dans la déclaration de requête, alors qu'il évalue ce code.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Remplacement d’un prédicat par une fonction pour activer l’exécution pas à pas (Visual Basic)
 Si vous devez effectuer un pas à pas détaillé d'un code de prédicat à des fins de débogage, vous pouvez remplacer le prédicat par un appel d'une fonction qui contient le code de prédicat d'origine. Par exemple, si vous avez le code suivant :

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 Vous pouvez déplacer le code de prédicat vers une nouvelle fonction, appelée `IsEven` :

```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt

For each item in query
      Console.WriteLine(item)
Next
...
Function IsEven(item As =Integer) as Boolean
      Return item Mod 2 = 0
End Function
```

 La requête modifiée appelle la fonction `IsEven` à chaque passe dans `items`. Vous pouvez utiliser les fenêtres du débogueur pour vérifier si chaque élément répond à la condition spécifiée. Vous pouvez également exécuter le code pas à pas dans `IsEven`. Dans cet exemple, le prédicat est assez simple. Toutefois, si vous devez déboguer un prédicat plus complexe, cette technique peut s’avérer très utile.

## <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Opération Modifier & Continuer non prise en charge pour LINQ
 Modifier & Continuer prend en charge les modifications apportées aux requêtes LINQ avec les limitations. Pour plus d’informations, consultez [modifications prises en charge de EnC](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))

## <a name="see-also"></a>Voir aussi

- [Débogage SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)
- [Introduction aux requêtes LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Introduction à LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
