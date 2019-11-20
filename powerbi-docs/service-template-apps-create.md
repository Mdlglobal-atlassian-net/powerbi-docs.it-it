---
title: Creare app modello in Power BI
description: Come creare in Power BI app modello distribuibili a tutti i clienti Power BI.
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/15/2019
ms.author: tebercov
ms.openlocfilehash: 4b3158cbe26efe05e3d35c1c6c93027738cc817a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871485"
---
# <a name="create-a-template-app-in-power-bi"></a>Creare un'app modello in Power BI

Le nuove *app modello* di Power BI consentono ai partner Power BI di creare app Power BI con un uso minimo o nullo di codice e quindi di distribuire le app a qualsiasi cliente Power BI.  Questo articolo contiene istruzioni dettagliate per la creazione di un'app modello di Power BI.

Se si ha familiarità con la creazione di report e dashboard di Power BI, è possibile diventare un *creatore di app modello* per integrare e organizzare contenuti analitici in un'*app*. È possibile distribuire l'app ad altri tenant di Power BI tramite qualsiasi piattaforma disponibile, ad esempio con AppSource, oppure usandola nel proprio servizio Web. In qualità di creatore dell'app è possibile creare un pacchetto analitico protetto per la distribuzione.

Gli amministratori tenant di Power BI determinano quali utenti dell'organizzazione sono autorizzati a creare app modello e quali utenti possono installare tali app. Gli utenti autorizzati possono installare l'app modello, quindi modificarla e distribuirla agli utenti Power BI dell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

I requisiti per la creazione di un'app modello sono i seguenti:  

- Una [licenza di Power BI Pro](service-self-service-signup-for-power-bi.md)
- Un'[installazione di Power BI Desktop](desktop-get-the-desktop.md) (facoltativa)
- Conoscenza dei [concetti di base di Power BI](service-basic-concepts.md)
- Autorizzazioni per condividere un'app modello pubblicamente. Per informazioni dettagliate, vedere [Impostazioni app modello nel portale di amministrazione](service-admin-portal.md#template-apps-settings) di Power BI.

## <a name="create-the-template-workspace"></a>Creare l'area di lavoro modello

Per creare un'app modello distribuibile ad altri tenant di Power BI, è necessario creare tale app in una delle nuove aree di lavoro.

