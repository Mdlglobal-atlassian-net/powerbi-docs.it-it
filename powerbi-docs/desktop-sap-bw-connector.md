---
title: Usare SAP Business Warehouse (BW) Connector in Power BI Desktop
description: Usare SAP BW Connector in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8e1f6c38af11c5bdf942a4dc3a20b4b5f0ec0601
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76038877"
---
# <a name="use-the-sap-business-warehouse-connector-in-power-bi-desktop"></a>Usare SAP Business Warehouse Connector in Power BI Desktop

Con Power BI Desktop è possibile accedere ai dati *SAP BusinessWarehouse (BW)* .

Per informazioni su come i clienti SAP possono trarre vantaggio dal collegamento di Power BI ai propri sistemi SAP BW esistenti, vedere il [white paper su Power BI e SAP BW](https://aka.ms/powerbiandsapbw). Per informazioni dettagliate sull'uso di DirectQuery con SAP BW, vedere [DirectQuery e SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

A partire dalla versione di giugno 2018 di *Power BI Desktop* e con disponibilità generale in ottobre 2018 è possibile usare SAP BW Connector con un'implementazione dotata di importanti miglioramenti di prestazioni e funzionalità. Microsoft ha sviluppato l'*implementazione 2.0* di SAP BW Connector. Selezionare la versione 1 (v1) o l'implementazione 2.0 di SAP BW Connector. Le sezioni seguenti illustrano l'installazione delle diverse versioni. È possibile scegliere uno dei due connettori al momento della connessione a SAP BW da Power BI Desktop.

Quando possibile, è consigliabile usare l'implementazione 2.0 di SAP Connector.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Installazione della versione 1 di Connector per SAP BW

Quando possibile, è consigliabile usare l'implementazione 2.0 di SAP BW Connector. Questa sezione descrive l'installazione della versione 1 di SAP BW Connector.

1. Installare la libreria *SAP NetWeaver* nel computer locale. È possibile ottenere la libreria SAP NetWeaver dall'amministratore SAP o direttamente da [SAP Software Download Center](https://support.sap.com/swdc) (area di download del software SAP). Dato che SAP Software Download Center cambia struttura di frequente, non sono disponibili indicazioni più specifiche per la navigazione nel sito. Di solito la libreria SAP NetWeaver è inclusa anche nell'installazione degli strumenti client SAP.

   È possibile cercare la *nota SAP 1025361* per ottenere il percorso di download per la versione più recente. Assicurarsi che l'architettura per la libreria SAP NetWeaver (a 32 bit o a 64 bit) corrisponda all'installazione di Power BI Desktop. Installare tutti i file inclusi in *SAP NetWeaver RFC SDK* in base alla nota SAP.
2. In Power BI Desktop selezionare **Recupera dati**. Le opzioni in **Database** includono le voci *Server applicazioni SAP Business Warehouse* e *Server messaggi SAP Business Warehouse*.

   ![Opzioni Recupera dati per SAP](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Installazione dell' implementazione 2.0 di SAP Connector

L'implementazione 2.0 di SAP Connector richiede SAP .NET Connector 3.0. Per l'accesso al download è necessario avere un ID utente SAP valido. Per ottenere SAP .NET Connector 3.0 contattare il team SAP Basis.

È possibile scaricare [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html) da SAP.

Il connettore è disponibile nelle versioni a 32 bit e a 64 bit. Scegliere la versione che corrisponde all'installazione di Power BI Desktop in uso. Attualmente il sito Web include due versioni per .NET 4.0 Framework:

* SAP Connector per Microsoft .NET 3.0.22.0 per Windows a 32 bit (x86) come file con estensione zip (6.896 KB), 1 giugno 2019
* SAP Connector per Microsoft .NET 3.0.22.0 per Windows a 64 bit (x64) come file con estensione zip (7180 KB), 1 giugno 2019

Al momento dell'installazione, in **Optional setup steps** (Procedura di installazione facoltativa) assicurarsi di selezionare *Install assemblies to GAC* (Installa gli assembly in GAC).

![Passaggi facoltativi di configurazione SAP](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> Nella prima versione di SAP BW l'implementazione richiedeva le DLL NetWeaver. Se si usa l'implementazione 2.0 di SAP Connector anziché la prima versione, le DLL NetWeaver non sono necessarie.

## <a name="version-1-sap-bw-connector-features"></a>Funzionalità della versione 1 di Connector per SAP BW

La versione 1 di SAP BW Connector in Power BI Desktop consente di importare dati dai cubi *Server SAP Business Warehouse* o di usare DirectQuery.

Per altre informazioni su SAP BW Connector e su come usarlo con DirectQuery, vedere [DirectQuery e SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

Al momento della connessione specificare **Server**, **Numero sistema** e **ID client** per stabilire la connessione.

![Impostazioni di connessione server SAP](media/desktop-sap-bw-connector/sap_bw_3a.png)

È anche possibile specificare altre due **Opzioni avanzate**: **Codice lingua** e un'**istruzione MDX** personalizzata da eseguire nel server specificato.

![Informazioni di connessione aggiuntive](media/desktop-sap-bw-connector/sap_bw_4a.png)

Se non si specifica un'istruzione MDX, l'impostazione di connessione visualizza l'elenco dei cubi disponibili nel server. È possibile eseguire il drill-down e selezionare elementi dai cubi disponibili, incluse le dimensioni e le misure. Power BI visualizza le query e i cubi esposti dalle [interfacce di analisi aperta](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Quando si seleziona uno o più elementi dal server, la finestra di dialogo Strumento di navigazione visualizza un'anteprima della tabella di output.

![Anteprima tabella SAP](media/desktop-sap-bw-connector/sap_bw_5.png)

Nella finestra di dialogo **Strumento di navigazione** sono disponibili anche opzioni di visualizzazione:

* **Solo gli elementi selezionati**. Per impostazione predefinita, lo **Strumento di navigazione** visualizza tutti gli elementi:  questa opzione è utile per verificare il set finale degli elementi selezionati. Un approccio alternativo alla visualizzazione degli elementi selezionati è la selezione dei nomi colonna nell'area di anteprima.
* **Abilita anteprime dati**. Questo è il valore predefinito. Visualizza le anteprime dati. La disattivazione delle anteprime dei dati riduce il numero di chiamate al server, perché il server non richiede più i dati per le anteprime.
* **Nomi tecnici**. SAP BW supporta il concetto di *nomi tecnici* per gli oggetti all'interno di un cubo. I nomi tecnici consentono al proprietario di un cubo di esporre *nomi descrittivi* per gli oggetti cubo, anziché esporre solo i *nomi fisici* per tali oggetti nel cubo.

![Finestra Strumento di navigazione](media/desktop-sap-bw-connector/sap_bw_6.png)

Dopo aver selezionato tutti gli oggetti necessari è possibile decidere cosa fare successivamente selezionando una delle opzioni seguenti:

* Selezionare **Carica** per caricare l'intero set di righe per la tabella di output nel modello di dati di Power BI Desktop. Viene aperta la visualizzazione **Report**. È possibile iniziare a visualizzare i dati o apportare ulteriori modifiche usando le visualizzazioni **Dati** o **Relazioni**.
* Selezionare **Modifica** per aprire l'**editor di query**. Specificare passaggi aggiuntivi di trasformazione e filtro dei dati prima di importare l'intero set di righe nel modello di dati di Power BI Desktop.

Oltre a importare dati dai cubi SAP BW, è possibile importare dati in Power BI Desktop da una vasta gamma di altre origini dati e quindi combinarli in un singolo report. Questa funzionalità offre molti scenari interessanti per i report e l'analisi oltre ai dati SAP BW.

## <a name="using-implementation-20-sap-bw-connector"></a>Uso dell'implementazione 2.0 di SAP BW Connector

Creare una nuova connessione per usare l'implementazione 2.0 di SAP BW Connector. Per creare una nuova connessione seguire questa procedura.

1. Selezionare **Recupera dati**. Selezionare **Server applicazioni SAP Business Warehouse** o **Server messaggi SAP Business Warehouse** e quindi eseguire la connessione.

2. Nella finestra di dialogo Nuova connessione selezionare l'implementazione. Se si seleziona **2.0** in **Implementazione**, come illustrato nell'immagine seguente, si abilitano le opzioni **Modalità di esecuzione**, **Dimensioni batch** e **Abilita le strutture per le caratteristiche**.

    ![Finestra di dialogo Connessione SAP](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Seleziona **OK**. Dopo questa fase l'esperienza è identica a quella descritta in [Funzionalità della versione 1 di Connector per SAP BW](#version-1-sap-bw-connector-features) per SAP BW Connector versione 1.

### <a name="new-options-for-implementation-20"></a>Nuove opzioni per l'implementazione 2.0

L'implementazione 2.0 supporta le seguenti opzioni:

* *ExecutionMode* specifica l'interfaccia MDX usata per eseguire query nel server. Sono valide le opzioni seguenti:

  * `SapBusinessWarehouseExecutionMode.BasXml`
  * `SapBusinessWarehouseExecutionMode.BasXmlGzip`
  * `SapBusinessWarehouseExecutionMode.DataStream`

    Il valore predefinito è `SapBusinessWarehouseExecutionMode.BasXmlGzip`.

    L'uso di `SapBusinessWarehouseExecutionMode.BasXmlGzip` può migliorare le prestazioni quando si verifica una latenza elevata per set di dati di grandi dimensioni.

* *BatchSize* specifica il numero massimo di righe recuperate in una singola operazione quando si esegue un'istruzione MDX. Un numero ridotto implica un numero maggiore di chiamate al server durante il recupero di un set di dati di grandi dimensioni. Un numero di righe elevato può migliorare le prestazioni, ma può anche causare problemi di memoria nel server SAP BW. Il valore predefinito è 50000 righe.

* *EnableStructures* indica se le strutture di caratteristiche vengono riconosciute. Il valore predefinito di questa opzione è false. L'opzione ha effetto sull'elenco degli oggetti disponibili per la selezione. Non è supportata in modalità Query nativa.

L'opzione *ScaleMeasures* è stata deprecata in questa implementazione. Il comportamento è ora uguale all'impostazione di *ScaleMeasures* su false, ovvero vengono visualizzati sempre valori non in scala.

### <a name="additional-improvements-for-implementation-20"></a>Altri miglioramenti per l'implementazione 2.0

L'elenco seguente descrive alcuni miglioramenti aggiuntivi inclusi nella nuova implementazione:

* Prestazioni migliorate.
* Possibilità di recuperare vari milioni di righe di dati e ottimizzazione tramite il parametro delle dimensioni batch.
* Possibilità di cambiare la modalità di esecuzione.
* Supporto della modalità compressa. Particolarmente vantaggioso per le connessioni con latenza elevata o set di dati di grandi dimensioni.
* Rilevamento migliorato delle variabili `Date`.
* [Sperimentale] Visualizzazione di valori `Date` (tipo ABAP DATS) e `Time` (tipo ABAP TIMS) come date e ore, anziché come valori di testo.
* Gestione delle eccezioni migliorata. Gli errori che si verificano nelle chiamate BAPI vengono ora rilevati.
* Riduzione delle colonne nelle modalità BasXml e BasXmlGzip. Se ad esempio la query MDX generata recupera 40 colonne ma la selezione corrente ne richiede solo 10, questa richiesta viene passata al server per il recupero di un set di dati più piccolo.

### <a name="changing-existing-reports-to-use-implementation-20"></a>Modifica dei report esistenti per l'uso dell'implementazione 2.0

La modifica dei report esistenti per l'uso dell'implementazione 2.0 è possibile solo in modalità importazione. A tale scopo, seguire questa procedura:

1. Aprire un report esistente, selezionare **Modifica query** nella barra multifunzione e quindi selezionare la query di SAP Business Warehouse da aggiornare.

1. Fare clic con il pulsante destro del mouse sulla query e selezionare **Editor avanzato**.

1. In **Editor avanzato** modificare la chiamata `SapBusinessWarehouse.Cubes` come indicato di seguito:

    Determinare se la query contiene già un record di opzione, come quello visualizzato nell'esempio seguente:

    ![Frammento di query](media/desktop-sap-bw-connector/sap_bw_9.png)

    Se sì, aggiungere l'opzione `Implementation` 2.0 e rimuovere l'opzione `ScaleMeasures`, se presente, come illustrato:

    ![Frammento di query](media/desktop-sap-bw-connector/sap_bw_10.png)

    Se la query non include un record di opzione, aggiungere il record. Nel caso dell'opzione seguente:

    ![Frammento di query](media/desktop-sap-bw-connector/sap_bw_11.png)

    Modificarla nel modo seguente:

    ![Frammento di query](media/desktop-sap-bw-connector/sap_bw_12.png)

La compatibilità tra l'implementazione 2.0 e la versione 1 di SAP BW Connector è stata elaborata con il massimo impegno. Tuttavia possono essere presenti alcune differenze, originate dalle diverse modalità di esecuzione MDX usate in SAP BW. Per risolvere eventuali discrepanze, provare ad alternare tra le diverse modalità di esecuzione.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Questa sezione include situazioni (e soluzioni) di risoluzione dei problemi per l'uso di SAP BW Connector.

1. I dati numerici di SAP BW restituiscono punti decimali anziché virgole. Ad esempio, 1,000,000 viene restituito come 1.000.000.

   SAP BW restituisce i dati decimali con `,` (virgola) o `.` (punto) come separatore decimale. Per specificare quale di questi simboli verrà usato da SAP BW come separatore decimale, il driver usato da Power BI Desktop esegue una chiamata a `BAPI_USER_GET_DETAIL`. Questa chiamata restituisce una struttura denominata `DEFAULTS`, con un campo denominato `DCPFM` che archivia *Decimal Format Notation* (Notazione formato decimale). Il campo accetta uno dei seguenti valori:

   * " " (spazio) = Il separatore decimale è la virgola: N.NNN,NN
   * "X" = Il separatore decimale è il punto: N,NNN.NN
   * "Y" = Il separatore decimale è N NNN NNN,NN

   I clienti che hanno segnalato questo problema hanno riscontrato che la chiamata a `BAPI_USER_GET_DETAIL` non riesce per un determinato utente (quello per cui sono visualizzati i dati non corretti), con un messaggio di errore simile al seguente:

   ```xml
    You are not authorized to display users in group TI:
        <item>
            <TYPE>E</TYPE>
            <ID>01</ID>
            <NUMBER>512</NUMBER>
            <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
            <LOG_NO/>
            <LOG_MSG_NO>000000</LOG_MSG_NO>
            <MESSAGE_V1>TI</MESSAGE_V1>
            <MESSAGE_V2/>
            <MESSAGE_V3/>
            <MESSAGE_V4/>
            <PARAMETER/>
            <ROW>0</ROW>
            <FIELD>BNAME</FIELD>
            <SYSTEM>CLNTPW1400</SYSTEM>
        </item>
   ```

   Per risolvere questo errore gli utenti devono chiedere all'amministratore SAP di concedere all'utente SAPBW usato in Power BI l'autorizzazione per l'esecuzione di `BAPI_USER_GET_DETAIL`. Vale anche la pena verificare che l'utente abbia il valore `DCPFM` richiesto, come descritto in precedenza in questa soluzione.

2. Connettività per le query BEx SAP
   
   È possibile eseguire query BEx in Power BI Desktop abilitando una proprietà specifica, come illustrato nella figura seguente:
   
   ![Abilitare Release for External Access](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. La finestra **Strumento di navigazione** non visualizza un'anteprima dei dati e visualizza invece il messaggio di errore *Riferimento oggetto non impostato su un'istanza di un oggetto*.
   
   Gli utenti SAP devono accedere a moduli di funzione BAPI specifici per ottenere i metadati e recuperare dati da InfoProvider di SAP BW. I moduli includono:

   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Per risolvere il problema verificare che l'utente abbia accesso ai vari moduli MDPROVIDER e a `BAPI_IOBJ_GETDETAIL`. Per altre opzioni di risoluzione per questo problema o problemi simili, è possibile abilitare la funzionalità di traccia. Selezionare **File** > **Opzioni e impostazioni** > **Opzioni**. In **Opzioni** selezionare **Diagnostica** e quindi selezionare **Abilita traccia**. Tentare il recupero dei dati da SAP BW mentre è attiva la traccia ed esaminare il file di traccia per altri dettagli.

## <a name="sap-bw-connection-support"></a>Supporto della connessione SAP BW

La tabella seguente illustra il supporto corrente per SAP BW.

|Product  |Modalità  |Autenticazione  |Connettore  |Libreria SNC  |Supportato  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |Qualsiasi         | Utente/Password  | Server applicazioni | N/D  | Sì  |
|Power BI Desktop     |Qualsiasi         | Windows          | Server applicazioni | sapcrypto + gsskrb5/gx64krb5  | Sì  |
|Power BI Desktop     |Qualsiasi         | Windows tramite rappresentazione | Server applicazioni | sapcrypto + gsskrb5/gx64krb5  | Sì  |
|Power BI Desktop     |Qualsiasi         | Utente/Password        | Server messaggi | N/D  | Sì  |
|Power BI Desktop     |Qualsiasi         | Windows        | Server messaggi | sapcrypto + gsskrb5/gx64krb5  | Sì  |
|Power BI Desktop     |Qualsiasi         | Windows tramite rappresentazione | Server messaggi | sapcrypto + gsskrb5/gx64krb5  | Sì  |
|Power BI Gateway     |Importa      | La stessa di Power BI Desktop |         |   |   |
|Power BI Gateway     |DirectQuery | Utente/Password        | Server applicazioni | N/D  | Sì  |
|Power BI Gateway     |DirectQuery | Windows tramite rappresentazione (utente fisso, no SSO) | Server applicazioni | sapcrypto + gsskrb5/gx64krb5  | Sì  |
|Power BI Gateway     |DirectQuery | SSO tramite Kerberos per l'opzione query DirectQuery | Server applicazioni | sapcrypto + gsskrb5/gx64krb5   | Sì  |
|Power BI Gateway     |DirectQuery | Utente/Password        | Server messaggi | N/D  | Sì  |
|Power BI Gateway     |DirectQuery | Windows tramite rappresentazione (utente fisso, no SSO) | Server messaggi | sapcrypto + gsskrb5/gx64krb5  | Sì  |
|Power BI Gateway     |DirectQuery | SSO tramite Kerberos per l'opzione query DirectQuery | Server messaggi | gsskrb5/gx64krb5  | No  |
|Power BI Gateway     |DirectQuery | SSO tramite Kerberos per l'opzione query DirectQuery | Server messaggi | sapcrypto  | Sì  |

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su SAP e DirectQuery, vedere le risorse seguenti:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery e SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
* [Origini dati di Power BI](desktop-directquery-data-sources.md)
* [White paper su Power BI e SAP BW](https://aka.ms/powerbiandsapbw)
