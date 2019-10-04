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
ms.openlocfilehash: 97c01966750d888f3420d265eb3f252b3a8f57d3
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194896"
---
# <a name="combo-chart-in-power-bi"></a>Grafico combinato in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

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
Questa esercitazione usa il [file Retail Analysis Sample PBIX](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu selezionare **File** > **Apri**
   
2. Trovare la copia del **file Retail Analysis Sample PBIX**

1. Aprire il **file Retail Analysis Sample PBIX** nella visualizzazione report ![Screenshot dell'icona della visualizzazione report](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleziona ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) per aggiungere una nuova pagina.



## <a name="create-a-basic-single-axis-combo-chart"></a>Creare un grafico combinato di base ad asse singolo
Questo video mostra come creare un grafico combinato usando l’esempio di analisi di vendite e marketing.
   > [!NOTE]
   > Questo video usa una versione precedente di Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a>

1. Iniziare in una pagina di report vuota e creare un istogramma che visualizzi le vendite dell'anno e il margine lordo per mese.

    a.  Nel riquadro Campi selezionare **Sales** \> **This Year Sales** > **Value**.

    b.  Trascinare **Sales** \> **Gross Margin This Year** nell'area **Valore**.

    c. Selezionare **Time** \> **FiscalMonth** per aggiungerlo all'area **Asse**.

    ![Esempio di esercitazione per un grafico combinato](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Selezionare i puntini di sospensione (...) nell'angolo superiore destro della visualizzazione e selezionare **Sort by > FiscalMonth**. Per modificare l'ordinamento, selezionare di nuovo i puntini di sospensione e scegliere **Ordinamento crescente** oppure **Ordinamento decrescente**. Per questo esempio si userà l'opzione **Ordinamento crescente**.

6. Convertire l'istogramma in un grafico combinato. Sono disponibili due grafici combinati: **Grafico a linee e istogramma a colonne in pila** e **Grafico a linee e istogramma a colonne raggruppate**. Con l'istogramma selezionato, nel riquadro **Visualizzazioni** selezionare **Grafico a linee e istogramma a colonne raggruppate**.

    ![Esempio di conversione di un grafico combinato](media/power-bi-visualization-combo-chart/converttocombo-new2.png)
7. Dal riquadro **Campi** trascinare **Sales** \> **Last Year Sales** all’area **Valori riga**.

   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   Il grafico combinato dovrebbe essere simile al seguente:

   ![Esempio di grafico combinato completato](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Creare un grafico combinato con due assi
In questa attività, si confronteranno margine lordo e vendite.

1. Creare un nuovo grafico a linee che tiene traccia di **Gross Margin last year %** per **FiscalMonth**. Selezionare i puntini di sospensione per ordinare per **mese** e in **ordine crescente**.  
La % di margine lordo nel mese di gennaio ammontava al 35%, in aprile al 45%, per poi diminuire nel mese di luglio e aumentare nuovamente in agosto. Si vedrà un modello simile per le vendite dell’anno scorso e di quest'anno?

   ![Esempio di vendite nel grafico combinato](media/power-bi-visualization-combo-chart/combo1-new.png)
2. Aggiungere **This Year Sales > Value** e **Last Year Sales** al grafico a linee. La scala usata per **Gross Margin Last Year %** è notevolmente ridotta rispetto a quella di **Sales**, di conseguenza risulta difficile confrontarle.      

   ![Esempio di linea piatta nel grafico combinato](media/power-bi-visualization-combo-chart/flatline-new.png)
3. Per facilitare la lettura e l'interpretazione dell'oggetto visivo, convertire il grafico a linee in un grafico a linee e istogramma a colonne in pila.

   ![Esempio di conversione in grafico combinato](media/power-bi-visualization-combo-chart/converttocombo-new.png)

4. Trascinare **% di margine lordo dello scorso anno** dai **Valori colonna** nei **Valori riga**. Power BI crea due assi, consentendo in tal modo di ridimensionare i set di dati in modo diverso: quello di sinistra misura i dollari in vendite, mentre quello di destra la percentuale. La risposta alla domanda è che effettivamente si vede un modello simile.

   ![Esempio di grafico combinato cluster](media/power-bi-visualization-combo-chart/power-bi-clustered-combo.png)    

## <a name="add-titles-to-the-axes"></a>Aggiungere titoli agli assi
1. Selezionare l'icona del rullo 
1. ![Icona del rullo](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) per aprire il riquadro Formato.
1. Selezionare la freccia rivolta verso il basso per espandere le opzioni relative all' **asse Y** .
1. Per **Asse Y (colonna)** , impostare **Posizione** su **A sinistra**, **Titolo** su **Sì**, **Stile** su **Mostra solo titolo** e **Unità visualizzate** su **Milioni**.

   ![Esempio di asse Y nel grafico combinato](media/power-bi-visualization-combo-chart/power-bi-open-y.png)
4. In **Asse Y (colonna)** scorrere verso il basso fino a visualizzare **Mostra secondario**. Sono disponibili così tante opzioni per gli assi Y che potrebbe essere necessario usare entrambe le barre di scorrimento. Nella sezione Mostra secondario sono visualizzate le opzioni per la formattazione della parte di grafico a linee del grafico combinato.

   ![Esempio della sezione Mostra secondario del grafico combinato](media/power-bi-visualization-combo-chart/power-bi-secondary.png)
5. Per **Asse Y (riga)** , lasciare **Posizione** su **A destra**, **Titolo** su **On** e impostare **Stile** su **Mostra solo titolo**.

   Il grafico combinato ora visualizzerà due assi, entrambi con un titolo.

   ![Esempio di titoli nel grafico combinato](media/power-bi-visualization-combo-chart/power-bi-2-titles.png)

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
