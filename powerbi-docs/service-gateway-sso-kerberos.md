---
title: Usare Kerberos per l'accesso Single Sign-On (SSO) alle origini dati locali
description: Configurare il gateway con Kerberos per abilitare l'accesso Single Sign-On da Power BI alle origini dati locali
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: d8cebda3ad0db9fba48804fb8d2dd029c1c07f8d
ms.sourcegitcommit: aef57ff94a5d452d6b54a90598bd6a0dd1299a46
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66809271"
---
# <a name="use-kerberos-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Usare Kerberos per l'accesso Single Sign-On (SSO) da Power BI alle origini dati locali

Usare la [delega vincolata Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) per abilitare la connettività Single Sign-On (SSO). L'abilitazione di SSO rende più semplice per i report e i dashboard di Power BI aggiornare i dati delle origini locali.

## <a name="supported-data-sources"></a>Origini dati supportate

Sono attualmente supportate le origini dati seguenti:

* SQL Server
* SAP HANA
* SAP BW
* Teradata
* Spark
* Impala

È supportato anche SAP HANA con [Security Assertion Markup Language (SAML)](service-gateway-sso-saml.md).

### <a name="sap-hana"></a>SAP HANA

Per abilitare SSO per SAP HANA, seguire innanzitutto questa procedura:

* Verificare che nel server SAP HANA sia in esecuzione la versione minima richiesta. Ciò dipende dal livello della piattaforma del server SAP HANA:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Nel computer gateway installare il driver ODBC per HANA più recente di SAP.  La versione minima è la versione ODBC per HANA 2.00.020.00 di agosto 2017.

Per altre informazioni sulla configurazione della funzionalità SSO per SAP HANA con Kerberos, vedere [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Single Sign-on tramite Kerberos) nella guida alla sicurezza di SAP HANA. Vedere anche i collegamenti in tale pagina, in particolare SAP Note 1837331 - HOWTO HANA DBSSO Kerberos/Active Directory.

## <a name="prepare-for-kerberos-constrained-delegation"></a>Preparare la delega vincolata Kerberos

Per il corretto funzionamento della delega vincolata Kerberos, è necessario configurare diversi elementi, ad esempio i *nomi delle entità servizio* e le impostazioni di delega negli account del servizio.

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>Prerequisito 1: installare e configurare il gateway dati locale

Questa versione del gateway dati locale supporta un aggiornamento sul posto, nonché l'acquisizione della proprietà delle impostazioni dei gateway esistenti.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Prerequisito 2: eseguire il servizio di Windows gateway come account di dominio

In un'installazione standard, il gateway viene eseguito come account del servizio locale del computer, ovvero *NT Service\PBIEgwService*.

