---
title: Usare il Single Sign-On Kerberos per l'accesso SSO a SAP BW tramite CommonCryptoLib (sapcrypto.dll)
description: Configurare il server SAP BW per abilitare il Single Sign-On dal servizio Power BI usando CommonCryptoLib (sapcrypto.dll)
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c4f2b0d8856d5e68e02b9b33cf393ca85ecb580
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106286"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Usare il Single Sign-On Kerberos per l'accesso SSO a SAP BW tramite CommonCryptoLib (sapcrypto.dll)

Questo articolo descrive come configurare il server SAP BW per abilitare il Single Sign-On dal servizio Power BI usando CommonCryptoLib (sapcrypto.dll).

> [!NOTE]
> Completare i passaggi descritti in questo articolo oltre a quelli descritti in [Configurare SSO - Kerberos](service-gateway-sso-kerberos.md) prima di provare ad aggiornare un report basato su SAP BW che usa il Single Sign-On Kerberos. L'uso di CommonCryptoLib come libreria SNC abilita le connessioni SSO ai server applicazioni SAP BW e ai server messaggi SAP BW.

## <a name="configure-sap-bw-server-to-enable-sso-using-commoncryptolib"></a>Configurare il server SAP BW per abilitare SSO usando CommonCryptoLib

> [!NOTE]
> Il gateway dati locale è un software a 64 bit e richiede quindi la versione a 64 bit di CommonCryptoLib (sapcrypto.dll). Se si prevede di testare la connessione SSO al server SAP BW nell'interfaccia utente grafica SAP prima di tentare una connessione SSO tramite il gateway (scelta consigliata), sarà necessaria anche la versione a 32 bit di CommonCryptoLib poiché l'interfaccia utente grafica SAP è un software a 32 bit.

