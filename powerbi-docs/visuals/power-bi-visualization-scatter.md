---
title: Grafici a dispersione, grafici a bolle e tracciati a punti in Power BI
description: Grafici a dispersione, tracciati a punti e grafici a bolle in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8222194359077cb0d88286a33d1c9b2a05f6bd80
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390979"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Grafici a dispersione, grafici a bolle e tracciati a punti in Power BI

Un grafico a dispersione ha sempre due assi di valori per mostrare un set di dati numerici lungo un asse orizzontale e un altro set di valori numerici lungo un asse verticale. Nel grafico vengono visualizzati i punti in corrispondenza dell'intersezione di un valore numerico x e un valore numerico y, combinando questi valori in punti dati singoli. Power BI può distribuire questi punti dati uniformemente o in maniera non uniforme sull'asse orizzontale, a seconda dei dati rappresentati nel grafico.

Guardare questo video per seguire la creazione del grafico a dispersione e quindi seguire la procedura riportata più avanti per crearne uno.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

È possibile impostare il numero di punti dati fino a un massimo di 10.000.  

## <a name="when-to-use-a-scatter-chart-bubble-chart-or-a-dot-plot-chart"></a>Quando usare un grafico a dispersione, un grafico a bolle o un tracciato a punti

### <a name="scatter-and-bubble-charts"></a>Grafici a dispersione e a bolle

Un grafico a dispersione mostra la relazione tra due valori numerici. Un grafico a bolle sostituisce i punti dati con bolle, con le *dimensioni* della bolla che rappresentano una terza dimensione aggiuntiva dei dati.

