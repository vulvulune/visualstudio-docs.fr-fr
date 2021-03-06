---
title: 'Procédure : Identifier les symboles dans une bibliothèque | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5eebe6382d2aec13996c57ef76aba2e04512463f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909953"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Procédure : Identifier les symboles dans une bibliothèque
Outils de consultation de symboles affichent des vues hiérarchiques des symboles. Les symboles représentent des espaces de noms, les objets, les classes, les membres de classe et les autres éléments de langage.

 Chaque symbole dans la hiérarchie peut être identifiée par les informations de navigation passées par la bibliothèque de symboles pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets via les interfaces suivantes :

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 L’emplacement du symbole dans la hiérarchie distingue un symbole. Il permet des outils de consultation de symboles accéder à un symbole spécifique. Le chemin d’accès unique et complet pour le symbole détermine l’emplacement. Chaque élément dans le chemin d’accès est un nœud. Le chemin d’accès commence par le nœud de niveau supérieur et se termine par le symbole spécifique. Par exemple, si la méthode M1 est un membre de la classe C1 et C1 est dans l’espace de noms N1, le chemin d’accès complet de la méthode M1 est N1. C1. M1. Ce chemin d’accès contient trois nœuds : N1, C1 et M1.

 Les informations de navigation permettent la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets pour rechercher, sélectionner et conserver sélectionné les symboles dans la hiérarchie. Il permet d’accéder à partir d’un outil de navigation vers un autre. Lors de l’utilisation **Explorateur d’objets** pour rechercher des symboles dans un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projet, vous pouvez cliquez sur une méthode et commencer le **Explorateur d’appels** outil pour afficher la méthode dans un graphique des appels.

 Deux formes décrivent l’emplacement de symboles. La forme canonique est basée sur le chemin d’accès qualifié complet du symbole. Il représente une position unique du symbole dans la hiérarchie. Elle est indépendante de l’outil de recherche de symboles. Pour obtenir les informations de la forme canonique, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> (méthode). Le formulaire de présentation décrit l’emplacement du symbole dans un outil de consultation de symboles spécifique. La position du symbole est relatif à la position d’autres symboles dans la hiérarchie. Un symbole donné peut avoir plusieurs chemins de présentation, mais qu’un seul chemin d’accès canonique. Par exemple, si C1 classe héritée de la classe de C2 et les deux classes se trouvent dans l’espace de noms N1, le **Explorateur d’objets** affiche l’arborescence hiérarchique suivant :

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Le chemin d’accès canonique de la classe C2, dans cet exemple, est N1 + C2. Le chemin d’accès de présentation de C2 inclut les nœuds C1 et « Bases et Interfaces » : N1 + C1 + « Bases et Interfaces » + C2.

 Pour obtenir les informations du formulaire de présentation, le Gestionnaire d’objets appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> (méthode).

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Pour obtenir canonique et informations de formulaires de présentation

1. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     Le Gestionnaire d’objets appelle cette méthode pour obtenir la liste de nœuds contenus dans le chemin d’accès canonique du symbole.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.

     Le Gestionnaire d’objets appelle cette méthode pour obtenir la liste de nœuds contenus dans le chemin d’accès de présentation du symbole.

## <a name="see-also"></a>Voir aussi
- [Prend en charge des outils de consultation de symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Guide pratique pour Inscrire une bibliothèque avec le Gestionnaire d’objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Guide pratique pour Exposer des listes de symboles fournis par la bibliothèque pour le Gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)