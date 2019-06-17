---
title: Incorporare con web part report in SharePoint Online
description: Con la nuova web part report di Power BI per SharePoint Online è possibile incorporare facilmente report interattivi di Power BI nelle pagine di SharePoint Online.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: ec70f4c9d6f3e6f51210a32f7efac7f160f462cb
ms.sourcegitcommit: 24781cdab5fbe43fc14248db636169cc54ef6721
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2019
ms.locfileid: "66498012"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Incorporare con web part report in SharePoint Online

Con la nuova web part report di Power BI per SharePoint Online è possibile incorporare facilmente report interattivi di Power BI nelle pagine di SharePoint Online.

Quando si usa la nuova opzione **Incorpora in SharePoint Online**, i report incorporati sono completamente protetti in modo che sia possibile creare facilmente portali interni protetti.

## <a name="requirements"></a>Requisiti

Affinché i report di **Incorpora in SharePoint Online** funzionino, è necessario quanto segue:

* Una licenza di Power BI Pro o una [capacità Power BI Premium (SKU EM o P)](service-premium-what-is.md) con una licenza di Power BI.
* La web part Power BI per SharePoint Online richiede le [pagine moderne](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Incorporare il report
Per incorporare il report in SharePoint Online, è necessario ottenere l'URL del report e usarlo con la web part Power BI di SharePoint Online.

### <a name="get-a-report-url"></a>Ottenere un URL del report

1. Visualizzare il report in Power BI.

2. Selezionare il menu a discesa **File**, quindi selezionare **Incorpora in SharePoint Online**.

    ![Menu File](media/service-embed-report-spo/powerbi-file-menu.png)

3. Copiare l'URL del report dalla finestra di dialogo.

    ![Collegamento di incorporamento](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Aggiungere il report di Power BI a una pagina di SharePoint Online

1. Aprire la pagina di destinazione in SharePoint Online e selezionare **Modifica**.

    ![Pagina modifiche SP](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Oppure, selezionare **+ Nuovo** in SharePoint Online per creare una nuova pagina moderna.

    ![Nuova pagina SP](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Selezionare l'elenco a discesa **+** e quindi selezionare la web part **Power BI**.

    ![Nuova web part SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Selezionare **Aggiungi report**.

    ![Nuovo report SP](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Incollare l'URL del report copiato in precedenza nel riquadro del **collegamento al report di Power BI**. Il report viene caricato automaticamente.

    ![Proprietà nuova web part SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Selezionare **Pubblica** per rendere visibile la modifica agli utenti di SharePoint Online.

    ![Report caricato SP](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Concedere l'accesso ai report

Incorporare un report in SharePoint Online non autorizza automaticamente gli utenti a visualizzare il report: è necessario impostare le autorizzazioni per la visualizzazione in Power BI.

> [!IMPORTANT]
> Assicurarsi di controllare chi può visualizzare il report all'interno del servizio Power BI e concedere l'accesso a chi non è elencato.

Esistono due modi per consentire l'accesso ai report in Power BI. Il primo modo, se si usa un gruppo di Office 365 per creare il sito del team di SharePoint Online, è aggiungere l'utente come membro dell'**area di lavoro per le app all'interno del servizio Power BI** e della **pagina SharePoint**. Per altre informazioni, vedere come [gestire un'area di lavoro per le app](service-manage-app-workspace-in-power-bi-and-office-365.md).

Il secondo consiste nell'incorporare un report all'interno di un'app e condividerlo direttamente con gli utenti:  

1. L'autore, che deve essere un utente della versione Pro, crea un report in un'area di lavoro per le app. Per la condivisione con gli *utenti della versione gratuita di Power BI*, l'area di lavoro per le app deve essere impostata come *area di lavoro Premium*.

2. L'autore pubblica l'app e la installa. L'autore deve installare l'app in modo da avere accesso all'URL del report usato per l'incorporamento in SharePoint Online.

3. A questo punto anche tutti gli utenti finali devono installare l'app. È anche possibile usare la funzionalità **Installa automaticamente l'app**, che può essere abilitata nel [portale di amministrazione di Power BI](service-admin-portal.md), per fare in modo che l'app sia preinstallata per gli utenti finali.

   ![Installa automaticamente l'app](media/service-embed-report-spo/install-app-automatically.png)

4. L'autore apre l'app e passa al report.

5. L'autore copia l'URL del report per l'incorporamento dal report installato dall'app. Non usare l'URL del report originale dall'area di lavoro per le app.

6. Creare un nuovo sito del team in SharePoint Online.

7. Aggiungere l'URL del report copiato in precedenza nella web part Power BI.

8. Aggiungere tutti gli utenti finali e/o i gruppi che utilizzeranno i dati nella pagina di SharePoint Online e nell'app Power BI creata.

    > [!NOTE]
    > **Gli utenti o i gruppi devono avere accesso sia alla pagina di SharePoint Online che al report nell'app Power BI per visualizzare il report nella pagina di SharePoint.**

A questo punto l'utente finale può passare al sito del team in SharePoint Online e visualizzare i report nella pagina.

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

Se l'ambiente di Power BI richiede di eseguire l'accesso con l'autenticazione a più fattori, potrà essere richiesto di accedere con un dispositivo di sicurezza per verificare la propria identità. Ciò si verifica se non si è eseguito l'accesso a SharePoint Online usando l'autenticazione a più fattori, ma l'ambiente di Power BI richiede un dispositivo di sicurezza per convalidare un account.

> [!NOTE]
> Power BI non supporta ancora l'autenticazione a più fattori con Azure Active Directory 2.0 e gli utenti visualizzeranno un messaggio di errore. Se l'utente accede nuovamente a SharePoint Online con il dispositivo di sicurezza, potrebbe riuscire a visualizzare il report.

## <a name="web-part-settings"></a>Impostazioni della web part

Di seguito sono riportate le impostazioni che è possibile regolare per la web part Power BI per SharePoint Online.

![Proprietà della web part SP](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Property | Descrizione |
| --- | --- |
| Nome pagina |Imposta la pagina predefinita della web part. Selezionare un valore nell'elenco a discesa. Se non viene visualizzata alcuna pagina, il report contiene una sola pagina o l'URL incollato contiene un nome di pagina. Rimuovere la sezione del report dall'URL per selezionare una pagina specifica. |
| Display |Adatta il report all'interno della pagina di SharePoint Online. |
| Show Navigation Pane |Mostra o nasconde il riquadro di spostamento. |
| Mostra riquadro Filtri |Mostra o nasconde il riquadro filtri. |

## <a name="reports-that-do-not-load"></a>Report che non vengono caricati

Se il report non viene caricato all'interno della web part Power BI, è possibile che venga visualizzato il messaggio seguente:

![Questo contenuto non è disponibile](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Esistono due motivi comuni per questo messaggio.

1. Non si ha accesso al report.
2. Il report è stato eliminato.

Contattare il proprietario della pagina di SharePoint Online per risolvere il problema.

## <a name="licensing"></a>Gestione delle licenze

Gli utenti che visualizzano un report in SharePoint devono avere una **licenza di Power BI Pro** oppure il contenuto deve essere in un'area di lavoro che si trova in una **[capacità Premium di Power BI (SKU EM o P)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Limitazioni e problemi noti

* Errore: "Si è verificato un errore. Provare a disconnettersi e riconnettersi, quindi visitare di nuovo questa pagina. ID di correlazione: non definito, stato risposta http: 400, codice errore server 10001, messaggio: Token di aggiornamento mancante"
  
  Se si riceve questo errore, provare una delle procedure di risoluzione dei problemi seguenti.
  
  1. Disconnettersi da SharePoint e accedere nuovamente. Assicurarsi di chiudere tutte le finestre del browser prima di accedere nuovamente.

  2. Se l'account utente richiede l'autenticazione a più fattori, assicurarsi di accedere a SharePoint usando un dispositivo MFA (Multi-Factor Authentication), ad esempio app per smartphone, smart card e così via.
  
  3. Gli account degli utenti Guest di Azure B2B non sono supportati. Per gli utenti viene visualizzato il logo Power BI che indica che è in corso il caricamento del componente ma non viene visualizzato il report.

* Power BI non supporta le stesse lingue localizzate supportate da SharePoint Online. Di conseguenza, la localizzazione all'interno del report incorporato potrebbe non essere corretta.

* Se si usa Internet Explorer 10, potrebbero verificarsi problemi. Per informazioni, vedere il [supporto dei browser per Power BI](consumer/end-user-browsers.md) e per [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* La web part Power BI non è disponibile per i [cloud nazionali](https://powerbi.microsoft.com/clouds/).

* SharePoint Server classico non è supportato con questa web part.

* I [filtri URL](service-url-filters.md) non sono supportati con la web part SPO.

## <a name="next-steps"></a>Passaggi successivi

* [Consentire o impedire la creazione di pagine del sito moderne dagli utenti finali](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Creare e distribuire un'app in Power BI](service-create-distribute-apps.md)  
* [Condividere un dashboard con i colleghi e altri utenti](service-share-dashboards.md)  
* [Che cos'è Power BI Premium?](service-premium-what-is.md)
* [Incorporare un report in un portale o un sito Web sicuro](service-embed-secure.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)