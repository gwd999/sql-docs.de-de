---
title: GetMaxColumnsInSelect-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnsInSelect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43c428df-ef91-4f55-81c3-49a4db3379cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83833d79c2822caacd2b0b0dde09cef543933d5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596943"
---
# <a name="getmaxcolumnsinselect-method-sqlserverdatabasemetadata"></a>getMaxColumnsInSelect-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die maximale Anzahl von Spalten ab, die bei dieser Datenbank in einer SELECT-Liste zulässig sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getMaxColumnsInSelect()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der maximalen Anzahl der zulässigen Spalten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetMaxColumnsInSelect-Methode wird von der GetMaxColumnsInSelect-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
