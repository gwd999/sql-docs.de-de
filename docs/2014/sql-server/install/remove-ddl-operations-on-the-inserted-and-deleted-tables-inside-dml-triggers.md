---
title: Entfernen Sie DDL-Vorgänge für die eingefügten und gelöschten Tabellen innerhalb von DML-Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe6aa8c12e6132fa44380158585bd13a7c313548
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188230"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a>Entfernen Sie DDL-Vorgänge aus den eingefügten und gelöschten Tabellen innerhalb von DML-Triggern
  Die Anweisungen der Data Definition Language (DDL), wie CREATE INDEX, können nicht für die eingefügten und gelöschten Tabellen innerhalb von DML-Triggern ausgeführt werden. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind einige DDL-Anweisungen für die inserted-Tabelle und die deleted-Tabelle zulässig. Weitere Informationen finden Sie unter "Verwenden der Tabellen inserted und deleted" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie DDL-Vorgänge, die für die inserted-Tabelle und die deleted-Tabelle in DML-Triggern ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
