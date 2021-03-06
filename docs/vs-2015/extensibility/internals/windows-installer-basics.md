---
title: Principes fondamentaux de programme d’installation de Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516deb626bd8c6056612fcc481b9d530da504b9d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437271"
---
# <a name="windows-installer-basics"></a>Éléments de base de Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le programme d’installation de Windows installe et désinstalle des applications ou des produits logiciels sur l’ordinateur d’un utilisateur, effectuer ces tâches dans des unités appelées des composants du programme d’installation de Windows (parfois appelés WICs ou composants uniquement). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les installations à l’aide du programme d’installation de Windows.  
  
 Pour obtenir une documentation complète de Windows Installer, consultez la rubrique de la Platform SDK, [programme d’installation de Windows](/previous-versions/2kt85ked(v=vs.120)).  
  
## <a name="authoring-a-vspackage"></a>Création d’un VSPackage  
 Programme d’installation de Windows utilise des packages d’installation, qui contiennent des informations dont le programme d’installation de Windows a besoin pour installer, désinstaller ou réparer un produit et exécuter l’interface utilisateur du programme d’installation (IU). Chaque package d’installation inclut un fichier .msi, qui contient une base de données de l’installation, un flux d’informations de résumé et les flux de données de diverses parties de l’installation. Pour utiliser le programme d’installation, vous devez créer une installation. Étant donné que le programme d’installation organise les installations autour du concept de composants et stocke des informations sur l’installation dans une base de données relationnelle, le processus de la création d’un package d’installation largement implique les étapes suivantes :  
  
1. Planifier votre configuration de création pour prendre en charge de votre contrôle de version et les stratégies de côte à côte.  
  
2. Identifier les fonctionnalités qui sera présenté aux utilisateurs.  
  
3. Organiser le VSPackage et les dépendances en composants.  
  
4. Remplir la base de données de l’installation avec les informations.  
  
5. Valider le package d’installation.  
  
   Cette documentation concerne principalement les première et troisième étapes du processus. Au cours de ces étapes vous organisez vos fonctionnalités de VSPackage en WICs afin de vous pouvez le cadre de votre contrôle de version et la maintenance de stratégie pour prendre en compte pour les versions ultérieures de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Les trois étapes restantes sont traitées en détail dans la documentation du programme d’installation de Windows dans le kit Platform SDK.  
  
## <a name="key-terms"></a>Termes clés  
 Voici les définitions des termes clés liés à la technologie de programme d’installation de Windows.  
  
 Ressource  
 Fichiers, des clés de Registre, des raccourcis, ou et ainsi de suite qui peut être installé sur un ordinateur. Ces ressources sont regroupées logiquement dans des composants de programme d’installation de Windows.  
  
 Composant de programme d’installation de Windows (WIC)  
 L’unité de base d’installation représentant un regroupement logique de ressources associées qui sont installés et désinstallés en tant qu’unité. Composants du programme d’installation de Windows sont identifiés par un ID de composant unique, ou GUID. En outre, le programme d’installation de Windows maintient son décompte de références au niveau du WIC. Pour une flexibilité maximale de contrôle de version, inclure pas plus d’une ressource principale, comme une DLL, dans un WIC donné. Notez que, après avoir identifié et remplir un WIC, lui donner un GUID et le déployer, vous ne pouvez pas modifier sa composition. Pour plus d’informations, consultez [organiser les Applications en composants](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Package (package redistribuable)  
 Une unité de déploiement qui se compose d’un fichier .msi et les fichiers source externe à laquelle ce fichier peut pointer. Un package contient toutes les informations dont le programme d’installation de Windows a besoin pour exécuter l’interface utilisateur et à installer ou désinstaller l’application.  
  
 fichier .msi  
 Un fichier de stockage structuré selon COM contenant les instructions et les données requises pour installer une application. Chaque package contient au moins un fichier .msi. Le fichier .msi contient la base de données du programme d’installation, un flux d’informations résumées et éventuellement une ou plusieurs transformations et les fichiers source interne. Installation des fichiers peuvent être compressés dans un fichier CAB et stockées dans un flux de données dans le fichier .msi ou stockées, compressés ou non compressés, en dehors du fichier .msi sur le support source. Pour plus d’informations, consultez [Extensions de fichier du programme d’installation Windows](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Mise en œuvre des règles de programme d’installation Windows  
 Deux ensembles de règles déterminent le déploiement des ressources via les composants de votre installation. Un ensemble de règles est géré par le programme d’installation de Windows lui-même, tandis que vous devez appliquer le second ensemble en tant qu’auteur de l’installation.  
  
> [!NOTE]
> Mise en œuvre de règles Windows Installer se produit uniquement si vous exécutez une validation de votre fichier .msi. Néanmoins, vous sont veillé à traiter ces règles comme meilleures pratiques. Pour plus d’informations, consultez [validation d’une base de données d’Installation](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) et [Validation du Package](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Règles appliquée par le programme d’installation  
  
- Tous les fichiers dans un composant donné doivent être installés dans le même répertoire. À l’inverse, les fichiers installés pour séparer les dossiers doivent appartenir pour séparer les composants.  
  
- Il peut y avoir qu’un seul chemin de clé par composant. Le chemin de clé est simplement une fichier ou clé de Registre qui représente le composant dans son intégralité.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilités du fournisseur de composants  
  
- Toutes les deux ressources qui peut être fourni séparément dans les versions ultérieures doivent exister dans des composants distincts. Ressources doivent être regroupés dans le même composant uniquement lorsque vous êtes certain que ces ressources ne seront jamais disponible séparément. En fait, il est recommandé que toutes les principales ressources (DLL, par exemple) existent toujours dans WICs distincts. Pour plus d’informations, consultez [définissant les composants de programme d’installation](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
- Aucune ressource de version ne doit expédier jamais dans plusieurs WIC.  
  
## <a name="see-also"></a>Voir aussi  
 [Que se passe-t-il si les règles de composant sont interrompues ?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)
