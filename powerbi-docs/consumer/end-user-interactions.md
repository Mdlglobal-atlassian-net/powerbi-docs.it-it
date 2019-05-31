---
title: Informazioni sulle interazioni degli oggetti visivi in un report
description: Documentazione per gli utenti finali di Power BI che illustra come interagiscono gli oggetti visivi in una pagina di un report.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413147"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Filtro incrociato per gli oggetti visivi in un report di Power BI
Una delle funzionalità interessanti di Power BI è il modo in cui sono interconnessi tutti gli oggetti visivi in una pagina del report. Se si seleziona un punto dati in uno degli oggetti visivi, tutti gli altri oggetti visivi nella pagina che contengono tali dati cambiano in base alla selezione. 

![Video delle interazioni tra oggetti visivi](media/end-user-interactions/interactions.gif)

Per impostazione predefinita, la selezione di un punto dati in una visualizzazione in una pagina del report sarà il filtro incrociato, un'evidenziazione incrociata e analizzare i dati nelle altre visualizzazioni nella pagina. 

Ciò può essere utile per identificare un valore nei dati contribuisce a un altro. Ad esempio, selezionando il segmento Moderation nel grafico ad anello, evidenzia il contributo da tale segmento a ogni colonna nel totale unità per il grafico di mese, e lo ha filtrato il grafico a linee sulla destra.

![immagine di oggetti visivi che interagiscono](media/end-user-interactions/power-bi-interactions.png)

Vedere [Informazioni su filtri ed evidenziazione](../power-bi-reports-filters-and-highlighting.md). 

Il modo esatto in cui interagiscono gli oggetti visivi in una pagina viene impostato dal *progettista* del report. I progettisti hanno la possibilità di attivare e disattivare la interazioni tra gli oggetti visivi e di modificare il comportamento predefinito per filtro incrociato, evidenziazione incrociata e drill. 
  
> [!NOTE]
> I termini *filtro incrociato* ed *evidenziazione incrociata* vengono usati per distinguere il comportamento qui descritto da ciò che accade quando si usa il riquadro **Filtri** per filtrare ed evidenziare le visualizzazioni.  

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se il report contiene una visualizzazione che supporti [drill](../power-bi-visualization-drill-down.md), per impostazione predefinita, eseguire il drill-una visualizzazione non ha alcun impatto sulle altre visualizzazioni nella pagina del report.     
- Se si usa visualA per interagire con visualB, filtri a livello di oggetto visivo da visualA verranno applicati a visualB.

## <a name="next-steps"></a>Passaggi successivi
[Come usare i filtri dei report](../power-bi-how-to-report-filter.md)
