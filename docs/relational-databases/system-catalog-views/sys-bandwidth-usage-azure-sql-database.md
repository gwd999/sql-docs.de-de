---
title: Sys. bandwidth_usage (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- bandwidth_usage
- sys.bandwidth_usage
- bandwidth_usage_TSQL
- sys.bandwidth_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.bandwidth_usage
- bandwidth_usage
ms.assetid: 43ed8435-f059-4907-b5c0-193a258b394a
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 90ad88cfaae5c82b79d9da1fa7de5baa60fe46f3
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52403716"
---
# <a name="sysbandwidthusage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Hinweis: Dies gilt nur für [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.**  
  
 Gibt Informationen über die Netzwerkbandbreite verwendet, die für jede Datenbank in eine  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] logische V11-Servers**,. Jede Zeile, die für eine bestimmte Datenbank zurückgegeben wird, gibt eine einzelne Richtung und eine Verwendungsklasse über eine Stunde hinweg an.  
  
 **Dies ist veraltet einem [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] logischen V12-Server.**  
  
 Die **Sys. bandwidth_usage** -Ansicht enthält die folgenden Spalten.  
  
|Column Name|Description|  
|-----------------|-----------------|  
|**Uhrzeit**|Die Stunde, als die Bandbreite verwendet wurde. Die Zeilen in dieser Sicht enthalten stündliche Angaben. Beispielsweise bedeutet 2009-09-19 02:00:00.000, dass die Bandbreite am 19. September 2009 zwischen 2:00 Uhr und 3:00 Uhr verwendet wurde.|  
|**database_name**|Der Name der Datenbank, die Bandbreite verwendet hat.|  
|**direction**|Der Typ der Bandbreite, der verwendet wurde. Dies kann eine der folgenden Optionen sein:<br /><br /> Eingang: In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] eingehende Daten.<br /><br /> Ausgang: Aus [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] ausgehende Daten.|  
|**class**|Die Klasse der Bandbreite, die verwendet wurde. Dies kann eine der folgenden Optionen sein:<br />Interne: Daten, die auf der Azure-Plattform verschoben werden.<br />Extern: Daten, die aus der Azure-Plattform heraus verschoben werden.<br /><br /> Diese Klasse wird nur zurückgegeben, wenn die Datenbank in einer kontinuierlichen Kopienbeziehung zwischen Regionen ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]) ist. Wenn eine bestimmte Datenbank nicht in jeder fortlaufenden kopierbeziehung beteiligt ist, werden keine "Interlink"-Zeilen zurückgegeben. Weitere Informationen finden Sie im Abschnitt "Hinweise" weiter unten in diesem Thema.|  
|**Zeitraum**|Der Zeitraum, der die Verwendung des Auftretens ist Spitze oder OffPeak. Die Spitzenzeit basiert auf der Region, in der der Server erstellt wurde. Wenn ein -Server beispielsweise in der Region "US_Northwest" erstellt wurde, liegt die Spitzenzeit laut Definition zwischen 10:00 Uhr und 18:00 Uhr PST.|  
|**Menge**|Die Menge der verwendeten Bandbreite in KB.|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Ansicht ist nur verfügbar, in der **master** Datenbank, um die prinzipalanmeldung auf Serverebene.  
  
## <a name="remarks"></a>Hinweise  
  
### <a name="external-and-internal-classes"></a>Externe und interne Klassen  
 Für jede Datenbank zu einem bestimmten Zeitpunkt, verwendet der **Sys. bandwidth_usage** -Sicht die Zeilen, die die Klasse und die Richtung der bandbreitenverwendung anzeigen zurück. Das folgende Beispiel zeigt Daten, die für eine bestimmte Datenbank verfügbar gemacht werden können. In diesem Beispiel ist der Zeitpunkt 2012-04-21 17:00:00, der im Zeitraum mit Spitzenwerten liegt. Der Datenbankname ist Db1. In diesem Beispiel **Sys. bandwidth_usage** wie folgt eine Zeile für alle vier Kombinationen der Ingress- und Egress-Richtungen und externe und interne Klassen zurück:  
  
|Uhrzeit|database_name|direction|class|time_period|quantity|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Ingress|External|Peak|66|  
|2012-04-21 17:00:00|Db1|Egress|External|Peak|741|  
|2012-04-21 17:00:00|Db1|Ingress|Internal|Peak|1052|  
|2012-04-21 17:00:00|Db1|Egress|Intern|Peak|3525|  
  
### <a name="interpreting-data-direction-for-includessgeodrincludesssgeodr-mdmd"></a>Interpretieren der Datenrichtung für [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]  
 Bei [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] sind die Bandbreitenverwendungsdaten in der logischen Masterdatenbank auf beiden Seiten einer kontinuierlichen Kopienbeziehung sichtbar. Daher müssen Sie die Ingress- und Egress-Richtungsindikatoren aus der Perspektive des logischen Servers interpretieren, den Sie abfragen. Betrachten Sie beispielsweise einen Replikationsdatenstrom, der 1 MB Daten vom Quell- auf den Zielserver überträgt. In diesem Fall auf dem Quellserver die 1MB gezählt gesendeten Daten, und klicken Sie auf dem Zielserver ist die 1MB als empfangene Daten aufgezeichnet.  
  
> [!NOTE]  
>  Die vom Quell- auf den Zielserver übertragenen Massendaten werden in Richtung des Benutzerdatendatenflusses übertragen. Manche Daten müssen jedoch in die andere Richtung übertragen werden.  
  
  
