---
title: Benutzerdefinierte Berichtselemente | Microsoft-Dokumentation
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7f761af835db61d9c2d5f3071ff4da9b4f445ad6
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52400413"
---
# <a name="custom-report-items"></a>Custom Report Items
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält ein komplexes Toolset für die Erstellung und Veröffentlichung von Unternehmensberichten, für die Verwaltung der Zugriffsrechte und Abonnements und die Erweiterung der Berichtsfunktionen durch eine umfassende API. Die Berichte werden mit der XML-Sprache RDL (Report Definition Language) definiert. RDL verfügt über einen Satz von Anweisungen, die Layout, Abfrageinformationen und Elementtypen eines Berichts beschreiben. Es ist möglich, RDL durch das Schreiben eines benutzerdefinierten Berichtselements zu erweitern. Das benutzerdefinierte Berichtselement besteht aus einer Laufzeitkomponente, die vom Berichtsprozessor zur Laufzeit aufgerufen wird, und einer Entwurfszeitkomponente, die das benutzerdefinierte Berichtselement im Berichts-Designer zur Verfügung stellt.  
  
 Ein Beispiel für ein vollständig implementiertes benutzerdefiniertes Berichtselement finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-scenarios"></a>Szenarien für benutzerdefinierte Berichtselemente  
 Es kann sein, dass Entwickler, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in Ihre Anwendungen integrieren müssen, Funktionen benötigen, die ursprünglich nicht in der RDL unterstützt werden. Dazu können folgende Elemente gehören: Zuordnungssteuerelemente, horizontale Listen, Spaltenlisten und Repivotable-Matrizen. Eine Laufzeitkomponente für ein benutzerdefiniertes Berichtselement kann zu diesem Zweck mit einer Anwendung entwickelt und verteilt werden.  
  
 Möglicherweise möchten einige Entwickler zusätzlich zur Entwicklung von Funktionen, die ursprünglich nicht unterstützt wurden, bestehende Funktionen durch Alternativversionen der Steuerelemente erweitern, die bereits in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthalten sind. In diesem Szenario könnte ein Entwickler drei Komponenten anbieten: eine Laufzeitkomponente, eine Entwurfszeitkomponente und eine Laufzeitkonvertierungskomponente, mit der ein vorhandenes Berichtselement bei Bedarf in ein benutzerdefiniertes Berichtselement umgewandelt wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Custom Report Item Architecture (Architektur des benutzerdefinierten Berichtselements)](../../reporting-services/custom-report-items/custom-report-item-architecture.md)  
 Erläutert die Komponenten, aus denen ein benutzerdefiniertes Berichtselement besteht.  
  
 [Custom Report Item Implementation Requirements (Implementierungsanforderungen für benutzerdefinierte Berichtselemente)](../../reporting-services/custom-report-items/custom-report-item-implementation-requirements.md)  
 Beschreibt die Voraussetzungen für die Erstellung eines benutzerdefinierten Berichtselements.  
  
 [Creating a Custom Report Item Run-Time Component (Erstellen einer Laufzeitkomponente für ein benutzerdefiniertes Berichtselement)](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)  
 Beschreibt, wie eine benutzerdefinierte Laufzeitkomponente für ein Berichtselement erstellt wird.  
  
 [Creating a Custom Report Item Design-Time Component (Erstellen einer Entwurfszeitkomponente für ein benutzerdefiniertes Berichtselement)](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)  
 Beschreibt, wie eine benutzerdefinierte Entwurfszeitkomponente für ein Berichtselement erstellt wird.  
  
 [Vorgehensweise: Bereitstellen eines benutzerdefinierten Berichtselements](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
 Beschreibt, wie ein benutzerdefiniertes Berichtselement angewendet wird.  
  
 [Custom Report Item Class Libraries (Klassenbibliotheken für ein benutzerdefiniertes Berichtselement)](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
 Beschreibt die Infrastrukturklassen benutzerdefinierter Berichtselemente und die verwalteten Wrapperklassen im **Microsoft.ReportDesigner** -Namespace.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Technische Referenz &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
