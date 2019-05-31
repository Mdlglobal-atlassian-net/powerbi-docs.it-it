---
title: Pubblicare un'app in Power BI
description: Informazioni su come pubblicare le nuove applicazioni, ovvero raccolte di dashboard e report con navigazione predefiniti.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941564"
---
# <a name="publish-an-app-in-power-bi"></a>Pubblicare un'app in Power BI

In Power BI, è possibile creare contenuto ufficiale incluso nel pacchetto, quindi distribuirlo a un vasto pubblico come un *app*. È possibile creare app nelle *aree di lavoro per le app*, in cui è possibile collaborare sul contenuto di Power BI con i colleghi. È quindi possibile pubblicare le app complete in ampi gruppi di persone all'interno dell'organizzazione. 

![App di Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Gli utenti aziendali spesso hanno bisogno di più dashboard e report di Power BI per l'esecuzione delle loro attività aziendali. Con le app Power BI è possibile creare raccolte di dashboard e report e pubblicare le app nell'intera organizzazione o soltanto a gruppi o utenti specifici. Per l'utente amministratore o autore del report, le app rendono più semplice gestire le autorizzazioni per queste raccolte.

Gli utenti aziendali di ottenere le App in diversi modi:

- È possibile trovare e installare l'app da Microsoft AppSource
- È possibile inviare loro un collegamento diretto.
- Se l'amministratore di Power BI concede l'autorizzazione, è possibile installarla automaticamente nell'account Power BI dei colleghi.

È possibile creare l'app con il proprio spostamento predefinita, in modo che gli utenti possono trovare facilmente arrivare attorno al contenuto. Non possono modificare il contenuto dell'app. È possibile interagire con esso nel servizio Power BI o una delle App per dispositivi mobili-: applicazione di filtri, evidenziazione e l'ordinamento dei dati stessi. Riceveranno gli aggiornamenti automaticamente e sarà possibile controllare la frequenza con cui vengono aggiornati i dati. Altre informazioni sull'[esperienza dell'app per gli utenti aziendali](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licenze per le app
Per creare o aggiornare un'app, è necessaria una licenza Power BI Pro. Per l'app *consumatore*, sono disponibili due opzioni.

* Opzione 1: tutti gli utenti aziendali devono disporre di una licenza **Power BI Pro** per visualizzare le app. 
* Opzione 2: Se l'area di lavoro di app si trova in una capacità di Power BI Premium, gli utenti gratuiti all'interno dell'organizzazione possono visualizzare il contenuto di app. Per informazioni dettagliate, leggere [What is Power BI Premium?](service-premium.md) (Che cos'è Power BI Premium?).

## <a name="publish-your-app"></a>Pubblicare l'app
Quando i dashboard e i report dell'area di lavoro sono pronti, è possibile scegliere i dashboard e i report da pubblicare e quindi pubblicarli come app. 

1. Nella visualizzazione elenco dell'area di lavoro, decidere quali dashboard e report desiderati **incluse nell'app**.

     ![Selezionare il dashboard per la pubblicazione](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se si sceglie di non includere un report che dispone di un dashboard correlato, viene visualizzato un avviso accanto al report. È comunque possibile pubblicare l'app, ma nel dashboard correlato non sarà disponibili i riquadri da tale report.

     ![Avviso sul dashboard correlato](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selezionare il **pubblica app** pulsante in alto a destra per avviare il processo di creazione e pubblicazione di un'app dall'area di lavoro.
   
     ![Pubblica app](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Sul **programma di installazione**, specificare il nome e descrizione per consentire agli utenti di trovare l'app. È possibile impostare un colore del tema per personalizzarla. È anche possibile aggiungere un collegamento a un sito di supporto.
   
     ![Crea la tua app](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Sul **navigazione**, si seleziona il contenuto verrà pubblicato come parte dell'app. È quindi possibile aggiungere app riquadro di spostamento per organizzare il contenuto nelle sezioni. Visualizzare [progettare l'esperienza di navigazione per l'app](#design-the-navigation-experience-for-your-app) in questo articolo per informazioni dettagliate.
   
     ![Spostamento di App](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Sul **accesso**, decidere chi avrà accesso all'app. 
    - Nelle [aree di lavoro classici](service-create-workspaces.md): tutti gli utenti nell'organizzazione, utenti specifici o ai gruppi di sicurezza di Azure Active Directory (AAD).
    - Nel [nuove aree di lavoro esperienza](service-create-the-new-workspaces.md): specifici utenti, gruppi di sicurezza AAD e liste di distribuzione e gruppi di Office 365.

6. Se si dispone delle autorizzazioni, è possibile installare automaticamente l'app per i destinatari. Un amministratore di Power BI può abilitare questa impostazione nel portale di amministrazione di Power BI. Altre informazioni, vedere [installazione di un'app automaticamente](#automatically-install-apps-for-end-users) in questo articolo.

     ![Autorizzazioni delle app](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Quando si seleziona **pubblica app**, vedrai un messaggio di conferma è pronto per la pubblicazione. Nel **Condividi questa app** nella finestra di dialogo è possibile copiare l'URL che è un collegamento diretto a questa app.
   
     ![Fine dell'app](media/service-create-distribute-apps/power-bi-apps-success.png)

È possibile inviare che un collegamento diretto alle persone è stato condiviso con, o sono disponibili le app nella scheda App visitando **Scarica ed Esplora altre app da AppSource**. Altre informazioni sull'[esperienza dell'app per gli utenti aziendali](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Modificare l'app pubblicata
Dopo aver pubblicato l'app, si potrebbe volerla modificare o aggiornare. È facile aggiornarla se è un amministratore o membro nella nuova area di lavoro di app. 

1. Aprire l'area di lavoro per le app che corrisponde all'app. 
   
     ![Apri area di lavoro](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Apportare le modifiche desiderate al dashboard o report.
 
     L'area di lavoro per le app è l'area di gestione temporanea personale, quindi le modifiche nell'app non vengono eseguite in tempo reale fino a quando non si pubblica di nuovo l'app. Ciò consente di apportare modifiche senza influire sulle app pubblicate.  
 
    > [!IMPORTANT]
    > Se si rimuove un report e aggiornare l'app, anche se si aggiungono report tornare all'app, i tuoi utenti app perdano tutte le personalizzazioni, ad esempio i segnalibri, commenti e così via.  
 
3. Tornare all'elenco dell'area di lavoro di app del contenuto e selezionare **Aggiorna app** nell'angolo superiore destro.
   
1. Update **programma di installazione**, **navigazione**, e **autorizzazioni**, se è necessario, quindi selezionare **Aggiorna app**.
   
Le persone per cui è stata pubblicata l'app visualizzano automaticamente la versione aggiornata dell'app. 

## <a name="design-the-navigation-experience-for-your-app"></a>Progettare l'esperienza di navigazione per l'app
Il **nuovo generatore di navigazione** opzione consente di compilare una navigazione personalizzata per l'app. Riquadro di spostamento personalizzato rende più semplice per gli utenti di trovare e utilizzare contenuto nell'app. Le app esistenti hanno questa opzione è disattivata e nuovo valore predefinito di App per l'opzione si trova in.

Quando l'opzione è disattivata, è possibile selezionare il **pagina di destinazione di App** essere **contenuti specifici**, ad esempio un dashboard o report oppure selezionare **None** per visualizzare un elenco di base di contenuto all'utente.

Quando si attivano **nuovo generatore di navigazione**, è possibile progettare una navigazione personalizzata. Per impostazione predefinita sono elencati tutti i report, dashboard e cartelle di lavoro di Excel che incluso nell'app come un elenco semplice. 

![Spostamento di App](media/service-create-distribute-apps/power-bi-apps-navigation.png)

È possibile personalizzare ulteriormente la navigazione di app per:
* Riordinare gli elementi utilizzando la freccia GIÙ / freccia giù. 
* Ridenominazione di elementi nel **segnalare i dettagli**, **i dettagli del Dashboard**, e **dettagli cartella di lavoro**.
* Nascondere determinati elementi dal riquadro di spostamento.
* Usando il **New** opzione per aggiungere **sezioni** al gruppo contenuto correlato.
* Usando il **New** opzione per aggiungere un **collegamento** a una risorsa esterna al riquadro di spostamento a sinistra. 

Quando si aggiunge un **collegamento**, nel **collegare dettagli** è possibile scegliere in cui viene aperto il collegamento. Per impostazione predefinita i collegamenti aperti nel **scheda corrente**, ma è possibile selezionare **nuova scheda**, o **area di contenuto**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Considerazioni sull'uso la nuova opzione di generatore di navigazione
Di seguito sono aspetti generali da tenere presenti quando si usa il nuovo generatore di navigazione:
* Le pagine del report vengono visualizzate nell'area di navigazione app come una sezione espandibile
* Se si disattiva il nuovo generatore di spostamento e quindi pubblicare o aggiornare l'app, si perdono le personalizzazioni apportate. Ad esempio, vengono persi tutte le sezioni, ordinamento, collegamenti e i nomi personalizzati per gli elementi di navigazione.

Quando si aggiungono collegamenti per l'esplorazione di app, selezionando l'opzione area di contenuto:
* Verificare che il collegamento può essere incorporato. Alcuni servizi di bloccare l'incorporamento dei propri contenuti nei siti di terze parti, come Power BI.
* Non è supportato l'incorporamento di contenuto del servizio Power BI, ad esempio report o dashboard in altre aree di lavoro. 
* Il Server di Report di Power BI incorpora il contenuto tramite nativo incorporare il contenuto di URL da una distribuzione locale. Usare la procedura descritta in [creazione di URL Server di Report di Power BI](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) per ottenere l'URL. Tenere presente che si applicano le regole di autenticazione regolari, in modo da visualizzare il contenuto richiede una connessione VPN al server in locale. 
* Nella parte superiore del contenuto incorporato viene visualizzato un avviso di sicurezza per indicare che il contenuto non è in Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Installare automaticamente le app per gli utenti finali
Se un amministratore concede le autorizzazioni, è possibile installare App automaticamente *push* li agli utenti finali. Questa funzionalità push rende più semplice distribuire le app corrette alle persone a destra o dei gruppi. L'app viene visualizzata automaticamente nell'elenco di contenuto App degli utenti finali. Non dispongono di trovarlo da Microsoft AppSource o seguire un collegamento di installazione. Vedere come gli amministratori di abilitano [il push delle App agli utenti finali](service-admin-portal.md#push-apps-to-end-users) nell'articolo del portale di amministrazione di Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Come eseguire il push di un'app automaticamente per gli utenti finali
Dopo che l'amministratore ha assegnato le autorizzazioni, sarà disponibile una nuova opzione per **installare automaticamente l'app**. Quando si la casella di controllo e si sceglie **pubblica app** (o **Aggiorna app**), l'app viene eseguito il push a tutti gli utenti o gruppi definiti nel **autorizzazioni** sezione dell'app nel **Accesso** scheda.

![Abilitare il push delle app](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Modalità di recupero delle App che si esegue il push a tali utenti
Dopo aver effettuato push un'app, viene visualizzato nel relativo elenco di App automaticamente. In questo modo, è possibile curare le app che determinati utenti o ruoli lavorativi alle esigenze dell'organizzazione per avere a portata di mano.

![Abilitare il push delle app](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considerazioni per l'installazione automatica delle app
Ecco alcuni aspetti da tenere in considerazione quando si effettua il push delle app agli utenti finali:

* L'installazione automatica di un'app per gli utenti può richiedere tempo. La maggior parte delle App install immediatamente per gli utenti, ma il push delle App può richiedere tempo.  Dipende dal numero di elementi nell'app e dal numero di utenti a cui viene consentito l'accesso. Si consiglia di effettuare il push delle app durante le ore non lavorative con molto anticipo prima che siano necessarie agli utenti. Prima di inviare una comunicazione generale sulla disponibilità delle app, eseguire una verifica con più utenti.

* Aggiornare il browser. Prima di visualizzare l'app di cui è stato effettuato il push nell'elenco App, l'utente potrebbe dover aggiornare o chiudere e riaprire il browser.

* Se gli utenti non vedono immediatamente l'app nell'elenco di App, si deve aggiornare o chiudere e riaprire il browser.

* Cercare di non sovraccaricare gli utenti. Prestare attenzione a non effettuare il push di troppe app in modo che gli utenti capiscano che le app preinstallate sono utili. È consigliabile controllare chi può effettuare il push delle app agli utenti finali per coordinare i tempi. Stabilire un punto di contatto per il recupero delle App nell'organizzazione il push agli utenti finali.

* Gli utenti guest che non hanno ancora accettato l'invito non ottengono le app installate automaticamente.  

## <a name="unpublish-an-app"></a>Annullare la pubblicazione di un'app
Qualsiasi membro di un'area di lavoro per le app può annullare la pubblicazione dell'app.

>[!IMPORTANT]
>Quando si annulla la pubblicazione di un'app, gli utenti dell'app perdono le loro personalizzazioni. Perdono eventuali segnalibri personali, commenti o sottoscrizioni associate al contenuto dell'app. Annullare la pubblicazione di un'app solo se è necessario rimuoverla.
> 
> 

* In un'area di lavoro per le app, selezionare i punti di sospensione ( **...** ) nell'angolo superiore destro > **Annulla pubblicazione app**.
  
     ![Annulla pubblicazione app](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Questa azione disinstalla l'app per tutti gli utenti a cui è stata pubblicata, i quali non potranno più accedervi. Non verranno eliminati l'area di lavoro per le app o il relativo contenuto.

## <a name="view-your-published-app"></a>Visualizzare l'app pubblicata

Quando gli utenti di app apre l'app, vengono visualizzati la navigazione che è stato creato, anziché il riquadro di spostamento a sinistra di Power BI standard. Lo spostamento di app sono elencati i report e dashboard nelle sezioni che sono state definite. Sono inoltre indicate le singole pagine in ogni report, piuttosto che solo il nome del report.

![App con spostamento](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Passaggi successivi
* [Creare un'area di lavoro per le app](service-create-workspaces.md)
* [Installare e usare app in Power BI](consumer/end-user-apps.md)
* [App Power BI per dispositivi esterni](service-connect-to-services.md)
* [Portale di amministrazione di Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
