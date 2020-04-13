---
title: Monitorare le capacità di Power BI Premium tramite il portale di amministrazione
description: Usare il portale di amministrazione di Power BI per monitorare le capacità Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/06/2020
LocalizationGroup: Premium
ms.openlocfilehash: 7f300cca6614f638f88886a913b30a93d0f52cfd
ms.sourcegitcommit: 2b93c1cc29aaf199ab7441a04c8e5ae49ffca5d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2020
ms.locfileid: "80813007"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorare le capacità nel portale di amministrazione

La scheda **Integrità** nell'area **Impostazioni di capacità** nel portale di amministrazione fornisce un riepilogo delle metriche relative alla capacità e ai carichi di lavoro abilitati.  

![Scheda Integrità della capacità nel portale](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Se sono necessarie metriche più complete, usare l'app [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md). L'app fornisce funzionalità di drill-down e filtro e le metriche più dettagliate per quasi tutti gli aspetti che influiscono sulle prestazioni della capacità. Per altre informazioni, vedere [Monitorare le capacità Premium con l'app](service-admin-premium-monitor-capacity.md).

> [!IMPORTANT]
> Se per la capacità Power BI Premium si riscontra un utilizzo elevato delle risorse, con conseguenti problemi di prestazioni o affidabilità, è possibile ricevere messaggi di posta elettronica di notifica per identificare e risolvere il problema. Per altre informazioni, vedere [Notifiche per capacità e affidabilità](service-interruption-notifications.md#capacity-and-reliability-notifications).

## <a name="system-metrics"></a>Metriche di sistema

Nella scheda **Health**, al livello più alto, l'utilizzo della CPU e l'utilizzo della memoria offrono una rapida visualizzazione delle metriche più importanti per la capacità. Queste metriche sono cumulative e includono tutti i carichi di lavoro abilitati relativi alla capacità.

| **Metrica** | **Descrizione** |
| --- | --- |
| UTILIZZO CPU | Utilizzo medio della CPU espresso come percentuale della CPU totale disponibile. |
| UTILIZZO MEMORIA | Utilizzo medio della memoria espresso in gigabyte (GB).|

## <a name="workload-metrics"></a>Metriche per carichi di lavoro

Per ogni carico di lavoro abilitato per la capacità. Vengono visualizzati l'utilizzo della CPU e l'utilizzo della memoria.

| **Metrica** | **Descrizione** |
| --- | --- |
| UTILIZZO CPU | Utilizzo medio della CPU espresso come percentuale della CPU totale disponibile. |
| UTILIZZO MEMORIA | Utilizzo medio della memoria espresso in gigabyte (GB).|

### <a name="detailed-workload-metrics"></a>Metriche dettagliate per carichi di lavoro

Ogni carico di lavoro prevede metriche aggiuntive. Il tipo di metriche visualizzato dipende dal carico di lavoro. Per visualizzare le metriche dettagliate per un carico di lavoro, fare clic sulla freccia di espansione (verso il basso).

![Espansione di Integrità carico di lavoro](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Flussi di dati

##### <a name="dataflow-operations"></a>Operazioni su flussi di dati

| **Metrica** | **Descrizione** |
| --- | --- |
| Total Count | aggiornamenti totali per ogni flusso di dati. |
| Success Count | Aggiornamenti totali riusciti per ogni flusso di dati.|
| Average Duration (ms) (Durata media (ms)) | durata media dell'aggiornamento per il flusso di dati, espressa in minuti |
| Max Duration (ms) (Durata massima (ms)) | durata dell'aggiornamento con esecuzione più prolungata per il flusso di dati, espressa in minuti. |
| Average Wait Time (min) (Tempo di attesa medio (min)) | ritardo medio tra l'ora pianificata e l'inizio di un aggiornamento per il flusso di dati, espresso in minuti. |
| Max Wait Time (minutes) (Tempo di attesa massimo (min)) | tempo di attesa massimo per il flusso di dati, espresso in minuti.  |

#### <a name="datasets"></a>Set di dati

##### <a name="refresh"></a>Aggiorna

| **Metrica** | **Descrizione** |
| --- | --- |
| Total Count | aggiornamenti totali per ogni set di dati. |
| Success Count | Aggiornamenti totali riusciti per ogni set di dati. |
| Failure Count | Aggiornamenti totali non riusciti per ogni set di dati. |
| Success Rate (Percentuale di riuscita)  | Numero di aggiornamenti riusciti, diviso per il numero totale di aggiornamenti per misurare l'affidabilità. |
| Average Duration (ms) (Durata media (ms)) | durata media dell'aggiornamento per il set di dati, espressa in minuti.  |
| Max Duration (ms) (Durata massima (ms)) | durata dell'aggiornamento con esecuzione più prolungata per il set di dati, espressa in minuti. |
| Average Wait Time (min) (Tempo di attesa medio (min)) | ritardo medio tra l'ora pianificata e l'inizio di un aggiornamento per il set di dati, espresso in minuti. |
| Max Wait Time (minutes) (Tempo di attesa massimo (min)) | tempo di attesa massimo per il set di dati, espresso in minuti. |

##### <a name="query"></a>Query

| **Metrica** | **Descrizione** |
| --- | --- |
| Total Count | numero totale di query eseguite per il set di dati. |
| Average Duration (ms) |durata media della query per il set di dati, espressa in millisecondi|
| Max Duration (ms) |durata della query con esecuzione più prolungata nel set di dati, espressa in millisecondi. |
| Average Wait Time (ms) |tempo di attesa medio della query per il set di dati, espresso in millisecondi. |
| Max Wait Time (ms) (Tempo massimo di attesa (ms)) |durata della query con attesa più prolungata nel set di dati, espressa in millisecondi. |

##### <a name="eviction"></a>Rimozione

| **Metrica** | **Descrizione** |
| --- | --- |
| Model Count (Conteggio modelli) | Numero totale di rimozioni di set di dati per questa capacità. Quando la capacità rileva un utilizzo elevato della memoria, il nodo rimuove uno o più set di dati dalla memoria. I set di dati inattivi (senza operazioni di query/aggiornamento in esecuzione) vengono rimossi per primi. Poi l'ordine di rimozione si basa sul principio LRU ("utilizzati meno di recente"). |

#### <a name="paginated-reports"></a>Paginated Reports

##### <a name="report-execution"></a>Esecuzione report

| **Metrica** | **Descrizione** |
| --- | --- |
| Execution Count (Conteggio esecuzioni)  | Numero di volte in cui il report è stato eseguito e visualizzato dagli utenti.|

##### <a name="report-usage"></a>Utilizzo report

| **Metrica** | **Descrizione** |
| --- | --- |
| Success Count | Numero di volte in cui il report è stato visualizzato da un utente. |
| Failure Count |Numero di volte in cui il report è stato visualizzato da un utente.|
| Row Count |numero di righe di dati nel report. |
| Data Retrieval Duration (ms) (Durata recupero dati (ms)) |tempo medio necessario per recuperare i dati per il report, espresso in millisecondi. Durate prolungate possono indicare query lente o altri problemi relativi all'origine dati.  |
| Processing Duration (ms) (Durata elaborazione (ms)) |tempo medio necessario per elaborare i dati per un report, espresso in millisecondi. |
| Rendering Duration (ms) (Durata rendering (ms)) |tempo medio necessario per eseguire il rendering di un report nel browser, espresso in millisecondi. |

> [!NOTE]
> Le metriche dettagliate per il carico di lavoro **Intelligenza artificiale** non sono ancora disponibili.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere appreso come monitorare le capacità di Power BI Premium, è possibile consultare informazioni su come ottimizzare le capacità.

> [!div class="nextstepaction"]
> [Ottimizzazione delle capacità di Power BI Premium](service-premium-capacity-optimize.md)
