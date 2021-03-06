---
title: 'CA2100 : Passez en revue les requêtes SQL pour les failles de sécurité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 167d9be908cef7e597e568a1fa60b4285960ad80
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950347"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100 : Vérifier si les requêtes SQL présentent des failles de sécurité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode définit le <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> propriété à l’aide d’une chaîne qui est construite à partir d’un argument de chaîne à la méthode.

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose que l’argument de chaîne contient des entrées d’utilisateur. Une chaîne de commande SQL générée par une entrée d'utilisateur est vulnérable aux attaques par injection de code SQL. Dans une attaque par injection SQL, un utilisateur malveillant fournit des entrées qui modifie la conception d’une requête dans le but d’endommager ou d’accès non autorisé à la base de données sous-jacente. Les techniques classiques englobent l’injection d’un guillemet ou une apostrophe, qui est le délimiteur de chaîne littérale SQL ; deux tirets, ce qui signifie un commentaire SQL ; et un point-virgule, ce qui indique qu’une nouvelle commande suit. Si l’entrée d’utilisateur doit faire partie de la requête, utilisez un des éléments suivants, répertoriés par ordre d’efficacité, afin de réduire le risque d’attaque.

- Utiliser une procédure stockée.

- Utilisez une chaîne de commande paramétrable.

- Valider l’entrée d’utilisateur pour le type et le contenu avant de générer la chaîne de commande.

  Ce qui suit [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] types implémentent le <xref:System.Data.IDbCommand.CommandText%2A> propriété ou fournissent des constructeurs qui définissent la propriété à l’aide d’un argument de chaîne.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> et <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> et <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> et <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.Data.SqlServerCe.SqlCeCommand](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) and  [System.Data.SqlServerCe.SqlCeDataAdapter](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> et <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Notez que cette règle est violée lorsque la méthode ToString d’un type est utilisée explicitement ou implicitement pour construire la chaîne de requête. Voici un exemple.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 La règle est enfreinte, car un utilisateur malveillant peut substituer la méthode ToString().

 La règle est enfreinte lors de la méthode ToString est utilisée implicitement.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez une requête paramétrable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le texte de commande ne contient pas d’entrée d’utilisateur.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `UnsafeQuery`, qui enfreint la règle et une méthode, `SaferQuery`, qui satisfait la règle en utilisant une chaîne de commande paramétrable.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble de la sécurité](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
