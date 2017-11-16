---
title: Grafici a dispersione in Power BI (esercitazione)
description: 'Esercitazione: Grafici a dispersione in Power BI'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: PVcfPoVE3Ys
qualityfocus: identified
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: c1801db4135d6d97a940e593de37ca2886194b53
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="scatter-charts-and-bubble-charts-in-power-bi-tutorial"></a>Grafici a dispersione e grafici a bolle in Power BI (esercitazione)
Un grafico a dispersione ha sempre due assi di valori per mostrare un set di valori numerici lungo un asse orizzontale e un altro set di dati numerici lungo un asse verticale. Nel grafico vengono visualizzati i punti in corrispondenza dell'intersezione di un valore numerico x e un valore numerico y, combinando questi valori in punti dati singoli. Questi punti dati possono essere distribuiti uniformemente o in maniera non uniforme sull'asse orizzontale, a seconda dei dati.

Un grafico a bolle sostituisce i punti dati con bolle, con le *dimensioni* della bolla che rappresentano una dimensione aggiuntiva dei dati.

![](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>Quando usare un grafico a dispersione o un grafico a bolle
### <a name="scatter-charts-are-a-great-choice"></a>I grafici a dispersione rappresentano un'ottima scelta nelle seguenti situazioni:
* per visualizzare le relazioni tra 2 (a dispersione) o 3 (a bolle) valori **numerici** .
* Per tracciare due gruppi di numeri come un'unica serie di coordinate xy.
* al posto di un grafico a linee quando si desidera modificare la scala dell'asse orizzontale    
* per attivare l'asse orizzontale in una scala logaritmica.
* per visualizzare i dati del foglio di lavoro che include valori a coppie o a insiemi raggruppati. In un grafico a dispersione, è possibile regolare le scale indipendenti degli assi per visualizzare ulteriori informazioni sui valori raggruppati.
* per visualizzare modelli in grandi set di dati, ad esempio tramite la visualizzazione di tendenze lineare o non lineari, cluster e outlier.
* per confrontare un numero elevato di punti dati indipendentemente dal tempo. Più dati si includono in un grafico a dispersione, migliori saranno i confronti apportati.

### <a name="bubble-charts-are-a-great-choice"></a>I grafici a bolle rappresentano un'ottima scelta nelle seguenti situazioni:
* se i dati dispongono di 3 serie di dati contenenti ciascuna un set di valori.
* per presentare i dati finanziari.  Dimensioni delle bolle diverse sono utili per evidenziare visivamente valori specifici.
* per utilizzare i quadranti.

## <a name="create-a-scatter-chart"></a>Creare un grafico a dispersione
<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Aprire l'esempio di analisi delle vendite al dettaglio in [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md) e [aggiungere una nuova pagina di report](power-bi-report-add-page.md).
2. Dal riquadro Campi, selezionare **Vendite** > **Vendite per piede quadrato** e **Vendite** > **% di varianza delle vendite**.
3. Selezionare **District > District** dal riquadro Campi.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_pre_convert.png)
4. Convertire in un grafico a dispersione. Dal riquadro Visualizzazione selezionare l'icona del grafico a dispersione.
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_icon.png).
5. Trascinare **Zona** da **Dettagli** in **Legenda**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_new.png)

È ora disponibile un grafico a dispersione che tiene traccia della % della varianza delle vendite totali lungo l'asse Y e delle vendite per ogni piede quadrato lungo l'asse X.  I colori del punto dati rappresentano le zone.  Ora si aggiungerà una terza dimensione.

## <a name="create-a-bubble-chart"></a>Creare un grafico a bolle
1. Dal riquadro Campi, trascinare **Vendite** > **Vendite di quest’anno** > **Valore** all’area **Dimensioni**. 
   
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_size.png)
2. Passare il mouse su una bolla.  La dimensione della bolla riflette il valore delle **Vendite di quest’anno**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)
3. Facoltativamente, [formattare i colori della visualizzazione, le etichette, i titoli, lo sfondo e altro ancora](service-getting-started-with-color-formatting-and-axis-properties.md).

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
### <a name="your-scatter-chart-has-only-one-data-point"></a>**Il grafico a dispersione presenta solo un punto dati**
Il grafico a dispersione ha solo un punto dati che aggrega tutti i valori sugli assi X e Y?  O forse aggrega tutti i valori lungo una singola riga orizzontale o verticale?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Aggiungere un campo all’area **Dettagli** per indicare a Power BI come raggruppare i valori. Il campo deve essere univoco per ogni punto che si desidera tracciare.  
Ad esempio un numero di riga semplice o un campo ID:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

O se non si dispone di questo nei dati, è possibile creare un campo che concatena i valori X e Y in un elemento univoco per ogni punto:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Per creare un nuovo campo, [usare l'Editor di query di Power BI Desktop per aggiungere una colonna indice](desktop-add-custom-column.md) al set di dati.  Quindi aggiungere la colonna all’area **Dettagli** della visualizzazione.

## <a name="next-steps"></a>Passaggi successivi
 [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Provalo gratuitamente](https://powerbi.com/)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

