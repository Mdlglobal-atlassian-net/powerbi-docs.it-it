---
title: Origini dati in Power BI Desktop
description: Origini dati in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f5fc52df86faa69683fa1e76f8893fb1d1a09ab9
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281161"
---
# <a name="data-sources-in-power-bi-desktop"></a>Origini dati in Power BI Desktop
Power BI Desktop permette di connettersi a dati da molte origini diverse. Un elenco completo delle origini dati disponibili è riportato alla fine di questa pagina.

Per connettersi ai dati, selezionare **Recupera dati** dalla barra multifunzione **Home** . Se si seleziona la freccia Giù o il testo **Recupera dati** sul pulsante viene visualizzato il menu dei tipi di dati **Più comuni**, riportato nella figura seguente:

![Recupera dati in Power BI Desktop](media/desktop-data-sources/data-sources_01.png)

Se si sceglie **Altro** dal menu **Più comuni**, viene visualizzata la finestra **Recupera dati**. È anche possibile visualizzare la finestra **Recupera dati** (e ignorare il menu **Più comuni** ) selezionando direttamente il **pulsante dell'icona** **Recupera dati** .

![Pulsante Recupera dati](media/desktop-data-sources/data-sources_02.png)

> [!NOTE]
> Il team di Power BI espande in continuazione le origini dati disponibili in **Power BI Desktop** e nel **servizio Power BI**. Di conseguenza, si noteranno spesso le prime versioni delle origini dati WIP contrassegnate come *Beta* o *Anteprima*. Qualsiasi origine dati contrassegnata come *Beta* o *Anteprima* offre supporto e funzionalità limitati e non deve essere usata in ambienti di produzione.

## <a name="data-sources"></a>Origini dati
I tipi di dati sono organizzati nelle categorie seguenti:

* Tutti
* File
* Database
* Power BI
* Azure
* Online Services
* Altro

La categoria **Tutti** include tutti i tipi di connessione dati di tutte le categorie.

La categoria **File** fornisce le connessioni dati seguenti:

* Excel
* Testo/CSV
* XML
* JSON
* Cartella
* PDF (Beta)
* Cartella di SharePoint

La figura seguente mostra la finestra **Recupera dati** per **File**.

![Recupera dati > File](media/desktop-data-sources/data-sources_03.png)

La categoria **Database** fornisce le connessioni dati seguenti:

* Database SQL Server
* Database di Access
* SQL Server Analysis Services
* Database Oracle
* Database IBM DB2
* Database Informix IBM (Beta)
* IBM Netezza
* Database MySQL
* Database PostgreSQL
* Database di Sybase
* Database Teradata
* Database SAP HANA
* Server applicazioni SAP Business Warehouse
* Server messaggi SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Snowflake
* Essbase (Beta)
* Connettore BI
* Exasol
* Dremio (Beta)
* Jethro (beta)
* Kyligence Enterprise (Beta)

> [!NOTE]
> Alcuni connettori di database devono essere abilitati selezionando **File > Opzioni e impostazioni > Opzioni** e quindi **Funzionalità in anteprima**. Se alcuni dei connettori citati sopra non sono visibili e si vuole usarli, controllare le impostazioni **Funzionalità in anteprima**. Si noti anche che qualsiasi origine dati contrassegnata come *Beta* o *Anteprima* offre supporto e funzionalità limitati e non deve essere usata in ambienti di produzione.

La figura seguente mostra la finestra **Recupera dati** per **Database**.

![Recupera dati > Database](media/desktop-data-sources/data-sources_04.png)

La categoria **Power BI** fornisce le connessioni dati seguenti:

* Set di dati Power BI
* Flussi di dati Power BI (beta)

La figura seguente mostra la finestra **Recupera dati** per **Power BI**.

![Recupera dati > Power BI](media/desktop-data-sources/data-sources_05.png)

La categoria **Azure** fornisce le connessioni dati seguenti:

* Database SQL di Azure
* Azure SQL Data Warehouse
* Database di Azure Analysis Services
* Archiviazione BLOB di Azure
* Archiviazione tabelle di Azure
* Azure Cosmos DB (Beta)
* Azure Data Lake Storage
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Esplora dati di Azure (beta)

La figura seguente mostra la finestra **Recupera dati** per **Azure**.

![Recupera dati > Azure](media/desktop-data-sources/data-sources_06.png)

La categoria **Online Services** fornisce le connessioni dati seguenti:

* Elenchi SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (locale)
* Common Data Service per le app (beta)
* Informazioni dettagliate sul consumo di Microsoft Azure (beta)
* Azure DevOps (beta)
* Azure DevOps Server (beta)
* Oggetti Salesforce
* Report di Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* comScore Digital Analytix (Beta)
* Dynamics 365 per Customer Insights (Beta)
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
* TeamDesk (beta)

La figura seguente mostra la finestra **Recupera dati** per **Online Services**.

![Recupera dati > Servizi online](media/desktop-data-sources/data-sources_07.png)

La categoria **Altro** fornisce le connessioni dati seguenti:

* Vertica
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
* Denado
* Paxata (Beta)
* Query vuota

La figura seguente mostra la finestra **Recupera dati** per **Altro**.

![Recupera dati > Altro](media/desktop-data-sources/data-sources_08.png)

> [!NOTE]
> Al momento non è possibile connettersi a origini dati personalizzate protette con Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Connessione a un'origine dati
Per connettersi a un'origine dati, selezionare l'origine dati dalla finestra **Recupera dati** e selezionare **Connetti**. Nella figura seguente **Web** viene selezionato dalla categoria di connessione dati **Altro** .

![Connettersi al Web](media/desktop-data-sources/data-sources_08a.png)

Viene visualizzata una finestra di connessione specifica per il tipo di connessione dati. Se sono necessarie credenziali, sarà necessario fornirle. L'immagine seguente illustrata un URL immesso per connettersi a un'origine dati Web.

![Immettere un URL Web](media/desktop-data-sources/datasources_fromwebbox.png)

Quando viene immesso l'URL o le informazioni di connessione alla risorsa, selezionare **OK**. Power BI Desktop stabilisce la connessione all'origine dati e presenta le origini dati disponibili nello **Strumento di navigazione**.

![Schermata Strumento di navigazione](media/desktop-data-sources/datasources_fromnavigatordialog.png)

È possibile caricare i dati selezionando il pulsante **Carica** nella parte inferiore del riquadro **Strumento di navigazione** oppure modificare la query prima di caricare i dati selezionando il pulsante **Modifica** .

Non sono necessarie altre operazioni per connettersi alle origini dati in Power BI Desktop. Provare a connettersi ai dati dall'elenco di origini dati in continua espansione ed esaminare spesso l'elenco, che viene continuamente ampliato.

## <a name="next-steps"></a>Passaggi successivi
Power BI Desktop offre infinite possibilità. Per altre informazioni sulle capacità disponibili, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](desktop-query-overview.md)
* [Tipi di dati in Power BI Desktop](desktop-data-types.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md)    
