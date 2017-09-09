---
title: CurveToLineWithTolerance (Geography-Datentyp) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CurveToLineWithTolerance_TSQL
- CurveToLineWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- CurveToLineWithTolerance method (geography)
ms.assetid: 74369c76-2cf6-42ae-b9cc-e7a051db2767
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 712ba7cb9705769ae805503a47880d5f349351d1
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="curvetolinewithtolerance-geography-data-type"></a>CurveToLineWithTolerance (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt eine polygonale Näherung einer Instanz von **geography** mit Kreisbogensegmenten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.CurveToLineWithTolerance( tolerance, relative )  
```  
  
## <a name="arguments"></a>Argumente  
 *Fehlertoleranz*  
 Ein **double** -Ausdruck, der die maximalen Fehler zwischen dem ursprünglichen Kreisbogensegment und der linearen Näherung definiert.  
  
 *relative*  
 Ein **bool** -Ausdruck, der angibt, ob ein relatives Maximum für die Abweichung verwendet werden soll. Wenn der relativer Wert auf false (0) festgelegt wird, wird ein absolutes Maximum für die Abweichung verwendet, die eine lineare Näherung aufweisen kann.  Wenn der relative Wert auf true (1) festgelegt wird, wird die Toleranz als Produkt des tolerance-Parameters und des Durchmessers des Begrenzungsrahmens für das räumliche Objekt berechnet.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Rückgabetyp: **Geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="exceptions"></a>Ausnahmen  
 Festlegen der Toleranz < = 0 löst eine **ArgumentOutOfRange** Ausnahme.  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode kann ein Umfang für die Fehlertoleranz in der resultierenden **LineString**angegeben werden.  
  
 Die**CurveToLineWithTolerance** -Methode gibt eine **LineString** -Instanz für eine **CircularString** oder eine **CompoundCurve** -Instanz und eine **Polygon** -Instanz für eine **CurvePolygon** -Instanz zurück.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. Verwenden verschiedener Toleranzwerte in einer CircularString-Instanz  
 Im folgenden Beispiel wird gezeigt, wie sich das Festlegen der Toleranz auf eine Instanz von `LineString`auswirkt, die von einer Instanz von `CircularString` zurückgegeben wird:  
  
 `DECLARE @g geography;`  
  
 `SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();`  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>B. Verwenden der Methode in einer MultiLineString-Instanz mit einem LineString  
 Im folgenden Beispiel wird die Rückgabe einer Instanz von `MultiLineString` gezeigt, die nur eine `LineString` -Instanz enthält:  
  
 `DECLARE @g geography;`  
  
 `SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649))');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();`  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>C. Verwenden der Methode in einer MultiLineString-Instanz mit mehreren LineStrings  
 Im folgenden Beispiel wird die Rückgabe einer Instanz von `MultiLineString` gezeigt, die mehrere `LineString` -Instanzen enthält:  
  
 `DECLARE @g geography;`  
  
 `SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649),(-123.358 47.653, -123.348 47.649))');`  
  
 `SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();`  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>D. Festlegen des relativen Werts für eine aufrufende CurvePolygon-Instanz auf true  
 Im folgenden Beispiel wird eine Instanz von `CurvePolygon` verwendet, um `CurveToLineWithTolerance()` mit *relative* und dem Wert true aufzurufen:  
  
 `DECLARE @g geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658), (-122.348 47.658, -122.358 47.658, -122.358 47.653)))';`  
  
 `SELECT @g.CurveToLineWithTolerance(.5,1).ToString();`  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Methoden für Geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  