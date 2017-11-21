---
title: Introduzione al servizio Power BI
description: Introduzione al servizio Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/31/2017
ms.author: mihart
ms.openlocfilehash: 6714283ea4590ac9c2f3728121e05d03d4aa646e
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-power-bi-service"></a>Introduzione al servizio Power BI
Questa esercitazione illustra come iniziare a usare il ***servizio Power BI***. Per comprendere come si colloca il servizio Power BI rispetto alle altre offerte Power BI, è consigliabile leggere prima di tutto [Che cos'è Power BI](guided-learning/gettingstarted.yml#step-1).

![](media/service-get-started/power-bi-components.png)

Il servizio Power BI offre una versione gratuita e una versione Pro. Indipendentemente dalla versione in uso, aprire un browser e digitare www.powerbi.com per iniziare. Se si è già iscritti, selezionare il collegamento **Accedi** visualizzato nell'angolo in alto a destra. Se non si è ancora iscritti al servizio Power BI, selezionare invece il collegamento **Iscrizione gratuita**.

![](media/service-get-started/power-bi-sign-up.png)

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

Se sono presenti dati importanti in file Excel o CSV, è possibile creare un dashboard di Power BI per rimanere sempre aggiornati e condividere informazioni dettagliate con altre persone.  Coloro che hanno una sottoscrizione a un'applicazione SaaS come Salesforce  si avvantaggeranno [connettendosi a Salesforce](service-connect-to-salesforce.md) per creare automaticamente un dashboard in base a tali dati oppure possono [dare un'occhiata a tutte le altre applicazioni SaaS](service-get-data.md) a cui è possibile connettersi. Se si fa parte di un'organizzazione, verificare la disponibilità di eventuali [app](service-create-distribute-apps.md) pubblicate automaticamente.

