---
title: Personnalisation des vérifications natives à l’exécution | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 66591308c2b0c59cf310d3957131f80191cc51c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905484"
---
# <a name="native-run-time-checks-customization"></a>Personnalisation des contrôles natifs à l'exécution
Lorsque vous compilez avec **/RTC** (contrôles d’exécution) ou utilisez le `runtime_checks` pragma, la bibliothèque Runtime C fournit les contrôles natifs à l’exécution. Dans certains cas, il est utile de personnaliser le contrôle à l'exécution :

- Pour acheminer des messages de contrôle à l'exécution vers d'autres emplacements que le fichier ou la destination par défaut.

- Pour spécifier une destination de sortie en cas de messages de contrôle à l'exécution venant d'un débogueur tiers.

- Pour rapporter des messages de contrôle à l’exécution en provenance d’un programme compilé avec une version Release de la bibliothèque Runtime C. Les versions finales de la bibliothèque n'utilisent pas `_CrtDbgReportW` pour rapporter les erreurs d'exécution. Elles affichent à la place une boîte de dialogue **Assert** par erreur d’exécution.

  Pour personnaliser le contrôle des erreurs d'exécution, vous pouvez :

- Écrire une fonction permettant d'obtenir un rapport sur les erreurs d'exécution. Pour plus d'informations, voir [Procédure : Écrire une fonction permettant d’obtenir un rapport sur les erreurs d’exécution](../debugger/how-to-write-a-run-time-error-reporting-function.md).

- Personnaliser la destination des messages d'erreur.

- Demander des informations sur les erreurs de contrôle à l'exécution.

## <a name="customize-the-error-message-destination"></a>Personnaliser la destination des messages d'erreur
 Si vous utilisez `_CrtDbgReportW` pour rapporter des erreurs, vous pouvez utiliser `_CrtSetReportMode` pour spécifier la destination des messages d'erreur.

 Si vous utilisez une fonction personnalisée pour obtenir vos rapports, associez une erreur à un type de rapport à l'aide de `_RTC_SetErrorType`.

## <a name="query-for-information-about-run-time-checks"></a>Demander des informations sur les contrôles à l'exécution
 `_RTC_NumErrors` retourne le nombre de types d’erreurs détectés par les vérifications des erreurs au moment de l’exécution. Pour obtenir une brève description de chaque erreur, faites une boucle allant de 0 à la valeur de retour `_RTC_NumErrors`, en transmettant, à chaque boucle, la valeur de l'itération à `_RTC_GetErrDesc`. Pour plus d’informations, consultez [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) et [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour utiliser les vérifications natives à l’exécution](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)