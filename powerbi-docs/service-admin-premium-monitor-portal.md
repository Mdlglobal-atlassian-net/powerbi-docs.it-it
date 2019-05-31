---
title: Monitorare le capacità di Power BI Premium tramite il portale di amministrazione
description: Usare il portale di amministrazione di Power BI per monitorare le capacità Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564908"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorare le capacità nel portale di amministrazione

Il **Health** scheda le **le impostazioni di capacità** area nel portale di amministrazione fornisce una riepilogo sui carichi di lavoro della capacità e abilitati le metriche.  

![Capacità di integrità, scheda nel portale](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Se è necessario le metriche più complete, usare il [le metriche della capacità di Power BI Premium](service-admin-premium-monitor-capacity.md) app. L'app fornisce il drill-down e di filtro e le metriche più dettagliate per quasi ogni aspetto sulle prestazioni della capacità. Per altre informazioni, vedere [le capacità di monitoraggio Premium con l'app](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Metriche di sistema

Nel **integrità** scheda livello più alto, l'utilizzo della CPU e utilizzo della memoria forniscono una visualizzazione rapida delle metriche più importanti per la capacità. Queste metriche sono cumulative, tra cui attivati tutti i carichi di lavoro alla capacità.

| **Metrica** | **Descrizione** |
| --- | --- |
| UTILIZZO DELLA CPU | Utilizzo medio della CPU, come percentuale della disponibilità totale della CPU. |
| UTILIZZO DELLA MEMORIA | Utilizzo di memoria Media in gigabyte (GB).|

## <a name="workload-metrics"></a>Metriche di carico di lavoro

Per ogni carico di lavoro abilitata per la capacità. Utilizzo della CPU e utilizzo della memoria vengono visualizzati.

| **Metrica** | **Descrizione** |
| --- | --- |
| UTILIZZO DELLA CPU | Utilizzo medio della CPU, come percentuale della disponibilità totale della CPU. |
| UTILIZZO DELLA MEMORIA | Utilizzo di memoria Media in gigabyte (GB).|

### <a name="detailed-workload-metrics"></a>Metriche di carico di lavoro dettagliato

Ogni carico di lavoro dispone di altre metriche. Il tipo delle metriche visualizzate variano a seconda del carico di lavoro. Per visualizzare le metriche dettagliate per un carico di lavoro, fare clic su di espansione (freccia in giù).

![Espandere di integrità del carico di lavoro](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Dataflows

##### <a name="dataflow-operations"></a>Operazioni del flusso di dati

| **Metrica** | **Descrizione** |
| --- | --- |
| Total Count | aggiornamenti totali per ogni flusso di dati. |
| Success Count | Totali aggiornamenti ha esito positivo per ogni flusso di dati.|
| Durata media (min) | durata media dell'aggiornamento per il flusso di dati, espressa in minuti |
| Durata max (min) | durata dell'aggiornamento con esecuzione più prolungata per il flusso di dati, espressa in minuti. |
| Tempo medio di attesa (min) | ritardo medio tra l'ora pianificata e l'inizio di un aggiornamento per il flusso di dati, espresso in minuti. |
| Tempo massimo di attesa (min) | tempo di attesa massimo per il flusso di dati, espresso in minuti.  |

#### <a name="datasets"></a>Set di dati

##### <a name="refresh"></a>Aggiorna

| **Metrica** | **Descrizione** |
| --- | --- |
| Total Count | aggiornamenti totali per ogni set di dati. |
| Success Count | Totali aggiornamenti ha esito positivo per ogni set di dati. |
| Failure Count | Aggiornamenti non riusciti totali per ogni set di dati. |
| Percentuale di successo  | Numero di aggiornamenti ha esito positivo, diviso per il totale viene aggiornato per misurare. Affidabilità. |
| Durata media (min) | durata media dell'aggiornamento per il set di dati, espressa in minuti.  |
| Durata max (min) | durata dell'aggiornamento con esecuzione più prolungata per il set di dati, espressa in minuti. |
| Tempo medio di attesa (min) | ritardo medio tra l'ora pianificata e l'inizio di un aggiornamento per il set di dati, espresso in minuti. |
| Tempo massimo di attesa (min) | tempo di attesa massimo per il set di dati, espresso in minuti. |

##### <a name="query"></a>Query

| **Metrica** | **Descrizione** |
| --- | --- |
| Total Count | numero totale di query eseguite per il set di dati. |
| Average Duration (ms) |durata media della query per il set di dati, espressa in millisecondi|
| Max Duration (ms) |durata della query con esecuzione più prolungata nel set di dati, espressa in millisecondi. |
| Average Wait Time (ms) |tempo di attesa medio della query per il set di dati, espresso in millisecondi. |
| Tempo massimo di attesa (ms) |durata della query con attesa più prolungata nel set di dati, espressa in millisecondi. |

##### <a name="eviction"></a>Rimozione

| **Metrica** | **Descrizione** |
| --- | --- |
| Numero modello | Numero totale di eliminazioni di set di dati per questa capacità. Quando la capacità rileva un utilizzo elevato della memoria, il nodo rimuove uno o più set di dati dalla memoria. I set di dati inattivi (senza operazioni di query/aggiornamento in esecuzione) vengono rimossi per primi. Poi l'ordine di rimozione si basa sul principio LRU ("utilizzati meno di recente"). |

#### <a name="paginated-reports"></a>Paginated Reports

##### <a name="report-execution"></a>Esecuzione del report

| **Metrica** | **Descrizione** |
| --- | --- |
| Conteggio delle esecuzioni  | Il numero di volte in cui è stato eseguito il report e visualizzati dagli utenti.|

##### <a name="report-usage"></a>Utilizzo di report

| **Metrica** | **Descrizione** |
| --- | --- |
| Success Count | Il numero di volte in cui che il report è stato visualizzato da un utente. |
| Failure Count |Il numero di volte in cui che il report è stato visualizzato da un utente.|
| Row Count |numero di righe di dati nel report. |
| Durata recupero dati (ms) |tempo medio necessario per recuperare i dati per il report, espresso in millisecondi. Durate prolungate possono indicare query lente o altri problemi relativi all'origine dati.  |
| Durata di elaborazione (ms) |tempo medio necessario per elaborare i dati per un report, espresso in millisecondi. |
| Il rendering di durata (ms) |tempo medio necessario per eseguire il rendering di un report nel browser, espresso in millisecondi. |

> [!NOTE]
> Visualizzate metriche dettagliate per la **intelligenza artificiale** carico di lavoro non sono ancora disponibili.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere appreso come monitorare le capacità di Power BI Premium, è possibile consultare informazioni su come ottimizzare le capacità.

> [!div class="nextstepaction"]
> [Ottimizzazione della capacità di Power BI Premium](service-premium-capacity-optimize.md)
