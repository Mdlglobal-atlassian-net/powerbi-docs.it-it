---
title: Distribuire le app modello nell'organizzazione - Power BI
description: Informazioni sull'installazione, la personalizzazione e la distribuzione di app modello nell'organizzazione in Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 158345c44f8801a98e19dcd9b4c7dde14aa6126b
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264520"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>Installare e distribuire le app modello nell'organizzazione - Power BI

Se l'utente è un analista di Power BI, troverà utile questo articolo che illustra la procedura per installare *app modello* da connettere a molti dei servizi usati per eseguire l'attività aziendale, come ad esempio Salesforce, Microsoft Dynamics e Google Analytics. È possibile modificare dashboard e report per soddisfare le esigenze dell'organizzazione e quindi distribuirli ai colleghi come un'*app*. 

![App Power BI installate](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Se si vuole creare app modello da distribuire autonomamente, vedere [Creare un'app modello in Power BI](service-template-apps-create.md). I partner Power BI possono compilare app di Power BI con un uso minimo o nullo di codice e distribuirle ai clienti Power BI. 

## <a name="prerequisites"></a>Prerequisiti  

Di seguito sono elencati i requisiti per l'installazione, la personalizzazione e la distribuzione di un'app modello: 

- Una [licenza di Power BI Pro](service-self-service-signup-for-power-bi.md)
- Conoscenza dei [concetti di base di Power BI](service-basic-concepts.md)
- Collegamento di installazione valido dall'autore dell'app modello o da AppSource. 
- Autorizzazioni per l'installazione di app modello. 

## <a name="install-a-template-app"></a>Installare un'app modello

È possibile che si riceva un collegamento a un'app modello. In caso contrario, è possibile cercare l'app desiderata in AppSource. In entrambi i casi, dopo l'installazione, è possibile modificare l'app e distribuirla all'organizzazione.

### <a name="search-appsource-from-a-browser"></a>Cercare in AppSource da un browser

In un browser selezionare il collegamento seguente per aprire AppSource con filtro per le app di Power BI:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>Cercare in AppSource dal servizio Power BI

1. Nel riquadro di spostamento a sinistra nel servizio Power BI selezionare **App** > **Scarica app**.

    ![Scarica app](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. In AppSource selezionare **App**.

    ![Cercare in AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Sfogliare o cercare l'app e quindi selezionare **Scarica adesso**.

4. Nella finestra di dialogo selezionare **Installa**.

    ![Installare l'app](media/service-template-apps-install-distribute/power-install-dialog.png) Se si ha una licenza di Power BI Pro, l'app viene installata con l'area di lavoro per le app associata. È possibile personalizzare l'app nell'area di lavoro associata.

    Al completamento dell'installazione una notifica indica che la nuova app è pronta.
4. Selezionare **Vai all'app**.
5. In **Operazioni iniziali con la nuova app** selezionare una delle tre opzioni:

    ![Operazioni iniziali con la nuova app](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **Esplora app**: esplorazione dei dati di esempio di base. Iniziare da qui per acquisire familiarità con l'app. 
    - **Connetti dati**: modificare l'origine dati dai dati di esempio alla propria origine dati. È possibile ridefinire i parametri dei set di dati e le credenziali dell'origine dati. Vedere [Limitazioni note](service-template-apps-tips.md#known-limitations) nell'articolo dei suggerimenti sulle app modello. 
    - **Vai all'area di lavoro** (opzione più avanzata): è possibile apportare qualsiasi modifica consentita dal generatore di app.

    In alternativa, ignorare questa finestra di dialogo e accedere all'area di lavoro associata direttamente tramite **Aree di lavoro** nel riquadro di spostamento a sinistra.
    >[!NOTE]
    >L'installazione di un'app modello ha installato un'*app aziendale* e un'*area di lavoro per le app*. Altre informazioni sulla [distribuzione delle app in Power BI](service-create-distribute-apps.md).
 
6. Prima di condividere l'app con i colleghi, si vorrà connetterla ai propri dati. È anche possibile modificare il report o il dashboard per adattarlo alla propria organizzazione. A questo punto è anche possibile aggiungere altri report o dashboard.

   Se si seleziona un collegamento di installazione per un'app che non è elencata in AppSource, una finestra di dialogo di convalida richiede di confermare la selezione.

   ![Installare l'app](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >Per installare app modello che non sono elencate in AppSource è necessario richiedere le autorizzazioni di amministratore. Per informazioni dettagliate, vedere [Impostazioni app modello nel portale di amministrazione](service-admin-portal.md#template-apps-settings) di Power BI.

## <a name="update-and-distribute-the-app"></a>Aggiornare e distribuire l'app

Dopo aver aggiornato l'app per la propria organizzazione, si è pronti per pubblicarla. I passaggi sono gli stessi della pubblicazione di qualsiasi altra app.

1. Dopo aver completato la personalizzazione, nella visualizzazione elenco dell'area di lavoro selezionare **Aggiorna app** nell'angolo superiore destro.  

    ![Avviare l'installazione dell'app](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. In **Dettagli** è possibile modificare la descrizione e il colore di sfondo.

   ![Impostare la descrizione e il colore dell'app](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. In **Contenuto** è possibile selezionare una pagina di destinazione, ovvero il dashboard o il report.

   ![Impostare la pagina di destinazione dell'app](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. In **Accesso** è possibile concedere l'accesso agli utenti selezionati o all'intera organizzazione.  

   ![Impostare l'accesso all'app](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Selezionare **Aggiorna app**. 

6. Dopo la pubblicazione, è possibile copiare il collegamento e condividerlo con gli utenti cui è stato concesso l'accesso. Se l'app è stata condivisa, gli utenti visualizzano l'app anche nella scheda **Organizzazione** in AppSource.

## <a name="next-steps"></a>Passaggi successivi 

[Creare aree di lavoro con i colleghi in Power BI](service-create-workspaces.md)





￼ 

 
