---
title: Origini dati dei report di Power BI nel server di report di Power BI
description: I report di Power BI possono connettersi a numerose origini dati. A seconda di come vengono usati i dati, sono disponibili diverse origini dati.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: maggies
ms.openlocfilehash: 166f72a717c99457e1d6b8e9a1f30535a9b4686f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80979846"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origini dati dei report di Power BI nel server di report di Power BI
I report di Power BI possono connettersi a numerose origini dati. A seconda di come vengono usati i dati, sono disponibili diverse origini dati. I dati possono essere importati oppure è possibile eseguire una query direttamente sui dati tramite DirectQuery o una connessione in tempo reale a SQL Server Analysis Services.

Queste origini dati sono specifiche dei report di Power BI usati nel server di report di Power BI. Per informazioni sulle origini dati supportate con i report impaginati (con estensione rdl), vedere [Origini dati supportate da Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Tutte le origini dati in un report di Power BI Desktop devono supportare la configurazione di aggiornamenti pianificati.
>  

## <a name="list-of-supported-data-sources"></a>Elenco di origini dati supportate

Altre origini dati potrebbero funzionare anche se non sono presenti nell'elenco di origini dati supportate.

| **Origine dati** | **Dati memorizzati nella cache** | **Aggiornamento pianificato** | **Dinamico/DirectQuery** |
| --- | --- | --- | --- |
| Database SQL Server |Yes |Yes |Yes |
| SQL Server Analysis Services |Yes |Yes |Yes |
| Database SQL di Azure |Yes |Yes |Yes |
| Azure SQL Data Warehouse |Yes |Yes |Yes |
| Excel |Yes |Yes |No |
| Database di Access |Yes |Yes |No |
| Active Directory |Yes |Yes |No |
| Amazon Redshift |Yes |No |No |
| Archivio BLOB Azure |Yes |Yes |No |
| Azure Data Lake Store |Yes |No |No |
| Azure HDInsight (HDFS) |Yes |No |No |
| Azure HDInsight (Spark) |Yes |No |No |
| Archivio tabelle Azure |Yes |Yes |No |
| Dynamics 365 (online) |Yes |No |No |
| Facebook |Yes |No |No |
| Cartella |Yes |Yes |No |
| Google Analytics |Yes |No |No |
| File Hadoop (HDFS) |Yes |No |No |
| Database IBM DB2 |Yes |Yes |No |
| Impala |Yes |No |No |
| JSON |Yes |Yes |No |
| Microsoft Exchange |Yes |No |No |
| Microsoft Exchange Online |Yes |No |No |
| Database MySQL |Yes |Yes |No |
| Feed OData |Yes |Yes |No |
| ODBC |Yes |Yes |No |
| OLE DB |Yes |Yes |No |
| Database Oracle |Yes |Yes |Yes |
| Database PostgreSQL |Yes |Yes |No |
| servizio Power BI |No |No |No |
| Script R |Yes |No |No |
| Oggetti Salesforce |Yes |No |No |
| Report di Salesforce |Yes |No |No |
| Server SAP Business Warehouse |Yes |Yes |Yes |
| Database SAP HANA |Yes |Yes |Yes |
| Cartella di SharePoint (locale) |Yes |Yes |No |
| Elenco di SharePoint (locale) |Yes |Yes |No |
| Elenchi SharePoint Online |Yes |No |No |
| Snowflake |Yes |No |No |
| Database di Sybase |Yes |Yes |No |
| Teradata |Yes |Yes |Yes |
| Testo/CSV |Yes |Yes |No |
| Web |Yes |Yes |No |
| XML |Yes |Yes |No |
| appFigures (beta) |Yes |No |No |
| Database di Azure Analysis Services |Yes |No |Yes |
| Azure Cosmos DB (Beta) |Yes |No |No |
| Spark in Azure HDInsight (Beta) |Yes |No |No |
| Common Data Service (Beta) |Yes |No |No |
| comScore Digital Analytix (Beta) |Yes |No |No |
| Dynamics 365 per Customer Insights (Beta) |Yes |No |No |
| Dynamics 365 per Financials (Beta) |Yes |No |No |
| GitHub (beta) |Yes |No |No |
| Google BigQuery (Beta) |Yes |No |No |
| Database Informix IBM (Beta) |Yes |No |No |
| IBM Netezza (Beta) |Yes |No |No |
| Kusto (Beta) |Yes |No |No |
| MailChimp (Beta) |Yes |No |No |
| Informazioni dettagliate sul consumo di Microsoft Azure (beta) |Yes |No |No |
| Mixpanel (Beta) |Yes |No |No |
| Planview Enterprise (Beta) |Yes |No |No |
| Projectplace (Beta) |Yes |No |No |
| QuickBooks Online (beta) |Yes |No |No |
| Smartsheet |Yes |No |No |
| Spark (Beta) |Yes |No |No |
| SparkPost (Beta) |Yes |No |No |
| SQL Sentry (Beta) |Yes |No |No |
| Stripe (Beta) |Yes |No |No |
| SweetIQ (beta) |Yes |No |No |
| Troux (Beta) |Yes |No |No |
| Twilio (Beta) |Yes |No |No |
| tyGraph (Beta) |Yes |No |No |
| Vertica (Beta) |Yes |No |No |
| Visual Studio Team Services (Beta) |Yes |No |No |
| Webtrends (Beta) |Yes |No |No |
| Zendesk (Beta) |Yes |No |No |

> [!IMPORTANT]
> La sicurezza a livello di riga configurata per l'origine dati funziona per determinate connessioni DirectQuery (SQL Server, database SQL di Azure, Oracle e Teradata) e connessioni in tempo reale, purché l'autenticazione Kerberos sia configurata correttamente nell'ambiente in uso.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Elenco di metodi di autenticazione supportati per l'aggiornamento dei modelli

Il server di report di Microsoft Power BI non supporta l'autenticazione basata su OAuth per l'aggiornamento dei modelli. Alcune origini dati, ad esempio Excel o i database di Access, per connettersi ai dati usano un passaggio separato, ad esempio File o Web.

| **Origine dati** | **Autenticazione anonima** | **Autenticazione con chiave** | **Nome utente e password** | **Autenticazione di Windows** |
| --- | --- | --- | --- | --- |
| Database SQL Server |No |No |Yes |Yes |
| SQL Server Analysis Services |No |No |Yes |Yes |
| Web |Yes |No |Yes |Yes |
| Database SQL di Azure |No |No |Yes |No |
| Azure SQL Data Warehouse |No |No |Yes |No |
| Active Directory |No |No |Yes |Yes |
| Amazon Redshift |No |No |No |No |
| Archivio BLOB Azure |Yes |Yes |No |No |
| Azure Data Lake Store |No |No |No |No |
| Azure HDInsight (HDFS) |No |No |No |No |
| Azure HDInsight (Spark) |No |No |No |No |
| Archivio tabelle Azure |No |Yes |No |No |
| Dynamics 365 (online) |No |No |No |No |
| Facebook |No |No |No |No |
| Cartella |No |No |No |Yes |
| Google Analytics |No |No |No |No |
| File Hadoop (HDFS) |No |No |No |No |
| Database IBM DB2 |No |No |Yes |Yes |
| Impala |No |No |No |No |
| Microsoft Exchange |No |No |No |No |
| Microsoft Exchange Online |No |No |No |No |
| Database MySQL |No |No |Yes |Yes |
| Feed OData |Yes |Yes |Yes |Yes |
| ODBC |Yes |No |Yes |Yes |
| OLE DB |Yes |No |Yes |Yes |
| Database Oracle |No |No |Yes |Yes |
| Database PostgreSQL |No |No |Yes |No |
| servizio Power BI |No |No |No |No |
| Script R |No |No |No |No |
| Oggetti Salesforce |No |No |No |No |
| Report di Salesforce |No |No |No |No |
| Server SAP Business Warehouse |No |No |Yes |No |
| Database SAP HANA |No |No |Yes |Yes |
| Cartella di SharePoint (locale) |Yes |No |No |Yes |
| Elenco di SharePoint (locale) |Yes |No |No |Yes |
| Elenchi SharePoint Online |No |No |No |No |
| Snowflake |No |No |No |No |
| Database di Sybase |No |No |Yes |Yes |
| Teradata |No |No |Yes |Sì** |
| appFigures (beta) |No |No |No |No |
| Database di Azure Analysis Services (Beta) |No |No |No |No |
| Azure Cosmos DB (Beta) |No |No |No |No |
| Spark in Azure HDInsight (Beta) |No |No |No |No |
| Common Data Service (Beta) |No |No |No |No |
| comScore Digital Analytix (Beta) |No |No |No |No |
| Dynamics 365 per Customer Insights (Beta) |No |No |No |No |
| Dynamics 365 per Financials (Beta) |No |No |No |No |
| GitHub (beta) |No |No |No |No |
| Google BigQuery (Beta) |No |No |No |No |
| Database Informix IBM (Beta) |No |No |No |No |
| IBM Netezza (Beta) |No |No |No |No |
| Kusto (Beta) |No |No |No |No |
| MailChimp (Beta) |No |No |No |No |
| Informazioni dettagliate sul consumo di Microsoft Azure (beta) |No |No |No |No |
| Mixpanel (Beta) |No |No |No |No |
| Planview Enterprise (Beta) |No |No |No |No |
| Projectplace (Beta) |No |No |No |No |
| QuickBooks Online (beta) |No |No |No |No |
| Smartsheet |No |No |No |No |
| Spark (Beta) |No |No |No |No |
| SparkPost (Beta) |No |No |No |No |
| SQL Sentry (Beta) |No |No |No |No |
| Stripe (Beta) |No |No |No |No |
| SweetIQ (beta) |No |No |No |No |
| Troux (Beta) |No |No |No |No |
| Twilio (Beta) |No |No |No |No |
| tyGraph (Beta) |No |No |No |No |
| Vertica (Beta) |No |No |No |No |
| Visual Studio Team Services (Beta) |No |No |No |No |
| Webtrends (Beta) |No |No |No |No |
| Zendesk (Beta) |No |No |No |No |

**L'uso dell'autenticazione LDAP con Teradata (abilitato in Power BI Desktop tramite il comando del prompt dei comandi 'setx PBI_EnableTeradataLdap true') non è supportato per l'aggiornamento del modello.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Elenco di metodi di autenticazione supportati per DirectQuery

Il server di report di Microsoft Power BI non supporta l'autenticazione basata su OAuth per DirectQuery.

| **Origine dati** | **Autenticazione anonima** | **Autenticazione con chiave** | **Nome utente e password** | **Autenticazione di Windows** | **Autenticazione di Windows integrata** |
| --- | --- | --- | --- | --- | --- |
| Database SQL Server |No |No |Yes |Yes |Yes |
| SQL Server Analysis Services |No |No |Yes |Yes |Yes |
| Database SQL di Azure |No |No |Yes |No |No |
| Azure SQL Data Warehouse |No |No |Yes |No |No |
| Database Oracle |No |No |Yes |Yes |Yes |
| Server SAP Business Warehouse |No |No |Yes |No |No |
| Database SAP HANA |No |No |Yes |Yes |Sì** |
| Teradata |No |No |Yes |Yes |Yes |

**SAP HANA supporta DirectQuery con Autenticazione integrata di Windows solo se usato come database relazionale nel file di Power BI Desktop pubblicato (PBIX).

## <a name="next-steps"></a>Passaggi successivi
Dopo essersi connessi all'origine dati, [creare un report di Power BI](quickstart-create-powerbi-report.md) con i dati di questa origine dati.

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
