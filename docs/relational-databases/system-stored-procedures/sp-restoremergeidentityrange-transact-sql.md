---
title: Sp_restoremergeidentityrange (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88cf393ac488f6e6f4c078b9bd346a3e6cb53204
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823054"
---
# <a name="sprestoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mit dieser gespeicherten Prozedur werden Identitätsbereichszuweisungen aktualisiert. Dies stellt sicher, dass die automatische Identitätsbereichsverwaltung ordnungsgemäß ausgeführt wird, nachdem ein Verleger von einer Sicherung wiederhergestellt wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication** =] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, Standardwert **alle**. Wenn dieses Argument angegeben ist, werden nur Identitätsbereiche für diese Veröffentlichung wiederhergestellt.  
  
 [ **@article** =] **"***Artikel***"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat den Standardwert des **alle**. Wenn dieses Argument angegeben ist, werden nur Identitätsbereiche für diesen Artikel wiederhergestellt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_restoremergeidentityrange** wird bei der Mergereplikation verwendet.  
  
 **Sp_restoremergeidentityrange** Ruft die maximale Informationen zur identitätsbereichszuordnung vom Verteiler ab und aktualisiert Werte in der **Max_used** Spalte [MSmerge_identity_range_allocations &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) für die Artikel die automatische identitätsbereichsverwaltung verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_restoremergeidentityrange**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
