---
title: Azure Data Lake Store Source | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2037890618a4977135d6366d8d84bb84a9c67744
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129434"
---
# <a name="azure-data-lake-store-source"></a>Azure Data Lake Store Source
  Die Komponente **Azure Data Lake Store Source** ermöglicht einem SSIS-Paket das Lesen von Daten aus Azure Data Lake Store. Die unterstützten Dateiformate sind: Text und Avro.
  
## <a name="configure-the-azure-data-lake-store-source"></a>Konfigurieren von Azure Data Lake Store Source 
  
1.  Um den Editor für Azure Data Lake Store Source aufzurufen, ziehen Sie die **Azure Data Lake Store Source** auf den Datenfluss-Designer, und doppelklicken Sie darauf, um den Editor zu öffnen.  
  
2.  Geben Sie im Feld **Azure Data Lake Store connection manager** (Azure Data Lake Store-Verbindungs-Manager) einen vorhandenen Azure Data Lake Store-Verbindungs-Manager an, oder erstellen Sie einen neuen, der auf einen Azure Data Lake Store-Dienst verweist.  
  
    1.  Geben Sie im Feld **Dateipfad** den Dateipfad der Quelldatei in Azure Data Lake Store an.   
  
    2.  Geben Sie im Feld **Dateiformat** das Dateiformat der Quelldatei an.  
  
        Wenn es sich um Textformat handelt, geben Sie den Wert für das **Spaltentrennzeichen** ein. Aktivieren Sie außerdem **Spaltennamen in der ersten Datenzeile** , wenn die erste Zeile in der Datei Spaltennamen enthält.  
  
3.  Nachdem Sie die Verbindungsinformationen angegeben haben, wechseln Sie zur Seite **Spalten** , um Quellspalten zu den Zielspalten für den SSIS-Datenfluss zuzuordnen.  
