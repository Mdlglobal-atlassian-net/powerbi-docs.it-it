---
title: Origini dati in Power BI Desktop
description: Origini dati in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: fa0686171ee6f9e171e69d60f804d8e141530103
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79207253"
---
# <a name="data-sources-in-power-bi-desktop"></a>Origini dati in Power BI Desktop

Power BI Desktop permette di connettersi a dati da molte origini diverse. Per un elenco completo delle origini dati disponibili, vedere [Origini dati di Power BI](power-bi-data-sources.md).

Per connettersi ai dati è possibile usare la barra multifunzione **Home**. Per visualizzare il menu **Più comuni** per i tipi di dati, selezionare l'etichetta del pulsante **Recupera dati** o la freccia a discesa.

![Menu dei tipi di dati Più comuni, Recupera dati in Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Per passare alla finestra di dialogo **Recupera dati** visualizzare il menu dei tipi di dati **Più comuni** e selezionare **Altro**. È anche possibile visualizzare la finestra di dialogo **Recupera dati** (e ignorare il menu **Più comuni**) selezionando direttamente l'icona **Recupera dati**.

![Pulsante Recupera dati, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> Il team di Power BI espande in continuazione le origini dati disponibili in Power BI Desktop e nel servizio Power BI. Di conseguenza, si noteranno spesso le prime versioni delle origini dati WIP contrassegnate come **Beta** o **Anteprima**. Qualsiasi origine dati contrassegnata come **Beta** o **Anteprima** offre supporto e funzionalità limitati e non deve essere usata in ambienti di produzione. Inoltre qualsiasi origine dati contrassegnata come **Beta** o **Anteprima** per Power BI Desktop potrebbe non essere disponibile per l'uso nel servizio Power BI o in altri servizi Microsoft fino a quando l'origine dati non diventa disponibile a livello generale (GA).

> [!NOTE]
> Ci sono molti connettori dati per Power BI Desktop che richiedono Internet Explorer 10 (o versione successiva) per l'autenticazione. 


## <a name="data-sources"></a>Origini dati

La finestra di dialogo **Recupera dati** organizza i tipi di dati nelle categorie seguenti:

* Tutti
* File
* Database
* Power Platform
* Azure
* Servizi online
* Altri

La categoria **Tutti** include tutti i tipi di connessione dati di tutte le categorie.

### <a name="file-data-sources"></a>Origini dati di file

La categoria **File** fornisce le connessioni dati seguenti:

* Excel
* Testo/CSV
* XML
* JSON
* Cartella
* PDF
* Cartella di SharePoint

La figura seguente mostra la finestra **Recupera dati** per **File**.

![Origini dati di file, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Origini dati dei database relazionali

La categoria **Database** fornisce le connessioni dati seguenti:

* Database SQL Server
* Database di Access
* Database di SQL Server Analysis Services
* Oracle Database
* Database IBM DB2
* Database Informix IBM (Beta)
* IBM Netezza
* Database MySQL
* Database PostgreSQL
* Database Sybase
* Database Teradata
* Database SAP HANA
* Server applicazioni SAP Business Warehouse
* Server messaggi SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* Cubi AtScale
* Connettore BI 
* Data Virtuality LDW (beta)
* Denodo
* Dremio
* Exasol
* Indexima (Beta)
* InterSystems IRIS (Beta)
* Jethro (beta)
* Kyligence
* MarkLogic

> [!NOTE]
> Alcuni connettori di database devono essere abilitati selezionando **File > Opzioni e impostazioni > Opzioni** e quindi **Funzionalità in anteprima**. Se alcuni dei connettori citati sopra non sono visibili e si vuole usarli, controllare le impostazioni **Funzionalità in anteprima**. Si noti anche che qualsiasi origine dati contrassegnata come *Beta* o *Anteprima* offre supporto e funzionalità limitati e non deve essere usata in ambienti di produzione.

La figura seguente mostra la finestra **Recupera dati** per **Database**.

![Origini dati di database, finestra di dialogo Ottieni dati, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Origini dati Power Platform

La categoria **Power Platform** fornisce le connessioni dati seguenti:

* Set di dati Power BI
* Flussi di dati Power BI
* Common Data Service
* Flussi di dati Power Platform

L'immagine seguente mostra la finestra **Recupera dati** per **Power Platform**.

![Origini dati Power Platform, finestra di dialogo Ottieni dati, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Origini dati di Azure

La categoria **Azure** fornisce le connessioni dati seguenti:

* database SQL di Azure
* Azure SQL Data Warehouse
* Database di Azure Analysis Services
* Database di Azure per PostgreSQL
* Archiviazione BLOB di Azure
* Archiviazione tabelle di Azure
* Azure Cosmos DB
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Esplora dati di Azure (Kusto)
* Gestione costi di Azure
* Azure Time Series Insights (Beta)

La figura seguente mostra la finestra **Recupera dati** per **Azure**.

![Origini dati Azure, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Origini dati di Servizi online

La categoria **Online Services** fornisce le connessioni dati seguenti:

* Elenchi SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (locale)
* Informazioni dettagliate sul consumo di Microsoft Azure (Beta)
* Azure DevOps (solo Boards)
* Azure DevOps Server (solo Boards)
* Oggetti Salesforce
* Report di Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* Data.World - Ottieni set di dati (Beta)
* GitHub (beta)
* LinkedIn Sales Navigator (Beta)
* Marketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One - PRM (Beta)
* Planview Projectplace (Beta)
* QuickBooks Online (beta)
* Smartsheet
* SparkPost (Beta)
* SweetIQ (beta)
* Planview Enterprise One - CTM (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)
* Asana (beta)
* Dynamics 365 Customer Insights (Beta)
* Origine dati Emigo
* Entersoft Business Suite (Beta)
* FactSet Analytics (Beta)
* Industrial App Store
* Data warehouse di Intune (Beta)
* Microsoft Graph Security (Beta)
* Product Insights (Beta)
* Quick Base
* TeamDesk (beta)
* Workplace Analytics (Beta)

La figura seguente mostra la finestra **Recupera dati** per **Online Services**.

![Origini dati di Servizi online, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Altre origini dati

La categoria **Altro** fornisce le connessioni dati seguenti:

* Web
* Elenco SharePoint
* Feed OData
* Active Directory
* Microsoft Exchange
* File Hadoop (HDFS)
* Spark
* Hive LLAP (Beta)
* Script R
* Script Python
* ODBC
* OLE DB
* BI360 - Budgeting & Financial Reporting (Beta)
* FHIR
* Information Grid (Beta)
* Jamf Pro (Beta)
* MicroStrategy for Power BI
* Paxata
* QubolePresto (Beta)
* Roamler (Beta)
* Siteimprove (beta)
* SurveyMonkey (Beta)
* Tenforce (Smart)List (Beta)
* TIBCO(R) Data Virtualization (Beta)
* Vena (beta)
* Workforce Dimensions (Beta)
* Zucchetti HR Infinity (Beta)
* Query vuota

La figura seguente mostra la finestra **Recupera dati** per **Altro**.

![Altre origini dati, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> Al momento non è possibile connettersi a origini dati personalizzate protette con Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Connessione a un'origine dati

Per connettersi a un'origine dati, selezionare l'origine dati dalla finestra **Recupera dati** e selezionare **Connetti**. Nella figura seguente **Web** viene selezionato dalla categoria di connessione dati **Altro** .

![Connessione al Web, finestra di dialogo Recupera dati, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

Viene visualizzata una finestra di connessione specifica per il tipo di connessione dati. Se sono necessarie credenziali, sarà necessario fornirle. L'immagine seguente illustrata un URL immesso per connettersi a un'origine dati Web.

![URL immesso, Finestra di dialogo Da Web, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Immettere l'URL o le informazioni di connessione alla risorsa e selezionare **OK**. Power BI Desktop stabilisce la connessione all'origine dati e presenta le origini dati disponibili nello **Strumento di navigazione**.

![Finestra di dialogo Strumento di navigazione, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Per caricare i dati, selezionare il pulsante **Carica** nella parte inferiore del riquadro **Strumento di navigazione**. Per trasformare o modificare la query nell'editor di Power Query prima di caricare i dati, selezionare il pulsante **Trasforma dati**.

Non sono necessarie altre operazioni per connettersi alle origini dati in Power BI Desktop. Provare a connettersi ai dati dall'elenco di origini dati in continua espansione ed esaminare spesso l'elenco, che viene continuamente ampliato.

## <a name="using-pbids-files-to-get-data"></a>Uso di file PBIDS per ottenere i dati

I file con estensione pbids sono file di Power BI Desktop con una struttura specifica e l'estensione li identifica come file origine dati di Power BI.

È possibile creare un file con estensione pbids per semplificare l'esperienza di **recupero dei dati** per gli autori di report all'interno dell'organizzazione. Per semplificare l'uso dei file con estensione pbids da parte di un nuovo autore di report, è consigliabile che un amministratore crei questi file per le connessioni usate di frequente.

Quando un autore apre un file con estensione pbids, Power BI Desktop si apre e chiede le credenziali dell'utente per l'autenticazione e la connessione all'origine dati specificata nel file. Viene visualizzata la finestra di dialogo **Navigazione** e l'utente deve selezionare le tabelle dell'origine dati da caricare nel modello. È anche possibile che gli utenti debbano selezionare uno o più database, se non ne è stato specificato nessuno nel file con estensione pbids.

A questo punto l'utente può iniziare a creare visualizzazioni oppure selezionare **Origini recenti** per caricare un nuovo set di tabelle nel modello.

I file con estensione pbids attualmente supportano un'unica origine dati in un singolo file. Se si specificano più origini dati, si ottiene come risultato un errore.

Per creare il file con estensione pbids, un amministratore deve specificare gli input necessari per una singola connessione. Può anche specificare la modalità di connessione come DirectQuery o Import. Se **mode** è mancante o Null nel file, all'utente che apre il file in Power BI Desktop viene chiesto di selezionare **DirectQuery** o **Import**.

### <a name="pbids-file-examples"></a>Esempi di file PBIDS

Questa sezione offre alcuni esempi relativi a origini dati di uso comune. Il tipo di file pbids supporta solo connessioni dati supportate anche in Power BI Desktop, con due eccezioni: Live Connect e le query vuote.

Il file con estensione pbids *non* include le informazioni di autenticazione né le informazioni sulla tabella e sullo schema.  

I frammenti di codice seguenti visualizzano esempi comuni di file con estensione pbids. Questi esempi non sono completi né esaustivi. Per altre origini dati, è possibile fare riferimento al [formato DSR (Data Source Reference) per le informazioni relative al protocollo e all'indirizzo](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification).

Questi esempi hanno solo uno scopo pratico, non sono intesi come esaustivi e non includono tutti i connettori supportati nel formato DSR. Un amministratore o un'organizzazione può creare origini dati personalizzate usando questi esempi come guide per la creazione e il supporto.

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>Cartella

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>Elenco SharePoint

L'URL deve puntare al sito SharePoint e non a un elenco all'interno del sito. Gli utenti ottengono uno strumento di navigazione che consente di selezionare uno o più elenchi da tale sito, ognuno dei quali diventa una tabella nel modello.

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>File di testo

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>Flusso di dati

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Passaggi successivi

Power BI Desktop offre infinite possibilità. Per altre informazioni sulle capacità disponibili, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Tipi di dati in Power BI Desktop](desktop-data-types.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)
