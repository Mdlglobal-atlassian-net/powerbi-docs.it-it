---
title: Come acquistare Power BI Premium
description: Informazioni su come acquistare Power BI Premium e abilitare l'accesso ai contenuti per tutta l'organizzazione.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/13/2020
LocalizationGroup: Premium
ms.openlocfilehash: aed0d1e4dec6f6efe49dd39cd5b6fc60f8977e44
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488615"
---
# <a name="how-to-purchase-power-bi-premium"></a>Come acquistare Power BI Premium

Questo articolo descrive le modalità di acquisto della capacità Premium di Power BI per l'organizzazione. Questo articolo illustra due scenari:

- Uso degli SKU P per scenari di produzione tipici. Gli SKU P richiedono un impegno mensile o annuale e vengono fatturati mensilmente.

- Uso degli SKU A per gli scenari di testing e nei casi in cui non sono disponibili le autorizzazioni necessarie per acquistare SKU P (ruolo Amministratore globale o Amministratore fatturazione di Microsoft 365). Gli SKU A non richiedono alcun impegno in termini di tempo e vengono fatturati su base oraria. Gli SKU A possono essere acquistati nel [portale di Azure](https://portal.azure.com).

Per altre informazioni su Power BI Premium, vedere [Che cos'è Power BI Premium?](service-premium-what-is.md) Per informazioni sui prezzi e la pianificazione correnti, vedere la [pagina dei prezzi di Power BI](https://powerbi.microsoft.com/pricing/) e il [calcolatore Power BI Premium](https://powerbi.microsoft.com/calculator/). Per gli autori del contenuto è ancora necessaria una [licenza di Power BI Pro](service-admin-purchasing-power-bi-pro.md), anche se l'organizzazione usa Power BI Premium. Acquistare almeno una licenza di Power BI Pro per l'organizzazione. Con gli SKU A, anche per _tutti gli utenti_ che utilizzano il contenuto sono richieste licenze Pro.

> [!NOTE]
> Quando una sottoscrizione Premium scade, l'accesso completo alla capacità è garantito per altri 30 giorni. Allo scadere di questo periodo, il contenuto torna ad avere una capacità condivisa. I modelli di dimensioni superiori a 1 GB non sono supportati nella capacità condivisa.

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>Acquistare SKU P per scenari di produzione tipici

È possibile creare un nuovo tenant con uno SKU P1 di Power BI Premium configurato oppure è possibile acquistare una capacità Power BI Premium per un'organizzazione esistente. In entrambi i casi è possibile aggiungere capacità in seguito all'occorrenza.

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Creare un nuovo tenant con Power BI Premium P1

Se non si ha un tenant esistente e si vuole crearne uno, è possibile acquistare contemporaneamente Power BI Premium. Il collegamento seguente guida attraverso il processo di creazione di un nuovo tenant e consente di acquistare Power BI Premium: [Power BI Premium P1](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). Quando si crea il tenant, si viene automaticamente assegnati al ruolo di amministratore globale di Microsoft 365 per il tenant.

Dopo aver acquistato la capacità, vedere come [gestire le capacità](service-admin-premium-manage.md#manage-capacity) e [assegnare le aree di lavoro](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) a una capacità.

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Acquistare capacità di Power BI Premium per l'organizzazione

Se si ha un'organizzazione esistente (tenant), è necessario avere il ruolo di amministratore globale di Microsoft 365 o di amministratore fatturazione per l'acquisto di sottoscrizioni e licenze. Per altre informazioni, vedere [Informazioni sui ruoli di amministratore di Microsoft 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Per acquistare la capacità Premium, seguire questa procedura.

1. Dal servizio Power BI selezionare la selezione app Microsoft 365 e quindi **Amministratore**.

    ![Selezione app Microsoft 365](media/service-admin-premium-purchase/o365-app-picker.png)

    In alternativa, è possibile passare al centro di amministrazione di Microsoft 365,

1. Selezionare **Fatturazione** > **Acquisto di servizi**.

1. In **Other plans** (Altri piani) cercare le offerte di Power BI Premium. Verranno elencate le offerte da P1 a P3, EM3 e P1 (mensile).

1. Passare il mouse sui puntini di sospensione ( **. . .** ) e selezionare **Buy now** (Acquista).

    ![Acquista ora](media/service-admin-premium-purchase/premium-purchase.png)

1. Per completare l'acquisto, seguire la procedura.

Dopo aver completato l'acquisto, la pagina **Acquisto di servizi** indica che l'elemento è stato acquistato ed è attivo.

![Acquisto di Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

Dopo aver acquistato la capacità, vedere come [gestire le capacità](service-admin-premium-manage.md#manage-capacity) e [assegnare le aree di lavoro](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) a una capacità.

### <a name="purchase-additional-capacities"></a>Acquistare capacità aggiuntive

Ora che si ha una capacità, è possibile aggiungerne altre in base alle esigenze. È possibile usare qualsiasi combinazione di SKU per la capacità Premium, da P1 a P3, all'interno dell'organizzazione. I vari SKU offrono diverse capacità delle risorse.

1. Nell'interfaccia di amministrazione di Microsoft 365 selezionare **Fatturazione** > **Acquisto di servizi**.

1. Trovare l'elemento di Power BI Premium che si desidera acquistare in **Other plans** (Altri piani).

1. Passare il mouse su **Altre opzioni** (...) e quindi selezionare **Cambia la quantità di licenze**.

    ![Cambia la quantità di licenze](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Modificare il numero di istanze che si desidera avere per questo elemento. Selezionare quindi **Invia** al termine.

   > [!IMPORTANT]
   > Se si seleziona **Invia** viene eseguito l'addebito sulla carta di credito inserita.

La pagina **Acquisto di servizi** indica il numero di istanze disponibili. All'interno del portale di amministrazione di Power BI, in **Impostazioni di capacità**, le memorie centrali virtuali disponibili riflettono la nuova capacità acquistata.

![Memorie centrali virtuali disponibili per la capacità di Power BI Premium](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>Annullare la sottoscrizione

È possibile annullare la sottoscrizione dall'interfaccia di amministrazione di Microsoft 365. Per annullare la sottoscrizione Premium, eseguire le operazioni seguenti.

1. Passare all'interfaccia di amministrazione di Microsoft 365.

1. Selezionare **Fatturazione** > **Sottoscrizioni**.

1. Selezionare la sottoscrizione di Power BI Premium dall'elenco.

1. Selezionare **Altre azioni** > **Annulla sottoscrizione**.

1. La pagina **Annulla sottoscrizione** indicherà se si è responsabili o no di una [penale per risoluzione anticipata](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3). Questa pagina indica anche quando verranno eliminati i dati per la sottoscrizione.

1. Leggere attentamente le informazioni e, se si vuole continuare, selezionare **Annulla sottoscrizione**.

#### <a name="when-canceling-or-your-license-expires"></a>Annullamento o scadenza della licenza

Quando si annulla la sottoscrizione Premium o la licenza per la capacità scade, è possibile continuare ad accedere alle capacità Premium per un periodo di 30 giorni dalla data dell'annullamento o della scadenza della licenza. Passati i 30 giorni non sarà più possibile accedere alle capacità Premium o alle relative aree di lavoro.

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>Acquistare SKU A per scenari di testing e di altro tipo

Gli SKU A vengono resi disponibili tramite il servizio Power BI Embedded di Azure. È possibile usare gli SKU A nei modi seguenti:

- Abilitare l'incorporamento di Power BI nelle applicazioni di terze parti. Per altre informazioni, vedere [Power BI Embedded](developer/embedded/azure-pbie-what-is-power-bi-embedded.md).

- Testare la funzionalità Premium prima di acquistare uno SKU P.

- Creare ambienti di sviluppo e test insieme a un ambiente di produzione che usa SKU P.

- Acquistare Power BI Premium anche se non si è un amministratore globale o un amministratore fatturazione di Microsoft 365.

> [!NOTE]
> Se si acquista uno SKU A4 o superiore, è possibile sfruttare tutte le funzionalità Premium, ad eccezione della condivisione illimitata di contenuto. Con gli SKU A, per _tutti gli utenti_ che utilizzano il contenuto sono richieste licenze Pro.

Seguire questa procedura per acquistare SKU A nel portale di Azure:

1. Accedere al [portale di Azure](https://portal.azure.com) con un account che abbia almeno le autorizzazioni di amministratore di capacità in Power BI.

1. Cercare _Power BI Embedded_ e selezionare il servizio nei risultati della ricerca.

    ![Ricerca nel portale di Azure](media/service-admin-premium-purchase/azure-portal-search.png)

1. Selezionare **Crea Power BI Embedded**.

    ![Crea Power BI Embedded](media/service-admin-premium-purchase/create-power-bi-embedded.png)

1. Nella schermata di creazione di **Power BI Embedded** specificare le informazioni seguenti:

    - La **Sottoscrizione** in cui creare il servizio di Power BI Embedded.

    - La **Posizione** fisica in cui creare il gruppo di risorse che contiene il servizio. Per ottenere prestazioni migliori, questa posizione dovrebbe essere vicina alla posizione del tenant di Azure Active Directory per Power BI.

    - Il **Gruppo di risorse** esistente da usare o crearne uno nuovo come illustrato nell'esempio.

    - L'**amministratore di capacità di Power BI**. L'amministratore di capacità deve essere un utente membro o un'entità servizio nel tenant di Azure AD.

    ![Sottoscrizione e gruppo di risorse](media/service-admin-premium-purchase/subscription-resource-group.png)

1. Se si vogliono usare tutte le funzionalità di Power BI Premium (ad eccezione della condivisione illimitata), è necessario almeno uno SKU A4. Selezionare **Modifica dimensioni**.

    ![Modifica le dimensioni della capacità](media/service-admin-premium-purchase/change-capacity-size.png)

1. Selezionare la dimensione della capacità A4, A5 o A6, corrispondente a P1, P2 e P3.

    ![Selezionare la capacità A3](media/service-admin-premium-purchase/select-a3-capacity.png)

1. Selezionare **Rivedi e crea**, rivedere le opzioni scelte e quindi selezionare **Crea**.

    ![Crea risorsa](media/service-admin-premium-purchase/create-resource.png)

1. Per il completamento della distribuzione possono essere richiesti alcuni minuti. Quando è pronta, selezionare **Vai alla risorsa**.

    ![Distribuzione completata](media/service-admin-premium-purchase/deployment-complete.png)

1. Nella schermata di gestione esaminare le opzioni disponibili per la gestione del servizio, inclusa la sospensione del servizio quando non viene usato.

    ![Gestire la capacità](media/service-admin-premium-purchase/manage-capacity.png)

Dopo aver acquistato la capacità, vedere come [gestire le capacità](service-admin-premium-manage.md#manage-capacity) e [assegnare le aree di lavoro](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) a una capacità.

## <a name="next-steps"></a>Passaggi successivi

[Configurare e gestire le capacità in Power BI Premium](service-admin-premium-manage.md)\
[Prezzi di Power BI](https://powerbi.microsoft.com/pricing/)\
[Calcolatore Power BI Premium](https://powerbi.microsoft.com/calculator/)\
[Domande frequenti su Power BI Premium](service-premium-faq.md)\
[Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendale di Power BI)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
