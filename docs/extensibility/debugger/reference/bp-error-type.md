---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2964c833abfa25b57678680f8b821f992cb31de8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689185"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Spécifie le type d’erreur d’un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="members"></a>Membres
BPET_NONE ne spécifie aucune erreur de point d’arrêt.

BPET_TYPE_WARNING spécifie une erreur de point d’arrêt de style de l’avertissement.

BPET_TYPE_ERROR spécifie une erreur de point d’arrêt de style d’erreur.

BPET_SEV_HIGH spécifie une erreur de point d’arrêt de niveau de gravité élevé.

BPET_SEV_GENERAL spécifie une erreur de point d’arrêt de gravité moyenne.

BPET_SEV_LOW spécifie une erreur de point d’arrêt de faible gravité.

BPET_TYPE_MASK spécifie une erreur de point d’arrêt de style de masque.

BPET_SEV_MASK spécifie une erreur de point d’arrêt de la gravité de type masque.

BPET_GENERAL_WARNING spécifie une erreur de point d’arrêt général de type avertissement.

BPET_GENERAL_ERROR spécifie une erreur de point d’arrêt de style d’erreur général.

BPET_ALL Spécifie tous les types d’erreurs de point d’arrêt.

## <a name="remarks"></a>Notes
Ces valeurs peuvent être combinées avec un opérateur de bits `OR` et utilisé pour le `dwType` membre de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) structure. Passé en tant que paramètre à la [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) (méthode).

Un type d’erreur de point d’arrêt se compose d’un type et un niveau de gravité. Cela signifie qu’un type d’erreur de point d’arrêt n’est jamais simplement un type (par exemple, `BPET_TYPE_ERROR`,) ou un niveau de gravité (par exemple, `BPET_SEV_GENERAL`) par lui-même. `BPET_GENERAL_WARNING` et `BPET_GENERAL_ERROR` fournir des valeurs prédéfinies pour les points d’arrêt générales de l’avertissement et erreur.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
