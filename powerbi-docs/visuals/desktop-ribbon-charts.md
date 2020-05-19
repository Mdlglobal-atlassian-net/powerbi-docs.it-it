---
title: Usare grafici a nastri in Power BI
description: Creare e usare grafici a nastri in Power BI Desktop
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 6da3dd980b180398cf75c8e01f81501ec5d62ed6
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83127467"
---
# <a name="create-ribbon-charts-in-power-bi"></a>Creare grafici a nastri in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

È possibile creare grafici a nastri per visualizzare i dati e individuare rapidamente la categoria di dati di livello più alto (valore più elevato). I grafici a nastri rappresentano una valida opzione nella visualizzazione delle variazioni di posizione, con il valore massimo visualizzato sempre in cima per ogni periodo di tempo. 

![Grafico a nastri](media/desktop-ribbon-charts/ribbon-charts-01.png)

> [!NOTE]
> Per condividere il report con un collega di Power BI, è necessario che entrambi gli utenti abbiano licenze di Power BI Pro individuali o che il report venga salvato nella capacità Premium. Vedere l'articolo sulla [condivisione di report](../collaborate-share/service-share-reports.md).

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione usa il [file Retail Analysis Sample PBIX](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu selezionare **File** > **Apri**
   
2. Trovare la copia del **file Retail Analysis Sample PBIX**

1. Aprire il **file Retail Analysis Sample PBIX** nella visualizzazione report ![Screenshot dell'icona della visualizzazione report](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleziona ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) per aggiungere una nuova pagina.

## <a name="create-a-ribbon-chart"></a>Creare un grafico a nastri

1. Per creare un grafico a nastri, selezionare **Grafico a nastri** nel riquadro **Visualizzazioni**.

    ![modelli di visualizzazione](media/desktop-ribbon-charts/power-bi-template.png)

    I grafici a nastri collegano una categoria di dati in relazione al periodo di tempo visualizzato tramite nastri, consentendo di osservare la posizione di una categoria lungo l'asse X del grafico, che in genere rappresenta la sequenza temporale.

2. Selezionare i campi per **Asse**, **Legenda** e **Valore**.  In questo esempio sono state effettuate le selezioni seguenti: **Store** > **OpenDate**, **Item** > **Category** e **Sales** > **This year sales** > **Value**.  

    ![Campi selezionati](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Poiché il set di dati contiene dati per un solo anno, il campo **Year** e **Quarter** sono stati rimossi dall'area **Asse**.

3. Il grafico a nastri visualizza la classifica per ogni mese. Si noti come la classifica varia nel tempo. La categoria Home, ad esempio, passa da seconda in febbraio a quinta in marzo.

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

Impostare le opzioni di formattazione per le etichette dati. In questo esempio il colore del testo è stato impostato su bianco e le unità di visualizzazione su migliaia.

![modello di grafico a nastri nel riquadro Visualizzazione](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Passaggi successivi

[Grafici a dispersione e grafici a bolle in Power BI](power-bi-visualization-scatter.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
