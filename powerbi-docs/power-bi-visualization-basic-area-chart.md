---
title: Grafico ad aree di base (esercitazione)
description: 'Esercitazione: Grafico ad aree di base.'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c4a7a90a8647b4a5d2c76cefbba5041a6e31607d
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="basic-area-chart-tutorial"></a>Grafico ad aree di base (esercitazione)
Il grafico ad aree di base, detto anche grafico ad aree su più livelli, è basato sul grafico a linee. L'area compresa tra l'asse e la linea viene riempita con colori per indicare un volume. 

I grafici ad aree enfatizzano l'entità del cambiamento nel tempo e possono essere usati per attirare l'attenzione sul valore totale in una tendenza. Ad esempio, i dati che rappresentano il profitto nel tempo possono essere tracciati in un grafico ad aree per enfatizzare il profitto totale.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Quando usare un grafico ad aree di base
I grafici ad aree di base rappresentano un'ottima scelta nelle seguenti situazioni:

* per vedere e confrontare la tendenza del volume su diverse serie temporali 
* per singole serie che rappresentano un set fisicamente numerabile

### <a name="prerequisites"></a>Prerequisiti
 - Servizio Power BI
 - Esempio di analisi delle vendite al dettaglio

Per seguire la procedura, accedere a Power BI e selezionare **Recupera dati \> Esempi \> Esempio di analisi delle vendite al dettaglio**  Connetti e scegliere **Passa al dashboard**. 

## <a name="create-a-basic-area-chart"></a>Creare un grafico ad aree di base
 

1. Dal dashboard "Esempio di analisi delle vendite al dettaglio" selezionare il riquadro **Total Stores** per aprire il report "Esempio di analisi delle vendite al dettaglio".
2. Selezionare **Modifica report** per aprire il report in Visualizzazione di modifica.
3. Aggiungere una nuova pagina del report selezionando l'icona con il segno più (+) di colore giallo nella parte inferiore del report.
4. Creare un grafico ad aree che visualizzi le vendite dell'anno e le vendite dell'anno precedente per mese.
   
   a. Nel riquadro CAMPI selezionare **Sales \> Last Year Sales** e **This Year Sales > Value**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Convertire il grafico in un grafico ad area di base selezionando l'icona del grafico ad area nel riquadro VISUALIZZAZIONI.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Selezionare **Ora \> Mese** per aggiungerlo all'area **Asse**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Per visualizzare il grafico in base al mese, selezionare i puntini di sospensione (in alto a destra dell'oggetto visivo) e scegliere **Ordina per mese**.

## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato
Per informazioni sull'uso del riquadro FILTRI, vedere [Aggiungere un filtro a un report](power-bi-report-add-filter.md).

Per evidenziare un'area specifica nel grafico, selezionare l'area o il bordo superiore.  Diversamente da altri tipi di visualizzazioni, se nella stessa pagina sono presenti altre visualizzazioni, evidenziando un grafico ad area di base non viene applicato il filtro incrociato alle altre visualizzazioni nella pagina del report. Sono comunque una destinazione per i filtri incrociati applicati da altre visualizzazioni nella pagina del report. Per altre informazioni, vedere [Interazioni tra le visualizzazioni nei report](service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* I grafici ad aree di base non sono efficaci per il confronto di valori a causa dell'occlusione sulle aree su più livelli. Power BI usa la trasparenza per indicare la sovrapposizione di aree. Questo, tuttavia, risulta efficace solo in presenza di due o tre aree diverse. Quando si deve confrontare la tendenza con più di tre misure, provare a usare i grafici a linee. Quando si deve confrontare il volume con più di tre misure, provare a usare la mappa ad albero.

## <a name="next-steps"></a>Passaggi successivi
[Report in Power BI](service-reports.md)  
[Visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)  
[Power BI - Concetti di base](service-basic-concepts.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

