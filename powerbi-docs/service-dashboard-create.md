---
title: Creare un riquadro a un dashboard di Power BI da un report
description: Creare un riquadro a un dashboard di Power BI da un report
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/09/2017
ms.author: mihart
ms.openlocfilehash: 67cc9508d71fa29303d09e8901294a2d6b7f8a56
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Creare un riquadro a un dashboard di Power BI da un report
Dopo aver letto [Dashboard in Power BI](service-dashboards.md) si vuole creare un dashboard personalizzato. Ci sono molti modi diversi per creare un dashboard: partendo da un report, da zero, da un set di dati, attraverso la duplicazione di un dashboard esistente e altri ancora.  Questo argomento e il video correlato illustrano come creare un nuovo dashboard aggiungendo le visualizzazioni da un report esistente.

> **NOTA**: i dashboard sono una funzionalità del servizio Power BI, non di Power BI Desktop. I dashboard non possono essere creati nella versione di Power BI per i dispositivi mobili, sui cui possono essere soltanto [visualizzati e condivisi](mobile-apps-view-dashboard.md).
> 
> 

![](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Video: Creare un dashboard aggiungendo oggetti visivi e immagini da un report
Osserviamo Amanda creare un nuovo dashboard aggiungendo le visualizzazioni da un report. Dopodiché, provare a farlo da sé usando l'esempio dell'analisi di approvvigionamento e seguendo la procedura indicata sotto al video.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importare un set di dati con un report
Importeremo uno dei set di dati di esempio di Power BI e lo useremo per creare il nuovo dashboard. L'esempio che useremo è una cartella di lavoro di Excel con due fogli PowerView. Quando Power BI importa la cartella di lavoro, aggiunge un set di dati e anche un report all'area di lavoro.  Il report viene creato automaticamente dai fogli PowerView.

1. [Selezionare questo collegamento](http://go.microsoft.com/fwlink/?LinkId=529784) per scaricare e salvare il file di Excel di esempio dell'analisi di approvvigionamento. È consigliabile salvarlo in OneDrive for Business.
2. Aprire il servizio Power BI nel browser (app.powerbi.com).
3. Selezionare un'area di lavoro esistente oppure creare una nuova area di lavoro per le app.
4. Nel riquadro di spostamento a sinistra selezionare **Recupera dati**.
   
    ![](media/service-dashboard-create/power-bi-get-data3.png)
5. Selezionare **File**.
   
   ![](media/service-dashboard-create/power-bi-select-files.png)
6. Andare al percorso in cui è stato salvato il file di Excel di esempio dell'analisi di approvvigionamento. Selezionarlo e scegliere **Connetti**.
   
   ![](media/service-dashboard-create/power-bi-connectnew.png)
7. Per questo esercizio, selezionare **Importa**.
   
    ![](media/service-dashboard-create/power-bi-import.png)
8. Quando viene visualizzato il messaggio di conferma, fare clic sulla **x** per chiuderlo.
   
   ![](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>Aprire il report e aggiungere alcuni riquadri a un dashboard
1. Rimanendo nella stessa area di lavoro selezionare la scheda **Report**. Il report appena importato appare contrassegnato con un asterisco giallo. Selezionare il nome del report per aprirlo.
   
    ![](media/service-dashboard-create/power-bi-reports.png)
2. Il report viene aperto nella [Visualizzazione di lettura](service-reading-view-and-editing-view.md). Si noti che nella parte inferiore sono presenti due schede: Discount Analysis (Analisi sconti) e Spend Overview (Panoramica spesa). Ogni scheda rappresenta una pagina del report.
   
    ![](media/service-dashboard-create/power-bi-reading-view.png)
3. Passare il mouse su una visualizzazione per vedere le opzioni disponibili. Per aggiungere la visualizzazione a un dashboard, selezionare l'icona ![](media/service-dashboard-create/power-bi-pin-icon.png) perno.
   
    ![](media/service-dashboard-create/power-bi-hover.png)
4. Poiché stiamo creando un nuovo dashboard, selezionare l'opzione per **Nuovo dashboard** e assegnare un nuovo nome. 
   
   ![](media/service-dashboard-create/power-bi-pin-tile.png)
5. Quando si seleziona **Aggiungi**, Power BI crea il nuovo dashboard nell'area di lavoro corrente. Quando appare il messaggio **Aggiunti al dashboard**, selezionare **Vai al dashboard**. Se viene chiesto di salvare il report, scegliere **Salva**.
   
     ![](media/service-dashboard-create/power-bi-pin-success.png)
6. Power BI apre il nuovo dashboard in cui è presente un riquadro: la visualizzazione che appena stata aggiunta. 
   
   ![](media/service-dashboard-create/power-bi-pinned.png)
7. Per tornare al report, selezionare il riquadro. Aggiungere qualche altro riquadro al nuovo dashboard. A questo punto, quando viene visualizzata la finestra **Aggiungi al dashboard**, selezionare **Dashboard esistente**.  
   
   ![](media/service-dashboard-create/power-bi-existing-dashboard.png)

Congratulazioni per aver creato il primo dashboard. Ora che si dispone di un dashboard, ci sono molte altre cose che si possono fare con esso.  Provare uno dei **Passaggi successivi** suggeriti di seguito oppure usare ed esplorare per proprio conto.   

## <a name="next-steps"></a>Passaggi successivi
* [Ridimensionare e spostare i riquadri](service-dashboard-edit-tile.md)
* [Informazioni sui riquadri del dashboard](service-dashboard-tiles.md)
* [Condividere il dashboard creando un'app](service-create-distribute-apps.md)
* [Power BI - Concetti di base](service-basic-concepts.md)
* [Dashboard in Power BI](service-dashboards.md)
* [Suggerimenti per la progettazione di un dashboard ottimale](service-dashboards-design-tips.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

