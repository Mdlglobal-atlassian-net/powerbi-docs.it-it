---
title: Modificare l'interazione degli oggetti visivi in un report
description: Documentazione su come impostare le interazioni degli oggetti visivi in un report di Microsoft Power BI.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 126bd40e98a88138a2732155f9792d65666e52c7
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interazioni tra le visualizzazioni in un report di Power BI
Per impostazione predefinita, le visualizzazioni in una pagina di report possono essere usate per applicare un filtro incrociato e un'evidenziazione incrociata nelle altre visualizzazioni nella pagina.
Ad esempio, se si seleziona uno stato in una visualizzazione mappa, viene evidenziato l'istogramma e il grafico a linee viene filtrato in modo da visualizzare solo i dati applicabili allo stato selezionato.
Vedere [Informazioni su filtri ed evidenziazione](power-bi-reports-filters-and-highlighting.md).

Per modificare questo comportamento predefinito, usare il controllo **Interazione con oggetti visivi**. Le interazioni con oggetti visivi sono disponibili solo in [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md). Se un report è stato condiviso con l'utente corrente, non si avrà accesso alle interazioni con oggetti visivi.

> [!NOTE]
> I termini *filtro incrociato* ed *evidenziazione incrociata* vengono usati per distinguere il comportamento qui descritto da ciò che accade quando si usa il riquadro **Filtri** per filtrare ed evidenziare le visualizzazioni.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Selezionare una visualizzazione per attivarla.  
2. Selezionare l'opzione **Interazioni con oggetti visivi** nella barra dei menu superiore per attivarla. Notare le icone di filtro ed evidenziazione che appaiono quando si passa il mouse sulle altre visualizzazioni nella pagina del report.
   
    ![](media/service-reports-visual-interactions/pbi-visual-interaction-icon.png)
3. Determinare l'impatto che la visualizzazione selezionata dovrà avere sulle altre.  
   
   * Se deve applicare un filtro incrociato nelle altre visualizzazioni, selezionare l'icona del **filtro** ![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Se deve applicare un'evidenziazione incrociata nelle altre visualizzazioni, selezionare l'icona dell'**evidenziazione** ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Se non deve avere alcun impatto, selezionare l'icona che indica **nessun impatto** ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).
4. Facoltativamente, ripetere per tutte le altre visualizzazioni nella pagina del report.

### <a name="next-steps"></a>Passaggi successivi
[Come usare i filtri dei report](power-bi-how-to-report-filter.md)

[Filtri ed evidenziazione nei report](power-bi-reports-filters-and-highlighting.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

