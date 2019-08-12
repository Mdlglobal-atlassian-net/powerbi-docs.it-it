---
title: Creare un riquadro a un dashboard di Power BI da un report
description: Creare un riquadro a un dashboard di Power BI da un report
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
ms.openlocfilehash: b50d247f54cfe2af4cefbd14b9528b1dfa263acf
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68624293"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Creare un riquadro a un dashboard di Power BI da un report
Dopo aver letto l'[introduzione ai dashboard in Power BI](service-dashboards.md) si può creare il proprio dashboard. Per creare un dashboard è possibile procedere in molti modi. Si può partire da un report, da zero, da un set di dati o dalla duplicazione di un dashboard esistente.  

L'operazione può sembrare complicata all'inizio, quindi si può iniziare creando un dashboard semplice e rapido che prende le visualizzazioni da un report già creato. 

Dopo aver seguito questa procedura rapida per iniziare, si avrà una buona conoscenza dei seguenti aspetti:
- Relazione tra dashboard e report
- Come aprire la visualizzazione di modifica nell'editor di report
- Come aggiungere riquadri 
- Come spostarsi tra un dashboard e un report 

## <a name="who-can-create-a-dashboard"></a>Chi può creare un dashboard?
La creazione di un dashboard è una funzionalità per *autori* e richiede autorizzazioni di modifica sul report. Le autorizzazioni di modifica sono disponibili per gli autori dei report e per i colleghi a cui l'autore concede l'accesso. Ad esempio, se un utente crea un report in un'area di lavoro e quindi aggiunge un altro utente come membro di tale area di lavoro, entrambi avranno le autorizzazioni di modifica. Se invece un report viene condiviso direttamente o come parte di un'[app Power BI](service-create-distribute-apps.md) (*utilizzo* del report), non sarà possibile aggiungere riquadri a un dashboard.
 
