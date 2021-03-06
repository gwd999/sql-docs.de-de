---
title: Sp_update_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_schedule
- sp_update_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_schedule
ms.assetid: 97b3119b-e43e-447a-bbfb-0b5499e2fefe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eeff4b38e3736241e0dd56729e42c5e7207f310f
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591804"
---
# <a name="spupdateschedule-transact-sql"></a>sp_update_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Einstellungen für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Zeitplan.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_schedule   
    {   [ @schedule_id = ] schedule_id   
      | [ @name = ] 'schedule_name' }  
    [ , [ @new_name = ] new_name ]  
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @automatic_post =] automatic_post ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@schedule_id =** ] *schedule_id*  
 Der Bezeichner des Zeitplans, der geändert werden soll. *Schedule_id* ist **Int**, hat keinen Standardwert. Entweder *Schedule_id* oder *Schedule_name* muss angegeben werden.  
  
 [  **@name =** ] **"**_Schedule_name_**"**  
 Der Name des zu ändernden Zeitplan. *Schedule_name*ist **Sysname**, hat keinen Standardwert. Entweder *Schedule_id* oder *Schedule_name* muss angegeben werden.  
  
 [ **@new_name**=] *New_name*  
 Der neue Name des Zeitplans. *New_name* ist **Sysname**, hat den Standardwert NULL. Wenn *New_name* NULL ist, der Namen des Zeitplans bleibt unverändert.  
  
 [ **@enabled =** ] *enabled*  
 Gibt den aktuellen Status des Zeitplans an. *aktiviert*ist **Tinyint**, hat den Standardwert **1** (aktiviert). Wenn **0**, der Zeitplan ist nicht aktiviert. Wenn der Zeitplan nicht aktiviert ist, werden über diesen Zeitplan keine Aufträge ausgeführt.  
  
 [ **@freq_type =** ] *freq_type*  
 Ein Wert, der angibt, wann ein Auftrag ausgeführt werden soll. *Freq_type*ist **Int**, hat den Standardwert **0**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ zum *freq_interval*|  
|**64**|Ausführen beim Start des SQLServerAgent-Diensts|  
|**128**|Ausführen, wenn sich der Computer im Leerlauf befindet|  
  
 [ **@freq_interval =** ] *freq_interval*  
 Die Tage, an denen ein Auftrag ausgeführt wird. *Freq_interval* ist **Int**, hat den Standardwert **0**, und hängt vom Wert der *Freq_type*.  
  
|Wert von *Freq_type*|Auswirkung auf *Freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (einmal)|*Freq_interval* wird nicht verwendet.|  
|**4** (täglich)|Jede *Freq_interval* Tage.|  
|**8** (wöchentlich)|*Freq_interval* kann einen oder mehrere der folgenden (in Kombination mit einem **OR** logischen Operator):<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **4** = Dienstag<br /><br /> **8** = Mittwoch<br /><br /> **16** = Donnerstag<br /><br /> **32** = Freitag<br /><br /> **64** = Samstag|  
|**16** (monatlich)|Auf der *Freq_interval* Tag des Monats.|  
|**32** (mit relativem Monatsintervall)|*Freq_interval* ist eine der folgenden:<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **3** = Dienstag<br /><br /> **4** = Mittwoch<br /><br /> **5** = Donnerstag<br /><br /> **6** = Freitag<br /><br /> **7** = Samstag<br /><br /> **8** = Tag<br /><br /> **9** = Arbeitstag<br /><br /> **10** = Wochenendtag|  
|**64** (wenn der SQLServerAgent-Dienst startet)|*Freq_interval* wird nicht verwendet.|  
|**128**|*Freq_interval* wird nicht verwendet.|  
  
 [ **@freq_subday_type =** ] *freq_subday_type*  
 Gibt die Einheiten für *Freq_subday_interval **.* *Freq_subday_type*ist **Int**, hat den Standardwert **0**, und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**0x1**|Zum angegebenen Zeitpunkt|  
