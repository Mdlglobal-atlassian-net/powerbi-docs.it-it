---
title: Origini dati dei report impaginati nel Server di report di Power BI
description: Informazioni sulle origini dati a cui possono connettersi i report impaginati (con estensione rdl) nel Server di report di Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260716"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Origini dati dei report impaginati nel Server di report di Power BI
I report impaginati di Reporting Services nel Server di report di Power BI supportano le stesse origini dati supportate in SQL Server Reporting Services. Vedere l'elenco di [Origini dati supportate da Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Connettersi a origini dati Oracle con UseInstalledUICulture

Per connettersi alle origini dati Oracle, il Server di report di Power BI usa il provider di dati Oracle per .NET (ODP.NET) che è indipendente dal NLS.

Per impostazione predefinita, il server di report usa le impostazioni cultura dell'interfaccia utente del primo client per caricare ODP.NET.  Di conseguenza, tutte le connessioni successive a Oracle dal server di report avranno le impostazioni cultura dell'interfaccia utente iniziali fino al riavvio del servizio.  Questo approccio può causare problemi durante il rendering di un report a causa di mancate corrispondenze nella formattazione delle impostazioni cultura dell'interfaccia utente.

Per offrire un'esperienza migliore nel Server di report di Power BI, è stata introdotta un'impostazione di configurazione denominata UseInstalledUICulture. Quando UseInstalledUICulture è impostato su true, il server di report carica sempre ODP.NET nelle impostazioni cultura dell'interfaccia utente del server anziché le impostazioni cultura del primo client.
Questa impostazione è disponibile nel Server di report di Power BI a partire dalla versione del servizio di febbraio

Per abilitare la funzionalità, modificare il file rsreportserver.config della voce di estensione ORACLE come indicato di seguito.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Passaggi successivi
Dopo essersi connessi all'origine dati, [creare un report impaginato](quickstart-create-paginated-report.md).  


Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