![Screenshot di un grafico a bolle di esempio.](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

I grafici a dispersione rappresentano un'ottima scelta nelle seguenti situazioni:

* Per visualizzare le relazioni tra due valori numerici.

* Per tracciare due gruppi di numeri come un'unica serie di coordinate x e y.

* Al posto di un grafico a linee quando si vuole modificare la scala dell'asse orizzontale.

* Per trasformare l'asse orizzontale in una scala logaritmica.

* Per visualizzare i dati del foglio di lavoro che includono coppie o set raggruppati di valori.

    > [!TIP]
    > In un grafico a dispersione, è possibile regolare le scale indipendenti degli assi per visualizzare ulteriori informazioni sui valori raggruppati.

* Per visualizzare modelli in grandi set di dati, ad esempio tramite la visualizzazione di tendenze lineari o non lineari, cluster e outlier.

* Per confrontare numeri elevati di punti dati indipendentemente dal tempo.  Maggiore è la quantità di dati inclusi in un grafico a dispersione, migliore saranno i confronti che è possibile ottenere.

Oltre alle potenzialità offerte dai grafici a dispersione, i grafici a bolle rappresentano un'ottima scelta nelle situazioni seguenti:

* Se i dati includono tre serie di dati contenenti ciascuna un set di valori.

* Per presentare i dati finanziari.  Dimensioni delle bolle diverse sono utili per evidenziare visivamente valori specifici.

* Per usare i quadranti.

### <a name="dot-plot-charts"></a>Tracciati a punti

Un tracciato a punti è simile a un grafico a bolle e a un grafico a dispersione, ma è anche possibile tracciare dati numerici o categorici lungo l'asse X.

![Screenshot di un tracciato a punti.](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Questi grafici sono un'ottima scelta se si vogliono includere dati categorici lungo l'asse X.

## <a name="prerequisites"></a>Prerequisiti

* Servizio Power BI

* Report Retail Analysis Sample

## <a name="create-a-scatter-chart"></a>Creare un grafico a dispersione

Per seguire la procedura, accedere al [servizio Power BI](https://app.powerbi.com) e aprire il report [Retail Analysis Sample](../sample-datasets.md) nella visualizzazione [Modifica report](../service-interact-with-a-report-in-editing-view.md).

1. Selezionare ![Screenshot dell'icona con segno più gialla.](media/power-bi-visualization-scatter/power-bi-yellow-plus-icon.png) per creare una pagina del report vuota.

1. Nel riquadro **Campi** selezionare questi campi:

    * **Vendite** > **Vendite per piedi quadrati**

    * **Vendite** >  **% di scostamento vendite totali**

    * **Distretto** > **Distretto**

    ![Screenshot dell'istogramma a colonne raggruppate, del riquadro Visualizzazioni e del riquadro Campi con i campi selezionati evidenziati.](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

1. Nel riquadro **Visualizzazioni** selezionare ![Screenshot dell'icona del grafico a dispersione](media/power-bi-visualization-scatter/power-bi-scatter-chart-icon.png) per convertire l'istogramma a colonne raggruppate in un grafico a dispersione.

   ![Screenshot dell'istogramma a colonne raggruppate che diventa un grafico a dispersione.](media/power-bi-visualization-scatter/power-bi-scatter-new.png)

1. Trascinare **Zona** da **Dettagli** in **Legenda**.

    Power BI visualizza un grafico a dispersione che rappresenta **Total Sales Variance %** lungo l'asse Y e **Sales Per Square Feet** lungo l'asse X. I colori del punto dati rappresentano le zone:

    ![Screenshot del grafico a dispersione.](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Ora si aggiungerà una terza dimensione.

## <a name="create-a-bubble-chart"></a>Creare un grafico a bolle

1. Dal riquadro **Campi** trascinare **Sales** > **This Year Sales** > **Valore** nell'area **Dimensioni**. I punti dati si espandono in volumi proporzionati al valore delle vendite.

   ![Screenshot del grafico a dispersione che diventa un grafico a bolle aggiungendo il valore di Sales all'area Dimensioni.](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

1. Passare il mouse su una bolla. La dimensione della bolla riflette il valore delle **Vendite di quest’anno**.

    ![visualizzazione delle descrizioni comando](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

1. È possibile impostare il numero di punti dati da mostrare nel grafico a bolle nella sezione **Formato** del riquadro **Visualizzazioni** espandendo **Generale** e modificando **Volume dati**.

    ![Screenshot del riquadro Visualizzazioni con l'icona Formato, l'elenco a discesa Generale e l'opzione Volume dati evidenziati.](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png)

    È possibile impostare il volume dei dati su un numero massimo di 10.000. All'approssimarsi del numero massimo, è consigliabile eseguire un test per garantire migliori prestazioni.

    > [!NOTE]
    > Più punti dati possono comportare tempi di caricamento più lunghi. Se si sceglie di pubblicare report con limiti ai livelli più elevati della scala, assicurarsi di testare i report anche nel Web e nei dispositivi mobili. È importante verificare che le prestazioni del grafico corrispondano alle aspettative degli utenti.

1. È possibile [formattare i colori della visualizzazione, le etichette, i titoli, lo sfondo e altro ancora](service-getting-started-with-color-formatting-and-axis-properties.md).

    Per [migliorare l'accessibilità](../desktop-accessibility.md), considerare la possibilità di aggiungere forme di marcatore a ogni riga. Per selezionare la forma del marcatore, espandere **Forme**, selezionare **Forma del marcatore** e selezionare una forma.

    ![Screenshot dell'elenco a discesa Forme con le opzioni Forma del marcatore evidenziate.](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

    È possibile cambiare la forma del marcatore in rombo, triangolo o quadrato. L'uso di una forma del marcatore diversa per ogni riga consente agli utenti dei report di distinguere più facilmente le linee dalle aree.

## <a name="create-a-dot-plot-chart"></a>Creare un tracciato a punti

Per creare un tracciato a punti, sostituire il campo dell'**asse X** numerico con un campo categorico.

Dal riquadro **Asse X** rimuovere **Sales per sq ft** e sostituirlo con **District** > **District Manager**.

![Screenshot di un nuovo tracciato a punti.](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

### <a name="your-scatter-chart-has-only-one-data-point"></a>Il grafico a dispersione presenta solo un punto dati

Il grafico a dispersione ha solo un punto dati che aggrega tutti i valori sugli assi X e Y?  O forse aggrega tutti i valori lungo una singola riga orizzontale o verticale?

![Screenshot di un grafico a dispersione con un punto dati.](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Aggiungere un campo all'area **Dettagli** per indicare a Power BI come raggruppare i valori. Il campo deve essere univoco per ogni punto che si desidera tracciare. Ad esempio un numero di riga semplice o un campo ID.

![Screenshot di un grafico a dispersione con RowNum aggiunto all'area Dettagli.](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Se non è disponibile un elemento di questo tipo nei dati, creare un campo che concatena i valori X e Y in un elemento univoco per ogni punto:

![Screenshot di un grafico a dispersione con TempTime aggiunto all'area Dettagli.](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Per creare un nuovo campo, [usare l'Editor di query di Power BI Desktop per aggiungere una colonna indice](../desktop-add-custom-column.md) al set di dati. Aggiungere quindi la colonna all'area **Dettagli** della visualizzazione.

## <a name="next-steps"></a>Passaggi successivi

* [Campionamento ad alta densità nei grafici a dispersione di Power BI](desktop-high-density-scatter-charts.md)

* [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
