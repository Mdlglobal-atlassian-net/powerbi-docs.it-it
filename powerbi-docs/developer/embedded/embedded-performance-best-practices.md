---
title: Procedure consigliate per le prestazioni di Power BI Embedded
description: Questo articolo offre indicazioni sulle procedure consigliate per l'analisi incorporata
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: c619f37ac062eec02eb379ba7cd97731254a171a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279389"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Procedure consigliate per le prestazioni di Power BI Embedded

Questo articolo contiene suggerimenti su come velocizzare il rendering di report, dashboard e riquadri nell'applicazione.

> [!Note]
> Tenere presente che il tempo di caricamento dipende principalmente dagli elementi rilevanti per il report e dai dati, inclusi gli oggetti visivi, le dimensioni dei dati e la complessità delle query e delle misure calcolate. Per altre informazioni, vedere la [Guida all'ottimizzazione per Power BI](../../guidance/power-bi-optimization.md).

## <a name="update-tools-and-sdk-packages"></a>Aggiornare strumenti e pacchetti SDK

Mantenere gli strumenti e i pacchetti SDK aggiornati.

* Usare sempre la versione più recente di [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installare la versione più recente dell'[SDK del client Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Vengono continuamente rilasciati miglioramenti aggiuntivi, quindi è opportuno verificarne regolarmente la disponibilità.

## <a name="embed-parameters"></a>Parametri di incorporamento

Il metodo `powerbi.embed(element, config)` riceve un elemento e una configurazione. Il parametro config include campi con implicazioni sulle prestazioni.

### <a name="embed-url"></a>URL di incorporamento

Evitare di generare manualmente l'URL di incorporamento. Assicurarsi invece di ricevere l'URL di incorporamento chiamando l'API [Get Reports](/rest/api/power-bi/reports/getreportsingroup), [Get dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) o [Get tiles](/rest/api/power-bi/dashboards/gettilesingroup). È stato aggiunto all'URL un nuovo parametro denominato **_config_** , usato per migliorare le prestazioni.

### <a name="permissions"></a>Autorizzazioni

Concedere le autorizzazioni per la **visualizzazione** se non si prevede di incorporare un report in modalità di modifica. In questo modo il codice incorporato non inizializza i componenti usati in modalità di modifica.

### <a name="filters-bookmarks-and-slicers"></a>Filtri, segnalibri e filtri dei dati

In genere, gli oggetti visivi del report vengono salvati con i dati memorizzati nella cache. I dati memorizzati nella cache vengano usati per offrire le prestazioni percepite. I report eseguono il rendering dei dati memorizzati nella cache durante l'esecuzione delle query. Se vengono specificati filtri, segnalibri o filtri dei dati, i dati memorizzati nella cache non sono rilevanti e il rendering degli oggetti visivi viene eseguito solo dopo il termine della query.

Se si incorporano report con gli stessi filtri, segnalibri e filtri dei dati, per migliorare le prestazioni salvare il report con i filtri, i segnalibri e i filtri dei dati già applicati. In questo modo viene eseguito il rendering del report con i dati memorizzati nella cache che includono filtri, segnalibri e filtri dei dati.

## <a name="switching-between-reports"></a>Spostamento tra report

Quando si incorporano più report nello stesso iFrame, non generare un nuovo iFrame per ogni report. Usare invece `powerbi.embed(element, config)` con una configurazione diversa per incorporare il nuovo report.

> [!NOTE]
> Lo spostamento tra report per uno scenario in cui i dati sono di proprietà dell'app potrebbe non essere molto efficace a causa della necessità di generare un nuovo token di incorporamento.

## <a name="query-caching"></a>Memorizzazione di query nella cache

Le organizzazioni con capacità Power BI Premium o Power BI Embedded possono sfruttare la memorizzazione di query nella cache per velocizzare la produzione di report associati a un set di dati.

[Altre informazioni sulla memorizzazione di query nella cache in Power BI](../../connect-data/power-bi-query-caching.md).

## <a name="preload"></a>Precaricamento

Usare `powerbi.preload()` per migliorare le prestazioni per l'utente finale. Il metodo `powerbi.preload()` scarica JavaScript, file con estensione css e altri artefatti, che vengono usati in seguito per l'incorporamento di un report.

Se non si incorpora immediatamente il report, chiamare `powerbi.preload()`. Se ad esempio il contenuto incorporato di Power BI non viene visualizzato nella home page, usare `powerbi.preload()` per scaricare e memorizzare nella cache gli artefatti usati per incorporare il contenuto.

## <a name="bootstrapping-the-iframe"></a>Bootstrap dell'iFrame

> [!NOTE]
> Per eseguire il bootstrap dell'iFrame è necessario [Power BI client SDK](https://github.com/Microsoft/PowerBI-JavaScript) versione 2.9.

`powerbi.bootstrap(element, config)` consente di iniziare l'incorporamento prima che siano disponibili tutti i parametri necessari. L'API di bootstrap prepara e inizializza l'iFrame.
Quando si usa l'API di bootstrap, è comunque necessario chiamare `powerbi.embed(element, config)` sullo stesso elemento HTML.

Ad esempio uno dei casi d'uso di questa funzionalità è l'esecuzione in parallelo del bootstrap dell'iFrame e delle chiamate back-end per l'incorporamento.
> [!TIP]
> Usare l'API di bootstrap quando è possibile generare l'iFrame prima che sia visibile per l'utente finale.

[Altre informazioni sul bootstrap dell'iFrame](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Misurare le prestazioni

### <a name="performance-events"></a>Eventi di prestazioni

Per misurare le prestazioni incorporate, è possibile usare due eventi:

1. Evento caricato: tempo di inizializzazione del report. Il logo di Power BI scomparirà al termine del caricamento.
2. Evento con rendering: tempo necessario per il rendering completo del report usando i dati effettivi. L'evento con rendering viene generato ogni volta che il report viene di nuovo sottoposto a rendering, ad esempio, dopo l'applicazione di filtri. Per misurare un report, assicurarsi di eseguire i calcoli sul primo evento generato.

Il rendering dei dati memorizzati nella cache viene eseguito quando disponibile ma non viene generato alcun evento aggiuntivo.

[Altre informazioni sulla gestione degli eventi](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Analizzatore prestazioni

Per esaminare le prestazioni degli elementi del report, è possibile usare l'analizzatore prestazioni in Power BI Desktop.
L'analizzatore prestazioni consente di visualizzare e registrare log che misurano le prestazioni di ogni report.

[Altre informazioni sull'analizzatore prestazioni](../../create-reports/desktop-performance-analyzer.md).

> [!NOTE]
> Ricordarsi sempre di confrontare le prestazioni del report incorporato con le prestazioni in powerbi.com. Questo può essere utile per comprendere l'origine dei problemi di prestazioni

## <a name="next-steps"></a>Passaggi successivi

* [Guida all'ottimizzazione per Power BI](../../guidance/power-bi-optimization.md)
* [Come risolvere i problemi di Power BI Embedded](embedded-troubleshoot.md)
* [Domande frequenti su Power BI Embedded](embedded-faq.md)
