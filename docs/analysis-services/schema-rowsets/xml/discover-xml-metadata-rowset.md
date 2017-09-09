---
title: DISCOVER_XML_METADATA-Rowset | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_XML_METADATA
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_XML_METADATA rowset
ms.assetid: 0befd026-db1b-43ac-b0e6-734abb56a4b1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d0f2a0a63ff4d08a3a273f303a956b49f4932a21
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="discoverxmlmetadata-rowset"></a>DISCOVER_XML_METADATA-Rowset
  Gibt ein XML-Dokument zurück, in dem ein angefordertes Objekt beschrieben wird. Das zurückgegebene Rowset besteht immer aus einer Zeile und einer Spalte.  
  
 Beim Aufrufen der [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) Methode mit der **DISCOVER_XML_METATDATA** Enumerationswert in der [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) Element, das **Discover**Methode gibt die **DISCOVER_XML_METATDATA** Rowset.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_XML_METADATA** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**METADATEN**|**DBTYPE_WSTR**||Ein XML-Dokument, das das von der Einschränkung angeforderte Objekt beschreibt.|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
> [!IMPORTANT]  
>  Das **DISCOVER_XML_METADATA** -Rowset kann nicht mithilfe der SELECT-Befehlssyntax abgefragt werden. Allerdings die **DISCOVER_XML_METADATA** Rowset kann abgefragt werden, mithilfe von <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_XML_METADATA** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**DatabaseID**|**DBTYPE_WSTR**|Optional.|  
|**DimensionID**|**DBTYPE_WSTR**|Optional.|  
|**CubeID**|**DBTYPE_WSTR**|Optional.|  
|**MeasureGroupID**|**DBTYPE_WSTR**|Optional.|  
|**PartitionID**|**DBTYPE_WSTR**|Optional.|  
|**PerspectiveID**|**DBTYPE_WSTR**|Optional.|  
|**DimensionPermissionID**|**DBTYPE_WSTR**|Optional.|  
|**RoleID-Wert**|**DBTYPE_WSTR**|Optional.|  
|**DatabasePermissionID**|**DBTYPE_WSTR**|Optional.|  
|**MiningModelID**|**DBTYPE_WSTR**|Optional.|  
|**MiningModelPermissionID**|**DBTYPE_WSTR**|Optional.|  
|**DataSourceID-Wert**|**DBTYPE_WSTR**|Optional.|  
|**MiningStructureID**|**DBTYPE_WSTR**|Optional.|  
|**AggregationDesignID**|**DBTYPE_WSTR**|Optional.|  
|**TraceID**|**DBTYPE_WSTR**|Optional.|  
|**MiningStructurePermissionID**|**DBTYPE_WSTR**|Optional.|  
|**CubePermissionID**|**DBTYPE_WSTR**|Optional.|  
|**AssemblyID**|**DBTYPE_WSTR**|Optional.|  
|**MdxScriptID**|**DBTYPE_WSTR**|Optional.|  
|**DataSourceViewID**|**DBTYPE_WSTR**|Optional.|  
|**DataSourcePermissionID**|**DBTYPE_WSTR**|Optional.|  
|**ObjectExpansion**|**DBTYPE_WSTR**|Optional.|  
  
 Die Einschränkung **ObjectExpansion**, steht für jedes Hauptobjekt von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Der Client verwendet normalerweise Einschränkungen, um die OLAP-Objekte zu beschreiben, für die der DDL-Code zurückgegeben wird, und er verwendet die **ObjectExpansion** -Einschränkung, um den Grad der Erweiterung im zurückgegebenen DDL-Code zu definieren. In der folgenden Tabelle angibt, ob der Enumerationswert für [Alter-Element &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) Befehle.  
  
|Enumerationswert|Description|  
|-----------------------|-----------------|  
|**' ReferenceOnly '**|Gibt nur den angeforderten Namen, den Timestamp, die ID und den Status für das angeforderte Objekt und alle nachfolgenden Hauptobjekte rekursiv zurück.|  
|**' ObjectProperties '**|Erweitert das angeforderte Objekt ohne Verweise auf enthaltene Objekte (schließt enthaltene erweiterte Nebenobjekte ein).|  
|**' ExpandObject '**|Wie *ObjectProperties*, gibt jedoch auch den Namen, die ID und den Timestamp für enthaltene Hauptobjekte zurück.|  
|**ExpandFull**|Erweitert das angeforderte Objekt vollständig rekursiv bis zum Ende eines jeden enthaltenen Objekts.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  