---
title: Suggerimenti e consigli per la formattazione dei colori in Power BI
description: Suggerimenti e consigli per la formattazione dei colori in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 71ed70344281dec3353b73c8698594d62ef32eae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285600"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Suggerimenti e consigli per la formattazione dei colori in Power BI
In Power BI sono disponibili vari modi per personalizzare i dashboard e i report. Questo articolo presenta una raccolta di suggerimenti utili per fare in modo che le visualizzazioni di Power BI siano più accattivanti, interessanti e personalizzate in base alle proprie esigenze.

Sono forniti i suggerimenti seguenti. Se si hanno suggerimenti interessanti, è possibile inviarli. Verranno valutati e, se ritenuti utili, verranno aggiunti a questo elenco.

* Cambiare il colore di un unico punto dati
* Basare i colori di un grafico su un valore numerico
* Basare i colori dei punti dati su un valore di campo
* Personalizzare i colori usati nella scala dei colori
* Usare scale dei colori divergenti
* Come annullare un'operazione in Power BI

Per apportare modifiche, è necessario modificare un report. Aprire il report e quindi scegliere **Modifica report** dall'area del menu superiore, come illustrato nell'immagine seguente.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Quando viene visualizzato il riquadro **Visualizzazioni** a destra dell'area di disegno **Report** , è possibile iniziare a personalizzare. Se il riquadro non viene visualizzato, selezionare la freccia nell'angolo superiore destro per aprirlo.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>Cambiare il colore di un unico punto dati
In alcuni casi è utile evidenziare un particolare punto dati, ad esempio le cifre delle vendite per il lancio di un nuovo prodotto o l'aumento dei punteggi di qualità dopo il lancio di un nuovo programma. Con Power BI è possibile evidenziare un particolare punto dati modificandone il colore.

La visualizzazione seguente classifica le unità vendute in base al segmento di prodotto. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-grey.png)

Si supponga ora di voler mettere in evidenza il segmento **Convenience** per mostrare le ottime prestazioni di questo nuovo segmento, usando il colore. Ecco i passaggi necessari:

Espandere la sezione **Colori dati** e spostare il dispositivo di scorrimento di **Mostra tutto** su Sì. Verranno visualizzati i colori per ogni elemento dati nella visualizzazione. Quando si passa il puntatore del mouse sui punti dati, viene abilitato lo scorrimento per consentire la modifica di qualsiasi punto dati.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Impostare il colore arancione per **Convenience**. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-orange.png)

Una volta selezionato, il punto dati **Convenience** viene visualizzato con una gradevole tonalità di arancione e risalta molto bene.

Anche se si cambia tipo di visualizzazione e in seguito si ripristina quella corrente, Power BI ricorda la selezione e mantiene il colore arancione per **Convenience**.

È possibile modificare il colore di un punto dati per uno, alcuni o tutti gli elementi dati nella visualizzazione. Potrebbe essere utile usare i colori aziendali per un oggetto visivo. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Con i colori è possibile ottenere molti effetti diversi. Nella prossima sezione verranno illustrate le sfumature.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Basare i colori di un grafico su un valore numerico
I grafici spesso si avvalgono dell'impostazione dinamica dei colori in base al valore numerico di un campo. In questo modo, è possibile presentare un valore diverso rispetto a quello usato per la dimensione di una barra mostrando due valori in un unico grafico. Questa funzionalità consente anche di evidenziare i punti dati al di sopra (o al di sotto) di un determinato valore, magari per evidenziare aree con redditività bassa.

La sezione seguente illustra vari modi per basare il colore su un valore numerico.

## <a name="base-the-color-of-data-points-on-a-value"></a>Basare i colori dei punti dati su un valore
Per cambiare il colore in base a un valore, trascinare il campo su cui si vuole basare il colore nell'area **Saturazione colore** nel riquadro **Campi**. Nell'immagine seguente, il campo **%Market Share SPLY YTD** è stato trascinato in **Saturazione colore**. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-color-saturation.png)

E nel riquadro Formattazione, in **Colori dati**, determinare come il valore di **% Market Share SPAS YTD** cambierà il colore e l'ombreggiatura nell'istogramma. In questo esempio, i valori minori per %Market Share saranno azzurro chiaro e i valori più alti saranno di colore blu più scuro.


