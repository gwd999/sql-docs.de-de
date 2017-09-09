---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f15d9d23726f7558f0bf73aff3f8c3c5253cb24d
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den Meldungstext des Fehlers zurück, der die Ausführung des CATCH-Blockes eines TRY…CATCH-Konstrukts verursacht hat.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Aufruf in einem CATCH-Block den vollständigen Meldungstext des Fehlers zurück, der die Ausführung des CATCH-Blockes verursacht hat. Der Text umfasst die Werte, die für alle ersetzbaren Parameter angegeben werden, wie z. B. Längen, Objektnamen oder Zeitangaben.  
  
 Gibt NULL zurück, wenn die Funktion außerhalb des Bereichs eines CATCH-Blockes aufgerufen wird.  
  
## <a name="remarks"></a>Hinweise  
 ERROR_MESSAGE kann an jeder beliebigen Position im Bereich eines CATCH-Blockes aufgerufen werden.  
  
 ERROR_MESSAGE gibt die Fehlermeldung unabhängig davon zurück, wie oft oder wo im Bereich des CATCH-Blockes die Funktion aufgerufen wird. Dies steht im Gegensatz zu Funktionen, wie etwa @@ERROR, die nur eine Fehlernummer zurückgibt, in der Anweisung unmittelbar auf das Projekt, das einen Fehler verursacht hat, oder die erste Anweisung eines catch-block.  
  
 In geschachtelten CATCH-Blöcken gibt ERROR_MESSAGE die Fehlermeldung für den Bereich des CATCH-Blockes zurück, in dem auf die Funktion verwiesen wird. Beispielsweise könnte der CATCH-Block eines äußeren TRY...CATCH-Konstrukts ein geschachteltes TRY...CATCH-Konstrukt aufweisen. Innerhalb des geschachtelten CATCH-Blockes gibt ERROR_MESSAGE die Meldung des Fehlers zurück, der den geschachtelten CATCH-Block aufgerufen hat. Wird ERROR_MESSAGE im äußeren CATCH-Block ausgeführt, gibt es die Meldung des Fehlers zurück, der diesen CATCH-Block aufgerufen hat.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Verwenden von ERROR_MESSAGE in einem CATCH-Block  
 Das folgende Codebeispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 generiert. Die Fehlermeldung wird zurückgegeben.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. Verwenden von ERROR_MESSAGE in einem CATCH-Block mit anderen Fehlerbehandlungstools  
 Das folgende Codebeispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 generiert. Zusammen mit der Fehlermeldung werden Informationen bezüglich des Fehlers zurückgegeben.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errormessage-in-a-catch-block"></a>C. Verwenden von ERROR_MESSAGE in einem CATCH-Block  
 Das folgende Codebeispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 generiert. Die Fehlermeldung wird zurückgegeben.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>D. Verwenden von ERROR_MESSAGE in einem CATCH-Block mit anderen Fehlerbehandlungstools  
 Das folgende Codebeispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 generiert. Zusammen mit der Fehlermeldung werden Informationen bezüglich des Fehlers zurückgegeben.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

