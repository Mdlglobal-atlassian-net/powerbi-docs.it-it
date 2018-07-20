---
title: Mappe ad albero in Power BI
description: Mappe ad albero in Power BI
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b3f49487677f00e1026c9eab813633f470e6b41
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34295354"
---
# <a name="treemaps-in-power-bi"></a>Mappe ad albero in Power BI
Le mappe ad albero mostrano dati gerarchici in un set di rettangoli annidati.  Ogni livello della gerarchia è rappresentato da un rettangolo colorato (detto anche "ramo") che contiene altri rettangoli ("foglie").  Lo spazio all'interno di ogni rettangolo viene allocato in base al valore quantitativo misurato, con i rettangoli disposti per dimensione dall'angolo in alto a sinistra (più grande) all'angolo in basso a destra (più piccolo).

![](media/power-bi-visualization-treemaps/pbi-nancy_viz_treemap.png)

Ad esempio, se si analizzano le vendite, i rettangoli di livello superiore (rami) possono rappresentare le categorie di abbigliamento: **Urban**, **Rural**, **Youth**, and **Mix**.  I rettangoli delle categorie possono contenere rettangoli più piccoli (foglie) per le marche di abbigliamento nelle singole categorie e questi rettangoli più piccoli vengono dimensionati e ombreggiati il base al numero di articoli venduti.  Nel ramo **Urban** riportato sopra sono stati venduti molti capi Maximus, meno Natura e Fama e pochissimi Leo.  Quindi, il ramo **Urban** della mappa ad albero mostrerà un rettangolo più grande per Maximus (in alto a sinistra), rettangoli leggermente più piccoli per Natura e Fama, molti altri rettangoli che rappresentano tutti gli altri capi venduti e un piccolo rettangolo per Leo.  È anche possibile confrontare il numero di articoli venduti nelle altre categorie di abbigliamento confrontando la dimensione e l'ombreggiatura di ogni nodo foglia: più grande è il rettangolo e più scura è l'ombreggiatura, maggiore sarà il valore.

## <a name="when-to-use-a-treemap"></a>Quando usare una mappa ad albero
La mappe ad albero rappresentano un'ottima scelta nelle seguenti situazioni:

* per visualizzare grandi quantità di dati gerarchici.
* quando un grafico a barre non consente di gestire in modo efficiente un numero elevato di valori.
* per visualizzare le proporzioni tra le singole parti e l'insieme.
* per mostrare il modello di distribuzione della misura nei vari livelli di categorie nella gerarchia.
* per visualizzare gli attributi mediante la dimensione e la codifica a colori.
* per individuare modelli, outlier, elementi più importanti ed eccezioni.

### <a name="prerequisites"></a>Prerequisiti
 - Servizio Power BI o Power BI Desktop
 - Esempio di analisi delle vendite al dettaglio

## <a name="create-a-basic-treemap"></a>Creare una mappa ad albero di base
Se si preferisce prima assistere alla creazione di una mappa ad albero,  Andare al minuto 2:10 di questo video per vedere come creare una mappa ad albero.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

In alternativa, creare autonomamente una mappa ad albero personalizzata. Per queste istruzioni si usa l'esempio di analisi delle vendite al dettaglio. Per seguire la procedura, accedere al servizio Power BI (non a Power BI Desktop) e selezionare **Recupera dati \> Esempi \> Esempio di analisi delle vendite al dettaglio \> Connetti \>Passa al dashboard**. Per creare visualizzazioni in un report sono necessarie autorizzazioni di modifica per il set di dati e il report. Fortunatamente, gli esempi di Power BI sono modificabili. Tuttavia, in un report condiviso da un altro utente non sarà possibile aggiungere nuove visualizzazioni.

1. Selezionare il riquadro "Total Stores" per aprire il report di esempio di analisi delle vendite al dettaglio.    
2. Aprire la [visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md) e selezionare la misura **Sales** > **Last Years Sales**.   
   ![](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)   
3. Convertire il grafico in una mappa ad albero.  
   ![](media/power-bi-visualization-treemaps/treemapconvertto_new.png)   
4. Trascinare **Item** > **Category** nell'area **Gruppo**. Power BI crea una mappa ad albero in cui la dimensione dei rettangoli riflette il totale delle vendite e il colore rappresenta la categoria.  In sintesi, è stata creata una gerarchia che descrive visivamente la dimensione relativa del totale delle vendite per categoria.  La categoria **Mens** è quella con il volume di vendite maggiore, mentre la categoria **Hosiery** è quella con il volume minore.   
   ![](media/power-bi-visualization-treemaps/treemapcomplete_new.png)   
5. Trascinare**Store** > **Chain** nell'area **Dettagli** per completare la mappa ad albero. A questo punto è possibile confrontare le vendite dell'anno per categoria e catena.   
   ![](media/power-bi-visualization-treemaps/treemap_addgroup_new.png)
   
   > [!NOTE]
   > Le opzioni Saturazione colore e Dettagli non possono essere usate contemporaneamente.
   > 
   > 
5. Passare il mouse su un’area **Chain** per visualizzare la descrizione comando per la parte del titolo della **Categoria**.  Ad esempio, se si passa il puntatore del mouse su **Lindseys** nel rettangolo **040-Juniors** viene visualizzata la descrizione comando per la parte relativa a Lindsey della categoria Juniors.  
   ![](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)
6. [Aggiungere la mappa ad albero come riquadro del dashboard (aggiungendo l'oggetto visivo)](service-dashboard-tiles.md). 
7. [Salvare il report](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato
Per informazioni sull'uso del riquadro Filtri, vedere [Aggiungere un filtro a un report](power-bi-report-add-filter.md).

Evidenziando una categoria o i dettagli in una mappa da albero vengono applicate l’evidenziazione incrociata e i filtri incrociati nelle altre visualizzazioni nella pagina del report e viceversa. Per seguire la procedura, aggiungere alcuni oggetti visivi alla stessa pagina oppure copiare e incollare la mappa ad albero in una pagina del report che già contiene altri oggetti visivi.

1. Nella mappa ad albero selezionare una voce Category o Chain all'interno di una categoria.  per evidenziare in modo incrociato le altre visualizzazioni nella pagina. Se ad esempio si seleziona **050-Shoes**, viene mostrato che l'anno scorso sono state vendute scarpe per 3.640.471 dollari, di cui 2.174.185 dollari riferiti a Fashions Direct.  
   ![](media/power-bi-visualization-treemaps/treemaphiliting.png)

2. Nel grafico a torta **Last Year Sales by Chain** selezionare la sezione **Fashions Direct** per applicare un filtro incrociato alla mappa ad albero.  
   ![](media/power-bi-visualization-treemaps/treemapnoowl.gif)    

3. Per gestire il modo in cui i grafici si evidenziano e applicano i filtri incrociati tra di loro, vedere [Interazioni tra le visualizzazioni in un report di Power BI](service-reports-visual-interactions.md).

## <a name="next-steps"></a>Passaggi successivi
[Aggiungere una visualizzazione a un dashboard](service-dashboard-pin-tile-from-report.md)  
[Power BI - Concetti di base](service-basic-concepts.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)  

