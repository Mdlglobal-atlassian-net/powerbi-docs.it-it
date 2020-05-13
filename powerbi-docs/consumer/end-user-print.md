---
title: Stampare dal servizio Power BI
description: Stampa di un dashboard, di un riquadro o di una pagina del report dal servizio Power BI.
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 8c91e2a07143a6355b7049e80cbdc3e4ba906013
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83145374"
---
# <a name="printing-from-the-power-bi-service"></a>Stampa dal servizio Power BI

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]
## <a name="what-can-be-printed"></a>Elementi stampabili
[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

È possibile stampare un intero dashboard, un riquadro del dashboard, una pagina del report o un oggetto visivo del report dal servizio Power BI. Se il report contiene più pagine, è necessario stampare ogni pagina separatamente. 

## <a name="printing-considerations"></a>Considerazioni sulla stampa

I dashboard e i report di Power BI vengono creati dai *progettisti* di report per lo più per essere usati online e avere un aspetto straordinario su una varietà di dispositivi. Quando si stampa un report, è il browser che controlla il modo in cui il contenuto appare sulla carta. 

Sono disponibili alcune impostazioni del browser da usare per modificare la stampa, ma non garantiscono che si ottenga il risultato desiderato. È consigliabile [esportare il contenuto in un file PDF](end-user-pdf.md) e quindi stampare il PDF. 

## <a name="adjust-your-browser-print-settings"></a>Modificare le impostazioni di stampa del browser
Quando si avvia la stampa da Power BI, il browser apre la finestra Stampa. La finestra di stampa è diversa da un browser all'altro, ma ognuna offre opzioni simili da usare per controllare l'aspetto della stampa. 

Ecco alcuni suggerimenti rapidi per la formattazione della stampa.

   > 
1. Se la larghezza del dashboard, del report o dell'oggetto visivo è superiore all'altezza, è consigliabile usare il layout **Orizzontale**. 

   ![Finestra di dialogo Stampa con l'opzione Layout impostata su Orizzontale](./media/end-user-print/power-bi-landscape-layout.png)

2. Per includere più contenuto in una pagina stampata, regolare impostazioni come i margini e la scala. 

    ![Finestra di dialogo Stampa con la sezione Altre impostazioni](./media/end-user-print/power-bi-margins.png)

Provare le varie impostazioni del browser in uso fino a ottenere l'aspetto desiderato. Alcuni browser offrono anche opzioni per stampare la grafica di sfondo. 

## <a name="print-a-dashboard"></a>Stampare un dashboard
1. Aprire il dashboard che si vuole stampare.
2. Nell'angolo in alto a sinistra selezionare Esporta e scegliere **Stampa questa pagina**.
   
    ![Opzione Stampa dashboard](./media/end-user-print/power-bi-dashboard-print.png)

3. Viene visualizzata la finestra di stampa del browser in uso. Scegliere le impostazioni. Ad esempio, se la larghezza del dashboard è superiore alla lunghezza, è consigliabile impostare il layout su **Orizzontale**. Selezionare **Stampa**.
   
    ![Finestra di dialogo Stampa](./media/end-user-print/power-bi-print-dash.png)

## <a name="print-a-dashboard-tile"></a>Stampare un riquadro del dashboard
1. Per aprire il dashboard nella [modalità schermo intero](end-user-focus.md), selezionare l'icona di tale modalità ![Icona Schermo intero](./media/end-user-print/power-bi-full-screen.png) nella barra dei menu superiore.

3. [Aprire il riquadro in modalità messa a fuoco](end-user-focus.md) passando il puntatore per visualizzare **Altre opzioni (...)** e scegliendo **Apri in modalità messa a fuoco** o l'icona della modalità messa a fuoco ![Icona Modalità messa a fuoco](./media/end-user-print/power-bi-focus-icon.png).
   
    ![Menu di puntini di sospensione](./media/end-user-print/power-bi-menu-options.png)

4. Passare il puntatore sul riquadro per visualizzare il menu delle opzioni.
   
    ![Menu delle opzioni a schermo intero](./media/end-user-print/menu-options-new.png)

4. Selezionare l'icona di stampa. ![icona Stampa](./media/end-user-print/print-icon.png).     

5. Viene visualizzata la finestra di stampa del browser in uso. Scegliere le impostazioni. Ad esempio, se il riquadro supera i limiti della pagina, è possibile ridurre la scala al 75%. Selezionare **Stampa**.

    ![finestra di stampa](./media/end-user-print/power-bi-scale.png) 

> [!TIP]
> Se sono stati seguiti tutti questi passaggi ma il riquadro non ha ancora l'aspetto desiderato, provare con le operazioni seguenti.
> 1. Aprire la finestra Stampa e apportare le modifiche alle impostazioni di stampa che si ritiene produrranno il risultato di stampa migliore. Ad esempio, modificare il layout, i margini e la scala. 
> 2. Invece di stampare, selezionare **Annulla**. 
> 3. Ripetere i passaggi da 1 a 5. Il riquadro verrà modificato in base alle nuove impostazioni della finestra Stampa e sarà pronto per la stampa.

## <a name="print-a-report-page"></a>Stampare una pagina del report
I report possono essere stampati una pagina alla volta.

1. Aprire il report e selezionare **Esporta** > **Stampa** per stampare la pagina del report corrente.
   
    ![Menu File di Power BI](./media/end-user-print/power-bi-report-print.png)
2. Viene visualizzata la finestra di stampa del browser in uso.

3. Seguire la procedura di stampa descritta nella precedente sezione **Stampare un dashboard**.
   


## <a name="print-a-report-visual"></a>Stampare un oggetto visivo del report
1. Per [aprire l'oggetto visivo nella modalità messa a fuoco](end-user-focus.md), passare con il puntatore del mouse sul riquadro e selezionare l'icona di tale modalità ![Icona Messa a fuoco](./media/end-user-print/power-bi-focus-icon.png) nell'angolo in alto a destra.

2. Nell'angolo in alto a sinistra selezionare **Esporta** > **Stampa** per stampare l'oggetto visivo.

    ![Menu File di Power BI](./media/end-user-print/power-bi-report-print.png)


3. Seguire la procedura di stampa descritta nella precedente sezione **Stampare un dashboard**.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

* D: non è possibile stampare tutte le pagine del report contemporaneamente.    
* A: è normale. Le pagine dei report possono essere stampate solo una alla volta.
* D: non è possibile a stampare in formato PDF.    
* A: questa opzione viene visualizzata solo se il driver PDF è già stato configurato nel browser.    
* D: quando si seleziona **Stampa**, la visualizzazione non corrisponde a quanto mostrato in questo articolo.    
* A: le schermate di stampa variano a seconda del browser e della versione del software.
* D: l'immagine stampata non è ridimensionata correttamente.  Il dashboard non si rientra nella pagina. Altre domande su ridimensionamento e orientamento.    
* A: non è possibile garantire che la copia stampata sarà esattamente identica a come appare nel servizio Power BI. Elementi come il ridimensionamento, i margini, le informazioni visive, l'orientamento e le dimensioni non sono controllati da Power BI. Provare a modificare le impostazioni di stampa del browser. Alcune delle impostazioni suggerite in precedenza sono l'orientamento della pagina (verticale o orizzontale), le dimensioni dei margini e la scala. Se il problema persiste, consultare la documentazione relativa al browser in uso.      
* D: in modalità schermo intero, l'opzione di stampa non viene visualizzata quando si passa il mouse sull'oggetto visivo.   
* A: tornare al dashboard o al report nella visualizzazione predefinita e riaprire l'oggetto visivo in modalità messa a fuoco e quindi in modalità schermo intero. 

## <a name="next-steps"></a>Passaggi successivi
[Condividere dashboard e report con i colleghi e altri utenti](../collaborate-share/service-share-dashboards.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
