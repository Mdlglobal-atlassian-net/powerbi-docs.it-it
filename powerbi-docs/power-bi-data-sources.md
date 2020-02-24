---
title: Origini dati di Power BI
description: Questo articolo elenca le origini dati supportate da Power BI, incluse le informazioni su DirectQuery e sul gateway dati locale.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: kfollis
ms.openlocfilehash: 261d800dac9b65747e648bc76944a0b8a5077b73
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427094"
---
# <a name="power-bi-data-sources"></a>Origini dati di Power BI

La tabella seguente visualizza le origini dati supportate da Power BI per i set di dati, incluse le informazioni su DirectQuery e sul gateway dati locale. Per informazioni sui flussi di dati, vedere [Connettersi a origini dati per i flussi di dati di Power BI](service-dataflows-data-sources.md).

> [!NOTE]
> Ci sono molti connettori dati per Power BI Desktop che richiedono Internet Explorer 10 (o versione successiva) per l'autenticazione. 


| Origine dati | Connessione da desktop | Connessione e aggiornamento dal servizio | Connessione DirectQuery/dinamica | Gateway (supportato) | Gateway (obbligatorio) |
|---|---|---|---|---|---|---|---|
| Database di Access | Sì | Sì | No | Sì<sup>1</sup> | Sì |
| Active Directory | Sì | Sì | No | Sì | Sì |
| Adobe Analytics | Sì | Sì | No | No | No |
| Amazon Redshift | Sì | Sì | Sì | Sì | No |
| appFigures | Sì | Sì | No | No | No |
| Cubi AtScale | Sì | Sì | Sì | Sì | No |
| Azure Analysis Services | Sì | Sì | Sì | Sì<sup>2</sup> | No |
| Archiviazione BLOB di Azure | Sì | Sì | No | Sì | No |
| Azure Cosmos DB | Sì | Sì | No | No | No |
| Gestione costi di Azure | Sì | Sì | No | No | No |
| Esplora dati di Azure (Kusto) | Sì | Sì | Sì | No | No |
| Azure Data Lake Storage Gen1 | Sì | Sì | No | No | No |
| Azure Data Lake Storage Gen2 | Sì | Sì | No | Sì | No |
| Azure DevOps | Sì | Sì | No | No | No |
| Azure DevOps Server | Sì | Sì | No | Sì | Sì |
| Azure HDInsight (HDFS) | Sì | Sì | No | No | No |
| Azure HDInsight Spark | Sì | Sì | Sì | No | No |
| Database SQL di Azure | Sì | Sì | Sì | Sì<sup>2</sup> | No |
| Azure SQL Data Warehouse | Sì | Sì | Sì | No | No |
| Archiviazione tabelle di Azure | Sì | Sì | No | Sì | No |
| Connettore BI | Sì | Sì | Sì | Sì | Sì |
| BI360 - Budgeting & Financial Reporting | Sì | Sì | No | No | No |
| Common Data Service | Sì | Sì | No | No | No |
| Data.World - Ottieni set di dati | Sì | Sì | No | No | No |
| Denodo | Sì | Sì | Sì | Sì | Sì |
| Dremio | Sì | Sì | Sì | Sì | Sì |
| Dynamics 365 (online) | Sì | Sì | No | No | No |
| Dynamics 365 Business Central | Sì | Sì | No | No | No |
| Dynamics 365 Business Central (locale) | Sì | Sì | No | No | No |
| Dynamics 365 per Customer Insights | Sì | Sì | No | No | No |
| Dynamics NAV | Sì | Sì | No | No | No |
| Origine dati Emigo | Sì | Sì | No | No | No |
| Entersoft Business Suite | Sì | Sì | No | No | No |
| Essbase | Sì | Sì | Sì | Sì | Sì |
| Exasol | Sì | Sì | Sì | Sì | Sì |
| Excel | Sì<sup>3</sup> | Sì<sup>3</sup> | No | Sì<sup>3</sup> | No<sup>4</sup> |
| Facebook | Sì | Sì | No | No | No |
| File | Sì | Sì | No | Sì | Sì |
| Cartella | Sì | Sì | No | Sì | Sì |
| GitHub | Sì | Sì | No | No | No |
| Google Analytics | Sì | Sì | No | No | No |
| Google BigQuery | Sì | Sì | No | No | No |
| File Hadoop (HDFS) | Sì | No | No | No | No |
| HDInsight Interactive Query | Sì | Sì | Sì | No | No |
| IBM DB2 | Sì | Sì | Sì | Sì | No |
| Database Informix IBM | Sì | Sì | No | Sì | No |
| IBM Netezza | Sì | Sì | Sì | Sì | Sì |
| Impala | Sì | Sì | Sì | Sì | Sì |
| Indexima | Sì | Sì | Sì | Sì | Sì |
| Industrial App Store | Sì | Sì | No | No | No |
| Information Grid | Sì | Sì | No | No | No |
| InterSystems IRIS | Sì | Sì | Sì | Sì | Sì |
| Data warehouse di Intune | Sì | Sì | No | No | No |
| ODBC Jethro | Sì | Sì | Sì | Sì | Sì |
| JSON | Sì | Sì | No | Sì** | No<sup>4</sup> |
| Kyligence Enterprise | Sì | Sì | Sì | Sì | Sì |
| MailChimp | Sì | Sì | No | No | No |
| Marketo | Sì | Sì | No | No | No |
| ODBC MarkLogic | Sì | Sì | Sì | Sì | Sì |
| Microsoft Azure Consumption Insights | Sì | Sì | No | No | No |
| Microsoft Exchange | Sì | Sì | No | Sì | No |
| Microsoft Exchange Online | Sì | Sì | No | No | No |
| Microsoft Graph Security | Sì | Sì | No | Sì | No |
| Mixpanel | Sì | Sì | No | No | No |
| MySQL | Sì | Sì | No | Sì | Sì |
| OData | Sì | Sì | No | Sì | No |
| ODBC | Sì | Sì | No | Sì | Sì |
| OleDb | Sì | Sì | No | Sì | Sì |
| Oracle | Sì | Sì | Sì | Sì | Sì |
| Paxata | Sì | Sì | No | Sì | No |
| PDF | Sì | Sì | No | Sì | No<sup>4</sup> |
| Planview Enterprise One - CTM | Sì | Sì | No | No | No |
| Planview Enterprise One - PRM | Sì | Sì | No | No | No |
| Planview Projectplace | Sì | Sì | No | No | No |
| PostgreSQL | Sì | Sì | Sì | Sì | No |
| Flussi di dati Power BI | Sì | Sì | No | No | No |
| Set di dati Power BI | Sì | Sì | Sì | No | No |
| Flussi di dati Power Platform | Sì | Sì | No | No | No |
| Script Python | Sì | Sì<sup>5</sup> | No | Sì<sup>5</sup> | Sì |
| QubolePresto | Sì | Sì | Sì | Sì | Sì |
| Quick Base | Sì | Sì | No | Sì | Sì |
| QuickBooks Online | Sì | Sì | No | No | No |
| Script R | Sì | Sì<sup>5</sup> | No | Sì<sup>5</sup> | No |
| Roamler | Sì | Sì | No | Sì | No |
| Oggetti Salesforce | Sì | Sì | No | No | No |
| Report di Salesforce | Sì | Sì | No | No | No |
| Server messaggi SAP Business Warehouse | Sì | Sì | Sì | Sì | Sì |
| Server SAP Business Warehouse | Sì | Sì | Sì | Sì | Sì |
| SAP HANA | Sì | Sì | Sì | Sì | Sì |
| Cartella di SharePoint | Sì | Sì | No | Sì | No<sup>4</sup> |
| Elenco SharePoint | Sì | Sì | No | Sì | No<sup>4</sup> |
| Elenco SharePoint Online | Sì | Sì | No | Sì<sup>2</sup> | No |
| Smartsheet | Sì | Sì | No | No | No |
| Snowflake | Sì | Sì | Sì | Sì | No |
| Spark | Sì | Sì | Sì | Sì | No |
| SparkPost | Sì | Sì | No | No | No |
| SQL Server | Sì | Sì | Sì | Sì | Sì |
| SQL Server Analysis Services | Sì | Sì | Sì | Sì | Sì |
| Stripe | Sì | Sì | No | No | No |
| SurveyMonkey | Sì | Sì | No | Sì | No |
| SweetIQ | Sì | Sì | No | No | No |
| Sybase | Sì | Sì | No | Sì | Sì |
| TeamDesk | Sì | Sì | No | Sì | No |
| Tenforce | Sì | Sì | No | No | No |
| Teradata | Sì | Sì | Sì | Sì | Sì |
| Testo/CSV | Sì | Sì | No | Sì | No<sup>4</sup> |
| Twilio | Sì | Sì | No | No | No |
| tyGraph | Sì | Sì | No | No | No |
| Vertica | Sì | Sì | Sì | Sì | Sì |
| Web | Sì | Sì | No | Sì | Sì |
| Webtrends | Sì | Sì | No | No | No |
| Workforce Dimensions | Sì | Sì | No | Sì | No |
| XML | Sì | Sì | No | Sì | No<sup>4</sup> |
| Zendesk | Sì | Sì | No | No | No |
| | | | | | | | |

<sup>1</sup> Supportato con il [provider ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920), installato nello stesso computer del gateway.

<sup>2</sup> Supportato con la stessa funzione M della versione locale.

<sup>3</sup> I file di Excel 1997-2003 (con estensione xls) richiedono il [provider ACE OLEDB](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Obbligatorio per la versione locale della tecnologia.

<sup>5</sup> Supportato solo con il [gateway dati (modalità personale)](service-gateway-personal-mode.md).

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
