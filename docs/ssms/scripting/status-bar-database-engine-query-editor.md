---
title: Statusleiste (Abfrage-Editor der Datenbank-Engine) | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d9d870762becec1ff0717c4e9d7aef5eda7be94c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52541903"
---
# <a name="status-bar-database-engine-query-editor"></a>Statusleiste (Abfrage-Editor der Datenbank-Engine)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Die Statusleiste des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fensters kann farblich codiert sein, um so anzuzeigen, mit welcher Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)] jedes Fenster verbunden ist.  
  
1.  **Vorbereitungen:**  [Statusleistenfarben](#StatusBarColors)  
  
2.  **Um eine Serverstatusfarbe einzurichten in:**  [Objekt-Explorer](#SetOEServerColor), [Registrierter Server](#SetRegServerColor)  
  
3.  **Um eine Statusfarbe zu verwenden:**  [Abfrage-Editor mithilfe einer Serverfarbe öffnen](#OpenServerColor), [Abfrage-Editor unter Angabe einer Statusfarbe öffnen](#OpenSpecColor)  
  
##  <a name="StatusBarColors"></a> Statusleistenfarben  
 Sie können einem bestimmten Serverknoten in entweder **Objekt-Explorer** oder **Registrierte Server**eine Statusleistenfarbe zuordnen. Die Farben können nur für Serverknoten angegeben werden, die mit einer Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden sind, nicht aber für Serverknoten für andere SQL Server-Technologien. Ebenso können Sie eine benutzerdefinierte Statusleistenfarbe angeben, wann immer Sie ein neues [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenster mit einer Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbinden. Sie können dann entweder mit der für den Serverknoten definierten Statusfarbe ein Abfrage-Editor-Fenster öffnen oder eine eindeutige Farbe für dieses Editorfenster angeben.  
  
 Eine benutzerdefinierte Statusleistenfarbe für einen Serverknoten in Objekt-Explorer muss beim Herstellen der Verbindung festgelegt werden. Um die einem vorhandenen Serverknoten zugeordnete Farbe zu ändern, müssen Sie die Verbindung trennen und dann unter Angabe der neuen Farbe die Verbindung erneut herstellen.  
  
##  <a name="SetOEServerColor"></a> Festlegen der Statusfarbe für einen Server in Objekt-Explorer  
 **So legen Sie eine Serverstatusfarbe in Objekt-Explorer fest**  
  
1.  Wählen Sie im **Objekt-Explorer** die Schaltfläche **Verbinden** und dann **Datenbank-Engine...** aus.  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** die Option **Optionen >>**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Benutzerdefinierte Farbe verwenden** .  
  
4.  Wählen Sie zur Festlegung der Farbe die Schaltfläche **Auswählen...** aus.  
  
5.  Wählen Sie entweder eine standardmäßige oder benutzerdefinierte Farbe aus und klicken Sie dann auf OK.  
  
6.  Geben Sie die restlichen Verbindungsinformationen ein und wählen Sie dann die Schaltfläche **Verbinden** aus.  
  
##  <a name="SetRegServerColor"></a> Festlegen der Statusfarbe für einen Registrierter Server  
 **So legen Sie eine Serverfarbe für einen Registrierten Server fest**  
  
1.  Klicken Sie unter **Registrierte Server** mit der rechten Maustaste auf einen Serverknoten, und wählen Sie dann **Eigenschaften...** aus.  
  
2.  Wählen Sie im Dialogfeld **Serverregistrierungseigenschaften bearbeiten** die Registerkarte **Verbindungseigenschaften** aus.  
  
3.  Aktivieren Sie das Kontrollkästchen **Benutzerdefinierte Farbe verwenden** .  
  
4.  Wählen Sie zur Festlegung der Farbe die Schaltfläche **Auswählen...** aus.  
  
5.  Wählen Sie entweder eine standardmäßige oder benutzerdefinierte Farbe aus und klicken Sie dann auf OK.  
  
6.  Wählen Sie im Dialogfeld **Serverregistrierungseigenschaften bearbeiten** die Schaltfläche **Speichern** aus.  
  
##  <a name="OpenServerColor"></a> Öffnen eines Editors mithilfe einer Serverfarbe  
 **So öffnen Sie ein Editorfenster mithilfe einer Serverfarbe**  
  
-   Klicken Sie mit der rechten Maustaste entweder in **Objekt-Explorer** oder **Registrierte Server**auf einen Serverknoten, und wählen Sie **Neue Abfrage**aus.  
  
-   Markieren Sie alternativ einen Serverknoten und wählen Sie dann die Symbolleistenschaltfläche **Neue Abfrage** aus.  
  
-   Die Statusleiste im Editorfenster verwendet die für den zugeordneten Server definierte Farbe.  
  
##  <a name="OpenSpecColor"></a> Öffnen eines Editors unter Angabe einer Statusfarbe  
 **So öffnen Sie ein Editorfenster unter Angabe einer Statusfarbe**  
  
-   Öffnen Sie das Menü **Datei**, wählen Sie **Neu** aus, und wählen Sie dann **Datenbank-Engine-Abfrage** aus.  
  
-   Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** die Option **Optionen >>**.  
  
-   Aktivieren Sie das Kontrollkästchen **Benutzerdefinierte Farbe verwenden** .  
  
-   Wählen Sie zur Festlegung der Farbe die Schaltfläche **Auswählen...** aus.  
  
-   Wählen Sie entweder eine standardmäßige oder benutzerdefinierte Farbe aus und klicken Sie dann auf OK.  
  
-   Geben Sie die restlichen Verbindungsinformationen ein und wählen Sie dann die Schaltfläche **Verbinden** aus.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Abfrage- und Text-Editoren &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
