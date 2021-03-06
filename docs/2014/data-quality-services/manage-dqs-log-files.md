---
title: Verwalten von DQS-Protokolldateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: be71c04c007c4801cd0e0166bcd7751937713af6
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033407"
---
# <a name="manage-dqs-log-files"></a>Verwalten von DQS-Protokolldateien
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS)-Protokolldateien unterstützen Sie bei der Diagnose und bei der Problembehandlung mit den Komponenten [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]und [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]. Für [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]und die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]werden separate Protokolldateien generiert.  
  
 Sie können die Einstellung des Protokollschweregrads für [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Funktionen und -Module mithilfe von [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] konfigurieren. Darüber hinaus können Sie auch andere (erweiterte) Einstellungen für die DQS-Protokolldateien konfigurieren, indem Sie die Einstellungen für die DQS-Protokollkonfiguration in der DQS_MAIN-Datenbank und in einer XML-Datei auf dem [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Computer manuell ändern.  
  
##  <a name="DQSServer"></a> Data Quality Server-Protokolldatei  
 Die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei, DQServerLog.DQS_MAIN.log, enthält Protokolle der Aktivitäten, die in [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]ausgeführt werden. Wenn Sie die Standardinstanz von SQL Server installiert haben, ist die Protokolldatei DQServerLog.DQS_MAIN.log unter C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log verfügbar. Die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei enthält die folgenden Informationen, die jeweils durch ein Pipezeichen (|) begrenzt sind:  
  
-   Datum und Uhrzeit  
  
-   Threadname  
  
-   Thread-ID  
  
-   Protokollschweregrad (FATAL, ERROR, WARN, INFO und DEBUG)  
  
    > [!NOTE]  
    >  Der DEBUG-Protokollierungsschweregrad entspricht der Option Ausführlich.  
  
-   UID (interne DQS-Infrastruktur-ID)  
  
-   Namespace  
  
-   Klasse und Methode  
  
-   MessageBox  
  
 Neben diesen Informationen werden in der Protokolldatei auch Informationen zur Anwendungsversion, zum Computernamen, Benutzernamen und Betriebssystem angezeigt.  
  
 Ein Beispieleintrag in der [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei sieht wie folgt aus:  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 Die Datei DQServerLog.DQS_MAIN.log [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ist eine Rolldatei. Eine neue Protokolldatei wird erstellt, sobald die vorhandene Protokolldatei die maximale Rolldateigröße überschreitet, die in den Konfigurationseinstellungen des -Protokolls angegeben ist. Weitere Informationen finden Sie unter [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="DQSClient"></a> Data Quality Client-Protokolldatei  
 Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei, DQClientLog.log, enthält die clientseitigen Protokolle. Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei ist unter %APPDATA%\SSDQS\Log verfügbar. Die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei enthält ähnliche Informationen wie die Serverprotokolldatei, jedoch auf Clientseite.  
  
 Wie die [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] -Protokolldatei ist auch die [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolldatei eine Rolldatei, und eine neue Protokolldatei wird erstellt, sobald die vorhandene Protokolldatei die maximale Rolldateigröße überschreitet, die in den Konfigurationseinstellungen des [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Protokolls angegeben ist. Weitere Informationen finden Sie unter [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).  
  
##  <a name="DQSCleansing"></a> Protokolldatei der DQS-Bereinigungskomponente  
 Die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] -Protokolldatei, DQSSSISLog.log, enthält Protokolle der Aktivitäten, die mithilfe der [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]ausgeführt werden. Die Protokolldatei der Komponente [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] ist unter %APPDATA%\SSDQS\Log verfügbar. Die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] -Protokolldatei enthält ähnliche Informationen wie die Serverprotokolldatei, jedoch für die [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].  
  
##  <a name="RT"></a> Verwandte Aufgaben  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie die Einstellungen des Protokollschweregrads für DQS-Protokolldateien mit [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]konfiguriert werden.|[Konfigurieren von Schweregraden für DQS-Protokolldateien](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Beschreibt, wie die erweiterten Einstellungen für DQS-Protokolldateien manuell konfiguriert werden.|[Konfigurieren der erweiterten Einstellungen für DQS-Protokolldateien](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [DQS-Verwaltung](../../2014/data-quality-services/dqs-administration.md)  
  
  
