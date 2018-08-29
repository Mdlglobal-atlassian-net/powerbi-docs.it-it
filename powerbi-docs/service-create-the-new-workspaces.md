---
title: Creare le nuove aree di lavoro (anteprima) - Power BI
description: Informazioni su come creare le nuove aree di lavoro, ovvero raccolte di dashboard e report creati per fornire all'organizzazione le metriche strategiche.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/24/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: cde28e7c41a35c3bbc37d0da56313ad7f8698110
ms.sourcegitcommit: 15b877343540bb7e21f1d5bbd3d6f64e66fa138c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42914520"
---
# <a name="create-the-new-workspaces-preview-in-power-bi"></a>Creare le nuove aree di lavoro (anteprima) in Power BI

Power BI ha introdotto una nuova esperienza dell'area di lavoro in anteprima. Le aree di lavoro consentono di collaborare con i colleghi per creare raccolte di dashboard e report che possono quindi essere aggregate in *app* e distribuite all'intera organizzazione o a gruppi o utenti specifici. 

![Nuove aree di lavoro in anteprima di Power BI](media/service-create-the-new-workspaces/power-bi-new-workspaces-preview.png)

Con le nuove aree di lavoro in anteprima è possibile:

- Assegnare ruoli dell'area di lavoro a gruppi di utenti: gruppi di sicurezza, liste di distribuzione, gruppi di Office 365 e singoli utenti.
- Creare un'area di lavoro in Power BI senza creare un gruppo di Office 365.
- Usare ruoli dell'area di lavoro con maggiore granularità per aumentare la flessibilità di gestione delle autorizzazioni in un'area di lavoro.
 
