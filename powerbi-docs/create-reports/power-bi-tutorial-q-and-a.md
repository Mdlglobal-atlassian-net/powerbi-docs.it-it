---
title: Usare Domande e risposte di Power BI per esplorare e creare oggetti visivi
description: Informazioni su come usare Domande e risposte di Power BI per creare nuove visualizzazioni nei dashboard e nei report.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: b98d3b154d779a9b9ae04dfa00a6033d59c45c9c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309591"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Usare Domande e risposte di Power BI per esplorare dati e creare oggetti visivi

A volte il modo più rapido per ottenere una risposta dai dati consiste nel porre una domanda usando il linguaggio naturale. La funzionalità Domande e risposte di Power BI consente di esplorare i dati usando le parole del linguaggio naturale.  La prima parte di questo articolo spiega come usare Domande e risposte nei dashboard del servizio Power BI. La seconda parte illustra le operazioni che è possibile eseguire con Domande e risposte quando si creano report nel servizio Power BI o in Power BI Desktop. Per altre informazioni, vedere l'articolo [Domande e risposte per i consumer](../consumer/end-user-q-and-a.md). 

Gli argomenti relativi a [Domande e risposte nelle app Power BI per dispositivi mobili](../consumer/mobile/mobile-apps-ios-qna.md) e [Domande e risposte con Power BI Embedded](../developer/embedded/qanda.md) vengono illustrati in articoli separati. 

Domande e risposte è una funzionalità interattiva, anche divertente. Una domanda porta spesso a formulare altre domande man mano che le visualizzazioni rivelano percorsi interessanti da perseguire. Il video seguente mostra come usare Domande e risposte per creare visualizzazioni, analizzare questi oggetti visivi e aggiungerli ai dashboard.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Parte 1: Usare Domande e risposte in un dashboard nel servizio Power BI

Nel servizio Power BI (app.powerbi.com) un dashboard contiene riquadri aggiunti da uno o più set di dati ed è quindi possibile porre domande su tutti i dati inclusi in questi set di dati. Per visualizzare i report e i set di dati usati per creare il dashboard, selezionare **Visualizza elementi correlati** dalla barra dei menu.