1. Nel servizio Power BI selezionare **Aree di lavoro** > **Crea area di lavoro**.

    ![Creare l'area di lavoro](media/service-template-apps-create/power-bi-new-workspace.png)

2. In **Crea area di lavoro** selezionare **Esegui aggiornamento alla nuova versione**.

    ![Provare le nuove aree di lavoro](media/service-template-apps-create/power-bi-upgrade-new.png)

3. Immettere il nome, la descrizione (facoltativa) e l'immagine del logo (facoltativa) dell'area di lavoro.

4. Espandere la sezione **Avanzate** e selezionare **Sviluppa un'app modello**.

    ![Sviluppa un'app modello](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Selezionare **Salva**.
>[!NOTE]
>Sono necessarie le autorizzazioni dell'amministratore di Power BI per alzare di livello le app modello.

## <a name="create-the-content-in-your-template-app"></a>Creare il contenuto nell'app modello

Come in qualsiasi area di lavoro di Power BI, il passaggio successivo è la creazione del contenuto nell'area di lavoro.  

- [Creare il contenuto di Power BI](power-bi-creator-landing.md) nell'area di lavoro.

Se si usano parametri in Power Query, assicurarsi che abbiano un tipo ben definito (ad esempio Testo). I tipi Qualsiasi e Binario non sono supportati.

[Suggerimenti per la creazione di app modello in Power BI](service-template-apps-tips.md) include suggerimenti utili per la creazione di report e dashboard per l'app modello.

## <a name="create-the-test-template-app"></a>Creare l'app modello di test

Ora che l'area di lavoro include contenuto, è possibile integrare tale contenuto in un'app modello. Il primo passaggio è la creazione di un'app modello di test, accessibile solo dall'interno dell'organizzazione nel tenant.

1. Nell'area di lavoro modello selezionare **Crea app**.

    ![Crea app](media/service-template-apps-create/power-bi-create-app.png)

    Definire le opzioni di compilazione aggiuntive per l'app modello, suddivise in cinque categorie:

    **Personalizzazione**

    ![Personalizzazione](media/service-template-apps-create/power-bi-create-branding.png)
    - Nome app
    - Descrizione
    - Sito del supporto (il collegamento viene presentato sotto le info dell'app dopo la ridistribuzione dell'app modello come app per l'organizzazione)
    - Logo dell'app (dimensione massima dei file 45K, proporzioni 1:1, formato png, jpg, jpeg)
    - Colore tema dell'app

    **Struttura di spostamento**

    Attivare il **Nuovo generatore di struttura di spostamento** in cui è possibile definire il riquadro di spostamento dell'app. Per informazioni dettagliate, vedere [Progettare l'esperienza di spostamento](service-create-distribute-apps.md#design-the-navigation-experience) in questo articolo.

   ![Impostare la pagina di destinazione dell'app](media/service-template-apps-install-distribute/power-bi-install-app-content.png)
    
    **Pagina di destinazione dell'app:** Se si decide di rifiutare esplicitamente il generatore della struttura di spostamento, è possibile selezionare la pagina di destinazione dell'app. definire un report o un dashboard come pagina di destinazione dell'app. Usare una pagina di destinazione che offra la giusta impressione.

    **Controllo**

    Impostare limitazioni e restrizioni per gli utenti dell'applicazione in merito al contenuto dell'applicazione. È possibile usare questo controllo per proteggere i dati dell'app coperti da proprietà intellettuale.

    ![Controllo](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >L'esportazione in formato pbix è sempre bloccata per gli utenti che installano l'app.

    **Parametri**

    Usare questa categoria per gestire il comportamento dei parametri quando ci si connette a origini dati. Per altre informazioni, vedere la [creazione di parametri di query](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Parametri](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Valore**: valore del parametro predefinito.
    - **Obbligatorio**: usare questa opzione per richiedere che il programma di installazione inserisca un parametro specifico dell'utente.
    - **Blocco**: il blocco impedisce al programma di installazione di aggiornare un parametro.

    **Accesso** Nella fase di test è possibile decidere quali altri utenti nell'organizzazione possono installare e testare l'app. È sempre possibile tornare indietro e modificare queste impostazioni in un secondo momento. Questa impostazione non influisce sull'accesso all'app modello distribuita.

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

L'URL non cambia passando da una fase di rilascio a un'altra. L'innalzamento di livello non ha alcun effetto sull'URL.

Di seguito sono riportate le fasi in dettaglio:

1. Nell'area di lavoro modello selezionare **Release Management**.

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
10. Quando si è pronti per alzare di livello l'app alla pre-produzione per altri test all'esterno del tenant, tornare al riquadro **Release Management** e selezionare **Alza di livello app**. 

    ![Alzare di livello l'app alla versione di pre-produzione](media/service-template-apps-create/power-bi-template-app-promote.png)
    >[!NOTE]
    > Quando l'app viene alzata di livello diventa disponibile pubblicamente all'esterno dell'organizzazione.

    Se l'opzione non è visibile, contattare l'amministratore di Power BI per ottenere le [autorizzazioni per lo sviluppo di app modello](service-admin-portal.md#template-apps-settings) nel portale di amministrazione.
11. Selezionare **Alza di livello** per confermare la scelta.
12. Copiare il nuovo URL da condividere all'esterno del tenant per i test. Questo collegamento è lo stesso che si invia per iniziare il processo di distribuzione dell'app in AppSource creando una [nuova offerta nel portale Cloud Partner](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Inviare solo collegamenti di pre-produzione nel portale Cloud Partner. Solo dopo che l'app viene approvata e si riceve la notifica della pubblicazione in AppSource, è possibile alzare di livello questo pacchetto alla produzione in Power BI.
13. Quando l'app è pronta per la produzione o la condivisione tramite AppSource, tornare al riquadro **Release Management** e selezionare **Alza di livello app** accanto a **Pre-produzione**.
14. Selezionare **Alza di livello** per confermare la scelta.

    A questo punto l'app è in fase di produzione ed è pronta per la distribuzione.

    ![App in produzione](media/service-template-apps-create/power-bi-template-app-production.png)

Per rendere disponibile l'app a migliaia di utenti di Power BI in tutto il mondo è consigliabile inviarla ad AppSource. Per informazioni dettagliate, vedere [Offerta di applicazione Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).

## <a name="next-steps"></a>Passaggi successivi

Osservare come i clienti interagiscono con l'app modello in [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Installare, personalizzare e distribuire app modello nell'organizzazione).

Per informazioni dettagliate sulla distribuzione dell'app, vedere [Offerta di applicazione Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
