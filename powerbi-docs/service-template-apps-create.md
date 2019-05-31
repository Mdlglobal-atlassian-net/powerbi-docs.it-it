---
title: Creare app modello in Power BI (anteprima)
description: Come creare in Power BI app modello distribuibili a tutti i clienti Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: maggies
ms.openlocfilehash: 653050fbe5c860ef1902a4700c3a70a8af2f7092
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514977"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Creare un'app modello in Power BI (anteprima)

Le nuove *app modello* di Power BI consentono ai partner Power BI di creare app Power BI con un uso minimo o nullo di codice e quindi di distribuire le app a qualsiasi cliente Power BI.  Questo articolo contiene istruzioni dettagliate per la creazione di un'app modello di Power BI.

Se è possibile creare dashboard e report di Power BI, può diventare una *generatore di app modello* e compila e Impacchetta contenuti analitici in un *app*. È possibile distribuire l'app ad altri tenant di Power BI tramite qualsiasi piattaforma disponibile, ad esempio AppSource o utilizzandolo in un proprio servizio web. Come generatore si ha la possibilità per creare un pacchetto protetto analitica per la distribuzione.

Gli amministratori tenant di Power BI determinano quali utenti dell'organizzazione sono autorizzati a creare app modello e quali utenti possono installare tali app. Gli utenti che sono autorizzati possono installare l'app di modello, quindi modificarla e distribuirla agli utenti di Power BI all'interno dell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

I requisiti per la creazione di un'app modello sono i seguenti:  