Altre informazioni su tutti gli altri modi per [recuperare dati per Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Passaggio 1: Recuperare i dati
Di seguito è riportato un esempio di recupero di dati da un file CSV. Per seguire questa esercitazione, [scaricare questo file CSV di esempio](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Accedere a Power BI](http://www.powerbi.com/). Non si ha un account? Nessun problema: è possibile iscriversi gratuitamente.
2. Power BI viene aperto nel browser. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-get-started/getdata3.png)
3. Selezionare **File**. 
   
   ![](media/service-get-started/gs1.png)
4. Selezionare **File locale**, selezionare il file sul computer, quindi scegliere **Apri**.
   
   ![](media/service-get-started/gs2.png)
5. Per questa esercitazione verrà selezionato **Importa** per aggiungere il file di Excel come set di dati da usare successivamente per creare report e dashboard.  
   
   > [!NOTE]
   > Se si seleziona **Carica**, l'intera cartella di lavoro di Excel verrà caricata in Power BI, da cui potrà essere aperta e modificata in Excel Online.
   > 
   > 
   
   ![](media/service-get-started/power-bi-import.png)
6. Quando il set di dati è pronto, selezionare **Visualizza set di dati** per aprirlo nell'editor di report. ![](media/service-get-started/power-bi-gs.png).
   
   > [!TIP]
   > Per acquisire familiarità con l'editor di report, è possibile [visualizzare la presentazione](service-the-report-editor-take-a-tour.md)
   > 
   > 

## <a name="step-2-start-exploring-your-dataset"></a>Passaggio 2: Iniziare a esplorare il set di dati
Dopo avere stabilito la connessione ai dati, esplorare per trovare approfondimenti.  Dopo aver trovato un elemento da monitorare, è possibile creare un dashboard per mantenersi aggiornati sulle modifiche.

1. Selezionare l'immagine del set di dati nel dashboard per esplorare i dati a cui ci si è appena connessi o, sotto l'intestazione **Set di dati**, selezionare il nome del set di dati per aprirlo. Il set di dati verrà visualizzato come un report vuoto.
   
   ![](media/service-get-started/power-bi-report-editor.png)
   
   > [!NOTE]
> Si può esplorare i dati anche con **Informazioni rapide**.  Per altre informazioni, vedere [Introduzione a Informazioni rapide](service-insights.md).
   > 
   > 
2. Nell'elenco **Campi** sul lato destro della pagina, selezionare i campi per creare una visualizzazione.  Selezionare la casella di controllo accanto a **Gross Sales** e **Date**.
   
   ![](media/service-get-started/fields.png)
3. Power BI analizza i dati e crea un oggetto visivo.  Se prima si è selezionato **Date** verrà visualizzata una tabella.  Se prima si è selezionato **Gross Sales** verrà visualizzato un grafico. Cambiare la modalità di visualizzazione dei dati. Provare a passare a un grafico a linee selezionando l'opzione del grafico a linee.
   
   ![](media/service-get-started/gettingstart5new.png)
4. Quando nel dashboard compare la visualizzazione desiderata, passare il puntatore su di essa e selezionare l'icona **Aggiungi**.  Quando si aggiunge questa visualizzazione, verrà archiviata nel dashboard in modo che sia possibile tenere traccia dell'ultimo valore in modo immediato.
   
   ![](media/service-get-started/pinnew.png)
5. Dal momento che si tratta di un nuovo report, è necessario salvarlo prima di poter aggiungere una visualizzazione da quest'ultimo al dashboard. Assegnare un nome al report (ad esempio, *Vendite nel tempo*) e selezionare **Salva e continua**. 
   
   ![](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
   Il nuovo report viene visualizzato nel riquadro di spostamento sotto all'intestazione **Report**.
6. Aggiungere il riquadro a un dashboard esistente o a un nuovo dashboard. 
   
   ![](media/service-get-started/power-bi-pin.png)
   
   * **Dashboard esistente**: selezionare il nome del dashboard nell'elenco a discesa.
   * **Nuovo dashboard**: digitare il nome del nuovo dashboard.
7. Selezionare **Aggiungi**.
   
   Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che è stata aggiunta la visualizzazione, come riquadro, al dashboard.
   
   ![](media/service-get-started/power-bi-pin-success.png)
8. Selezionare **Vai al dashboard** per visualizzare il nuovo dashboard con il riquadro bloccato. Il grafico a linee è bloccato, sotto forma di riquadro, al dashboard. Migliorare il dashboard [rinominando, ridimensionando, collegando e riposizionando i riquadri](service-dashboard-edit-tile.md).
   
   ![](media/service-get-started/power-bi-new-dashboard.png)
   
   Selezionare il nuovo riquadro nel dashboard per tornare al report in qualsiasi momento.

## <a name="step-3-continue-exploring-with-qa-natural-language-querying"></a>Passaggio 3: Continuare l'esplorazione con Domande e risposte (query in linguaggio naturale)
1. Per l'esplorazione rapida dei dati, provare a formulare una domanda nella finestra Domande e risposte. La casella Domande e risposte si trova nella parte superiore del dashboard. Ad esempio, provare a digitare "**quale segmento ha prodotto il massimo profitto**".
   
   ![](media/service-get-started/powerbi-qna.png)
2. Fare clic sull'icona Aggiungi ![](media/service-get-started/pbi_pinicon.png) per mostrare anche questa visualizzazione nel dashboard.
3. Aggiungere la visualizzazione al dashboard di esempio finanziario.
   
    ![](media/service-get-started/power-bi-pin2.png)
4. Selezionare la freccia Indietro relativa a **Chiudi Domande e risposte** ![](media/service-get-started/pbi_qabackarrow.png) per tornare al dashboard dove verrà visualizzato il nuovo riquadro.

## <a name="next-steps"></a>Passaggi successivi
Per approfondire ulteriormente l'argomento,  consultare i seguenti articoli.

* [Connettersi a un altro set di dati](service-get-data.md).
* [Condividere il dashboard](service-share-dashboards.md) con i colleghi.
* Leggere i [suggerimenti per la progettazione dei dashboard](service-dashboards-design-tips.md).
* Visualizzare i dashboard con un'[app di Power BI in un dispositivo mobile](mobile-apps-for-mobile-devices.md).

Se non si è ancora pronti a usarlo, iniziare con questi argomenti che consentono di familiarizzare con Power BI.

* [Informazioni sull'interazione tra report, set di dati, dashboard e riquadri](service-basic-concepts.md)
* [Video di Power BI](videos.md)
* [Vedere quali esempi sono disponibili](sample-datasets.md)

### <a name="stay-in-touch-with-power-bi"></a>Restare in contatto con Power BI
* Seguire [@MSPowerBI su Twitter](https://twitter.com/mspowerbi)
* Iscriversi al nostro [canale video di YouTube](https://www.youtube.com/channel/UCy--PYvwBwAeuYaR8JLmrfg)
* Guardare i [webinar di introduzione a Power BI](webinars.md) su richiesta
* Non si è sicuri su dove chiedere assistenza? Vedere la pagina [10 suggerimenti per chiedere assistenza](service-tips-for-finding-help.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

