---
title: Résoudre les problèmes liés au chargement des modèles de projet et d’élément
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70782646a52a5bca5741a864eee1f965941bb34b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547591"
---
# <a name="how-to-troubleshoot-templates"></a>Procédure : Dépanner des modèles

Si le chargement d’un modèle dans l’environnement de développement échoue, il existe plusieurs façons de procéder pour localiser le problème.

## <a name="validate-the-vstemplate-file"></a>Valider le fichier vstemplate

::: moniker range="vs-2017"

Si le fichier *.vstemplate* d’un modèle n’adhère pas au schéma de modèle Visual Studio, il se peut que le modèle n’apparaisse pas dans la boîte de dialogue **Nouveau projet**.

::: moniker-end

::: moniker range=">=vs-2019"

Si le fichier *vstemplate* d’un modèle n’est pas conforme au schéma de modèle Visual Studio, il se peut que le modèle n’apparaisse pas dans la boîte de dialogue où vous créez des projets.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Pour valider le fichier vstemplate

1. Localisez le fichier *.zip* qui contient le modèle.

1. Extrayez le fichier *.zip*.

1. Dans le menu **Fichier** de Visual Studio, choisissez **Ouvrir** > **Fichier**.

1. Sélectionnez le fichier *vstemplate* du modèle, puis choisissez **Ouvrir**.

1. Vérifiez que le code XML du fichier *vstemplate* adhère au schéma de modèle. Pour plus d’informations sur le schéma *vstemplate*, consultez [Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Pour obtenir une prise en charge d’IntelliSense quand vous créez le fichier *vstemplate*, ajoutez un attribut `xmlns` à l’élément `VSTemplate`, puis affectez-lui la valeur http://schemas.microsoft.com/developer/vstemplate/2005.

1. Enregistrez et fermez le fichier *vstemplate*.

1. Sélectionnez les fichiers inclus dans votre modèle, cliquez avec le bouton droit, puis choisissez **Envoyer vers** > **Dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier *.zip*.

1. Placez le nouveau fichier *.zip* dans le même répertoire que l’ancien fichier *.zip*.

1. Supprimez les fichiers de modèles extraits et l’ancien fichier *.zip* de modèle.

## <a name="enable-diagnostic-logging"></a>Activer la journalisation des diagnostics

Vous pouvez activer la journalisation des diagnostics pour la découverte de modèles en suivant les étapes indiquées dans [Résoudre les problèmes de découverte de modèles (extensibilité)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes de découverte de modèles (extensibilité)](../extensibility/troubleshooting-template-discovery.md)
- [Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)
- [Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
- [Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md)