---
title: Visualizzazioni Scheda (riquadri con totale)
description: Creare una visualizzazione Scheda in Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/24/2017
ms.author: mihart
ms.openlocfilehash: 1136aae9af4481a1d55ca3d11ed300242aab187b
ms.sourcegitcommit: 74fbbca81a056dda19b3647ae058005aba5296f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2018
---
# <a name="card-visualizations"></a>Visualizzazioni Scheda
A volte l'unico elemento che si vuole visualizzare in un dashboard o in un report di Power BI è un solo numero, ad esempio le vendite totali, la quota di mercato anno per anno o le opportunità totali. Questo tipo di visualizzazione è denominato *Scheda*. Come quasi tutte le visualizzazioni native di Power BI, è possibile creare le Schede con l'editor di report o con Domande e risposte.

![visualizzazione scheda](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Creare una scheda con l'editor di report
Per queste istruzioni si usa l'esempio di analisi delle vendite al dettaglio. Per seguire le istruzioni, [scaricare l'esempio](sample-datasets.md) per il servizio Power BI (app.powerbi.com) o Power BI Desktop.   

1. Iniziare in una [pagina di report vuota ](power-bi-report-add-page.md) e selezionare il campo **Store** \> **Open store count**. Se si usa il servizio Power BI, sarà necessario aprire il report nella [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md).

    Power BI crea un istogramma con un numero.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. Nel riquadro Visualizzazioni selezionare l'icona Scheda.

   ![](media/power-bi-visualization-card/pbi_changechartcard.png)
6. Passare il puntatore del mouse su una scheda e selezionare l'icona a forma di puntina ![](media/power-bi-visualization-card/pbi_pintile.png) per aggiungere la visualizzazione al dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Aggiungere il riquadro a un dashboard esistente o a un nuovo dashboard.

   * Dashboard esistente: selezionare il nome del dashboard nell'elenco a discesa.
   * Nuovo dashboard: digitare il nome del nuovo dashboard.
8. Selezionare **Aggiungi**.

   Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che è stata aggiunta la visualizzazione, come riquadro, al dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin-success-message.png)
9. Selezionare **Vai al dashboard**. In quel punto è possibile [modificare e spostare](service-dashboard-edit-tile.md) la visualizzazione aggiunta.


## <a name="create-a-card-from-the-qa-question-box"></a>Creare una scheda dalla casella delle domande di Domande e risposte
La casella delle domande di Domande e risposte rappresenta il modo più semplice per creare una scheda. La casella delle domande di Domande e risposte è disponibile in un dashboard o in un report del servizio Power BI (app.powerbi.com). La procedura seguente illustra come creare una scheda da un dashboard del servizio Power BI. Se si vuole creare una scheda usando Domande e risposte in Power BI Desktop, [seguire queste istruzioni](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA) per l'anteprima di Domande e risposte per i report di Power BI Desktop.

1. Creare un [dashboard](service-dashboards.md) e [recuperare i dati](service-get-data.md). In questa procedura viene usato l'[esempio di analisi delle opportunità](sample-opportunity-analysis.md).

1. Nella casella della domanda nella parte superiore del dashboard iniziare a digitare una domanda relativa ai dati. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

>**SUGGERIMENTO**: nella [Visualizzazione di modifica](service-reading-view-and-editing-view.md) in un report del servizio Power BI selezionare **Poni una domanda** nella barra dei menu superiore. In un report di Power BI Desktop individuare uno spazio vuoto e fare doppio clic per aprire una casella delle domande.

3. Ad esempio, digitare "number of opportunities" nella casella della domanda.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   La casella delle domande fornisce suggerimenti e riformulazioni e visualizza infine il numero totale.  
4. Selezionare l'icona a forma di puntina ![](media/power-bi-visualization-card/pbi_pintile.png) nell'angolo in alto a destra per aggiungere la scheda al dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. Aggiungere la scheda, come un riquadro, a un dashboard esistente o a un nuovo dashboard.

   * Dashboard esistente: selezionare il nome del dashboard nell'elenco a discesa. I dashboard selezionabili sono solo quelli presenti nell'area di lavoro corrente.
   * Nuovo dashboard: digitare il nome del nuovo dashboard per aggiungerlo all'area di lavoro corrente.
6. Selezionare **Aggiungi**.

   Un messaggio di operazione riuscita (nell'angolo superiore destro) informa l'utente che è stata aggiunta la visualizzazione, come riquadro, al dashboard.  

   ![](media/power-bi-visualization-card/power-bi-success.png)
7. Selezionare **Vai al dashboard** per visualizzare il nuovo riquadro. È quindi possibile [rinominare, ridimensionare, aggiungere un collegamento ipertestuale, riposizionare il riquadro e molto altro](service-dashboard-edit-tile.md) nel dashboard.

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se la casella delle domande non viene visualizzata, contattare l'amministratore tenant o di sistema.    
- Se si usa Power BI Desktop e facendo doppio clic su uno spazio vuoto in un report Domande e risposte non si apre, potrebbe essere necessario abilitare questa funzionalità.  Selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità in anteprima > Domande e risposte** e riavviare Power BI Desktop.


## <a name="next-steps"></a>Passaggi successivi
[Riquadri del dashboard in Power BI](service-dashboard-tiles.md)

[Dashboard in Power BI](service-dashboards.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)