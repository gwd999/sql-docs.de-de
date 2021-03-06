---
title: Parameter (ADO / WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad7331fbbfed123da5d7121d83558ba4bbabc912
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527253"
---
# <a name="parameter-ado---wfc-syntax"></a>Parameter (ADO/WFC-Syntax)
## <a name="package-commswfcdata"></a>Paket com.ms.wfc.data  
  
### <a name="constructor"></a>Konstruktor  
  
```  
public Parameter()  
public Parameter(String name)  
public Parameter(String name, int type)  
public Parameter(String name, int type, int dir)  
public Parameter(String name, int type, int dir, int size)  
public Parameter(String name, int type, int dir, int size, Object value)  
```  
  
### <a name="methods"></a>Methoden  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getDirection()  
public void setDirection(int dir)  
public String getName()  
public void setName(String name)  
public int getNumericScale()  
public void setNumericScale(int scale)  
public int getPrecision()  
public void setPrecision(int prec)  
public int getSize()  
public void setSize(int size)  
public int getType()  
public void setType(int type)  
public com.ms.com.Variant getValue()  
public void setValue(Object v)  
public AdoProperties getProperties()  
```  
  
## <a name="parameter-accessor-methods"></a>Parameter-Zugriffsmethoden  
 Die [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft eine [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt ruft ab oder legt den Inhalt dieses Objekts fest. Der Inhalt wird als eine Variante, eine Art von Objekt, das ein Wert zugewiesen werden kann und alle mit verschiedenen Datentypen dargestellt.  
  
 ADO/WFC-implementiert die **Wert** Eigenschaft mit dem die **"GetValue"** Methode, die ein VARIANT-Objekt zurückgibt und die **SetValue** Methode, die einen Variant-Wert als Argument akzeptiert. Varianten werden möglichst effizient in bestimmten Sprachen wie z. B. Microsoft Visual Basic.  
  
 Zusätzlich zu den **Wert** Eigenschaft ADO/WFC-bietet *Accessor* Methoden, mit denen Java-Datentypen zu erhalten, und legen Sie den Inhalt der **Parameter** Objekte. Die meisten dieser Methoden haben Namen im Format **erhalten**_DataType_ oder **festgelegt**_DataType_.  
  
 Es ist eine wichtige Ausnahme: Gibt es keine **GetNull** Eigenschaft; stattdessen wird eine **IsNull** -Eigenschaft, die gibt einen booleschen Wert, der angibt, ob das Feld null ist.  
  
```  
public boolean getBoolean()  
public void setBoolean(boolean v)  
public byte getByte()  
public void setByte(byte v)  
public double getDouble()  
public void setDouble(double v)  
public float getFloat()  
public void setFloat(float v)  
public int getInt()  
public void setInt(int v)  
public long getLong()  
public void setLong(long v)  
public short getShort()  
public void setShort(short v)  
public String getString()  
public void setString(String v)  
public boolean isNull()  
public void setNull()  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Parameter-Objekt](../../../ado/reference/ado-api/parameter-object.md)
