---
title: Memorizzazione di query nella cache in Power BI Premium
description: Memorizzazione di query nella cache in Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/03/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: fbfd8c98743144e0c9604aca4174d6ef32916e77
ms.sourcegitcommit: de0b72915183a8a784d3227838bd704c1c209422
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "58914277"
---
# <a name="query-caching-in-power-bi-premium"></a>Memorizzazione di query nella cache in Power BI Premium

Le organizzazioni con Power BI Premium possono sfruttare la *memorizzazione di query nella cache* per velocizzare la produzione di report associati a un set di dati. La memorizzazione di query nella cache imposta la capacità Premium in modo che usi il servizio di memorizzazione nella cache locale per la gestione dei risultati, evitandone il calcolo nell'origine dati sottostante.

> [!IMPORTANT]
> La memorizzazione di query nella cache è disponibile solo in Power BI Premium. Non è applicabile ai set di dati LiveConnect che si basano su Azure Analysis Services o su SQL Server Analysis Services.

I risultati delle query memorizzate nella cache sono specifici per l'utente e il contesto del set di dati e rispettano sempre le regole di sicurezza. Attualmente il servizio esegue la memorizzazione di query nella cache solo per la pagina iniziale che viene visualizzata. In altre parole le query non vengono memorizzate nella cache quando si interagisce con il report. La cache riflette i segnalibri personali e i filtri permanenti. Anche i [riquadri del dashboard](service-dashboard-tiles.md) basati sulle stesse query traggono vantaggi a livello di prestazioni quando le query vengono memorizzate nella cache. Il vantaggio in termini di prestazioni è particolarmente evidente quando si accede spesso a un set di dati che non richiede aggiornamenti frequenti. La memorizzazione di query nella cache può anche ridurre il carico di lavoro della capacità Premium, riducendo il numero complessivo di query.

È possibile controllare il comportamento di memorizzazione query nella cache tramite la pagina **Impostazioni** del set di dati nel servizio Power BI. Le impostazioni possibili sono tre:

- **Capacità predefinita**: Il set di dati eredita l'impostazione dalla capacità Premium. la capacità predefinita è controllata dall'amministratore di capacità di Power BI Premium.

- **Disattivata**: la memorizzazione di query nella cache non viene usata per questo set di dati.

- **Attivata**: la memorizzazione di query nella cache viene usata per questo set di dati.

![Finestra di dialogo Memorizzazione query nella cache](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> Quando si modifica l'impostazione di memorizzazione di query nella cache da **Attivata** a **Disattivata**, tutti i risultati delle query del set di dati salvati in precedenza vengono rimossi dalla capacità della cache. È possibile disattivare la memorizzazione nella cache sia in modo esplicito sia ripristinando l'impostazione predefinita di capacità che un amministratore ha impostato su **Disattivata**. Se si disattiva la memorizzazione, alla successiva esecuzione di query su questo set di dati da parte di un report è possibile che si registri un leggero ritardo. Il ritardo è causato dalle query del report che vengono eseguite su richiesta e non si avvalgono dei risultati salvati. È anche possibile che il set di dati vada caricato in memoria prima di diventare disponibile per le query.


