---
title: Validation de documents XML dans l’éditeur XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59b8ed5c74d998b47ff4a187b420695eab5be035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807715"
---
# <a name="xml-document-validation"></a>Validation de documents XML

L’éditeur XML vérifie la syntaxe XML 1.0 et effectue également la validation des données en cours de frappe. L'éditeur peut effectuer cette validation à l'aide d'une définition de type de document (DTD) ou d'un schéma. Des soulignements ondulés rouges marquent les erreurs XML 1.0 correctement construites. Des soulignements ondulés bleus marquent les erreurs sémantiques d'après la validation de la DTD ou du schéma. La liste d'erreurs comporte une entrée pour chaque erreur détectée. Vous pouvez également afficher le message d'erreur en plaçant le curseur sur la ligne ondulée.

 Les schémas utilisés pour la validation sont recherchés en fonction de la comparaison du `targetNamespace` d’un schéma compilé à la déclaration xmlns de l’élément. Les schémas compilés sont chargés à partir d'un des emplacements suivants, répertoriés par ordre de priorité :

- À partir du nom de fichier spécifié dans le **schémas** champ du document **propriétés** fenêtre.

- Une DTD ou un schéma inline

- Une DTD externe ou un attribut `xsd:schemaLocation` et `xsd:noNamespaceSchemaLocation`

- Un URI d'espace de noms de schéma XDR « x-schema »

Des schémas peuvent également être recherchés dans les emplacements supplémentaires suivants lorsque le schéma contient un espace de noms cible non vide :

- Une autre fenêtre d'éditeur qui contient le schéma

- Un schéma contenu dans la solution actuelle

- Un schéma du répertoire de cache de schéma

## <a name="xslt-files"></a>Fichiers XSLT
 Lorsque vous modifiez un fichier XSLT, le *xslt.xsd* fichier situé dans le cache de schéma est utilisé pour la validation. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. Les erreurs provenant du compilateur XSLT sont signalées par des soulignements ondulés rouges.

## <a name="xml-schema-xsd-files"></a>Fichiers XML schema (XSD)
 Lorsque vous modifiez un fichier de schéma XML, le *xsdschema.xsd* fichier situé dans le cache de schéma est utilisé pour la validation. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. Les erreurs de compilation sont signalées de la même façon.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)