---
title: Erste Schritte mit SQL Server (unter Linux) in der Cloud
titleSuffix: SQL Server
description: Dieser Schnellstart veranschaulicht das Ausführen von SQL Server unter Linux in der Cloud Ihrer Wahl.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 10/25/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 77e818109424b5f0d9dea3b495da4e927c506366
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299237"
---
# <a name="quickstart-run-sql-server-in-the-cloud"></a>Schnellstart: Führen Sie SQL Server in der cloud

  > [!div class="nextstepaction"]
  > [Teilen Sie uns Ihr Feedback zu SQL-Dokumentation des Inhaltsverzeichnisses!](https://aka.ms/sqldocsurvey)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Schnellstart installieren Sie SQL Server unter Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) oder Ubuntu in der Cloud Ihrer Wahl. Wechseln Sie zu [Bereitstellen eines virtuellen SQL Server-virtuellen Computers im Azure-Portal](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) zum Ausführen von SQL Server unter Linux in Azure.

> [!NOTE]
> Wenn Sie eine kostenpflichtige Edition von SQL Server ausführen, müssen Sie Ihre vorhandenen Lizenzen (BYOL) einbinden.

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Erstellen Sie einen Linux AMI mit mindestens 2 GB Speicher aus dem marketplace 
    * [RHEL 7.3 UND HÖHER](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Herstellen einer Verbindung mit dem AMI mit ssh
1.  Führen Sie den Schnellstart für die Linux-Distribution, die Sie ausgewählt haben: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Konfigurieren Sie für Remoteverbindungen: 
    * Öffnen der [Amazon EC2-Konsole]( https://console.aws.amazon.com/ec2/)
    * Wählen Sie im Navigationsbereich **Sicherheitsgruppen**. 
    * Wählen Sie **für eingehende Daten, bearbeiten "," Regel hinzufügen**
    * Hinzufügen einer eingehenden Regel zum Zulassen von Datenverkehr, auf dem Port, auf dem SQL Server (standardmäßig TCP-Port 1433) lauscht

    
## <a name="digital-ocean"></a>Digital Ocean
1. Melden Sie sich bei der [Systemsteuerung](https://cloud.digitalocean.com/login) und klicken Sie auf ein Droplet erstellen
1. Wählen Sie eine Ubuntu 16.04 Droplet mit mindestens 2 GB Arbeitsspeicher
1. Herstellen einer Verbindung mit der Droplet mit ssh
1. Führen Sie die [Ubuntu-Schnellstart](quickstart-install-connect-ubuntu.md)
1. Konfigurieren Sie für Remoteverbindungen:
    * Am oberen Rand der Systemsteuerung, befolgen Sie die **Networking** verknüpfen, und wählen Sie dann **Firewalls**
    * Hinzufügen einer eingehenden Regel zum Zulassen von Datenverkehr, auf dem Port, auf dem SQL Server (standardmäßig TCP-Port 1433) lauscht
    
## <a name="google-cloud-platform"></a>Google Cloud-Plattform
1.  Erstellen Sie ein Linux-Image mit mindestens 2 GB Speicher aus dem Cloud-Startfeld 
    * [RHEL 7.3 UND HÖHER](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Herstellen einer Verbindung mit dem Image mit ssh
1.  Führen Sie den Schnellstart für die Linux-Distribution, die Sie ausgewählt haben: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Konfigurieren Sie für Remoteverbindungen: 
    * Wechseln Sie zu der [Firewall-Regeln](https://console.cloud.google.com/networking/firewalls)
    * Hinzufügen einer eingehenden Regel zum Zulassen von Datenverkehr über den Port, auf dem SQL Server lauscht (standardmäßig Tcp: 1433)
