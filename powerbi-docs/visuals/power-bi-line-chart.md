---
title: Grafici a linee in Power BI
description: Grafici a linee in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0654dccf55b1e13f26d8ecaabee0349f0e56afc6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65535791"
---
# <a name="line-charts-in-power-bi"></a>Grafici a linee in Power BI
Un grafico a linee è una serie di punti dati che sono rappresentati da punti e uniti da linee rette. Un grafico a linee può avere uno o più righe. I grafici a linee sono una X e un asse Y. 

![grafico a linee](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Creare un grafico a linee
Queste istruzioni l'uso di vendita e app di esempio di Marketing per creare un grafico a linee che visualizzi le vendite dell'anno per categoria. Per proseguire, scaricare l'app di esempio da appsource.com.

1. Iniziare con una pagina del report vuota. Se si usa il servizio Power BI, assicurarsi di aprire il report nella [Visualizzazione di modifica](../service-interact-with-a-report-in-editing-view.md).

2. Nel riquadro campi, selezionare **SalesFact** \> **Total units**e selezionare **Date** > **mese**.  Power BI crea un istogramma a colonne nell'area di disegno report.

    ![Selezionare il riquadro campi](media/power-bi-line-charts/power-bi-step1.png)

4. Convertire in un grafico a linee selezionando il modello di linea del grafico nel riquadro visualizzazioni. 

    ![Converti in grafico a linee](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtrare il grafico a linee per visualizzare i dati per gli anni 2012, 2014. Se il riquadro filtri è compresso, espanderlo. Nel riquadro campi, selezionare **data** \> **anno** e trascinarla nel riquadro filtri. Rilasciarla sotto l'intestazione **filtri di questo oggetto visivo**. 
     
    ![riga accanto al riquadro campi](media/power-bi-line-charts/power-bi-year-filter.png)

    Change **Advanced filters** al **filtri di base** e selezionare **2012**, **2013** e **2014**.

    ![Filtro per anno](media/power-bi-line-charts/power-bi-filter-year.png)

6. Facoltativamente, [modificare le dimensioni e il colore del testo del grafico](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Aumentare le dimensioni del carattere e modificare axisfont Y](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Aggiungere altre righe al grafico
I grafici a linee può avere molte righe diverse. E, in alcuni casi, i valori nelle righe potrebbero essere così divergenti che non contengono bene insieme. Esaminiamo l'aggiunta di altre righe al nostro corrente del grafico e quindi informazioni su come formattare il grafico quando i valori rappresentati dalle linee sono molto diversi. 

### <a name="add-additional-lines"></a>Aggiungere altre righe
Invece di esaminare le unità totali per tutte le aree come una singola riga nel grafico, è possibile suddividere i totale unità per area. Aggiungere altre righe trascinando **geografica** > **area** per l'area della legenda.

   ![Una riga per ogni area](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Usare due assi Y
Cosa accade se si desidera esaminare le vendite totali e totale unità nello stesso grafico? I numeri di vendita sono molto superiori a numeri di unità, rendendo inutilizzabile il grafico a linee. In effetti, la linea rossa per totale unità sembra essere zero.

   ![elevata divergenti valori](media/power-bi-line-charts/power-bi-diverging.png)

Per visualizzare valori altamente divergenti nello stesso grafico, utilizzare un grafico combinato. È possibile Scopri tutto sui grafici combinati leggendo [grafici combinati in Power BI](power-bi-visualization-combo-chart.md). Nell'esempio riportato di seguito, è possibile visualizzare le unità di vendita e totali tra loro nello stesso grafico mediante l'aggiunta di un secondo asse Y. 

   ![elevata divergenti valori](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* Un grafico a linee non può avere due assi Y.  È necessario usare invece un grafico combinato.
* Negli esempi precedenti, i grafici sono stati formattati per aumentare la dimensione del carattere, modificare il colore del carattere, aggiungere i titoli degli assi, allineare al centro il titolo del grafico e una legenda, avviare entrambi gli assi a zero e altro ancora. Il riquadro formattazione (icona del rullo) ha un set di opzioni per rendere l'aspetto di grafici nel modo desiderato per apparentemente infinito. Il modo migliore per imparare è possibile aprire il riquadro formattazione ed esplorare.

## <a name="next-steps"></a>Passaggi successivi

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


