---
title: Dimension-Element (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Dimension Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension element
ms.assetid: 71886014-f463-4b70-a2a2-d9e5053ba4f0
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77985556c9de25bbe2cfcf22d2e3f7fda1c6d4b6
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="dimension-element-assl"></a>Dimension-Element (ASSL)
  Definiert eine Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimensions>  
   <Dimension xsi:type="Dimension">...</Dimension> <!-- ancestor: Database -->  
   <!-- or -->  
   <Dimension xsi:type="AggregationDimension">...</Dimension> <!-- ancestor: Aggregation -->  
   <!-- or -->  
   <Dimension xsi:type="AggregationDesignDimension">...</Dimension> <!-- ancestor: AggregationDesign -->  
   <!-- or -->  
   <Dimension xsi:type="AggregationInstanceCubeDimension">...</Dimension> <!-- ancestor: AggregationInstance -->  
      <!-- or -->  
   <Dimension xsi:type="CubeDimension">...</Dimension> <!-- ancestor: Cube -->  
      <!-- or -->  
   <Dimension xsi:type="MeasureGroupDimension">...</Dimension> <!-- ancestor: MeasureGroup -->  
   <!-- or -->  
   <Dimension xsi:type="PerspectiveDimension">...</Dimension> <!-- ancestor: Perspective -->  
</Dimensions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Finden Sie in der folgenden Tabelle aus.|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|------------------------|---------------|  
|[Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md)|[Dimension](../../../analysis-services/scripting/data-type/dimension-data-type-assl.md)|  
|[Aggregation](../../../analysis-services/scripting/objects/aggregation-element-assl.md)|[AggregationDimension](../../../analysis-services/scripting/data-type/aggregationdimension-data-type-assl.md)|  
|[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)|[AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)|  
|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|[AggregationInstanceCubeDimension](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|[MeasureGroup-Objekt](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|  
|[Perspektive](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die entsprechenden Elemente im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.AggregationDimension>, <xref:Microsoft.AnalysisServices.AggregationDesignDimension>, <xref:Microsoft.AnalysisServices.CubeDimension>, <xref:Microsoft.AnalysisServices.MeasureGroupDimension>, und <xref:Microsoft.AnalysisServices.PerspectiveDimension>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  