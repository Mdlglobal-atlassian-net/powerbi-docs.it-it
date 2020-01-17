---
title: Origini dati in Power BI Desktop
description: Origini dati in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: fd25e4ca6357dbfa5954eeabe0bf97fb6ccb8a1c
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761365"
---
# <a name="data-sources-in-power-bi-desktop"></a>Origini dati in Power BI Desktop

Power BI Desktop permette di connettersi a dati da molte origini diverse. Per un elenco completo delle origini dati disponibili, vedere [Origini dati di Power BI](power-bi-data-sources.md).

Per connettersi ai dati, selezionare **Recupera dati** dalla barra multifunzione **Home** . Se si seleziona la freccia Giù o il testo **Recupera dati** sul pulsante viene visualizzato il menu dei tipi di dati **Più comuni**, riportato nella figura seguente:

![Recupera dati in Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Se si sceglie **Altro** dal menu **Più comuni**, viene visualizzata la finestra **Recupera dati**. È anche possibile visualizzare la finestra **Recupera dati** (e ignorare il menu **Più comuni**) selezionando direttamente il **pulsante dell'icona** **Recupera dati**.

![Pulsante Recupera dati](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> Il team di Power BI espande in continuazione le origini dati disponibili in **Power BI Desktop** e nel **servizio Power BI**. Di conseguenza, si noteranno spesso le prime versioni delle origini dati WIP contrassegnate come *Beta* o *Anteprima*. Qualsiasi origine dati contrassegnata come *Beta* o *Anteprima* offre supporto e funzionalità limitati e non deve essere usata in ambienti di produzione. Inoltre, qualsiasi origine dati contrassegnata come *Beta* o *Preview* per **Power BI Desktop** potrebbe non essere disponibile per l'uso nel **servizio Power BI** o in altri servizi Microsoft finché l'origine dati non diventa disponibile a livello generale (GA).

> [!NOTE]
> Sono molti i connettori dati per Power BI Desktop che richiedono Internet Explorer 10 (o versione successiva) per l'autenticazione. 


## <a name="data-sources"></a>Origini dati
I tipi di dati sono organizzati nelle categorie seguenti:

* Tutti
* File
* Database
* Power BI
* Azure
* Servizi online
* Altro

La categoria **Tutti** include tutti i tipi di connessione dati di tutte le categorie.

La categoria **File** fornisce le connessioni dati seguenti:

* Excel
* Testo/CSV
* XML
* JSON
* Cartella
* PDF
* Cartella di SharePoint

La figura seguente mostra la finestra **Recupera dati** per **File**.

![Recupera dati > File](media/desktop-data-sources/data-sources-03.png)

La categoria **Database** fornisce le connessioni dati seguenti:

* Database SQL Server
* Database di Access
* Database di SQL Server Analysis Services
* Database Oracle
* Database IBM DB2
* Database Informix IBM (Beta)
* IBM Netezza
* Database MySQL
* Database PostgreSQL
* Database di Sybase
* Teradata
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
* Dremio
* Exasol
* Indexima (Beta)
* InterSystems IRIS (Beta)
* Jethro (beta)
* Kyligence Enterprise (Beta)
* MarkLogic (Beta)

> [!NOTE]
> Alcuni connettori di database devono essere abilitati selezionando **File > Opzioni e impostazioni > Opzioni** e quindi **Funzionalità in anteprima**. Se alcuni dei connettori citati sopra non sono visibili e si vuole usarli, controllare le impostazioni **Funzionalità in anteprima**. Si noti anche che qualsiasi origine dati contrassegnata come *Beta* o *Anteprima* offre supporto e funzionalità limitati e non deve essere usata in ambienti di produzione.

La figura seguente mostra la finestra **Recupera dati** per **Database**.

![Recupera dati > Database](media/desktop-data-sources/data-sources-04.png)

La categoria **Power Platform** fornisce le connessioni dati seguenti:

* Set di dati Power BI
* Flussi di dati Power BI
* Common Data Service
* Flussi di dati Power Platform

L'immagine seguente mostra la finestra **Recupera dati** per **Power Platform**.

![Recupera dati > Power BI](media/desktop-data-sources/data-sources-05.png)

La categoria **Azure** fornisce le connessioni dati seguenti:

* Database SQL di Azure
* Azure SQL Data Warehouse
* Database di Azure Analysis Services
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

![Recupera dati > Azure](media/desktop-data-sources/data-sources-06.png)

La categoria **Online Services** fornisce le connessioni dati seguenti:

* Elenchi SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (locale)
* Informazioni dettagliate sul consumo di Microsoft Azure (Beta)
* Azure DevOps (beta)
* Azure DevOps Server (beta)
* Oggetti Salesforce
* Report di Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* Data.World - Ottieni set di dati (Beta)
* Facebook
* GitHub (beta)
* MailChimp (Beta)
* Marketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One - PRM (Beta)
* Planview Projectplace (Beta)
* QuickBooks Online (beta)
* Smartsheet
* SparkPost (Beta)
* Stripe (Beta)
* SweetIQ (beta)
* Planview Enterprise One - CMT (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)
* Dynamics 365 Customer Insights (Beta)
* Origine dati Emigo (Beta)
* Entersoft Business Suite (Beta)
* Industrial App Store
* Data warehouse di Intune (Beta)
* Microsoft Graph Security (Beta)
* Quick Base
* TeamDesk (beta)


La figura seguente mostra la finestra **Recupera dati** per **Online Services**.

![Recupera dati > Servizi online](media/desktop-data-sources/data-sources-07.png)

La categoria **Altro** fornisce le connessioni dati seguenti:

* Web
* Elenco SharePoint
* Feed OData
* Active Directory
* Microsoft Exchange
* File Hadoop (HDFS)
* Spark
* Script R
* Script Python
* ODBC
* OLE DB
* BI360 - Budgeting & Financial Reporting (Beta)
* Denodo
* Information Grid (Beta)
* Paxata 
* QubolePresto (Beta)
* Roamler (Beta)
* SurveyMonkey (Beta)
* Tenforce (Smart)List (Beta)
* Workforce Dimensions (Beta)
* Query vuota

La figura seguente mostra la finestra **Recupera dati** per **Altro**.

![Recupera dati > Altro](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> Al momento non è possibile connettersi a origini dati personalizzate protette con Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Connessione a un'origine dati
Per connettersi a un'origine dati, selezionare l'origine dati dalla finestra **Recupera dati** e selezionare **Connetti**. Nella figura seguente **Web** viene selezionato dalla categoria di connessione dati **Altro** .

![Connettersi al Web](media/desktop-data-sources/data-sources-08.png)

Viene visualizzata una finestra di connessione specifica per il tipo di connessione dati. Se sono necessarie credenziali, sarà necessario fornirle. L'immagine seguente illustrata un URL immesso per connettersi a un'origine dati Web.

![Immettere un URL Web](media/desktop-data-sources/datasources-fromwebbox.png)

Quando viene immesso l'URL o le informazioni di connessione alla risorsa, selezionare **OK**. Power BI Desktop stabilisce la connessione all'origine dati e presenta le origini dati disponibili nello **Strumento di navigazione**.

![Schermata Strumento di navigazione](media/desktop-data-sources/datasources-fromnavigatordialog.png)

È possibile caricare i dati selezionando il pulsante **Carica** nella parte inferiore del riquadro **Strumento di navigazione** oppure modificare la query prima di caricare i dati selezionando il pulsante **Modifica** .

Non sono necessarie altre operazioni per connettersi alle origini dati in Power BI Desktop. Provare a connettersi ai dati dall'elenco di origini dati in continua espansione ed esaminare spesso l'elenco, che viene continuamente ampliato.

## <a name="using-pbids-files-to-get-data"></a>Uso di file PBIDS per ottenere i dati

I file PBIDS sono file di Power BI Desktop con una struttura specifica, identificati come file di origine dati di Power BI dall'estensione PBIDS.

È possibile creare un file con estensione PBIDS per semplificare l'esperienza di **recupero dei dati**  per gli autori di report all'interno dell'organizzazione. Si consiglia agli amministratori di creare file di questo tipo per le connessioni di uso comune, per facilitare l'uso dei file PBIDS per gli autori di nuovi report. 

Quando un autore apre un file PBIDS, Power BI Desktop si apre e chiede le credenziali dell'utente per l'autenticazione e la connessione all'origine dati specificata nel file. Viene visualizzata la finestra di dialogo di spostamento e l'utente deve selezionare le tabelle dell'origine dati da caricare nel modello. È anche possibile che gli utenti debbano selezionare uno o più database, se non ne è stato specificato alcuno nel file con estensione PBIDS. 

A questo punto, l'utente può iniziare a creare visualizzazioni o rivedere *Origini recenti* per caricare un nuovo set di tabelle nel modello. 

I file con estensione PBIDS attualmente supportano un'unica origine dati in un singolo file. Se si specificano più origini dati, si ottiene come risultato un errore. 

Per creare il file con estensione PBIDS, gli amministratori devono specificare gli input necessari per un'unica connessione e possono indicare la modalità di connessione, **DirectQuery** o **Import**. Se **mode** è mancante o Null nel file, all'utente che apre il file in Power BI Desktop viene richiesto di selezionare DirectQuery o Import. 

### <a name="pbids-file-examples"></a>Esempi di file PBIDS

Questa sezione offre alcuni esempi relativi a origini dati di uso comune. Il tipo di file PBIDS supporta solo connessioni dati supportate anche in Power BI Desktop, con due eccezioni: Live Connect e query vuote. 

Il file con estensione PBIDS *non* include le informazioni di autenticazione né le informazioni sullo schema e sulla tabella.  

Di seguito sono riportati alcuni esempi comuni di file con estensione PBIDS. Tali esempi non sono completi né esaustivi. Per altre origini dati, è possibile fare riferimento al [formato DSR (Data Source Reference) per le informazioni relative al protocollo e all'indirizzo](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification).

Questi esempi hanno solo uno scopo pratico, non sono intesi come esaustivi e non includono tutti i connettori supportati nel formato DSR. Gli amministratori e le organizzazioni possono creare origini dati personalizzate usando questi esempi come guide da cui trarre supporto. 


**Azure AS**
```
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


 

**Cartella**
```
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

**OData**
```
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
 
**SAP BW**
```
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
 
**SAP Hana**
```
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

**Elenco SharePoint**

L'URL deve puntare al sito SharePoint e non a un elenco all'interno del sito. Gli utenti ottengono uno strumento di navigazione che consente di selezionare uno o più elenchi da tale sito, ognuno dei quali diventa una tabella nel modello. 
```
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
 
 
**SQL Server**
```
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
 

**File di testo**
```
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
 

**Web**
```
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
 

**Flusso di dati**
```
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
