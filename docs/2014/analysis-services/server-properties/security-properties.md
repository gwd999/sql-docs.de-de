---
title: Sicherheitseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a382b37b9b7e25c8cb42e42bf873a0ce7f2a4920
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054960"
---
# <a name="security-properties"></a>Sicherheitseigenschaften
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] werden die in der folgenden Tabelle aufgeführten Sicherheitseigenschaften des Servers aufgeführt. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Gilt für:** mehrdimensionalen und Tabellenservermodus  
  
## <a name="properties"></a>Eigenschaften  
 `RequireClientAuthentication`  
 Eine boolesche Eigenschaft, die anzeigt, ob eine Client-Authentifizierung erforderlich ist.  
  
 Der Standardwert für diese Eigenschaft ist auf True festgelegt, was anzeigt, dass eine Client-Authentifizierung erforderlich ist.  
  
 `SecurityPackageList`  
 Eine Zeichenfolgeneigenschaft, die eine Liste mit durch Trennzeichen getrennten SSPI-Paketen enthält, die vom Server zur Client-Authentifizierung verwendet werden.  
  
 `DisableClientImpersonation`  
 Eine boolesche Eigenschaft, die anzeigt, ob Clientidentitätswechsel (z. B. für gespeicherte Prozeduren) deaktiviert sind.  
  
 Der Standardwert für diese Eigenschaft ist auf False festgelegt, was anzeigt, dass Clientidentitätswechsel aktiviert sind.  
  
 `BuiltinAdminsAreServerAdmins`  
 Eine boolesche Eigenschaft, die anzeigt, ob Mitglieder der Gruppe Administratoren auf dem lokalen Computer Administratoren von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sind.  
  
 `ServiceAccountIsServerAdmin`  
 Eine boolesche Eigenschaft, die anzeigt, ob das Dienstkonto ein Serveradministrator ist.  
  
 Der Standardwert für diese Eigenschaft ist auf True festgelegt, was anzeigt, dass das Dienstkonto ein Serveradministrator ist.  
  
 `ErrorMessageMode`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `DataProtection\ RequiredProtectionLevel`  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die erforderliche Schutzebene für alle Clientanforderungen definiert. Diese Eigenschaft hat einen der in der folgenden Tabelle aufgeführten Werte.  
  
|value|Description|  
|-----------|-----------------|  
|*0*|Keine, Klartext ist zulässig|  
|*1*|(Standard) Verschlüsselung erforderlich, keine Klartextprotokollierung|  
|*2*|Klartextanforderungen zulässig, aber nur mit Signaturen (schwächer als die Verschlüsselung)|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servereigenschaften in Analysis Services](server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
