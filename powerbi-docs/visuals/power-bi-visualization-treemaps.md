---
title: Mappe ad albero in Power BI
description: Mappe ad albero in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b70e9611b22f1df20d39cdbd338fd5b6bfe1b43d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73880739"
---
# <a name="treemaps-in-power-bi"></a>Mappe ad albero in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

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

   > [!NOTE]
   > Questo video usa una versione precedente di Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>Quando usare una mappa ad albero

La mappe ad albero rappresentano un'ottima scelta nelle seguenti situazioni:

* Per visualizzare grandi quantità di dati gerarchici.

* Quando un grafico a barre non consente di gestire in modo efficiente un numero di valori elevato.

* Per visualizzare le proporzioni tra le singole parti e l'insieme.

* Per mostrare il modello di distribuzione della misura nei vari livelli di categorie nella gerarchia.

* Per visualizzare gli attributi mediante le dimensioni e la codifica a colori.

* Per individuare modelli, outlier, elementi con il maggiore contributo ed eccezioni.

## <a name="prerequisite"></a>Prerequisito

Questa esercitazione usa il [file Retail Analysis Sample PBIX](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu selezionare **File** > **Apri**
   
2. Trovare la copia del **file Retail Analysis Sample PBIX**

1. Aprire il **file Retail Analysis Sample PBIX** nella visualizzazione report ![Screenshot dell'icona della visualizzazione report](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Select ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) per aggiungere una nuova pagina.


Dopo avere scaricato il set di dati **Retail Analysis Sample**, è possibile iniziare.

## <a name="create-a-basic-treemap"></a>Creare una mappa ad albero di base

Verrà creato un report e si aggiungerà una mappa ad albero semplice.


1. Dal riquadro **Campi** selezionare la misura **Sales** > **Last Year Sales**.

   ![Screenshot della selezione di Sales > Last Year Sales e dell'oggetto visivo risultante.](media/power-bi-visualization-treemaps/treemapfirstvalue-new.png)

1. Selezionare l'icona della mappa ad albero ![Screenshot dell'icona della mappa ad albero](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) per convertire il grafico in una mappa ad albero.

   ![Screenshot della mappa ad albero senza configurazione.](media/power-bi-visualization-treemaps/treemapconvertto-new.png)

1. Selezionare **Elemento** > **Categoria** per aggiungere **Categoria** all'area **Gruppo**.

    Power BI crea una mappa ad albero in cui le dimensioni dei rettangoli si basano sul totale delle vendite e in cui il colore rappresenta la categoria. In sintesi, è stata creata una gerarchia che descrive visivamente la dimensione relativa del totale delle vendite per categoria. La categoria **Mens** è quella con il volume di vendite maggiore, mentre la categoria **Hosiery** è quella con il volume minore.

    ![Screenshot della mappa ad albero configurata.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Selezionare **Store** > **Chain** per aggiungere **Chain** nell’area **Dettagli** per completare la mappa ad albero. A questo punto è possibile confrontare le vendite dell'anno per categoria e catena.

   ![Screenshot della mappa ad albero con Store > Chain aggiunto all'area Dettagli.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Le opzioni Saturazione colore e Dettagli non possono essere usate contemporaneamente.

1. Passare il mouse su un’area **Chain** per visualizzare la descrizione comando per la parte del titolo della **Categoria**.

    Se ad esempio si posiziona il mouse su **Fashions Direct** nel rettangolo **090-Home**, viene visualizzata la descrizione comando per la parte relativa a Fashions Direct della categoria Home.

   ![Screenshot della descrizione comando per Home visualizzata.](media/power-bi-visualization-treemaps/treemaphoverdetail-new.png)


## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato

Se si evidenzia una **categoria** o un **dettaglio** in una mappa ad albero, vengono applicati l'evidenziazione incrociata e i filtri incrociati nelle altre visualizzazioni nella pagina del report. Per seguire la procedura, aggiungere alcuni oggetti visivi alla pagina del report o copiare la mappa ad albero in una delle altre pagine in questo report. La mappa ad albero illustrata di seguito è stata copiata nella pagina **Overview**. 

1. Nella mappa ad albero selezionare una voce **Category** o **Chain** all'interno di una **categoria**. Verrà applicata l'evidenziazione incrociata alle altre visualizzazioni nella pagina. Se si seleziona **050-Shoes**, ad esempio, viene mostrato che l'anno scorso sono state vendute scarpe per **16.352.432** dollari, di cui **2.174.185** dollari riferiti a **Fashions Direct**.

   ![Screenshot del report Store Sales Overview che mostra l'evidenziazione incrociata.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. Nel grafico a torta **Last Year Sales by Chain** selezionare la sezione **Fashions Direct** per applicare un filtro incrociato alla mappa ad albero.
   ![Dimostrazione GIF della funzionalità filtro incrociato.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Per gestire il modo in cui i grafici applicano reciprocamente l'evidenziazione incrociata e il filtro incrociato, vedere [Modificare l'interazione degli oggetti visivi in un report di Power BI](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Passaggi successivi

* [Grafici a cascata in Power BI](power-bi-visualization-waterfall-charts.md)

* [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