![Screenshot dell'account del servizio](media/service-gateway-sso-kerberos/service-account.png)

Per abilitare la delega vincolata Kerberos, il gateway deve essere eseguito come account di dominio, a meno che l'istanza di Azure Active Directory (Azure AD) non sia già sincronizzata con l'istanza di Active Directory locale tramite Azure AD DirSync/Connect. Per passare a un account di dominio, vedere [Modificare l'account del servizio gateway in un account di dominio](#switch-the-gateway-to-a-domain-account) più avanti in questo articolo.

> [!NOTE]
> Se Azure AD Connect è configurato e gli account utente sono sincronizzati, il servizio gateway non deve eseguire ricerche locali in AD in fase di esecuzione. Per il servizio gateway è possibile usare il SID del servizio locale, anziché un account di dominio. La procedura di configurazione della delega vincolata Kerberos descritta in questo articolo corrisponde a questa configurazione, che viene semplicemente applicata all'oggetto computer del gateway anziché all'account di dominio.

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Prerequisito 3: ottenere i diritti di amministratore di dominio per configurare i nomi delle entità servizio (SetSPN) e le impostazioni di delega vincolata Kerberos

Non è consigliabile per un amministratore di dominio concedere temporaneamente o definitivamente a un altro utente i diritti per configurare i nomi delle entità servizio e la delega vincolata senza richiedere diritti di amministratore di dominio. Nella sezione seguente viene illustrata in modo più dettagliato la procedura di configurazione consigliata.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Configurare la delega vincolata Kerberos per il gateway e l'origine dati

Con un account amministratore di dominio configurare un nome dell'entità servizio (SPN) per l'account di dominio del servizio gateway e configurare le impostazioni di delega nell'account di dominio del servizio gateway.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Configurare un nome dell'entità servizio per l'account del servizio gateway

Determinare prima se è già stato creato un nome dell'entità servizio per l'account di dominio usato come account del servizio gateway:

1. Con un account amministratore di dominio aprire **Utenti e computer di Active Directory**.

2. Fare clic con il pulsante destro del mouse sul dominio, selezionare **Trova** e immettere il nome dell'account del servizio gateway.

3. Nei risultati della ricerca fare clic con il pulsante destro del mouse sull'account del servizio gateway e selezionare **Proprietà**.

4. Se la scheda **Delega** è visibile nella finestra di dialogo **Proprietà**, è già stato creato un nome SPN ed è possibile passare direttamente alla configurazione delle impostazioni di delega.

    Se non è presente alcuna scheda **Delega** nella finestra di dialogo **Proprietà**, è possibile creare manualmente un nome SPN per l'account. Questa operazione aggiunge la scheda **Delega**. Usare lo [strumento setspn](https://technet.microsoft.com/library/cc731241.aspx) incluso in Windows. Per creare il nome SPN sono necessari diritti di amministratore di dominio.

    Ad esempio, si supponga che l'account del servizio gateway sia "PBIEgwTest\GatewaySvc" e il nome computer in cui è in esecuzione il servizio gateway sia **Computer1**. Per impostare il nome dell'entità servizio per l'account del servizio gateway del computer in questo esempio, eseguire il comando seguente:

    ![Immagine del comando SPN impostato](media/service-gateway-sso-kerberos/set-spn.png)

    Dopo aver completato questo passaggio, sarà possibile procedere alla configurazione delle impostazioni di delega.

### <a name="configure-delegation-settings-on-the-gateway-service-account"></a>Configurare le impostazioni di delega nell'account del servizio gateway

Il secondo requisito di configurazione riguarda le impostazioni di delega nell'account del servizio gateway. Per eseguire questi passaggi sono disponibili vari strumenti. Qui si userà Utenti e computer di Active Directory, uno snap-in di MMC (Microsoft Management Console) che consente di gestire e pubblicare informazioni nella directory. È disponibile nei controller di dominio per impostazione predefinita. È possibile abilitare questa funzionalità anche in altri computer tramite la configurazione di Funzionalità di Windows.

È necessario configurare la delega vincolata Kerberos con protocollo in transito. Con la delega vincolata, è necessario dichiarare esplicitamente a quali servizi si vuole delegare. Ad esempio, solo SQL Server o il server SAP HANA accettano le chiamate di delega dall'account del servizio gateway.

Questa sezione presuppone che i nomi delle entità servizio per le origini dati sottostanti, ad esempio SQL Server, SAP HANA, Teradata e Spark. Per informazioni su come configurare i nomi dell'entità servizio dei server delle origini dati, vedere la documentazione tecnica per i rispettivi server di database. È anche possibile vedere il post di blog [What SPN does your app require?](https://blogs.msdn.microsoft.com/psssql/2010/06/23/my-kerberos-checklist/) (Quale nome SPN è necessario per l'app?).

Nella procedura seguente si presuppone un ambiente locale con due computer: un computer gateway e un server di database che eseguono SQL Server. Ai fini di questo esempio, si presuppongono anche le impostazioni e i nomi seguenti:

* Nome del computer del gateway: **PBIEgwTestGW**
* Account del servizio gateway: **PBIEgwTest\GatewaySvc** (nome visualizzato dell'account: Gateway Connector)
* Nome del computer dell'origine dati SQL Server: **PBIEgwTestSQL**
* Account del servizio dell'origine dati SQL Server: **PBIEgwTest\SQLService**

Ecco come configurare le impostazioni di delega:

1. Con diritti di amministratore di dominio aprire **Utenti e computer di Active Directory**.

2. Fare clic con il pulsante destro del mouse sull'account del servizio gateway (**PBIEgwTest\GatewaySvc**) e selezionare **Proprietà**.

3. Selezionare la scheda **Delega**.

4. Selezionare **Computer attendibile per la delega solo ai servizi specificati** > **Usa un qualsiasi protocollo di autenticazione**.

6. In **Servizi ai quali l'account può presentare credenziali delegate** selezionare **Aggiungi**.

7. Nella nuova finestra di dialogo selezionare **Utenti o computer**.

8. Immettere l'account del servizio per l'origine dati SQL Server (**PBIEgwTest\SQLService**) e selezionare **OK**.

9. Selezionare il nome dell'entità servizio creato per il server di database. In questo esempio il nome SPN inizia con **MSSQLSvc**. Se sono stati aggiunti sia il nome di dominio completo sia il nome dell'entità servizio NetBIOS, verranno selezionati entrambi, ma potrebbe esserne visualizzato solo uno.

10. Selezionare **OK**. A questo punto verrà visualizzato il nome SPN nell'elenco.

    Facoltativamente, è possibile selezionare **Espansa** per visualizzare sia il nome di dominio completo sia il nome dell'entità servizio di NetBIOS. Se la casella di controllo **Espansa** è selezionata, la finestra di dialogo è simile alla seguente. Selezionare **OK**.

    ![Screenshot della finestra di dialogo Gateway Connector Properties (Proprietà connettore gateway)](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Infine, nel computer in cui è in esecuzione il servizio gateway, **PBIEgwTestGW** in questo esempio, è necessario concedere all'account del servizio gateway i criteri locali **Rappresenta un client dopo l'autenticazione**. È possibile eseguire e verificare questa operazione con Editor Criteri di gruppo locali (**gpedit**).

1. Nel computer gateway eseguire *gpedit.msc*.

1. Passare a **Criteri del computer locale** > **Configurazione computer** > **Impostazioni di Windows** > **Impostazioni di sicurezza** > **Criteri locali** > **Assegnazione diritti utente**.

    ![Screenshot della struttura di cartelle Criteri del computer locale](media/service-gateway-sso-kerberos/user-rights-assignment.png)

1. Nell'elenco di criteri in **Assegnazione diritti utente** selezionare **Rappresenta un client dopo l'autenticazione**.

    ![Screenshot dei criteri Rappresenta un client](media/service-gateway-sso-kerberos/impersonate-client.png)

    Fare clic con il pulsante destro del mouse e aprire **Proprietà**. Controllare l'elenco degli account. e accertarsi che includa l'account del servizio gateway (**PBIEgwTest\GatewaySvc**).

1. Nell'elenco di criteri in **Assegnazione diritti utente** selezionare **Agire come parte del sistema operativo (SeTcbPrivilege)** . Anche in questo caso, accertarsi che l'account del servizio gateway sia incluso nell'elenco degli account.

1. Riavviare il processo del servizio **Gateway dati locale**.

Se si usa SAP HANA, è consigliabile eseguire anche i passaggi aggiuntivi seguenti per migliorare le prestazioni.

1. Nella directory di installazione del gateway trovare e aprire questo file di configurazione: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

1. Trovare la proprietà *FullDomainResolutionEnabled* e impostarla su *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

## <a name="run-a-power-bi-report"></a>Eseguire un report di Power BI

Dopo aver completato tutti i passaggi di configurazione, è possibile usare la pagina **Gestisci gateway** in Power BI per configurare l'origine dati. Quindi in **Impostazioni avanzate** abilitare l'accesso SSO e pubblicare i report e i set di dati associati all'origine dati.

![Screenshot dell'opzione Impostazioni avanzate](media/service-gateway-sso-kerberos/advanced-settings.png)

Questa configurazione funziona nella maggior parte dei casi. Con Kerberos, tuttavia, potrebbero essere necessarie configurazioni diverse a seconda dell'ambiente in uso. Se il report non viene caricato, contattare l'amministratore di dominio per indagini più approfondite.

## <a name="switch-the-gateway-to-a-domain-account"></a>Modificare l'account del servizio gateway in un account di dominio

Se necessario, è possibile modificare l'esecuzione del gateway dall'account del servizio locale a un account di dominio tramite l'interfaccia utente **Gateway dati locale**. Ecco come:

1. Aprire lo strumento di configurazione **Gateway dati locale**.

   ![Screenshot dell'opzione per avviare l'app desktop del gateway](media/service-gateway-sso-kerberos/gateway-desktop-app.png)

2. Selezionare il pulsante **Accedi** nella pagina principale ed eseguire l'accesso con l'account Power BI.

3. Dopo aver eseguito l'accesso, selezionare la scheda **Impostazioni servizio**.

4. Selezionare **Cambia account** per avviare la procedura guidata.

   ![Screenshot dell'app desktop Gateway dati locale, con l'opzione Cambia account evidenziata](media/service-gateway-sso-kerberos/change-account.png)

## <a name="configure-sap-bw-for-sso"></a>Configurare SAP BW per l'accesso SSO

Dopo aver compreso il funzionamento di Kerberos con un gateway, è possibile configurare l'accesso SSO per SAP Business Warehouse (SAP BW). La procedura seguente presuppone che sia già stata eseguita la [preparazione per la delega vincolata Kerberos](#prepare-for-kerberos-constrained-delegation), come descritto in precedenza in questo articolo.

Questa guida cerca di offrire informazioni più dettagliate possibili. Se alcuni di questi passaggi sono già stati completati, è possibile ignorarli, ad esempio se è già stato creato un utente del servizio per il server SAP BW e a questo è stato mappato un nome SPN, oppure se è già stata installata la libreria `gsskrb5`.

### <a name="set-up-gsskrb5-on-client-machines-and-the-sap-bw-server"></a>Configurare la libreria gsskrb5 nei computer client e nel server SAP BW

> [!NOTE]
> La libreria `gsskrb5` non è più supportata attivamente da SAP. Per altre informazioni, vedere [Nota SAP 352295](https://launchpad.support.sap.com/#/notes/352295). Si noti anche che `gsskrb5` non consente connessioni SSO tra il gateway dati e i server messaggi SAP BW. Sono possibili solo connessioni a server applicazioni SAP BW. Per completare una connessione SSO tramite il gateway, la libreria `gsskrb5` deve essere in uso sia nel client che nel server. È attualmente supportata la libreria di crittografia comune (sapcrypto) per SAP BW.

1. Scaricare `gsskrb5` - `gx64krb5` da [SAP Note 2115486](https://launchpad.support.sap.com/) (è necessario il nome utente SAP). Assicurarsi di aver installato almeno la versione 1.0.11.x di gsskrb5.dll e gx64krb5.dll.

1. Inserire la libreria in un percorso nel computer gateway accessibile dall'istanza del gateway (e anche dall'interfaccia grafica utente SAP, se si vuole testare la connessione SSO usando SAP Logon).

1. Inserire un'altra copia nel computer server SAP BW in un percorso accessibile dal server SAP BW.

1. Nei computer client e server impostare le variabili di ambiente `SNC\_LIB` e `SNC\_LIB\_64` in modo che facciano riferimento al percorso di gsskrb5.dll e gx64krb5.dll, rispettivamente.

### <a name="create-a-sap-bw-service-user-and-enable-snc-communication"></a>Creare un utente del servizio SAP BW e abilitare la comunicazione SNC

Oltre alla configurazione del gateway già eseguita, è necessario eseguire alcuni altri passaggi specifici di SAP BW. La sezione [Configurare le impostazioni di delega nell'account del servizio gateway](#configure-delegation-settings-on-the-gateway-service-account) della documentazione presuppone che siano già stati configurati i nomi SPN per le origini dati sottostanti. Per completare la configurazione per SAP BW:

1. In un server del controller di dominio Active Directory creare un utente del servizio (inizialmente un utente Active Directory semplice) per il server applicazioni SAP BW nell'ambiente Active Directory. Quindi assegnare un SPN all'utente.

    SAP consiglia di aggiungere sempre il prefisso `SAP/` al nome SPN, ma è possibile usare anche altri prefissi, ad esempio `HTTP/`. Il testo che segue `SAP/` può essere scelto liberamente. È possibile usare il nome utente dell'utente del servizio del server SAP BW. Se ad esempio si crea `BWServiceUser@\<DOMAIN\>` come utente del servizio, è possibile usare il nome SPN `SAP/BWServiceUser`. Per impostare il mapping di SPN è possibile usare il comando setspn. Per impostare il nome SPN dell'utente del servizio creato, ad esempio, è possibile eseguire il comando seguente da una finestra di comando in un computer controller di dominio: `setspn -s SAP/ BWServiceUser DOMAIN\ BWServiceUser`. Per altre informazioni, vedere la documentazione di SAP BW.

1. Assegnare all'utente del servizio l'accesso al server applicazioni SAP BW:

    1. Nel computer server SAP BW aggiungere l'utente del servizio al gruppo degli amministratori locali per il server SAP BW. Aprire il programma Gestione computer e fare doppio clic sul gruppo degli amministratori locali per il server.

        ![Screenshot del programma Gestione computer](media/service-gateway-sso-kerberos/computer-management.png)

    1. Fare doppio clic sul gruppo degli amministratori locali e selezionare **Aggiungi** per aggiungere l'utente del servizio al gruppo. Selezionare **Controlla nomi** per assicurarsi di aver immesso il nome correttamente. Selezionare **OK**.

1. Impostare l'utente del servizio del server SAP BW in modo che corrisponda all'utente che avvia il servizio del server SAP BW nel computer server SAP BW.

    1. Aprire **Esegui** e immettere "Services.msc". Cercare il servizio corrispondente all'istanza del server applicazioni SAP BW. Fare clic con il pulsante destro del mouse sul servizio e selezionare **Proprietà**.

        ![Screenshot di Servizi con il comando Proprietà evidenziato](media/service-gateway-sso-kerberos/server-properties.png)

    1. Passare alla scheda **Accedi** e sostituire l'utente con l'utente del servizio SAP BW. Immettere la password dell'utente e selezionare **OK**.

1. Accedere al server da SAP Logon e impostare i parametri di profilo seguenti usando la transazione RZ10:

    1. Impostare il parametro di profilo snc/identity/as su p:\<utente del servizio SAP BW creato\>, ad esempio p:BWServiceUser@MYDOMAIN.COM. Si noti il parametro p: che precede l'UPN dell'utente del servizio. Non è p:CN=, come avviene quando la libreria di crittografia comune viene usata come libreria SNC.

    1. Impostare il parametro di profilo snc/gssapi\_lib su \<percorso di gsskrb5.dll/gx64krb5.dll nel computer server (la libreria usata varia a seconda del numero di bit del sistema operativo)\>. Si ricordi di inserire la libreria in un percorso accessibile al server applicazioni SAP BW.

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

1. Dopo aver impostato i parametri di profilo, aprire la console di gestione SAP nel computer server e riavviare l'istanza SAP BW. Se il server non si avvia, verificare di aver impostato i parametri di profilo in modo corretto. Per altre informazioni sulle impostazioni dei parametri di profilo, vedere la [documentazione di SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Se si verificano problemi, è anche possibile fare riferimento alle informazioni sulla risoluzione dei problemi più avanti in questa sezione.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Eseguire il mapping di un utente SAP BW a un utente di Active Directory

Eseguire il mapping di un utente di Active Directory a un utente del server applicazioni SAP BW e testare la connessione SSO in SAP Logon.

1. Accedere al server SAP BW tramite SAP Logon. Eseguire la transazione SU01.

1. Per **User** (Utente) immettere l'utente SAP BW per cui si vogliono abilitare le connessioni SSO (nello screenshot seguente vengono impostate le autorizzazioni per BIUSER). Selezionare l'icona di **modifica** (immagine di una penna) nella parte superiore sinistra della finestra di SAP Logon.

    ![Screenshot della schermata User Maintenance (Gestione utenti) di SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selezionare la scheda **SNC**. Nella casella di input del nome SNC immettere p:\<utente Active Directory\>@\<dominio\>. Si noti che è obbligatorio specificare p: all'inizio dell'UPN dell'utente di Active Directory. L'utente di Active Directory specificato deve appartenere alla persona o all'organizzazione per cui si vuole abilitare l'accesso SSO per il server applicazioni SAP BW. Ad esempio, se si vuole abilitare l'accesso SSO per l'utente [testuser@TESTDOMAIN.COM](mailto:testuser@TESTDOMAIN.COM), immettere p:testuser@TESTDOMAIN.COM.

    ![Screenshot della schermata Maintain Users (Gestisci utenti) di SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Selezionare l'icona di **salvataggio** (immagine di un disco floppy) nella parte superiore sinistra della schermata.

### <a name="test-sign-in-by-using-sso"></a>Testare l'accesso con SSO

Verificare che sia possibile accedere al server. Usare SAP Logon tramite SSO con l'account dell'utente di Active Directory per il quale è stato appena abilitato l'accesso SSO.

1. Con l'account dell'utente di Active Directory per cui è stato appena abilitato l'accesso SSO accedere a un computer in cui è installato SAP Logon. Avviare SAP Logon e creare una nuova connessione.

1. Nella schermata **Create New System Entry** (Crea nuova voce di sistema) selezionare **User Specified System** (Sistema specificato dall'utente) > **Next** (Avanti).

    ![Screenshot della schermata Create New System Entry (Crea nuova voce di sistema)](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Specificare i dettagli appropriati nella schermata successiva, inclusi il server applicazioni, il numero di istanza e l'ID sistema, e quindi fare clic su **Finish** (Fine).

1. Fare clic con il pulsante destro del mouse sulla nuova connessione e selezionare **Properties** (Proprietà). Selezionare la scheda **Network** (Rete). Nella casella di testo **SNC Name** (Nome SNC) immettere p:\<UPN utente servizio SAP BW\>, ad esempio p:BWServiceUser@MYDOMAIN.COM. Selezionare quindi **OK**.

    ![Screenshot della schermata System Entry Properties (Proprietà voce sistema)](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Fare doppio clic sulla connessione creata per tentare una connessione SSO al server SAP BW. Se la connessione viene stabilita, procedere al passaggio successivo. In caso contrario, rivedere i passaggi precedenti di questo documento per assicurarsi che siano stati eseguiti correttamente o rivedere la sezione sulla risoluzione dei problemi che segue. Si noti che se non è possibile connettersi al server SAP BW tramite SSO in questo contesto non sarà possibile connettersi al server SAP BW tramite SSO nel contesto del gateway.

### <a name="troubleshoot-installation-and-connections"></a>Risolvere i problemi dell'installazione e delle connessioni

Se si verificano problemi, eseguire i passaggi seguenti per risolvere i problemi dell'installazione di gsskrb5 e delle connessioni SSO da SAP Logon.

- La visualizzazione dei log del server (…work\dev\_w0 nel computer server) può essere utile per risolvere eventuali errori che si verificano durante l'esecuzione dei passaggi di configurazione di gsskrb5, in particolare se il server SAP BW non si avvia dopo che i parametri di profilo sono stati cambiati.

- Se non è possibile avviare il servizio SAP BW a causa di un errore di accesso, è possibile che sia stata specificata una password errata durante l'impostazione dell'utente di avvio SAP BW. Verificare la password accedendo a un computer nell'ambiente Active Directory come utente del servizio SAP BW.

- Se si verificano errori relativi alle credenziali SQL che impediscono l'avvio del server, verificare di aver assegnato all'utente del servizio l'accesso al database SAP BW.

- Può essere visualizzato il messaggio seguente: "(GSS-API) specified target is unknown or unreachable" ((GSS-API) destinazione specificata sconosciuta o non raggiungibile). Questo in genere significa che è stato specificato un nome SNC errato. Assicurarsi di usare solo "p:", non "p:CN=" o altri parametri nell'applicazione client diversi dall'UPN dell'utente del servizio.

- Può essere visualizzato il messaggio seguente: "(GSS-API) An invalid name was supplied" ((GSS-API) È stato specificato un nome non valido). Assicurarsi di aver incluso "p:" nel valore del parametro di profilo dell'identità SNC del server.

- Può essere visualizzato il messaggio seguente: "(SNC error) the specified module could not be found" ((Errore SNC) impossibile trovare il modulo specificato). Questo errore è in genere causato dall'inserimento di `gsskrb5.dll/gx64krb5.dll` in una posizione il cui accesso richiede privilegi elevati (diritti di amministratore).

### <a name="add-registry-entries-to-the-gateway-machine"></a>Aggiungere voci del Registro di sistema nel computer gateway

Aggiungere le voci del registro necessarie nel registro del computer in cui è installato il gateway. Ecco i comandi da eseguire:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="set-configuration-parameters-on-the-gateway-machine"></a>Impostare i parametri di configurazione nel computer gateway

Per impostare i parametri di configurazione sono disponibili due opzioni, a seconda che Azure AD Connect sia o meno configurato in modo che gli utenti possano accedere al servizio Power BI come utenti di Azure AD.

Se Azure AD Connect è configurato, seguire questa procedura.

1. Aprire il file di configurazione principale del gateway, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Per impostazione predefinita, il file si trova in C:\Programmi\Gateway dati locale.

1. Assicurarsi che la proprietà **FullDomainResolutionEnabled** sia impostata su **True** e che la proprietà **SapHanaSsoRemoveDomainEnabled** sia impostata su **False**.

1. Salvare il file di configurazione.

1. Nella scheda **Servizi** di Gestione attività fare clic con il pulsante destro del mouse sul servizio gateway e selezionare **Riavvia**.

    ![Screenshot della scheda Servizi di Gestione attività](media/service-gateway-sso-kerberos/restart-gateway.png)

Se Azure AD Connect non è configurato, seguire questa procedura per ogni utente del servizio Power BI di cui eseguire il mapping a un utente di Azure AD. Questa procedura consente di collegare manualmente un utente del servizio Power BI a un utente di Active Directory con l'autorizzazione per l'accesso a SAP BW.

1. Aprire il file di configurazione principale del gateway, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Per impostazione predefinita, il file si trova in C:\Programmi\Gateway dati locale.

1. Impostare **ADUserNameLookupProperty** su `msDS-cloudExtensionAttribute1` e **ADUserNameReplacementProperty** su `SAMAccountName`. Salvare il file di configurazione.

1. Nella scheda **Servizi** di Gestione attività fare clic con il pulsante destro del mouse sul servizio gateway e selezionare **Riavvia**.

    ![Screenshot della scheda Servizi di Gestione attività](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Impostare la proprietà `msDS-cloudExtensionAttribute1` dell'utente di Active Directory. Questo è l'utente di cui è stato eseguito il mapping a un utente di SAP BW. Impostare la proprietà sull'utente del servizio Power BI per il quale si vuole abilitare Kerberos SSO. Un modo per impostare la proprietà `msDS-cloudExtensionAttribute1` consiste nell'usare lo snap-in MMC di Utenti e computer di Active Directory. È possibile usare anche altri metodi.

    1. Accedere a un computer del controller di dominio come utente amministratore.

    1. Aprire la cartella **Utenti** nella finestra dello snap-in e fare doppio clic sull'utente di Active Directory di cui è stato eseguito il mapping a un utente SAP BW.

    1. Selezionare la scheda **Editor attributi**.

        Se la scheda non è visualizzata, cercare le istruzioni su come abilitarla o usare un altro metodo per impostare la proprietà. Selezionare uno degli attributi e quindi il tasto M per passare alle proprietà di Active Directory che iniziano con la lettera m. Individuare la proprietà `msDS-cloudExtensionAttribute1` e fare doppio clic su di essa. Impostare il valore sul nome utente usato per accedere al servizio Power BI nel formato YourUser@YourDomain.

    1. Selezionare **OK**.

        ![Screenshot della finestra di dialogo Editor attributo stringa](media/service-gateway-sso-kerberos/edit-attribute.png)

    1. Selezionare **Applica**. Verificare che sia stato impostato il valore corretto nella colonna **Valore**.

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service"></a>Aggiungere una nuova origine dati del server applicazioni SAP BW al servizio Power BI

Aggiungere l'origine dati SAP BW al gateway seguendo le istruzioni per l'[esecuzione di un report](#run-a-power-bi-report) fornite in precedenza in questo articolo.

1. Nella finestra di configurazione dell'origine dati immettere **Nome host**, **Numero sistema** e **ID client** del server applicazioni per accedere al server SAP BW da Power BI Desktop. Per **Metodo di autenticazione** selezionare **Windows**.

1. Nel campo **Nome del partner SNC** immettere p: \<nome SPN mappato all'utente del servizio SAP BW\>. Ad esempio, se il nome SNC è SAP/BWServiceUser@MYDOMAIN.COM, immettere p:SAP/BWServiceUser@MYDOMAIN.COM nel campo **Nome del partner SNC**.

1. Per la libreria SNC selezionare **SNC\_LIB** o **SNC\_LIB\_64**.

1. **Nome utente** e **Password** devono corrispondere al nome utente e alla password di un utente di Active Directory con l'autorizzazione ad accedere al server SAP BW con SSO. In altre parole, devono appartenere a un utente di Active Directory di cui è stato eseguito il mapping a un utente SAP BW tramite la transazione SU01. Queste credenziali vengono usate solo se la casella **Usa SSO tramite Kerberos per le query DirectQuery** non è selezionata.

1. Selezionare la casella **Usa SSO tramite Kerberos per le query DirectQuery** e selezionare **Applica**. Se la connessione di test ha esito negativo, verificare di aver eseguito correttamente i passaggi di installazione e configurazione descritti in precedenza.

    Il gateway usa sempre le credenziali digitate per stabilire una connessione di prova al server e per eseguire aggiornamenti pianificati di report basati sull'importazione. Il gateway tenta di stabilire una connessione SSO solo se l'opzione **Usa SSO tramite Kerberos per le query DirectQuery** è selezionata e l'utente sta accedendo a un report o a un set di dati basati su query DirectQuery.

### <a name="test-your-setup"></a>Testare l'installazione

Per testare l'installazione, pubblicare un report DirectQuery da Power BI Desktop al servizio Power BI. Assicurarsi di aver eseguito l'accesso al servizio Power BI come utente di Azure AD o come utente di cui è stato eseguito il mapping alla proprietà `msDS-cloudExtensionAttribute1` di un utente di Azure AD. Se l'installazione è stata completata correttamente, è possibile creare un report dal set di dati pubblicato nel servizio Power BI. È anche possibile eseguire il pull dei dati tramite oggetti visivi nel report.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Risolvere i problemi di connettività del gateway

1. Controllare i registri del gateway. Aprire l'applicazione di configurazione del gateway e selezionare **Diagnostica** > **Esporta log**. Gli errori più recenti sono indicati nella parte inferiore dei file di log.

    ![Screenshot dell'applicazione Gateway dati locale, con la voce Diagnostica evidenziata](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Attivare la traccia SAP BW e rivedere i file di log generati. Sono disponibili diversi tipi di traccia SAP BW. Per altre informazioni, consultare la documentazione di SAP.

## <a name="errors-from-an-insufficient-kerberos-configuration"></a>Errori derivanti da una configurazione Kerberos insufficiente

Se il gateway e il server di database sottostanti non sono configurati correttamente per la delega vincolata Kerberos, può essere visualizzato il messaggio di errore seguente relativo all'impossibilità di caricare i dati:

![Screenshot del messaggio di errore](media/service-gateway-sso-kerberos/load-data-error.png)

I dettagli tecnici associati al messaggio di errore (DM_GWPipeline_Gateway_ServerUnreachable) possono avere un aspetto simile al seguente:

![Screenshot dei dettagli tecnici del messaggio di errore](media/service-gateway-sso-kerberos/server-unreachable.png)

Il gateway non riesce a rappresentare correttamente l'utente di origine e il tentativo di connessione non è riuscito.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su **Gateway dati locale** e su **DirectQuery**, vedere le risorse seguenti:

* [On-premises data gateway (Gateway dati locale)](service-gateway-onprem.md)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