![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Si può notare che, anche se il numero di unità vendute è maggiore sia per **Productivity** che per **Extreme** (le colonne sono più alte), **Moderation** ha una valore maggiore per **%Market Share SPLY YTD** (la saturazione del colore della colonna è maggiore).

![](media/service-tips-and-tricks-for-color-formatting/power-bi-saturation.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>Personalizzare i colori usati nella scala dei colori
È anche possibile personalizzare i colori usati nella scala dei colori Per impostazione predefinita, il valore più basso nei dati viene mappato al colore meno saturo e il valore più alto con al colore più saturo. Nell'immagine precedente è stata usata una sfumatura di colore blu. 

Espandere **Colori dati** per vedere le sfumature di colore usate per visualizzare i dati. La gamma di colori viene mostrata in una barra sfumata che rappresenta lo spettro tra il valore **Minimo** e **Massimo** del colore, con il colore con il valore **Minimo** a sinistra e quello con il valore **Massimo** a destra.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Per cambiare la scala in modo da usare una gamma di colori diversa, selezionare l'elenco a discesa accanto a **Minimo** o **Massimo**e selezionare un colore. Nell'immagine il colore **Massimo** è impostato sul nero e la barra sfumata mostra il nuovo spettro di colore tra **Minimo** e **Massimo**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

È anche possibile modificare l'associazione tra i valori e questi colori. Nell'immagine seguente, i colori per **Minimo** e **Massimo** sono impostati rispettivamente su arancione e verde.

Si noti che le barre del grafico nella prima immagine riflettono la sfumatura presente nella barra: il valore massimo è verde, quello minimo è arancione e le barre intermedie sono visualizzate con una tonalità di colore nello spettro tra il verde e l'arancione.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Vediamo ora cosa succede se si specificano valori numerici nelle caselle dei valori **Minimo** e **Massimo** , che si trovano sotto i selettori **Minimo** e **Maximo** , come mostrato nell'immagine seguente. Impostare **Minimo** su 20.000,000 e impostare **Massimo** su 20.000.001.

Impostando questi valori, la sfumatura non viene più applicata ai valori inferiori a **Minimo** o superiori a **Massimo** nel grafico. Tutte le barre con un valore superiore a **Massimo** vengono colorate in verde e quelle con un valore inferiore a **Minimo** in rosso.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Usare scale dei colori divergenti
A volte i dati possono avere una scala naturalmente divergente. Ad esempio, un intervallo di temperature ha un centro naturale al punto di congelamento e un punteggio di redditività ha un punto medio (zero) naturale.

Per usare scale di colore divergenti, posizionare il dispositivo di scorrimento **Divergente** su **Sì**. Quando l'opzione **Divergente** è attivata, appaiono un selettore di colore e una casella di valore aggiuntivi, entrambi denominati **Centrale**, come mostrato nella figura seguente.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Quando il dispositivo di scorrimento **Divergente** è attivato, è possibile impostare separatamente i colori per **Minimo**, **Massimo** e **Centrale** . Nell'immagine seguente **Centrale** è impostato su uno, quindi le barre con valori al di sopra di uno sono in una sfumatura di verde e le barra al di sotto di uno sono in una sfumatura di rosso.

## <a name="how-to-undo-in-power-bi"></a>Come annullare un'operazione in Power BI
Come molti altri servizi e software Microsoft, Power BI consente di annullare rapidamente l'ultimo comando. Si supponga ad esempio di modificare il colore di un punto dati o di una serie di punti dati e che il colore rappresentato nella visualizzazione non sia di proprio gradimento. Si vorrebbe ripristinare il colore precedente ma non si ricorda esattamente quale colore fosse.

Per **annullare** l'ultima azione o le ultime azioni è sufficiente:

- Premere CTRL+Z

## <a name="feedback"></a>Commenti e suggerimenti
Se si hanno suggerimenti da condividere, è possibile inviarli. è possibile inviarli. Verranno valutati e, se ritenuti utili, verranno inseriti qui.

>[!NOTE]
>Queste personalizzazioni di colori, assi ed elementi correlati, disponibili quando l'icona **Formato** è selezionata, sono disponibili anche in Power BI Desktop.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione alla formattazione dei colori e alle proprietà degli assi](service-getting-started-with-color-formatting-and-axis-properties.md)

