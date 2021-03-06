---
title: Partition Speichermodi und Verarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- hybrid OLAP
- data storage [Analysis Services]
- relational OLAP
- multidimensional OLAP
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- HOLAP
- MOLAP
- ROLAP
ms.assetid: 86d17547-a0b6-47ac-876c-d7a5b15ac327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ffb6331f3e02c0974320d8d9c71df9aff7602874
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507789"
---
# <a name="partition-storage-modes-and-processing"></a>Speichermodi und Verarbeitung von Partitionen
  Der Speichermodus einer Partition wirkt sich auf die Abfrage- und Verarbeitungsleistung, die Speicheranforderungen und die Speicherorte der Partition, der übergeordneten Measuregruppe und des übergeordneten Cubes aus. Die Entscheidung für einen Speichermodus wirkt sich zudem auf die Verarbeitungsmöglichkeiten aus.  
  
 Für eine Partition kann einer von drei grundlegenden Speichermodi verwendet werden:  
  
-   Mehrdimensionale OLAP (MOLAP)  
  
-   Relationale OLAP (ROLAP)  
  
-   Hybride OLAP (HOLAP)  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt alle drei grundlegenden Speichermodi. Zudem wird die proaktive Zwischenspeicherung unterstützt. Damit können die Merkmale der ROLAP-Speicherung und der MOLAP-Speicherung sowohl für die Unmittelbarkeit der Daten als auch für die Abfrageleistung kombiniert werden. Weitere Informationen finden Sie unter [Proaktives Zwischenspeichern &#40;Partitionen&#41;](partitions-proactive-caching.md).  
  
## <a name="molap"></a>MOLAP  
 Der Speichermodus MOLAP bewirkt, dass die Aggregationen der Partition sowie eine Kopie der zugehörigen Quelldaten in einer mehrdimensionalen Struktur in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert werden, wenn die Partition verarbeitet wird. Diese MOLAP-Struktur ist stark optimiert, um die Abfrageleistung zu maximieren. Als Speicherort kann der Computer, auf dem die Partition definiert wurde, oder ein anderer Computer mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]verwendet werden. Da sich eine Kopie der Quelldaten in der mehrdimensionalen Struktur befindet, können Abfragen aufgelöst werden, ohne auf die Quelldaten der Partition zuzugreifen. Durch das Verwenden von Aggregationen können die Antwortzeiten für Abfragen erheblich verbessert werden. Die Daten in der MOLAP-Struktur der Partition sind nur so aktuell wie am Datum, an dem die letzte Verarbeitung der Partition erfolgte.  
  
 Da sich die Quelldaten ändern, müssen Objekte mit MOLAP-Speicherung regelmäßig verarbeitet werden, um diese Änderungen aufzunehmen und sie den Benutzern zur Verfügung zu stellen. Durch die Verarbeitung werden die Daten in der MOLAP-Struktur entweder vollständig oder inkrementell aktualisiert. Die Zeit zwischen zwei Verarbeitungsvorgängen bewirkt eine Latenzzeit, während derer Daten in OLAP-Objekten möglicherweise nicht mit den Quelldaten übereinstimmen. Sie können Objekte mit MOLAP-Speicherung inkrementell oder vollständig aktualisieren, ohne die Partition oder den Cube offline schalten zu müssen. In bestimmten Situationen kann es jedoch erforderlich sein, einen Cube offline zu schalten, um bestimmte Strukturänderungen an OLAP-Objekten zu verarbeiten. Sie können die zum Aktualisieren der MOLAP-Speicherung erforderliche Ausfallzeit minimieren, indem Sie Cubes auf einem Stagingserver aktualisieren und verarbeiten und die verarbeiteten Objekte mithilfe der Datenbanksynchronisierung auf den Produktionsserver kopieren. Sie können auch die proaktive Zwischenspeicherung verwenden, um die Latenzzeit zu minimieren und die Verfügbarkeit zu optimieren und dabei gleichzeitig die Leistungsvorteile der MOLAP-Speicherung weiter zu nutzen. Weitere Informationen finden Sie unter [proaktives Zwischenspeichern &#40;Partitionen&#41;](partitions-proactive-caching.md), [Analysis Services-Datenbanken synchronisieren](../multidimensional-models/synchronize-analysis-services-databases.md), und [mehrdimensionales Objekt Modellverarbeitung](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
## <a name="rolap"></a>ROLAP  
 Der Speichermodus ROLAP bewirkt, dass die Aggregationen der Partition in indizierten Sichten in der relationalen Datenbank gespeichert werden, die in den Quelldaten der Partition angegeben wurde. Anders als beim Speichermodus MOLAP wird beim Speichermodus ROLAP keine Kopie der Quelldaten in den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenordnern gespeichert. Wenn Ergebnisse nicht aus dem Abfragecache übernommen werden können, werden Abfragen stattdessen mithilfe der indizierten Sichten in der Datenquelle beantwortet. Beim ROLAP-Speicher erfolgt die Beantwortung von Abfragen i. A. langsamer als bei Verwendung der Speichermodi MOLAP oder HOLAP. Auch die Verarbeitungszeit ist bei ROLAP üblicherweise länger. ROLAP ermöglicht den Benutzern jedoch das Anzeigen von Daten in Echtzeit und kann dazu beitragen, Speicherplatz zu sparen, wenn Sie mit großen Datasets arbeiten, die nur unregelmäßig abgefragt werden, z. B. mit reinen Vergangenheitsdaten.  
  
> [!NOTE]  
>  Bei Verwendung von ROLAP gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] möglicherweise fehlerhafte Informationen bezüglich des unbekannten Elements zurück, falls ein Join mit einer GROUP BY-Klausel kombiniert wird. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] entfernt relationale Integritätsfehler anstatt den unbekannten Elementwert zurückzugeben.  
  
 Wenn eine Partition den Speichermodus ROLAP verwendet und die zugehörigen Quelldaten in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]gespeichert sind, erstellt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] indizierte Sichten, die Aggregationen der Partition enthalten. Wenn [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keine indizierten Sichten erstellen kann, werden keine Aggregationstabellen erstellt. Obwohl die Sitzungsanforderungen für das Erstellen indizierter Sichten im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] durch [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]behandelt werden, müssen für das Erstellen indizierter Sichten für Aggregationen durch [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die folgenden Bedingungen durch die ROLAP-Partition und die Tabellen im zugehörigen Schema erfüllt sein:  
  
-   Die Partition darf keine Measures enthalten, die die Aggregatfunktionen `Min` oder `Max` verwenden.  
  
-   Jede Tabelle im Schema der ROLAP-Partition darf nur einmal verwendet werden. Das Schema darf beispielsweise nicht [dbo].[address] AS "Customer Address" und [dbo].[address] AS "SalesRep Address" enthalten.  
  
-   Jede Tabelle muss eine Tabelle sein, keine Sicht.  
  
-   Alle Tabellennamen im Schema der Partition müssen mit dem Besitzernamen gekennzeichnet sein, z. B. [dbo].[customer].  
  
-   Alle Tabellen im Schema der Partition müssen denselben Besitzer aufweisen. Sie können beispielsweise keine FROM-Klausel verwenden, die auf die Tabellen in [tk].[customer], [john].[store] und [dave].[sales_fact_2004] verweist.  
  
-   Die Quellspalten der Measures der Partition dürfen keine NULL-Werte zulassen.  
  
-   Beim Erstellen aller in der Sicht verwendeten Tabellen müssen die folgenden Optionen auf ON festgelegt sein:  
  
    -   ANSI_NULLS  
  
    -   QUOTED_IDENTIFIER  
  
-   Die Gesamtgröße des Indexschlüssels in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]darf 900 Bytes nicht überschreiten. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] implementiert diese Bedingung anhand von Schlüsselspalten mit fester Länge, wenn die CREATE INDEX-Anweisung verarbeitet wird. Falls der Indexschlüssel jedoch Spalten variabler Länge enthält, überprüft [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Bedingung auch bei jedem Update der Basistabellen. Da unterschiedliche Aggregationen unterschiedliche Sichtdefinitionen aufweisen, kann die ROLAP-Verarbeitung mithilfe indizierter Sichten je nach Aggregationsentwurf erfolgreich verlaufen oder fehlschlagen.  
  
-   Für die Sitzung, in der die indizierte Sicht erstellt wird, müssen die folgenden Optionen den Wert ON aufweisen: ARITHABORT, CONCAT_NULL_YEILDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING und ANSI_WARNING. Diese Einstellung kann in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]vorgenommen werden.  
  