![Dashboard](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

> [!NOTE] 
> I dashboard sono una funzionalità del servizio Power BI, non di Power BI Desktop. I dashboard non possono essere creati nella versione di Power BI per i dispositivi mobili, ma possono essere [visualizzati e condivisi](consumer/mobile/mobile-apps-view-dashboard.md) su tali dispositivi.
>
> 

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Video: Creare un dashboard aggiungendo oggetti visivi e immagini da un report
Osserviamo Amanda creare un nuovo dashboard aggiungendo le visualizzazioni da un report. Seguiamo poi la procedura in [Importare un set di dati con un report](#import-a-dataset-with-a-report) per provare in autonomia usando l'esempio dell'analisi di approvvigionamento.
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importare un set di dati con un report
Importeremo uno dei set di dati di esempio di Power BI e lo useremo per creare il nuovo dashboard. L'esempio che useremo è una cartella di lavoro di Excel con due fogli PowerView. Quando Power BI importa la cartella di lavoro, aggiunge un set di dati e un report all'area di lavoro. Il report viene creato automaticamente dai fogli PowerView.

1. Scaricare il [file di Excel](http://go.microsoft.com/fwlink/?LinkId=529784) dell'esempio di analisi dell'approvvigionamento. È consigliabile salvarlo in OneDrive for Business.
2. Aprire il servizio Power BI nel browser (app.powerbi.com).
3. Nel riquadro di spostamento a sinistra selezionare **Area di lavoro personale** e quindi selezionare **Recupera dati**.

    ![Riquadro di spostamento a sinistra](media/service-dashboard-create/power-bi-get-data3.png)
5. Selezionare **File**.

   ![Ottenere i file](media/service-dashboard-create/power-bi-select-files.png)
6. Andare al percorso in cui è stato salvato il file di Excel di esempio dell'analisi di approvvigionamento. Selezionarlo e scegliere **Connetti**.

   ![Connettersi ai file](media/service-dashboard-create/power-bi-connectnew.png)
7. Per questo esercizio, selezionare **Importa**.

    ![Finestra OneDrive for Business](media/service-dashboard-create/power-bi-import.png)
8. Quando viene visualizzato il messaggio di conferma, fare clic sulla **x** per eliminarlo.

   ![Messaggio di operazione completata](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-tiles-to-your-dashboard"></a>Aprire il report e aggiungere alcuni riquadri a un dashboard
1. Nella stessa area di lavoro selezionare la scheda **Report** e quindi selezionare **Esempio di analisi dell'approvvigionamento** per aprire il report.

    ![Scheda Report](media/service-dashboard-create/power-bi-reports.png) Il report viene aperto nella visualizzazione di lettura. Si noti che sono presenti due schede nella parte inferiore: **Discount Analysis** (Analisi degli sconti) e **Spend Overview** (Panoramica di spesa). Ogni scheda rappresenta una pagina del report.

2. Selezionare **Modifica report** per aprire il report in visualizzazione di modifica.

    ![Report nella visualizzazione di lettura](media/service-dashboard-create/power-bi-reading-view.png)
3. Passare il mouse su una visualizzazione per vedere le opzioni disponibili. Per aggiungere una visualizzazione a un dashboard, selezionare l'icona di aggiunta. ![Icona Aggiungi](media/service-dashboard-create/power-bi-pin-icon.png).

    ![Passare il mouse sul riquadro](media/service-dashboard-create/power-bi-hover.png)
4. Poiché si sta creando un nuovo dashboard, selezionare l'opzione per **Nuovo dashboard** e assegnare un nome.

    ![Finestra di dialogo Aggiungi al dashboard](media/service-dashboard-create/power-bi-pin-tile.png)
5. Quando si seleziona **Aggiungi**, Power BI crea il nuovo dashboard nell'area di lavoro corrente. Quando appare il messaggio **Aggiunti al dashboard**, selezionare **Vai al dashboard**. Se viene chiesto di salvare il report, scegliere **Salva**.

    ![Messaggio di operazione completata](media/service-dashboard-create/power-bi-pin-success.png)

    Power BI apre il nuovo dashboard, che include un solo riquadro, vale a dire la visualizzazione appena bloccata.

   ![Dashboard con un riquadro](media/service-dashboard-create/power-bi-pinned.png)
7. Per tornare al report, selezionare il riquadro. Aggiungere qualche altro riquadro al nuovo dashboard. Quando viene visualizzata la finestra **Aggiungi al dashboard**, selezionare **Dashboard esistente**.  

   ![Finestra di dialogo Aggiungi al dashboard](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>Aggiungere un'intera pagina del report al dashboard
Invece di aggiungere un singolo oggetto visivo alla volta, è possibile [aggiungere un'intera pagina del report come *riquadro animato*](service-dashboard-pin-live-tile-from-report.md). Di seguito viene descritta la procedura.

1. Nell'editor di report selezionare la scheda **Spend Overview** (Panoramica di spesa) per aprire la seconda pagina del report.

   ![Scheda Report](media/service-dashboard-create/power-bi-page-tab.png)

2. È preferibile che tutti gli oggetti visivi nel report siano presenti nel dashboard. Nell'angolo superiore destro della barra dei menu selezionare **Aggiungi pagina dinamica**. In un dashboard, i riquadri delle pagine dinamiche vengono aggiornati ogni volta che viene aggiornata la pagina.

   ![Angolo in alto a destra dell'editor di report](media/service-dashboard-create/power-bi-pin-live.png)

3. Quando viene visualizzata la finestra **Aggiungi al dashboard**, selezionare **Dashboard esistente**.

   ![Finestra di dialogo Aggiungi al dashboard](media/service-dashboard-create/power-bi-pin-live2.png)

4. Quando viene visualizzato il messaggio di operazione riuscita, selezionare **Vai al dashboard**. Verranno visualizzati i riquadri aggiunti dal report. Nell'esempio riportato di seguito vengono aggiunti due riquadri dalla pagina 1 del report e un riquadro animato corrispondente alla pagina due del report.

   ![Dashboard](media/service-dashboard-create/power-bi-dashboard.png)

## <a name="next-steps"></a>Passaggi successivi
Congratulazioni per aver creato il primo dashboard. Ora che il dashboard è creato, lo si può usare per fare molte altre cose. Leggere uno degli articoli suggeriti di seguito o iniziare a esplorare autonomamente: 

* [Ridimensionare e spostare i riquadri](service-dashboard-edit-tile.md)
* [Informazioni sui riquadri del dashboard](service-dashboard-tiles.md)
* [Condividere il dashboard creando un'app](service-create-workspaces.md)
* [Power BI - Concetti di base](service-basic-concepts.md)
* [Suggerimenti per la progettazione di un dashboard ottimale](service-dashboards-design-tips.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/).
