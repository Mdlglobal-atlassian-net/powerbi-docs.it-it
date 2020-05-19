---
title: Esempi di oggetti visivi Power BI
description: Questo articolo presenta alcuni esempi di oggetti visivi Power BI, inclusi i filtri dei dati, più di 20 tipi di grafici, WebGL e oggetti visivi e script R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132087"
---
# <a name="samples-of-power-bi-visuals"></a>Esempi di oggetti visivi di Power BI

È possibile scaricare, usare e modificare questi oggetti visivi Power BI da GitHub. Questi esempi illustrano come gestire situazioni comuni quando si usa Power BI per lo sviluppo.

## <a name="slicers"></a>Filtri dei dati

Un filtro dei dati riduce la quantità di dati visualizzati in altre visualizzazioni all'interno del report. I filtri dei dati sono uno dei diversi modi per filtrare i dati in Power BI.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Chiclet Slicer](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Visualizza pulsanti con immagini o testo che fungono da filtro interno all'area di disegno per altri oggetti visivi | [Filtro dei dati sequenza temporale](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Selettore di intervallo di date grafico che filtra per data | [Esempio di filtro dei dati](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Illustra l'uso dell'API di filtro avanzato

## <a name="charts"></a>Grafici

È possibile ispirarsi alla raccolta, inclusi grafici a barre, grafici a torta, Word Cloud e altro ancora.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Aster Plot](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Torsione su un grafico ad anello standard che usa un secondo valore per orientare l'angolo di apertura | [Grafico a punti](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Grafico a barre con elementi visivi aggiuntivi che forniscono contesto utile per tenere traccia degli obiettivi | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Soluzione grafica che visualizza le relazioni tra i dati in una matrice
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Dot Plot](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Visualizza la distribuzione delle frequenze in modo accattivante | [Indicatore KPI doppio](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Visualizza in modo efficiente due misure nel corso del tempo indicando le tendenze in una sequenza temporale comune | [Enhanced Scatter](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Miglioramenti del grafico a dispersione esistente
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Force Graph](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Diagramma di layout Force con tracciato curvo, utile per visualizzare le connessioni tra entità | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Grafico a barre che illustra una sequenza temporale o una pianificazione del progetto con risorse | [Mappa termina con tabella](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Confrontare i dati in modo semplice e intuitivo usando i colori di una tabella
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Istogramma](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualizza la distribuzione dei dati in un intervallo di tempo continuo o in un periodo di tempo determinato | [Grafico LineDot](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Grafico a linee animato con punti animati per presentare dati al pubblico | [Grafico Mekko](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Istogramma a colonne in pila 100% e grafico a barre in pila 100% combinati in un'unica vista
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Multi KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Una potente visualizzazione Multi KPI con una chiave KPI oltre a più grafici sparkline di dati di supporto | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Potente indicatore KPI con grafico a più linee ed etichette per data corrente, valore e varianze | [Power KPI Matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Esegue il monitoraggio delle scorecard bilanciate e di un numero illimitato di metriche e indicatori KPI in un elenco compatto e facile da leggere
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Grafico degli impulsi](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Questo grafico a linee con annotazioni per gli eventi principali è perfetto per raccontare storie con i dati| [Grafico radar](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Presenta più misure tracciate su un asse categorico, utile per confrontare gli attributi | [Diagramma di Sankey](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Diagramma di flusso in cui la larghezza della serie è proporzionale alla quantità del flusso
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Grafico di flusso](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Grafico ad area in pila con interpolazione uniforme, usato spesso per visualizzare valori nel tempo | [Grafico radiale](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Grafico ad anello multilivello per visualizzare i dati gerarchici| [Grafico Tornado](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Confronto dell'importanza relativa delle variabili tra due gruppi
 | <img src="media/samples/word-cloud.png" width="200">
 | [Cloud di parole](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Crea un oggetto visivo da testo ricorrente nei dati

## <a name="webgl"></a>WebGL

WebGL consente ai contenuti Web di usare un'API basata su OpenGL ES 2.0 per eseguire il rendering 2D e 3D in un canvas HTML.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Globe Map](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Rilevamento delle posizioni in una mappa 3D interattiva

## <a name="r-visuals"></a>Oggetti visivi R

Questi esempi illustrano come sfruttare la potenza analitica e visiva degli oggetti visivi R e degli script R.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Regole di associazione](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Individuare le relazioni tra dati apparentemente non correlati usando istruzioni if-then | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Trovare i gruppi di somiglianza nei dati usando l'algoritmo K-medie | [Clustering con outlier](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Trovare i gruppi di somiglianza e gli outlier nei dati
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Correlation plot](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Evidenziare le variabili più correlate in una tabella dati | [Grafico albero delle decisioni](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Diagramma a forma di albero schematico per determinare la probabilità statistica tramite il partizionamento ricorsivo | [Forecasting TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Previsioni di serie temporali per serie con più stagionalità tramite il modello TBATS
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Forecasting with ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Stimare i valori futuri in base ai dati cronologici usando ARIMA (Autoregressive Integrated Moving Avg) | [Tracciato a imbuto](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Individuare gli outlier nei dati con un tracciato a imbuto | [Rilevamento outlier](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Trovare gli outlier nei dati usando il metodo e il tracciato più appropriati
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Spline chart](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Visualizzare e comprendere i dati rumorosi | [Time series decomposition chart](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Comprendere i componenti delle serie temporali usando la "scomposizione di stagionalità e tendenza con Loess" | [Grafico delle previsioni basate su serie temporali](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Uso del modello di livellamento esponenziale per stimare valori futuri in base a valori osservati in precedenza

## <a name="next-steps"></a>Passaggi successivi

Per provare a creare oggetti visivi Power BI, vedere [esercitazione: Sviluppo di un oggetto visivo di Power BI](custom-visual-develop-tutorial.md).