-   Für die Sitzung, in der die indizierte Sicht erstellt wird, muss die folgende Option den Wert OFF aufweisen: NUMERIC_ROUNDABORT. Diese Einstellung kann in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]vorgenommen werden.  
  
## <a name="holap"></a>HOLAP  
 Der Speichermodus HOLAP kombiniert Attribute von MOLAP und ROLAP. Wie bei MOLAP bewirkt auch HOLAP, dass die Aggregationen der Partition in einer mehrdimensionalen Struktur in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert werden. Die Verwendung von HOLAP führt nicht dazu, dass eine Kopie der Quelldaten gespeichert wird. Bei Abfragen, die lediglich auf zusammengefasste Daten in den Aggregationen einer Partition zugreifen, ist HOLAP das Äquivalent zu MOLAP. Abfragen, die Quelldaten zugreifen – beispielsweise sollten Sie eine atomare Cubezelle Drilldown für den es keine Aggregation Daten muss Daten aus der relationalen Datenbank abgerufen werden und werden nicht so schnell, wie dies der Fall wäre, wenn die Quelldaten in der MOLAP-Structur gespeichert wurden e. Beim Speichermodus HOLAP werden Benutzer normalerweise erhebliche Unterschiede bei den Abfragezeiten feststellen, je nachdem, ob die Abfrage anhand das Caches oder mittels Aggregationen aufgelöst werden kann oder ob hierzu die Quelldaten selbst benötigt werden.  
  
 Partitionen mit HOLAP-Speicherung sind kleiner als die vergleichbaren MOLAP-Partitionen, da sie keine Quelldaten enthalten, und antworten schneller als ROLAP-Partitionen auf Abfragen, die zusammengefasste Daten einbeziehen. Der Speichermodus HOLAP eignet sich i. A. für Partitionen in Cubes, die schnelle Abfrageantworten für Zusammenfassungen erfordern, die auf großen Mengen von Quelldaten basieren. Wenn Benutzer jedoch Abfragen generieren, die auf Daten auf Blattebene zugreifen müssen, wie z. B. beim Berechnen des Medians, eignet sich MOLAP i. A. besser.  
  
## <a name="see-also"></a>Siehe auch  
 [Proaktives Zwischenspeichern &#40;Partitionen&#41;](partitions-proactive-caching.md)   
 [Synchronisieren von Analysis Services-Datenbanken](../multidimensional-models/synchronize-analysis-services-databases.md)   
 [Partitionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](partitions-analysis-services-multidimensional-data.md)  
  
  
