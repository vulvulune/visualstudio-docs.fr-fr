---
title: Visualisation et affichage des données | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 852616ac77096a5b31078d64051f67f6cbb3ecb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912827"
---
# <a name="visualizing-and-viewing-data"></a>Visualisation et affichage des données
Visualiseurs de type et les visionneuses personnalisées présentent les données de manière significative rapidement à un développeur. L’évaluateur d’expression (EE) peut prendre en charge les visualiseurs de types de fournisseurs tiers ainsi que fournir ses propres visionneuses personnalisées.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Détermine combien des visualiseurs de type et des visionneuses personnalisées sont associées avec le type d’objet en appelant le [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) (méthode). Si le visualiseur d’au moins un type ou de la visionneuse personnalisée est disponible, Visual Studio appelle le [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour récupérer une liste de ces visualiseurs et les visionneuses (méthode) (en fait, une liste de s qui implémente les visualiseurs et visionneuses) et les présente à l’utilisateur.

## <a name="supporting-type-visualizers"></a>Prise en charge les visualiseurs de type
 Il existe un nombre d’interfaces que le EE doit implémenter pour prendre en charge les visualiseurs de type. Ces interfaces peuvent être divisés en deux grandes catégories : les interfaces qui répertorient les visualiseurs de type et les interfaces qui accèdent aux données de la propriété.

### <a name="listing-type-visualizers"></a>Visualiseurs de type de liste
 Prend en charge de la EE répertoriant les visualiseurs de type dans son implémentation de `IDebugProperty3::GetCustomViewerCount` et `IDebugProperty3::GetCustomViewerList`. Ces méthodes passent l’appel aux méthodes correspondantes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 Le [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) est obtenu en appelant [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Cette méthode requiert le [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interface, qui est obtenue à partir de la [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interface transmise au [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` requiert également le [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) et [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaces, qui ont été passés à `IDebugParsedExpression::EvaluateSync`. L’interface finale requise pour créer le `IEEVisualizerService` interface est la [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface qui implémente le EE. Cette interface permet aux modifications à apporter à la propriété qui est affichée. Toutes les données de propriété est encapsulé dans un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interface, ce qui est également implémentée par le EE.

### <a name="accessing-property-data"></a>L’accès aux données de propriété
 L’accès aux données de propriété s’effectue via le [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Pour obtenir cette interface, Visual Studio appelle [QueryInterface](/cpp/atl/queryinterface) sur l’objet de propriété à obtenir le [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface (implémenté sur le même objet qui implémente le [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface), puis appelle la [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) méthode pour obtenir le `IPropertyProxyEESide` interface.

 Toutes les données transmises dans et hors de la `IPropertyProxyEESide` interface est encapsulée dans le [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interface. Cette interface représente un tableau d’octets et est implémentée par Visual Studio et le Java EE. Lorsque les données d’une propriété doit être modifié, Visual Studio crée un `IEEDataStorage` objet contenant les nouvelles données et les appels [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) avec cet objet de données afin d’obtenir un nouveau `IEEDataStorage` objet qui, à son tour, est passé à [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) pour mettre à jour les données de la propriété. `IPropertyProxyEESide::CreateReplacementObject` permet la EE instancier sa propre classe qui implémente le `IEEDataStorage` interface.

## <a name="supporting-custom-viewers"></a>Prise en charge des visionneuses personnalisées
 L’indicateur `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` est défini dans le `dwAttrib` champ la [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) structure (retourné par un appel à [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) pour indiquer que l’objet a une visionneuse personnalisée associée avec elle. Lorsque cet indicateur est défini, Visual Studio obtient les [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) de l’interface à partir de la [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) à l’aide de l’interface [QueryInterface](/cpp/atl/queryinterface).

 Si l’utilisateur sélectionne une visionneuse personnalisée, Visual Studio instancie la visionneuse personnalisée à l’aide de la visionneuse `CLSID` fourni par le `IDebugProperty3::GetCustomViewerList` (méthode). Visual Studio appelle ensuite [une valeur d’affichage](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) pour afficher la valeur à l’utilisateur.

 Normalement, `IDebugCustomViewer::DisplayValue` présente une vue en lecture seule des données. Pour autoriser les modifications sur les données, le EE doit implémenter une interface personnalisée qui prend en charge la modification des données sur un objet de propriété. Le `IDebugCustomViewer::DisplayValue` méthode utilise cette interface personnalisée pour prendre en charge la modification des données. La méthode recherche l’interface personnalisée le `IDebugProperty2` interface transmis en tant que le `pDebugProperty` argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Prise en charge les visualiseurs de type et les visionneuses personnalisées
 Un EE peut prendre en charge les visualiseurs de type et des visionneuses personnalisées dans le [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) méthodes. Tout d’abord, le EE ajoute le nombre de visionneuses personnalisées qui il fournit à la valeur retournée par la [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) (méthode). En second lieu, le EE ajoute le `CLSID`s de ses propres visionneuses personnalisées à la liste retournée par la [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [Visualiseur de type et visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)