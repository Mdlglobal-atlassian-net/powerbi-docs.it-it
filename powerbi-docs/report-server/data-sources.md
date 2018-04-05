---
title: Origini dati dei report di Power BI nel server di report di Power BI
description: I report di Power BI possono connettersi a varie origini dati. A seconda di come vengono usati i dati, sono disponibili diverse origini dati.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/02/2018
ms.author: maghan
ms.openlocfilehash: bc490834b215af45df1063fd06b94ed9b735d852
ms.sourcegitcommit: 8132f7edc6879eda824c900ba90b29cb6b8e3b21
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Origini dati dei report di Power BI nel server di report di Power BI
I report di Power BI possono connettersi a varie origini dati. A seconda di come vengono usati i dati, sono disponibili diverse origini dati. I dati possono essere importati oppure è possibile eseguire una query direttamente sui dati tramite DirectQuery o una connessione in tempo reale a SQL Server Analysis Services.

Queste origini dati sono specifiche dei report di Power BI usati nel server di report di Power BI. Per informazioni sulle origini dati supportate con i report impaginati, vedere [Origini dati supportate da Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Per configurare un aggiornamento pianificato, è necessario che tutte le origini dati in un report di Power BI Desktop siano supportate.
> 
> 

## <a name="list-of-supported-data-sources"></a>Elenco di origini dati supportate

Altre origini dati potrebbero funzionare anche se non sono presenti nell'elenco di origini dati supportate.

| **Origine dati** | **Dati memorizzati nella cache** | **Aggiornamento pianificato** | **Dinamico/DirectQuery** |
| --- | --- | --- | --- |
| Database SQL Server |Sì |Sì |Sì |
| SQL Server Analysis Services |Sì |Sì |Sì |
| Database SQL di Azure |Sì |Sì |Sì |
| Azure SQL Data Warehouse |Sì |Sì |Sì |
| Excel |Sì |Sì |No |
| Database di Access |Sì |Sì |No |
| Active Directory |Sì |Sì |No |
| Amazon Redshift |Sì |No |No |
| Archivio BLOB Azure |Sì |Sì |No |
| Azure Data Lake Store |Sì |No |No |
| Azure HDInsight (HDFS) |Sì |No |No |
| Azure HDInsight (Spark) |Sì |Sì |No |
| Archivio tabelle Azure |Sì |Sì |No |
| Dynamics 365 (online) |Sì |No |No |
| Facebook |Sì |No |No |
| Cartella |Sì |Sì |No |
| Google Analytics |Sì |No |No |
| File Hadoop (HDFS) |Sì |No |No |
| Database IBM DB2 |Sì |Sì |No |
| Impala |Sì |No |No |
| JSON |Sì |Sì |No |
| Microsoft Exchange |Sì |No |No |
| Microsoft Exchange Online |Sì |No |No |
| Database MySQL |Sì |Sì |No |
| Feed OData |Sì |Sì |No |
| ODBC |Sì |Sì |No |
| OLE DB |Sì |Sì |No |
| Database Oracle |Sì |Sì |Sì |
| Database PostgreSQL |Sì |Sì |No |
| Servizio Power BI |No |No |No |
| Script R |Sì |No |No |
| Oggetti Salesforce |Sì |No |No |
| Report di Salesforce |Sì |No |No |
| Server SAP Business Warehouse |Sì |Sì |Sì |
| Database SAP HANA |Sì |Sì |Sì |
| Cartella di SharePoint (locale) |Sì |Sì |No |
| Elenco di SharePoint (locale) |Sì |Sì |No |
| Elenchi SharePoint Online |Sì |No |No |
| Snowflake |Sì |No |No |
| Database di Sybase |Sì |Sì |No |
| Database Teradata |Sì |Sì |Sì |
| Testo/CSV |Sì |Sì |No |
| Web |Sì |Sì |No |
| XML |Sì |Sì |No |
| appFigures (beta) |Sì |No |No |
| Database di Azure Analysis Services |Sì |No |Sì |
| Azure Cosmos DB (Beta) |Sì |No |No |
| Spark in Azure HDInsight (Beta) |Sì |No |No |
| Common Data Service (Beta) |Sì |No |No |
| comScore Digital Analytix (Beta) |Sì |No |No |
| Dynamics 365 per Customer Insights (Beta) |Sì |No |No |
| Dynamics 365 per Financials (Beta) |Sì |No |No |
| GitHub (beta) |Sì |No |No |
| Google BigQuery (Beta) |Sì |No |No |
| Database Informix IBM (Beta) |Sì |No |No |
| IBM Netezza (Beta) |Sì |No |No |
| Kusto (Beta) |Sì |No |No |
| MailChimp (Beta) |Sì |No |No |
| Microsoft Azure Consumption Insights (Beta) |Sì |No |No |
| Mixpanel (Beta) |Sì |No |No |
| Planview Enterprise (Beta) |Sì |No |No |
| Projectplace (Beta) |Sì |No |No |
| QuickBooks Online (beta) |Sì |No |No |
| Smartsheet |Sì |No |No |
| Spark (Beta) |Sì |No |No |
| SparkPost (Beta) |Sì |No |No |
| SQL Sentry (Beta) |Sì |No |No |
| Stripe (Beta) |Sì |No |No |
| SweetIQ (beta) |Sì |No |No |
| Troux (Beta) |Sì |No |No |
| Twilio (beta) |Sì |No |No |
| tyGraph (Beta) |Sì |No |No |
| Vertica (Beta) |Sì |No |No |
| Visual Studio Team Services (Beta) |Sì |No |No |
| Webtrends (Beta) |Sì |No |No |
| Zendesk (Beta) |Sì |No |No |

> [!IMPORTANT]
> La sicurezza a livello di riga configurata per l'origine dati funziona per determinate connessioni DirectQuery (SQL Server, database SQL di Azure, Oracle e Teradata) e connessioni in tempo reale, purché l'autenticazione Kerberos sia configurata correttamente nell'ambiente in uso.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Elenco di metodi di autenticazione supportati per l'aggiornamento dei modelli

Il server di report di Microsoft Power BI non supporta l'autenticazione basata su OAuth per l'aggiornamento dei modelli. Alcune origini dati, ad esempio Excel o i database di Access, per connettersi ai dati usano un passaggio separato, ad esempio File o Web.

| **Origine dati** | **Autenticazione anonima** | **Autenticazione con chiave** | **Nome utente e password** | **Autenticazione di Windows** |
| --- | --- | --- | --- | --- |
| Database SQL Server |No |No |Sì |Sì |
| SQL Server Analysis Services |No |No |Sì |Sì |
| Web |Sì |No |Sì |Sì |
| Database SQL di Azure |No |No |Sì |No |
| Azure SQL Data Warehouse |No |No |Sì |No |
| Active Directory |No |No |Sì |Sì |
| Amazon Redshift |No |No |No |No |
| Archivio BLOB Azure |Sì |Sì |No |No |
| Azure Data Lake Store |No |No |No |No |
| Azure HDInsight (HDFS) |No |No |No |No |
| Azure HDInsight (Spark) |Sì |Sì |No |No |
| Archivio tabelle Azure |No |Sì |No |No |
| Dynamics 365 (online) |No |No |No |No |
| Facebook |No |No |No |No |
| Cartella |No |No |No |Sì |
| Google Analytics |No |No |No |No |
| File Hadoop (HDFS) |No |No |No |No |
| Database IBM DB2 |No |No |Sì |Sì |
| Impala |No |No |No |No |
| Microsoft Exchange |No |No |No |No |
| Microsoft Exchange Online |No |No |No |No |
| Database MySQL |No |No |Sì |Sì |
| Feed OData |Sì |Sì |Sì |Sì |
| ODBC |Sì |No |Sì |Sì |
| OLE DB |Sì |No |Sì |Sì |
| Database Oracle |No |No |Sì |Sì |
| Database PostgreSQL |No |No |Sì |No |
| Servizio Power BI |No |No |No |No |
| Script R |No |No |No |No |
| Oggetti Salesforce |No |No |No |No |
| Report di Salesforce |No |No |No |No |
| Server SAP Business Warehouse |No |No |Sì |No |
| Database SAP HANA |No |No |Sì |Sì |
| Cartella di SharePoint (locale) |Sì |No |No |Sì |
| Elenco di SharePoint (locale) |Sì |No |No |Sì |
| Elenchi SharePoint Online |No |No |No |No |
| Snowflake |No |No |No |No |
| Database di Sybase |No |No |Sì |Sì |
| Database Teradata |No |No |Sì |Sì |
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
| Microsoft Azure Consumption Insights (Beta) |No |No |No |No |
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
| Twilio (beta) |No |No |No |No |
| tyGraph (Beta) |No |No |No |No |
| Vertica (Beta) |No |No |No |No |
| Visual Studio Team Services (Beta) |No |No |No |No |
| Webtrends (Beta) |No |No |No |No |
| Zendesk (Beta) |No |No |No |No |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Elenco di metodi di autenticazione supportati per DirectQuery

Il server di report di Microsoft Power BI non supporta l'autenticazione basata su OAuth per DirectQuery.

| **Origine dati** | **Autenticazione anonima** | **Autenticazione con chiave** | **Nome utente e password** | **Autenticazione di Windows** | **Autenticazione di Windows integrata** |
| --- | --- | --- | --- | --- | --- |
| Database SQL Server |No |No |Sì |Sì |Sì |
| SQL Server Analysis Services |No |No |Sì |Sì |Sì |
| Database SQL di Azure |No |No |Sì |No |No |
| Azure SQL Data Warehouse |No |No |Sì |No |No |
| Database Oracle |No |No |Sì |Sì |Sì |
| Server SAP Business Warehouse |No |No |Sì |No |Sì |
| Database SAP HANA |No |No |Sì |Sì |No |
| Database Teradata |No |No |Sì |Sì |Sì |


## <a name="next-steps"></a>Passaggi successivi
A questo punto, dopo aver selezionato l'origine dati, [creare un report](quickstart-create-powerbi-report.md) con i dati di questa origine dati.

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

