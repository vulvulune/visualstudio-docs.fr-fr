---
title: IRemoteDebugApplication110::GetMainThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a4b51d87f89d77bebf065ce5f52a297ada333d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383501"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Retourne le thread principal pour les ordinateurs hôtes qui appellent [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), sinon retourne E_FAIL.  
  
> [!IMPORTANT]
> [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppThread`  
 [out] La principale [IRemoteDebugApplicationThread (Interface)](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplication (Interface)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)