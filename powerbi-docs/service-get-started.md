---
title: Introduzione al servizio Power BI
description: Introduzione al servizio Power BI
author: adamw
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: d66653ebe9232cb6da2f3c53b01e791ca9966db9
ms.sourcegitcommit: dcde910817720c05880ffe24755034f916c9b890
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
---
# <a name="get-started-with-power-bi-service-apppowerbicom"></a>Introduzione al servizio Power BI (app.powerbi.com)
Questa esercitazione illustra come iniziare a usare il ***servizio Power BI***. Per comprendere come si colloca il servizio Power BI rispetto alle altre offerte Power BI, è consigliabile leggere prima di tutto [Che cos'è Power BI](guided-learning/gettingstarted.yml?tutorial-step=1).

![Immagine che illustra la relazione tra Desktop, servizio, dispositivi mobili](media/service-get-started/power-bi-components.png)

Il servizio Power BI offre una versione gratuita e una versione Pro. Indipendentemente dalle versione in uso, *se si ha già un account*, per accedere al servizio Power BI, aprire un browser e digitare app.powerbi.com. Per i nuovi utenti, è consigliabile iniziare da www.powerbi.com. Da qui sarà possibile ottenere informazioni su Power BI prima di accedere al servizio.  Per provare il servizio, selezionare il collegamento **Iscriviti gratuitamente** nell'angolo in alto a destra. Se invece l'amministratore ha già abilitato Power BI, non usare il pulsante Iscriviti gratuitamente, ma passare direttamente all'indirizzo app.powerbi.com. 

![Accedere o iscriversi gratuitamente](media/service-get-started/power-bi-sign-up.png)

Per informazioni su Power BI Desktop, vedere [Introduzione a Power BI Desktop](desktop-getting-started.md). Per informazioni su Power BI per dispositivi mobili, vedere [App Power BI per dispositivi mobili](mobile-apps-for-mobile-devices.md).

> [!TIP]
> Se si preferisce un corso di formazione gratuito per l'autoapprendimento, [iscriversi al corso Analyzing and Visualizing Data su EdX](http://aka.ms/edxpbi) (Analisi e visualizzazione dei dati).

Visitare la nostra [playlist su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). Un buon video da cui iniziare è Introduzione al servizio Power BI:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 
> 
> 

Microsoft Power BI consente di rimanere aggiornati sulle informazioni a cui si è interessati.  Con il servizio Power BI, i ***dashboard*** aiutano a tenere sotto controllo l'andamento dell'attività.  I dashboard mostrano ***riquadri*** su cui è possibile fare clic per aprire i ***report*** e ottenere informazioni ancora più dettagliate.  È possibile connettersi a più ***set di dati*** per visualizzare tutti i dati rilevanti insieme in un'unica posizione. Per saperne di più sui componenti essenziali di Power BI,  vedere [Power BI - Concetti di base](service-basic-concepts.md).

Se sono presenti dati importanti in file Excel o CSV, è possibile creare un dashboard di Power BI per rimanere sempre aggiornati e condividere informazioni dettagliate con altre persone.  Coloro che hanno una sottoscrizione a un'applicazione SaaS come Salesforce  si avvantaggeranno connettendosi a Salesforce per creare automaticamente un dashboard in base a tali dati o [dare un'occhiata a tutte le altre applicazioni SaaS](service-get-data.md) a cui è possibile connettersi. Se si fa parte di un'organizzazione, verificare la disponibilità di eventuali [app](service-create-distribute-apps.md) pubblicate automaticamente.

