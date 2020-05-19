---
title: Creare certificati SSL per gli oggetti visivi di Power BI
description: Informazioni su come generare certificati SSL usando gli strumenti per oggetti visivi di Power BI in Windows, Mac o Linux oppure manualmente.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 37bd8f15dcf17cd0f967e819338a719edf2a3054
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276376"
---
# <a name="create-an-ssl-certificate"></a>Creare un certificato SSL

Questo articolo descrive come generare e installare certificati SSL (Secure Sockets Layer) per gli oggetti visivi di Power BI.

Per le procedure di Windows, macOS X e Linux è necessario che sia installato il pacchetto **pbiviz** degli strumenti per oggetti visivi Power BI. Per altre informazioni, vedere [Configurazione dell'ambiente di sviluppo](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Creare un certificato in Windows

Per generare un certificato usando il cmdlet `New-SelfSignedCertificate` di PowerShell in Windows 8 o versione successiva, eseguire il comando seguente:

```powershell
pbiviz --install-cert
```

Per Windows 7, lo strumento `pbiviz` richiede che l'utilità OpenSSL sia disponibile dalla riga di comando. Per installare OpenSSL, passare a [OpenSSL](https://www.openssl.org) o a [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) (Distribuzioni binarie di OpenSSL).

Per altre informazioni e istruzioni per l'installazione di un certificato, vedere [Creare e installare un certificato per Windows](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#windows).

## <a name="create-a-certificate-on-macos-x"></a>Creare un certificato in macOS X

L'utilità OpenSSL è in genere disponibile nel sistema operativo macOS X.

È anche possibile installare l'utilità OpenSSL eseguendo uno dei due comandi seguenti:

- Dall'utilità di gestione pacchetti *Brew*:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Usando *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

Dopo aver installato l'utilità OpenSSL eseguire il comando seguente per generare un nuovo certificato:

```cmd
pbiviz --install-cert
```

Per altre informazioni e istruzioni, vedere [Creare e installare un certificato per OS X](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#osx).

## <a name="create-a-certificate-on-linux"></a>Creare un certificato in Linux

L'utilità OpenSSL è in genere disponibile nel sistema operativo Linux.

Prima di iniziare, eseguire i comandi seguenti per assicurarsi che `openssl` e `certutil` siano installate:

```sh
which openssl
which certutil
```

Se `openssl` e `certutil` non sono installate, installare le utilità `openssl` e `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Creare il file di configurazione SSL

Creare un file */tmp/openssl.cnf* che include il testo seguente:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Generare l'autorità di certificazione radice

Per generare l'autorità di certificazione radice (CA) per la firma dei certificati locali, eseguire i comandi seguenti:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Generare un certificato per localhost 

Per generare un certificato per `localhost` usando la CA generata e *openssl.cnf*, eseguire i comandi seguenti:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Aggiungere certificati radice

Per aggiungere un certificato radice al database del browser Chrome, eseguire:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Per aggiungere un certificato radice al database del browser Mozilla, eseguire:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Per aggiungere un certificato radice a livello di sistema, eseguire:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Rimuovere i certificati radice

Per rimuovere un certificato radice, eseguire:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Generare manualmente un certificato

È anche possibile generare manualmente un certificato SSL usando OpenSSL. È possibile specificare qualsiasi strumento per generare i certificati.

Se l'utilità OpenSSL è già installata, generare un nuovo certificato eseguendo:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

In genere è possibile trovare i certificati del server Web `PowerBI-visuals-tools` eseguendo uno dei comandi seguenti:

- Per l'istanza globale degli strumenti:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Per l'istanza locale degli strumenti:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>Formato PEM

Se si usa il formato di certificato Privacy Enhanced Mail (PEM), salvare il file del certificato con nome *PowerBIVisualTest_public.crt* e salvare la chiave privata con nome *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>Formato PFX

Se si usa il formato di certificato Personal Information Exchange (PFX), salvare il file del certificato con nome *PowerBIVisualTest_public.pfx*.

Se il file del certificato PFX richiede una passphrase:

1. Nel file di configurazione specificare:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. Nella sezione `server` specificare la passphrase sostituendo il segnaposto \<YOUR PASSPHRASE>:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Passaggi successivi
- [Sviluppare un oggetto visivo di Power BI](custom-visual-develop-tutorial.md)
- [Esempi di oggetti visivi Power BI](samples.md)
- [Pubblicare un oggetto visivo di Power BI in AppSource](office-store.md)
