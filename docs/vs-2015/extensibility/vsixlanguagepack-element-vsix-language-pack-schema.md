---
title: Élément VSIXLanguagePack (schéma du module linguistique VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b4ba4e98b8b2d42485a7594d5bab658e1bd6ccb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422485"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Élément VSIXLanguagePack (schéma du module linguistique VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obligatoire. Fournit l’élément racine pour un module linguistique VSIX. Le module linguistique VSIX fournit des informations d’installation localisé pour un package VSIX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`xmlns`|L’espace de noms XML dans lequel le schéma du module linguistique VSIX est défini.|  
  
## <a name="xmlns-attribute"></a>xmlns attribut  
  
|Value|Description|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obligatoire. L’emplacement du fichier qui définit le schéma pour les modules linguistiques.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obligatoire. Le nom localisé de l’extension à installer.|  
|[Élément LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obligatoire. La description localisée de l’extension à installer.|  
|[Élément MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Optionnel. Un lien vers des informations localisées sur l’extension.|  
|[Élément License](../extensibility/license-element-vsix-language-pack-schema.md)|Optionnel. Le chemin d’accès d’une version localisée du fichier de licence pour l’extension.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.||  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Espace de noms    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nom du schéma   |                 Schéma du module linguistique VSIX                 |
| Fichier de validation |                VSIXLanguagePackSchema.xsd                 |
|  Peut être vide   |                            Non                             |
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma du module linguistique VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localisation de Packages VSIX](../extensibility/localizing-vsix-packages.md)   
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
