---
title: Integrazione di Power BI con Microsoft Flow
description: Informazioni su come creare flussi attivati dagli avvisi per i dati di Power BI.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: dc79282a5c221e85fae7838009f6cecf91cbfdb8
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow e Power BI

[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) è un'applicazione SaaS che automatizza i flussi di lavoro nel crescente numero di applicazioni e servizi SaaS su cui si basano gli utenti aziendali. Con Flow è possibile automatizzare le attività grazie all'integrazione delle app preferite e dei servizi (incluso Power BI) per ricevere le notifiche, sincronizzare i file, raccogliere dati e altro ancora. Le attività ripetitive saranno facilitate con l'automazione del flusso di lavoro.

[Introduzione all'uso di Flow.](https://flow.microsoft.com/documentation/getting-started)

Guardare il video per scoprire come creare un flusso che invia posta dettagliata ai colleghi quando viene attivato un avviso di Power BI. Seguire quindi le istruzioni successive per sotto il video per fare una prova in prima persona.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Creare un flusso che sia attivato da un avviso per i dati di Power BI

### <a name="prerequisites"></a>Prerequisiti
Questa esercitazione illustrerà come creare due diversi flussi, uno da un modello e l'altro da zero. Per iniziare, [creare un avviso per i dati in Power BI](service-set-data-alerts.md), creare un account Slack gratuito e [iscriversi a Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup) gratuitamente.

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Creare un flusso che usa Power BI in base a un modello
In questa attività si userà un modello per creare un semplice flusso che viene attivato da un avviso (notifica) per i dati di Power BI.

1. Accedere a Microsoft Flow (flow.microsoft.com).
2. Selezionare **Flussi personali**.
   
   ![Barra dei menu di Flow](media/service-flow-integration/power-bi-my-flows.png)
3. Selezionare **Crea da modello**.
   
    ![Barra dei menu Flussi personali](media/service-flow-integration/power-bi-template.png)
4. Usare la casella di ricerca per trovare i modelli di Power BI e selezionare **Invia un messaggio di posta elettronica a tutti i destinatari quando viene attivato un avviso di Power BI basato sui dati > Continua**.
   
    ![Risultati della ricerca](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>Creare il flusso
Questo modello prevede un trigger (avviso per i dati di Power BI per le nuove medaglie olimpiche all'Irlanda) e un'azione (inviare un messaggio di posta elettronica). Quando si seleziona un campo, Flow mostra il contenuto dinamico che è possibile includere.  In questo esempio sono inclusi il valore e l'URL del riquadro nel corpo del messaggio.

![Modello di flusso](media/service-flow-integration/power-bi-template1.png)

1. Nell'elenco a discesa del trigger, selezionare un avviso per i dati di Power BI. Selezionare **New medal for Ireland**. Per informazioni su come creare un avviso, vedere [Avvisi per i dati nel servizio Power BI](service-set-data-alerts.md).
   
   ![Elenco a discesa Avviso](media/service-flow-integration/power-bi-trigger-flow.png)
2. Immettere uno o più indirizzi di posta elettronica validi, quindi selezionare **Modifica** (mostrato sotto) o **Aggiungi contenuto dinamico**. 
   
   ![Schermata Inviare un messaggio di posta elettronica](media/service-flow-integration/power-bi-flow-email.png)

3. Flow crea automaticamente un titolo e un messaggio che è possibile mantenere o modificare. Tutti i valori impostati al momento della creazione dell'avviso in Power BI sono disponibili per l'uso. È sufficiente posizionare il cursore ed effettuare una selezione nell'area grigia evidenziata. 

   ![Schermata Inviare un messaggio di posta elettronica](media/service-flow-integration/power-bi-flow-email-default.png)

1.  Ad esempio, se si crea il titolo di avviso **Abbiamo vinto un'altra medaglia** in Power BI, è possibile selezionare **Titolo avviso** per aggiungere tale testo nel campo Oggetto del messaggio di posta elettronica.

    ![Creare il testo del messaggio di posta elettronica](media/service-flow-integration/power-bi-flow-message.png)

    È anche possibile accettare il corpo del messaggio di posta elettronica predefinito o crearne uno personalizzato. L'esempio precedente contiene alcune modifiche al messaggio.

1. Al termine, selezionare **Crea flusso** o **Salva flusso**.  Il flusso viene creato e valutato.  Flow informa l'utente se vengono rilevati errori.
2. In tale evenienza, selezionare **Modifica flusso** per correggere gli errori, altrimenti selezionare **Fatto** per eseguire il nuovo flusso.
   
   ![Messaggio di operazione completata](media/service-flow-integration/power-bi-flow-running.png)
5. Quando viene attivato l'avviso dati, verrà inviato un messaggio di posta elettronica agli indirizzi indicati.  
   
   ![Messaggio di avviso](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Creare un flusso che usa Power BI da zero (vuoto)
In questa attività si creerà da zero un semplice flusso che viene attivato da un avviso (notifica) per i dati di Power BI.

1. Eseguire l'accesso a Microsoft Flow.
2. Selezionare **Flussi personali** > **Crea da zero**.
   
   ![Barra dei menu superiore di Flow](media/service-flow-integration/power-bi-my-flows.png)
3. Usare la casella di ricerca per trovare un trigger di Power BI e selezionare **Quando viene attivato un avviso di Power BI basato sui dati**.

### <a name="build-your-flow"></a>Creare il flusso
1. Nell'elenco a discesa, selezionare il nome dell'avviso.  Per informazioni su come creare un avviso, vedere [Avvisi per i dati nel servizio Power BI](service-set-data-alerts.md).
   
    ![Selezionare il nome dell'avviso](media/service-flow-integration/power-bi-totalstores2.png)
2. Selezionare **Nuovo passaggio** > **Aggiungi un'azione**.
   
   ![Aggiungere un nuovo passaggio](media/service-flow-integration/power-bi-new-step.png)
3. Cercare **Outlook** e selezionare **Crea evento**.
   
   ![Creare il flusso](media/service-flow-integration/power-bi-create-event.png)
4. Compilare i campi dell'evento. Quando si seleziona un campo, Flow mostra il contenuto dinamico che è possibile includere.
   
   ![Continuare a creare il flusso](media/service-flow-integration/power-bi-flow-event.png)
5. Selezionare **Crea flusso** al termine.  Flow salva e valuta il flusso. Se non sono presenti errori, selezionare **Fatto** per eseguire questo flusso.  Il nuovo flusso viene aggiunto alla pagina **Flussi personali**.
   
   ![Completare il flusso](media/service-flow-integration/power-bi-flow-running.png)
6. Quando il flusso viene attivato dall'avviso per i dati di Power BI, si riceverà una notifica degli eventi Outlook simile alla seguente.
   
    ![Flow attiva la notifica di Outlook](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Passaggi successivi
* [Introduzione a Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [Impostare gli avvisi per i dati nel servizio Power BI](service-set-data-alerts.md)
* [Impostare gli avvisi per i dati nell'iPhone](mobile-set-data-alerts-in-the-mobile-apps.md)
* [Impostare gli avvisi per i dati nell'app Power BI per dispositivi mobili per Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

