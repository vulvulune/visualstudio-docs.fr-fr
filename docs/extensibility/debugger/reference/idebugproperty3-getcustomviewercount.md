---
title: IDebugProperty3::GetCustomViewerCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c4179b6e762d925ca918e459c5109deb6579c10
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458841"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Obtient le nombre de visionneuses personnalisées qui peuvent être disponibles pour cette propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Paramètres
`pcelt`\

 [out] Le nombre de visionneuses personnalisées disponibles pour cette propriété.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
Pour prendre en charge les visualiseurs de type, cette méthode transfère l’appel à la [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) (méthode). Si l’évaluateur d’expression prend également en charge les visionneuses personnalisées pour ce type de propriété, cette méthode ajoute le nombre de visionneuses personnalisées à la valeur retournée.

Pour plus d’informations sur les différences entre les visualiseurs de type et les visionneuses personnalisées, consultez [visualiseur de Type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Exemple
L’exemple suivant montre comment implémenter cette méthode pour un **CProperty** objet qui expose le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface.

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Voir aussi
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
