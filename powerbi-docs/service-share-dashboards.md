---
title: Condividere i dashboard con i colleghi e con altri utenti - Power BI
description: Come condividere i dashboard di Power BI con i colleghi all'interno e all'esterno dell'organizzazione e cosa bisogna sapere sulla condivisione.
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: monitoring
qualitydate: 08/14/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 0b50568e49df8e2594519028b90d5d833d17c6b7
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="share-your-power-bi-dashboards-with-coworkers-and-others"></a>Condividere i dashboard di Power BI con i colleghi e con altri utenti
La *condivisione* è un approccio valido per consentire ad alcuni utenti di accedere ai dashboard e ai report. Power BI offre [diversi modi per collaborare all'elaborazione dei dashboard e distribuirli](service-how-to-collaborate-distribute-dashboards-reports.md). La condivisione è solo uno di essi.

![Icona Condividi in un elenco di dashboard](media/service-share-dashboards/power-bi-share-dash.png)

Sia che si condivida il contenuto all'interno o all'esterno dell'organizzazione, l'utente e i destinatari necessitano di una [licenza Power BI Pro](service-free-vs-pro.md). In caso contrario, il contenuto deve avere una [capacità Premium](service-premium.md). Se si hanno suggerimenti, il team di Power BI è sempre lieto di ricevere commenti da parte degli utenti, tramite il [sito della community di Power BI](https://community.powerbi.com/).

È possibile condividere un dashboard dall'area di lavoro personale o da un'area di lavoro per le app. Quando si condivide un dashboard, gli utenti che lo condividono possono visualizzarlo e interagire con esso, ma non possono modificarlo. Essi vedranno gli stessi dati che l'utente vede nei dashboard e nei report, a meno che non sia stata applicata la [sicurezza a livello di riga](service-admin-rls.md). I colleghi con cui si condivide il dashboard possono condividerlo con i loro colleghi, se vengono autorizzati a tale scopo. Quelli all'esterno dell'organizzazione possono visualizzare il dashboard e interagire con esso, ma non condividerlo. 

È anche possibile [condividere un dashboard da una delle app Power BI per dispositivi mobili](mobile-share-dashboard-from-the-mobile-apps.md). È possibile condividere i dashboard dal servizio Power BI e dalle app Power BI per dispositivi mobili, ma non da Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Video: Condividere un dashboard
Il video seguente mostra come condividere il dashboard con i colleghi all'interno e all'esterno dell'azienda. Seguire quindi le istruzioni successive per sotto il video per fare una prova in prima persona.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard"></a>Condividere un dashboard
1. Nell'area di lavoro personale o in un'area di lavoro della app aprire un dashboard e selezionare **Condividi** ![Icona Condividi](media/service-share-dashboards/power-bi-share-icon.png).
2. Nella casella superiore, immettere gli indirizzi di posta elettronica completi di singoli utenti, gruppi di distribuzione o gruppi di sicurezza. Non è possibile condividere con le liste di distribuzione dinamiche. 
   
   È possibile condividere con utenti con indirizzi esterni all'organizzazione, ma verrà visualizzato un avviso.
   
   ![Avviso relativo alla condivisione esterna](media/service-share-dashboards/power-bi-share-dialog-warning.png)  
3. Aggiungere un messaggio, se si vuole. È facoltativo.
4. Per consentire ai colleghi di condividere a loro volta il dashboard con altri utenti, selezionare **Consenti ai destinatari di condividere il dashboard**.
   
   Il consenso alla condivisione da parte di altri utenti è definito *ricondivisione*. Se li autorizzi, gli utenti possono ricondividere dal servizio Power BI e dalle app per dispositivi mobili oppure possono inoltrare l'invito tramite posta elettronica ad altri utenti dell'organizzazione. L'invito scade dopo un mese. Gli utenti esterni all'organizzazione non possono ricondividere il dashboard. Il proprietario del dashboard può disattivare la ricondivisione o revocare la ricondivisione in base ai singoli utenti. Vedere [Interrompere la condivisione di un dashboard o impedire la condivisione da parte di altri utenti](service-share-dashboards.md#stop-sharing-a-dashboard-or-stop-others-from-sharing) più avanti.
5. Seleziona **Condividi**.
   
   ![Selezionare il pulsante Condividi](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   I singoli utenti, ma non i gruppi riceveranno nella posta elettronica un invito contenente un collegamento al dashboard condiviso e si riceverà una notifica di tipo **Operazione riuscita**. 
   
   Quando i destinatari dell'organizzazione fanno clic sul collegamento, Power BI aggiunge il dashboard alla rispettiva pagina elenco **Condivisi con l'utente corrente**. Infine, potranno selezionare il nome del mittente per visualizzare tutti i dashboard condivisi. 
   
   ![Pagina elenco Condivisi con l'utente corrente](media/service-share-dashboards/power-bi-shared-with-me-list-page.png)
   
   Quando i destinatari esterni all'organizzazione fanno clic sul collegamento, possono visualizzare il dashboard, ma non nel consueto portale di Power BI. Per altri dettagli, vedere [Condividere un dashboard con utenti esterni all'organizzazione](service-share-dashboards.md#share-a-dashboard-with-people-outside-your-organization) più avanti.

## <a name="who-has-access-to-a-dashboard-you-shared"></a>Utenti autorizzati ad accedere al dashboard condiviso
In alcuni casi è necessario visualizzare gli utenti con cui è stato condiviso un dashboard e verificare con chi lo hanno a loro volta condiviso.

1. Nell'elenco di dashboard o nel dashboard stesso selezionare **Condividi** ![Icona Condividi](media/service-share-dashboards/power-bi-share-icon.png). 
2. Nella finestra di dialogo **Condividi dashboard** selezionare **Accesso**.
   
    ![Finestra di dialogo Condividi dashboard, scheda Accesso](media/service-share-dashboards/power-bi-share-dialog-access.png)
   
    Gli utenti esterni all'organizzazione sono indicati come **Guest**.

## <a name="stop-sharing-a-dashboard-or-stop-others-from-sharing"></a>Interrompere la condivisione di un dashboard o impedire la condivisione da parte di altri utenti
Solo il proprietario del dashboard può attivare e disattivare la ricondivisione.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Se l'invito per la condivisione non è stato ancora inviato
* Deselezionare la casella di controllo **Consenti ai destinatari di condividere il dashboard** nella parte inferiore dell'invito prima di inviarlo.

### <a name="if-youve-already-shared-the-dashboard"></a>Se il dashboard è già stato condiviso
1. Nell'elenco di dashboard o nel dashboard stesso selezionare **Condividi** ![Icona Condividi](media/service-share-dashboards/power-bi-share-icon.png). 
2. Nella finestra di dialogo **Condividi dashboard** selezionare **Accesso**.
   
    ![Finestra di dialogo Condividi dashboard, scheda Accesso](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Fare clic sui puntini di sospensione (**...**) accanto a **Lettura e ricondivisione** e selezionare:
   
   ![Puntini di sospensione Lettura e ricondivisione](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Lettura** per evitare che l'utente condivida il dashboard con altri utenti.
   * **Rimuovi accesso** per impedire all'utente di visualizzare il dashboard.

## <a name="share-a-dashboard-with-people-outside-your-organization"></a>Condividere un dashboard con utenti esterni all'organizzazione
Quando si condivide con utenti esterni all'organizzazione, questi ricevono un messaggio di posta elettronica con un collegamento al dashboard condiviso e devono accedere a Power BI per visualizzare il dashboard. Se non dispongono di una licenza Power BI Pro, possono richiederla facendo clic sul collegamento.

Dopo avere eseguito l'accesso, il dashboard condiviso viene visualizzato in una finestra del browser separata senza il riquadro di spostamento a sinistra, non nel consueto portale di Power BI. Per accedere allo stesso dashboard in futuro, dovranno aggiungere il collegamento ai segnalibri.

Non possono modificare il contenuto del dashboard o report. Possono interagire con i grafici nel report (evidenziazione incrociata) e modificare i filtri/filtri dei dati disponibili nei report connessi al dashboard, ma non possono salvare le modifiche.

Il dashboard condiviso è visibile solo ai destinatari diretti. Ad esempio, se è stato inviato il messaggio a Vicki@contoso.com, solo Vicki può visualizzare il dashboard. Nessun altro può visualizzarlo, neanche se ha il collegamento, e Vicki dovrà usare lo stesso indirizzo di posta elettronica per accedere ai dashboard. Se effettua l'iscrizione con un altro indirizzo di posta elettronica, non potrà accedere al dashboard.

Gli utenti esterni all'organizzazione non possono visualizzare del tutto i dati se è implementata la sicurezza a livello di ruolo o di riga nei modelli tabulari di Analysis Services in locale.

Se si invia un collegamento da un'app Power BI per dispositivi mobili a persone all'esterno dell'organizzazione, quando si fa clic sul collegamento viene aperto il dashboard in un browser, non nell'app Power BI per dispositivi mobili.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Aspetti da tenere presenti sulla condivisione dei dashboard:

* In generale, i dati visualizzati nel dashboard sono gli stessi sia per l'utente che per i relativi colleghi. Se quindi un utente dispone delle autorizzazioni per visualizzare una maggior quantità di dati rispetto ai colleghi, questi ultimi potranno visualizzare tutti i dati presenti nel dashboard dell'utente. Tuttavia, se la [sicurezza a livello di riga](service-admin-rls.md) viene applicata al set di dati sottostante di un dashboard, le credenziali di ogni persona vengono usate per determinare a quali dati può accedere.
* Tutti gli utenti con cui si condivide il dashboard lo possono visualizzare e possono interagire con i report nella [Visualizzazione lettura](service-report-open-in-reading-view.md). Non possono creare report o salvare le modifiche apportate a report esistenti.
* Nessuno può visualizzare o scaricare il set di dati.
* Tutti gli utenti possono [aggiornare manualmente i dati del dashboard](refresh-data.md).
* Se si usa Office 365 per la posta elettronica, è possibile condividere con i membri di un gruppo di distribuzione immettendo l'indirizzo di posta elettronica associato a quel gruppo.
* I colleghi con lo stesso dominio di posta elettronica dell'utente e quelli che usano un dominio diverso ma registrato nel medesimo tenant possono condividere il dashboard con altri utenti. Si supponga ad esempio che i domini contoso.com e contoso2.com siano stati registrati nello stesso tenant. Se l'indirizzo di posta elettronica è konrads@contoso.com, allora sia ravali@contoso.com che gustav@contoso2.com possono condividere il dashboard, purché abbiano l'autorizzazione alla condivisione.
* Se i colleghi hanno già accesso a un dashboard specifico, è possibile inviare un collegamento diretto a tale dashboard semplicemente copiandone l'URL quando ci si trova al suo interno. Ad esempio: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* Analogamente, se i colleghi possono già accedere a un dashboard specifico, è possibile [inviare un collegamento diretto al report sottostante](service-share-reports.md). 

## <a name="next-steps"></a>Passaggi successivi
* Per inviare suggerimenti, passare al [sito della community di Power BI](https://community.powerbi.com/).
* [Come si condividono i dashboard e i report e in che modo ci si collabora?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Condividere solo un report di Power BI](service-share-reports.md)
* Domande? [Provare la community di Power BI](http://community.powerbi.com/).

