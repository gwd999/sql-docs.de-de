---
title: PDOStatement::fetchColumn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6ebf385c-ddb0-4c53-9dc6-7df0d3740b04
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ab2eaab547e582df30375a4caadbc96a11f4396
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603080"
---
# <a name="pdostatementfetchcolumn"></a>PDOStatement::fetchColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt eine Spalte in einer Zeile zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
string PDOStatement::fetchColumn ([ $column_number ] );  
```  
  
#### <a name="parameters"></a>Parameter  
$*column_number*: Eine optionale ganze Zahl, die die nullbasierte Spaltennummer angibt. Der Standardwert ist 0 (die erste Spalte in der Zeile).  
  
## <a name="return-value"></a>Rückgabewert  
Eine Spalte oder „false“, wenn keine weiteren Zeilen vorhanden sind.  
  
## <a name="remarks"></a>Remarks  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   while ( $result = $stmt->fetchColumn(1)) {   
      print($result . "\n");   
   }  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
