---
title: Risolvere i problemi relativi alle prestazioni dei report in Power BI
description: Guida alla risoluzione dei problemi per la diagnosi di prestazioni lente per i report in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: dd3be575946502a886bbf2b89e2a1844f4046ea7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276951"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Risolvere i problemi relativi alle prestazioni dei report in Power BI

Questo articolo fornisce indicazioni che consentono agli sviluppatori e agli amministratori di risolvere i problemi relativi a prestazioni lente per i report. Si applica ai report di Power BI e anche ai report impaginati di Power BI.

I report lenti possono essere identificati dagli utenti dei report che notano lentezza nel caricamento o per l'aggiornamento durante l'interazione con filtri dei dati o altre funzionalità. Quando i report sono ospitati in una capacità Premium, è anche possibile identificare i report lenti monitorando l'[app Metriche di Power BI Premium](../admin/service-admin-premium-monitor-capacity.md). Questa app consente di monitorare l'integrità e la capacità della sottoscrizione Power BI Premium.

## <a name="follow-flowchart-steps"></a>Seguire i passaggi del diagramma di flusso

Usare il diagramma di flusso seguente per comprendere la causa del rallentamento delle prestazioni e determinare l'azione da intraprendere.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Immagine che mostra il diagramma di flusso descritto in dettaglio nel testo dell'articolo." border="true":::

Sono presenti sei terminatori del diagramma di flusso, ognuno degli quali descrive l'azione da eseguire:

|Carattere di terminazione|Azioni|
|---------|---------|
|![Terminatore diagramma di flusso 1.](media/common/icon-01-red-30x30.png)|Gestire la capacità<br />Ridimensionare la capacità |
|![Terminatore diagramma di flusso 2.](media/common/icon-02-red-30x30.png)|Esaminare l'attività della capacità durante l'utilizzo tipico del report|
|![Terminatore diagramma di flusso 3.](media/common/icon-03-red-30x30.png)|Modifica dell'architettura<br />Prendere in considerazione Azure Analysis Services<br />Controllare il gateway locale|
|![Terminatore diagramma di flusso 4.](media/common/icon-04-red-30x30.png)|Prendere in considerazione Azure Analysis Services<br />Prendere in considerazione Power BI Premium|
|![Terminatore diagramma di flusso 5.](media/common/icon-05-red-30x30.png)|Usare l'analizzatore prestazioni di Power BI Desktop<br />Ottimizzare report, modello o DAX|
|![Terminatore diagramma di flusso 6.](media/common/icon-06-red-30x30.png)|Creare un ticket di supporto|

## <a name="take-action"></a>Intervieni

È prima di tutto necessario capire se il report lento è ospitato in una capacità Premium.

### <a name="premium-capacity"></a>Capacità Premium

Quando il report è ospitato in una capacità Premium, usare l'**app Metriche di Power BI Premium** per determinare se la capacità di hosting del report supera spesso le risorse di capacità. Questo è il caso, ad esempio, se l'utilizzo della CPU è spesso superiore al 80%. Per la memoria, è quando la [metrica della memoria attiva](../admin/service-premium-metrics-app.md#the-active-memory-metric) supera 50. In condizioni di pressione per le risorse potrebbe essere necessario [gestire o ridimensionare la capacità](../admin/service-admin-premium-manage.md) (terminatore del diagramma di flusso 1). Quando le risorse disponibili sono adeguate, esaminare l'attività della capacità durante l'utilizzo tipico del report (terminatore del diagramma di flusso 2).

### <a name="shared-capacity"></a>Capacità condivisa

Quando il report è ospitato in una capacità condivisa, non è possibile monitorare l'integrità della capacità. È necessario adottare un approccio diverso per le indagini.

Per prima cosa, determinare se le prestazioni lente si verificano in orari specifici del giorno o del mese. In caso affermativo e se molti utenti aprono il report in questi momenti, prendere in considerazione due opzioni:

- Aumentare la velocità effettiva delle query eseguendo la migrazione del set di dati ad [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) o a una capacità Premium (terminatore del diagramma di flusso 4).
- Usare [Analizzatore prestazioni](../create-reports/desktop-performance-analyzer.md) di Power BI Desktop per esaminare le prestazioni di tutti gli elementi del report, ad esempio oggetti visivi e formule DAX. Analizzatore prestazioni è particolarmente utile per determinare se il rendering della query o dell'oggetto visivo causa problemi di prestazioni (terminatore del diagramma di flusso 5).

Se non si riscontra un problema correlato al tempo, valutare se le prestazioni lente sono isolate in una specifica area geografica. Se questo è il caso, è probabile che l'origine dati sia remota e che le comunicazioni di rete siano lente. In questo caso, prendere in considerazione quanto segue:

- Modifica dell'architettura tramite [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (terminatore del diagramma di flusso 3).
- Ottimizzazione delle [prestazioni del gateway dati locale](/data-integration/gateway/service-gateway-performance) (terminatore del diagramma di flusso 3).

Infine, se si determina che non è presente un problema correlato al tempo _e_ che le prestazioni lente si verificano in tutte le aree, controllare se il problema di prestazioni riguarda dispositivi, client o Web browser specifici. Se questo non è il caso, usare [Analizzatore prestazioni](../create-reports/desktop-performance-analyzer.md) di Power BI Desktop, come descritto in precedenza, per ottimizzare il report o il modello (terminatore del diagramma di flusso 5).

Se si determina che dispositivi, client o Web browser specifici contribuiscono a rallentare le prestazioni, è consigliabile creare un ticket di supporto tramite la [pagina del supporto tecnico di Power BI](https://powerbi.microsoft.com/support/) (terminatore del diagramma di flusso 6).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Linee guida per Power BI](index.yml)
- [Monitoraggio delle prestazioni dei report](monitor-report-performance.md)
- [Analizzatore prestazioni](../create-reports/desktop-performance-analyzer.md)
- White paper: [Pianificazione della distribuzione aziendale di Power BI](https://go.microsoft.com/fwlink/?linkid=2057861)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
