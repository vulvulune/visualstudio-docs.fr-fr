---
title: Collecte de statistiques d’applications pour les services en utilisant la méthode d’échantillonnage du profileur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9e71f1d8219f61946bc8242514429130530fb12
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440247"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Collecter des statistiques d’application des services en utilisant la méthode d’échantillonnage du profileur
Cette section décrit les procédures et les options de collecte des statistiques de performances des services Windows utilisant la méthode d’échantillonnage à partir de la ligne de commande.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Attacher le profileur à un service .NET**|-   [Guide pratique pour attacher le profileur à un service .NET pour collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Ajouter des interactions de couche**|-   [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Attacher le profileur à un service C/C++**|-   [Guide pratique pour attacher le profileur à un service natif pour collecter des statistiques d’applications](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tâches connexes

### <a name="profile-windows-services"></a>Profiler des services Windows

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler à l’aide de la méthode d’instrumentation**|-   [Collecter les données temporelles détaillées à l’aide de l’instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profiler l’allocation de mémoire .NET et le garbage collection**|-   [Collecter des données de mémoire .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profiler le conflit des ressources et l’activité des threads**|-   [Collecter des données concurrentielles](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Profiler à l’aide de la méthode d’échantillonnage

|Tâche|Contenu associé|
|----------|---------------------|
|**Profiler des applications autonomes (clientes)**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profiler des applications web ASP.NET**|-   [Collecter des statistiques d’applications en utilisant l’échantillonnage](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analyser des vues et des rapports de données d’échantillonnage
- [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)
