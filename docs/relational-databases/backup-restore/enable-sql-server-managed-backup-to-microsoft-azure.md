---
title: Aktivieren der verwalteten SQL Server-Sicherung in Microsoft Azure | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ab667a25583a8415d44cbc40f1116cac2fb254c3
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54326621"
---
# <a name="enable-sql-server-managed-backup-to-microsoft-azure"></a>Aktivieren der verwalteten SQL Server-Sicherung in Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] sowohl auf Datenbank- als auch auf Instanzebene mit Standardeinstellungen aktiviert wird. Außerdem wird erläutert, wie E-Mail-Benachrichtigungen aktiviert und Sicherungsaktivitäten überwacht werden.  
  
 In diesem Tutorial wird Azure PowerShell verwendet. Bevor Sie das Tutorial starten, müssen Sie [Azure PowerShell herunterladen und installieren](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!IMPORTANT]  
>  Wenn Sie auch erweiterte Optionen aktivieren oder einen benutzerdefinierten Zeitplan verwenden möchten, konfigurieren Sie diese Einstellungen zuerst, bevor Sie [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]aktivieren. Weitere Informationen finden Sie unter [Configure Advanced Options for SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/configure-advanced-options-for-sql-server-managed-backup-to-microsoft-azure.md).  
  
## <a name="enable-and-configure-includesssmartbackupincludesss-smartbackup-mdmd-with-default-settings"></a>Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit Standardeinstellungen  
  
#### <a name="create-the-azure-blob-container"></a>Erstellen des Azure-Blobcontainers  
  
