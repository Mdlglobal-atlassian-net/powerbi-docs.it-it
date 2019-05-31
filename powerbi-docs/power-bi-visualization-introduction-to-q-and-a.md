---
title: Creare un oggetto visivo con Power BI domande e risposte
description: Informazioni su come creare un oggetto visivo con domande e risposte nel servizio Power BI usando l'esempio di analisi delle vendite al dettaglio
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625188"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Creare un oggetto visivo con Power BI domande e risposte

A volte il modo più rapido per ottenere una risposta dai dati consiste nel porre una domanda usando il linguaggio naturale.  In questo articolo vengono esaminati due diversi modi di creare la stessa visualizzazione: prima di tutto, ponendo una domanda con domande e risposte e in secondo luogo, creare l'applicazione in un report. Usiamo il servizio Power BI per creare l'oggetto visivo nel report, ma il processo è quasi identico tramite Power BI Desktop.

![Power BI riempito grafico](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Per seguire la procedura serve un report che si possa modificare e quindi verrà usato uno degli esempi disponibili per Power BI.

## <a name="create-a-visual-with-qa"></a>Creare un oggetto visivo con domande e risposte

Come si vedrà la creazione di questo grafico a linee mediante domande e risposte?

1. Nell'area di lavoro di Power BI selezionare **Recupera dati** \> **Esempi** \> **Esempio di analisi delle vendite al dettaglio** > **Connetti**.

1. Aprire il dashboard di esempio di analisi delle vendite al dettaglio e posizionare il cursore in una casella, le domande e risposte **porre una domanda sui dati**.

    ![Posizionare il cursore in una casella di domande e risposte](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Nella casella di domande e risposte, digitare simile a questa domanda:
   
    **vendite di quest'anno e vendite anno per mese come grafico ad area**
   
    Durante la digitazione di una domanda, Domande e risposte seleziona la visualizzazione più adatta per fornire una risposta. La visualizzazione cambia dinamicamente via via che si modifica la domanda. Domande e risposte consente anche di formulare una domanda con i suggerimenti, il completamento automatico e le correzioni ortografiche. Domande e risposte suggerisce una modifica di piccole formulazione delle parole: "vendite di quest'anno e vendite anno per *mese ora* come grafico ad aree".  

    ![Domande e risposte una formulazione con correzione](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Selezionare la frase per accettare il suggerimento. 
   
   Quando si finisce di digitare la domanda, il risultato è lo stesso grafico visualizzati nel dashboard.
   
   ![Domande e risposte di un grafico ad area colorata](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Per aggiungere il grafico al dashboard, selezionare l'icona della puntina ![Icona Aggiungi](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) nell'angolo in alto a destra.

## <a name="create-a-visual-in-the-report-editor"></a>Creare un oggetto visivo nell'editor del report

1. Tornare al dashboard Esempio di analisi delle vendite al dettaglio.
   
2. Il dashboard contiene il riquadro grafico area stesso per "Vendite dello scorso anno e vendite di quest'anno".  Selezionare questo riquadro. Non selezionare il riquadro che è stato creato con domande e risposte. Selezione di questa consente di aprire domande e risposte. Il riquadro grafico area originale è stato creato in un report, in modo che il report viene visualizzata la pagina che contiene la visualizzazione.

    ![Dashboard dell'esempio di analisi delle vendite al dettaglio](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Aprire il report in Visualizzazione di modifica selezionando **Modifica report**.  Se non si è proprietari di un report, non sarà possibile aprire il report in Visualizzazione di modifica.
   
    ![Pulsante Modifica report](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selezionare il grafico ad aree ed esaminare le impostazioni nel riquadro **Campi**.  L'autore del report ha creato questo grafico selezionando questi tre valori (**Last Year Sales** e **This Year Sales > valore** dal **Sales** tabella, e  **FiscalMonth** dal **fase** tabella) e organizzandoli nel **asse** e **valori** wells.
   
    ![Riquadro Visualizzazioni](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Noterete che finisce con l'oggetto visivo stesso. Creazione di queste caratteristiche non era troppo complicata. Ma creato con domande e risposte è più facile!

## <a name="next-steps"></a>Passaggi successivi

- [Usare domande e risposte nei dashboard e report](power-bi-tutorial-q-and-a.md)  
- [Domande e risposte per i consumer](consumer/end-user-q-and-a.md)
- [Usare correttamente i dati con Domande e risposte di Power BI](service-prepare-data-for-q-and-a.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

