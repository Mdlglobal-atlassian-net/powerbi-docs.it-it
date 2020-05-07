---
title: Grafici ad anello in Power BI
description: Grafici ad anello in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0e870163552e64594e574669ed8dea6937633282
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75757723"
---
# <a name="create-and-use-doughnut-charts-in-power-bi"></a>Creare e usare grafici ad anello in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un grafico ad anello è simile a un grafico a torta perché mostra la relazione delle parti rispetto a un intero. L'unica differenza è data dal fatto che il centro è vuoto e consente di inserire un'etichetta o un'icona.

## <a name="prerequisite"></a>Prerequisito

Questa esercitazione usa il [file Retail Analysis Sample PBIX](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu selezionare **File** > **Apri**
   
2. Trovare la copia del **file Retail Analysis Sample PBIX**

1. Aprire il **file Retail Analysis Sample PBIX** nella visualizzazione report ![Screenshot dell'icona della visualizzazione report](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selezione ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) per aggiungere una nuova pagina.


## <a name="create-a-doughnut-chart"></a>Creare un grafico ad anello

1. Iniziare da una pagina di report vuota e nel riquadro Campi selezionare **Sales** \> **Last Year Sales**.  
   
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


