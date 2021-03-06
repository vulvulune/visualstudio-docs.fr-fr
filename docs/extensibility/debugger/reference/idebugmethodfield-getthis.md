---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fc3c4a37b30d2ce7d4f5228b60d6c411afb5c9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872935"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtient le `this` (`Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) pointeur de l’objet qui contient la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

#### <a name="parameters"></a>Paramètres
 `ppClass`

 [out] Retourne un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objet représentant le pointeur « this ».

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Dans les langages orientés objet, il est généralement un pointeur implicite à l’instanciation actuelle d’une classe. Il s’agit `this` en C# / C++ et en tant que `Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Voir aussi
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)