1. Verificare che il server BW sia configurato correttamente per il Single Sign-On Kerberos usando CommonCryptoLib. In caso affermativo, dovrebbe essere possibile usare SSO per accedere al server BW, direttamente o tramite un server messaggi SAP BW, con uno strumento SAP quale l'interfaccia utente grafica SAP configurata per l'uso di CommonCryptoLib. Per altre informazioni sui passaggi di configurazione, vedere [Single Sign-On SAP: Eseguire l'autenticazione con Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). Il server BW deve usare CommonCryptoLib come libreria SNC e avere un nome SNC che inizia con "CN =", ad esempio "CN = BW1". Per altre informazioni sui requisiti dei nomi SNC, vedere [Parametri SNC per la configurazione Kerberos](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (in particolare, il parametro snc/identity/as).

1. Se non è già stato fatto, installare la versione x64 del [connettore SAP .NET](https://support.sap.com/en/product/connectors/msnet.html) nel computer in cui è stato installato il gateway. È possibile verificare se il componente è stato installato provando a connettersi al server BW in Power BI Desktop. Se non è possibile connettersi usando l'implementazione 2.0, il connettore .NET non è installato.

1. Verificare che SAP Secure Login Client (SLC) non sia in esecuzione nel computer in cui è installato il gateway. SLC memorizza nella cache i ticket Kerberos in un modo che può interferire con la capacità del gateway di usare Kerberos per l'accesso SSO. Se SLC è installato, disinstallarlo o assicurarsi di chiudere SAP Secure Login Client facendo clic con il pulsante destro del mouse sull'icona nell'area di notifica e selezionando il comando di disconnessione e chiusura prima di provare a stabilire una connessione SSO tramite il gateway. SLC non è supportato per l'uso nei computer Windows Server. Per altre informazioni, vedere la [nota SAP 2780475](https://launchpad.support.sap.com/#/notes/2780475) (è necessario un account utente SAP).

    ![SAP Secure Login Client](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Se si disinstalla SLC o si seleziona **Log Out** (Disconnetti) ed **Exit** (Esci), aprire una finestra di comando e immettere `klist purge` per cancellare eventuali ticket Kerberos memorizzati nella cache prima di provare a stabilire una connessione SSO tramite il gateway.

1. Scaricare la versione a 64 bit di CommonCryptoLib (sapcrypto.dll) **8.5.25 o successiva** da SAP Launchpad e copiarla in una cartella del computer gateway. Nella stessa directory in cui è stato copiato il file sapcrypto.dll, creare un file denominato sapcrypto.ini con il contenuto seguente:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    Il file INI contiene le informazioni di configurazione richieste da CommonCryptoLib per abilitare l'accesso SSO nello scenario del gateway.

    > [!NOTE]
    > Questi file devono essere archiviati nello stesso percorso. In altre parole, _/path/to/sapcrypto/_ deve contenere sia sapcrypto.ini che sapcrypto.dll.

    Sia l'utente del servizio gateway che l'utente Active Directory (AD) che verrà rappresentato dall'utente del servizio necessitano delle autorizzazioni di lettura ed esecuzione per entrambi i file. È consigliabile concedere al gruppo Authenticated Users le autorizzazioni per entrambi i file con estensione ini e dll. A scopo di test, è anche possibile concedere queste autorizzazioni in modo esplicito all'utente del servizio gateway e all'utente Active Directory che verranno usati per il test. Nello screenshot seguente sono state concesse al gruppo Authenticated Users le autorizzazioni **Lettura ed esecuzione** per sapcrypto.dll:

    ![Utenti autenticati](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Se non si ha un'origine dati SAP BW, nella pagina **Gestisci gateway** del servizio Power BI aggiungere un'origine dati. Se si ha già un'origine dati BW associata al gateway in cui si vuole usare la connessione SSO, prepararsi a modificarla. Scegliere **SAP Business Warehouse** come **Tipo di origine dati** se si vuole creare una connessione SSO a un server applicazioni BW. Selezionare **Server messaggi SAP Business Warehouse** se si vuole creare una connessione SSO a un server messaggi BW.

    Per **Libreria SNC**, selezionare **Variabile di ambiente SNC\_LIB o SNC\_LIB\_64** oppure **Personalizzata**. Se si seleziona l'opzione **SNC\_LIB**, è necessario impostare il valore della variabile di ambiente **SNC\_LIB\_64** nel computer gateway sul percorso assoluto della copia a 64 bit di sapcrypto.dll presente nel computer gateway, ad esempio C:\Utenti\Test\Desktop\sapcrypto.dll. Se si sceglie **Personalizzata**, incollare il percorso assoluto di sapcrypto.dll nel campo Percorso libreria SNC personalizzato visualizzato nella pagina **Gestisci gateway**. Per **Nome del partner SNC**, immettere il nome SNC del server BW. In **Impostazioni avanzate** verificare che l'opzione **Usa SSO tramite Kerberos per le query DirectQuery** sia selezionata. Gli altri campi devono essere compilati come se si stesse stabilendo una connessione con autenticazione di Windows da PBI Desktop.

1. Creare una variabile di ambiente di sistema CCL\_PROFILE che punti a sapcrypto.ini:

    ![Variabile di ambiente di sistema CCL\_PROFILE](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Tenere presente che i file sapcrypto.dll e sapcrypto.ini devono trovarsi nello stesso percorso. Nell'esempio illustrato in precedenza in cui sapcrypto.ini si trova sul desktop, anche sapcrypto.dll deve trovarsi sul desktop.

1. Riavviare il servizio gateway:

    ![Riavviare il servizio gateway](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Eseguire un report di Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se non è possibile aggiornare il report nel servizio Power BI, è possibile usare le funzionalità di traccia di gateway, CPIC e CommonCryptoLib per agevolare la diagnosi del problema. Le soluzioni di traccia di CPIC e CommonCryptoLib sono prodotti SAP, quindi Microsoft non può fornire supporto diretto. Per gli utenti Active Directory a cui verrà concesso l'accesso SSO a BW, alcune configurazioni di Active Directory possono richiedere che gli utenti siano membri del gruppo Administrators nel computer in cui è installato il gateway.

1. **Log del gateway:** riprodurre semplicemente il problema, aprire l'[app gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), passare alla scheda **Diagnostica** e selezionare **Esporta log**:

    ![Esportare i log del gateway](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **Traccia di CPIC:** per abilitare la traccia di CPIC, impostare due variabili di ambiente: CPIC\_TRACE e CPIC\_TRACE\_DIR. La prima variabile imposta il livello di traccia e la seconda variabile imposta la directory dei file di traccia. La directory deve essere un percorso in cui i membri del gruppo Authenticated Users possono scrivere. Impostare CPIC\_TRACE su 3 e CPIC\_TRACE\_DIR sulla directory in cui si vuole che vengano scritti i file di traccia.

    ![Traccia di CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Riprodurre il problema e verificare che CPIC\_TRACE\_DIR contenga i file di traccia.

1. **Traccia di CommonCryptoLib:** attivare la traccia di CommonCryptoLib aggiungendo due righe al file sapcrypto.ini creato in precedenza:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    Assicurarsi di modificare l'opzione _ccl/trace/directory_ scegliendo un percorso in cui i membri del gruppo Authenticated Users possono scrivere. In alternativa, creare un nuovo file INI per modificare questo comportamento. Nella stessa directory di sapcrypto.ini e sapcrypto.dll creare un file denominato sectrace.ini con il contenuto riportato di seguito. Sostituire l'opzione DIRECTORY con un percorso nel computer in cui l'utente autenticato può scrivere:

    ```
    LEVEL = 5

    DIRECTORY = <drive>:\logs\sectrace
    ```

    Riprodurre ora il problema e verificare che il percorso a cui punta DIRECTORY contenga i file di traccia. Al termine, assicurarsi di disattivare la traccia di CPIC e CCL.

    Per altre informazioni sulla traccia di CommonCryptoLib, vedere la [nota SAP 2491573](https://launchpad.support.sap.com/#/notes/2491573) (è necessario un account utente SAP).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sul **gateway dati locale** e su **DirectQuery**, vedere le risorse seguenti:

* [Informazioni sul gateway dati locale](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
