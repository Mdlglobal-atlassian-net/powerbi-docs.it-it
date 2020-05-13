---
title: Origini dati supportate in Power BI
description: Questo articolo elenca le origini dati supportate da Power BI, incluse le informazioni su DirectQuery e sul gateway dati locale.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: kfollis
ms.openlocfilehash: a29dcd8c89d064678e558d5ebfee7ccb3cc8a8e0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83330107"
---
# <a name="power-bi-data-sources"></a>Origini dati supportate in Power BI

La tabella seguente visualizza le origini dati supportate da Power BI per i set di dati, incluse le informazioni su DirectQuery e sul gateway dati locale. Per informazioni sui flussi di dati, vedere [Connettersi a origini dati per i flussi di dati di Power BI](../transform-model/service-dataflows-data-sources.md).

> [!NOTE]
> Sono molti i connettori dati per Power BI Desktop che richiedono Internet Explorer 10 (o versione successiva) per l'autenticazione. 


| Origine dati | Connessione da desktop | Connessione e aggiornamento dal servizio | Connessione DirectQuery/dinamica | Gateway (supportato) | Gateway (obbligatorio) |
|---|---|---|---|---|---|---|---|
| Database di Access | Yes | Yes | No | Sì<sup>1</sup> | Yes |
| Active Directory | Yes | Yes | No | Yes | Yes |
| Adobe Analytics | Yes | Yes | No | No | No |
| Amazon Redshift | Yes | Yes | Yes | Yes | No |
| appFigures | Yes | Yes | No | No | No |
| Cubi AtScale | Yes | Yes | Yes | Yes | No |
| Azure Analysis Services | Yes | Yes | Yes | Sì<sup>2</sup> | No |
| Archivio BLOB Azure | Yes | Yes | No | Yes | No |
| Azure Cosmos DB | Yes | Yes | No | No | No |
| Gestione costi di Azure | Yes | Yes | No | No | No |
| Esplora dati di Azure (Kusto) | Yes | Yes | Yes | No | No |
| Azure Data Lake Storage Gen1 | Yes | Yes | No | No | No |
| Azure Data Lake Storage Gen2 | Yes | Yes | No | Yes | No |
| Azure DevOps | Yes | Yes | No | No | No |
| Azure DevOps Server | Yes | Yes | No | Yes | Yes |
| Azure HDInsight (HDFS) | Yes | Yes | No | No | No |
| Azure HDInsight Spark | Yes | Yes | Yes | No | No |
| Database SQL di Azure | Yes | Yes | Yes | Sì<sup>2</sup> | No |
| Azure SQL Data Warehouse | Yes | Yes | Yes | Sì<sup>2</sup> | No |
| Archivio tabelle Azure | Yes | Yes | No | Yes | No |
| Connettore BI | Yes | Yes | Yes | Yes | Yes |
| BI360 - Budgeting & Financial Reporting | Yes | Yes | No | No | No |
| Common Data Service | Yes | Yes | No | No | No |
| Data.World - Ottieni set di dati | Yes | Yes | No | No | No |
| Denodo | Yes | Yes | Yes | Yes | Yes |
| Dremio | Yes | Yes | Yes | Yes | Yes |
| Dynamics 365 (online) | Yes | Yes | No | No | No |
| Dynamics 365 Business Central | Yes | Yes | No | No | No |
| Dynamics 365 Business Central (locale) | Yes | Yes | No | No | No |
| Dynamics 365 per Customer Insights | Yes | Yes | No | No | No |
| Dynamics NAV | Yes | Yes | No | No | No |
| Origine dati Emigo | Yes | Yes | No | No | No |
| Entersoft Business Suite | Yes | Yes | No | No | No |
| Essbase | Yes | Yes | Yes | Yes | Yes |
| Exasol | Yes | Yes | Yes | Yes | Yes |
| Excel | Sì<sup>3</sup> | Sì<sup>3</sup> | No | Sì<sup>3</sup> | No<sup>4</sup> |
| Facebook | Yes | Yes | No | No | No |
| file | Yes | Yes | No | Yes | Yes |
| Cartella | Yes | Yes | No | Yes | Yes |
| GitHub | Yes | Yes | No | No | No |
| Google Analytics | Yes | Yes | No | No | No |
| Google BigQuery | Yes | Yes | No | No | No |
| File Hadoop (HDFS) | Yes | No | No | No | No |
| HDInsight Interactive Query | Yes | Yes | Yes | No | No |
| IBM DB2 | Yes | Yes | Yes | Yes | No |
| Database Informix IBM | Yes | Yes | No | Yes | No |
| IBM Netezza | Yes | Yes | Yes | Yes | Yes |
| Impala | Yes | Yes | Yes | Yes | Yes |
| Indexima | Yes | Yes | Yes | Yes | Yes |
| Industrial App Store | Yes | Yes | No | No | No |
| Information Grid | Yes | Yes | No | No | No |
| InterSystems IRIS | Yes | Yes | Yes | Yes | Yes |
| Data warehouse di Intune | Yes | Yes | No | No | No |
| ODBC Jethro | Yes | Yes | Yes | Yes | Yes |
| JSON | Yes | Yes | No | Sì** | No<sup>4</sup> |
| Kyligence Enterprise | Yes | Yes | Yes | Yes | Yes |
| MailChimp | Yes | Yes | No | No | No |
| Marketo | Yes | Yes | No | No | No |
| ODBC MarkLogic | Yes | Yes | Yes | Yes | Yes |
| Microsoft Azure Consumption Insights | Yes | Yes | No | No | No |
| Microsoft Exchange | Yes | Yes | No | Yes | No |
| Microsoft Exchange Online | Yes | Yes | No | No | No |
| Microsoft Graph Security | Yes | Yes | No | Yes | No |
| Mixpanel | Yes | Yes | No | No | No |
| MySQL | Yes | Yes | No | Yes | Yes |
| OData | Yes | Yes | No | Yes | No |
| ODBC | Yes | Yes | No | Yes | Yes |
| OleDb | Yes | Yes | No | Yes | Yes |
| Oracle | Yes | Yes | Yes | Yes | Yes |
| Paxata | Yes | Yes | No | Yes | No |
| PDF | Yes | Yes | No | Yes | No<sup>4</sup> |
| Planview Enterprise One - CTM | Yes | Yes | No | No | No |
| Planview Enterprise One - PRM | Yes | Yes | No | No | No |
| Planview Projectplace | Yes | Yes | No | No | No |
| PostgreSQL | Yes | Yes | Yes | Yes | No |
| Flussi di dati Power BI | Yes | Yes | No | No | No |
| Set di dati Power BI | Yes | Yes | Yes | No | No |
| Flussi di dati Power Platform | Yes | Yes | No | No | No |
| Script Python | Yes | Sì<sup>5</sup> | No | Sì<sup>5</sup> | Yes |
| QubolePresto | Yes | Yes | Yes | Yes | Yes |
| Quick Base | Yes | Yes | No | Yes | Yes |
| QuickBooks Online | Yes | Yes | No | No | No |
| Script R | Yes | Sì<sup>5</sup> | No | Sì<sup>5</sup> | No |
| Roamler | Yes | Yes | No | Yes | No |
| Oggetti Salesforce | Yes | Yes | No | No | No |
| Report di Salesforce | Yes | Yes | No | No | No |
| Server messaggi SAP Business Warehouse | Yes | Yes | Yes | Yes | Yes |
| Server SAP Business Warehouse | Yes | Yes | Yes | Yes | Yes |
| SAP HANA | Yes | Yes | Yes | Yes | Yes |
| Cartella di SharePoint | Yes | Yes | No | Yes | No<sup>4</sup> |
| Elenco SharePoint | Yes | Yes | No | Yes | No<sup>4</sup> |
| Elenchi SharePoint Online | Yes | Yes | No | Sì<sup>2</sup> | No |
| Smartsheet | Yes | Yes | No | No | No |
| Snowflake | Yes | Yes | Yes | Yes | No |
| Spark | Yes | Yes | Yes | Yes | No |
| SparkPost | Yes | Yes | No | No | No |
| SQL Server | Yes | Yes | Yes | Yes | Yes |
| SQL Server Analysis Services | Yes | Yes | Yes | Yes | Yes |
| Stripe | Yes | Yes | No | No | No |
| SurveyMonkey | Yes | Yes | No | Yes | No |
| SweetIQ | Yes | Yes | No | No | No |
| Sybase | Yes | Yes | No | Yes | Yes |
| TeamDesk | Yes | Yes | No | Yes | No |
| Tenforce | Yes | Yes | No | No | No |
| Teradata | Yes | Yes | Yes | Yes | Yes |
| Testo/CSV | Yes | Yes | No | Yes | No<sup>4</sup> |
| Twilio | Yes | Yes | No | No | No |
| tyGraph | Yes | Yes | No | No | No |
| Vertica | Yes | Yes | Yes | Yes | Yes |
| Web | Yes | Yes | No | Yes | Sì <sup>6</sup> |
| Webtrends | Yes | Yes | No | No | No |
| Workforce Dimensions | Yes | Yes | No | Yes | No |
| XML | Yes | Yes | No | Yes | No<sup>4</sup> |
| Zendesk | Yes | Yes | No | No | No |
| | | | | | | | |

