---
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daf0b48aca06b404824059030052223a8545a6b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839704"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Reçoit des rappels de symbole DIA procédure de localisation, ce qui permet de restrictions à imposer sur le processus de localisation.

## <a name="syntax"></a>Syntaxe

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes dans le [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interface, cette interface expose les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Détermine si la recherche d’un fichier .pdb dans le répertoire de débogage d’origine.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Détermine si la recherche d’un fichier .pdb est autorisée dans le chemin d’accès où se trouve le fichier .exe.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Détermine si vous recherchez des informations de débogage est autorisé à partir de fichiers .dbg.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Détermine si la recherche des fichiers .pdb est autorisée dans le répertoire racine du système.|

## <a name="remarks"></a>Notes
 L’application cliente implémente cette interface et fournit une référence à celle-ci dans l’appel à la [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode). N’oubliez pas d’implémenter toutes les méthodes dans le [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interface également.

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2.h

 Bibliothèque : diaguids.lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)