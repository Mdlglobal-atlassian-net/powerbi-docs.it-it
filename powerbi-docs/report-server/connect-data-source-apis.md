---
title: Modificare le stringhe di connessione all'origine dati con PowerShell
description: Modificare le stringhe di connessione all'origine dati usando le API in PowerShell - Server di report di Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: maggies
ms.openlocfilehash: 9ca5d47a938210c10903c916c54713b89923e287
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80751528"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Modificare le stringhe di connessione all'origine dati nei report di Power BI con PowerShell - Server di report di Power BI


È possibile modificare le stringhe di connessione all'origine dati nei report di Power BI in Server di report di Power BI usando le API in PowerShell. 

> [!NOTE]
> Questa funzionalità attualmente funziona solo per DirectQuery. Il supporto per l'importazione e l'aggiornamento dei dati sarà presto disponibile.

1. Installare i cmdlet di PowerShell per Server di report di Power BI. I cmdlet e le istruzioni di installazione sono disponibili all'indirizzo [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

2. Recuperare le informazioni sull'origine dati esistenti per il file di Power BI tramite i cmdlet di PowerShell:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Per visualizzare le informazioni per la prima origine dati contenuta nel report di Power BI: 

    ```powershell
    $dataSources[0]
    ```

3. Aggiornare le informazioni sulla connessione e sulle credenziali se necessario. Se si aggiorna la stringa di connessione e l'origine dati usa le credenziali archiviate, è necessario fornire la password dell'account. 

    Per aggiornare una stringa di connessione all'origine dati:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Per modificare il tipo di credenziali dell'origine dati:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Per modificare nome utente e password dell'origine dati:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Salvare di nuovo le credenziali aggiornate nel server.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Passaggi successivi

[Origini dati dei report impaginati nel Server di report di Power BI](connect-data-sources.md) 

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
