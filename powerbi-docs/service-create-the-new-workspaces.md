---
title: Creare le nuove aree di lavoro - Power BI
description: Informazioni su come creare le nuove aree di lavoro, raccolte di dashboard, report e i report impaginati compilati per offrire metriche chiave per l'organizzazione.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61142076"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Creare le nuove aree di lavoro in Power BI

Power BI ha introdotto una nuova esperienza dell'area di lavoro. Le aree di lavoro sono ancora la posizione in cui collaborare con colleghi alla creazione di raccolte di dashboard, report e i report impaginati. Quindi è possibile aggregare tale raccolta in un' *app* e distribuirlo nell'intera organizzazione o a specifici utenti o gruppi. 

Ecco cosa è diversa. In nuove aree di lavoro, è possibile:

- Assegnare ruoli dell'area di lavoro a gruppi di utenti: gruppi di sicurezza, liste di distribuzione, gruppi di Office 365 e singoli utenti.
- Creare un'area di lavoro in Power BI senza creare un gruppo di Office 365.
- Usare ruoli dell'area di lavoro con maggiore granularità per aumentare la flessibilità di gestione delle autorizzazioni in un'area di lavoro.

> [!NOTE]
> Per applicare la sicurezza a livello di riga (RLS) per Power BI Pro agli utenti di cercare contenuto in un'area di lavoro, continuare a usare [aree di lavoro classici](service-create-workspaces.md). Selezionare il **i membri possono solo visualizzare il contenuto di Power BI** opzione. In alternativa, pubblicare un'app di Power BI agli utenti oppure utilizzare la condivisione per distribuire il contenuto. Il ruolo di Visualizzatore imminente abilitando questo scenario in futuro in nuove aree di lavoro dell'area di lavoro esperienza.

Per altre informazioni, vedere la [nuove aree di lavoro](service-new-workspaces.md) articolo.

## <a name="create-one-of-the-new-app-workspaces"></a>Creare una delle nuove aree di lavoro per le app

