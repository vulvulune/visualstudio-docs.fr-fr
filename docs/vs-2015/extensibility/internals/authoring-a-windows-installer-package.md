---
title: Création d’un Package de programme d’installation de Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 30c941fd4f3c281dfe363d284a559bafe055451c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001642"
---
# <a name="authoring-a-windows-installer-package"></a>Création d’un package Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les lecteurs de données du modèle de programme d’installation de Windows. Au lieu d’écrire un script de procédure pour copier des fichiers et écrire des entrées de Registre, par exemple, vous créer des lignes et des colonnes dans les tables de base de données qui contiennent des données de fichiers et du Registre.  
  
## <a name="database-entries"></a>Entrées de la base de données  
 Pour installer un package Visual Studio, un package Windows Installer doit contenir des entrées de base de données pour effectuer les tâches suivantes :  
  
- Rechercher le système pour localiser les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] votre VSPackage prend en charge (à l’aide de tables de programme d’installation de Windows qui incluent AppSearch CompLocator, RegLocator, DrLocator et Signature).  
  
- Annuler l’installation si aucune version prise en charge de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est installé ou si un autre système du VSPackage ne sont pas remplies (à l’aide de la table LaunchCondition).  
  
- Installez le VSPackage et les fichiers dépendants (à l’aide de l’annuaire, composant et tables de fichiers).  
  
- Ajoutez les informations appropriées pour le VSPackage dans le Registre (à l’aide de la table de Registre).  
  
- Intégrer le VSPackage dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en appelant **devenv.exe /setup** (à l’aide de la table CustomAction).  
  
  Pour plus d’informations, consultez [programme d’installation de Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Outils d’installation  
 Une variété d’outils de d’installation tiers fournissent un environnement de développement pour les packages de programme d’installation de Windows. Deux outils gratuits sont les suivantes :  
  
- Installshield Limited Edition  
  
   Vous pouvez obtenir une version limitée de InstallShield via Visual Studio **nouveau projet** boîte de dialogue. Développez **autres Types de projets** , puis sélectionnez **le programme d’installation et de déploiement**. Sélectionnez le modèle de InstallShield.  
  
- ensemble d'outils XML de Windows Installer  
  
   L’ensemble d’outils génère des packages de programme d’installation de Windows à partir des fichiers de source XML. L’ensemble d’outils est un projet open source de Microsoft. Vous pouvez télécharger le code source et les exécutables à partir de [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
  Pour les produits commerciaux qui s’intègrent dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à l’aide de la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], consultez [ https://marketplace.visualstudio.com/ ](https://marketplace.visualstudio.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
