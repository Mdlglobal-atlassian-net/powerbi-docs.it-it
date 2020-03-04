---
title: Monitorare le prestazioni dei report in Power BI
description: Indicazioni su come monitorare le prestazioni dei report in Power BI.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: b1ab74ec7f7f6594450ec2cf95528d06dc45f613
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77610019"
---
# <a name="monitor-report-performance-in-power-bi"></a>Monitorare le prestazioni dei report in Power BI

Monitorare le prestazioni dei report in Power BI Desktop usando l'[app Power BI Premium Metrics](../service-premium-metrics-app.md) e scoprire come individuare i colli di bottiglia e migliorare le prestazioni dei report.

Il monitoraggio delle prestazioni è applicabile nelle situazioni seguenti:

- L'aggiornamento del modello di dati di importazione è lento.
- I report DirectQuery o LiveConnection sono lenti.
- I calcoli del modello sono lenti.

Le query o gli oggetti visivi dei report con esecuzione lenta dovranno essere sottoposti a un'ottimizzazione continua.

## <a name="use-query-diagnostics"></a>Usare la diagnostica delle query

Usare [Diagnostica query](/power-query/QueryDiagnostics) in Power BI Desktop per determinare l'azione di Power Query durante l'anteprima o l'applicazione delle query. Usare anche la funzione _Diagnostica passaggio_ per registrare informazioni dettagliate sulla valutazione per ogni passaggio della query. I risultati vengono resi disponibili in Power Query ed è possibile applicare le trasformazioni per comprendere meglio l'esecuzione delle query.

> [!NOTE]
> Poiché la diagnostica delle query è attualmente una funzionalità di anteprima, è necessario abilitarla in _Opzioni e impostazioni_. Dopo aver abilitato la funzionalità, i comandi sono disponibili nella finestra dell'editor di Power Query nella scheda della barra multifunzione **Strumenti**.

![Immagine che mostra la scheda della barra multifunzione Strumenti dell'editor di Power Query. La barra multifunzione visualizza i comandi Diagnostica passaggio, il comando Avvia diagnostica e Arresta diagnostica.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>Usare l'analizzatore prestazioni

Usare [Analizzatore prestazioni](../desktop-performance-analyzer.md) in Power BI Desktop per esaminare le prestazioni di tutti gli elementi del report, ad esempio oggetti visivi e formule DAX. L'analizzatore prestazioni è particolarmente utile per determinare se il rendering della query o dell'oggetto visivo causa problemi di prestazioni.

## <a name="use-sql-server-profiler"></a>Usare SQL Server Profiler

È anche possibile usare [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) per identificare le query lente.

> [!NOTE]
> SQL Server Profiler è incluso in [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

Usare SQL Server Profiler quando l'origine dati è:

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop supporta la connessione a una porta di diagnostica, La porta di diagnostica consente ad altri strumenti di stabilire connessioni per eseguire analisi a scopi diagnostici. Le modifiche al modello di dati di Power Desktop non sono supportate. Le modifiche al modello di dati potrebbero causare danneggiamento e perdita dei dati.

Per creare una traccia di SQL Server Profiler, seguire queste istruzioni:

1. Aprire il report di Power BI Desktop (per facilitare l'individuazione della porta nel passaggio successivo, chiudere tutti gli altri report aperti).
1. Per determinare la porta usata da Power BI Desktop, in PowerShell (con privilegi di amministratore) o al prompt dei comandi, immettere il comando seguente:
    ```powershell
    netstat -b -n
    ```
    L'output sarà costituito da un elenco di applicazioni e delle relative porte aperte. Cercare la porta usata da **msmdsrv.exe** e prenderne nota per un uso successivo. Si tratta dell'istanza di Power BI Desktop.
1. Per connettere SQL Server Profiler al report di Power BI Desktop:
    1. Aprire SQL Server Profiler.
    1. In SQL Server Profiler nel menu _File_ selezionare _Nuova traccia_.
    1. Per **Tipo di server**, selezionare _Analysis Services_.
    1. Per **Nome server**, immettere _localhost:[porta registrata in precedenza]_ .
    1. Fare clic su _Esegui_. La traccia di SQL Server Profiler è ora attiva ed è in corso la profilatura delle query di Power BI Desktop.
1. Quando le query di Power BI Desktop vengono eseguite, verranno visualizzate le rispettive durate e i tempi della CPU. A seconda del tipo di origine dati, è possibile che vengano visualizzati altri eventi che indicano la modalità di esecuzione della query. Usando queste informazioni, è possibile individuare le query che rappresentano i colli di bottiglia.

L'uso di SQL Server Profiler offre il vantaggio di poter salvare una traccia del database di SQL Server (relazionale). La traccia può diventare un input per l'[Ottimizzazione guidata motore di database](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor). In questo modo, è possibile ricevere raccomandazioni su come ottimizzare l'origine dati.

## <a name="monitor-premium-metrics"></a>Monitorare le metriche Premium

Per le capacità di Power BI Premium, usare l'**app Power BI Premium Metrics** per monitorare l'integrità e la capacità della sottoscrizione Power BI Premium. Per altre informazioni, vedere [App Power BI Premium Metrics](../service-premium-metrics-app.md).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Diagnostica delle query](/power-query/QueryDiagnostics)
- [Analizzatore prestazioni](../desktop-performance-analyzer.md)
- [App Power BI Premium Metrics](../service-premium-metrics-app.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
