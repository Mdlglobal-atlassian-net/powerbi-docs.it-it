---
title: Risolvere i problemi relativi ai gateway - Power BI
description: Questo articolo illustra come individuare e risolvere i problemi relativi al gateway dati locale e a Power BI. Fornisce soluzioni alternative potenziali per problemi noti e strumenti utili.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: a013b42f1cd7cc9b2c5c24f9636683a52687ceb8
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271427"
---
# <a name="troubleshoot-gateways---power-bi"></a>Risolvere i problemi relativi ai gateway - Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Questo articolo illustra alcuni problemi comuni durante l'uso del **gateway dati locale** con Power BI. Se si verifica un errore diverso da quelli elencati di seguito, è possibile usare il [sito delle community](http://community.powerbi.com) di Power BI o creare un [ticket di supporto](http://powerbi.microsoft.com/support).

## <a name="configuration"></a>Configurazione

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>Errore: Il servizio Power BI ha segnalato che il gateway locale non è raggiungibile. Riavviare il gateway e riprovare

Al termine della configurazione, il servizio Power BI viene chiamato di nuovo per convalidare il gateway. Il servizio Power BI non dichiara il gateway come dinamico. Il riavvio del servizio windows potrebbe consentire la riuscita della comunicazione. Per avere maggiori dettagli, è possibile raccogliere e rivedere i log, come descritto nell'articolo sulla [raccolta dei log dall'app del gateway dati locale](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

## <a name="data-sources"></a>Origini dati

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Errore: La connessione non è riuscita. Dettagli: "Le credenziali di connessione non sono valide"

In **Mostra dettagli** viene visualizzato il messaggio di errore ricevuto dall'origine dati. Per SQL Server, ha un aspetto simile al seguente.

    Login failed for user 'username'.

Verificare la correttezza del nome utente e della password. Verificare anche che tali credenziali permettano di connettersi correttamente all'origine dati. Assicurarsi che l'account utilizzato corrisponda al **Metodo di autenticazione**.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Errore: La connessione non è riuscita. Dettagli: "Non è possibile stabilire la connessione al database"

Siamo in grado di effettuare la connessione al server, ma non per il database specificato. Verificare il nome del database, e che la credenziale dell'utente disponga dell'autorizzazione per accedere al database.

In **Mostra dettagli** viene visualizzato il messaggio di errore ricevuto dall'origine dati. Per SQL Server, ha un aspetto simile al seguente.

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Errore: La connessione non è riuscita. Dettagli: "Si è verificato un errore sconosciuto nel gateway dati"

Questo errore può verificarsi per diversi motivi. Assicurarsi che sia possibile connettersi all'origine dati dal computer che ospita il gateway. Questo può essere il risultato dell’inaccessibilità al server.

In **Mostra dettagli** può essere visualizzato il codice di errore **DM_GWPipeline_UnknownError**.

Per altri dettagli, è anche possibile cercare in Registri eventi > **Registri applicazioni e servizi** > **Servizio Gateway dati locale**.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Errore: Si è verificato un errore durante il tentativo di connessione a \<server\>. Dettagli: "Il gateway dati è raggiungibile, ma non può accedere all'origine dati locale."

Non è stato possibile connettersi all'origine dati specificata. Controllare le informazioni fornite per l'origine dati.

In **Mostra dettagli** può essere visualizzato il codice di errore **DM_GWPipeline_Gateway_DataSourceAccessError**.

Se il messaggio di errore sottostante è simile al seguente, significa che l'account in uso per l'origine dati non è un amministratore del server per l'istanza di Analysis Services. [Altre informazioni](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance)

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Se il messaggio di errore sottostante è simile al seguente, l'account del servizio per Analysis Services potrebbe non includere l'attributo [token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx) (TGGAU) della directory.

    The username or password is incorrect.

L'attributo TGGAU è abilitato nei domini con accesso compatibile con le versioni precedenti a Windows 2000. La maggior parte dei domini creati di recente, tuttavia, non abilita questo attributo per impostazione predefinita. Per altre informazioni, vedere [qui](https://support.microsoft.com/kb/331951).

Per confermare, seguire questa procedura.

1. Connettersi al computer di Analysis Services in SQL Server Management Studio. All'interno delle proprietà avanzate di connessione includere il valore EffectiveUserName per l'utente specifico e verificare se l'errore viene riprodotto.
2. È possibile usare lo strumento dsacls di Active Directory per verificare che l'attributo sia incluso nell'elenco. Questo strumento è disponibile in un controller di dominio. È necessario conoscere il nome di dominio distinto per l'account e passarlo allo strumento.

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    I risultati dovrebbero avere un aspetto simile al seguente.

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

Per risolvere il problema, è necessario abilitare TGGAU nell'account usato per il servizio di Windows Analysis Services.

#### <a name="another-possibility-for-username-or-password-incorrect"></a>Un'altra possibilità per password o nome utente non corretto

Questo errore può dipendere anche dal fatto che il server di Analysis Services si trova in un dominio diverso rispetto a quello dell'utente e che non è stato stabilito alcun trust bidirezionale.

È necessario collaborare con gli amministratori del dominio per verificare la relazione di trust tra i domini.

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Non è possibile visualizzare le origini dati del gateway dati nell'esperienza "Recupera dati" per Analysis Services dal servizio Power BI

Assicurarsi che il proprio account sia elencato nella scheda **Utenti** dell'origine dati all'interno della configurazione del gateway. Se non si ha accesso al gateway, rivolgersi all'amministratore del gateway e chiedere di verificare. Solo gli account presenti nell'elenco **Utenti** possono visualizzare l'origine dati riportata nell'elenco di Analysis Services.

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>Errore: Non sono presenti gateway installati o configurati per le origini dati in questo set di dati

Verificare di aver aggiunto una o più origini dati al gateway, come descritto in [Aggiungere un'origine dati](service-gateway-data-sources.md#add-a-data-source). Se il gateway non è visualizzato nel portale di amministrazione in **Gestisci gateway**, provare a cancellare la cache del browser o a disconnettersi dal servizio e quindi riconnettersi.

## <a name="datasets"></a>Set di dati

### <a name="error-there-is-not-enough-space-for-this-row"></a>Errore: Non è disponibile spazio sufficiente per questa riga

Questo accade in presenza di una riga singola le cui dimensioni superano 4 MB. È necessario determinare quale sia la riga dall'origine dati e tentare di filtrarla o di ridurne le dimensioni.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Errore: Il nome del server specificato non corrisponde al nome del server nel certificato SSL di SQL Server

Questo errore può verificarsi quando il nome comune (CN) del certificato corrisponde al nome di dominio (FQDN) completo del server, ma viene specificato solo il nome NetBIOS per il server. Ciò causa una mancata corrispondenza con il certificato. Per risolvere questo problema, è necessario far sì che per il nome del server all'interno dell'origine dati del gateway e il file PBIX venga usato il nome di dominio completo del server.

### <a name="i-dont-see-the-on-premises-data-gateway-present-when-configuring-scheduled-refresh"></a>Il gateway dati locale non è visibile durante la configurazione dell'aggiornamento pianificato

Questo problema può essere dovuto ad alcuni scenari diversi.

1. I nomi del server e del database non corrispondono a quelli immessi in Power BI Desktop e all'origine dati configurata per il gateway. Deve trattarsi degli stessi valori, senza distinzione tra maiuscole e minuscole.
2. L'account non è elencato nella scheda **Utenti** dell'origine dati all'interno della configurazione del gateway. È necessario chiedere all'amministratore del gateway di essere aggiunti all'elenco.
3. All'interno del file di Power BI Desktop sono presenti più origini dati, ma non tutte configurate con il gateway. È necessario definire ogni origine dati con il gateway in modo da visualizzarlo in Aggiornamento pianificato.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>Errore: La quantità di dati non compressi ricevuti nel client del gateway ha superato il limite

La limitazione esatta è di 10 GB di dati non compressi per ogni tabella. Se si verifica questo problema, ci sono buone opzioni per ottimizzare ed evitare il problema. In particolare, aiuta ridurre l'uso di valori stringa lunghi e molto costanti, usando invece una chiave normalizzata o rimuovendo la colonna (se non usata).

## <a name="reports"></a>Report

### <a name="report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>Il report non è riuscito ad accedere all'origine dati perché non si ha accesso all'origine dati tramite un gateway dati locale

Questo è in genere dovuto a uno dei motivi seguenti.

1. Le informazioni sull'origine dati non corrispondono al contenuto del set di dati sottostante. Il nome del server e del database devono corrispondere tra l'origine dati definita per il gateway dati locale e i dati forniti all'interno di Power BI Desktop. Se si usa un indirizzo IP in Power BI Desktop, anche l'origine dati per il gateway dati locale deve usare un indirizzo IP.
2. Non sono disponibili origini dati in alcun gateway dell'organizzazione. È possibile configurare l'origine dati in un gateway dati locale nuovo o esistente.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Errore: Si è verificato un errore di accesso all'origine dati. Contattare l'amministratore del gateway

Se questo report usa una connessione dinamica di Analysis Services, potrebbe verificarsi un problema con un valore passato a EffectiveUserName non valido o privo delle autorizzazioni per il computer di Analysis Services. Un problema di autenticazione dipende in genere dal fatto che il valore passato per EffectiveUserName non corrisponde al nome dell'entità utente locale.

Per risolvere il problema, seguire questa procedura.

1. Trovare il nome utente effettivo entro i [log del gateway](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).
2. Dopo avere passato il valore, verificarne la correttezza. Se corrisponde all'utente, è possibile usare il comando seguente da un prompt dei comandi per visualizzare il nome dell'entità utente. Il nome dell'entità utente assomiglia a un indirizzo di posta elettronica.

        whoami /upn

È facoltativamente possibile verificare i dati che Power BI riceve da Azure Active Directory.

1. Passare a [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Selezionare **Sign in** (Accedi) in alto a destra.
3. Eseguire la query seguente. Viene visualizzata una risposta JSON di dimensioni abbastanza grandi.

        https://graph.windows.net/me?api-version=1.5
4. Cercare **userPrincipalName**.

Se il nome dell'entità utente di Azure Active Directory non corrisponde al nome dell'entità utente di Active Directory locale, è possibile usare la funzionalità [Mapping nomi utente](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources) per sostituirlo con un valore valido. In alternativa, è possibile collaborare con l'amministratore del tenant o l'amministratore locale di Active Directory per ottenere una modifica del nome dell'entità utente.

## <a name="kerberos"></a>Kerberos

Se il server di database sottostante e il gateway dati locale non sono configurati in modo appropriato per la [delega vincolata Kerberos](service-gateway-sso-kerberos.md), abilitare la [registrazione dettagliata](/data-integration/gateway/service-gateway-performance#slow-performing-queries) nel gateway ed esaminare i dati in base agli errori e alle tracce nei file di log del gateway, come punto di partenza per la risoluzione dei problemi. Per raccogliere i log del gateway per la visualizzazione, vedere l'articolo sulla [raccolta dei log dall'app del gateway dati locale](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

### <a name="impersonationlevel"></a>ImpersonationLevel

Il valore di ImpersonationLevel è correlato alla configurazione del nome dell'entità servizio oppure all'impostazione dei criteri locali.

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**Soluzione**

Seguire questi passaggi per risolvere il problema:

1. Configurare un nome dell'entità servizio per il gateway locale.
2. Configurare la delega vincolata in Active Directory (AD).

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException: Impossibile creare l'identità di Windows per l'utente idutente

L'eccezione FailedToImpersonateUserException si verifica se non è possibile la rappresentazione per conto di un altro utente. Ciò può verificarsi anche se l'account che si tenta di rappresentare proviene da un altro dominio rispetto a quello del servizio gateway (questa è una limitazione).

**Soluzione**

* Verificare che la configurazione sia corretta in base ai passaggi indicati nella sezione ImpersonationLevel precedente.
* Assicurarsi che l'ID utente che si tenta di rappresentare sia un account di Active Directory valido.

### <a name="general-error-1033-error-while-parsing-the-protocol"></a>Errore generale. Errore 1033 durante l'analisi del protocollo

L'errore 1033 viene visualizzato quando l'ID esterno configurato in SAP HANA non corrisponde all'account di accesso se l'utente è rappresentato con l'UPN (alias@domain.com). Nei log comparirà il messaggio "Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com'" (UPN originale sostituito con il nuovo UPN) all'inizio dei log degli errori come illustrato di seguito.

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**Soluzione**

* SAP HANA richiede che l'utente rappresentato usi l'attributo sAMAccountName in Active Directory (alias utente). Se non è corretto, viene visualizzato l'errore 1033.

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* Nei log viene visualizzato il nome sAMAccountName (alias) e non il nome UPN, ovvero l'alias seguito dal dominio (alias@doimain.com).

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Communication link failure;-10709 Connection failed (RTE:[-1] Kerberos error. Major: "Miscellaneous failure [851968]", minor: "No credentials are available in the security package

Il messaggio di errore di connessione non riuscita -10709 viene visualizzato se la delega non è configurata correttamente in Active Directory.

**Soluzione**

* Assicurarsi che il server SAP Hana sia incluso nella scheda della delega in Active Directory per l'account del servizio gateway.

   ![Scheda della delega](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>Cronologia aggiornamenti

Quando si usa il gateway per un aggiornamento pianificato, **Cronologia aggiornamenti** consente di visualizzare gli errori che si sono verificati, nonché di fornire dati utili nel caso in cui sia necessario creare una richiesta di supporto. È possibile visualizzare sia gli aggiornamenti pianificati che quelli su richiesta. Per accedere alla **Cronologia aggiornamenti**, eseguire le operazioni seguenti.

1. In **Set di dati** nel riquadro di spostamento di Power BI selezionare un set di dati &gt; Apri menu &gt;**Pianifica aggiornamento**.

    ![Come selezionare Pianifica aggiornamento](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. In **Impostazioni per...** &gt; **Pianifica aggiornamento** selezionare **Cronologia aggiornamenti**.

    ![Selezionare la cronologia aggiornamenti](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![Visualizzazione della cronologia aggiornamenti](media/service-gateway-onprem-tshoot/refresh-history.png)

Per altre informazioni sulla risoluzione degli scenari per la risoluzione dei problemi di aggiornamento, vedere l'articolo [Scenari per la risoluzione dei problemi di aggiornamento](refresh-troubleshooting-refresh-scenarios.md).

## <a name="fiddler-trace"></a>Traccia di Fiddler

[Fiddler](http://www.telerik.com/fiddler) è uno strumento gratuito di Telerik che monitora il traffico HTTP. È possibile visualizzare il traffico dal servizio Power BI al computer client e viceversa. Potrebbero essere illustrati errori e altre informazioni correlate.

![Uso della traccia di Fiddler](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>Passaggi successivi

* [Risolvere i problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)
* [Configurazione delle impostazioni del proxy per il gateway dati locale](/data-integration/gateway/service-gateway-proxy)  
* [Gestire l'origine dati - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gestire l'origine dati - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gestire l'origine dati - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
