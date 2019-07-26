---
title: Memorizzazione di query nella cache in Power BI Premium
description: Memorizzazione di query nella cache in Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/16/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: e45773784fbe97f8521ad071c03e86dcbddddbeb
ms.sourcegitcommit: 4689766f08f5285deac50bec595d57c3a398fff5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2019
ms.locfileid: "68329123"
---
# <a name="query-caching-in-power-bi-premium"></a>Memorizzazione di query nella cache in Power BI Premium

Le organizzazioni con Power BI Premium possono sfruttare la *memorizzazione di query nella cache* per velocizzare la produzione di report associati a un set di dati. La memorizzazione di query nella cache imposta la capacità Premium in modo che usi il servizio di memorizzazione nella cache locale per la gestione dei risultati, evitandone il calcolo nell'origine dati sottostante.

> [!IMPORTANT]
> La memorizzazione di query nella cache è disponibile solo in Power BI Premium. Non è applicabile ai set di dati LiveConnect che si basano su Azure Analysis Services o su SQL Server Analysis Services.

I risultati delle query memorizzate nella cache sono specifici per l'utente e il contesto del set di dati e rispettano sempre le regole di sicurezza. Attualmente il servizio esegue la memorizzazione di query nella cache solo per la pagina iniziale che viene visualizzata. In altre parole le query non vengono memorizzate nella cache quando si interagisce con il report. La cache delle query rispetta i [segnalibri personali](consumer/end-user-bookmarks.md#personal-bookmarks) e i [filtri permanenti](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/), pertanto le query generate da un report personalizzato verranno memorizzate nella cache. Anche i [riquadri del dashboard](service-dashboard-tiles.md) basati sulle stesse query traggono vantaggi a livello di prestazioni quando le query vengono memorizzate nella cache. Il vantaggio in termini di prestazioni è particolarmente evidente quando si accede spesso a un set di dati che non richiede aggiornamenti frequenti. La memorizzazione di query nella cache può anche ridurre il carico di lavoro della capacità Premium, riducendo il numero complessivo di query.

È possibile controllare il comportamento di memorizzazione query nella cache tramite la pagina **Impostazioni** del set di dati nel servizio Power BI. Le impostazioni possibili sono due:

- **Disattivata**: la memorizzazione di query nella cache non viene usata per questo set di dati.

- **Attivata**: la memorizzazione di query nella cache viene usata per questo set di dati.

![Finestra di dialogo Memorizzazione query nella cache](media/power-bi-query-caching/power-bi-query-caching.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

- Quando si modifica l'impostazione di memorizzazione di query nella cache da **Attivata** a **Disattivata**, tutti i risultati delle query del set di dati salvati in precedenza vengono rimossi dalla capacità della cache. È possibile disattivare la memorizzazione nella cache sia in modo esplicito sia ripristinando l'impostazione predefinita di capacità che un amministratore ha impostato su **Disattivata**. Se si disattiva la memorizzazione, alla successiva esecuzione di query su questo set di dati da parte di un report è possibile che si registri un leggero ritardo. Il ritardo è causato dalle query del report che vengono eseguite su richiesta e non si avvalgono dei risultati salvati. È anche possibile che il set di dati vada caricato in memoria prima di diventare disponibile per le query.
- Quando viene aggiornata la cache delle query, Power BI deve eseguire query nei modelli di dati sottostanti per ottenere i risultati più recenti. Se la memorizzazione nella cache è abilitata in un numero elevato di set di dati e la capacità Premium è soggetta a un carico elevato, potrebbe verificarsi una riduzione delle prestazioni durante l'aggiornamento della cache. Riduzione dei risultati a causa dall'aumento del volume delle query eseguite.

## <a name="next-steps"></a>Passaggi successivi

[Che cos'è Power BI Premium?](service-premium-what-is.md)

