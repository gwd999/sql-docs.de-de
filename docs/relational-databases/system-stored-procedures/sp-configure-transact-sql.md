---
title: Sp_configure (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_configure
- sp_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_configure
ms.assetid: d18b251d-b37a-4f5f-b50c-502d689594c8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f3b983411fade381b926e05a3bdbb81355bf4c02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852338"
---
# <a name="spconfigure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-pdw-md.md)]

  Mit dieser Prozedur können globale Konfigurationseinstellungen für den aktuellen Server angezeigt oder geändert werden.

> [!NOTE]  
>  Auf Datenbankebene Konfigurationsoptionen finden Sie unter [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Zum Konfigurieren von Soft-NUMA finden Sie unter [Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server  
  
sp_configure [ [ @configname = ] 'option_name'   
    [ , [ @configvalue = ] 'value' ] ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- List all of the configuration options  
sp_configure  
[;]  
  
-- Configure Hadoop connectivity  
sp_configure [ @configname= ] 'hadoop connectivity',  
             [ @configvalue = ] { 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 }  
[;]  
RECONFIGURE  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@configname=** ] **'***Optionsname***'**  
 Der Name einer Konfigurationsoption. *option_name* ist vom Datentyp **varchar(35)**. Der Standardwert ist NULL. Von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] wird jede eindeutige Zeichenfolge erkannt, die Teil des Konfigurationsnamens ist. Erfolgt keine Angabe, wird die gesamte Liste der Optionen zurückgegeben.  
  
 Weitere Informationen zu den verfügbaren Konfigurationsoptionen und ihren Einstellungen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 [ **@configvalue=** ] **'***Wert***'**  
 Die neue Konfigurationseinstellung. *value* ist vom Datentyp **int**. Der Standardwert ist NULL. Der Maximalwert kann je nach Option unterschiedlich sein.  
  
 Der maximale Wert für die einzelnen Optionen finden Sie unter den **maximale** Spalte die **sys.configurations** -Katalogsicht angezeigt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Bei der Ausführung ohne Parameter **Sp_configure** gibt ein Resultset mit fünf Spalten zurück, und die Optionen sind alphabetisch aufsteigend sortiert, wie in der folgenden Tabelle gezeigt.  
  
 Die Werte für **Config_value** und **Run_value** sind nicht automatisch gleich. Nach dem Update einer Konfigurationseinstellung mithilfe von **Sp_configure**, die vom Systemadministrator muss des ausgeführten Konfigurationswerts mit entweder RECONFIGURE oder RECONFIGURE WITH OVERRIDE aktualisieren. Weitere Informationen finden Sie im Abschnitt mit Hinweisen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|Der Name der Konfigurationsoption.|  
|**minimum**|**int**|Der Mindestwert der Konfigurationsoption.|  
|**maximum**|**int**|Der Höchstwert der Konfigurationsoption.|  
|**config_value**|**int**|Wert, der Festlegen der Konfigurationsoption wurde mit **Sp_configure** (Wert in **sysconfigures.Value**). Weitere Informationen zu diesen Optionen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md) und [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
|**run_value**|**int**|Aktuell ausgeführter Wert der Konfigurationsoption (Wert in **Sys.Configurations**).<br /><br /> Weitere Informationen finden Sie unter [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
  
## <a name="remarks"></a>Hinweise  
 Verwendung **Sp_configure** anzeigen oder Ändern von Einstellungen für die Serverebene. Zum Ändern von Einstellungen auf Datenbankebene können Sie ALTER DATABASE verwenden. Wenn Einstellungen geändert werden sollen, die nur die aktuelle Benutzersitzung betreffen, verwenden Sie die SET-Anweisung.  
  
## <a name="updating-the-running-configuration-value"></a>Aktualisieren des ausgeführten Konfigurationswerts  
 Wenn Sie ein neues angeben *Wert* für eine *Option*, das Resultset zeigt diesen Wert in der **Config_value** Spalte. Dieser Wert zunächst unterscheidet sich vom Wert in der **Run_value** Spalte, die die aktuell ausgeführte Konfigurationswert angezeigt wird. Beim Aktualisieren des ausgeführten Konfigurationswerts in der **Run_value** Spalte, die vom Systemadministrator muss entweder RECONFIGURE oder RECONFIGURE WITH OVERRIDE ausführen.  
  
 RECONFIGURE und RECONFIGURE WITH OVERRIDE können für jede Konfigurationsoption verwendet werden. Die einfache RECONFIGURE-Anweisung weist jedoch Optionswerte zurück, die außerhalb eines angemessenen Bereichs liegen oder die zu Konflikten bei den Optionen führen. Z. B. ein Fehler generiert, wenn die **Wiederherstellungsintervall** Wert ist größer als 60 Minuten oder, wenn die **Affinitätsmaske** Wert überschneidet sich mit den **Affinity i/o Mask**Wert. Von RECONFIGURE WITH OVERRIDE hingegen werden alle Optionswerte vom richtigen Datentyp akzeptiert. Eine Neukonfiguration mit dem angegebenen Wert wird dann erzwungen.  
  
> [!CAUTION]  
>  Ein nicht geeigneter Optionswert kann negative Auswirkungen auf die Konfiguration der Serverinstanz haben. Verwenden Sie RECONFIGURE WITH OVERRIDE mit Sorgfalt.  
  
 Mit der RECONFIGURE-Anweisung werden einige Optionen dynamisch aktualisiert. Für andere Optionen ist jedoch das Beenden und Neustarten des Servers erforderlich. Z. B. die **Min. Serverarbeitsspeicher** und **Max. Serverarbeitsspeicher** Serverarbeitsspeicher-Optionen werden dynamisch aktualisiert die [!INCLUDE[ssDE](../../includes/ssde-md.md)]; aus diesem Grund können Sie sie ändern, ohne einen Neustart des Servers. Neukonfiguration des laufenden Werts für die **Füllfaktor** Option erfordert einen Neustart der [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Nach dem Ausführen von RECONFIGURE für eine Konfigurationsoption, sehen Sie, ob die Option durch Ausführen dynamisch aktualisiert wurde **Sp_configure'***Optionsname***"**. Die Werte in der **Run_value** und **Config_value** Spalten zu einer dynamisch aktualisierten Option übereinstimmen sollte. Sie können auch überprüfen, um festzustellen, welche Optionen dynamisch sind, anhand der **Is_dynamic** Spalte die **sys.configurations** -Katalogsicht angezeigt.  
  
> [!NOTE]  
>  Wenn ein angegebener *Wert* ist zu hoch ist, eine Option der **Run_value** -Spalte dargestellt, die die [!INCLUDE[ssDE](../../includes/ssde-md.md)] hat standardmäßig dynamischer Arbeitsspeicher nicht mehr benötigen Sie eine Einstellung, die nicht gültig ist.  
  
 Weitere Informationen finden Sie unter [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md).  
  
## <a name="advanced-options"></a>Erweiterte Optionen  
 Einige Konfigurationsoptionen, z. B. **Affinitätsmaske** und **Wiederherstellungsintervall**, werden als erweiterte Optionen bezeichnet. Diese Optionen stehen zum Anzeigen und Ändern nicht zur Verfügung. Damit sie verfügbar ist, legen Sie die **ShowAdvancedOptions** Konfigurationsoption auf 1.  
  
 Weitere Informationen zu den Konfigurationsoptionen und ihren Einstellungen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Auszuführende **Sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung, Sie müssen die Berechtigung ALTER SETTINGS-Serverebene. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. Auflisten der erweiterten Konfigurationsoptionen  
 Im folgenden Beispiel wird das Festlegen und Auflisten aller Konfigurationsoptionen dargestellt. Erweiterte Konfigurationsoptionen werden angezeigt, indem zunächst `show advanced option` auf `1` festgelegt wird. Nachdem diese Option geändert wurde, werden beim Ausführen von `sp_configure` ohne Parameter alle Konfigurationsoptionen angezeigt.  
  
```  
USE master;  
GO  
EXEC sp_configure 'show advanced option', '1';  
```  
  
 Im Folgenden wird die Meldung aufgeführt: "Die Konfigurationsoption 'show advanced options' wurde von 0 in 1 geändert. Führen Sie zum Installieren die RECONFIGURE-Anweisung aus."  
  
 Führen Sie `RECONFIGURE` aus, und zeigen Sie alle Konfigurationsoptionen an:  
  
```  
RECONFIGURE;  
EXEC sp_configure;  
```  
  
### <a name="b-changing-a-configuration-option"></a>B. Ändern einer Konfigurationsoption  
 Im folgenden Beispiel wird `recovery interval` für das System auf `3` Minuten festgelegt.  
  
```  
USE master;  
GO  
EXEC sp_configure 'recovery interval', '3';  
RECONFIGURE WITH OVERRIDE;  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-list-all-available-configuration-settings"></a>C. Auflisten aller verfügbaren Konfigurationseinstellungen  
 Im folgenden Beispiel wird dargestellt, wie alle Konfigurationsoptionen aufgelistet werden.  
  
```  
EXEC sp_configure;  
```  
  
 Das Ergebnis gibt den Optionsnamen zurück, gefolgt von den minimalen und maximalen Werten für die Option. Die **Config_value** ist der Wert, der [!INCLUDE[ssDW](../../includes/ssdw-md.md)] verwenden, wenn die Neukonfiguration abgeschlossen ist. **run_value** ist der Wert, der gerade verwendet wird. **config_value** und **run_value** sind in der Regel gleich, sofern der Wert nicht gerade geändert wird.  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>D. Auflisten der Konfigurationseinstellungen für einen Konfigurationsnamen  
  
```  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>E. Festlegen der Hadoop-Konnektivität  
 Festlegen von Hadoop-Konnektivität erfordert einige zusätzliche Schritte neben dem Ausführen von Sp_configure. Finden Sie in der vollständigen Prozedur [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
## <a name="see-also"></a>Siehe auch  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SET-Anweisungen (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