<sup>1</sup> Supportato con il [provider ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920), installato nello stesso computer del gateway.

<sup>2</sup> Supportato con la stessa funzione M della versione locale, determinando opzioni di autenticazione con restrizioni (il gateway non supporta OAuth).

<sup>3</sup> I file di Excel 1997-2003 (con estensione xls) richiedono il [provider ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Obbligatorio per la versione locale della tecnologia.

<sup>5</sup> Supportato solo con il [gateway dati (modalità personale)](service-gateway-personal-mode.md).

<sup>6</sup> Necessario per i file con estensione html, xls, e i database di Access

## <a name="single-sign-on-sso-for-directquery-sources"></a>Single Sign-On (SSO) per le origini DirectQuery

Quando l'opzione SSO è abilitata e gli utenti accedono ai report generati dall'origine dati, Power BI invia le relative credenziali di Azure AD autenticate nelle query all'origine dati sottostante. Questo consente a Power BI di rispettare le impostazioni di sicurezza configurate al livello dell'origine dati.
L'opzione SSO è effettiva in tutti i set di dati che usano l'origine dati specifica. Non interessa il metodo di autenticazione usato per gli scenari di importazione. Le origini dati seguenti supportano l'accesso SSO per le connessioni tramite DirectQuery:

- Database SQL di Azure
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Server messaggi SAP BW
- Snowflake
- Spark
- SQL Server
- Teradata

> [!Note]
> L'autenticazione MFA (Azure Multi-Factor Authentication) non è supportata. Gli utenti che vogliono usare SSO con DirectQuery devono essere esentati dall'autenticazione MFA.

## <a name="next-steps"></a>Passaggi successivi

[Connettersi ai dati in Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Uso di DirectQuery in Power BI](desktop-directquery-about.md)  
[Dati dinamici di SQL Server Analysis Services in Power BI](sql-server-analysis-services-tabular-data.md)  
[Informazioni sul gateway dati locale](service-gateway-onprem.md)  
