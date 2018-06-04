---
title: Grafici ad anello in Power BI
description: Grafici ad anello in Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/23/2017
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5d8be3d160e8ea37ba9814c7bd78c3ad5a751d3b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34294197"
---
# <a name="doughnut-charts-in-power-bi"></a>Grafici ad anello in Power BI
Un grafico ad anello è simile a un grafico a torta perché mostra la relazione delle parti rispetto a un intero. L'unica differenza è data dal fatto che il centro è vuoto e consente di inserire un'etichetta o un'icona.

## <a name="create-a-doughnut-chart"></a>Creare un grafico ad anello
Queste istruzioni usano l'esempio di analisi delle vendite al dettaglio per creare un grafico ad anello che mostra le vendite dell'anno corrente per categoria. Per seguire le istruzioni, [scaricare l'esempio](sample-datasets.md) per il servizio Power BI (app.powerbi.com) o Power BI Desktop.

1. Iniziare in una [pagina di report vuota ](power-bi-report-add-page.md) e selezionare il campo **SalesStage** \> **Sales Stage**. Se si usa il servizio Power BI, assicurarsi di aprire il report nella [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md).

2. Dal riquadro Campi selezionare **Sales** \> **Last Year Sales**.  
   
3. Dal riquadro Visualizzazioni selezionare l'icona per il grafico ad anello ![icona del grafico ad anello]() per convertire il grafico a barre in un grafico ad anello. Se **Last Year Sales** non è nell'area **Valori**, trascinarlo in tale area.
     
   ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Selezionare **Elemento** \> **Categoria** per aggiungerlo all'area **Legenda**. 
     
    ![](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Facoltativamente, [modificare le dimensioni e il colore del testo del grafico](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* La somma dei valori del grafico ad anello deve essere pari al 100%.
* Un eccessivo numero di categorie ne rende difficile la lettura e l'interpretazione.
* I grafici ad anello sono particolarmente indicati per confrontare una specifica sezione con l'intero, invece di confrontare singole sezioni reciprocamente. 

## <a name="next-steps"></a>Passaggi successivi
[Report in Power BI](service-reports.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

