---
title: MSSQL_ENG020557 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f7e67a65939589a340071f291d1547b1d53d7af
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54135790"
---
# <a name="mssqleng020557"></a>MSSQL_ENG020557
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20557|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Agent wird heruntergefahren. Weitere Informationen finden Sie im Auftragsverlauf des SQL Server-Agents für den Auftrag '%s'.|  
  
## <a name="explanation"></a>Erklärung  
 Ein Replikations-Agent wurde beendet, ohne dass ein Grund in die entsprechende Verlaufstabelle geschrieben wurde, oder der Agent wurde während eines Prozesses beendet.  
  
## <a name="user-action"></a>Benutzeraktion  
  
-   Starten Sie den Agent neu, um zu ermitteln, ob er nun fehlerfrei ausgeführt wird. Weitere Informationen finden Sie unter [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) oder [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
-   Überprüfen Sie Agent- und Auftragsverlauf auf andere Fehler, die eventuell um dieselbe Zeit aufgetreten sind. Informationen zum Anzeigen des Agent-Status und der Fehlerinformationen im Replikationsmonitor finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
 
-   Stellen Sie sicher, dass die Konnektivität zwischen den Computern, auf die der Agent zugreift, funktioniert, und stellen Sie dann mithilfe eines Hilfsprogramms eine Verbindung mit den einzelnen Computern her, z. B. mithilfe des Hilfsprogramms **sqlcmd** . Benutzen Sie zum Herstellen der Verbindungen dasselbe Konto wie der Agent. Weitere Informationen zu den erforderlichen Berechtigungen für die einzelnen Agentkonten finden Sie unter [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Wenn der Fehler auftritt, während Sie eine Momentaufnahme erstellen oder anwenden, überprüfen Sie die Dateien im Momentaufnahmeverzeichnis auf Fehler.  
  
-   Wenn der Fehler weiterhin auftritt, erhöhen Sie die Protokollierungsstufe des Agents, und geben Sie eine Ausgabedatei für das Protokoll an. Je nach Zusammenhang, in dem der Fehler auftritt, finden Sie hier möglicherweise die Schritte, die zum Fehler führen, und weitere Fehlermeldungen. Weitere Informationen zur Konfiguration der Protokollierung für die Replikation finden Sie im Microsoft Knowledge Base-Artikel [312292](https://support.microsoft.com/kb/312292).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
