---
title: Les décisions de conception de contrôle de source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e17e5a88b958c1361e7f8b3db70d7599f44f766
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62858990"
---
# <a name="source-control-design-decisions"></a>Décisions de conception du contrôle de code source
Les décisions de conception suivantes doivent être considérées pour les projets lors de la mise en œuvre du contrôle de code source.

## <a name="will-information-be-shared-or-private"></a>Informations sera partagé ou privé ?
 La décision de conception plus importantes, que vous pouvez effectuer est les informations sont partageables et enfin privé. Par exemple, la liste des fichiers pour le projet est partagée, mais au sein de cette liste de fichiers, certains utilisateurs peuvent également placer les fichiers privés. Paramètres du compilateur sont partagés, mais le projet de démarrage est généralement privé. Les paramètres sont purement partagé, partagé avec un remplacement ou purement privés. Par conception, les éléments privés, tels que les options de l’utilisateur de Solution (.suo), fichiers, ne sont pas vérifiées dans [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Veillez à stocker des informations confidentielles dans des fichiers privés, tels que le fichier .suo, ou un fichier privé spécifique que vous créez, par exemple, un. csproj.user fichier pour Visual c# ou un. fichier vbproj.user pour Visual Basic.

 Cette décision n’est pas exhaustive et peut être effectuée sur une base de l’élément par élément.

## <a name="will-the-project-include-special-files"></a>Le projet inclut les fichiers spéciaux ?
 Une autre décision de conception importante est que la structure de votre projet utilise des fichiers spéciaux. Fichiers spéciaux sont des fichiers cachés qui sous-tendent les fichiers qui sont des boîtes de dialogue visible dans l’Explorateur de solutions et dans l’archivage et d’extraction. Si vous utilisez des fichiers spéciaux, suivez ces instructions :

1. N’associez pas des fichiers spéciaux avec le nœud racine du projet, autrement dit, avec le projet de fichiers lui-même. Votre fichier projet doit être un seul fichier.

2. Lorsque des fichiers spéciaux sont ajoutés, supprimés ou renommés dans un projet, approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> événements doivent être déclenchés avec l’indicateur qui indique les fichiers sont des fichiers spéciaux. Ces événements sont appelés par l’environnement en réponse au projet appelant approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> méthodes.

3. Lorsque votre projet ou votre éditeur appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> pour un fichier, les fichiers spéciaux associés à ce fichier ne sont pas automatiquement extraits. Transmettre des fichiers spéciaux dans ainsi que le fichier parent. L’environnement détecte la relation entre tous les fichiers qui sont passés et masquer correctement les fichiers spéciaux dans l’interface utilisateur d’extraction.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)