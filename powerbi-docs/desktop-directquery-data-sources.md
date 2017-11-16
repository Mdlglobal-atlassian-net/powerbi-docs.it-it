---
title: Origini dati supportate da DirectQuery in Power BI
description: Ottenere un elenco di origini dati che possono essere usati da DirectQuery.
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/26/2017
ms.author: davidi
ms.openlocfilehash: 5de07cb5f834d7f40ddd5391e83afa85edd7233c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Origini dati supportate da DirectQuery in Power BI
**Power BI Desktop** e il **servizio Power BI** dispongono di diverse origini dati a cui è possibile connettersi per accedere ai dati. Questo articolo descrive le origini dati per Power BI che supportano il metodo di connessione noto come **DirectQuery**. Per altre informazioni su DirectQuery, vedere [**DirectQuery in Power BI**](desktop-directquery-about.md).

Le origini dati seguenti supportano DirectQuery in Power BI:

* Amazon Redshift
* Spark in Azure HDInsight (Beta)
* Database SQL di Azure
* Azure SQL Data Warehouse
* Google BigQuery (Beta)
* IBM Netezza (Beta)
* Impala (versione 2.x)
* Database di Oracle (versione 12 e successive)
* SAP Business Warehouse (Beta)
* SAP HANA
* Snowflake
* Spark (Beta) (versione 0.9 e successive)
* SQL Server
* Database Teradata
* Vertica (Beta)

Le origini dati il cui nome è seguito da **(Beta)** o **(Anteprima)** sono soggette a modifiche e non sono supportate per l'uso nella produzione. Possono anche non essere supportate dopo la pubblicazione di un report per il **servizio Power BI**, il che significa che l'apertura di un report pubblicato o l'esplorazione del set di dati può comportare un errore.

L'unica differenza tra le origini dati **(Beta)** e **(Anteprima)** è che le origini **(anteprima)** devono essere abilitate come funzionalità di anteprima prima di poter essere usate. Per abilitare un connettore dati **(Anteprima)**, in **Power BI Desktop** andare in **File > Opzioni e impostazioni**, quindi in **Impostazioni > Opzioni > Funzionalità di anteprima**.

## <a name="on-premises-gateway-requirements"></a>Requisiti del gateway locale
La tabella seguente specifica se è necessario un **gateway dati locale** per connettersi all'origine dati specificata, dopo la pubblicazione di un report nel **servizio Power BI**.

| Origine | Gateway necessario? |
| --- | --- |
| SQL Server |Sì |
| Database SQL di Azure |No |
| Azure SQL Data Warehouse |No |
| SAP HANA |Sì |
| Database Oracle |Sì |
| Database Teradata |Sì |
| Amazon Redshift |No |
| Impala (versione 2.x) |Sì |
| Snowflake (anteprima) |Non è ancora supportato nel **servizio Power BI** |
| Spark (Beta), versione 0.9 e successive |Non è ancora supportato nel **servizio Power BI** |
| Spark in Azure HDInsight (Beta) |Non è ancora supportato nel **servizio Power BI** |
| IBM Netezza (Beta) |Non è ancora supportato nel **servizio Power BI** |
| SAP Business Warehouse (Beta) |Non è ancora supportato nel **servizio Power BI** |

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni su DirectQuery, vedere le risorse seguenti:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway dati locale](service-gateway-onprem.md)

