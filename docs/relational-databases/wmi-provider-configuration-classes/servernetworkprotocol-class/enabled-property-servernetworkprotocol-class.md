---
title: Aktiviert-Eigenschaft (ServerNetworkProtocol-Klasse) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Enabled Property (ServerNetworkProtocol Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: Enabled property
ms.assetid: a514822a-91f1-4aca-9175-2b96cff29700
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f789a9d36597f03b533bf9aad962d328967f2ae1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="enabled-property-servernetworkprotocol-class"></a>Enabled-Eigenschaft (ServerNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Ruft die boolesche Eigenschaft, die angibt, ob das servernetzwerkprotokoll aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 A [ServerNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , das das Netzwerkprotokoll darstellt, das von der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob das Server-Netzwerkprotokoll aktiviert ist: **true** , wenn das Server-Netzwerkprotokoll aktiviert ist, bzw. **false** , wenn das Server-Netzwerkprotokoll deaktiviert ist.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  