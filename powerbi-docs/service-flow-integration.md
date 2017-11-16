---
title: 'Esercitazione: Integrazione di Power BI con Microsoft Flow'
description: Informazioni su come creare flussi attivati dagli avvisi per i dati di Power BI.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: YhmNstC39Mw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/30/2017
ms.author: mihart
ms.openlocfilehash: 387f6bf9f9022fedf1266c32da3d61d3035e7d90
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow e Power BI
## <a name="what-is-microsoft-flow"></a>Che cos'è Microsoft Flow
[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) è un'applicazione SaaS che automatizza i flussi di lavoro nel crescente numero di applicazioni e servizi SaaS su cui si basano gli utenti aziendali. Con Flow è possibile automatizzare le attività grazie all'integrazione delle app preferite e dei servizi (incluso Power BI) per ricevere le notifiche, sincronizzare i file, raccogliere dati e altro ancora. Le attività ripetitive saranno facilitate con l'automazione del flusso di lavoro.

[Introduzione all'uso di Flow.](https://flow.microsoft.com/documentation/getting-started)

Guardare il video per scoprire come creare un flusso che invia posta dettagliata ai colleghi quando viene attivato un avviso di Power BI. Seguire quindi le istruzioni successive per sotto il video per fare una prova in prima persona.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Creare un flusso che sia attivato da un avviso per i dati di Power BI
Questa esercitazione illustrerà come creare due diversi flussi, uno da un modello e l'altro da zero. Per iniziare, [creare un avviso per i dati in Power BI](service-set-data-alerts.md) e [iscriversi a Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup) gratuitamente.

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Creare un flusso che usa Power BI in base a un modello
In questa attività si userà un modello per creare un semplice flusso che viene attivato da un avviso (notifica) per i dati di Power BI.

1. Accedere a Microsoft Flow (flow.microsoft.com).
2. Selezionare **Flussi personali**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Selezionare **Crea da modello**.
   
    ![](media/service-flow-integration/power-bi-template.png)
4. Usare la casella di ricerca per trovare i modelli di Power BI e selezionare **Post a message to a Slack channel when a Power BI data alert is triggered**.
   
    ![](media/service-flow-integration/power-bi-template2.png)
5. Selezionare **Usa questo modello**.
   
   ![](media/service-flow-integration/power-bi-use-template.png)
6. Se richiesto, connettersi a Slack e Power BI selezionando **Accedi** e quindi seguendo le istruzioni. Un segno di spunta verde indica che è stato effettuato l'accesso.  Dopo aver confermato le connessioni, selezionare **Continua**.
   
   ![](media/service-flow-integration/power-bi-flow-signin.png)

### <a name="build-the-flow"></a>Creare il flusso
Questo modello prevede un trigger (avviso per i dati di Power BI per le nuove medaglie olimpiche all'Irlanda) e un'azione (pubblicare un messaggio su Slack). Quando si seleziona un campo, Flow mostra il contenuto dinamico che è possibile includere.  In questo esempio sono inclusi il valore e l'URL del riquadro nel corpo del messaggio.

![](media/service-flow-integration/power-bi-flow-template.png)

1. Nell'elenco a discesa del trigger, selezionare un avviso per i dati di Power BI. Selezionare **New medal for Ireland**. Per informazioni su come creare un avviso, vedere [Avvisi per i dati nel servizio Power BI](service-set-data-alerts.md).
   
   ![](media/service-flow-integration/power-bi-trigger-flow.png)
2. Per pubblicare un post su Slack, immettere il nome del canale e il testo del messaggio. È anche possibile selezionare il messaggio predefinito creato da Microsoft Flow. Si noti il contenuto dinamico che è stato incluso nel campo di testo del messaggio.
   
   > [!NOTE]
   > Includere "@" all'inizio del nome del canale.  Ad esempio, se il canale Slack è denominato "channelA", in Flow immettere "@channelA".
   > 
   > 
   
   ![](media/service-flow-integration/power-bi-flow-slacker.png)
3. Al termine, selezionare **Crea flusso** o **Salva flusso**.  Il flusso viene creato e valutato.  Flow informa l'utente se vengono rilevati errori.
4. In tale evenienza, selezionare **Modifica flusso** per correggere gli errori, altrimenti selezionare **Fatto** per eseguire il nuovo flusso.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
5. Aprire l'account di Slack per visualizzare il messaggio.  
   
   ![](media/service-flow-integration/power-bi-slack-message.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Creare un flusso che usa Power BI da zero (vuoto)
In questa attività si creerà da zero un semplice flusso che viene attivato da un avviso (notifica) per i dati di Power BI.

1. Eseguire l'accesso a Microsoft Flow.
2. Selezionare **Flussi personali** > **Crea da zero**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Usare la casella di ricerca per trovare un trigger di Power BI e selezionare **Attiva un flusso con un avviso basato sui dati di Power BI**.

### <a name="build-your-flow"></a>Creare il flusso
1. Nell'elenco a discesa, selezionare il nome dell'avviso.  Per informazioni su come creare un avviso, vedere [Avvisi per i dati nel servizio Power BI](service-set-data-alerts.md).
   
    ![](media/service-flow-integration/power-bi-totalstores.png)
2. Selezionare **Nuovo passaggio** > **Aggiungi un'azione**.
   
   ![](media/service-flow-integration/power-bi-new-step.png)
3. Cercare **Outlook** e selezionare **Crea evento**.
   
   ![](media/service-flow-integration/power-bi-create-event.png)
4. Compilare i campi dell'evento. Quando si seleziona un campo, Flow mostra il contenuto dinamico che è possibile includere.
   
   ![](media/service-flow-integration/power-bi-flow-event.png)
5. Selezionare **Crea flusso** al termine.  Flow salva e valuta il flusso. Se non sono presenti errori, selezionare **Fatto** per eseguire questo flusso.  Il nuovo flusso viene aggiunto alla pagina **Flussi personali**.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
6. Quando il flusso viene attivato dall'avviso per i dati di Power BI, si riceverà una notifica degli eventi Outlook simile alla seguente.
   
    ![](media/service-flow-integration/power-bi-flow-notice.png)

### <a name="next-steps"></a>Passaggi successivi
* [Introduzione a Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [Impostare gli avvisi per i dati nel servizio Power BI](service-set-data-alerts.md)
* [Impostare gli avvisi per i dati nell'iPhone](mobile-set-data-alerts-in-the-mobile-apps.md)
* [Impostare gli avvisi per i dati nell'app Power BI per dispositivi mobili per Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md)
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

