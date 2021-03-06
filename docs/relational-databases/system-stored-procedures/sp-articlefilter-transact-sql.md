---
title: Sp_articlefilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0869cfb6914766e2ab43e138831e2992aa6977b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53209199"
---
# <a name="sparticlefilter-transact-sql"></a>sp_articlefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Filtert Daten, die auf Grundlage eines Tabellenartikels veröffentlicht werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_articlefilter [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @filter_name = ] 'filter_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung, die den Artikel enthält. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article=**] **"**_Artikel_**"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@filter_name=**] **"**_Filter_name_**"**  
 Der Name der gespeicherten Filterprozedur aus erstellt werden die *Filter_name*. *Filter_name* ist **nvarchar(386)**, hat den Standardwert NULL. Sie müssen einen eindeutigen Namen für den Artikelfilter angeben.  
  
 [  **@filter_clause=**] **"**_Filter_clause_**"**  
 Eine Einschränkungsklausel (WHERE), die einen horizontalen Filter definiert. Wenn Sie die Einschränkungsklausel eingeben, lassen Sie das Schlüsselwort, in dem. *Filter_clause* ist **Ntext**, hat den Standardwert NULL.  
  
 [ **@force_invalidate_snapshot =** ] *Force_invalidate_snapshot*  
 Bestätigt, dass durch die von dieser gespeicherten Prozedur ausgeführte Aktion möglicherweise eine vorhandene Momentaufnahme ungültig wird. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, die Momentaufnahme ungültig wird. Wenn die gespeicherte Prozedur erkennt, dass die Änderungen eine neue Momentaufnahme erfordern, tritt ein Fehler auf und es werden keine Änderungen vorgenommen.  
  
 **1** gibt an, dass Änderungen am Artikel kann dazu führen, dass die Momentaufnahme ungültig wird, und wenn es sind Abonnements vorhanden, die eine neue Momentaufnahme erfordern würden Berechtigung erteilt, die vorhandene Momentaufnahme als veraltet zu markieren und eine neue Momentaufnahme zu generieren.  
  
 [  **@force_reinit_subscription =** ] *Force_reinit_subscription*  
 Bestätigt, dass die von dieser gespeicherten Prozedur ausgeführte Aktion die erneute Initialisierung vorhandener Abonnements erfordern kann. *Force_reinit_subscription* ist eine **Bit**, hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, Abonnements erneut initialisiert werden. Wenn die gespeicherte Prozedur erkennt, dass die Änderung die erneute Initialisierung von Abonnements erfordert, wird ein Fehler auftritt und keine Änderungen vorgenommen werden.  
  
 **1** gibt an, dass Änderungen am Artikel bewirkt, dass vorhandene Abonnements erneut initialisiert werden, und erteilt die Berechtigung für die Initialisierung des Abonnements erfolgen.  
  
 [  **@publisher=** ] **"**_Verleger_**"**  
 Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_articlefilter** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Ausführen von **Sp_articlefilter** für ein Artikel mit vorhandenen Abonnements, erfordert diese Abonnements erneut initialisiert werden.  
  
 **Sp_articlefilter** erstellt den Filter und fügt die ID der gespeicherten Filterprozedur in die **Filter** Spalte die [Sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) Tabelle, und klicken Sie dann Fügt den Text der Einschränkungsklausel in die **Filter_clause** Spalte.  
  
 Um einen Artikel mit einem horizontalen Filter zu erstellen, führen [Sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) ohne *Filter* Parameter. Führen Sie **Sp_articlefilter**, und geben Sie alle Parameter einschließlich *Filter_clause*, und führen Sie dann [Sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md), dabei alle Parameter einschließlich eines identischen *Filter_clause*. Wenn der Filter bereits vorhanden ist und die **Typ** in **Sysarticles** ist **1** (Protokollbasierter Artikel), wird der vorherige Filter gelöscht und ein neuer Filter erstellt.  
  
 Wenn *Filter_name* und *Filter_clause* nicht bereitgestellt werden, wird der vorherige Filter gelöscht, und die Filter-ID nastaven NA hodnotu **0**.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_articlefilter**.  
  
## <a name="see-also"></a>Siehe auch  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definieren und Ändern eines statischen Zeilenfilters](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [Sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
