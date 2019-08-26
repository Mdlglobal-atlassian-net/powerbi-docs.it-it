---
title: Introduzione al servizio Power BI
description: Introduzione al servizio Power BI online (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 007819ead82f558efa8179a49dfba9454558dfbb
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995180"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>Esercitazione: Introduzione al servizio Power BI (app.powerbi.com)
Questa esercitazione illustra come iniziare a usare il *servizio Power BI*. Per comprendere come si posiziona il servizio Power BI rispetto alle altre offerte Power BI, è prima di tutto consigliabile leggere [Che cos'è Power BI](power-bi-overview.md).

![Relazione tra Power BI Desktop, il servizio Power BI e Power BI per dispositivi mobili](media/service-get-started/power-bi-components.png)

In questa esercitazione viene completata la procedura seguente:

> [!div class="checklist"]
> * Trovare contenuti introduttivi per il servizio Power BI.
> * Accedere all'account Power BI online o iscriversi se non si ha ancora un account.
> * Aprire il servizio Power BI.
> * Ottenere alcuni dati e aprirli in visualizzazione report.
> * Usare tali dati per creare visualizzazioni e salvarli come report.
> * Creare un dashboard aggiungendo i riquadri dai report.
> * Aggiungere un'altra visualizzazione al dashboard usando lo strumento di linguaggio naturale Domande e risposte.
> * Pulire le risorse eliminando il set di dati, il report e il dashboard.

## <a name="sign-up-for-the-power-bi-service"></a>Iscriversi al servizio Power BI
Se non si ha un account Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

Dopo aver creato un account, immettere *app.powerbi.com* nel browser per aprire il servizio Power BI. 

Per informazioni su Power BI Desktop, vedere [Introduzione a Power BI Desktop](desktop-getting-started.md). Per informazioni su Power BI per dispositivi mobili, vedere [App Power BI per dispositivi mobili](consumer/mobile/mobile-apps-for-mobile-devices.md).

> [!TIP]
> Se si preferisce un corso di formazione gratuito per l'autoapprendimento, [iscriversi al corso Analyzing and Visualizing Data su EdX](http://aka.ms/edxpbi) (Analisi e visualizzazione dei dati).

Visitare la nostra [playlist su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). Un buon video da cui iniziare è *Introduzione al servizio Power BI*:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>Che cos'è il servizio Power BI?
Il servizio Microsoft Power BI è talvolta denominato Power BI online o app.powerbi.com. Power BI consente di rimanere aggiornati sulle informazioni a cui si è interessati. Nel servizio Power BI i *dashboard* aiutano a tenere sotto controllo l'andamento dell'attività. I dashboard mostrano *riquadri* che è possibile selezionare per aprire i *report* e ottenere informazioni ancora più dettagliate. È possibile connettersi a più *set di dati* per visualizzare tutti i dati rilevanti insieme in un'unica posizione. Per saperne di più sui componenti essenziali di Power BI, Vedere [Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md).

Se sono presenti dati importanti in file Excel o CSV, è possibile creare un dashboard di Power BI per rimanere sempre aggiornati e condividere informazioni dettagliate con altre persone.  Coloro che hanno una sottoscrizione a un'applicazione SaaS come Salesforce  si avvantaggeranno connettendosi a Salesforce per creare automaticamente un dashboard in base a tali dati o [dare un'occhiata a tutte le altre applicazioni SaaS](service-get-data.md) a cui è possibile connettersi. Se si fa parte di un'organizzazione, verificare la disponibilità di eventuali [app](service-create-distribute-apps.md) pubblicate automaticamente.

Altre informazioni su tutti gli altri modi per [recuperare dati per Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Passaggio 1: Recupera dati
Di seguito è riportato un esempio di recupero di dati da un file CSV. Per seguire questa esercitazione, [Scaricare il file CSV di esempio Financial](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Accedere a Power BI](http://www.powerbi.com/). Non si ha un account? Nessun problema: è possibile iscriversi a una versione di prova gratuita.
2. Power BI viene aperto nel browser. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.

    Verrà aperta la pagina **Recupera dati**.   

3. Nella sezione **Creare nuovo contenuto** selezionare **File**. 
   
   ![Ottenere i file](media/service-get-started/gs1.png)
4.  Selezionare **File locale**.
   
     ![Schermata Recupera dati > File](media/service-get-started/gs2.png)

5. Selezionare il file nel computer e scegliere **Apri**.

5. Per questa esercitazione verrà selezionato **Importa** per aggiungere il file di Excel come set di dati da usare successivamente per creare report e dashboard. Se si seleziona **Carica**, l'intera cartella di lavoro di Excel verrà caricata in Power BI, da cui potrà essere aperta e modificata in Excel Online.
   
   ![Scegliere Importa](media/service-get-started/power-bi-import.png)
6. Quando il set di dati è pronto, selezionare **Visualizza set di dati** per aprirlo nell'editor di report. 

    ![Finestra di dialogo Il set di dati è pronto](media/service-get-started/power-bi-gs.png)

    Poiché non sono state ancora create visualizzazioni, il canvas del report è vuoto.

    ![Canvas del report vuoto](media/service-get-started/power-bi-report-editor.png)

7. Si noti l'opzione **Visualizzazione di lettura** sulla barra di spostamento superiore. Se questa opzione è visualizzata, significa che si sta usando la visualizzazione di modifica. 

    ![Opzione Visualizzazione di lettura](media/service-get-started/power-bi-editing-view.png)

    Nella visualizzazione di modifica è possibile creare e modificare i report, perché l'utente è il *proprietario* del report. Vale a dire che ne è l'*autore*. Quando si condivide un report con i colleghi, questi ultimi possono interagire con il report esclusivamente nella visualizzazione di lettura, perché sono *consumer*. Altre informazioni sulla [Visualizzazione di lettura e sulla Visualizzazione di modifica](consumer/end-user-reading-view.md).
    
    Per acquisire familiarità con l'editor di report, è possibile [visualizzare la presentazione](service-the-report-editor-take-a-tour.md).
 

## <a name="step-2-start-exploring-your-dataset"></a>Passaggio 2: Iniziare a esplorare il set di dati
Ora che si è connessi ai dati, è possibile iniziare l'esplorazione.  Se si trovano elementi interessanti, si può creare un dashboard per monitorarli e visualizzarne le variazioni nel tempo. Ecco come funziona.
    
1. Nell'editor di report verrà usato il riquadro **Campi** sul lato destro della pagina per creare una visualizzazione. Selezionare le caselle di controllo **Gross Sales** e **Date**.
   
   ![Elenco di campi](media/service-get-started/fields.png)

    Power BI analizza i dati e crea una visualizzazione. Se prima si è selezionato **Date**, viene visualizzata una tabella. Se prima si è selezionato **Gross Sales** viene visualizzato un grafico. 

2. Cambiare la modalità di visualizzazione dei dati. È possibile visualizzare i dati sotto forma di grafico a linee. Selezionare l'icona del grafico a linee dal riquadro **Visualizzazioni**.
   
   ![Editor di report con il grafico a linee selezionato](media/service-get-started/gettingstart5new.png)

3. Il grafico sembra interessante, quindi lo si *aggiungerà* a un dashboard. Passare il puntatore del mouse sulla visualizzazione, quindi selezionare l'icona Aggiungi. Quando si aggiunge una visualizzazione, verrà archiviata nel dashboard e aggiornata automaticamente in modo che sia possibile tenere traccia dell'ultimo valore in modo immediato.
   
   ![Icona Aggiungi](media/service-get-started/pinnew.png)

4. Dato che il report è nuovo, è necessario salvarlo prima di poter aggiungere una visualizzazione a un dashboard. Assegnare un nome al report, ad esempio *Sales over time* e quindi selezionare **Salva e continua**. 
   
   ![Finestra di dialogo Salva report con nome](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. Aggiungere il grafico a linee a un nuovo dashboard e assegnargli il nome *Financial sample for tutorial*. 
   
   ![Assegnare un nome al report](media/service-get-started/power-bi-pin.png)
   
6. Selezionare **Aggiungi**.
   
    Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che la visualizzazione è stata aggiunta come riquadro al dashboard.
   
    ![Finestra di dialogo Aggiunto al dashboard](media/service-get-started/power-bi-pin-success.png)

7. Selezionare **Vai al dashboard** per visualizzare il grafico a linee aggiunto sotto forma di riquadro al nuovo dashboard. Migliorare il dashboard aggiungendo altri riquadri di visualizzazione e [rinominando, ridimensionando, collegando e riposizionando i riquadri](service-dashboard-edit-tile.md).
   
   ![Dashboard con visualizzazione aggiunta](media/service-get-started/power-bi-new-dashboard.png)
   
8. Selezionare il nuovo riquadro nel dashboard per tornare al report. Power BI reindirizzerà l'utente all'editor di report in Visualizzazione di lettura. Per tornare alla visualizzazione di modifica, selezionare **Modifica report** nella barra di spostamento. Una volta tornati nella visualizzazione di modifica, è possibile continuare a esplorare e ad aggiungere i riquadri. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Passaggio 3:  Continuare l'esplorazione con Domande e risposte (query in linguaggio naturale)
1. Per l'esplorazione rapida dei dati, formulare una domanda nella finestra Domande e risposte. La casella delle domande di Domande e risposte si trova nella parte superiore del dashboard (**Porre una domanda sui dati**) e nella barra di spostamento superiore del report (**Poni una domanda**). Digitare, ad esempio, *quale segmento ha generato il massimo profitto* nella casella Domande e risposte.
   
   ![Area di disegno Domande e risposte](media/service-get-started/powerbi-qna.png)

2. Domande e risposte cerca una risposta e la presenta sotto forma di visualizzazione. Selezionare l'icona Aggiungi ![Icona Aggiungi](media/service-get-started/pbi_pinicon.png) per mostrare questa visualizzazione nel dashboard.
3. Aggiungere la visualizzazione al dashboard **Financial Sample for tutorial**.
   
    ![Finestra di dialogo Aggiungi al dashboard](media/service-get-started/power-bi-pin2.png)

4. Tornare al dashboard, dove viene visualizzato il nuovo riquadro.

   ![Dashboard con grafico aggiunto](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>Pulire le risorse
Dopo aver completo l'esercitazione, è possibile eliminare il set di dati, il report e il dashboard. 

1. Selezionare **Area di lavoro** dal riquadro di spostamento a sinistra.
2. Selezionare la scheda **Set di dati** e individuare il set di dati che è stato importato per questa esercitazione.  
3. Selezionare i puntini di sospensione (...) > **Elimina**.

    ![Eliminare il set di dati](media/service-get-started/power-bi-delete.jpg)

    Quando si elimina il set di dati, Power BI elimina anche il report e il dashboard. 


## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Connettersi ai servizi online usati con Power BI](service-connect-to-services.md)

