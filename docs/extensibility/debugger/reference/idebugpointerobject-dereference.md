---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f01e863d03f6179ef4c15f50521cc72ba21f5740
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842689"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtient l’objet désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwIndex`  
 [in] Un décalage d’octet simple à partir du début de l’objet désigné.  
  
 `ppObject`  
 [out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de l’objet qui représente l’objet vers lequel pointe, ainsi que décalage, le cas échéant.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si cet objet ne pointe pas vers un autre objet.  
  
## <a name="remarks"></a>Notes  
 L’objet vers lequel pointé peut être un type primitif ou un type plus complexe comme une classe ou structure.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
