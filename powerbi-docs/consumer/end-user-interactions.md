---
title: Informazioni sulle interazioni degli oggetti visivi in un report
description: Documentazione per gli utenti finali di Power BI che illustra come interagiscono gli oggetti visivi in una pagina di un report.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 3a73656d8de462dfc7d1d9e7ac742d588cc8c810
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71943900"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Filtro incrociato per gli oggetti visivi in un report di Power BI
Una delle funzionalità interessanti di Power BI è il modo in cui sono interconnessi tutti gli oggetti visivi in una pagina del report. Se si seleziona un punto dati in uno degli oggetti visivi, tutti gli altri oggetti visivi nella pagina che contengono tali dati cambiano in base alla selezione. 

![Video delle interazioni tra oggetti visivi](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Come gli oggetti visivi interagiscono reciprocamente

Per impostazione predefinita, selezionando un punto dati in un oggetto visivo in una pagina del report, viene applicato un filtro incrociato o un'evidenziazione incrociata agli altri oggetti visivi nella pagina. Il modo esatto in cui interagiscono gli oggetti visivi in una pagina viene impostato dal *progettista* del report. I *progettisti* hanno la possibilità di attivare e disattivare le interazioni tra gli oggetti visivi e di modificare il comportamento predefinito per filtro incrociato, evidenziazione incrociata e [drill](end-user-drill.md). 

Se non si conoscono ancora le gerarchie né i drill, per informazioni è possibile vedere [Eseguire il drill-down in Power BI](end-user-drill.md). 

Il filtro incrociato e l'evidenziazione incrociata possono essere utili per identificare in che modo un valore nei dati contribuisce a un altro. Se ad esempio si seleziona il segmento Moderation nel grafico ad anello, viene evidenziato il contributo da tale segmento a ogni colonna del grafico "Total units by Month" e viene filtrato il grafico a linee.

![Immagine delle interazioni tra oggetti visivi](media/end-user-interactions/power-bi-interactions.png)

Vedere [Informazioni su filtri ed evidenziazione](end-user-report-filter.md). 


  
> [!NOTE]
> I termini *filtro incrociato* ed *evidenziazione incrociata* vengono usati per distinguere il comportamento qui descritto da ciò che accade quando si usa il riquadro **Filtri** per filtrare ed evidenziare gli oggetti visivi.  

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se il report ha un oggetto visivo che supporta il [drill](end-user-drill.md) per impostazione predefinita, l'esecuzione del drill in un oggetto visivo non ha alcun impatto sugli altri oggetti visivi nella pagina del report.     
- Se si usa visualA per interagire con visualB, i filtri a livello di oggetto visivo da visualA verranno applicati a visualB.

## <a name="next-steps"></a>Passaggi successivi
[Come usare i filtri dei report](../power-bi-how-to-report-filter.md)
