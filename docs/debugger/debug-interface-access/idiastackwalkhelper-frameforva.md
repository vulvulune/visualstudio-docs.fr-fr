---
title: IDiaStackWalkHelper::frameForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::frameForVA method
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03607cec9b314f4f6e329a3150d097f8a2186705
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838026"
---
# <a name="idiastackwalkhelperframeforva"></a>IDiaStackWalkHelper::frameForVA
Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT frameForVA( 
   ULONGLONG        va,
   IDiaFrameData**  ppFrame
);
```

#### <a name="parameters"></a>Paramètres
 `va`

[in] L’adresse virtuelle pour les données de trame.

 `ppFrame`

[out] Un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet qui représente le frame de pile à l’adresse spécifiée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)