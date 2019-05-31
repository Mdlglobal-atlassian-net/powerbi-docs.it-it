---
title: Visualizzazioni Scheda (riquadri con totale)
description: Creare una visualizzazione Scheda in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 164385fc232774999a21e1870b02fcb59b74ad50
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61153133"
---
# <a name="card-visualizations"></a>Visualizzazioni Scheda
A volte l'unico elemento che si vuole visualizzare in un dashboard o in un report di Power BI è un solo numero, ad esempio le vendite totali, la quota di mercato anno per anno o le opportunità totali. Questo tipo di visualizzazione è denominato *Scheda*. Come quasi tutte le visualizzazioni native di Power BI, è possibile creare le Schede con l'editor di report o con Domande e risposte.

![visualizzazione scheda](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Creare una scheda con l'editor di report
Per queste istruzioni si usa l'esempio di analisi delle vendite al dettaglio. Per seguire le istruzioni, [scaricare l'esempio](../sample-datasets.md) per il servizio Power BI (app.powerbi.com) o Power BI Desktop.   

1. Iniziare in una pagina di report vuota e selezionare il campo **Store** \> **Open store count**. Se si usa il servizio Power BI, sarà necessario aprire il report nella [Visualizzazione di modifica](../service-interact-with-a-report-in-editing-view.md).

    Power BI crea un istogramma con un numero.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. Nel riquadro Visualizzazioni selezionare l'icona Scheda.

   ![](media/power-bi-visualization-card/power-bi-templates.png)
6. Passare il puntatore del mouse su una scheda e selezionare l'icona a forma di puntina ![](media/power-bi-visualization-card/pbi_pintile.png) per aggiungere la visualizzazione al dashboard.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Aggiungere il riquadro a un dashboard esistente o a un nuovo dashboard.

   * Dashboard esistente: selezionare il nome del dashboard nell'elenco a discesa.
   * Nuovo dashboard: digitare il nome del nuovo dashboard.
8. Selezionare **Aggiungi**.

   Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che è stata aggiunta la visualizzazione, come riquadro, al dashboard.

   ![](media/power-bi-visualization-card/power-bi-success2.png)
9. Selezionare **Vai al dashboard**. In quel punto è possibile [modificare e spostare](../service-dashboard-edit-tile.md) la visualizzazione aggiunta.


## <a name="create-a-card-from-the-qa-question-box"></a>Creare una scheda dalla casella delle domande di Domande e risposte
La casella delle domande di Domande e risposte rappresenta il modo più semplice per creare una scheda. La casella delle domande di Domande e risposte è disponibile in un dashboard o in un report del servizio Power BI e nella visualizzazione report Desktop. La procedura seguente illustra come creare una scheda da un dashboard del servizio Power BI. Se si vuole creare una scheda usando Domande e risposte in Power BI Desktop, [seguire queste istruzioni](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#QandA) per l'anteprima di Domande e risposte per i report di Power BI Desktop.

1. Creare un [dashboard](../service-dashboards.md) e [recuperare i dati](../service-get-data.md). In questa procedura viene usato l'[esempio di analisi delle opportunità](../sample-opportunity-analysis.md).

1. Nella casella della domanda nella parte superiore del dashboard iniziare a digitare una domanda relativa ai dati. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

> [!TIP]
> In Visualizzazione di modifica in un report del servizio Power BI selezionare **Poni una domanda** sulla barra dei menu superiore. In un report di Power BI Desktop individuare uno spazio vuoto e fare doppio clic per aprire una casella delle domande.

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

   ![](media/power-bi-visualization-card/power-bi-success2.png)
7. Selezionare **Vai al dashboard** per visualizzare il nuovo riquadro. È quindi possibile [rinominare, ridimensionare, aggiungere un collegamento ipertestuale, riposizionare il riquadro e molto altro](../service-dashboard-edit-tile.md) nel dashboard.

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- Se la casella delle domande non viene visualizzata, contattare l'amministratore tenant o di sistema.    
- Se si usa Power BI Desktop e facendo doppio clic su uno spazio vuoto in un report Domande e risposte non si apre, potrebbe essere necessario abilitare questa funzionalità.  Selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità in anteprima > Domande e risposte** e riavviare Power BI Desktop.

## <a name="format-a-card"></a>Formattare una scheda
Sono disponibili molte opzioni per la modifica di etichette, testo, colore e altri elementi. Il modo migliore per imparare a usare queste opzioni consiste nel creare una scheda e quindi esplorare il riquadro Formattazione. Di seguito sono descritte alcune delle opzioni di formattazione disponibili. 

1. Iniziare selezionando l'icona del rullo per aprire il riquadro Formattazione. 

    ![scheda con rullo evidenziato](media/power-bi-visualization-card/power-bi-format-card.png)
2. Espandere **Etichetta dati** e modificare colore, dimensioni e famiglia di caratteri. Se si dispone di migliaia di archivi, è possibile usare **Unità visualizzate** per visualizzare il numero di archivi nell'ordine delle migliaia e controllare anche le cifre decimali. Ad esempio, 125,8 migliaia anziché 125.832,00.

3.  Espandere **Etichetta categorie** e modificare colore e dimensioni.

    ![colore blu selezionato](media/power-bi-visualization-card/power-bi-card-format.png)

4. Espandere **Sfondo** e spostare il dispositivo di scorrimento su On.  È ora possibile modificare il colore di sfondo e la trasparenza.

    ![dispositivo di scorrimento impostato su ON](media/power-bi-visualization-card/power-bi-format-color.png)

5. Continuare a esplorare le opzioni di formattazione fino a quando l'aspetto della scheda corrisponde alle proprie esigenze. 

    ![Scheda dopo il completamento della formattazione](media/power-bi-visualization-card/power-bi-formatted.png)

## <a name="next-steps"></a>Passaggi successivi
[Grafici combinati in Power BI](power-bi-visualization-combo-chart.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
