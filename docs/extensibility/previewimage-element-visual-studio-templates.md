---
title: Élément PreviewImage (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15e09d7837c04c276e955f88e8b1afd670d6e948
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433472"
---
# <a name="previewimage-element-visual-studio-templates"></a>Élément PreviewImage (modèles Visual Studio)
Spécifie l’image d’aperçu, comme un nom de fichier pour l’image d’aperçu qui apparaîtra dans le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.

 \<VSTemplate> \<TemplateData> \<PreviewImage>

## <a name="syntax"></a>Syntaxe

```
<PreviewImage>"filename"</PreviewImage>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché dans un le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|

## <a name="text-value"></a>Valeur texte
 Une valeur texte est requise.

 Le texte doit être une chaîne qui représente un nom de fichier.

## <a name="remarks"></a>Notes
 `PreviewImage` est un élément facultatif.

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)