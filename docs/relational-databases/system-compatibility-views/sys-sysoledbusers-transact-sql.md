---
title: Sys.sysoledbusers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 71d04ef07053eb893a98d654424eb49b61f0c7e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809138"
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Diese [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-Systemtabelle wird nur aus Gründen der Abwärtskompatibilität als Sicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt. Wir empfehlen die Verwendung [Katalogsichten](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) stattdessen.  
  
 Enthält eine Zeile für jede Benutzer- und Kennwortzuordnung für den angegebenen Verbindungsserver. **Sysoledbusers** befindet sich in der **master** Datenbank.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|Sicherheits-ID (SID) des Servers.|  
|**rmtloginame**|**Nvarchar (** 128 **)**|Name des remoteanmeldenamens, **Loginsid** für die verbundene **Rmtservid**.|  
|**rmtpassword**|**Nvarchar (** 128 **)**|Gibt NULL zurück.|  
|**loginsid**|**Varbinary (** 85 **)**|SID des lokalen Anmeldenamens, der zugeordnet werden soll.|  
|**status**|**smallint**|Wenn 1, sollten die Anmeldeinformationen des Benutzers für die Zuordnung verwendet werden.|  
|**changedate**|**datetime**|Datum, an dem die Zuordnungsinformationen zuletzt geändert wurden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
