---
title: GetFunctions-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6032cd14cf93d75714d46bfc825d53ecc68d39b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622438"
---
# <a name="getfunctions-method-sqlserverdatabasemetadata"></a>getFunctions-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der System- und Benutzerfunktionen ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Der Name eines Katalogs in der Datenbank. Bei einer leeren Zeichenfolge ("") enthält das Ergebnis die Funktionen ohne einen Katalog. Bei **NULL** wird der Katalogname nicht für die Suche verwendet.  
  
 *schemaPattern*  
  
 Der Name eines Schemas. Bei einer leeren Zeichenfolge ("") enthält das Ergebnis die Funktionen ohne ein Schema. Bei **NULL** wird der Schemaname nicht für die Suche verwendet.  
  
 *functionNamePattern*  
  
 Der Name einer Funktion.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetFunctions-Methode wird von der GetFunctions-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Von dieser Methode werden nur die System- und Benutzerfunktionen zurückgegeben, die dem angegebenen Schema- und Funktionsnamen entsprechen.  
  
> [!IMPORTANT]  
>  Das zurückgegebene Resultset kann Funktionen enthalten, zu deren Ausführung der aufrufende Benutzer nicht berechtigt ist.  
  
 Jede Funktionsbeschreibung umfasst die folgenden Spalten:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Der Name der Datenbank, in der die Funktion gespeichert ist.|  
|FUNCTION_SCHEM|**String**|Der Name des Schemas, in dem die Funktion gespeichert ist.|  
|FUNCTION_NAME|**String**|Der Name der Funktion.|  
|NUM_INPUT_PARAMS|**int**|Reserviert für zukünftige Verwendung. Gibt derzeit den Wert "-1" zurück.|  
|NUM_OUTPUT_PARAMS|**int**|Reserviert für zukünftige Verwendung. Gibt derzeit den Wert "-1" zurück.|  
|NUM_RESULT_SETS|**int**|Reserviert für zukünftige Verwendung. Gibt derzeit den Wert "-1" zurück.|  
|REMARKS|**String**|Kommentare zur Funktion.|  
|FUNCTION_TYPE|**short**|Der Typ der Funktion. Mögliche Werte:<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
 Alle Beschreibungen im zurückgegebenen Resultset sind nach "FUNCTION_CAT", "FUNCTION_SCHEM", "FUNCTION_NAME" und "SPECIFIC_NAME" sortiert.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
