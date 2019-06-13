---
title: Procedure consigliate per le prestazioni di Power BI Embedded
description: Questo articolo offre indicazioni sulle procedure consigliate per l'analisi incorporata
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: d2e4a29b3dd7e36081458ff6ca51b0006a10466f
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750946"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Procedure consigliate per le prestazioni di Power BI Embedded

Questo articolo contiene suggerimenti su come velocizzare il rendering di report, dashboard e riquadri nell'applicazione

## <a name="embed-parameters"></a>Parametri di incorporamento

Il metodo Powerbi.embed() riceve alcuni parametri per incorporare un report, un dashboard o un riquadro. Questi parametri presentano implicazioni per le prestazioni.

### <a name="embed-url"></a>URL di incorporamento

Evitare di generare manualmente l'URL di incorporamento. Assicurarsi invece di ricevere l'URL di chiamando l'API [Get Reports](/rest/api/power-bi/reports/getreportsingroup), [Get Dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) o [Get Tiles](/rest/api/power-bi/dashboards/gettilesingroup). È stato aggiunto all'URL un nuovo parametro denominato **_config_** , usato per migliorare le prestazioni.

### <a name="permissions"></a>Autorizzazioni

Concedere le autorizzazioni per la **visualizzazione** se non si prevede di incorporare un report in **modalità di modifica**. In questo modo il codice di incorporamento non inizializza i componenti usati per la modalità di modifica.

### <a name="filters-bookmarks-and-slicers"></a>Filtri, segnalibri e filtri dei dati

In genere, gli oggetti visivi del report vengono salvati con i dati memorizzati nella cache. I dati memorizzati nella cache vengano usati per offrire le prestazioni percepite. I report eseguono il rendering dei dati memorizzati nella cache durante l'esecuzione delle query. Se sono disponibili filtri, segnalibri o filtri dei dati, i dati memorizzati nella cache non sono rilevanti. Quindi, gli oggetti visivi vengono visualizzati solo dopo aver eseguito la query visiva.

Se si incorporano report con gli stessi filtri, per evitare di passare un elenco di filtri nella configurazione del carico, salvare il report con i filtri già applicati.

## <a name="preload"></a>Precaricamento

Usare l'API JavaScript di *precaricamento* per migliorare le prestazioni per gli utenti finali.
Powerbi.preload() scarica JavaScript, file CSS e altri artefatti, che vengono usati successivamente per l'incorporamento in un report.

Chiamare il precaricamento se non si incorpora il report immediatamente. Ad esempio, se si incorpora un report facendo clic su un pulsante, è preferibile chiamare il precaricamento quando viene caricata la pagina precedente. Quando l'utente dell'applicazione fa clic sul pulsante, il rendering sarà più veloce.

## <a name="measure-performance"></a>Misurare le prestazioni

Per misurare le prestazioni, usare:

1. Loaded (Caricato): tempo trascorso fino all'inizializzazione del report (l'utente non vede la rotellina).
2. Rendered (Con rendering): tempo trascorso finché viene eseguito il rendering completo del report usando dati effettivi. L'evento con rendering viene generato ogni volta che il report viene di nuovo sottoposto a rendering, vale a dire, dopo l'applicazione di filtri. Per misurare prima un report, assicurarsi di eseguire i calcoli nel primo evento generato.

I dati memorizzati nella cache vengono sottoposti a rendering quando sono disponibili, ma non esiste ancora un evento per questi dati.

## <a name="update-tools-and-sdk-packages"></a>Aggiornare strumenti e pacchetti SDK

Mantenere gli strumenti e i pacchetti SDK aggiornati.

* Usare sempre la versione più recente di [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installare la versione più recente dell'[SDK del client Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Vengono continuamente rilasciati altri miglioramenti, quindi è opportuno verificarne regolarmente la disponibilità.

* Pacchetti da installare:
    * Pacchetto Npm: powerbi-client
    * Pacchetto NuGet: Microsoft.PowerBI.JavaScript

> [!Note]
> Tenere presente che il tempo di caricamento dipende principalmente dagli elementi rilevanti per il report e gli stessi dati, ad esempio il numero di oggetti visivi, le dimensioni dei dati e la complessità delle query e delle misure calcolate. Attenersi alle [procedure consigliate](../power-bi-reports-performance.md) per ottimizzare il tempo di caricamento dei report.

## <a name="next-steps"></a>Passaggi successivi

* [Procedure consigliate per le prestazioni dei report di Power BI](../power-bi-reports-performance.md)
* [Come risolvere i problemi di Power BI Embedded](embedded-troubleshoot.md)
* [Domande frequenti su Power BI Embedded](embedded-faq.md)
