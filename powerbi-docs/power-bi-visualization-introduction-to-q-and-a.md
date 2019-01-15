---
title: Introduzione a Power BI - Domande e risposte
description: Introduzione a Domande e risposte nel servizio Power BI con l'Esempio di analisi delle vendite al dettaglio
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 87783b928fdec1cadf5318ae184858c37daa4acc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279252"
---
# <a name="get-started-with-power-bi-qa"></a>Introduzione a Power BI - Domande e risposte

A volte il modo più rapido per ottenere una risposta dai dati consiste nel porre una domanda usando il linguaggio naturale.  In questa guida introduttiva verranno esaminati due modi diversi per creare la stessa visualizzazione, ovvero creandola in un report e ponendo una domanda con Domande e risposte. Verrà usato il servizio Power BI, ma il processo per Power BI Desktop è quasi identico.

Per seguire la procedura serve un report che si possa modificare e quindi verrà usato uno degli esempi disponibili per Power BI.

## <a name="create-a-visual-in-the-report-editor"></a>Creare un oggetto visivo nell'editor del report

1. Nell'area di lavoro di Power BI selezionare **Recupera dati** \> **Esempi** \> **Esempio di analisi delle vendite al dettaglio** > **Connetti**.
   
2. Il dashboard contiene un riquadro con un grafico ad aree per le vendite dell'anno precedente e le vendite per l'anno in corso.  Selezionare questo riquadro. Se il riquadro è stato creato con Domande e risposte, verrà aperto in Domande e risposte. In questo caso, invece, siccome il riquadro è stato creato in un report, viene aperto il report e viene visualizzata la pagina che contiene la visualizzazione.

    ![Dashboard dell'esempio di analisi delle vendite al dettaglio](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Aprire il report in Visualizzazione di modifica selezionando **Modifica report**.  Se non si è proprietari di un report, non sarà possibile aprire il report in Visualizzazione di modifica.
   
    ![Pulsante Modifica report](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selezionare il grafico ad aree ed esaminare le impostazioni nel riquadro **Campi**.  L'autore del report ha creato questo grafico selezionando questi tre valori (**Time > FiscalMonth**, **Sales > This Year Sales**, **Sales > Last Year Sales**) e organizzandoli nelle aree **Asse** e **Valori**.
   
    ![Riquadro Visualizzazioni](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="create-the-same-visual-with-qa"></a>Creare lo stesso oggetto visivo con Domande e risposte

In che modo si potrebbe creare questo stesso grafico a linee mediante Domande e risposte?

![Casella Porre una domanda](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Tornare al dashboard Esempio di analisi delle vendite al dettaglio.
2. Usando il linguaggio naturale, digitare una domanda simile alla seguente nella casella della domanda:
   
   **a quanto ammontano le vendite di quest'anno e le vendite dell'anno scorso per mese in un grafico ad area**
   
   Durante la digitazione di una domanda, Domande e risposte seleziona la visualizzazione più adatta per fornire una risposta. La visualizzazione cambia dinamicamente via via che si modifica la domanda. Domande e risposte consente anche di formulare una domanda con i suggerimenti, il completamento automatico e le correzioni ortografiche.
   
   Terminato l'inserimento della domanda, si ottiene lo stesso identico grafico presente nel report,  ma in modo molto più rapido.
   
   ![Esempio di domanda](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. Analogamente all'elaborazione dei report, in Domande e risposte si ha accesso ai riquadri Visualizzazioni, Filtri e Campi.  Aprire questi riquadri per esplorare e modificare ulteriormente l'oggetto visivo.
4. Per aggiungere il grafico al dashboard, selezionare l'icona della puntina ![Icona Aggiungi](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Passaggi successivi
[Domande e risposte in Power BI](consumer/end-user-q-and-a.md)

[Usare correttamente i dati con Domande e risposte di Power BI](service-prepare-data-for-q-and-a.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

