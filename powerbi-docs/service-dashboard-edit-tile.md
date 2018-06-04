---
title: Modificare un riquadro del dashboard
description: Questa esercitazione illustra la creazione di un riquadro, l'aggiunta del riquadro a un dashboard e infine spiega come modificare il riquadro del dashboard, ovvero come ridimensionare, spostare, rinominare, aggiungere, eliminare il riquadro e aggiungere un collegamento ipertestuale.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: lJKgWnvl6bQ
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 07db52bd2ffd881417f7ff59647c6779f7dc6bce
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34248343"
---
# <a name="edit-or-remove-a-dashboard-tile"></a>Modificare o rimuovere un riquadro del dashboard

## <a name="dashboard-owners-versus-dashboard-consumers"></a>Confronto tra *proprietari* del dashboard e *consumer* del dashboard
Quando si crea o si è proprietari di un dashboard, sono disponibili molte opzioni per la modifica dell'aspetto e del comportamento predefinito dei riquadri in tale dashboard. Usare le impostazioni e le strategie seguenti per progettare l'esperienza di *utilizzo* del dashboard per i colleghi.  È possibile stabilire che la selezione di un riquadro comporti l'apertura del report sottostante, di un URL personalizzato o di un dashboard diverso, oppure [aggiungere un riquadro che mostra un video o dati di streaming](service-dashboard-add-widget.md). È anche possibile [creare un riquadro con filtri dei dati interattivi](service-dashboard-pin-live-tile-from-report.md). L'*autore* può scegliere tra diverse opzioni. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

In questo articolo vengono trattati gli argomenti seguenti.

