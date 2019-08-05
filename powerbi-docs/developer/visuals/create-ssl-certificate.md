---
title: Creazione del certificato SSL
description: Istruzioni alternative per creare certificati manualmente per il server di sviluppo
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425437"
---
# <a name="creating-ssl-certificate"></a>Creazione del certificato SSL

Eseguire il comando seguente per generare il certificato usando il cmdlet New-SelfSignedCertificate di PowerShell in Windows 8 o versione successiva.

Lo strumento richiede l'installazione di OpenSSL per **Windows** **7**. L'utilità `openssll` deve essere disponibile dalla riga di comando.

Per installare OpenSSL, visitare il sito Web all'indirizzo [https://www.openssl.org](https://www.openssl.org) o [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Creare il certificato (Mac OS X)

In genere le utilità OpenSSL sono disponibili nel sistema operativo Linux o Mac OS X.

In caso contrario, possono essere installate da

Gestione pacchetti *Brew*

```cmd
brew install openssl
brew link openssl --force
```

Oppure usando *MacPorts*

```cmd
sudo port install openssl
```

Dopo l'installazione di OpenSSL, per generare la chiamata del nuovo certificato:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Creare il certificato (Linux)

Se le utilità OpenSSL non sono disponibili nel sistema operativo Linux, è possibile eseguire l'installazione usando i comandi seguenti.

Per la gestione pacchetti *APT*:

```cmd
sudo apt-get install openssl
```

Per *Yellowdog Updater*:

```cmd
yum install openssl
```

Per *Redhat Package Manager*:

```cmd
rpm install openssl
```

Se OpenSSL è già disponibile nel sistema operativo, chiamare

```cmd
pbiviz --create-cert
```

Per generare il nuovo certificato.

In alternativa, ottenere OpenSSL da [https://www.openssl.org](https://www.openssl.org) o [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

## <a name="generate-certificate-manually"></a>Generare manualmente il certificato

È possibile specificare i certificati generati da qualsiasi strumento.

Se nel sistema è installato OpenSSL, è possibile eseguire il comando seguente per generare un nuovo certificato

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

In genere i certificati del server PowerBI-visuals-tools si trovano in

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

Per l'istanza globale degli strumenti

oppure

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

Per l'istanza locale degli strumenti.

È consigliabile salvare il file di certificato come `PowerBICustomVisualTest_public.cer` e privatekey come `PowerBICustomVisualTest_public.key` se si usa il formato PEM.
Salvare il file di certificato come `PowerBICustomVisualTest_public.pfx` se si usa il formato PFX.

Se il file di certificato PFX richiede una passphrase, è necessario specificarla in

```cmd
\PowerBI-visuals-tools\config.json
```

Nella sezione server:

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
