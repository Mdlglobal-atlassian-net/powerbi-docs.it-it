---
title: Condividere i dashboard e i report di Power BI con i colleghi e con altri utenti
description: Come condividere dashboard e report di Power BI con i colleghi all'interno e all'esterno dell'organizzazione e cosa bisogna sapere sulla condivisione.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: cb4fdeeea228d388197c35c69d934c0bf04c8033
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374710"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Condividere i dashboard e i report di Power BI con i colleghi e con altri utenti
La *condivisione* è un approccio valido per consentire ad alcuni utenti di accedere ai dashboard e ai report. Power BI offre anche [diversi altri modi per collaborare a dashboard e report e distribuirli](service-how-to-collaborate-distribute-dashboards-reports.md).

![Icona Condividi in un elenco di dashboard preferiti](media/service-share-dashboards/power-bi-share-dash-report-favorites.png)

Sia che si condivida il contenuto all'interno o all'esterno dell'organizzazione, è necessaria una [licenza Power BI Pro](service-features-license-type.md). I destinatari devono anche avere licenze Power BI Pro, a meno che il contenuto sia un [capacità Premium](service-premium-what-is.md). 

È possibile condividere dashboard e report dalla maggior parte delle posizioni nel servizio Power BI: Preferiti, recenti, condivisi con l'utente corrente (se il proprietario lo consente), area di lavoro personale o altre aree di lavoro. Quando si condivide un dashboard o un report, gli utenti che lo condividono possono visualizzarlo e interagire con esso, ma non modificarlo. Essi vedranno gli stessi dati che l'utente vede nei dashboard o nei report, a meno che non sia stata applicata la [sicurezza a livello di riga](service-admin-rls.md). I colleghi con cui si condivide il dashboard possono anche condividerlo con i loro colleghi, se sono autorizzati a tale scopo. Gli utenti all'esterno dell'organizzazione possono anche visualizzano e interagiscano con il dashboard o report, ma non condividono. 

È anche possibile [condividere un dashboard da una delle app Power BI per dispositivi mobili](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md). Tuttavia, non è possibile condividere i dashboard di Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Video: Condividere un dashboard
Il video seguente mostra come condividere il dashboard con i colleghi all'interno e all'esterno dell'azienda. Seguire quindi tutte le istruzioni riportate sotto il video per provare a farlo da soli.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Condividere un dashboard o un report

1. In un elenco di dashboard o report o in un dashboard o report aperto, selezionare **Condividi** ![Icona Condividi](media/service-share-dashboards/power-bi-share-icon.png).

