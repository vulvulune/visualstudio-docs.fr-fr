---
title: Création de fichiers de données de profilage portables à partir de la ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434293"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Création de fichiers de données de profilage portables à partir de la ligne de commande
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour faciliter le partage des données de profilage, vous pouvez utiliser l’outil en ligne de commande [VSPerfReport](../profiling/vsperfreport.md) visant à incorporer les symboles pour une exécution de profilage dans le fichier .vsp.  
  
 Vous pouvez également créer un fichier de données de profilage pré-analysé (.vsps), plus petit et donc plus rapide à charger dans l’IDE.  
  
> [!NOTE]
> Vérifiez que les fichiers de symboles (.pdb) sont disponibles pour **VSPerfReport**. Pour plus d'informations, voir [Procédure : Spécifier les emplacements de fichier de symboles à partir de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Pour plus d’informations sur le chemin de **VSReport**, consultez [Spécification du chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Les données de profilage d’un fichier .vsps ne peuvent pas être filtrées.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Pour incorporer les symboles d’une exécution de profilage dans un fichier de données de profilage (.vsp)  
  
- Dans une fenêtre d’invite de commandes, tapez la commande suivante :  
  
   \<Chemin><strong>VSPerfReport \<</strong>Fichier VSP> **/PackSymbols**  
  
   Par défaut, le fichier .vsps est nommé d’après le nom de base du fichier .vsp. Vous pouvez spécifier un autre nom avec l’option **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Pour créer un fichier récapitulatif des données de profilage  
  
- Dans une fenêtre d’invite de commandes, tapez la commande suivante :  
  
   \<Chemin><strong>VSPerfReport \<</strong>Fichier VSP> **/SummaryFile** [**/Output:**\<Nom de fichier>]  
  
   Par défaut, le fichier .vsps est nommé d’après le nom de base du fichier .vsp. Vous pouvez spécifier un autre nom avec l’option **Output**.
