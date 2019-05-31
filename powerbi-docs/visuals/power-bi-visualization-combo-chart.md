---
title: Grafico combinato in Power BI
description: Questa esercitazione sui grafici combinati spiega quando usarli e come crearli nel servizio Power BI e in Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e461480f53f4a97aeb4282e64a8a03eb8e1418d1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187810"
---
# <a name="combo-chart-in-power-bi"></a>Grafico combinato in Power BI
Un grafico combinato in Power BI è una singola visualizzazione che combina un grafico a linee e un istogramma. La combinazione dei 2 grafici in uno permette di confrontare i dati in modo più rapido.

I grafici combinati possono avere uno o due assi Y.

## <a name="when-to-use-a-combo-chart"></a>Quando usare un grafico combinato
I grafici combinati rappresentano un'ottima scelta nelle seguenti situazioni:

* quando si ha un grafico a linee e un istogramma con lo stesso asse X.
* per confrontare più misure con intervalli di valori diversi.
* per illustrare la correlazione tra due misure in una visualizzazione.
* per verificare se una misura incontra la destinazione definita da un'altra misura
* per risparmiare spazio nell'area di disegno.

### <a name="prerequisites"></a>Prerequisiti
I grafici combinati sono disponibili nel servizio Power BI e in Power BI Desktop. Questa esercitazione usa il servizio Power BI per creare un grafico combinato. Per seguire la procedura, aprire il servizio Power BI e connettersi all'Esempio di analisi delle vendite al dettaglio ([istruzioni più avanti](#create)).


## <a name="create-a-basic-single-axis-combo-chart"></a>Creare un grafico combinato di base ad asse singolo
Questo video mostra come creare un grafico combinato usando l’esempio di analisi di vendite e marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a> Per creare un grafico combinato personalizzato, accedere al servizio Power BI e selezionare **Recupera dati \> Esempi \> Esempio di analisi delle vendite al dettaglio &gt; Connetti &gt; Vai al dashboard**.

1. Dal dashboard "Esempio di analisi delle vendite al dettaglio" selezionare il riquadro **Total Stores** per aprire il report "Esempio di analisi delle vendite al dettaglio".
2. Selezionare **Modifica report** per aprire il report in Visualizzazione di modifica.
3. Aggiungere una nuova pagina del report.
4. Creare un istogramma che visualizzi le vendite dell'anno e il margine lordo per mese.

    a.  Nel riquadro Campi selezionare **Sales** \> **This Year Sales** > **Value**.

    b.  Trascinare **Sales** \> **Gross Margin This Year** nell'area **Valore**.

    c. Selezionare **Time** \> **FiscalMonth** per aggiungerlo all'area **Asse**.

    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Selezionare i puntini di sospensione (...) nell'angolo superiore destro della visualizzazione e selezionare **Sort by > FiscalMonth**. Per modificare l'ordinamento, selezionare di nuovo i puntini di sospensione e scegliere **Ordinamento crescente** oppure **Ordinamento decrescente**.

6. Convertire l'istogramma in un grafico combinato. Sono disponibili due grafici combinati: **Grafico a linee e istogramma a colonne in pila** e **Grafico a linee e istogramma a colonne raggruppate**. Con l'istogramma selezionato, nel riquadro **Visualizzazioni** selezionare **Grafico a linee e istogramma a colonne raggruppate**.

    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. Dal riquadro **Campi** trascinare **Sales** \> **Last Year Sales** all’area **Valori riga**.

   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   Il grafico combinato dovrebbe essere simile al seguente:

   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Creare un grafico combinato con due assi
In questa attività, si confronteranno margine lordo e vendite.

1. Creare un nuovo grafico a linee che tiene traccia **Gross Margin last year %** dal **FiscalMonth**. Selezionare i puntini di sospensione per ordinare per **mese** e in **ordine crescente**.  
La % di margine lordo nel mese di gennaio ammontava al 35%, in aprile al 45%, per poi diminuire nel mese di luglio e aumentare nuovamente in agosto. Si vedrà un modello simile per le vendite dell’anno scorso e di quest'anno?

   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Aggiungere **This Year Sales > Value** e **Last Year Sales** al grafico a linee. La scala usata per **Gross Margin Last Year %** è notevolmente ridotta rispetto a quella di **Sales**, di conseguenza risulta difficile confrontarle.      

   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Per facilitare la lettura e l'interpretazione dell'oggetto visivo, convertire il grafico a linee in un grafico a linee e istogramma a colonne in pila.

   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Trascinare **% di margine lordo dello scorso anno** dai **Valori colonna** nei **Valori riga**. Power BI crea due assi, consentendo in tal modo di ridimensionare i set di dati in modo diverso: quello di sinistra misura i dollari in vendite, mentre quello di destra la percentuale. La risposta alla domanda è che effettivamente si vede un modello simile.

   ![](media/power-bi-visualization-combo-chart/power-bi-clustered-combo.png)    

## <a name="add-titles-to-the-axes"></a>Aggiungere titoli agli assi
1. Selezionare l'icona del rullo ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) per aprire il riquadro di formattazione.
2. Selezionare la freccia rivolta verso il basso per espandere le opzioni relative all' **asse Y** .
3. Per **asse y (colonna)** , impostare **posizione** al **sinistra**, impostare **titolo** a **nel**,  **Stile** al **Mostra solo titolo**, e **unità visualizzate** come **milioni**.

   ![](media/power-bi-visualization-combo-chart/power-bi-open-y.png)
4. Sotto **asse y (colonna)** , scorrere verso il basso fino a visualizzare **Mostra secondario**. Poiché sono presenti numerose opzioni per gli assi Y, è possibile usare entrambe le barre di scorrimento. Nell'area secondaria Show visualizzata le opzioni di formattazione parte relativa linea del grafico combinato.

   ![](media/power-bi-visualization-combo-chart/power-bi-secondary.png)
5. Per **Asse Y (riga)** , lasciare **Posizione** su **A destra**, **Titolo** su **On** e impostare **Stile** su **Mostra solo titolo**.

   Il grafico combinato ora visualizzerà due assi, entrambi con un titolo.

   ![](media/power-bi-visualization-combo-chart/power-bi-2-titles.png)

6. È facoltativamente possibile modificare il tipo di carattere, le dimensioni e il colore del testo e configurare altre opzioni di formattazione per migliorare la visualizzazione e la leggibilità del grafico.

Da qui è possibile:

* [Aggiungere il grafico combinato come riquadro del dashboard](../service-dashboard-tiles.md).
* [Salvare il report](../service-report-save.md).
* [Rendere il report più accessibile agli utenti con particolari esigenze](../desktop-accessibility.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Evidenziazione incrociata e filtro incrociato

Evidenziando una colonna o una linea in un grafico combinato vengono applicati l'evidenziazione incrociata e il filtro incrociato nelle altre visualizzazioni nella pagina del report e viceversa. Usare le [interazioni visive](../service-reports-visual-interactions.md) per modificare questo comportamento predefinito.

## <a name="next-steps"></a>Passaggi successivi

[Grafici ad anello in Power BI](power-bi-visualization-doughnut-charts.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
