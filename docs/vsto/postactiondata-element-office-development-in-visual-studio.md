---
title: '&lt;postActionData&gt; élément (développement Office dans Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cda7829fc615c64be75f295a0cbc26b2ebbc7eea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561484"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt; élément (développement Office dans Visual Studio)
  L’élément `postActionData` de l’espace de noms `vstav3` spécifie les données associées aux actions de post-déploiement qui s’exécutent après l’installation des solutions Office.

## <a name="syntax"></a>Syntaxe

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `postActionData` est facultatif et se trouve dans l’espace de noms `vstav3` . Il existe un élément `postActionData` défini dans un manifeste de l’application pour chaque action de post-déploiement.

 L’élément `postActions` ne comporte pas d’attributs.

 `postActions` n’a aucun élément enfant.

## <a name="post-deployment-action-example"></a>Exemple d’action de post-déploiement

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `postAction` d’un manifeste de l’application pour une solution Office déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
