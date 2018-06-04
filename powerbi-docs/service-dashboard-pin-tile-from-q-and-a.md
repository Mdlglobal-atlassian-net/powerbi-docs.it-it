---
title: Come aggiungere un riquadro a un dashboard da Domande e risposte
description: Documentazione su come aggiungere un riquadro a un dashboard di Power BI nella casella della domanda di Domande e risposte
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: e71412febc5b8d8a9ee4ff20174496de0c7d51f2
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34251415"
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Aggiungere un riquadro a un dashboard da Domande e risposte
## <a name="how-to-pin-a-tile-from-qa"></a>Come aggiungere un riquadro dalle domande e risposte
Domande e risposte è lo strumento ad hoc per la creazione di report di Power BI. Se ad esempio si vogliono ottenere informazioni dettagliate specifiche, è possibile porre una domanda sui dati per ottenere una risposta sotto forma di visualizzazione.

In questa procedura viene usato il servizio Power BI (app.powerbi.com) per aprire un dashboard, porre una domanda usando il linguaggio naturale per creare una visualizzazione e aggiungere tale visualizzazione a un dashboard. I dashboard non sono disponibili in Power BI Desktop. Per informazioni su come usare Domande e risposte con altri strumenti e contenuti di Power BI, vedere la [Panoramica di Domande e risposte di Power BI](power-bi-q-and-a.md). 

Per seguire la procedura, aprire il [dashboard dell'esempio di analisi delle vendite al dettaglio](sample-retail-analysis.md).


1. Aprire un [dashboard](service-dashboards.md) a cui è stato aggiunto almeno un riquadro da un report. Quando si pone una domanda, Power BI cerca la risposta in qualsiasi set di dati per il quale è stato aggiunto un riquadro nel dashboard.  Per altre informazioni, vedere [Origini dati per il servizio Power BI](service-get-data.md).
2. Nella casella della domanda nella parte superiore del dashboard iniziare a digitare una domanda relativa ai dati.  
   ![Casella delle domande di Domande e risposte](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Ad esempio, se si digita "vendite dell'ultimo anno per mese e territorio"...  
   ![Digitare una domanda](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)

   la casella della domanda offre alcuni suggerimenti.
4. Per aggiungere il grafico al dashboard sotto forma di riquadro, selezionare la puntina ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) sul lato destro superiore dell'area di disegno. Se il dashboard è stato condiviso con l'utente, non sarà possibile aggiungere visualizzazioni.

5. Aggiungere il riquadro a un dashboard esistente o a un nuovo dashboard.

   ![Finestra di dialogo Aggiungi al dashboard](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Dashboard esistente: selezionare il nome del dashboard nell'elenco a discesa. I dashboard selezionabili sono solo quelli presenti nell'area di lavoro corrente.
   * Nuovo dashboard: digitare il nome del nuovo dashboard per aggiungerlo all'area di lavoro corrente.

6. Selezionare **Aggiungi**.

   Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che la visualizzazione è stata aggiunta al dashboard sotto forma di riquadro.  

   ![Aggiunto al dashboard](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Selezionare **Vai al dashboard** per visualizzare il nuovo riquadro. È quindi possibile [rinominare, ridimensionare, aggiungere un collegamento ipertestuale, riposizionare il riquadro e molto altro](service-dashboard-edit-tile.md) nel dashboard.

   ![dashboard con riquadri](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* Quando si inizia a digitare una domanda, Domande e risposte inizia subito a cercare la risposta migliore in tutti i set di dati associati al dashboard corrente,  ovvero quello elencato nella barra di spostamento superiore. Questa domanda, ad esempio, viene posta nel dashboard dell'**esempio di analisi delle vendite al dettaglio**, che fa parte dell'area di lavoro per le app **mihart**.

  ![Percorsi di navigazione](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **Per individuare i set di dati da usare**,  Domande e risposte accede a tutti i set di dati per cui è stata aggiunta almeno una visualizzazione al dashboard.

* **Se non è possibile visualizzare la casella della domanda**, contattare l'amministratore di Power BI. L'amministratore può disabilitare Domande e risposte.


## <a name="next-steps"></a>Passaggi successivi
[Rinominare, ridimensionare, aggiungere un collegamento ipertestuale, riposizionare il riquadro e molto altro ancora](service-dashboard-edit-tile.md)    
[Visualizzare il riquadro del dashboard nella modalità messa a fuoco](service-focus-mode.md)     
Tornare a [Domande e risposte in Power BI](power-bi-q-and-a.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
