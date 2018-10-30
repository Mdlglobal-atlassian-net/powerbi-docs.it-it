---
title: Informazioni su come interagiscono gli oggetti visivi in un report (per i consumer di report)
description: Documentazione per gli utenti finali di Power BI che illustra come interagiscono gli oggetti visivi in una pagina di un report.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c87f99b768f52fe7f6b565c47ed7e434b167a046
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112062"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interazioni tra le visualizzazioni in un report di Power BI
Una delle funzionalità interessanti di Power BI è il modo in cui sono interconnessi tutti gli oggetti visivi in una pagina del report. Se si seleziona un punto dati in uno degli oggetti visivi, tutti gli altri oggetti visivi nella pagina che contengono tali dati cambiano in base alla selezione. 

![Video delle interazioni tra oggetti visivi](media/end-user-interactions/interactions.gif)

Per impostazione predefinita, le visualizzazioni in una pagina di report possono essere usate per applicare un filtro incrociato o un'evidenziazione incrociata ed eseguire il drill nelle altre visualizzazioni nella pagina. Ad esempio, se si seleziona uno stato in una visualizzazione mappa, potrebbe essere evidenziato l'istogramma e il grafico a linee potrebbe essere filtrato in modo da visualizzare solo i dati applicabili allo stato selezionato.

Vedere [Informazioni su filtri ed evidenziazione](../power-bi-reports-filters-and-highlighting.md). Se è presente anche una visualizzazione che supporta il [drill](../power-bi-visualization-drill-down.md) per impostazione predefinita, l'esecuzione del drill in una visualizzazione non ha alcun impatto sulle altre visualizzazioni nella pagina del report. 

Il modo esatto in cui interagiscono gli oggetti visivi in una pagina viene impostato dal *progettista* del report. I progettisti hanno la possibilità di attivare e disattivare la interazioni tra gli oggetti visivi e di modificare il comportamento predefinito per filtro incrociato, evidenziazione incrociata e drill.
  
> [!NOTE]
> I termini *filtro incrociato* ed *evidenziazione incrociata* vengono usati per distinguere il comportamento qui descritto da ciò che accade quando si usa il riquadro **Filtri** per filtrare ed evidenziare le visualizzazioni.  

### <a name="next-steps"></a>Passaggi successivi
[Come usare i filtri dei report](../power-bi-how-to-report-filter.md)