- Una [licenza di Power BI Pro](service-self-service-signup-for-power-bi.md)
- Un'[installazione di Power BI Desktop](desktop-get-the-desktop.md) (facoltativa)
- Familiarità con la [concetti di base di Power BI](service-basic-concepts.md)
- Autorizzazioni per la creazione di un'app modello. Per informazioni dettagliate, vedere [Impostazioni app modello nel portale dell'amministratore](service-admin-portal.md#template-apps-settings-preview) di Power BI.

## <a name="enable-app-developer-mode"></a>Abilitare la modalità di sviluppo app

Per creare un'app distribuibile ad altri tenant di Power BI è necessario aver attivato la modalità di sviluppo app. In caso contrario si crea semplicemente un'app per utenti di Power BI nell'organizzazione di appartenenza.

1. Aprire il servizio Power BI in un browser.
2. Passare a **Impostazioni** > **Generali** > **Sviluppatore** > **Abilita modalità di sviluppo app modello**.

    ![Abilitare le app modello](media/service-template-apps-create/power-bi-dev-template-app.png)

    Se l'opzione non è visibile, contattare l'amministratore di Power BI per ottenere le [autorizzazioni per lo sviluppo di app modello](service-admin-portal.md#template-apps-settings-preview) nel portale di amministrazione.

3. Selezionare **Applica**.

## <a name="create-the-template-app-workspace"></a>Creare l'area di lavoro app modello

Per creare un'app distribuibile ad altri tenant di Power BI è necessario crearla in una delle nuove aree di lavoro per le app.

1. Nel servizio Power BI selezionare **Aree di lavoro** > **Crea area di lavoro per le app**.

    ![Crea area di lavoro per le app](media/service-template-apps-create/power-bi-new-workspace.png)

2. In **Crea area di lavoro per le app** in **Anteprima aree di lavoro migliorate** selezionare **Prova adesso**.

    ![Provare le nuove aree di lavoro](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

3. Immettere il nome, la descrizione (facoltativa) e l'immagine del logo (facoltativa) dell'area di lavoro per le app.

4. Selezionare **Sviluppa un'app modello**.

    ![Sviluppare un'app modello](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Selezionare **Salva**.
>[!NOTE]
>L'amministratore di Power BI per alzare di livello App modello sono necessarie autorizzazioni.

## <a name="create-the-content-in-your-template-app"></a>Creare il contenuto nell'app modello

Come in qualsiasi area di lavoro per le app di Power BI, il passaggio successivo è la creazione del contenuto nell'area di lavoro.  In questa versione di anteprima delle app modello è supportato un solo elemento di ogni tipo: un solo set di dati, un solo report e un solo dashboard.

- [Creare il contenuto di Power BI](power-bi-creator-landing.md) nell'area di lavoro per le app.

Se si usano parametri in Power Query, assicurarsi che abbiano un tipo ben definito (ad esempio Testo). I tipi Qualsiasi e Binario non sono supportati.

[Suggerimenti per la creazione di app modello in Power BI (anteprima)](service-template-apps-tips.md) include suggerimenti utili per la creazione di report e dashboard per l'app modello.

## <a name="create-the-test-template-app"></a>Creare l'app modello di test

Ora che l'area di lavoro include contenuto, è possibile integrare tale contenuto in un'app modello. Il primo passaggio è la creazione di un'app modello di test, accessibile solo dall'interno dell'organizzazione nel tenant.

1. Nell'area di lavoro delle app modello selezionare **Crea app**.

    ![Crea app](media/service-template-apps-create/power-bi-create-app.png)

    In questo caso, riempire nelle opzioni di compilazione aggiuntivi per l'app di modello, in cinque categorie:

    **Personalizzazione**

    ![Personalizzazione](media/service-template-apps-create/power-bi-create-branding.png)
    - Nome dell'app
    - Descrizione
    - Sito del supporto tecnico (collegamento viene presentato sotto info app dopo la ridistribuzione di modello app come app per l'organizzazione)
    - Logo dell'App (dimensione massima dei file 45 KB, proporzioni 1:1, i formati JPEG. jpg. PNG)
    - Colore del tema App

    **Contenuto**

    **Pagina di destinazione di App:** Definire un report o dashboard in cui eseguire la pagina di destinazione dell'app, usare una pagina di destinazione che fornirà l'impressione di destra:

    ![Contenuto](media/service-template-apps-create/power-bi-create-content.png)

    **Controllo**

    Impostare i limiti e restrizioni che gli utenti dell'applicazione hanno con il contenuto dell'applicazione. È possibile utilizzare questo controllo per la protezione della proprietà intellettuale nell'app.

    ![Controllo](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >Esportazione in formato pbix è sempre bloccato per gli utenti che installano l'app.

    **Parametri**

    Usare questa categoria per gestire il comportamento di parametro quando ci si connette a origini dati. Altre informazioni sulle [creazione di parametri di query](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Parametri](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Valore**: il valore di parametro predefinito.
    - **Obbligatorio**: utilizzare questa opzione per richiedere il programma di installazione inserire un parametro specifico dell'utente.
    - **Blocco**: Il blocco impedisce l'aggiornamento di un parametro il programma di installazione.
    - **Statico**: Abilitare nel caso in cui l'app contiene *solo* campionare i dati. Quando si seleziona **statici**, l'installazione guidata non chiede agli utenti di connettersi a un'origine dati.

    **Accesso** nella fase di test, decidere quali altri utenti nell'organizzazione possono installare e testare l'app. Non preoccuparti, è sempre possibile tornare indietro e modificare queste impostazioni in un secondo momento (impostazione non influisce sull'accesso dell'app modello distribuito).

2. Selezionare **Crea app**.

    Viene visualizzato un messaggio indicante che l'app di test è pronta, con un collegamento da copiare e condividere con i tester di app.

    ![L'app di test è pronta](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    È stato completato anche il primo passaggio del processo di gestione del rilascio, descritto di seguito.

## <a name="manage-the-template-app-release"></a>Gestire il rilascio dell'app modello

Prima di rilasciare pubblicamente l'app modello è importante verificare che sia pronta per il rilascio. Power BI ha creato il riquadro di gestione del rilascio, nel quale è possibile seguire e controllare il percorso completo di rilascio dell'app. È anche possibile attivare la transizione da una fase alla fase successiva. Le fasi comuni sono:

- Generare l'app di test: solo per i test all'interno dell'organizzazione.
- Alzare di livello il pacchetto di test alla fase di pre-produzione: per i test all'esterno dell'organizzazione.
- Alzare di livello il pacchetto di pre-produzione a Produzione: versione di produzione.
- Eliminare tutti i pacchetti o iniziare di nuovo dalla fase precedente.

L'URL non cambia quando si spostano tra le fasi di rilascio. Innalzamento di livello non ha alcun effetto nell'URL stesso.

Verrà ora analizzato le fasi:

1. Nell'area di lavoro delle app modello selezionare **Release Management**.

    ![Icona Release Management](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Selezionare **Crea app**.

    Se l'app di test è stata creata con la procedura **Creare l'app modello di test** descritta in precedenza, il punto giallo accanto a **Test** è già visualizzato come pieno e non è necessario selezionare **Crea app** qui. Se si seleziona Crea app, si torna al processo di creazione di app modello.

3. Selezionare **Ottieni il collegamento**.

    ![Crea app, Ottieni collegamento](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. Per testare l'esperienza di installazione dell'app, copiare il collegamento nella finestra di notifica e incollarlo in una nuova finestra del browser.

    Da questo punto si segue la stessa procedura che eseguiranno i clienti. Per la versione corrispondente, vedere [Install and distribute template apps in your organization](service-template-apps-install-distribute.md) (Installare e distribuire app modello nell'organizzazione).

5. Nella finestra di dialogo selezionare **Installa**.

    Al completamento dell'installazione una notifica indica che la nuova app è pronta.

6. Selezionare **Vai all'app**.
7. In **Operazioni iniziali con la nuova app** l'app viene visualizzata come la vedono i clienti.

    ![Operazioni iniziali con la nuova app](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. Selezionare **Esplora app** per verificare l'app di test con i dati di esempio.
9. Per apportare modifiche, tornare all'app nell'area di lavoro originale. Aggiornare l'app di test fino a quando non si è soddisfatti.
10. Quando si è pronti a promuovere l'app nell'ambiente di pre-produzione per altri test all'esterno del tenant, tornare indietro per la **Release Management** riquadro, quindi selezionare **Alza di livello app**. 

    ![Alzare di livello l'app alla versione di pre-produzione](media/service-template-apps-create/power-bi-template-app-promote.png)

    >[!NOTE]
    > Quando l'app viene promossa diventa disponibile pubblicamente all'esterno dell'organizzazione.

11. Selezionare **Alza di livello** per confermare la scelta.
12. Copiare il nuovo URL da condividere all'esterno del tenant per i test. Questo collegamento è anche quello l'invio per iniziare il processo di distribuzione dell'app in AppSource mediante la creazione di un [nuova offerta Cloud Partner Portal](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Inviare solo pre-produzione collegamenti al portale Cloud Partner. Solo dopo che l'app viene approvata e si riceve notifica che la pubblicazione in AppSource, quindi è possibile alzare di livello questo pacchetto nell'ambiente di produzione in Power BI.
13. Quando l'app è pronta per la produzione o la condivisione tramite AppSource, tornare al riquadro **Release Management** e selezionare **Alza di livello app** accanto a **Pre-produzione**.
14. Selezionare **Alza di livello** per confermare la scelta.

    A questo punto l'app è in fase di produzione ed è pronta per la distribuzione.

    ![App in produzione](media/service-template-apps-create/power-bi-template-app-production.png)

Per rendere disponibile l'app a migliaia di utenti di Power BI in tutto il mondo è consigliabile inviarla ad AppSource. Per informazioni dettagliate, vedere [Offerta di applicazione Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).

## <a name="update-your-app"></a>Aggiornare l'app

Ora che l'app è in fase di produzione è possibile riattivare la fase di test, senza alcun effetto sull'app nell'ambiente di produzione.

1. Nel riquadro **Release Management** selezionare **Crea app**.
2. Ripetere il processo di creazione app.
3. Dopo aver impostato le opzioni in **Personalizzazione**, **Contenuto**, **Controllo** e **Accesso** selezionare di nuovo **Crea app**.
4. Selezionare **Chiudi** e tornare a **Release Management**.

   Ora sono disponibili due versioni: la versione nell'ambiente di produzione e una nuova versione di test.

    ![Due versioni di un'app modello](media/service-template-apps-create/power-bi-template-app-2-versions.png)

5. Quando si è pronti a promuovere l'app nell'ambiente di pre-produzione per altri test all'esterno del tenant, tornare al riquadro di Release Management e selezionare **Alza di livello app** accanto a **test**.
6. È ora disponibile anche il collegamento, inviarla nuovamente al portale Cloud Partner seguendo i passaggi descritti in [aggiornamento di App di Power BI offerta](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).

>[!NOTE]
>Promuovi la tua app alla fase di produzione solo dopo che l'app viene approvata dal portale per Cloud Partner ed è stato pubblicato.

## <a name="next-steps"></a>Passaggi successivi

Osservare come i clienti interagiscono con l'app modello in [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Installare, personalizzare e distribuire app modello nell'organizzazione).

Per informazioni dettagliate sulla distribuzione dell'app, vedere [Offerta di applicazione Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
