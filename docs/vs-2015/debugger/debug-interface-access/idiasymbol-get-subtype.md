---
title: IDiaSymbol::get_subType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0b3cbf77-8f11-434a-ad60-ea9829fec6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 705bbb952436c9e87e16fe0a5901472b0bbb71be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428269"
---
# <a name="idiasymbolgetsubtype"></a>IDiaSymbol::get_subType
Récupère le sous-type.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_subType(
   IDiaSymbol** pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Pointeur vers le sous-type.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)