2. Nella casella superiore, immettere gli indirizzi di posta elettronica completi di singoli utenti, gruppi di distribuzione o gruppi di sicurezza. Non è possibile condividere con le liste di distribuzione dinamiche. 
   
   È possibile condividere con utenti con indirizzi esterni all'organizzazione, ma verrà visualizzato un avviso.
   
   ![Avviso relativo alla condivisione esterna](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >La casella di input supporta al massimo 100 utenti o gruppi. Se si desidera condividere con un numero elevato di utenti, è consigliabile creare il dashboard in un'area di lavoro e [distribuirla come app](service-create-distribute-apps.md).
   > 
   > 


3. Aggiungere un messaggio, se si vuole. È facoltativo.
4. Per consentire ai collaboratori di condividere il contenuto con altri utenti, selezionare **Consenti ai destinatari di condividere i dashboard (o report)** .
   
   Il consenso alla condivisione da parte di altri utenti è definito *ricondivisione*. Se li autorizzi, gli utenti possono ricondividere dal servizio Power BI e dalle app per dispositivi mobili oppure possono inoltrare l'invito tramite posta elettronica ad altri utenti dell'organizzazione. L'invito scade dopo un mese. Gli utenti esterni all'organizzazione non possono ricondividere il dashboard. Il proprietario del contenuto può disattivare la ricondivisione o revocarla per singoli utenti. Visualizzare [interrompere la condivisione o impedire ad altri utenti la condivisione da](#stop-sharing-or-stop-others-from-sharing).

5. Seleziona **Condividi**.
   
   ![Selezionare il pulsante Condividi](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI invia un invito tramite posta elettronica per utenti singoli, ma non ai gruppi, con un collegamento al contenuto condiviso. Verrà visualizzata una notifica **Operazione riuscita**. 
   
   Quando i destinatari nell'organizzazione fanno clic sul collegamento, Power BI aggiunge il dashboard o il report alla rispettiva pagina elenco **Condivisi con l'utente corrente**. Infine, potranno selezionare il nome del mittente per visualizzare tutto il contenuto condiviso. 
   
   ![Pagina elenco Condivisi con l'utente corrente](media/service-share-dashboards/power-bi-shared-with-me-dashboards-reports.png)
   
   Quando i destinatari esterni all'organizzazione fanno clic sul collegamento, possono visualizzare il dashboard o il report, ma non nel consueto portale di Power BI. Per altre informazioni, vedere [condividere un dashboard o report con utenti esterni all'organizzazione](#share-a-dashboard-or-report-with-people-outside-your-organization).

## <a name="who-has-access-to-a-dashboard-or-report-you-shared"></a>Utenti autorizzati ad accedere al dashboard o al report condiviso
In alcuni casi è necessario visualizzare gli utenti si è condiviso e vedere chi sono condivisi con:

1. Nell'elenco di dashboard o report oppure nel dashboard o report stesso selezionare **Condividi** ![Icona Condividi](media/service-share-dashboards/power-bi-share-icon.png). 
2. Nel **Condividi dashboard** oppure **condividere report** nella finestra di dialogo **accesso**.
   
    ![Finestra di dialogo Condividi dashboard, scheda Accesso](media/service-share-dashboards/power-bi-share-dialog-access.png)

    Gli utenti esterni all'organizzazione sono indicati come **Guest**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Interrompere la condivisione o impedire la condivisione da parte di altri utenti
Solo il proprietario del dashboard o del report può attivare e disattivare la ricondivisione.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Se l'invito per la condivisione non è stato ancora inviato
* Cancella il **Consenti ai destinatari di condividere i dashboard (o report)** casella di controllo nella parte inferiore dell'invito prima di inviarlo.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Se il dashboard o il report è già stato condiviso
1. Nell'elenco di dashboard o report oppure nel dashboard o report stesso selezionare **Condividi** ![Icona Condividi](media/service-share-dashboards/power-bi-share-icon.png). 
2. Nel **Condividi dashboard** oppure **condividere report** nella finestra di dialogo **accesso**.
   
    ![Finestra di dialogo Condividi dashboard, scheda Accesso](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Fare clic sui puntini di sospensione ( **...** ) accanto a **Lettura e ricondivisione** e selezionare:
   
   ![Puntini di sospensione Lettura e ricondivisione](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Lettura** per evitare che l'utente condivida il dashboard con altri utenti.
   * **Rimuovi accesso** per impedire all'utente di visualizzare il contenuto condiviso.

4. Nel **rimuovere l'accesso** dialogo casella, decidere se si desidera anche rimuovere l'accesso al contenuto correlato, ad esempio report e set di dati. Se si rimuove gli elementi con un'icona di avviso ![icona di avviso di Power BI](media/service-share-dashboards/power-bi-warning-icon.png), è consigliabile anche rimuovere contenuto correlato, poiché non viene visualizzata correttamente.

    ![Finestra di dialogo di avviso di condivisione di Power BI](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-with-people-outside-your-organization"></a>Condividere un dashboard o un report con utenti esterni all'organizzazione
Quando si condivide con utenti esterni all'organizzazione, riceve un messaggio di posta elettronica con un collegamento al dashboard condiviso o report, è necessario accedere a Power BI per visualizzare. Se non dispongono di una licenza Power BI Pro, possono richiederla facendo clic sul collegamento.

Dopo l'accesso, viene visualizzato il dashboard o report condiviso nella finestra del browser separata, non nel consueto portale di Power BI. Per accedere in seguito a questo dashboard o report, si deve aggiungere un segnalibro il collegamento.

Non possono modificare il contenuto del dashboard o report. Anche se è possibile interagire con i grafici e modificare filtri o sezionamenti, questi non possono salvare le modifiche. 

Il dashboard o il report condiviso è visibile solo per i destinatari diretti. Ad esempio, se è stato inviato il messaggio a Vicki@contoso.com, solo Vicki può visualizzare il dashboard. Nessun utente può visualizzare il dashboard, anche se dispongono di collegamento. Vicki deve usare lo stesso indirizzo di posta elettronica per accedervi; Se effettua l'iscrizione con un altro indirizzo di posta elettronica, potrà accedere al dashboard.

Gli utenti esterni all'organizzazione non possono visualizzare i dati se è implementata la sicurezza a livello di ruolo o di riga nei modelli tabulari di Analysis Services in locale.

Se si invia un collegamento da un'app di Power BI per dispositivi mobili a persone all'esterno dell'organizzazione, selezionando il collegamento viene aperto il dashboard in un browser, non nell'app per dispositivi mobili di Power BI.

Se si [consentire agli utenti guest esterni di modificare e gestire contenuto all'interno dell'organizzazione](service-admin-portal.md#export-and-sharing-settings), l'esperienza predefinita solo consumo non è applicabile ad essi. [Altre informazioni](service-admin-azure-ad-b2b.md)

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Aspetti da tenere presenti per la condivisione di dashboard e report:

* In generale, i dati visualizzati nel dashboard o nel report sono gli stessi sia per l'utente che per i relativi colleghi. Quindi, se un utente dispone delle autorizzazioni per visualizzare una maggior quantità di dati rispetto ai colleghi, questi ultimi potranno visualizzare tutti i dati presenti nel dashboard o nel report. Tuttavia, se la [sicurezza a livello di riga](service-admin-rls.md) viene applicata al set di dati sottostante di un dashboard o un report, vengono usate le credenziali di ogni persona per determinare a quali dati può accedere.
* Tutti gli utenti si condivide il dashboard possono visualizzarlo e interagire con i report correlati nella [visualizzazione di lettura](consumer/end-user-reading-view.md#reading-view). Non possono creare report o salvare le modifiche apportate a report esistenti.
* Sebbene nessuno può visualizzare o scaricare il set di dati, può accedere al set di dati direttamente usando l'analizza nella funzionalità di Excel. Un amministratore può limitare la possibilità di usare analizza in Excel per tutti gli utenti in un gruppo. Tuttavia, la restrizione riguarda tutti gli utenti in tale gruppo per ogni area di lavoro a cui appartiene al gruppo.
* Tutti gli utenti possono [aggiornare manualmente i dati](refresh-data.md).
* Se si usa Office 365 per la posta elettronica, è possibile condividere con i membri di un gruppo di distribuzione immettendo l'indirizzo di posta elettronica associato a quel gruppo.
* I colleghi che condividono il dominio di posta elettronica e quelli che usano il cui dominio è diverso ma registrato nel medesimo tenant può condividere il dashboard con altri utenti. Ad esempio, se i domini contoso.com e Contoso2.com siano stati registrati nel tenant stesso e indirizzo di posta elettronica viene konrads@contoso.com, quindi entrambi ravali@contoso.com e gustav@contoso2.com condivisibile, purché dispongano dell'autorizzazione per condividere.
* Se i colleghi hanno già accesso a un dashboard specifico o un report, è possibile inviare un collegamento diretto copiandone l'URL quando ci si trova il dashboard o report. Ad esempio: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* Analogamente, se i colleghi hanno già accesso a un dashboard specifico, è possibile [inviare un collegamento diretto al report sottostante](service-share-reports.md). 
* È possibile condividere con, al massimo, 100 utenti o gruppi in un'azione singola condivisione. Si può però consentire l'accesso a un elemento a più di 500 utenti. A tale scopo, condividere più volte specificando gli utenti singolarmente o condividere con un gruppo di utenti contenente tutti gli utenti.

## <a name="troubleshoot-sharing"></a>Risolvere i problemi di condivisione

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>I destinatari del dashboard visualizzano un'icona a forma di lucchetto in un riquadro o un messaggio di "Autorizzazione obbligatoria"

È possibile che gli utenti con cui si condivide il dashboard vedano un riquadro bloccato in un o un messaggio di "Autorizzazione obbligatoria" quando provano a visualizzare un report.

![Riquadro bloccato di Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

In questo caso, è necessario concedere loro le autorizzazioni per il set di dati sottostante:

1. Passare alla scheda **Set di dati** nell'elenco del contenuto.

1. Selezionare i puntini di sospensione ( **...** ) accanto al set di dati, quindi selezionare **gestire le autorizzazioni**.

    ![Gestione delle autorizzazioni](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Selezionare **Aggiungi utente**.

    ![Selezionare Aggiungi utente](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Immettere gli indirizzi di posta elettronica completi di singoli utenti, gruppi di distribuzione o gruppi di sicurezza. Non è possibile condividere con le liste di distribuzione dinamiche.

    ![Aggiungere gli indirizzi di posta elettronica](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Selezionare **Aggiungi**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Non è possibile condividere un dashboard o un report

Per condividere un dashboard o report, necessaria l'autorizzazione per ricondividere il contenuto sottostante. vale a dire, le relative relazioni e i set di dati. Se viene visualizzato un messaggio che informa che non è possibile condividere, chiedere all'autore di report per concedere ricondividere il dashboard dell'autorizzazione per tali report e set di dati.

![Messaggio "Non è possibile condividere"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Passaggi successivi
* Per inviare suggerimenti, passare al [sito della community di Power BI](https://community.powerbi.com/).
* [Come si condividono i dashboard e i report e in che modo ci si collabora?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Condividere un report di Power BI filtrato](service-share-reports.md).
* Domande? [Provare la community di Power BI](http://community.powerbi.com/).

