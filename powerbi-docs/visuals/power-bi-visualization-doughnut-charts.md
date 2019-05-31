---
title: Grafici ad anello in Power BI
description: Grafici ad anello in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c69113d245d47a4d2702f16f6cea21a6cbd3b0b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61136076"
---
# <a name="doughnut-charts-in-power-bi"></a>Grafici ad anello in Power BI
Un grafico ad anello è simile a un grafico a torta perché mostra la relazione delle parti rispetto a un intero. L'unica differenza è data dal fatto che il centro è vuoto e consente di inserire un'etichetta o un'icona.

## <a name="create-a-doughnut-chart"></a>Creare un grafico ad anello
Queste istruzioni usano l'esempio di analisi delle vendite al dettaglio per creare un grafico ad anello che mostra le vendite dell'anno corrente per categoria. Per seguire le istruzioni, [scaricare l'esempio](../sample-datasets.md) per il servizio Power BI o per Power BI Desktop.

1. Iniziare con una pagina del report vuota. Se si usa il servizio Power BI, assicurarsi di aprire il report nella [Visualizzazione di modifica](../service-interact-with-a-report-in-editing-view.md).

2. Dal riquadro Campi selezionare **Sales** \> **Last Year Sales**.  
   
3. Dal riquadro Visualizzazioni selezionare l'icona per il grafico ad anello ![icona del grafico ad anello](media/power-bi-visualization-doughnut-charts/power-bi-icon.png) per convertire il grafico a barre in un grafico ad anello. Se **Last Year Sales** non è nell'area **Valori**, trascinarlo in tale area.
     
   ![Riquadro di visualizzazione con grafico ad anello selezionato](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Selezionare **Elemento** \> **Categoria** per aggiungerlo all'area **Legenda**. 
     
    ![grafico ad anello accanto al riquadro Campi](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Facoltativamente, [modificare le dimensioni e il colore del testo del grafico](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* La somma dei valori del grafico ad anello deve essere pari al 100%.
* Un eccessivo numero di categorie ne rende difficile la lettura e l'interpretazione.
* I grafici ad anello sono particolarmente indicati per confrontare una specifica sezione con l'intero, invece di confrontare singole sezioni reciprocamente. 

## <a name="next-steps"></a>Passaggi successivi
[Grafici a imbuto in Power BI](power-bi-visualization-funnel-charts.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


