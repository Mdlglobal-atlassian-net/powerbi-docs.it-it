---
title: Memorizzazione di query nella cache in Power BI Premium
description: Memorizzazione di query nella cache in Power BI Premium
author: KesemSharabi
ms.author: kesharab
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/04/2019
LocalizationGroup: ''
ms.openlocfilehash: bf9248b29c71f42de9fed53ee0148847a8f60d30
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488638"
---
# <a name="query-caching-in-power-bi-premiumembedded"></a>Memorizzazione di query nella cache in Power BI Premium/Power BI Embedded

Le organizzazioni con Power BI Premium o Power BI Embedded possono sfruttare la *memorizzazione di query nella cache* per velocizzare la produzione di report associati a un set di dati. La memorizzazione di query nella cache imposta la capacità Premium/Embedded in modo che usi il servizio di memorizzazione nella cache locale per la gestione dei risultati, evitandone il calcolo nell'origine dati sottostante.

> [!IMPORTANT]
> La memorizzazione di query nella cache è disponibile solo in Power BI Premium o Power BI Embedded. Non è applicabile ai set di dati LiveConnect che si basano su Azure Analysis Services o su SQL Server Analysis Services.

I risultati delle query memorizzate nella cache sono specifici per l'utente e il contesto del set di dati e rispettano sempre le regole di sicurezza. Attualmente il servizio esegue la memorizzazione di query nella cache solo per la pagina iniziale che viene visualizzata. In altre parole le query non vengono memorizzate nella cache quando si interagisce con il report. La cache delle query rispetta i [segnalibri personali](consumer/end-user-bookmarks.md#personal-bookmarks) e i [filtri permanenti](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/), pertanto le query generate da un report personalizzato verranno memorizzate nella cache. Anche i [riquadri del dashboard](service-dashboard-tiles.md) basati sulle stesse query traggono vantaggi a livello di prestazioni quando le query vengono memorizzate nella cache. Il vantaggio in termini di prestazioni è particolarmente evidente quando si accede spesso a un set di dati che non richiede aggiornamenti frequenti. La memorizzazione di query nella cache può anche diminuire il carico di lavoro della capacità Premium/Embedded, riducendo il numero complessivo di query.

È possibile controllare il comportamento di memorizzazione query nella cache tramite la pagina **Impostazioni** del set di dati nel servizio Power BI. Le impostazioni possibili sono tre:

- **Capacità predefinita**: memorizzazione query nella cache disabilitata
- **Off**: la memorizzazione di query nella cache non viene usata per questo set di dati.
- **Attivata**: la memorizzazione di query nella cache viene usata per questo set di dati.

    ![Finestra di dialogo Memorizzazione query nella cache](media/power-bi-query-caching/power-bi-query-3-options.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limiti

- Quando si modifica l'impostazione di memorizzazione di query nella cache da **Attivata** a **Disattivata**, tutti i risultati delle query del set di dati salvati in precedenza vengono rimossi dalla capacità della cache. È possibile disattivare la memorizzazione nella cache sia in modo esplicito sia ripristinando l'impostazione predefinita di capacità che un amministratore ha impostato su **Disattivata**. Se si disattiva la memorizzazione, alla successiva esecuzione di query su questo set di dati da parte di un report è possibile che si registri un leggero ritardo. Il ritardo è causato dalle query del report che vengono eseguite su richiesta e non si avvalgono dei risultati salvati. È anche possibile che il set di dati vada caricato in memoria prima di diventare disponibile per le query.
- Quando viene aggiornata la cache delle query, Power BI deve eseguire query nei modelli di dati sottostanti per ottenere i risultati più recenti. Se la memorizzazione nella cache è abilitata in un numero elevato di set di dati e la capacità Premium/Embedded è soggetta a un carico elevato, potrebbe verificarsi una riduzione delle prestazioni durante l'aggiornamento della cache. Riduzione dei risultati a causa dall'aumento del volume delle query eseguite.

## <a name="next-steps"></a>Passaggi successivi

* [Che cos'è Power BI Premium?](service-premium-what-is.md)
* [Che cos'è Azure Power BI Embedded](developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
