---
title: Analysis Services-Verbindungstyp für DMX (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], DMX
- Data Mining Prediction [Reporting Services]
- query view [Reporting Services]
- DMX [Reporting Services]
- design view [Reporting Services]
- data mining [Reporting Services]
- passing parameters [Reporting Services]
ms.assetid: 2de825e9-6d8a-4128-add0-da15dc6cea3e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a909c905fd9cb61df019f2db5eca85279cc85a8c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085660"
---
# <a name="analysis-services-connection-type-for-dmx-ssrs"></a>Analysis Services-Verbindungstyp für DMX (SSRS)
  Wenn Sie ein Dataset mithilfe einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquelle erstellen, wird vom Berichts-Designer standardmäßig der MDX-Abfrage-Designer (Multidimensional Expressions) angezeigt, sobald ein gültiger Cube erkannt wird. Falls kein Cube erkannt wird, jedoch ein Data Mining-Modell verfügbar ist, zeigt der Berichts-Designer den DMX-Abfrage-Designer (Data Mining-Erweiterungen) an. Klicken Sie für einen Wechsel zwischen dem MDX- und dem DMX-Designer auf die Schaltfläche **DMX-Befehlstyp** (![Ändern der Anzeige der DMX-Abfragesprache](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")) auf der Symbolleiste. Mithilfe des DMX-Abfrage-Designers können Sie interaktiv eine DMX-Abfrage erstellen, die grafische Elemente verwendet. Damit der DMX-Abfrage-Designer verwendet werden kann, muss die angegebene Datenquelle bereits über ein Data Mining-Modell verfügen, das die Daten bereitstellt. Die Abfrageergebnisse werden für die Verwendung im Bericht in ein vereinfachtes Rowset konvertiert.  
  
> [!NOTE]  
>  Vor dem Entwerfen Ihres Berichts müssen Sie Ihr Modell trainieren. Weitere Informationen finden Sie unter [Data Mining-Projektmappen](../../analysis-services/data-mining/data-mining-solutions.md).  
  
## <a name="design-mode"></a>Entwurfsmodus  
 Der DMX-Abfrage-Designer wird im Entwurfsmodus geöffnet. Der Entwurfsmodus umfasst eine grafische Entwurfsoberfläche, die zum Auswählen eines einzelnen Data Mining-Modells und einer Eingabetabelle verwendet wird, und ein Raster zum Angeben der Vorhersageabfrage. Im DMX-Abfrage-Designer gibt es zwei weitere Modi: den Abfragemodus und den Ergebnismodus. Im Abfragemodus wird das Raster aus dem Entwurfsmodus durch einen Abfragebereich ersetzt, den Sie für die Eingabe von DMX-Abfragen verwenden können. Im Ergebnismodus wird das von der Abfrage zurückgegebene Resultset in einem Datenraster angezeigt.  
  
 Wenn Sie die Modi für den DMX-Abfrage-Designer ändern möchten, klicken Sie mit der rechten Maustaste auf die Abfrageentwurfsoberfläche, und wählen Sie **Entwurf**, **Abfrage**oder **Ergebnis**aus. Weitere Informationen finden Sie unter [Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services](analysis-services-dmx-query-designer-user-interface.md) und [Abrufen von Daten aus einem Data Mining-Modell (DMX) (SSRS)](retrieve-data-from-a-data-mining-model-dmx-ssrs.md).  
  
## <a name="designing-a-prediction-query"></a>Entwerfen einer Vorhersageabfrage  
 Der Bereich Abfrageentwurf im Entwurfsmodus enthält zwei Fenster: **Miningmodell** und **Eingabetabelle(n) auswählen**. Verwenden Sie das Fenster **Miningmodell** , um das für die Abfrage zu verwendende Miningmodell auszuwählen. Verwenden Sie das Fenster **Eingabetabelle(n) auswählen** , um die Tabelle auszuwählen, auf der Sie Ihre Vorhersagen basieren möchten. Wenn Sie anstelle einer Eingabetabelle eine SINGLETON-Abfrage verwenden möchten, klicken Sie mit der rechten Maustaste in den Bereich Abfrageentwurf, und wählen Sie **SINGLETON-Abfrage**aus. Das Fenster **Eingabetabelle(n) auswählen** wird durch das Fenster **SINGLETON-Abfrageeingabe** ersetzt.  
  
 Ziehen Sie im Entwurfsmodus die Felder aus den Fenstern **Miningmodell** und **Eingabetabelle(n) auswählen** in die **Feld** -Spalte des Rasterbereichs. Sie können bei Bedarf die verbleibenden Spalten ausfüllen, um einen Alias anzugeben, um das Feld in den Ergebnissen anzuzeigen, um Felder zusammen zu gruppieren und um einen Operator einzugeben, mit dem der Feldwert auf bestimmte Kriterien oder ein Argument begrenzt wird. Wenn Sie sich im Abfragemodus befinden, erstellen Sie die DMX-Abfrage, indem Sie Felder in den Bereich Abfrage ziehen.  
  
## <a name="using-parameters"></a>Verwenden von Parametern  
 Sie können Berichtsparameter an einen DMX-Abfrageparameter übergeben. Hierzu müssen Sie Ihrer DMX-Abfrage einen Parameter hinzufügen, die Abfrageparameter im Dialogfeld **Abfrageparameter** definieren und dann die zugeordneten Berichtsparameter ändern. Klicken Sie für das Definieren eines Abfrageparameters auf die Schaltfläche **Abfrageparameter** (![Symbol für das Dialogfeld „Abfrageparameter“](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")) auf der Symbolleiste. Eine Anleitung zum Definieren von Parametern in einer DMX-Abfrage finden Sie unter [Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services &#40;Berichts-Generator und SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md).  
  
 Weitere Informationen zum Verwalten der Beziehung zwischen Berichtsparametern und Abfrageparametern finden Sie unter [Zuordnen eines Abfrageparameters zu einem Berichtsparameter (Berichts-Generator und SSRS)](associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md). Weitere Informationen zu Parametern finden Sie unter [Berichtsparameter (Berichts-Generator und Berichts-Designer)](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Projektmappen](../../analysis-services/data-mining/data-mining-solutions.md)   
 [Abfrageentwurfstools im Berichts-Designer SQL-Server-Datatools &#40;SSRS&#41;](query-design-tools-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