1.  **Registrieren für Azure:** Überspringen Sie diesen Schritt, wenn Sie bereits über ein Azure-Abonnement verfügen. Andernfalls können Sie zum Einstieg eine [kostenlose Testversion](https://azure.microsoft.com/pricing/free-trial/) verwenden oder sich die [Kaufoptionen](https://azure.microsoft.com/pricing/purchase-options/)ansehen.  
  
2.  **Erstellen eines Azure-Speicherkontos:** Überspringen Sie diesen Schritt, wenn Sie bereits über ein Speicherkonto verfügen. Andernfalls können Sie das Speicherkonto über das [Azure-Verwaltungsportal](https://manage.windowsazure.com/) oder über Azure PowerShell erstellen. Der folgende `New-AzureStorageAccount` -Befehl erstellt ein Speicherkonto namens `managedbackupstorage` in der Region USA, Osten.  
  
    ```powershell  
    New-AzureStorageAccount -StorageAccountName "managedbackupstorage" -Location "EAST US"  
    ```  
  
     Weitere Informationen zu Speicherkonten finden Sie unter [Informationen zu Azure-Speicherkonten](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).  
  
3.  **Erstellen eines Blobcontainers für die Sicherungsdateien:** Sie können einen Blobcontainer im Azure-Verwaltungsportal oder mit Azure PowerShell erstellen. Der folgende `New-AzureStorageContainer` -Befehl erstellt einen Blobcontainer namens `backupcontainer` im Speicherkonto `managedbackupstorage` .  
  
    ```powershell  
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey (Get-AzureStorageKey -StorageAccountName managedbackupstorage).Primary  
    New-AzureStorageContainer -Name backupcontainer -Context $context  
    ```  
  
4.  **Generieren einer SAS (Shared Access Signature):** Sie müssen eine SAS erstellen, um auf den Container zuzugreifen. Dies kann mit einigen Tools, anhand von Code und über Azure PowerShell erfolgen. Der folgende `New-AzureStorageContainerSASToken` -Befehl erstellt das SAS-Token für den Blobcontainer `backupcontainer` , das in einem Jahr abläuft.  
  
    ```powershell  
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey (Get-AzureStorageKey -StorageAccountName managedbackupstorage).Primary   
    New-AzureStorageContainerSASToken -Name backupcontainer -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context  
    ```  
    Verwenden Sie für Azure den folgenden Befehl:
       ```powershell
    Connect-AzAccount
    Set-AzContext -SubscriptionId "YOURSUBSCRIPTIONID"
    $StorageAccountKey = (Get-AzStorageAccountKey -ResourceGroupName YOURRESOURCEGROUPFORTHESTORAGE -Name managedbackupstorage)[0].Value
    $context = New-AzureStorageContext -StorageAccountName managedbackupstorage -StorageAccountKey $StorageAccountKey 
    New-AzureStorageContainerSASToken -Name backupcontainer -Permission rwdl -ExpiryTime (Get-Date).AddYears(1) -FullUri -Context $context
   ```  
  
     Die Ausgabe für diesen Befehl enthält sowohl die URL zum Container als auch das SAS-Token. Es folgt ein Beispiel:  
  
    ```  
    https://managedbackupstorage.blob.core.windows.net/backupcontainer?sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl  
    ```  
  
     Trennen Sie im vorherigen Beispiel die Container-URL an der Stelle des Fragezeichens vom SAS-Token (ohne das Fragezeichen einzubeziehen). Beispielsweise würde die vorherige Ausgabe zu den folgenden beiden Werten führen.  
  
    |||  
    |-|-|  
    |**Container-URL:**|https://managedbackupstorage.blob.core.windows.net/backupcontainer|  
    |**SAS-Token:**|sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl|  
  
     Speichern Sie die Container-URL und die SAS, um sie beim Erstellen von SQL-Anmeldeinformationen zu verwenden. Weitere Informationen zur SAS finden Sie unter [Shared Access Signatures, Teil 1: Grundlagen zum SAS-Modell](https://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/).  
  
#### <a name="enable-includesssmartbackupincludesss-smartbackup-mdmd"></a>Aktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
1.  **Erstellen von SQL-Anmeldeinformationen für die SAS-URL:** Verwenden Sie das SAS-Token, um SQL-Anmeldeinformationen für die Blobcontainer-URL zu erstellen. Verwenden Sie in SQL Server Management Studio die folgende Transact-SQL-Abfrage, um die Anmeldeinformationen für die Blobcontainer-URL auf Grundlage des folgenden Beispiels zu erstellen:  
  
    ```sql  
    CREATE CREDENTIAL [https://managedbackupstorage.blob.core.windows.net/backupcontainer]   
    WITH IDENTITY = 'Shared Access Signature',  
    SECRET = 'sv=2014-02-14&sr=c&sig=xM2LXVo1Erqp7LxQ%9BxqK9QC6%5Qabcd%9LKjHGnnmQWEsDf%5Q%se=2015-05-14T14%3B93%4V20X&sp=rwdl'  
    ```  
  
2.  **Sicherstellen, dass der SQL Server-Agent-Dienst ausgeführt wird:** Starten Sie den SQL Server-Agent, wenn er nicht ausgeführt wird.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] benötigt einen laufenden SQL Server-Agent auf der Instanz, um Sicherungsvorgänge durchführen zu können.  Sie können den Starttyp des SQL Server-Agents auf "Automatisch" festlegen, um zu gewährleisten, dass regelmäßige Sicherungsvorgänge durchgeführt werden können.  
  
3.  **Bestimmen des Aufbewahrungszeitraums:** Die Beibehaltungsdauer für die Sicherungsdateien in Tagen. Die Beibehaltungsdauer wird in Tagen angegeben und kann zwischen 1 und 30 Tagen liegen.  
  
4.  **Aktivieren und Konfigurieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:** Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Zielinstanz her. Führen Sie im Abfragefenster folgende Anweisung aus, nachdem Sie die Werte für Datenbankname, Container-URL und Beibehaltungsdauer Ihren Anforderungen entsprechend angepasst haben:  
  
    > [!IMPORTANT]  
    >  Geben Sie zum Aktivieren des Managed Backup auf Instanzebene `NULL` für den `database_name` -Parameter an.  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC msdb.managed_backup.sp_backup_config_basic   
     @enable_backup = 1,   
     @database_name = 'yourdatabasename',  
     @container_url = 'https://managedbackupstorage.blob.core.windows.net/backupcontainer',   
     @retention_days = 30  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ist damit für die angegebene Datenbank aktiviert. Es kann bis zu 15 Minuten dauern, bis die Sicherungsvorgänge für die Datenbank gestartet werden.  
  
5.  **Überprüfen der Standardkonfiguration für erweiterte Ereignisse:** Überprüfen Sie die Einstellungen für erweiterte Ereignisse, indem Sie die folgende transact-SQL-Anweisung ausführen.  
  
    ```  
    SELECT * FROM msdb.managed_backup.fn_get_current_xevent_settings()  
    ```  
  
     Stellen Sie sicher, dass Ereignisse der Kanäle Admin, Operational und Analytical standardmäßig aktiviert sind und nicht deaktiviert werden können. Dies sollte ausreichen, um alle Ereignisse zu überwachen, die ein manuelles Eingreifen erfordern.  Sie können die Debugereignisse ebenfalls aktivieren. Diese Kanäle enthalten jedoch auch Informations- und Debugereignisse, die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] intern zur Erkennung und Behebung von Fehlern verwendet.  
  
6.  **Aktivieren und Konfigurieren der Benachrichtigung für den Integritätsstatus:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] verfügt über eine gespeicherte Prozedur, die einen Agent-Auftrag erstellt, um E-Mail-Benachrichtigungen mit Fehlern oder Warnungen zu senden, die möglicherweise ein Eingreifen erfordern. In den folgenden Schritten wird der Prozess zum Aktivieren und Konfigurieren der E-Mail-Benachrichtigungen beschrieben:  
  
    1.  Richten Sie Datenbank-E-Mail ein, falls diese Funktion auf der Instanz noch nicht aktiviert wurde. Weitere Informationen finden Sie unter [Configure Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
    2.  Konfigurieren Sie SQL Server-Agent-Benachrichtigungen für die Verwendung von Datenbank-E-Mail. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Aktivieren der E-mail-Benachrichtigungen für den Empfang von Sicherungsfehlern und Warnungen:** Führen Sie im Abfragefenster die folgenden Transact-SQL-Anweisungen aus:  
  
        ```  
        EXEC msdb.managed_backup.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
7.  **Anzeigen von Sicherungsdateien im Microsoft Azure Storage-Konto:** Stellen Sie eine Verbindung zum Speicherkonto von SQL Server Management Studio oder Azure-Verwaltungsportal her. Alle Sicherungsdateien im angegebenen Container werden angezeigt. Beachten Sie, dass innerhalb der ersten 5 Minuten nach dem Aktivieren von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank möglicherweise eine Datenbank und eine Protokollsicherung angezeigt werden.  
  
8.  **Überwachen des Integritätsstatus:**  Sie können die zuvor konfigurierten E-Mail-Benachrichtigungen verwenden oder die protokollierten Ereignisse manuell überwachen. Die folgenden Beispiele zeigen einige Transact-SQL-Anweisungen, mit denen die Ereignisse angezeigt werden können:  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC managed_backup.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Die in diesem Abschnitt beschriebenen Schritte sind speziell für die erste Konfiguration von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für die Datenbank vorgesehen. Mithilfe derselben gespeicherten Systemprozeduren können Sie vorhandene Konfigurationen bearbeiten und neue Werte festlegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Managed Backup für Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
