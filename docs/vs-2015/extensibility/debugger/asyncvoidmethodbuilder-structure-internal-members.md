---
title: Structure AsyncVoidMethodBuilder - membres internes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 770e66c4136379a24cee349b04fcc06f5278a379
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953554"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Structure AsyncVoidMethodBuilder - Membres internes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> rubrique de référence.  
  
 **Espace de noms :** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membres internes  
  
|Nom|Description|  
|----------|-----------------|  
|[Propriété de ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtient un objet qui peut être utilisé pour identifier de manière unique ce générateur au débogueur.|  
|[champ de m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Représente l’objet initialisée tardivement utilisé par le débogueur pour identifier de manière unique ce générateur.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Valeurs internes d’extension parallèle pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
