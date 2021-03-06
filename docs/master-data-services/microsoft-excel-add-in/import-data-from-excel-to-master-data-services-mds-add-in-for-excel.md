---
title: Importieren von Daten aus Excel in Master Data Services (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 7e987ab75413334865b5e7d577860c498540adcd
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53200850"
---
# <a name="import-data-from-excel-to-master-data-services-mds-add-in-for-excel"></a>Importieren von Daten aus Excel in Master Data Services (MDS-Add-In für Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Veröffentlichen Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]Daten an das MDS-Repository, wenn Sie mit der Arbeit in Excel fertig sind und die Änderungen speichern möchten, damit andere Benutzer Zugriff auf sie haben.  
  
> [!NOTE]
>  -   Wenn Sie Änderungen veröffentlichen, werden die Kommentare zu von MDS verwalteten Zellen gelöscht.  
> -   Eine Formel wird in einer von MDS verwalteten Zelle nicht unterstützt. Eine Formel in einer von MDS verwalteten Zelle wird als Textwert behandelt.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Das aktive Arbeitsblatt muss von MDS verwaltete Daten enthalten, und Sie müssen Änderungen oder Hinzufügungen zu den von MDS verwalteten Daten vorgenommen haben.  
  
-   Wenn Sie Elemente hinzufügen, müssen Sie keinen **Code** -Wert angeben, wenn Codes für die Entität automatisch generiert werden. Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](../../master-data-services/automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>So veröffentlichen Sie Daten im MDS-Repository  
  
1.  Klicken Sie in der Gruppe **Veröffentlichen und Validieren** auf **Veröffentlichen**.  
  
2.  Optional. Wenn das Dialogfeld **Veröffentlichen und mit Anmerkung versehen** angezeigt wird, wählen Sie die Freigabe der gleichen Anmerkung (Kommentar) für alle Updates oder die Kommentierung jeder Änderung einzeln.  
  
3.  Optional. Aktivieren Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** . Sie können das Dialogfeld zukünftig immer anzeigen, indem Sie **Einstellungen** auswählen und das Kontrollkästchen **Dialogfeld 'Veröffentlichen und mit Anmerkung versehen' beim Veröffentlichen anzeigen** aktivieren.  
  
4.  Klicken Sie auf **Veröffentlichen**.  
  
> [!NOTE]  
>  Wenn Sie dem Arbeitsblatt neue Elemente (Zeilen) hinzufügen, sie aber nicht erfolgreich im MDS-Repository veröffentlichen können, verfügen Sie möglicherweise nicht für alle Attribute im Arbeitsblatt über die Berechtigung **Aktualisieren** . Klicken Sie auf der Registerkarte **Überprüfen** in der Gruppe **Änderungen** auf **Blattschutz aufheben** , und versuchen Sie, erneut zu veröffentlichen.  
  
## <a name="next-steps"></a>Next Steps  
 [Anwenden von Geschäftsregeln &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht: Importieren von Daten aus Excel &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Überprüfen von Daten &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
  
