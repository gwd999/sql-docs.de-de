---
title: Sp_changearticlecolumndatatype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07213247345280e992c2fbd5552d5cdfb96747ab
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133560"
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Datentypzuordnung der Artikelspalte für eine Oracle-Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
> [!NOTE]  
>  Die Datentypzuordnungen zwischen unterstützten Verlegertypen werden standardmäßig bereitgestellt. Verwendung **Sp_changearticlecolumndatatype** nur, wenn Sie diese Standardeinstellungen überschreiben.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=** ] **"**_Veröffentlichung_**"**  
 Der Name der Oracle-Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article =** ] **"**_Artikel_**"**  
 Der Name des Artikels. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@column**=] **"**_Spalte_**"**  
 Der Name der Spalte, für die die Datentypzuordnung geändert werden soll. *Spalte* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@type** =] **"**_Typ_**"**  
 Der Name des der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp in der Zielspalte. *Typ* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@length** =] *Länge*  
 Die Länge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyps in der Zielspalte. *Länge* ist **Bigint**, hat den Standardwert NULL.  
  
 [ **@precision**=] *mit einfacher Genauigkeit*  
 Die Genauigkeit des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyps in der Zielspalte. *Genauigkeit* ist **Bigint**, hat den Standardwert NULL.  
  
 [ **@publisher**=] **"**_Verleger_**"**  
 Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changearticlecolumndatatype** dient zum Überschreiben der standardmäßigen datentypzuordnungen zwischen unterstützten verlegertypen (Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Führen Sie zum Anzeigen dieser standardmäßigen datentypzuordnungen [Sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **Sp_changearticlecolumndatatype** wird nur für Oracle-Verleger unterstützt. Das Ausführen dieser gespeicherten Prozedur für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Veröffentlichung führt zu einem Fehler.  
  
 **Sp_changearticlecolumndatatype** muss ausgeführt werden, für jede spaltenzuordnung für Artikel, die geändert werden muss.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