* [Creare una visualizzazione e aggiungerla a un dashboard](#create)
* [Spostare un riquadro](#move)
* [Ridimensionare un riquadro](#resize)
* [Rinominare un riquadro](#rename)
* [Aggiungere un collegamento ipertestuale a un riquadro](#hyperlink)
* [Aggiungere un riquadro a un altro dashboard](#different)
* [Eliminare un riquadro](#delete)
  
 > [!TIP]
 > Per modificare la visualizzazione nel riquadro, eliminare il riquadro e aggiungere un nuovo [riquadro del dashboard](service-dashboard-tiles.md).
 > 

 ### <a name="prerequisites"></a>Prerequisiti
 1. Per seguire la procedura, aprire il servizio Power BI (non Power BI Desktop) e [scaricare l'Esempio di analisi della spesa IT](sample-it-spend.md). Quando viene visualizzato il messaggio "Operazione riuscita", selezionare **Vai al dashboard**

- - -
<a name="create"></a>

## <a name="create-a-new-visualization-and-pin-it-to-the-dashboard"></a>Creare una nuova visualizzazione e aggiungerla al dashboard
1. Dal dashboard dell'Esempio di analisi della spesa IT selezionare il riquadro "Amount" per aprire il report.

    ![Riquadro della quantità](media/service-dashboard-edit-tile/power-bi-amount-tile.png)

2. Aprire il report in visualizzazione di modifica selezionando **Modifica report** sulla barra dei menu in alto.

3. Aggiungere una nuova pagina del report selezionando il segno più (+) nella parte inferiore del report.

    ![Icona segno più](media/service-dashboard-edit-tile/power-bi-add-page.png)

4. Dal riquadro CAMPI selezionare **Fact > Amount** e **Business Area > Business Area**.
 
5. Dal riquadro VISUALIZZAZIONI selezionare l'icona del grafico ad anello per convertire la visualizzazione in un grafico ad anello.

    ![Riquadro Visualizzazioni](media/service-dashboard-edit-tile/power-bi-donut-chart.png)

5. Selezionare l'icona a forma di puntina e aggiungere il grafico ad anello al dashboard dell'Esempio di analisi della spesa IT.

   ![Passare il mouse sul riquadro](media/service-dashboard-edit-tile/power-bi-pin.png)

6. Quando viene visualizzato il messaggio "Operazione riuscita", selezionare **Vai al dashboard**. Verrà richiesto di salvare le modifiche. Selezionare **Salva**.

- - -
<a name="move"></a>

## <a name="move-the-tile"></a>Spostare il riquadro
Individuare il nuovo riquadro nel dashboard. Selezionare e tenere premuto il riquadro per trascinarlo nella nuova posizione nell'area di disegno dashboard.

- - -
<a name="resize"></a>

## <a name="resize-the-tile"></a>Ridimensionare il riquadro
È possibile creare riquadri di dimensioni diverse, da unità di riquadro 1x1 fino a 5x5. Selezionare e trascinare il punto di controllo (nell'angolo in basso a destra) per ridimensionare il riquadro.

![Video](media/service-dashboard-edit-tile/pbigif_resizetile4.gif)

- - -
## <a name="the-ellipses--menu"></a>Menu di puntini di sospensione (...)

1. Selezionare i puntini di sospensione (...) nell'angolo in alto a destra del riquadro. 
   
   ![Puntini di sospensione del riquadro](media/service-dashboard-edit-tile/power-bi-tile.png)

2. Passare il puntatore del mouse sul riquadro "Account" del dashboard e selezionare i puntini di sospensione per visualizzare le opzioni. Le opzioni disponibili dipendono dal tipo di riquadro.  Ad esempio, le opzioni disponibili per un riquadro animato sono diverse rispetto alle opzioni per un riquadro di visualizzazione standard. Se un dashboard è stato condiviso con l'utente, ovvero se non si è il proprietario del dashboard, saranno inoltre disponibili meno opzioni.

   ![Menu opzioni puntini di sospensione](media/service-dashboard-edit-tile/power-bi-tile-menu-new.png)

3. Selezionare **Modifica dettagli** per aprire la finestra "Dettagli riquadro". 

    Modificare il titolo e il comportamento predefinito del riquadro.  È ad esempio possibile che si voglia stabilire che quando un *consumer* seleziona un riquadro non venga aperto il report usato per creare tale riquadro ma venga invece visualizzato un nuovo dashboard.  
   


<a name="rename"></a>

### <a name="rename-the-tile"></a>Rinominare il riquadro
Nella parte superiore della finestra "Dettagli riquadro" cambiare **Titolo** in **Amount spent**.

![Finestra Dettagli riquadro](media/service-dashboard-edit-tile/power-bi-tile-title.png)


<a name="hyperlink"></a>

### <a name="change-the-default-hyperlink"></a>Modificare il collegamento ipertestuale predefinito
Per impostazione predefinita, se si seleziona un riquadro viene in genere aperto il report in cui è stato creato il riquadro oppure Domande e risposte (se il riquadro è stato creato in Domande e risposte). Per creare un collegamento a una pagina Web, a un altro dashboard o report (nella stessa area di lavoro), a un report SSRS o ad altri contenuti online, aggiungere un collegamento personalizzato.

1. Sotto l'intestazione Funzionalità selezionare **Imposta collegamento personalizzato**.

2. Selezionare **Collega a un dashboard o un report nell'area di lavoro corrente** e quindi selezionare un'opzione dall'elenco a discesa.  In questo esempio è stato selezionato il dashboard dell'Esempio di analisi delle risorse umane. Se questo esempio non è già disponibile nell'area di lavoro, è possibile aggiungerlo e tornare a questo passaggio oppure selezionare un dashboard diverso. 

    ![Finestra di dialogo Funzionalità](media/service-dashboard-edit-tile/power-bi-custom-link.png)

3. Selezionare **Applica**.

4. Il nuovo titolo viene visualizzato nel riquadro.  Quando si seleziona il riquadro, Power BI apre il dashboard delle risorse umane. 

    ![Titolo del riquadro](media/service-dashboard-edit-tile/power-bi-title.png)

<a name="different"></a>

### <a name="pin-the-tile-to-a-different-dashboard"></a>Aggiungere il riquadro a un altro dashboard
1. Dal menu a discesa con puntini di sospensione selezionare **Aggiungi sezione** ![Icona della puntina](media/service-dashboard-edit-tile/pinnooutline.png).
2. Decidere se aggiungere un duplicato di questo riquadro a un dashboard esistente o a un nuovo dashboard. 
   
   ![Finestra di dialogo Aggiungi al dashboard](media/service-dashboard-edit-tile/pbi_pintoanotherdash.png)
3. Selezionare **Aggiungi**.

<a name="delete"></a>

### <a name="delete-the-tile"></a>Eliminare il riquadro
1. Per rimuovere in modo permanente un riquadro da un dashboard, selezionare **Elimina riquadro** ![Icona Elimina](media/service-dashboard-edit-tile/power-bi-delete-tile-icon.png) dal menu a discesa con puntini di sospensione. 

2. Se si elimina un riquadro, non viene eliminata la visualizzazione sottostante. Aprire il report sottostante selezionando il riquadro "Amount". Aprire l'ultima pagina del report per verificare che le visualizzazioni originali non siano state eliminate dal report. 

- - -
## <a name="next-steps"></a>Passaggi successivi
[Riquadri del dashboard in Power BI](service-dashboard-tiles.md)

[Dashboard in Power BI](service-dashboards.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

