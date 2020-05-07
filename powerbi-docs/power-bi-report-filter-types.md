---
title: Tipi di filtri nei report di Power BI
description: Aggiungere un filtro di pagina, di visualizzazione o di report a un report in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874411"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Tipi di filtri nei report di Power BI

I filtri non si comportano tutti allo stesso modo perché vengono creati in modo diverso. La modalità di creazione influisce sul loro comportamento in modalità di modifica all'interno del riquadro dei filtri. In questo articolo sono descritti i diversi tipi di filtri, con le varie modalità di creazione e finalità d'uso. Leggere come [aggiungere filtri ai report](power-bi-report-add-filter.md). 

![Riquadro filtro](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Per prima cosa, si esamineranno i due tipi di filtri più comuni: manuale e automatico.

## <a name="manual-filters"></a>Filtri manuali 

I filtri manuali sono i filtri che gli autori dei report possono trascinare e rilasciare in qualsiasi punto nel nuovo riquadro dei filtri. Gli utenti con autorizzazione di modifica del report possono modificare, eliminare, cancellare, nascondere, bloccare, rinominare oppure ordinare i filtri di questo tipo nel nuovo riquadro.

## <a name="automatic-filters"></a>Filtri automatici 

I filtri automatici sono i filtri che vengono aggiunti automaticamente al livello del riquadro dei filtri relativo agli oggetti visivi quando si crea un oggetto visivo. Questi filtri sono basati sui campi che costituiscono l'oggetto visivo. Gli utenti con autorizzazione di modifica del report possono modificare, cancellare, nascondere, bloccare, rinominare oppure ordinare i filtri di questo tipo nel nuovo riquadro. Non possono eliminare i filtri automatici perché l'oggetto visivo fa riferimento a tali campi.

## <a name="more-advanced-filters"></a>Altri filtri avanzati

Questi altri tipi di filtri sono meno comuni, ma è comunque importante comprenderne il funzionamento se vengono visualizzati nel report. Possono inoltre risultare utili per creare un filtro specifico, adatto al proprio report.

## <a name="include-and-exclude-filters"></a>Filtri di inclusione ed esclusione

I filtri di inclusione ed esclusione vengono aggiunti automaticamente al riquadro dei filtri quando si usa la funzionalità di inclusione o esclusione per un oggetto visivo. Gli utenti con autorizzazione di modifica del report possono eliminare, bloccare, nascondere oppure ordinare i filtri di questo tipo nel nuovo riquadro. Non possono modificare, cancellare o rinominare un filtro di inclusione o esclusione perché è associato alla funzionalità di inclusione ed esclusione degli oggetti visivi.

![Filtro di esclusione](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Filtri di drill-down

I filtri di drill-down vengono aggiunti automaticamente al riquadro dei filtri quando si usa la funzionalità di drill-down per un oggetto visivo nel report. Gli utenti con autorizzazione di modifica del report possono modificare o cancellare i filtri di questo tipo nel nuovo riquadro. Non possono eliminare, nascondere, bloccare, rinominare oppure ordinare un filtro di drill-down perché è associato alla funzionalità di drill-down degli oggetti visivi. Per rimuovere il filtro di drill-down, fare clic sul pulsante per il drill-up relativo all'oggetto visivo.

![Filtro di drill-down](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Filtri di cross-drill

I filtri di cross-drill vengono aggiunti automaticamente al nuovo riquadro quando un filtro di drill-down viene passato a un altro oggetto visivo nella pagina del report tramite la funzionalità di filtro incrociato o evidenziazione incrociata. Gli utenti con autorizzazione di modifica del report non possono eliminare, cancellare, nascondere, bloccare, rinominare oppure ordinare i filtri di questo tipo perché sono associati alla funzionalità di drill-down degli oggetti visivi. Non possono nemmeno modificare un filtro di cross-drill perché proviene dal drill-down in un altro oggetto visivo. Per rimuovere il filtro di drill-down, fare clic sul pulsante per il drill-up relativo all'oggetto visivo che passa il filtro.

## <a name="drillthrough-filters"></a>Filtri di drill-through

I filtri di drill-through vengono passati da una pagina all'altra tramite la funzionalità di drill-through. Vengono visualizzati nel riquadro di drill-through. Esistono due tipi di filtri di drill-through. Il primo tipo è quello che richiama il drill-through. Gli autori dei report possono modificare, eliminare, cancellare, nascondere o bloccare i filtri di questo tipo. Il secondo tipo è il filtro di drill-through che viene passato alla destinazione, in base ai filtri a livello di pagina della pagina di origine. Gli autori dei report possono modificare, eliminare o cancellare questo tipo di filtro di drill-through temporaneo. Non possono bloccare o nascondere questo filtro per gli utenti finali.

## <a name="url-filters"></a>Filtri URL

I filtri URL vengono inseriti nel nuovo riquadro aggiungendo un parametro di query URL. Gli utenti con autorizzazione di modifica del report possono modificare, eliminare o cancellare i filtri di questo tipo nel nuovo riquadro. Non possono nascondere, bloccare, rinominare o ordinare un filtro URL perché è associato al parametro dell'URL. Per eliminare il filtro, rimuovere il parametro dall'URL. Ecco un esempio di URL con un parametro:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![Filtro URL](media/power-bi-report-filter-types/power-bi-filter-url.png)

Leggere altre informazioni sui [filtri URL](service-url-filters.md).

## <a name="pass-through-filters"></a>Filtri pass-through

I filtri pass-through sono filtri a livello di oggetto visivo creati tramite domande e risposte. Gli autori possono eliminare, nascondere o ordinare tali filtri nel nuovo riquadro. Non possono tuttavia rinominarli, modificarli, cancellarli o bloccarli.

![Filtro pass-through con domande e risposte](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Tipi di filtri a confronto

Questa tabella mette a confronto le operazioni che possono essere eseguite dagli autori di report con i diversi tipi di filtri.

| Tipo di filtro | Edit | Deseleziona | Eliminazione | Nascondi | Lock | Ordinamento | Rinomina |
|----|----|----|----|----|----|----|----|
| Filtri manuali | Y | Y | Y | Y | Y | Y | Y |
| Filtri automatici | Y | Y | N | Y | Y | Y | Y |
| Filtri di inclusione/esclusione | N | N | Y | Y | Y | Y | N |
| Filtri di drill-down | Y | Y | N | N | N | N | N |
| Filtri di cross-drill | N | N | N | N | N | N | N |
| Filtri di drill-through (con richiamo di drill-through) | Y | Y | Y | Y | Y | N | N |
| Filtri di drill-through (temporanei) | Y | Y | Y | N | N | N | N |
| Filtri URL (temporanei) | Y | Y | Y | N | N | N | N |
| Filtri pass-through | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Passaggi successivi

[Aggiungere filtri ai report](power-bi-report-add-filter.md)

[Presentazione del riquadro Filtri del report](consumer/end-user-report-filter.md)

[Filtri ed evidenziazione nei report](power-bi-reports-filters-and-highlighting.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

