---
title: Installer et utiliser Visual Studio pour Mac derrière un pare-feu ou un serveur proxy
description: Ce document présente la liste des hôtes qui doivent figurer dans la liste verte du pare-feu pour permettre à Visual Studio pour Mac (et ses charges de travail, dont Xamarin) de fonctionner dans un environnement professionnel.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: asb3993
ms.author: amburns
ms.date: 10/23/2018
ms.openlocfilehash: bf12f8803fbdbbf1de31899501c31545a09d6b09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982870"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installer et utiliser Visual Studio pour Mac derrière un pare-feu ou un serveur proxy

Si vous ou votre organisation utilisez des mesures de sécurité comme un pare-feu ou un serveur proxy, vous aurez des URL de domaine à mettre sur « liste verte » et des ports et protocoles à ouvrir pour profiter d’une expérience optimale d’installation et d’utilisation de Visual Studio pour Mac et des services Azure.

- [**Installer Visual Studio pour Mac**](#install-visual-studio-for-mac) : Ces tableaux comportent les URL à mettre sur liste verte afin que vous ayez accès à toutes les fonctionnalités et charges de travail de Visual Studio pour Mac.

- [**Utiliser Visual Studio pour Mac**](#use-visual-studio-for-mac) : Ces tableaux comportent les URL à mettre sur liste verte afin que vous ayez accès à l’ensemble des services et fonctionnalités que vous souhaitez.

## <a name="install-visual-studio-for-mac"></a>Installer Visual Studio pour Mac

Dans la mesure où le programme d’installation de Visual Studio pour Mac effectue des téléchargements sur différents domaines et serveurs de téléchargement, voici les domaines et les URL que vous pouvez marquer comme approuvés dans vos configurations.

### <a name="microsoft-domains"></a>Domaines Microsoft

| Domaine| Objectif |
| ----------------------------------- |---------------------------|
| *.live.com| Gestion des informations d’identification |
| app.vssps.visualstudio.com| Métadonnées du programme d’installation|
| vortex.data.microsoft.com | Rapports d’incidents et d’erreurs |
| az667904.vo.msecnd.net| Rapports d’incidents et d’erreurs |
| xamarin.com | Métadonnées du programme d’installation|
| xampubdl.blob.core.windows.net| Packages du programme d’installation|
| download.visualstudio.microsoft.com | Packages du programme d’installation|
| xamarin.azureedge.net | Packages du programme d’installation|
| developer.xamarin.com | Packages du programme d’installation|
| dc.services.visualstudio.com| Rapports d’incidents |

### <a name="third-party-domains"></a>Domaines tiers

| Domaine| Objectif |
| --------------------------|-------------------------|
| dl.google.com | Kit de développement logiciel Android SDK |
| download.oracle.com | Kit SDK Java|
| api.apple-cloudkit.com| Services de sécurité Apple |

## <a name="use-visual-studio-for-mac"></a>Utiliser Visual Studio pour Mac

Nous vous recommandons, pour avoir accès à toutes les fonctionnalités dont vous avez besoin dans Visual Studio pour Mac derrière un proxy ou un pare-feu, de mettre sur liste verte les domaines et ports suivants.

### <a name="general"></a>Général

| Domaine | Port(s)|Objectif|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Résolution d’URL Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Données de la page de démarrage|
| software.xamarin.com |  80/443|Service de mise à jour|
| addins.monodevelop.com | 80/443| Services d’extension |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Notifications et fonctionnalité expérimentale |
| targetednotifications.azurewebsites.net|  80/443| Permet de filtrer une liste de notifications globale sur une liste qui s’applique uniquement à certains types de scénarios de machines/d’utilisation|

### <a name="identity"></a>Identité

| Domaine | Port(s)|Objectif|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Fournisseur d’identité|
| secure.aadcdn.microsoftonline-p.com | 80/443|Fournisseur d’identité|
| dc.services.visualstudio.com| 80/443|Rapports d’incidents|
| management.azure.com|80/443| API des services Azure |

### <a name="nuget"></a>NuGet

| Domaine | Port(s)|Objectif|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|API NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Fournisseur d’identité|

### <a name="android-projects"></a>Projets Android

| Domaine| Objectif|
| ------------------------------------|------------------------------------|
| time.android.com| Serveur de temps pour l’Émulateur Android |
| connectivitycheck.gstatic.com | Connectivité pour l’Émulateur Android|
| cloudconfig.googleapis.com| API pour l’Émulateur Android|

## <a name="see-also"></a>Voir aussi

- [Installer et utiliser Visual Studio et les services Azure derrière un pare-feu ou un serveur proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Résoudre des problèmes similaires sur Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
