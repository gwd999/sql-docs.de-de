---
title: dm_cryptographic_provider_properties (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ded9cecb8f5fca6c876e0971e80b0a3964b8aa24
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmcryptographicproviderproperties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen über registrierte Kryptografieanbieter zurück.  
  
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|ID des Kryptografieanbieters.|  
|guid|**uniqueidentifier**|Eindeutige Anbieter-GUID.|  
|provider_version|**nvarchar(256)**|Version des Anbieters im Format '*aa.bb.cccc.dd*'.|  
|sqlcrypt_version|**nvarchar(256)**|Hauptversion des der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cryptographic API im Format "*aa.bb.cccc.dd*".|  
|friendly_name|**nvarchar(2048)**|Vom Anbieter bereitgestellter Name.|  
|authentication_type|**nvarchar(256)**|WINDOWS, BASIC oder OTHER.|  
|symmetric_key_support|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_export|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_import|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_persistance|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|asymmetric_key_support|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|asymmetric_key_export|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_import|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
|symmetric_key_persistance|**tinyint**|0 (nicht unterstützt)<br /><br /> 1 (unterstützt)|  
  
## <a name="remarks"></a>Hinweise  
 Die sys.dm_cryptographic_provider_properties-Sicht ist öffentlich sichtbar.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Erweiterbare Schlüsselverwaltung &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Sicherheitsbezogene dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  