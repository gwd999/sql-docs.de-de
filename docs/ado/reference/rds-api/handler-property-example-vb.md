---
title: "Beispiel für Dateneigenschaften Handler (VB) | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Handler property [ADO], Visual Basic example
ms.assetid: 9664f9a6-65fc-4e7f-be3d-3e4b501b558a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8eaff81d3a43a36b671c31354948da2f54e3f199
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="handler-property-example-vb"></a>Beispiel für Dateneigenschaften Handler (VB)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen nicht, und planen Sie das Ändern von Anwendungen, in denen es zurzeit verwendet wird. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Dieses Beispiel zeigt die [RDS DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt [Handler](../../../ado/reference/rds-api/handler-property-rds.md) Eigenschaft. (Siehe [DataFactory Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md) Weitere Details.)  
  
 Angenommen Sie, in den folgenden Abschnitten in der Parameterdatei "Msdfmap.ini", auf dem Server gespeichert sind:  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 Der Code sieht wie folgt aus. Der Befehl zugewiesen der [SQL](../../../ado/reference/rds-api/sql-property.md) Eigenschaft entspricht der ***AuthorById*** Bezeichner und eine Zeile für den Autor Michael O'Leary abgerufen wird. Die **DataControl** Objekt **Recordset** Eigenschaft zugewiesen ist, einen getrennten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt einfacherer Codierung.  
  
```  
'BeginHandlerVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim dc As New DataControl  
    Dim rst As ADODB.Recordset  
  
    dc.Handler = "MSDFMAP.Handler"  
    dc.ExecuteOptions = 1  
    dc.FetchOptions = 1  
    dc.Server = "http://MyServer"  
    dc.Connect = "Data Source=AuthorDataBase"  
    dc.SQL = "AuthorById('267-41-2394')"  
    dc.Refresh                  'Retrieve the record  
    Set rst = dc.Recordset      'Use another Recordset as a convenience  
    Debug.Print "Author is '" & rst!au_fname & " " & rst!au_lname & "'"  
  
    ' clean up  
    If rst.State = adStateOpen Then rst.Close  
    Set rst = Nothing  
    Set dc = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
    Set dc = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndHandlerVB  
```  
  
## <a name="see-also"></a>Siehe auch  
 [RDS (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Handlereigenschaft (RDS)](../../../ado/reference/rds-api/handler-property-rds.md)


