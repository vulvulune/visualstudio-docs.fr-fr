---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 963ee64b639780bae60a4c2655db8b666d87c702
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554246"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Fournit un mappage d’adresses pour prendre en charge les traductions de disposition d’image.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Paramètres
 `cbData`

[in] Le nombre d’éléments dans le `data` paramètre.

 `data[]`

[in] Un tableau de [diaaddressmapentry, Structure](../../debugger/debug-interface-access/diaaddressmapentry.md) structures qui définissent le mappage de conversion.

 `imagetoSymbols`

[in] `TRUE` si le `data` paramètre définit un mappage à partir de la nouvelle disposition de l’image à la disposition d’origine (comme indiqué par les symboles de débogage). `FALSE` Si `data` est un mappage de la nouvelle disposition d’image extraite de la disposition d’origine.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 En règle générale, le DIA récupère les mappages de traduction d’adresse à partir du fichier de base de données (.pdb) de programme. Si ces valeurs sont manquantes, le [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) méthode est appelée à deux reprises, une fois avec le `imagetoSymbols` paramètre défini sur `TRUE` et une fois avec le `imagetoSymbols` paramètre défini sur `FALSE`. Mappage des traductions d’adresses ne peut pas être activées à l’aide de la [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) (méthode), sauf si les deux cartes de traduction sont fournies.

## <a name="see-also"></a>Voir aussi
- [DiaAddressMapEntry, structure](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)