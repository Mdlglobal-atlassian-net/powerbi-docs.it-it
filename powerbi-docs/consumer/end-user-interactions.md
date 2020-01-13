---
title: Informazioni sulle interazioni degli oggetti visivi in un report
description: Documentazione per gli utenti finali di Power BI che illustra come interagiscono gli oggetti visivi in una pagina di un report.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: dc8dad0417ac2ed6498fb7612900ebdbb0ce2a18
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75303845"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Filtro incrociato per gli oggetti visivi in un report di Power BI
Una delle funzionalità interessanti di Power BI è il modo in cui sono interconnessi tutti gli oggetti visivi in una pagina del report. Se si seleziona un punto dati in uno degli oggetti visivi, tutti gli altri oggetti visivi nella pagina che contengono tali dati cambiano in base alla selezione. 

![Video delle interazioni tra oggetti visivi](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Come gli oggetti visivi interagiscono reciprocamente

Per impostazione predefinita, selezionando un punto dati in un oggetto visivo in una pagina del report, viene applicato un filtro incrociato o un'evidenziazione incrociata agli altri oggetti visivi nella pagina. Il modo esatto in cui interagiscono gli oggetti visivi in una pagina viene impostato dal *progettista* del report. I *progettisti* hanno la possibilità di attivare e disattivare le interazioni tra gli oggetti visivi e di modificare il comportamento predefinito per filtro incrociato, evidenziazione incrociata e [drill](end-user-drill.md). 

Se non si conoscono ancora le gerarchie né i drill, per informazioni è possibile vedere [Eseguire il drill-down in Power BI](end-user-drill.md). 

### <a name="cross-filtering-and-cross-highlighting"></a>Filtro incrociato ed evidenziazione incrociata

Il filtro incrociato e l'evidenziazione incrociata possono essere utili per identificare in che modo un valore nei dati contribuisce a un altro. I termini *filtro incrociato* ed *evidenziazione incrociata* vengono usati per distinguere il comportamento qui descritto da ciò che accade quando si usa il riquadro **Filtri** per filtrare ed evidenziare gli oggetti visivi.  

Definiamo questi termini aiutandoci con le pagine di report seguenti. Il grafico ad anello "Total category volume by segment" ha due valori: "Moderation" e "Convenience". 

![Pagina del report](media/end-user-interactions/power-bi-interactions-before.png)

1. Vediamo cosa accade quando si seleziona **Moderation**.

    ![Pagina del report dopo la selezione del segmento Moderation del grafico ad anello](media/end-user-interactions/power-bi-interactions-after.png)

2. Il **filtro incrociato** rimuove i dati non pertinenti. Selezionando **Moderation** nel grafico ad anello viene applicato un filtro incrociato al grafico a linee. Il grafico a linee ora mostra solo i punti dati del segmento Moderation. 

3. L'**evidenziazione incrociata** mantiene tutti i punti dati originali, ma disattiva la parte che non si applica alla selezione. Selezionando **Moderation** nel grafico ad anello viene applicata l'evidenziazione incrociata all'istogramma. L'istogramma disattiva tutti i dati che si applicano al segmento Convenience ed evidenzia tutti i dati che si applicano al segmento Moderation. 


## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se il report ha un oggetto visivo che supporta il [drill](end-user-drill.md) per impostazione predefinita, l'esecuzione del drill in un oggetto visivo non ha alcun impatto sugli altri oggetti visivi nella pagina del report.     
- I filtri a livello di oggetto visivo vengono conservati quando si applica un filtro incrociato e l'evidenziazione incrociata ad altri oggetti visivi nella pagina del report. Se quindi l'oggetto visivo A dispone di filtri a livello di oggetto visivo applicati dal progettista del report o dall'utente e si usa tale oggetto visivo per interagire con l'oggetto visivo B, i filtri a livello di oggetto visivo di A verranno applicati a B.

    ![Pagina del report dopo la selezione del segmento Moderation del grafico ad anello](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Passaggi successivi
[Come usare i filtri dei report](../power-bi-how-to-report-filter.md)    


[Informazioni su filtri ed evidenziazione](end-user-report-filter.md). 
