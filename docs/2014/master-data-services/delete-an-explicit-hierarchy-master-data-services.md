---
title: Löschen einer expliziten Hierarchie (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2ce91292f7c904abfb1e802b4f4600c0e3d1c149
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759162"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>Löschen einer expliziten Hierarchie (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie eine explizite Hierarchie löschen, die Sie nicht mehr benötigen.  
  
> [!WARNING]  
>  Wenn Sie eine explizite Hierarchie löschen, werden alle konsolidierten Elemente in der Hierarchie ebenfalls gelöscht. Wenn Sie alle expliziten Hierarchien für eine Entität löschen, werden auch alle Auflistungen für die Entität gelöscht und die Entität ist nicht mehr für explizite Hierarchien und Auflistungen aktiviert.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md)zuzugreifen.  
  
### <a name="to-delete-an-explicit-hierarchy"></a>So löschen Sie eine explizite Hierarchie  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie die Zeile der Entität aus, die die zu löschende explizite Hierarchie enthält.  
  
5.  Klicken Sie auf **Ausgewählte Entität bearbeiten**.  
  
6.  Auf der **Entität bearbeiten** auf der Seite die **explizite Hierarchien** Bereich, klicken Sie auf die explizite Hierarchie, die Sie löschen möchten.  
  
7.  Klicken Sie auf **ausgewählte Hierarchie löschen**.  
  
8.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
9. Klicken Sie im zusätzlichen Bestätigungsdialogfeld auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
