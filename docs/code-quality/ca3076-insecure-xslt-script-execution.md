---
title: 'CA3076 : Exécution non sécurisée de script XSLT'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f98b022aef49a4d98ad4864793aa55732f8de6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541088"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076 : Exécution non sécurisée de script XSLT

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Si vous exécutez le langage XSLT (Extensible Stylesheet Language Transformations) dans les applications .NET de manière non sécurisée, le processeur peut résoudre les références URI non fiables qui pourraient divulguer des informations sensibles à des personnes malveillantes, ce qui aboutirait à des attaques par déni de service et intersites. Pour plus d’informations, consultez [XSLT sécurité Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Description de la règle

**XSLT** est une norme W3C (World Wide Web Consortium) pour la transformation des données XML. XSLT est généralement utilisé pour écrire des feuilles de style pour transformer des données XML dans d’autres formats tels que HTML, texte de longueur fixe, séparées par des virgules ou un autre format XML. Bien qu’il soit interdit par défaut, vous pouvez choisir de l’activer pour votre projet.

Pour garantir que vous n’exposez pas une surface d’attaque, cette règle se déclenche chaque fois que le XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> reçoit des instances de combinaisons non sécurisées de <xref:System.Xml.Xsl.XsltSettings> et <xref:System.Xml.XmlResolver>, ce qui permet le traitement d’un script malveillant.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Remplacez l’argument XsltSettings non sécurisé par XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> ou avec une instance qui a désactivé l’exécution de script et de fonction document.

- Remplacez l’argument <xref:System.Xml.XmlResolver> par la valeur null ou une instance de <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Sauf si vous êtes sûr que l’entrée provient d’une source fiable, ne supprimez aucune règle de cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Violation qui utilise XsltSettings.TrustedXslt

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solution-that-uses-xsltsettingsdefault"></a>Solution qui utilise XsltSettings.Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Violation&mdash;documenter l’exécution de script et de fonction ne pas désactivée

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Solution&mdash;désactiver l’exécution du script et de fonction document

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Considérations de sécurité XSLT (Guide .NET)](/dotnet/standard/data/xml/xslt-security-considerations)