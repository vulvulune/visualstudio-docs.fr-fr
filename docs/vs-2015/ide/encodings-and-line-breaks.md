---
title: Encodages et sauts de ligne | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fd03dba0dfb13723fcb44d489a7b850aebeb1e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503532"
---
# <a name="encodings-and-line-breaks"></a>Encodages et sauts de ligne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [encodages et sauts de ligne](https://docs.microsoft.com/visualstudio/ide/encodings-and-line-breaks).  
  
Dans Visual Studio, vous pouvez utiliser les paramètres **Options d’enregistrement de fichier/avancées** pour déterminer le type de caractères de saut de ligne que vous souhaitez. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.  
  
> [!NOTE]
>  Si vous avez certains types de paramètres de développement (Visual Basic, F#, développement web), vous pouvez ne pas voir **Options d’enregistrement avancées** dans le menu. Pour modifier vos paramètres (en spécifiant par exemple Général), ouvrez **Outils / Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Dans Visual Studio, les caractères suivants sont interprétés comme des sauts de ligne :  
  
-   CRLF : retour chariot + saut de ligne, caractères Unicode 000D + 000A  
  
-   LF : saut de ligne, caractère Unicode 000A  
  
-   NEL : ligne suivante, caractère Unicode 0085  
  
-   LS : séparateur de ligne, caractère Unicode 2028  
  
-   PS : séparateur de paragraphe, caractère Unicode 2029  
  
 Du texte copié à partir d’autres applications conserve les caractères d’encodage et de saut de ligne d’origine. Par exemple, lorsque vous copiez du texte à partir du Bloc-notes pour le coller dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres que dans le Bloc-notes.  
  
 Lorsque vous ouvrez un fichier qui a des caractères de saut de ligne différents, vous pouvez voir une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérents doivent être normalisés, ainsi que le type de saut de ligne à choisir.


