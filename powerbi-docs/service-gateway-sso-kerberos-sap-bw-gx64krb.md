---
title: Usare Kerberos per il Single Sign-On (SSO) a SAP BW tramite gx64krb5
description: Configurare il server SAP BW per abilitare SSO dal servizio Power BI usando gx64krb5
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5dd31dc4333dc03100370100e16eadab6012c1f0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106332"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Usare Kerberos per il Single Sign-On (SSO) a SAP BW tramite gx64krb5

Questo articolo descrive come configurare il server SAP BW per abilitare SSO dal servizio Power BI usando gx64krb5.

> [!NOTE]
> È possibile completare i passaggi descritti in questo articolo oltre a quelli descritti in [Configurare SSO - Kerberos](service-gateway-sso-kerberos.md) per abilitare l'aggiornamento per i report basati sul server applicazioni SAP BW che usano il Single Sign-On Kerberos nel servizio Power BI. Tuttavia, Microsoft consiglia di usare CommonCryptoLib come libreria SNC. SAP non offre più il supporto per gx64krb5 e i passaggi necessari per configurarlo per l'uso con il gateway sono molto più complessi rispetto a CommonCryptoLib. Vedere [Configurare SAP BW per l'accesso SSO tramite CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) per informazioni sulla configurazione di SSO tramite CommonCryptoLib. Completare la configurazione per CommonCryptoLib _o_ gx64krb5. Non completare i passaggi di configurazione per entrambe le librerie.

### <a name="set-up-gx64krb5gsskrb5-on-gateway-machine-and-the-sap-bw-server"></a>Configurare gx64krb5/gsskrb5 nel computer gateway e nel server SAP BW

> [!NOTE]
> `gx64krb5` e `gsskrb5` non sono più supportate attivamente da SAP. Per altre informazioni, vedere [Nota SAP 352295](https://launchpad.support.sap.com/#/notes/352295). Si noti anche che `gx64krb5` non consente connessioni SSO tra il gateway dati e i server messaggi SAP BW. Sono possibili solo connessioni a server applicazioni SAP BW. La restrizione relativa ai soli server applicazioni non esiste se si usa [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) come libreria SNC. Per il Single Sign-On a BW potrebbero funzionare anche altre librerie SNC, ma queste non sono ufficialmente supportate da Microsoft.

Per completare una connessione SSO tramite il gateway, è necessario che `gx64krb5` \ `gsskrb5` siano in uso sia nel client che nel server, ovvero il client e il server devono usare la stessa libreria SNC.

1. Scaricare `gx64krb5` dalla [nota SAP 2115486](https://launchpad.support.sap.com/) (è necessario il nome utente SAP). Assicurarsi di aver installato la versione 1.0.11. x o successive. Scaricare anche `gsskrb5` (la versione a 32 bit della libreria) se si vuole testare la connessione SSO nell'interfaccia utente grafica SAP prima di tentare la connessione SSO tramite il gateway (scelta consigliata). La versione a 32 bit è necessaria per il test con l'interfaccia utente grafica SAP poiché quest'ultima è disponibile solo nella versione a 32 bit.

1. Inserire `gx64krb5` in un percorso del computer gateway che sia accessibile all'utente del servizio gateway (e anche all'interfaccia utente grafica SAP, se si vuole testare la connessione SSO usando SAP Logon). Sia l'utente del servizio gateway che gli utenti Active Directory (AD) che l'utente del servizio rappresenterà necessitano delle autorizzazioni di lettura ed esecuzione per il file con estensione dll. È consigliabile concedere al gruppo Authenticated Users le autorizzazioni per il file con estensione dll. A scopo di test, è anche possibile concedere queste autorizzazioni in modo esplicito all'utente del servizio gateway e all'utente Active Directory che verranno usati per il test.

1. Se il server BW non è ancora stato configurato per SSO usando gx64krb5/gsskrb5, inserire un'altra copia nel computer server SAP BW in un percorso accessibile al server SAP BW. 

1. Nei computer client e server, impostare le variabili di ambiente `SNC_LIB` o `SNC_LIB_64`. Se si usa gsskrb5, impostare la variabile `SNC_LIB` sul percorso assoluto di gsskrb5.dll. Se si usa gx64krb5, impostare la variabile `SNC_LIB_64` sul percorso assoluto di gx64krb5.dll.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication"></a>Configurare un utente del servizio SAP BW e abilitare la comunicazione SNC

Completare questa sezione se il server SAP BW non è ancora stato configurato per la comunicazione SNC, ad esempio l'accesso SSO, usando gx64krb5/gsskrb5.

> [!NOTE]
> Questa sezione presuppone che sia già stato creato un utente del servizio per BW e che a questo sia stato associato un nome dell'entità servizio appropriato (ad esempio, un nome che inizia con `SAP/`).

1. Assegnare all'utente del servizio l'accesso al server applicazioni SAP BW:

    1. Nel computer server SAP BW aggiungere l'utente del servizio al gruppo degli amministratori locali. Aprire il programma Gestione computer e fare doppio clic sul gruppo degli amministratori locali per il server.

        ![Screenshot del programma Gestione computer](media/service-gateway-sso-kerberos/computer-management.png)

    1. Fare doppio clic sul gruppo degli amministratori locali e selezionare **Aggiungi** per aggiungere l'utente del servizio al gruppo. Selezionare **Controlla nomi** per assicurarsi di aver immesso il nome correttamente. Selezionare **OK**.

1. Impostare l'utente del servizio del server SAP BW come l'utente che avvia il servizio del server SAP BW nel computer server SAP BW.

    1. Aprire **Esegui** e immettere "Services.msc". Cercare il servizio corrispondente all'istanza del server applicazioni SAP BW. Fare clic con il pulsante destro del mouse sul servizio e selezionare **Proprietà**.

        ![Screenshot di Servizi con il comando Proprietà evidenziato](media/service-gateway-sso-kerberos/server-properties.png)

    1. Passare alla scheda **Accedi** e sostituire l'utente con l'utente del servizio SAP BW. Immettere la password dell'utente e selezionare **OK**.

1. Accedere al server da SAP Logon e impostare i parametri di profilo seguenti usando la transazione RZ10:

    1. Impostare il parametro di profilo snc/identity/as su p:\<utente del servizio SAP BW creato\>, ad esempio p:BWServiceUser@MYDOMAIN.COM. Si noti il parametro p: che precede l'UPN dell'utente del servizio. Non è p:CN=, come avviene quando la libreria di crittografia comune viene usata come libreria SNC.

    1. Impostare il parametro di profilo snc/gssapi\_lib su \<percorso di gsskrb5.dll/gx64krb5.dll nel computer server BW (la libreria usata varia a seconda del numero di bit del sistema operativo)\>. Si ricordi di inserire la libreria in un percorso accessibile al server applicazioni SAP BW.

    1. Impostare anche i parametri di profilo seguenti, modificando i valori in base alle proprie esigenze. Si noti che le ultime cinque opzioni consentono ai client di connettersi al server SAP BW usando SAP Logon senza aver configurato il nome SNC.

        | **Impostazione** | **Valore** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Impostare la proprietà snc/enable su 1.

1. Dopo aver impostato i parametri di profilo, aprire la console di gestione SAP nel computer server e riavviare l'istanza di SAP BW. Se il server non si avvia, verificare di aver impostato i parametri di profilo in modo corretto. Per altre informazioni sulle impostazioni dei parametri di profilo, vedere la [documentazione di SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Se si verificano problemi, è anche possibile fare riferimento alle informazioni sulla risoluzione dei problemi più avanti in questa sezione.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Eseguire il mapping di un utente SAP BW a un utente di Active Directory

Se non è ancora stato fatto, mappare un utente Active Directory a un utente del server applicazioni SAP BW e testare la connessione SSO in SAP Logon.

1. Accedere al server SAP BW tramite SAP Logon. Eseguire la transazione SU01.

1. Per **User** (Utente) immettere l'utente SAP BW per cui si vogliono abilitare le connessioni SSO (nello screenshot seguente vengono impostate le autorizzazioni per BIUSER). Selezionare l'icona di **modifica** (immagine di una penna) nella parte superiore sinistra della finestra di SAP Logon.

    ![Screenshot della schermata User Maintenance (Gestione utenti) di SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selezionare la scheda **SNC**. Nella casella di input del nome SNC immettere p:\<utente Active Directory\>@\<dominio\>. Si noti che è obbligatorio specificare p: all'inizio dell'UPN dell'utente di Active Directory. L'utente di Active Directory specificato deve appartenere alla persona o all'organizzazione per cui si vuole abilitare l'accesso SSO per il server applicazioni SAP BW. Ad esempio, se si vuole abilitare l'accesso SSO per l'utente testuser\@TESTDOMAIN.COM, immettere p:testuser@TESTDOMAIN.COM.

    ![Screenshot della schermata Maintain Users (Gestisci utenti) di SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Selezionare l'icona di **salvataggio** (immagine di un disco floppy) nella parte superiore sinistra della schermata.

### <a name="test-sign-in-by-using-sso"></a>Testare l'accesso con SSO

Verificare che l'utente di Active Directory per il quale è stato appena abilitato l'accesso SSO possa accedere al server usando SAP Logon tramite SSO.

1. Con l'account dell'utente di Active Directory per cui è stato appena abilitato l'accesso SSO accedere a un computer in cui è installato SAP Logon. Avviare SAP Logon e creare una nuova connessione.

1. Nella schermata **Create New System Entry** (Crea nuova voce di sistema) selezionare **User Specified System** (Sistema specificato dall'utente) > **Next** (Avanti).

    ![Screenshot della schermata Create New System Entry (Crea nuova voce di sistema)](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Specificare i dettagli appropriati nella schermata successiva, inclusi il server applicazioni, il numero di istanza e l'ID sistema, e quindi fare clic su **Finish** (Fine).

1. Fare clic con il pulsante destro del mouse sulla nuova connessione e selezionare **Properties** (Proprietà). Selezionare la scheda **Network** (Rete). Nella casella di testo **SNC Name** (Nome SNC) immettere p:\<UPN utente servizio SAP BW\>, ad esempio p:BWServiceUser@MYDOMAIN.COM. Selezionare quindi **OK**.

    ![Screenshot della schermata System Entry Properties (Proprietà voce sistema)](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Fare doppio clic sulla connessione creata per tentare una connessione SSO al server SAP BW. Se la connessione viene stabilita, procedere al passaggio successivo. In caso contrario, rivedere i passaggi precedenti di questo documento per assicurarsi che siano stati eseguiti correttamente o rivedere la sezione sulla risoluzione dei problemi che segue. Si noti che se non è possibile connettersi al server SAP BW tramite SSO in questo contesto, non sarà possibile connettersi al server SAP BW tramite SSO nel contesto del gateway.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Aggiungere voci del Registro di sistema nel computer gateway

Aggiungere le voci del Registro di sistema necessarie al Registro di sistema del computer in cui è installato il gateway, oltre che nei computer a cui si intende connettersi da Power BI Desktop. Ecco i comandi da eseguire:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Aggiungere una nuova origine dati del server applicazioni SAP BW al servizio Power BI oppure modificarne una esistente

1. Nella finestra di configurazione dell'origine dati immettere **Nome host**, **Numero sistema** e **ID client** del server applicazioni per accedere al server SAP BW da Power BI Desktop.

1. Nel campo **Nome del partner SNC** immettere p: \<nome SPN mappato all'utente del servizio SAP BW\>. Ad esempio, se il nome SNC è SAP/BWServiceUser@MYDOMAIN.COM, immettere p:SAP/BWServiceUser@MYDOMAIN.COM nel campo **Nome del partner SNC**.

1. Per la libreria SNC, selezionare **SNC_LIB** o **SNC_LIB_64**. Verificare che SNC_LIB_64 nel computer gateway punti a gx64krb5.dll. In alternativa, è possibile selezionare l'opzione "Personalizzata" e specificare il percorso assoluto di gx64krb5.dll (nel computer gateway).

1. Selezionare la casella **Usa SSO tramite Kerberos per le query DirectQuery** e selezionare **Applica**. Se la connessione di test ha esito negativo, verificare di aver eseguito correttamente i passaggi di installazione e configurazione descritti in precedenza.

1. [Eseguire un report di Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="troubleshoot-gx64krb5gsskrb5-configuration"></a>Risolvere i problemi di configurazione di gx64krb5/gsskrb5

In caso di problemi di installazione di gx64krb5/gsskrb5 e delle connessioni SSO da SAP Logon, seguire questa procedura per risolverli.

* La visualizzazione dei log del server (…work\dev\_w0 nel computer server) può essere utile per risolvere eventuali errori che si verificano durante l'esecuzione dei passaggi di configurazione di gx64krb5/gsskrb5. in particolare se il server SAP BW non si avvia dopo che i parametri di profilo sono stati cambiati.

* Se non è possibile avviare il servizio SAP BW a causa di un errore di accesso, è possibile che sia stata specificata una password errata durante l'impostazione dell'utente di avvio SAP BW. Verificare la password accedendo a un computer nell'ambiente Active Directory come utente del servizio SAP BW.

* Se si verificano errori relativi alle credenziali SQL che impediscono l'avvio del server, verificare di aver assegnato all'utente del servizio l'accesso al database SAP BW.

* Può essere visualizzato il messaggio seguente: "(GSS-API) specified target is unknown or unreachable" ((GSS-API) destinazione specificata sconosciuta o non raggiungibile). Questo in genere significa che è stato specificato un nome SNC errato. Assicurarsi di usare solo "p:", non "p:CN=" o altri parametri nell'applicazione client diversi dall'UPN dell'utente del servizio.

* Può essere visualizzato il messaggio seguente: "(GSS-API) An invalid name was supplied" ((GSS-API) È stato specificato un nome non valido). Assicurarsi di aver incluso "p:" nel valore del parametro di profilo dell'identità SNC del server.

* Può essere visualizzato il messaggio seguente: "(SNC error) the specified module could not be found" ((Errore SNC) impossibile trovare il modulo specificato). Questo errore è in genere causato dall'inserimento di `gsskrb5.dll/gx64krb5.dll` in una posizione il cui accesso richiede privilegi elevati (diritti di amministratore).

### <a name="troubleshoot-gateway-connectivity-issues"></a>Risolvere i problemi di connettività del gateway

1. Controllare i registri del gateway. Aprire l'applicazione di configurazione del gateway e selezionare **Diagnostica** > **Esporta log**. Gli errori più recenti sono indicati nella parte inferiore dei file di log.

    ![Screenshot dell'applicazione Gateway dati locale, con la voce Diagnostica evidenziata](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Attivare la traccia SAP BW e rivedere i file di log generati. Sono disponibili diversi tipi di traccia SAP BW. Per altre informazioni, consultare la documentazione di SAP.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sul **gateway dati locale** e su **DirectQuery**, vedere le risorse seguenti:

* [Informazioni sul gateway dati locale](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
