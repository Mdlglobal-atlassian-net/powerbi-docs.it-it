---
title: Grafici a cascata in Power BI
description: Grafici a cascata in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/5/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 20b597507a3619b60ef1db058d0ff3c8fd63b867
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276675"
---
# <a name="waterfall-charts-in-power-bi"></a>Grafici a cascata in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

I grafici a cascata mostrano il totale aggiornato ogni volta che Power BI aggiunge e sottrae valori. Sono utili per comprendere in che modo un valore iniziale (ad esempio, il reddito netto) è interessato da una serie di modifiche positive e negative.

Le colonne sono contraddistinte dal colore per poter notare rapidamente gli aumenti e le diminuzioni. Le colonne del valore iniziale e del valore finale spesso [iniziano sull'asse orizzontale](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "iniziano sull'asse orizzontale"), mentre i valori intermedi sono colonne mobili. In virtù di questo stile, i grafici a cascata sono noti anche come grafici a ponte.

## <a name="when-to-use-a-waterfall-chart"></a>Quando usare un grafico a cascata

I grafici a cascata rappresentano un'ottima scelta nelle seguenti situazioni:

* In presenza di modifiche per la misura nel tempo, per una serie o per categorie diverse.

* Per controllare le principali modifiche che contribuiscono a determinare il valore totale.

* Per rappresentare graficamente il profitto annuo di un'azienda mostrando le varie fonti di ricavi e calcolare il profitto (o la perdita) totale.

* Per illustrare il numero di dipendenti iniziale e finale dell'azienda in un anno.

* Per visualizzare la quantità di denaro incassata e spesa ogni mese e il saldo corrente per il proprio conto.

## <a name="prerequisite"></a>Prerequisito

Questa esercitazione usa il [file Retail Analysis Sample PBIX](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu selezionare **File** > **Apri**
   
2. Trovare la copia del **file Retail Analysis Sample PBIX**

1. Aprire il **file Retail Analysis Sample PBIX** nella visualizzazione report ![Screenshot dell'icona della visualizzazione report](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleziona ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) per aggiungere una nuova pagina.

> [!NOTE]
> Per condividere il report con un collega di Power BI, è necessario che entrambi gli utenti abbiano licenze di Power BI Pro individuali o che il report venga salvato nella capacità Premium.    

## <a name="create-a-waterfall-chart"></a>Creare un grafico a cascata

Verrà creato un grafico a cascata che visualizza la varianza delle vendite (confronto tra vendite stimate ed effettive) per mese.

### <a name="build-the-waterfall-chart"></a>Creare il grafico a cascata

1. Dal riquadro **Campi** selezionare **Sales** > **Total Sales Variance**.

   ![Screenshot della selezione di Sales > Total Sales Variance e dell'oggetto visivo risultante.](media/power-bi-visualization-waterfall-charts/power-bi-bar.png)

1. Selezionare l'icona del grafico a cascata ![Screenshot dell'icona del grafico a cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![Modelli di visualizzazione](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. Selezionare **Time** > **FiscalMonth** per aggiungerlo all'area **Categoria**.

    ![cascata](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-month.png)

### <a name="sort-the-waterfall-chart"></a>Ordinare il grafico a cascata

1. Assicurarsi che Power BI ordini il grafico a cascata in ordine cronologico per mese. Selezionare **Altre opzioni** (...) nell'angolo superiore destro del grafico.

    Per questo esempio, selezionare **Ordina per** e scegliere **FiscalMonth**. Un indicatore giallo accanto alla selezione indica quando è in corso l'applicazione dell'opzione di selezione.

    ![Selezionare Ordina per > FiscalMonth](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscalmonth.png)
    
    Per visualizzare i mesi in ordine cronologico, selezionare **Ordinamento crescente**. Come nel passaggio precedente, verificare che sia presente un indicatore giallo a sinistra di **Ordinamento crescente**. Ciò indica che l'opzione selezionata viene applicata.

    ![Selezionare Ordina per > Ordinamento crescente](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-ascending.png)

    

    Si noti che il grafico è ordinato da gennaio ad agosto per FiscalMonth.  

### <a name="explore-the-waterfall-chart"></a>Esplorare il grafico a cascata

Approfondire ulteriormente per scoprire qual è il fattore che contribuisce maggiormente ai cambiamenti da un mese all'altro.

1.  Selezionare **Store** > **Territory** per aggiungere **Territory** al bucket **Scomposizione**.

    ![Mostra Store nel bucket Breakdown](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Power BI usa il valore in **Scomposizione** per aggiungere altri dati alla visualizzazione. Aggiunge i primi cinque territori che contribuiscono agli aumenti o alle diminuzioni per ogni mese fiscale. Questo significa che febbraio, ad esempio, ora ha sei punti dati invece che uno solo.  

    ![Mostra Store nel bucket Breakdown](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-default.png)

    Si supponga di essere interessati solo ai primi due.

1. Nel riquadro **Formato** selezionare **Scomposizione** e impostare **Numero massimo scomposizioni** su **2**.

    ![Formato > Scomposizione](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-two.png)

    Una rapida analisi rivela che i territori di Ohio e Pennsylvania sono quelli che contribuiscono maggiormente agli spostamenti, sia negativi che positivi, nel grafico a cascata.

    ![Grafico a cascata](media/power-bi-visualization-waterfall-charts/power-bi-axis-waterfall.png)

## <a name="next-steps"></a>Passaggi successivi

* [Modificare l'interazione degli oggetti visivi in un report di Power BI](../create-reports/service-reports-visual-interactions.md)

* [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

