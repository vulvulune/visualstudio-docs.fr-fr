---
title: CvInitProvider, fonction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5a8a9e70c85563e95037c754c59b6077ed21f28
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54771867"
---
# <a name="cvinitprovider-function"></a>CvInitProvider, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Initialise le fournisseur de marqueurs. Doit être appelée avant toute autre fonction du kit SDK du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pGuid`  
 GUID du fournisseur. Ne peut pas être Null.  
  
 `ppProvider`  
 Adresse d’une variable de sortie qui doit stocker le contexte du fournisseur. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque le fournisseur est correctement initialisé, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête** : cvmarkers.h  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)
