---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6b5e1e820dc63c2f771eadf89c1afd0b0e8e3c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501858"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [MODULE_INFO_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-info-fields).  
  
Spécifie les indicateurs pour les informations de module de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Membres  
 MIF_NONE  
 Initialize/utiliser aucun des champs dans la structure.  
  
 MIF_NAME  
 Initialize/utiliser le `m_bstrName` champ dans le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) structure.  
  
 MIF_URL  
 Initialize/utiliser le `m_bstrUrl` champ dans le `MODULE_INFO` structure.  
  
 MIF_VERSION  
 Initialize/utiliser le `m_bstrVersion` champ dans le `MODULE_INFO` structure.  
  
 MIF_DEBUGMESSAGE  
 Initialize/utiliser le `m_bstrDebugMessage` champ dans le `MODULE_INFO` structure.  
  
 MIF_LOADADDRESS  
 Initialize/utiliser le `m_addrLoadAddress` champ dans le `MODULE_INFO` structure.  
  
 MIF_PREFFEREDADDRESS  
 Initialize/utiliser le `m_addrPreferredLoadAddress` champ dans le `MODULE_INFO` structure.  
  
 MIF_SIZE  
 Initialize/utiliser le `m_dwSize` champ dans le `MODULE_INFO` structure.  
  
 MIF_LOADORDER  
 Initialize/utiliser le `m_dwLoadOrder` champ dans le `MODULE_INFO` structure.  
  
 MIF_TIMESTAMP  
 Initialize/utiliser le `m_TimeStamp` champ dans le `MODULE_INFO` structure.  
  
 MIF_URLSYMBOLLOCATION  
 Initialize/utiliser le `m_bstrUrlSymbolLocation` champ dans le `MODULE_INFO` structure.  
  
 MIF_FLAGS  
 Initialize/utiliser le `m_dwModuleFlags` champ dans le `MODULE_INFO` structure.  
  
 MIF_ALLFIELDS  
 Initialize/utiliser tous les champs dans le `MODULE_INFO` structure.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont passées en tant qu’argument à la [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) méthode pour indiquer les champs de la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) structure doivent être initialisées.  
  
 Ces valeurs sont également utilisées dans le `MODULE_INFO` structure pour indiquer quels champs sont utilisés et valide.  
  
 Ces indicateurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
