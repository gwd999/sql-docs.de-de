---
title: EnvelopeAggregate (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geometry)
ms.assetid: c4c15abe-0fe9-441d-9d42-6572e264869c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00b45ed5ff3fcefbd803ecbb6d50aefbda20aaa0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761028"
---
# <a name="envelopeaggregate-geometry-data-type"></a>EnvelopeAggregate (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Gibt für einen angegebenen Satz von **geometry** -Objekten einen Begrenzungsrahmen zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
EnvelopeAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Argumente  
 *geometry_operand*  
 Eine Tabellenspalte vom Typ **geometry** , die den Satz von **geometry** -Objekten darstellt.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
## <a name="exceptions"></a>Ausnahmen  
 Löst eine `FormatException` aus, wenn ungültige Eingabewerte vorhanden sind. Weitere Informationen finden Sie unter [STIsValid &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt **null** zurück, wenn die Eingabe leer ist oder andere SRIDs aufweist. Weitere Informationen finden Sie unter [SRIDs &#40;Spatial Reference Identifiers&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 Diese Methode ignoriert **null** -Eingaben.  
  
> [!NOTE]  
>  Diese Methode gibt **null** zurück, wenn alle eingegebenen Werte **null**sind.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Begrenzungsrahmen für einen Satz von Objekten in der Variablenspalte einer Tabelle zurückgegeben.  
  
 ```
 -- Setup table variable for EnvelopeAggregate example 
DECLARE @Geom TABLE 
( 
shape geometry, 
shapeType nvarchar(50) 
) 
INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'), 
('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle'); 
-- Perform EnvelopeAggregate on @Geom.shape column 
SELECT geometry::EnvelopeAggregate(shape).ToString() 
FROM @Geom;
 ```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte statische geometry-Methoden](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

