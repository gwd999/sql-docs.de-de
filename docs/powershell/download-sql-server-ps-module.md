---
title: Herunterladen des SQL Server PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/08/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
keywords:
- SQL Server PowerShell installieren, SQL Server PowerShell herunterladen
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40873fe63b897da52fc9a7d440a8568872431d72
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851755"
---
# <a name="install-sql-server-powershell-module"></a>Installieren des SQL Server PowerShell-Moduls
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Dieser Artikel enthält Anleitungen zur Installation des PowerShell-Moduls **SqlServer**.
> [!NOTE]
> Es gibt zwei SQL Server PowerShell-Module: 
> * **SQLPS:** Dieses Modul ist zwar in der SQL Server-Installation (für die Abwärtskompatibilität) enthalten, wird jedoch nicht mehr aktualisiert. Das **SqlServer**-Modul ist das aktuellste PowerShell-Modul.
> * **SqlServer:** Dieses Modul enthält neue Cmdlets zur Unterstützung der neuesten SQL-Funktionen. Das Modul enthält ebenso aktualisierte Versionen der Cmdlets in **SQLPS**. 

Vorherige Versionen des **SqlServer**-Moduls *waren* in SQL Server Management Studio (SSMS) enthalten, allerdings nur in den Versionen 16.x. Das **SqlServer**-Modul muss über den [PowerShell-Katalog](https://www.powershellgallery.com/packages/Sqlserver) installiert werden, damit PowerShell mit SSMS 17.0 und höher verwendet werden kann.
Die aktuelle Version des **SqlServer**-Moduls lautet 21.0.17279. Diese basiert auf der Version v140 von Microsoft.SQLServer.SMO.  
Wenn Sie nach einer Modulversion suchen, die die nächste Version von SQL Server unterstützt (basierend auf Version v150 von Microsoft.SQLServer.SMO), lesen Sie im Abschnitt ganz unten auf dieser Seite die Informationen, wie Vorabversionen des Moduls abgerufen werden können. Die neueste Vorabversion des Moduls ist 21.1.18040-preview.

Starten Sie eine **PowerShell**-Sitzung, und verwenden Sie folgende Befehle, um das [SqlServer](https://docs.microsoft.com/powershell/scripting/powershell-scripting)-Modul über den PowerShell-Katalog zu installieren. Wenn bei der Installation Probleme auftreten, finden Sie weitere Informationen unter [Install-Module documentation (Dokumentation zu „Install-Module“)](https://docs.microsoft.com/powershell/gallery/psget/module/psget_install-module) und [Install-Module reference (Referenz zu „Install-Module“)](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

So installieren Sie das **SqlServer**-Modul:

```Install-Module -Name SqlServer```

Wenn vorherige Versionen des **SqlServer**-Moduls auf dem Computer vorhanden sind, können Sie wie später in diesem Artikel beschrieben `Update-Module` verwenden oder den Parameter `-AllowClobber` bereitstellen:  

```Install-Module -Name SqlServer -AllowClobber```

Wenn Sie die PowerShell-Sitzung nicht als Administrator ausführen können, können Sie die Installation für den aktuellen Benutzer durchführen:

```Install-Module -Name SqlServer -Scope CurrentUser```

Wenn aktualisierte Versionen des **SqlServer**-Moduls verfügbar sind, können Sie die Version mithilfe von `Update-Module` aktualisieren:

```Update-Module -Name SqlServer```

So zeigen Sie die Versionen der installierten Module an:

```Get-Module SqlServer -ListAvailable```

Wenn Sie eine spezifische Version des Moduls verwenden möchten, können Sie dieses folgendermaßen mit einer spezifischen Versionsnummer importieren:

```Import-Module SqlServer -Version 21.0.17178```

> [!NOTE]
> Vorabversionen (oder „Preview“-Versionen) des Modul sind möglicherweise im PowerShell-Katalog verfügbar. Sie können über die aktualisierten Cmdlets *Find-Module* und *Install-Module*, die Teil des [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet)-Moduls sind, ermittelt und installiert werden, indem der *-AllowPrerelease*-Switch übergeben wird.
>
> Sie können den folgenden Befehl ausführen, um die Vorabversion bzw. Preview-Version des Moduls zu ermitteln:
>
> ```Find-Module SqlServer -AllowPrerelease```
>
> Wenn Sie eine spezifische Vorab-/Preview-Version des Moduls installieren möchten, können Sie dieses folgendermaßen mit einer spezifischen Versionsnummer installieren:
>
> ```Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease```
> 

Die Versionen des **SqlServer**-Moduls im PowerShell-Katalog unterstützen die Versionsverwaltung und erfordern Version 5.0 oder höher von PowerShell. 

* [SqlServer-Modul im PowerShell-Katalog](https://www.powershellgallery.com/packages/Sqlserver) 
* [SqlServer-Cmdlets](https://docs.microsoft.com/powershell/module/sqlserver)
* [SQLPS-Cmdlets](https://docs.microsoft.com/powershell/module/sqlps)