Altre informazioni su tutti gli altri modi per [recuperare dati per Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Passaggio 1: Recuperare i dati
Di seguito è riportato un esempio di recupero di dati da un file CSV. Per seguire questa esercitazione, [scaricare questo file CSV di esempio](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Accedere a Power BI](http://www.powerbi.com/). Non si ha un account? Nessun problema: è possibile iscriversi gratuitamente.
2. Power BI viene aperto nel browser. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![Recuperare i dati](media/service-get-started/getdata3.png)
3. Selezionare **File**. 
   
   ![Ottenere i file](media/service-get-started/gs1.png)
4. Selezionare il file nel computer e scegliere **Apri**. Se il file è stato salvato in OneDrive for Business, selezionare l'opzione corrispondente. Se il file è stato salvato in locale, selezionare **File locale**. 
   
   ![Schermata Recupera dati > File](media/service-get-started/gs2.png)
5. Per questa esercitazione verrà selezionato **Importa** per aggiungere il file di Excel come set di dati da usare successivamente per creare report e dashboard. Se si seleziona **Carica**, l'intera cartella di lavoro di Excel verrà caricata in Power BI, da cui potrà essere aperta e modificata in Excel Online.
   
   ![Scegliere Importa](media/service-get-started/power-bi-import.png)
6. Quando il set di dati è pronto, selezionare **Visualizza set di dati** per aprirlo nell'editor di report. 

    ![Finestra di dialogo Il set di dati è pronto](media/service-get-started/power-bi-gs.png)

    Poiché non sono state ancora create visualizzazioni, l'area di disegno del report sarà vuota.

    ![Area di disegno report vuota](media/service-get-started/power-bi-report-editor.png)

6. Osservare la barra dei menu superiore e notare l'opzione per la **Visualizzazione di lettura**. Dal momento che è disponibile l'opzione per la Visualizzazione di lettura, significa che la modalità corrente è la **Visualizzazione di modifica**. 

    ![Opzione Visualizzazione di lettura](media/service-get-started/power-bi-editing-view.png)

    Nella Visualizzazione di modifica è possibile creare e modificare i report perché l'utente è il *proprietario* del report, ovvero un *autore*. Quando si condivide un report con i colleghi, questi ultimi potranno interagire con il report esclusivamente nella Visualizzazione di lettura, perché sono *consumer*. Altre informazioni sulla [Visualizzazione di lettura e sulla Visualizzazione di modifica](service-reading-view-and-editing-view.md).
    
    Per acquisire familiarità con l'editor di report, è possibile [visualizzare la presentazione](service-the-report-editor-take-a-tour.md)
   > 
 

## <a name="step-2-start-exploring-your-dataset"></a>Passaggio 2: Iniziare a esplorare il set di dati
Ora che si è connessi ai dati, è possibile iniziare l'esplorazione.  Se si trovano elementi interessanti, si può creare un dashboard per monitorarli e visualizzarne le variazioni nel tempo. Ecco come funziona.
    
1. Nell'editor di report verrà usato il riquadro **Campi** sul lato destro della pagina per creare una visualizzazione.  Selezionare la casella di controllo accanto a **Gross Sales** e **Date**.
   
   ![Elenco di campi](media/service-get-started/fields.png)

2. Power BI analizza i dati e crea una visualizzazione.  Se prima si è selezionato **Date** verrà visualizzata una tabella.  Se prima si è selezionato **Gross Sales** verrà visualizzato un grafico. Cambiare la modalità di visualizzazione dei dati. È possibile visualizzare i dati sotto forma di grafico a linee. Nel riquadro **Visualizzazioni** selezionare l'icona del grafico a linee, nota anche come modello.
   
   ![Editor di report con icona selezionata](media/service-get-started/gettingstart5new.png)

3. Sembra interessante, quindi la *aggiungeremo* a un dashboard. Passare il puntatore del mouse sulla visualizzazione, quindi selezionare l'icona **Aggiungi**.  Quando si aggiunge una visualizzazione, verrà archiviata nel dashboard e aggiornata automaticamente in modo che sia possibile tenere traccia dell'ultimo valore in modo immediato.
   
   ![Icona Aggiungi](media/service-get-started/pinnew.png)

5. Dal momento che si tratta di un nuovo report, è necessario salvarlo prima di poter aggiungere una visualizzazione a un dashboard. Assegnare un nome al report, ad esempio *Sales over time*, e selezionare **Salva e continua**. 
   
   ![Finestra di dialogo Salva report con nome](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
6. Aggiungere il grafico a linee al nuovo dashboard e assegnargli il nome "Financial sample for tutorial". 
   
   ![Assegnare un nome al report](media/service-get-started/power-bi-pin.png)
   
 1. Selezionare **Aggiungi**.
   
    Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che è stata aggiunta la visualizzazione, come riquadro, al dashboard.
   
    ![Finestra di dialogo Aggiunto al dashboard](media/service-get-started/power-bi-pin-success.png)

8. Selezionare **Vai al dashboard** per visualizzare il grafico a linee aggiunto, sotto forma di riquadro, al nuovo dashboard appena creato. Migliorare il dashboard aggiungendo altri riquadri di visualizzazione e [rinominando, ridimensionando, collegando e riposizionando i riquadri](service-dashboard-edit-tile.md).
   
   ![Dashboard con visualizzazione aggiunta](media/service-get-started/power-bi-new-dashboard.png)
   
   Selezionare il nuovo riquadro nel dashboard per tornare al report in qualsiasi momento. Power BI reindirizzerà l'utente all'editor di report in Visualizzazione di lettura. Per tornare alla Visualizzazione di modifica, selezionare **Modifica report** nella barra dei menu superiore. Nella Visualizzazione di modifica è possibile continuare a esplorare e ad aggiungere riquadri. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Passaggio 3: Continuare l'esplorazione con Domande e risposte (query in linguaggio naturale)
1. Per l'esplorazione rapida dei dati, provare a formulare una domanda nella finestra Domande e risposte. La casella delle domande di Domande e risposte si trova nella parte superiore del dashboard (**Porre una domanda sui dati**) e nella barra dei menu superiore del report (**Poni una domanda**). Ad esempio, provare a digitare "quale segmento ha generato il massimo profitto".
   
   ![Area di disegno Domande e risposte](media/service-get-started/powerbi-qna.png)

2. Domande e risposte cerca una risposta e la presenta sotto forma di visualizzazione. Selezionare l'icona Aggiungi ![Icona Aggiungi](media/service-get-started/pbi_pinicon.png) per mostrare anche questa visualizzazione nel dashboard.
3. Aggiungere la visualizzazione al dashboard "Financial Sample for tutorial".
   
    ![Finestra di dialogo Aggiungi al dashboard](media/service-get-started/power-bi-pin2.png)

4. Tornare al dashboard dove verrà visualizzato il nuovo riquadro.

   ![Dashboard con grafico aggiunto](media/service-get-started/power-bi-final-dashboard.png)

## <a name="next-steps"></a>Passaggi successivi
Per approfondire ulteriormente l'argomento,  consultare gli articoli seguenti.

* [Connettersi a un altro set di dati](service-get-data.md).
* [Condividere il dashboard](service-share-dashboards.md) con i colleghi.
* Leggere i [suggerimenti per la progettazione dei dashboard](service-dashboards-design-tips.md).
* Visualizzare i dashboard con un'[app di Power BI in un dispositivo mobile](mobile-apps-for-mobile-devices.md).

Se non si è ancora pronti a usarlo, iniziare con questi argomenti che consentono di familiarizzare con Power BI.

* [Informazioni sull'interazione tra report, set di dati, dashboard e riquadri](service-basic-concepts.md)
* Visitare il sito [Apprendimento guidato di Power BI](guided-learning/index.md) e svolgere alcuni (brevi) corsi
* Guardare alcuni [video di Power BI](videos.md)
* [Vedere quali esempi sono disponibili](sample-datasets.md)

### <a name="stay-in-touch-with-power-bi"></a>Restare in contatto con Power BI
* Seguire [@MSPowerBI su Twitter](https://twitter.com/mspowerbi)
* Iscriversi al nostro [canale video di YouTube](https://www.youtube.com/channel/UCy--PYvwBwAeuYaR8JLmrfg)
* Guardare i [webinar di introduzione a Power BI](webinars.md) su richiesta
* Non si è sicuri su dove chiedere assistenza? Vedere la pagina [10 suggerimenti per chiedere assistenza](service-tips-for-finding-help.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

