---
title: Grafico combinato in Power BI (esercitazione)
description: "Esercitazione (con video) che mostra perché e come creare un grafico combinato in Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: lnv66cTZ5ho
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: c00ba74501a411743036c4514750bccbbae3eb00
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="combo-chart-in-power--tutorial"></a>Grafico combinato in Power BI (esercitazione)
Un grafico combinato in Power BI è una singola visualizzazione che combina un grafico a linee e un istogramma. La combinazione dei 2 grafici in uno permette di confrontare i dati in modo più rapido.

I grafici combinati possono avere uno o due assi Y.

## <a name="when-to-use-a-combo-chart"></a>Quando usare un grafico combinato
I grafici combinati rappresentano un'ottima scelta nelle seguenti situazioni:

* quando si ha un grafico a linee e un istogramma con lo stesso asse X.
* per confrontare più misure con intervalli di valori diversi.
* per illustrare la correlazione tra due misure in una visualizzazione.
* per verificare se una misura incontra la destinazione definita da un'altra misura
* per risparmiare spazio nell'area di disegno.

## <a name="create-a-basic-single-axis-combo-chart"></a>Creare un grafico combinato di base ad asse singolo
Questo video mostra come creare un grafico combinato usando l’esempio di analisi di vendite e marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Per creare un grafico combinato personalizzato, accedere a Power BI e selezionare **Recupera dati \> Esempi \> Esempio di analisi delle vendite al dettaglio**. 

1. Dal dashboard "Esempio di analisi delle vendite al dettaglio" selezionare il riquadro **Total Stores** per aprire il report "Esempio di analisi delle vendite al dettaglio".
2. Selezionare **Modifica report** per aprire il report in Visualizzazione di modifica.
3. [Aggiungere una nuova pagina del report](power-bi-report-add-page.md).
4. Creare un istogramma che visualizzi le vendite dell'anno e il margine lordo per mese.
   
    a.  Nel riquadro Campi selezionare **Sales** \> **This Year Sales** > **Value**.
   
    b.  Trascinare **Sales** \> **Gross Margin This Year** nell'area **Valore**.
   
    c.  Selezionare **Time** \> **FiscalMonth** per aggiungerlo all'area **Asse**. 
   
    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Selezionare i puntini di sospensione (...) nell'angolo in alto a destra della visualizzazione e selezionare **Sort by FiscalMonth**.
6. Convertire l'istogramma in un grafico combinato. Con l'istogramma selezionato, nel riquadro **Visualizzazioni** selezionare **Grafico a linee e istogramma a colonne raggruppate**.
   
    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. Dal riquadro **Campi** trascinare **Sales** \> **Last Year Sales** all’area **Valori riga**.
   
   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)
   
   Il grafico combinato dovrebbe essere simile al seguente:
   
   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Creare un grafico combinato con due assi
In questa attività, si confronteranno margine lordo e vendite.

1. Creare un nuovo grafico a linee che tiene traccia della % del margine lordo dello scorso anno per i singoli mesi.  La % di margine lordo nel mese di gennaio ammontava al 35%, in aprile al 45%, per poi diminuire nel mese di luglio e aumentare nuovamente in agosto. Si vedrà un modello simile per le vendite dell’anno scorso e di quest'anno?
   
   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Aggiungere **This Year Sales > Value** e **Last Year Sales** al grafico a linee. La scala della **&amp; del margine lordo dello scorso anno** è notevolmente ridotta rispetto a quella di **Vendite** , di conseguenza risulta difficile confrontarle.      
   
   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Per facilitare la lettura e l'interpretazione dell'oggetto visivo, convertire il grafico a linee in un grafico a linee e istogramma a colonne in pila.
   
   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Trascinare **% di margine lordo dello scorso anno** dai **Valori colonna** nei **Valori riga**. Power BI crea due assi, consentendo in tal modo di ridimensionare i set di dati in modo diverso: quello di sinistra misura i dollari, mentre quello di destra la percentuale.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-combochart.png)    

## <a name="add-titles-to-the-axes"></a>Aggiungere titoli agli assi
1. Selezionare l'icona del rullo ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) per aprire il riquadro di formattazione.
2. Selezionare la freccia rivolta verso il basso per espandere le opzioni relative all' **asse Y** .
3. Per **Asse Y (colonna)**, impostare **Posizione** su **A sinistra**, **Titolo** su **On**, **Stile** su **Mostra solo titolo** e **Visualizza** su **Milioni**.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-y-axis-column.png)
4. Anche in **Asse Y (colonna)** verificare che **Mostra secondario** sia impostato su **On**. In questo modo è possibile visualizzare le opzioni per la formattazione della parte di grafico a linee del grafico combinato.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-show-secondary.png)
5. Per **Asse Y (riga)**, lasciare **Posizione** su **A destra**, **Titolo** su **On** e impostare **Stile** su **Mostra solo titolo**.
   
   Il grafico combinato ora visualizzerà due assi, entrambi con un titolo.
   
   ![](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

Da qui è possibile:

* [Aggiungere il grafico combinato come riquadro del dashboard](service-dashboard-tiles.md).
* [Salvare il report](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato
Per informazioni sull'uso del riquadro Filtri, vedere [Aggiungere un filtro a un report](power-bi-report-add-filter.md).

Evidenziando una colonna o una linea in un grafico combinato viene applicato il filtro incrociato nelle altre visualizzazioni nella pagina del report e viceversa.

## <a name="next-steps"></a>Passaggi successivi
[Aggiungere una visualizzazione a un report](power-bi-report-add-visualizations-i.md)

[Visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI - Concetti di base](service-basic-concepts.md)

[Provalo gratuitamente](https://powerbi.com/)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

