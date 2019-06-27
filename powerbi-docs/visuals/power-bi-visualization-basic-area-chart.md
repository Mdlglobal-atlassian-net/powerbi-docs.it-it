---
title: Grafico ad aree di base
description: Grafico ad aree di base.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fe1d2a6f086831a4ae6bd78d8669dce9459bffad
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839860"
---
# <a name="basic-area-chart"></a>Grafico ad aree di base
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
2. Selezionare **Modifica** per aprire il report in visualizzazione di modifica.
3. Aggiungere una nuova pagina del report selezionando l'icona con il segno più (+) di colore giallo nella parte inferiore del report stesso.
4. Creare un grafico ad aree che visualizzi le vendite dell'anno e le vendite dell'anno precedente per mese.
   
   a. Nel riquadro Campi selezionare **Sales \> Last Year Sales** e **This Year Sales > Value**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Convertire il grafico in un grafico ad area di base selezionando l'icona corrispondente nel riquadro Visualizzazioni.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Selezionare **Ora \> Mese** per aggiungerlo all'area **Asse**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Per visualizzare il grafico in base al mese, selezionare i puntini di sospensione (in alto a destra dell'oggetto visivo) e scegliere **Ordina per mese**. Per modificare l'ordinamento, selezionare di nuovo i puntini di sospensione e selezionare **Ordinamento crescente** oppure **Ordinamento decrescente**.

## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato
Per informazioni sull'uso del riquadro Filtri, vedere [Aggiungere un filtro a un report](../power-bi-report-add-filter.md).

Per evidenziare un'area specifica nel grafico, selezionare l'area o il bordo superiore.  Diversamente da altri tipi di visualizzazioni, se nella stessa pagina sono presenti altre visualizzazioni, evidenziando un grafico ad area di base non viene applicato il filtro incrociato alle altre visualizzazioni nella pagina del report. Sono comunque una destinazione per i filtri incrociati applicati da altre visualizzazioni nella pagina del report. 

1. Provare a selezionare il grafico ad area e a copiarlo in un'altra pagina del report (CTRL-C e CTRL-V).
2. Selezionare una delle aree ombreggiate e quindi l'altra. Si noterà che questa operazione non ha alcun effetto sulle altre visualizzazioni nella pagina.

    ![Vendite dell'anno in corso selezionate nel grafico ad area](media/power-bi-visualization-basic-area-chart/power-bi-select-area.png)

3. Selezionare ora un elemento in una delle altre visualizzazioni nella pagina, ad esempio una barra di un grafico a colonne o un mese in un grafico a linee. Si noti l'effetto sul grafico ad area, che viene filtrato.  

    ![Barra Ft Oglethorpe selezionata](media/power-bi-visualization-basic-area-chart/power-bi-filter.png) 

Per altre informazioni, vedere [Interazioni tra le visualizzazioni nei report](../service-reports-visual-interactions.md).


## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi   
* [Rendere il report più accessibile agli utenti con particolari esigenze](../desktop-accessibility.md)
* I grafici ad aree di base non sono efficaci per il confronto di valori a causa dell'occlusione sulle aree su più livelli. Power BI usa la trasparenza per indicare la sovrapposizione di aree. Questo, tuttavia, risulta efficace solo in presenza di due o tre aree diverse. Quando si deve confrontare la tendenza con più di tre misure, provare a usare i grafici a linee. Quando si deve confrontare il volume con più di tre misure, provare a usare la mappa ad albero.

## <a name="next-step"></a>Passaggio successivo
[Report in Power BI](power-bi-visualization-card.md)  

