---
title: Linee guida per le impostazioni di amministrazione del tenant
description: Linee guida per le impostazioni del tenant di Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: v-pemyer
ms.openlocfilehash: 1ab1ed139a62b1929cb1b4da411bf7949a5d151e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279757"
---
# <a name="tenant-admin-settings-guidance"></a>Linee guida per le impostazioni di amministrazione del tenant

Questo articolo è destinato agli amministratori di Power BI responsabili della configurazione dell'ambiente Power BI nella loro organizzazione.

Contiene le linee guida per le impostazioni specifiche del tenant che consentono di migliorare l'esperienza di Power BI o che possono esporre a rischio l'organizzazione. È consigliabile configurare sempre il tenant in base ai criteri e ai processi dell'organizzazione.

Le [impostazioni del tenant](../admin/service-admin-portal.md#tenant-settings) vengono gestite nel [portale di amministrazione](https://app.powerbi.com/admin-portal/tenantSettings) e possono essere configurate da un [amministratore del servizio Power BI](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi). Molte impostazioni del tenant possono limitare le funzionalità a un determinato set di utenti. È quindi consigliabile acquisire familiarità con le impostazioni per pianificare i gruppi di sicurezza necessari. Si noterà che è possibile applicare lo stesso gruppo di sicurezza a più impostazioni.

## <a name="improve-power-bi-experience"></a>Migliorare l'esperienza di Power BI

### <a name="publish-get-help-information"></a>Pubblica informazioni su "Supporto"

È consigliabile configurare siti interni correlati a Power BI usando [Microsoft Teams](/microsoftteams) o un'altra piattaforma di collaborazione. Questi siti possono essere usati per archiviare la documentazione per il training, ospitare discussioni, richiedere licenze o rispondere a richieste di supporto.

In tal caso, è consigliabile abilitare l'impostazione **Pubblica informazioni su "Supporto"** _per l'intera organizzazione_. Si trova nel gruppo **Impostazioni per Guida e supporto tecnico**. È possibile impostare gli URL per:

- Documentazione per training
- Forum di discussione
- Richieste di licenza
- Help desk

Questi URL diventeranno disponibili come collegamenti nel menu della Guida di Power BI.

> [!NOTE]
> Se si specifica l'URL per **Richieste di licenza**, i singoli utenti non potranno iscriversi per la versione di valutazione gratuita di 60 giorni di Power BI Pro. Verranno invece indirizzati al sito interno con informazioni sulla modalità di acquisizione di una licenza, gratuita o Pro.

![Visualizzazione dell'impostazione Pubblica informazioni su "Supporto".](media/admin-tenant-settings/publish-get-help-information.png)

## <a name="manage-risk"></a>per gestire i rischi.

### <a name="receive-email-notification-service-outages-or-incidents"></a>Ricevere notifiche di posta elettronica per interruzioni del servizio o eventi imprevisti

È possibile ricevere una notifica tramite posta elettronica se il tenant subisce un'interruzione del servizio o un evento imprevisto. In questo modo, è possibile rispondere in modo proattivo agli eventi imprevisti.

È consigliabile abilitare l'impostazione **Ricevi notifiche di posta elettronica per interruzioni del servizio o eventi imprevisti**. Si trova nel gruppo **Impostazioni per Guida e supporto tecnico**. Assegnare uno o più gruppi di sicurezza _abilitati per la posta_.

![Visualizzazione dell'impostazione "Ricevi notifiche di posta elettronica per interruzioni del servizio o eventi imprevisti".](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>Protezione delle informazioni

La protezione delle informazioni consente di applicare le impostazioni di protezione, ad esempio la crittografia o le filigrane, quando si esportano dati dal servizio Power BI.

Sono disponibili due impostazioni del tenant correlate alla protezione delle informazioni. Per impostazione predefinita, entrambe sono disabilitate per l'intera organizzazione.

È consigliabile abilitarle quando è necessario gestire e proteggere i dati sensibili. Per altre informazioni, vedere [Protezione dei dati in Power BI](../admin/service-security-data-protection-overview.md).

### <a name="create-workspaces"></a>Creare aree di lavoro

È possibile impedire agli utenti di creare aree di lavoro in modo da avere un maggiore controllo sugli elementi creati all'interno dell'organizzazione.

> [!NOTE]
> Attualmente è in corso una fase di transizione tra l'esperienza dell'area di lavoro precedente e quella nuova. Questa impostazione del tenant si applica solo alla nuova esperienza.

L'impostazione **Crea aree di lavoro** è abilitata per impostazione predefinita per l'intera organizzazione. Si trova nel gruppo **Impostazioni area di lavoro**.

È consigliabile assegnare uno o più gruppi di sicurezza. A questi gruppi è possibile concedere _o negare_ l'autorizzazione per la creazione di aree di lavoro.

Assicurarsi di includere nella documentazione le istruzioni che spiegano agli utenti (privi dei diritti di creazione dell'area di lavoro) come richiedere una nuova area di lavoro.

![Visualizzazione dell'impostazione "Crea aree di lavoro".](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>Condividi contenuti con utenti esterni

Gli utenti possono condividere report e dashboard con persone esterne all'organizzazione.

L'impostazione **Condividi contenuto con utenti esterni** è abilitata per impostazione predefinita per l'intera organizzazione. Si trova nel gruppo **Impostazioni di esportazione e condivisione**.

È consigliabile assegnare uno o più gruppi di sicurezza. A questi gruppi è possibile concedere _o negare_ l'autorizzazione per la condivisione di contenuti con utenti esterni.

![Visualizzazione dell'impostazione "Condividi contenuti con utenti esterni".](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>Pubblica sul Web

La funzionalità [Pubblica sul Web](../collaborate-share/service-publish-to-web.md) consente di pubblicare report pubblici sul Web. Se è usata in modo inappropriato, si corre il rischio che le informazioni riservate vengano rese disponibili sul Web.

L'impostazione **Pubblica sul Web** è abilitata per impostazione predefinita per l'intera organizzazione, ma limita la capacità degli utenti non amministratori di creare codici di incorporamento. Si trova nel gruppo **Impostazioni di esportazione e condivisione**.

Se è abilitata, è consigliabile assegnare uno o più gruppi di sicurezza. A questi gruppi è possibile concedere _o negare_ l'autorizzazione per la pubblicazione di report.

È inoltre possibile scegliere la modalità di funzionamento dei codici di incorporamento. Per impostazione predefinita, è attivata l'opzione **Consenti solo i codici esistenti**. In questo modo, gli utenti dovranno contattare un amministratore di Power BI per creare un codice di incorporamento.

![Visualizzazione dell'impostazione "Pubblica sul Web".](media/admin-tenant-settings/publish-to-web.png)

È consigliabile esaminare regolarmente i [codici di incorporamento di Pubblica sul Web](https://app.powerbi.com/admin-portal/embedCodes). Rimuovere i codici se comportano la pubblicazione di informazioni private o riservate.

### <a name="export-data"></a>Esporta dati

È possibile impedire agli utenti di esportare i dati dai riquadri di dashboard o dagli oggetti visivi di report.

L'impostazione **Esporta dati** è abilitata per impostazione predefinita per l'intera organizzazione. Si trova nel gruppo **Impostazioni di esportazione e condivisione**.

È consigliabile assegnare uno o più gruppi di sicurezza. A questi gruppi è possibile concedere _o negare_ l'autorizzazione per la pubblicazione di report.

> [!IMPORTANT]
> La disabilitazione di questa impostazione limita anche l'utilizzo delle funzionalità [Analizza in Excel](../collaborate-share/service-analyze-in-excel.md) e [Connessione dinamica](../connect-data/desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management) del servizio Power BI.

![Visualizzazione dell'impostazione "Esporta dati".](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> Se agli utenti è consentito di esportare dati, è possibile aggiungere un livello di protezione applicando la funzionalità di [protezione dei dati](../admin/service-security-data-protection-overview.md). Quando questa funzionalità è configurata, gli utenti non autorizzati non possono esportare contenuto con etichette di riservatezza.

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione

È possibile consentire agli utenti guest esterni di modificare e gestire il contenuto di Power BI. Per altre informazioni, vedere [Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B](../admin/service-admin-azure-ad-b2b.md).

L'impostazione **Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione** è disabilitata per impostazione predefinita per l'intera organizzazione. Si trova nel gruppo **Impostazioni di esportazione e condivisione**.

Se è necessario autorizzare utenti esterni a modificare e gestire il contenuto, è consigliabile assegnare uno o più gruppi di sicurezza. A questi gruppi è possibile concedere _o negare_ l'autorizzazione per la pubblicazione di report.

![Visualizzazione dell'impostazione "Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione".](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>Impostazioni modalità sviluppatore

Sono disponibili due impostazioni del tenant correlate all'[incorporamento del contenuto di Power BI](../developer/embedded/embedding.md), ovvero:

- Incorpora il contenuto nelle app (abilitata per impostazione predefinita)
- Consenti alle entità servizio di usare le API Power BI (disabilitata per impostazione predefinita)

Se non si ha intenzione di usare le API per sviluppatori per incorporare il contenuto, è consigliabile disabilitare queste opzioni. In alternativa, configurare almeno gruppi di sicurezza specifici per l'esecuzione di questo lavoro.

![Visualizzazione delle impostazioni per sviluppatori.](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Che cos'è l'amministrazione di Power BI?](../admin/service-admin-administering-power-bi-in-your-organization.md)
- [Amministrazione di Power BI nel portale di amministrazione](../admin/service-admin-portal.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com)