|**0x2**|Sekunden|  
|**0x4**|Minuten|  
|**0x8**|Stunden|  
  
 [ **@freq_subday_interval =** ] *freq_subday_interval*  
 Die Anzahl der *Freq_subday_type* -Perioden zwischen den einzelnen Ausführungen eines Auftrags. *Freq_subday_interval*ist **Int**, hat den Standardwert **0**.  
  
 [ **@freq_relative_interval =** ] *freq_relative_interval*  
 Vorhandensein eines Auftrags *Freq_interval* in jedem Monat, wenn *Freq_interval* ist **32** (mit relativem Monatsintervall). *Freq_relative_interval*ist **Int**, hat den Standardwert **0**, und kann einen der folgenden Werte sein.  
  
|Wert|Beschreibung (Einheit)|  
|-----------|--------------------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
 [ **@freq_recurrence_factor =** ] *freq_recurrence_factor*  
 Die Anzahl der Wochen oder Monate zwischen den geplanten Ausführungen eines Auftrags. *Freq_recurrence_factor* wird nur verwendet, wenn *Freq_type* ist **8**, **16**, oder **32**. *Freq_recurrence_factor*ist **Int**, hat den Standardwert **0**.  
  
 [ **@active_start_date =** ]  *active_start_date*  
 Das Datum, an dem die Ausführung eines Auftrags beginnen kann. *Active_start_date*ist **Int**, hat den Standardwert NULL, womit des heutigen Datums. Das Datum wird als JJJJMMTT formatiert. Wenn *Active_start_date* ist nicht NULL ist, muss das Datum größer oder gleich 19900101 sein.  
  
 Überprüfen Sie nach dem Erstellen des Zeitplans, ob das Startdatum korrekt ist. Weitere Informationen finden Sie im Abschnitt "Planen von Startdaten" in [erstellen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 [ **@active_end_date =** ] *active_end_date*  
 Das Datum, an dem die Ausführung eines Auftrags beendet werden kann. *Active_end_date*ist **Int**, hat den Standardwert **99991231**, womit der 31. Dezember 9999 angegeben. Im Format JJJJMMTT.  
  
 [ **@active_start_time =** ] *active_start_time*  
 Die Zeit auf einem beliebigen Tag zwischen *Active_start_date* und *Active_end_date* zum Starten der Ausführung eines Auftrags. *Active_start_time*ist **Int**, hat den Standardwert 000000, womit 00:00:00 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
 [ **@active_end_time =** ] *active_end_time*  
 Die Zeit auf einem beliebigen Tag zwischen *Active_start_date* und *Active_end_date* zu der die Ausführung eines Auftrags. *Active_end_time*ist **Int**, hat den Standardwert **235959**, womit 23:59:59 Uhr im 24-Stunden-Format an und muss im Format HHMMSS eingegeben werden.  
  
 [ **@owner_login_name**=] **"**_Owner_login_name_**"**]  
 Der Name des Serverprinzipals, der Besitzer des Zeitplans ist. *Owner_login_name* ist **Sysname**, hat den Standardwert NULL, gibt an, dass der Ersteller des Zeitplans Besitz ist.  
  
 [ **@automatic_post =**] *automatic_post*  
 Reserviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Alle Aufträge, die den Zeitplan verwenden, verwenden sofort die neuen Einstellungen. Zurzeit ausgeführte Aufträge werden durch das Ändern eines Zeitplans jedoch nicht beendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **Sysadmin** können einen Zeitplan, der Besitz eines anderen Benutzers ändern.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktivierte Status des `NightlyJobs`-Zeitplans zu `0` und der Besitzer zu `terrid` geändert.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_schedule  
    @name = 'NightlyJobs',  
    @enabled = 0,  
    @owner_login_name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [Planen eines Auftrags](../../ssms/agent/schedule-a-job.md)   
 [Erstellen Sie einen Zeitplan](../../ssms/agent/create-a-schedule.md)   
 [SQL Server-Agent-gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
