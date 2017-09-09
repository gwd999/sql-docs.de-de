---
title: Erstellen von XML-INDEX (selektive XML-Indizes) | Microsoft Docs
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1f510151-41d5-45c2-9cd0-b1ca0246fffe
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 02b6c4b19007ecce500046ce6f3824abf9956309
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="create-xml-index-selective-xml-indexes"></a>CREATE XML INDEX (selektive XML-Indizes)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Erstellt einen neuen sekundären selektiven XML-Index für einen einzelnen Pfad, der bereits von einem vorhandenen selektiven XML-Index indiziert wird. Sie können auch primäre selektive XML-Indizes erstellen. Informationen finden Sie unter [Create, Alter und Drop selektive XML-Indizes](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE XML INDEX index_name  
    ON <table_object> ( xml_column_name )  
    USING XML INDEX sxi_index_name  
    FOR ( <xquery_or_sql_values_path> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<xquery_or_sql_values_path>::=   
<path_name>   
  
<path_name> ::=   
character string literal  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
xmlnamespace_uri AS xmlnamespace_prefix  
  
<index_options> ::=   
(    
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Argumente  
 *index_name*  
 Ist der Name des neuen Indexes zu erstellen. Indexnamen müssen innerhalb einer Tabelle eindeutig sein, können aber innerhalb einer Datenbank mehrfach vorkommen. Indexnamen müssen den Regeln der [Bezeichner](../../relational-databases/databases/database-identifiers.md).  
  
 ON  *\<Table_object >* ist die Tabelle, die die Spalte XML-Index enthält. Sie können die folgenden Formate verwenden:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
 *xml_column_name*  
 Der Name der XML-Spalte, die den zu indizierenden Pfad enthält.  
  
 USING XML INDEX *Sxi_index_name*  
 Der Name des vorhandenen selektiven XML-Indexes.  
  
 FÜR **(** \<Xquery_or_sql_values_path > **)** ist der Name des indizierten Pfads auf dem sekundären selektiven XML-Index erstellt. Der zu indizierende Pfad entspricht dem zugewiesenen Namen aus der CREATE SELECTIVE XML INDEX-Anweisung. Weitere Informationen finden Sie unter [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
 MIT \<Index_options > Informationen zu den Indexoptionen finden Sie unter [CREATE XML INDEX](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>Hinweise  
 In jeder XML-Spalte der Basistabelle kann es mehrere sekundäre selektive XML-Indizes geben.  
  
## <a name="limitations-and-restrictions"></a>Einschränkungen  
 Für eine XML-Spalte muss ein selektiver XML-Index vorhanden sein, bevor sekundäre selektive XML-Indizes für die Spalte erstellt werden können.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung in der Tabelle oder Sicht. Der Benutzer muss ein Mitglied der festen Serverrolle **sysadmin** bzw. der festen Datenbankrollen **db_ddladmin** und **db_owner** sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein sekundärer selektiver XML-Index für den Pfad `pathabc`erstellt. Der zu indizierende Pfad entspricht dem zugewiesenen Namen aus der [CREATE SELECTIVE XML INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
```  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR ( pathabc );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Selektive XML-Indizes &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Erstellen, Ändern und Löschen sekundärer, selektiver XML-Indizes](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)  
  
  