1. Iniziare creando l'area di lavoro per le app. Selezionare **Aree di lavoro** > **Creare un'area di lavoro per le app**.
   
     ![Crea area di lavoro per le app](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. Si crea automaticamente un'area di lavoro aggiornata, a meno che non si sceglie al **ripristinare la versione classica**.
   
     ![Nuova esperienza dell'area di lavoro](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Se si seleziona **ripristinare la versione classica**, si crea un'area di lavoro basato su un gruppo di Office 365. Usare questa opzione se è necessario il **i membri possono solo visualizzare il contenuto di Power BI** opzione per applicare la sicurezza a livello di riga (RLS) per i membri dell'area di lavoro.

2. Assegnare un nome all'area di lavoro. Se il nome non è disponibile, modificare in modo da ottenere con un nome univoco.
   
     L'app per l'area di lavoro avrà lo stesso nome e icona dell'area di lavoro.
   
1. Ecco alcuni elementi facoltativi, che è possibile impostare per l'area di lavoro:

    Caricare un **immagine dell'area di lavoro**. I file possono essere formato con estensione jpg o PNG. Dimensioni del file deve essere inferiori a 45 KB.
    
    [Aggiungere un **elenco contatti**](#workspace-contact-list). Per impostazione predefinita, gli amministratori dell'area di lavoro sono i contatti. 
    
    [Specificare una **area di lavoro di OneDrive** ](#workspace-onedrive) digitando semplicemente il nome di un gruppo di 365 Office esistente, non nell'URL. Questa area di lavoro può ora usare il percorso di archiviazione file di tale gruppo di Office 365. 

    ![Specificare un percorso di OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Per assegnare l'area di lavoro a un **capacità dedicata**via le **Premium** scheda selezionare **capacità dedicata**.
     
    ![Capacità dedicata](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Selezionare **Salva**.

    Power BI crea l'area di lavoro, che verrà aperta e visualizzata nell'elenco delle aree di lavoro di cui si è membri. 

## <a name="workspace-contact-list"></a>Elenco dei contatto dell'area di lavoro

Elenco dei contatti nuova area di lavoro consente di specificare gli utenti che ricevono notifiche sui problemi che si verificano nell'area di lavoro. Per impostazione predefinita, qualsiasi utente o gruppo specificato come un'area di lavoro amministrazione è una notifica, ma è possibile personalizzare l'elenco. Gli utenti o gruppi elencati nell'elenco dei contatti verranno visualizzati nell'interfaccia utente (UI) per consentire agli utenti informazioni correlate all'area di lavoro.

1. Accedere al nuovo **elenco contatti** impostazione in uno dei due modi:

    Nel **creare un'area di lavoro** riquadro quando si crea innanzitutto.

    Nel riquadro di spostamento a sinistra, selezionare la freccia accanto a **aree di lavoro**, selezionare i puntini di sospensione (...) accanto al nome dell'area di lavoro > **le impostazioni dell'area di lavoro**. Il **impostazioni** viene visualizzato il riquadro.

    ![Impostazioni dell'area di lavoro](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Sotto **avanzate** > **elenco contatti**, accettare quello predefinito **gli amministratori dell'area di lavoro**, o aggiungere il proprio elenco di **gruppioutentispecifici**. 
3. Selezionare **Salva**.

## <a name="workspace-onedrive"></a>OneDrive dell'area di lavoro

La funzionalità di OneDrive dell'area di lavoro consente di configurare un gruppo di Office 365 con archiviazione file di raccolta documenti di SharePoint è disponibile per gli utenti dell'area di lavoro. Prima di tutto si crea il gruppo di fuori di Power BI. 

Power BI non sincronizzare le autorizzazioni di utenti o gruppi che sono configurati per l'area di lavoro di accedere con l'appartenenza al gruppo di Office 365. La procedura consigliata è assegnare lo stesso gruppo di Office 365, archiviazione file di cui si configura in questo gruppo di impostazioni Office 365, [l'accesso all'area di lavoro](#give-access-to-your-workspace). Quindi gestire l'accesso dell'area di lavoro mediante la gestione di appartenenza al gruppo di Office 365. 

1. Accedere al nuovo **area di lavoro di OneDrive** impostazione in uno dei due modi:

    Nel **creare un'area di lavoro** riquadro quando si crea innanzitutto.

    Nel riquadro di spostamento a sinistra, selezionare la freccia accanto a **aree di lavoro**, selezionare i puntini di sospensione (...) accanto al nome dell'area di lavoro > **le impostazioni dell'area di lavoro**. Il **impostazioni** viene visualizzato il riquadro.

    ![Impostazioni dell'area di lavoro](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Sotto **avanzate** > **area di lavoro di OneDrive**, digitare il nome del gruppo di Office 365 creata in precedenza. Power BI recupererà automaticamente da OneDrive per il gruppo.

    ![Specificare un percorso di OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Selezionare **Salva**.

### <a name="access-the-workspace-onedrive-location"></a>Il percorso OneDrive dell'area di lavoro di accesso

Dopo aver configurato il percorso di OneDrive, è possibile passare a tale da alcune posizioni diverse nell'area di lavoro:

- Selezionare **aree di lavoro** > *nome area di lavoro* > i puntini di sospensione ( **...** ) dal menu > **file**. 

    ![Percorso dei file di area di lavoro](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Selezionare i puntini di sospensione ( **...** ) dal menu nell'angolo superiore destro dell'area di lavoro > **file**.

    ![Percorso dei file di area di lavoro](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- Nel **recupera dati** > **file** esperienza. Il **OneDrive-Business** voce è il proprio OneDrive for Business. Il secondo OneDrive è quello che è stato aggiunto.

    ![Percorso dei file di area di lavoro - ottenere i dati](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>Aggiungere contenuto all'area di lavoro per le app

Dopo aver creato una nuova area di lavoro esperienza dell'area di lavoro, è possibile aggiungervi contenuto. Aggiunta di contenuto è simile nelle aree di lavoro nuove e classiche. Utilizzare il pulsante Crea o recupera dati per aggiungere contenuto nell'area di lavoro.

1. Nel **benvenuto** schermata per la nuova area di lavoro, è possibile aggiungere contenuto. 

    ![Schermata di benvenuto della nuova area di lavoro](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Ad esempio, selezionare **Esempi** > **Esempio di analisi della redditività dei clienti**.

> [!NOTE]
> In nuove aree di lavoro, è Impossibile usare pacchetti di contenuto aziendali o pacchetti di contenuto di terze parti. Le app sono disponibili per tutti i contenuti di terze parti Pack è usato in precedenza. Usare le aree di lavoro classici se è necessario continuare a usare Power BI. Pacchetti di contenuto sono deprecati, pertanto è consigliabile usare invece le app.

Quando si visualizza il contenuto in un'area di lavoro per le app, il nome dell'area di lavoro per le app è indicato come il proprietario.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>La connessione ai servizi di terze parti in nuove aree di lavoro

Nell'esperienza delle nuove aree di lavoro sono state apportate modifiche per concentrarsi sulle *app*. Le app per i servizi di terze parti semplificano il recupero dei dati dai servizi che usano, ad esempio Microsoft Dynamics CRM, Salesforce o Google Analytics.

Nella nuova esperienza dell'area di lavoro, è possibile creare o usare pacchetti di contenuto aziendali. È invece possibile usare le app fornite per connettersi a servizi di terze parti o chiedere ai team interni di fornire le app per gli eventuali pacchetti di contenuto in uso. 

## <a name="give-access-to-your-workspace"></a>Concedere l'accesso all'area di lavoro

1. Nell'elenco del contenuto dell'area di lavoro, perché sei un amministratore è una nuova azione, di visualizzare **accesso**.

    ![Elenco di contenuto di aree di lavoro](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. Selezionare **Accesso**.

1. Aggiungere a queste aree di lavoro gruppi di sicurezza, liste di distribuzione, gruppi di Office 365 o singoli utenti come membri, collaboratori o amministratori. Per una spiegazione dei diversi ruoli disponibili, vedere [Ruoli nelle nuove aree di lavoro](service-new-workspaces.md#roles-in-the-new-workspaces).

    ![Aggiunta di membri, amministratori, collaboratori alle aree di lavoro](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Selezionare **Aggiungi** > **Chiudi**.


## <a name="distribute-an-app"></a>Distribuire un'app

Se si desidera distribuire il contenuto ufficiale a un ampio all'interno dell'organizzazione, è possibile pubblicare un'app dall'area di lavoro.  Quando il contenuto è pronto, si scegliere quali dashboard e report da pubblicare e quindi pubblicarlo come un *app*. È possibile creare un'app da ogni area di lavoro.

Informazioni su [pubblicazione di un'app da nuove aree di lavoro](service-create-distribute-apps.md)

## <a name="next-steps"></a>Passaggi successivi
* Informazioni su [organizzazione lavoro nella nuova esperienza di aree di lavoro in Power BI](service-new-workspaces.md)
* [Creare aree di lavoro classici](service-create-workspaces.md)
* [Pubblicare un'app da nuove aree di lavoro in Power BI](service-create-distribute-apps.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
