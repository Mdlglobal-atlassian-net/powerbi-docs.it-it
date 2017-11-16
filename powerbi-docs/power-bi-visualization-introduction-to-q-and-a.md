---
title: Introduzione a Domande e risposte di Power BI (esercitazione)
description: 'Esercitazione: Introduzione a Domande e risposte nel servizio Power BI con l''Esempio di analisi delle vendite al dettaglio'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 2038fb5bd4a21235c3026c8506ae30b8c3e287e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="get-started-with-power-bi-qa-tutorial"></a>Introduzione a Domande e risposte di Power BI (esercitazione)
## <a name="tutorial-use-power-bi-qa-with-the-retail-analysis-sample"></a>Esercitazione: Usare Domande e risposte di Power BI con l'esempio di analisi delle vendite al dettaglio
A volte il modo più rapido per ottenere una risposta dai dati consiste nel porre una domanda usando il linguaggio naturale.  In questa esercitazione si esamineranno 2 modi diversi per creare la stessa visualizzazione, ovvero creandola in un report e ponendo una domanda con Domande e risposte.  

## <a name="method-1-using-the-report-editor"></a>Metodo 1: uso dell'editor di report
1. Nell'area di lavoro di Power BI selezionare **Recupera dati** \> **Esempi** \> **Esempio di analisi delle vendite al dettaglio** > **Connetti**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)
2. Il dashboard contiene un riquadro con un grafico ad aree per le vendite dell'anno precedente e le vendite per l'anno in corso.  Selezionare questo riquadro. 
   
   * Se il riquadro è stato creato con Domande e risposte, verrà aperto in Domande e risposte. 
   * In questo caso, invece, siccome il riquadro è stato creato in un report, viene aperto il report e viene visualizzata la pagina che contiene la visualizzazione.
3. Aprire il report in Visualizzazione di modifica selezionando **Modifica report**.  Se non si è proprietari di un report, non sarà possibile aprire il report in Visualizzazione di modifica.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selezionare il grafico ad aree ed esaminare le impostazioni nel riquadro **Campi**.  L'autore del report ha creato questo grafico selezionando questi 3 valori (**Time > FiscalMonth**, **Sales > This Year Sales**, **Sales > Last Year Sales**) e organizzandoli nelle aree **Asse** e **Valori**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="method-2-using-qa"></a>Metodo 2: uso di domande e risposte
In che modo si potrebbe creare questo stesso grafico a linee mediante Domande e risposte?

![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Tornare al dashboard Esempio di analisi delle vendite al dettaglio.
2. Usando il linguaggio naturale, digitare una domanda simile alla seguente nella casella della domanda:
   
   **a quanto ammontano le vendite di quest'anno e le vendite dell'anno scorso per mese in un grafico ad area**
   
   Durante la digitazione di una domanda, Domande e risposte seleziona la visualizzazione più adatta per fornire una risposta. La visualizzazione cambia dinamicamente via via che si modifica la domanda. Domande e risposte consente anche di formulare una domanda con i suggerimenti, il completamento automatico e le correzioni ortografiche.
   
   Terminato l'inserimento della domanda, si ottiene lo stesso identico grafico presente nel report,  ma in modo molto più rapido.
   
   ![](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. Analogamente all'elaborazione dei report, in Domande e risposte si ha accesso ai riquadri Visualizzazioni, Filtri e Campi.  Aprire questi riquadri per esplorare e modificare ulteriormente l'oggetto visivo.
4. Per aggiungere il grafico al dashboard, selezionare l'icona della puntina ![](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Passaggi successivi
[Che tipo di domande si possono porre in Domande e risposte?](service-q-and-a.md)

[Domande e risposte in Power BI](service-q-and-a.md)

[Usare correttamente i dati con Domande e risposte di Power BI](service-prepare-data-for-q-and-a.md)

[Preparazione di una cartella di lavoro per Domande e risposte](service-prepare-data-for-q-and-a.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

