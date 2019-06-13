---
title: Usare grafici a nastri in Power BI
description: Creare e usare grafici a nastri nel servizio Power BI e in Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3400071c6b8cee472bb61475e6d3482189680563
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840084"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Usare grafici a nastri in Power BI
È possibile usare grafici a nastri per visualizzare i dati e individuare rapidamente la categoria di dati di livello più alto (valore più elevato). I grafici a nastri rappresentano una valida opzione nella visualizzazione delle variazioni di posizione, con il valore massimo visualizzato sempre in cima per ogni periodo di tempo. 

![Grafico a nastri](media/desktop-ribbon-charts/ribbon-charts_01.png)

## <a name="create-a-ribbon-chart"></a>Creare un grafico a nastri
Per seguire la procedura, aprire il [report di esempio di analisi delle vendite al dettaglio](../sample-retail-analysis.md). 

1. Per creare un grafico a nastri, selezionare **Grafico a nastri** nel riquadro **Visualizzazioni**.

    ![modelli di visualizzazione](media/desktop-ribbon-charts/power-bi-template.png)

    I grafici a nastri collegano una categoria di dati in relazione al periodo di tempo visualizzato tramite nastri, consentendo di osservare la posizione di una categoria lungo l'asse X del grafico, che in genere rappresenta la sequenza temporale.

2. Selezionare i campi per **Asse**, **Legenda** e **Valore**.  In questo esempio sono state effettuate le selezioni seguenti: **Date** (Data), **Category** (Categoria) e **This year sales** (Vendite anno corrente).  

    ![campi selezionati](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Poiché il set di dati contiene dati per un solo anno, il campo **Year** (Anno) è stato rimosso dall'area **Asse**. 

3. Il grafico a nastri visualizza la classifica a mesi alterni. Si noti come la classifica varia nel tempo.  Ad esempio la categoria Home (Casa) passa dal terzo al quarto posto e quindi di nuovo al terzo posto. La categoria Juniors (Ragazzi) passa dal terzo al quinto posto nel mese di luglio. 

    ![Grafico a nastri](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Formattare un grafico a nastri
Quando si crea un grafico a nastri, la sezione **Formato** del riquadro **Visualizzazioni** mette a disposizione opzioni di formattazione. Le opzioni di formattazione per i grafici a nastri sono simili a quelle di un istogramma in pila, con opzioni aggiuntive specifiche per i grafici a nastri.

![modello di grafico a nastri nel riquadro Visualizzazione](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Queste opzioni di formattazione per i grafici a nastri consentono di eseguire rettifiche.

* **Spaziatura** consente di definire lo spazio tra i nastri. Il numero è la percentuale dell'altezza massima della colonna.
* **Abbina al colore della serie** consente abbinare il colore dei nastri al colore della serie. Se l'opzione è **disattivata**, i nastri vengono visualizzati in grigio.
* **Trasparenza** consente di specificare la trasparenza dei nastri, con il valore predefinito impostato su 30.
* **Bordo** consente di applicare un bordo scuro sulla parte superiore e inferiore dei nastri. Per impostazione predefinita, i bordi sono disattivati.

Dato che il grafico a nastri non dispone di etichette dell'asse y, può risultare utile aggiungere etichette dati. Nel riquadro Formattazione selezionare **Etichette dati**. 

![opzioni di formattazione per le etichette dati](media/desktop-ribbon-charts/power-bi-labels.png)

Impostare le opzioni di formattazione per le etichette dati.  In questo esempio il colore del testo è stato impostato su bianco, le cifre decimali su zero e le unità di visualizzazione su migliaia. 

![modello di grafico a nastri nel riquadro Visualizzazione](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Passaggi successivi

[Grafici a dispersione e grafici a bolle in Power BI](power-bi-visualization-scatter.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)