---
title: Origini dati supportate da DirectQuery in Power BI
description: Ottenere un elenco di origini dati che possono essere usati da DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/31/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: dae93a2555101a42f072158f8536319783b3f973
ms.sourcegitcommit: aef57ff94a5d452d6b54a90598bd6a0dd1299a46
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66809123"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Origini dati supportate da DirectQuery in Power BI

**Power BI Desktop** e il **servizio Power BI** dispongono di diverse origini dati a cui è possibile connettersi per accedere ai dati. Questo articolo descrive le origini dati per Power BI che supportano il metodo di connessione noto come **DirectQuery**. Per altre informazioni su DirectQuery, vedere [**DirectQuery in Power BI**](desktop-directquery-about.md).

Le origini dati seguenti supportano DirectQuery in Power BI:

* Amazon Redshift
* AtScale (Beta)
* Esplora dati di Azure
* Azure HDInsight Spark
* [Database SQL di Azure](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Google BigQuery
* HDInsight Interactive Query
* Database IBM DB2
* IBM Netezza
* Impala (versione 2.x)
* Database di Oracle (versione 12 e successive)
* Oracle Essbase
* Server applicazioni SAP Business Warehouse
* Server messaggi SAP Business Warehouse
* SAP HANA
* Snowflake
* Spark (versione 0.9 e successive)
* SQL Server
* Database Teradata
* Vertica

Le origini dati il cui nome è seguito da **(Beta)** o **(Anteprima)** sono soggette a modifiche e non sono supportate per l'uso in produzione. Possono anche non essere supportate dopo la pubblicazione di un report per il **servizio Power BI**, il che significa che l'apertura di un report pubblicato o l'esplorazione del set di dati può comportare un errore.

L'unica differenza tra le origini dati **(Beta)** e **(Anteprima)** è che le origini **(anteprima)** devono essere abilitate come funzionalità di anteprima prima di poter essere usate. Per abilitare un connettore dati **(Anteprima)**, in **Power BI Desktop**, passare a **File > Opzioni e impostazioni** e quindi selezionare **Funzionalità di anteprima**.

> [!NOTE]
> Le query DirectQuery per SQL Server richiedono l'autenticazione tramite credenziali di autenticazione di Windows o credenziali del database valide per stabilire l'accesso. Le credenziali alternative non sono supportate.
>

## <a name="on-premises-gateway-requirements"></a>Requisiti del gateway locale
La tabella seguente specifica se è necessario un **gateway dati locale** per connettersi all'origine dati specificata, dopo la pubblicazione di un report nel **servizio Power BI**.

| Origine | Gateway necessario? |
| --- | --- |
| Amazon Redshift |No |
| Spark in Azure HDInsight (Beta) |No |
| Database SQL di Azure |No |
| Azure SQL Data Warehouse |No |
| Google BigQuery |No |
| IBM Netezza |Sì |
| Impala (versione 2.x) |Sì |
| Database Oracle |Sì |
| Server applicazioni SAP Business Warehouse |Sì |
| Server messaggi SAP Business Warehouse |Non è ancora supportato nel **servizio Power BI** |
| SAP HANA |Sì |
| Snowflake |Sì |
| Spark (Beta), versione 0.9 e successive |Sì |
| SQL Server |Sì |
| Database Teradata |Sì |

## <a name="single-sign-on-sso-for-directquery-sources"></a>Single Sign-On (SSO) per le origini DirectQuery

Quando l'opzione SSO è abilitata e gli utenti accedono ai report generati dall'origine dati, Power BI invia le relative credenziali di Azure AD autenticate nelle query all'origine dati sottostante. Questo consente a Power BI di rispettare le impostazioni di sicurezza configurate al livello dell'origine dati.

L'opzione SSO interessa tutti i set di dati che usano l'origine dati specifica. Non interessa il metodo di autenticazione usato per gli scenari di importazione. Le origini dati seguenti supportano l'accesso SSO per le connessioni tramite DirectQuery:

- Database SQL di Azure
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> L'autenticazione MFA (Azure Multi-Factor Authentication) non è supportata. Gli utenti che vogliono usare SSO con DirectQuery devono essere esentati dall'autenticazione MFA.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su DirectQuery, vedere le risorse seguenti:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway dati locale](service-gateway-onprem.md)