Quando si crea una delle nuove aree di lavoro, non si crea un gruppo di Office 365 sottostante associato. Tutta l'amministrazione dell'area di lavoro viene gestita da Power BI e non da Office 365. È comunque possibile aggiungere un gruppo di Office 365 all'area di lavoro per continuare a gestire l'accesso degli utenti al contenuto tramite i gruppi di Office 365. Tuttavia, è anche possibile usare gruppi di sicurezza, liste di distribuzione e aggiungere singoli utenti direttamente in Power BI in modo da gestire con maggiore flessibilità l'accesso all'area di lavoro. Dato che l'amministrazione dell'area di lavoro avviene ora in Power BI, gli amministratori di Power BI decidono chi può creare aree di lavoro in un'organizzazione. Vedere la [sezione Aree di lavoro dell'articolo sul portale di amministrazione di Power BI](service-admin-portal.md#workspace-settings) per informazioni dettagliate. 

I gruppi di utenti o i singoli utenti vengono aggiunti alle nuove aree di lavoro come membri, collaboratori o amministratori. A tutti i membri in un gruppo di utenti viene assegnato il ruolo definito. Se un utente singolo appartiene a più gruppi di utenti, ottiene il livello di autorizzazione più elevato specificato dal ruolo.  Per una spiegazione dei diversi ruoli disponibili, vedere [Ruoli nelle nuove aree di lavoro](#roles-in-the-new-workspaces) più avanti in questo articolo.

Tutti gli utenti che vengono aggiunti a un'area di lavoro per le app devono possedere una licenza di Power BI Pro. Nell'area di lavoro tutti gli utenti possono collaborare sui dashboard e i report che si intende pubblicare e rendere disponibili a un pubblico più ampio o all'intera organizzazione. Per distribuire contenuto ad altri utenti all'interno dell'organizzazione, è possibile assegnare loro licenze di Power BI Pro oppure assegnare l'area di lavoro a una capacità Power BI Premium.

Con le nuove aree di lavoro, alcune funzionalità sono state riprogettate. Vedere [Funzionalità delle aree di lavoro per le app che funzionano in modo diverso](#app-workspace-features-that-work-differently) più avanti in questo articolo per una spiegazione delle modifiche dell'anteprima che verranno mantenute definitivamente. Poiché questa è una funzionalità in anteprima, sono previste alcune limitazioni di cui è necessario tenere conto. Vedere [Problemi noti](#known-issues) più avanti in questo articolo per una spiegazione delle limitazioni correnti. 

## <a name="roll-out-new-app-workspaces"></a>Implementare le nuove aree di lavoro per le app

Durante il periodo di anteprima, è possibile creare e usare sia le aree di lavoro nuove che quelle precedenti. Al termine dell'anteprima per le nuove aree di lavoro, quando queste diventeranno disponibili a livello generale, sarà possibile usare le aree di lavoro precedenti ancora per qualche tempo. Non sarà tuttavia possibile crearne di nuove e sarà necessario preparare la migrazione delle aree di lavoro all'infrastruttura delle nuove aree di lavoro. Non c'è di che preoccuparsi, saranno disponibili vari mesi per completare la migrazione.

## <a name="create-one-of-the-new-app-workspaces"></a>Creare una delle nuove aree di lavoro per le app

1. Iniziare creando l'area di lavoro per le app. Selezionare **Aree di lavoro** > **Creare un'area di lavoro per le app**.
   
     ![Crea un'area di lavoro per le app](media/service-create-workspaces/power-bi-create-app-workspace.png)

2. In **Anteprima aree di lavoro migliorate** selezionare **Prova adesso**.
   
     ![Anteprima delle aree di lavoro migliorate](media/service-create-workspaces/power-bi-preview-improved-workspaces.png)

2. Assegnare un nome all'area di lavoro. Se il nome non è disponibile, modificarlo in modo da ottenere un ID univoco.
   
     All'app sarà assegnato lo stesso nome dell'area di lavoro.
   
1. Se si vuole, è possibile aggiungere un'immagine. Le dimensioni massime del file non possono superare 45 kB.
 
    ![Assegnare un nome all'area di lavoro e aggiungere un'immagine](media/service-create-workspaces/power-bi-name-workspace.png)

1. Selezionare **Salva**.

    Nella schermata di **Benvenuto** della nuova area di lavoro, sarà possibile aggiungere i dati. 

    ![Schermata di benvenuto della nuova area di lavoro](media/service-create-workspaces/power-bi-workspace-welcome-screen.png)

1. Ad esempio, selezionare **Esempi** > **Esempio di analisi della redditività dei clienti**.

    Nell'elenco del contenuto dell'area di lavoro, è visualizzata l'opzione **Anteprima nuove aree di lavoro**. Poiché l'utente è un amministratore, è visualizzata anche una nuova azione, **Accesso**.

    ![Elenco del contenuto dell'anteprima aree di lavoro](media/service-create-workspaces/power-bi-workspaces-preview-content-list.png)

1. Selezionare **Accesso**.

1. Aggiungere a queste aree di lavoro gruppi di sicurezza, liste di distribuzione, gruppi di Office 365 o singoli utenti come membri, collaboratori o amministratori. Per una spiegazione dei diversi ruoli disponibili, vedere [Ruoli nelle nuove aree di lavoro](#roles-in-the-new-workspaces) più avanti in questo articolo.

    ![Aggiunta di membri, amministratori, collaboratori alle aree di lavoro](media/service-create-workspaces/power-bi-access-add-members.png)

9. Selezionare **Aggiungi** > **Chiudi**.

1. Power BI crea l'area di lavoro, che verrà aperta e visualizzata nell'elenco delle aree di lavoro di cui si è membri. Gli amministratori potranno a questo punto selezionare i puntini di sospensione (…) per tornare indietro e apportare modifiche alle impostazioni dell'area di lavoro, aggiungere nuovi membri o modificarne le autorizzazioni.

     ![Modificare le impostazioni e l'accesso per un'area di lavoro](media/service-create-workspaces/power-bi-edit-workspace.png)

## <a name="add-content-to-your-app-workspace"></a>Aggiungere contenuto all'area di lavoro per le app

Dopo aver creato un'area di lavoro per le app con il nuovo stile, è possibile aggiungere il contenuto. L'aggiunta del contenuto nelle nuove aree di lavoro funziona come per quelle precedenti, con una sola eccezione. All'interno dell'area di lavoro per le app è possibile caricare o connettersi ai file proprio come avviene nell'Area di lavoro personale. Nelle nuove aree di lavoro non è tuttavia possibile connettersi ai pacchetti di contenuto aziendali o pacchetti di contenuto di terze parti, ad esempio Microsoft Dynamics CRM, Salesforce o Google Analytics. Nelle aree di lavoro correnti è possibile connettersi a pacchetti di contenuto.

Quando si visualizza il contenuto in un'area di lavoro per le app, il nome dell'area di lavoro per le app è indicato come il proprietario.

### <a name="connecting-to-third-party-services-in-new-workspaces-preview"></a>Connessione a servizi di terze parti nelle nuove aree di lavoro (anteprima)

Nell'esperienza delle nuove aree di lavoro sono state apportate modifiche per concentrarsi sulle app. Le app per i servizi di terze parti semplificano il recupero dei dati dai servizi che usano, ad esempio Microsoft Dynamics CRM, Salesforce o Google Analytics.
Le app aziendali forniscono agli utenti i dati interni di cui hanno bisogno. È prevista l'aggiunta di funzionalità alle app aziendali per consentire agli utenti di personalizzare il contenuto trovato nelle app. In questo modo, i pacchetti di contenuto non saranno più necessari. 

Con l'anteprima delle nuove aree di lavoro, non è possibile creare o utilizzare pacchetti di contenuto aziendali. È invece possibile usare le app fornite per connettersi a servizi di terze parti o chiedere ai team interni di fornire le app per gli eventuali pacchetti di contenuto in uso. 

## <a name="roles-in-the-new-workspaces"></a>Ruoli nelle nuove aree di lavoro

I ruoli consentono di gestire chi può fare cosa in un'area di lavoro per permettere ai team di collaborare. Le nuove aree di lavoro consentono di assegnare ruoli a singoli utenti e gruppi di utenti: gruppi di sicurezza, gruppi di Office 365 e liste di distribuzione. 

Quando si assegnano i ruoli a un gruppo di utenti, i singoli utenti del gruppo possono accedere al contenuto. Se si annidano gruppi di utenti, tutti gli utenti contenuti sono autorizzati. Un utente incluso in più gruppi di utenti con ruoli diversi ottiene il livello più elevato dell'autorizzazione concessa. 

Nelle nuove aree di lavoro sono disponibili tre ruoli: amministratori, membri e collaboratori.

**Gli amministratori possono:**

- Aggiornare ed eliminare l'area di lavoro. 
- Aggiungere/rimuovere utenti, inclusi altri amministratori.
- Eseguire tutte le operazioni che possono eseguire i membri.

**I membri possono:** 

- Aggiungere membri o altri utenti con autorizzazioni inferiori.
- Pubblicare e aggiornare un'app.
- Condividere un elemento o condividere un'app.
- Consentire ad altri utenti di ricondividere a loro volta gli elementi.
- Eseguire tutte le operazioni che possono eseguire i collaboratori.


**I collaboratori possono:** 

- Creare, modificare ed eliminare contenuto nell'area di lavoro. 
- Pubblicare report nell'area di lavoro, eliminare contenuto.
- Non possono concedere l'accesso al contenuto a nuovi utenti. Non possono condividere nuovo contenuto ma possono condividere con utenti con cui l'area di lavoro, l'elemento o l'app è già condivisa. 
- Non possono modificare i membri del gruppo.
 
È in corso la creazione di flussi di richiesta di accesso nel servizio, affinché gli utenti che non hanno accesso possano richiederlo. I flussi di lavoro di richiesta di accesso sono attualmente disponibili per dashboard, report e app.

## <a name="distribute-an-app"></a>Distribuire un'app

Quando il contenuto è pronto, è possibile scegliere quali dashboard e report pubblicare e quindi pubblicarli come un'*app*. È possibile creare un'app da ogni area di lavoro. I colleghi possono ottenere l'app in diversi modi. Se l'amministratore di Power BI concede l'autorizzazione, è possibile installarla automaticamente nell'account Power BI dei colleghi. Altrimenti, è possibile trovare e installare l'app da Microsoft AppSource oppure è possibile inviare loro un collegamento diretto. Riceveranno gli aggiornamenti automaticamente e sarà possibile controllare la frequenza con cui vengono aggiornati i dati. Per informazioni dettagliate, vedere [Creare e pubblicare app con dashboard e report in Power BI](service-create-distribute-apps.md).

## <a name="convert-old-app-workspaces-to-new-app-workspaces"></a>Convertire le aree di lavoro per le app precedenti nelle nuove aree di lavoro per le app

Durante il periodo di anteprima, non è possibile convertire automaticamente le aree di lavoro per le app precedenti in quelle nuove. È tuttavia possibile creare una nuova area di lavoro per le app e pubblicare il contenuto nella nuova posizione. 

Quando le nuove aree di lavoro saranno disponibili a livello generale, sarà possibile scegliere di eseguire automaticamente la migrazione delle aree di lavoro precedenti. A un certo punto, una volta disponibili a livello generale, sarà comunque necessario eseguire la migrazione.

## <a name="power-bi-apps-faq"></a>Domande frequenti sulle app di Power BI

### <a name="how-are-the-new-app-workspaces-different-from-current-app-workspaces"></a>Quali sono le differenze tra le nuove aree di lavoro per le app e quelle correnti?
* La creazione di aree di lavoro per le app non crea entità corrispondenti in Office 365, come succede con le aree di lavoro correnti. Sarà comunque possibile aggiungere un gruppo di Office 365 all'area di lavoro assegnandogli un ruolo. 
* Nelle aree di lavoro per le app correnti, è possibile aggiungere solo singoli utenti agli elenchi di membri e amministratori. Nelle nuove aree di lavoro per le app, è possibile aggiungere più gruppi di sicurezza di Active Directory, liste di distribuzione o gruppi di Office 365 a questi elenchi per semplificare la gestione degli utenti. 
- È possibile creare un pacchetto di contenuto aziendale da un'area di lavoro per le app corrente. Non è possibile crearne uno dalle nuove aree di lavoro per le app.
- È possibile utilizzare un pacchetto di contenuto aziendale da un'area di lavoro per le app corrente. Non è possibile utilizzarne uno dalle nuove aree di lavoro per le app.
- Durante l'anteprima, alcune funzionalità non sono ancora abilitate per le nuove aree di lavoro per le app. Per informazioni dettagliate, vedere la sezione successiva [Altre funzionalità pianificate per le nuove aree di lavoro](service-create-the-new-workspaces.md#other-planned-new-app-workspace-preview-features).

## <a name="planned-new-app-workspace-preview-features"></a>Nuove funzionalità pianificate per l'anteprima delle nuove aree di lavoro per le app

Alcune altre funzionalità per l'anteprima delle nuove aree di lavoro per le app sono ancora in fase di sviluppo e non sono ancora pronte:

- Il pulsante **Lascia l'area di lavoro** non è disponibile.
- Le metriche di utilizzo non sono ancora supportate.
- Funzionamento del livello Premium: è possibile creare e assegnare aree di lavoro alla capacità Premium, ma per spostare un'area di lavoro tra capacità, è necessario passare alle impostazioni dell'area di lavoro.
- L'incorporamento di Web part SharePoint non è ancora supportato.
- Non è disponibile il pulsante **OneDrive** per i gruppi di Office 365 in Recupera dati/file.

## <a name="app-workspace-features-that-work-differently"></a>Funzionalità delle aree di lavoro per le app che funzionano in modo diverso

Alcune funzionalità delle nuove aree di lavoro per le app funzionano diversamente da quelle delle aree di lavoro per le app correnti. Queste differenze sono intenzionali e sono state modificate in base ai commenti e suggerimenti ricevuti dai clienti al fine di consentire un approccio più flessibile alla collaborazione con le aree di lavoro:

- Ricondivisione/Non è possibile ricondividere per i membri: funzionalità sostituita dal ruolo Collaboratore
- Aree di lavoro di sola lettura: invece di concedere agli utenti l'accesso di sola lettura a un'area di lavoro, si assegnerà agli utenti il ruolo futuro di Visualizzatore, che consente un accesso di sola lettura simile al contenuto in un'area di lavoro.

## <a name="known-issues"></a>Problemi noti

Di seguito sono riportati i problemi noti. Le correzioni corrispondenti sono in fase di sviluppo:

- Gli utenti o i gruppi di utenti del livello gratuito aggiunti come destinatari delle sottoscrizioni ai messaggi di posta elettronica potrebbero non ricevere i messaggi, anche se dovrebbero. Questo problema si verifica quando l'area di lavoro della nuova esperienza è assegnata alla capacità Premium ma l'area di lavoro personale dell'utente che crea la sottoscrizione non è assegnata a una capacità Premium. Se l'area di lavoro personale è assegnata a una capacità Premium, gli utenti e i gruppi di utenti del livello gratuito riceveranno i messaggi di posta elettronica.
- Se un'area di lavoro viene spostata da una capacità Premium a una capacità condivisa, in alcuni casi gli utenti e i gruppi di utenti del livello gratuito continueranno a ricevere i messaggi di posta elettronica anche se non dovrebbero. Questo problema si verifica quando l'area di lavoro personale dell'utente che crea la sottoscrizione è assegnata a una capacità Premium.

## <a name="next-steps"></a>Passaggi successivi

- [Creare le aree di lavoro correnti](service-create-workspaces.md)
* [Installare e usare app in Power BI](service-install-use-apps.md)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
