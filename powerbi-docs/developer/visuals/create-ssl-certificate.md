---
title: Creare un certificato SSL
description: Istruzioni alternative per creare certificati manualmente per il server di sviluppo
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: c96489e6577f4887d2f22a9e81ea50f46cc9a5a3
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194429"
---
# <a name="create-an-ssl-certificate"></a>Creare un certificato SSL

Questo articolo descrive come creare un certificato SSL.

Per generare il certificato usando il cmdlet `New-SelfSignedCertificate` di PowerShell in Windows 8 o versione successiva, eseguire il comando seguente:

```cmd
pbiviz --create-cert
```

Lo strumento richiede un'installazione di OpenSSL per Windows 7. L'utilità OpenSSL deve essere disponibile dalla riga di comando.

Per installare OpenSSL, passare al sito di [OpenSSL](https://www.openssl.org) o [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) (Distribuzioni binarie di OpenSSL).



## <a name="create-a-certificate-mac-os-x"></a>Creare un certificato (Mac OS X)

L'utilità OpenSSL è in genere disponibile nel sistema operativo Linux o Mac OS X.

È anche possibile installare l'utilità eseguendo uno dei due comandi seguenti:
* Dall'utilità di gestione pacchetti *Brew*:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* Usando *MacPorts*:

    ```cmd
    sudo port install openssl
    ```

Dopo aver installato l'utilità OpenSSL per generare un nuovo certificato, eseguire il comando seguente:

```cmd
pbiviz --create-cert
```

## <a name="create-a-certificate-linux"></a>Creare un certificato (Linux)

Se l'utilità OpenSSL non è disponibile nel sistema operativo Linux, è possibile l'installarla usando uno dei comandi seguenti:

* Per la gestione pacchetti *APT*:

    ```cmd
    sudo apt-get install openssl
    ```

* Per *Yellowdog Updater*:

    ```cmd
    yum install openssl
    ```

* Per *Redhat Package Manager*:

    ```cmd
    rpm install openssl
    ```

Se l'utilità OpenSSL è già disponibile nel sistema operativo, generare un nuovo certificato eseguendo il comando seguente:

```cmd
pbiviz --create-cert
```

Per ottenere l'utilità OpenSSL, è anche possibile passare al sito di [OpenSSL](https://www.openssl.org) o [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) (Distribuzioni binarie di OpenSSL).

## <a name="generate-the-certificate-manually"></a>Generare manualmente il certificato

È possibile specificare che i certificati vengano generati da qualsiasi strumento.

Se l'utilità OpenSSL è già installata nel sistema, generare un nuovo certificato eseguendo i comandi seguenti:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

In genere è possibile trovare i certificati del server Web PowerBI-visuals-tools eseguendo uno dei comandi seguenti:

* Per l'istanza globale degli strumenti:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Per l'istanza locale degli strumenti:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Se si usa il formato PEM, salvare il file del certificato come *PowerBICustomVisualTest_public.crt* e salvare privateKey come *PowerBICustomVisualTest_public.key*.

Se si usa il formato PFX, salvare il file del certificato come *PowerBICustomVisualTest_public.pfx*.

Se il file del certificato PFX richiede una passphrase, eseguire le operazioni seguenti:
1. Nel file di configurazione specificare:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. Nella sezione `server` specificare la passphrase sostituendo il segnaposto "*YOUR PASSPHRASE*":

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```