![Visualizzare report e set di dati correlati](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

La casella delle domande di Domande e risposte si trova nell'angolo in alto a sinistra del dashboard e consente di digitare le domande usando il linguaggio naturale. Se la casella di Domande e risposte non è visualizzata, vedere [Considerazioni e risoluzione dei problemi](../consumer/end-user-q-and-a.md#considerations-and-troubleshooting) nell'articolo **Domande e risposte per i consumer**.  Domande e risposte riconosce le parole digitate e determina dove (ovvero in quale set di dati) trovare la risposta. Domande e risposte consente anche di formulare la domanda con il completamento automatico, la riformulazione e altri ausili testuali e visivi.

![Casella delle domande di Domande e risposte](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

La risposta alla domanda viene mostrata come visualizzazione interattiva e si aggiorna man mano che si modifica la domanda.

1. Aprire un dashboard e posizionare il cursore nella casella delle domande. Selezionare **Nuova esperienza Domande e risposte** nell'angolo in alto a destra.

    ![Nuova esperienza Domande e risposte di Power BI](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Ancora prima di iniziare a digitare, Domande e risposte mostra una nuova schermata con suggerimenti utili a formulare la domanda. Verranno visualizzate frasi e domande complete contenenti i nomi delle tabelle nei set di dati sottostanti e, in alcuni casi, un elenco contenente domande complete se il proprietario del set di dati ha creato [domande in primo piano](service-q-and-a-create-featured-questions.md).

   ![Domande consigliate di Domande e risposte](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Si può scegliere una di queste domande come punto di partenza e quindi perfezionare la domanda per trovare una risposta specifica. In alternativa, usare un nome di tabella per agevolare l'inserimento di una nuova domanda.

2. Effettuare una selezione nell'elenco di domande oppure iniziare a digitare la domanda desiderata e selezionare una voce nell'elenco a discesa dei suggerimenti.

   ![Selezionare una domanda nell'elenco](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. Mentre si digita una domanda, Domande e risposte sceglie la visualizzazione migliore per visualizzare la risposta.

   ![Domanda "how many stores by state" in Domande e risposte](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. La visualizzazione cambia dinamicamente durante la modifica della domanda.

   ![Domanda "how many stores by state as bar chart" in Domande e risposte](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Quando si digita una domanda, Power BI cerca la migliore risposta in qualsiasi set di dati per cui è presente un riquadro nel dashboard.  Se tutti i riquadri si riferiscono al *set di dati A*, la risposta proverrà dal *set di dati A*.  Se invece sono presenti riquadri del *set di dati A* e del *set di dati B*, Domande e risposte cerca la risposta migliore in questi due set di dati.

   > [!TIP]
   > Prestare attenzione se è presente un solo riquadro del *set di dati A* perché, se viene rimosso dal dashboard, Domande e risposte non avrà più accesso al *set di dati A*.
   >

5. Quando il risultato è soddisfacente, aggiungere la visualizzazione a un dashboard selezionando l'icona di aggiunta nell'angolo in alto a destra. Se il dashboard è stato condiviso con l'utente corrente o fa parte di un'app, non sarà possibile aggiungere la visualizzazione.

   ![Aggiunta dell'oggetto visivo in Domande e risposte](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Parte 2: Usare Domande e risposte in un report del servizio Power BI o di Power BI Desktop

Usare Domande e risposte per esplorare il set di dati e aggiungere visualizzazioni al report e ai dashboard. Un report è basato su un singolo set di dati e potrebbe risultare completamente vuoto o contenere pagine piene di visualizzazioni. Tuttavia, se un report è vuoto, non significa che non sono presenti dati da esplorare. Il set di dati è collegato al report e attende che gli utenti esplorino i dati e creino le visualizzazioni.  Per visualizzare il set di dati usato per creare un report, aprire il report nella Visualizzazione di lettura nel servizio Power BI e selezionare **Visualizza elementi correlati** dalla barra dei menu.

![Visualizzare i set di dati correlati](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Per usare Domande e risposte nei report, sono necessarie le autorizzazioni di modifica per il report e per i set di dati sottostanti. Nell'articolo [Domande e risposte per i consumer](../consumer/end-user-q-and-a.md) questo viene descritto come uno scenario *autore*. Se invece si sta *utilizzando* un report condiviso da altri, Domande e risposte non è disponibile.

1. Aprire un report in Visualizzazione di modifica (servizio Power BI) o Visualizzazione report (Power BI Desktop) e selezionare **Poni/Invia una domanda** dalla barra dei menu.

    **Power BI Desktop**    
    ![Selezione di Poni una domanda in Power BI Desktop](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Servizio**    
    ![Selezione di Invia una domanda nel servizio Power BI](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Nell'area di disegno del report verrà visualizzata la casella delle domande di Domande e risposte. Nell'esempio seguente la casella delle domande viene visualizzata sopra un'altra visualizzazione. In questo caso, è consigliabile aggiungere una pagina vuota al report prima di porre una domanda.

    ![Casella delle domande di Domande e risposte](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Posizionare il cursore nella casella della domanda. Mentre si digita, Domande e risposte visualizza suggerimenti per formulare la domanda.

   ![Digitare nella casella delle domande di Domande e risposte](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. Mentre si digita una domanda, Domande e risposte seleziona la [visualizzazione](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) più adatta per la risposta. La visualizzazione cambia dinamicamente via via che si modifica la domanda.

   ![Domande e risposte crea una visualizzazione](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Quando si ottiene la visualizzazione desiderata, premere il tasto INVIO. Per salvare la visualizzazione con il report, fare clic su **File > Salva**.

6. Interagire con la nuova visualizzazione. Non è importante il modo in cui è stata creata la visualizzazione, perché l'interattività, la formattazione e le funzionalità saranno le stesse.

   ![Interagire con la visualizzazione](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Se la visualizzazione è stata creata nel servizio Power BI, sarà possibile [aggiungerla a un dashboard](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Indicare a Domande e risposte quali visualizzazioni usare 
Con Domande e risposte non solo è possibile chiedere ai dati di parlare da sé, ma è anche possibile specificare in che modo visualizzarli. È sufficiente aggiungere "come <visualization type>" alla fine della domanda.  ad esempio "mostra volume inventario per stabilimento come mappa" e "mostra inventario totale come scheda".  Provare in prima persona.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se la connessione al set di dati è stata effettuata tramite una connessione in tempo reale o un gateway, è necessario che la funzionalità Domande e risposte sia [abilitata per il set di dati](service-q-and-a-direct-query.md) in questione.

- È stato aperto un report ma l'opzione Domande e risposte non è visualizzata. Se si usa il servizio Power BI, assicurarsi di aprire il report nella Visualizzazione di modifica. Se non è possibile aprire la Visualizzazione di modifica, non si dispone delle autorizzazioni di modifica per il report e non è quindi possibile usare Domande e risposte per il report specifico.

## <a name="next-steps"></a>Passaggi successivi

- [Domande e risposte per i consumer](../consumer/end-user-q-and-a.md)   
- [Suggerimenti per porre domande in Domande e risposte](../consumer/end-user-q-and-a-tips.md)   
- [Preparare una cartella di lavoro per Domande e risposte](service-prepare-data-for-q-and-a.md)  
- [Preparare un set di dati locale per Domande e risposte](service-q-and-a-direct-query.md)   
- [Aggiungere un riquadro a un dashboard da Domande e risposte](service-dashboard-pin-tile-from-q-and-a.md)
