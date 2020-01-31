---
title: Incorporare una nuova app di Power Apps n report di Power BI
description: Incorporare un'app che usa la stessa origine dati e può essere filtrata come altri elementi del report
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/16/2020
ms.author: mblythe
LocalizationGroup: Visualizations
ms.openlocfilehash: bbca812644b82f8a0b848dc16e450f880ccb596c
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539901"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Esercitazione: Incorporare un oggetto visivo di Power Apps in un report di Power BI

Questa esercitazione usa l'oggetto visivo di Power Apps per creare una nuova app incorporata in un report di esempio di Power BI. Questa app interagisce con altri oggetti visivi presenti nel report.

Se non si ha una sottoscrizione a Power Apps, [creare un account gratuito](https://web.powerapps.com/signup?redirect=marketing&email=) prima di iniziare.

In questa esercitazione viene illustrato come:
> [!div class="checklist"]
> * Aggiungere un oggetto visivo di Power Apps a un report di Power BI
> * Usare Power Apps per creare una nuova app che usa i dati del report di Power BI
> * Visualizzare e interagire con l'oggetto visivo di Power Apps nel report

## <a name="prerequisites"></a>Prerequisiti

* Browser [Google Chrome](https://www.google.com/chrome/browser/) o [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* Una [sottoscrizione di Power BI](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi) con l'[Esempio di analisi delle opportunità](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample) installato
* Conoscenza di come [creare app in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) e come [modificare i report di Power BI](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)



## <a name="create-a-new-app"></a>Creare una nuova app
Quando si aggiunge l'oggetto visivo di Power Apps al report, viene avviato Power Apps Studio con una connessione dati dinamica tra Power Apps e Power BI.

1. Aprire il report Opportunity Analysis Sample e selezionare la pagina *Upcoming Opportunities*. 


2. Spostare e ridimensionare alcuni dei riquadri del report per ottenere spazio per il nuovo oggetto visivo.

    ![Spostare e ridimensionare i riquadri del report](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. Dal riquadro Visualizzazioni selezionare l'icona Power Apps, quindi ridimensionare l'oggetto visivo per adattarlo allo spazio creato.

    ![Riquadro Visualizzazioni con l'icona di Power Apps selezionata](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. Nel riquadro **Campi** selezionare **Nome**, **Product Code** (Codice prodotto) e **Sales Stage** (Fase vendite). 

    ![selezionare i campi](media/power-bi-visualization-powerapp/power-bi-fields.jpg)

4. Nell'oggetto visivo di Power Apps selezionare l'ambiente di Power Apps in cui si vuole creare l'app, quindi selezionare **Crea nuovo**.

    ![Creare una nuova app](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    In Power Apps Studio si può osservare che viene creata un'app di base con una *raccolta* che visualizza uno dei campi selezionati in Power BI.

    ![Apertura di Power Apps](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Ridimensionare la raccolta in modo che occupi solo la metà della schermata. 

6. Nel riquadro sinistro selezionare **Screen1**, quindi impostare la proprietà **Riempimento** su "Blu chiaro", per una migliore visualizzazione nel report.

    ![tavolozza dei colori](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Creare spazio per un controllo etichetta. 

    ![modificare le dimensioni della raccolta](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. Nella **raccolta** inserire un controllo etichetta di testo.

   ![controllo etichetta](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Trascinare l'etichetta nella parte inferiore dell'oggetto visivo. Impostare la proprietà **Text** su `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Viene ora visualizzato il numero totale di opportunità nel set di dati.

    ![App con raccolta ridimensionata](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![App con etichetta aggiornata](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Salvare l'app con il nome "Opportunities app". 

    ![salvare l'app](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Visualizzare l'app nel report
L'app è ora disponibile nel report di Power BI e interagisce con altri oggetti visivi perché condivide la stessa origine dati.

![App nel report di Power BI](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

Nel report di Power BI selezionare **Gen** nel filtro dei dati, che consente di applicare il filtro all'intero report compresi i dati nell'app.

![report filtrato](media/power-bi-visualization-powerapp/power-bi-last.png)

Si noti che il numero di opportunità nell'app corrisponde al conteggio in alto a sinistra del report. È possibile selezionare altri elementi nel report e i dati nell'app vengono aggiornati di conseguenza.


## <a name="clean-up-resources"></a>Pulire le risorse
Se non si vuole più usare l'esempio di analisi delle opportunità, è possibile eliminare il dashboard, il report e il set di dati.


## <a name="next-steps"></a>Passaggi successivi
[Oggetto visivo Domande e risposte](power-bi-visualization-types-for-reports-and-q-and-a.md)