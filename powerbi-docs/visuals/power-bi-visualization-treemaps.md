---
title: Mappe ad albero in Power BI
description: Mappe ad albero in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408818"
---
# <a name="treemaps-in-power-bi"></a>Mappe ad albero in Power BI

Le mappe ad albero mostrano dati gerarchici in un set di rettangoli annidati. Ogni livello della gerarchia è rappresentato da un rettangolo colorato (ramo) che contiene rettangoli più piccoli (foglie). Power BI basa le dimensioni dello spazio all'interno di ogni rettangolo sul valore misurato. I rettangoli vengono disposti per dimensioni dall'angolo superiore sinistro (il più grande) all'angolo inferiore destro (il più piccolo).

![Screenshot di Count of Product by Category e della mappa ad albero Manufacturer.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Ad esempio, per l'analisi delle vendite potrebbero essere disponibili rami di primo livello per le categorie di abbigliamento: **Urban**, **Rural**, **Youth** e **Mix**. Power BI suddividerebbe i rettangoli delle categorie in foglie, per i produttori di abbigliamento all'interno di tale categoria. I rettangoli foglia verrebbero dimensionati e ombreggiati in base al numero di articoli venduti.

Nel ramo **Urban** citato in precedenza, è stato venduto un numero elevato di capi **VanArsdel**, un numero minore di capi **Natura** e **Fama** e solo pochi capi **Leo**. Il ramo **Urban** della mappa ad albero ha quindi:

* Il rettangolo più grande per **VanArsdel** nell'angolo superiore sinistro.

* Rettangoli leggermente più piccoli per **Natura** e **Fama**.

* Molti altri rettangoli per tutti gli altri capi venduti.

* Un rettangolo molto piccolo per **Leo**.

È anche possibile confrontare il numero di articoli venduti nelle altre categorie di abbigliamento confrontando le dimensioni e l'ombreggiatura di ogni nodo foglia: i rettangoli più grandi e più scuri rappresentano valori più alti.

Se si preferisce prima assistere alla creazione di una mappa ad albero, Andare al minuto 2:10 di questo video per vedere come creare una mappa ad albero.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>Quando usare una mappa ad albero

La mappe ad albero rappresentano un'ottima scelta nelle seguenti situazioni:

* Per visualizzare grandi quantità di dati gerarchici.

* Quando un grafico a barre non consente di gestire in modo efficiente un numero di valori elevato.

* Per visualizzare le proporzioni tra le singole parti e l'insieme.

* Per mostrare il modello di distribuzione della misura nei vari livelli di categorie nella gerarchia.

* Per visualizzare gli attributi mediante le dimensioni e la codifica a colori.

* Per individuare modelli, outlier, elementi con il maggiore contributo ed eccezioni.

## <a name="prerequisites"></a>Prerequisiti

* Servizio Power BI o Power BI Desktop

* Report Retail Analysis Sample

## <a name="get-the-retail-analysis-sample-report"></a>Ottenere il report Retail Analysis Sample

Per queste istruzioni si usa l'esempio di analisi delle vendite al dettaglio. Per creare una visualizzazione sono necessarie autorizzazioni di modifica per il set di dati e per il report. Fortunatamente, gli esempi di Power BI sono tutti modificabili. Non è possibile creare visualizzazioni nei report condivisi da altri utenti. Per seguire la procedura, scaricare il [report Retail Analysis Sample](../sample-datasets.md).

Dopo avere scaricato il set di dati **Retail Analysis Sample**, è possibile iniziare.

## <a name="create-a-basic-treemap"></a>Creare una mappa ad albero di base

Verrà creato un report e si aggiungerà una mappa ad albero semplice.

1. Da **Area di lavoro personale** selezionare **Set di dati** > **Crea report**.

    ![Screenshot di Set di dati > Crea report.](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. Dal riquadro **Campi** selezionare la misura **Sales** > **Last Year Sales**.

   ![Screenshot della selezione di Sales > Last Year Sales e dell'oggetto visivo risultante.](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. Selezionare l'icona della mappa ad albero ![Screenshot dell'icona della mappa ad albero](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) per convertire il grafico in una mappa ad albero.

   ![Screenshot della mappa ad albero senza configurazione.](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. Trascinare **Item** > **Category** nell'area **Gruppo**.

    Power BI crea una mappa ad albero in cui le dimensioni dei rettangoli si basano sul totale delle vendite e in cui il colore rappresenta la categoria. In sintesi, è stata creata una gerarchia che descrive visivamente la dimensione relativa del totale delle vendite per categoria. La categoria **Mens** è quella con il volume di vendite maggiore, mentre la categoria **Hosiery** è quella con il volume minore.

    ![Screenshot della mappa ad albero configurata.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Trascinare**Store** > **Chain** nell'area **Dettagli** per completare la mappa ad albero. A questo punto è possibile confrontare le vendite dell'anno per categoria e catena.

   ![Screenshot della mappa ad albero con Store > Chain aggiunto all'area Dettagli.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Le opzioni Saturazione colore e Dettagli non possono essere usate contemporaneamente.

1. Passare il mouse su un’area **Chain** per visualizzare la descrizione comando per la parte del titolo della **Categoria**.

    Se ad esempio si posiziona il mouse su **Fashions Direct** nel rettangolo **090-Home**, viene visualizzata la descrizione comando per la parte relativa a Fashions Direct della categoria Home.

   ![Screenshot della descrizione comando per Home visualizzata.](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. Aggiungere la mappa ad albero come [riquadro del dashboard (aggiungendo l'oggetto visivo)](../service-dashboard-tiles.md).

1. Salvare il [report](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato

Per informazioni sull'uso del riquadro **Filtri**, vedere [Aggiungere un filtro a un report](../power-bi-report-add-filter.md).

Se si evidenzia una **categoria** o un **dettaglio** in una mappa ad albero, vengono applicati l'evidenziazione incrociata e i filtri incrociati nelle altre visualizzazioni della pagina del report e viceversa. Per seguire la procedura, aggiungere alcuni oggetti visivi alla pagina del report o copiare la mappa ad albero in una delle altre pagine in questo report.

1. Nella mappa ad albero selezionare una voce **Category** o **Chain** all'interno di una **categoria**. Verrà applicata l'evidenziazione incrociata alle altre visualizzazioni nella pagina. Se si seleziona **050-Shoes**, ad esempio, viene mostrato che l'anno scorso sono state vendute scarpe per **3.640.471** dollari, di cui **2.174.185** dollari riferiti a **Fashions Direct**.

   ![Screenshot del report Store Sales Overview che mostra l'evidenziazione incrociata.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. Nel grafico a torta **Last Year Sales by Chain** selezionare la sezione **Fashions Direct** per applicare un filtro incrociato alla mappa ad albero.
   ![Dimostrazione GIF della funzionalità filtro incrociato.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Per gestire il modo in cui i grafici applicano reciprocamente l'evidenziazione incrociata e il filtro incrociato, vedere [Modificare l'interazione degli oggetti visivi in un report di Power BI](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Passaggi successivi

* [Grafici a cascata in Power BI](power-bi-visualization-waterfall-charts.md)

* [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
