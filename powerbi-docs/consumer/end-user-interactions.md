---
title: Informazioni sulle interazioni degli oggetti visivi in un report
description: Documentazione per gli utenti finali di Power BI che illustra come interagiscono gli oggetti visivi in una pagina di un report.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256288"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Filtro incrociato per gli oggetti visivi in un report di Power BI
Una delle funzionalità interessanti di Power BI è il modo in cui sono interconnessi tutti gli oggetti visivi in una pagina del report. Se si seleziona un punto dati in uno degli oggetti visivi, tutti gli altri oggetti visivi nella pagina che contengono tali dati cambiano in base alla selezione. 

![Video delle interazioni tra oggetti visivi](media/end-user-interactions/interactions.gif)

Per impostazione predefinita, selezionando un punto dati in una visualizzazione in una pagina del report, viene applicato un filtro incrociato o un'evidenziazione incrociata e viene eseguito il drill nelle altre visualizzazioni nella pagina. 

Questo può essere utile per identificare in che modo un valore nei dati contribuisce a un altro. Se ad esempio si seleziona il segmento Moderation nel grafico ad anello, viene evidenziato il contributo da tale segmento a ogni colonna del grafico Total units by Month e viene filtrato il grafico a linee sulla destra.

![Immagine delle interazioni tra oggetti visivi](media/end-user-interactions/power-bi-interactions.png)

Vedere [Informazioni su filtri ed evidenziazione](../power-bi-reports-filters-and-highlighting.md). 

Il modo esatto in cui interagiscono gli oggetti visivi in una pagina viene impostato dal *progettista* del report. I progettisti hanno la possibilità di attivare e disattivare la interazioni tra gli oggetti visivi e di modificare il comportamento predefinito per filtro incrociato, evidenziazione incrociata e drill. 
  
> [!NOTE]
> I termini *filtro incrociato* ed *evidenziazione incrociata* vengono usati per distinguere il comportamento qui descritto da ciò che accade quando si usa il riquadro **Filtri** per filtrare ed evidenziare le visualizzazioni.  

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se il report ha una visualizzazione che supporta il [drill](../power-bi-visualization-drill-down.md) per impostazione predefinita, l'esecuzione del drill in una visualizzazione non ha alcun impatto sulle altre visualizzazioni nella pagina del report.     
- Se si usa visualA per interagire con visualB, i filtri a livello di oggetto visivo da visualA verranno applicati a visualB.

## <a name="next-steps"></a>Passaggi successivi
[Come usare i filtri dei report](../power-bi-how-to-report-filter.md)
