---
title: Wiederherstellen der Datenbank (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9231189bb3bf127c7413a0b5d55ae286a32f42cc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091030"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld Datenbank wiederherstellen (Analysis Services – Mehrdimensionale Daten)
  Im Dialogfeld **Datenbank wiederherstellen** von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie eine Datenbank von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aus einer Sicherungsdatei wiederherstellen, die im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-eigenen Format für Sicherungsdateien (*.abf) erstellt wurde.  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Wiederherstellungsbefehl ausführt, über die Berechtigung zum Lesen von dem für jede Datei angegebenen Sicherungsspeicherort verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank, die nicht auf dem Server installiert ist, muss der Benutzer zusätzlich Mitglied der Serverrolle für die betreffende [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz sein. Zum Überschreiben einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank muss der Benutzer entweder Mitglied der Serverrolle für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit den Berechtigungen "Vollzugriff" (Administrator) für die wiederherzustellende Datenbank sein.  
  
> [!NOTE]  
>  Nach dem Wiederherstellen einer vorhandenen Datenbank verliert der Benutzer, der die Datenbank wiederhergestellt hat, möglicherweise den Zugriff auf diese Datenbank. Dies ist u. U. der Fall, wenn der Benutzer zum Zeitpunkt der Sicherung kein Mitglied der Serverrolle oder der Datenbankrolle mit der Berechtigung "Vollzugriff (Administrator)" war.  
  
 **Um das Dialogfeld Wiederherstellungsdatenbank anzuzeigen.**  
  
-   Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste entweder auf den Ordner **Datenbanken** einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder auf eine Datenbank im **Objekt-Explorer**, und klicken Sie anschließend auf **Wiederherstellen**.  
  
 Das Dialogfeld **Datenbank wiederherstellen** enthält die folgenden Seiten.  
  
## <a name="pages"></a>Seiten  
 **Allgemein**  
 Auf dieser Seite können Sie die wiederherzustellende Datenbank auswählen sowie die Sicherungsdatei, aus der die Datenbank wiederhergestellt werden soll. Darüber hinaus können Sie einige allgemeine Optionen und das Kennwort festlegen, das beim Wiederherstellen der Datenbank verwendet werden soll. Weitere Informationen zu dieser Seite finden Sie unter [Allgemein &#40;Dialogfeld „Datenbank wiederherstellen“, Analysis Services – mehrdimensionale Daten&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Partitionen**  
 Mithilfe dieser Seite können Sie lokale Partitionen an angegebenen Speicherorten wiederherstellen und Remotepartitionen aus Remotesicherungsdateien wiederherstellen. Weitere Informationen zu dieser Seite finden Sie unter [Partitionen &#40;Dialogfeld „Datenbank wiederherstellen“, Analysis Services – mehrdimensionale Daten&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
