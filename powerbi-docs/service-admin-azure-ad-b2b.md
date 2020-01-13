---
title: Distribuire il contenuto agli utenti guest esterni usando Azure AD B2B
description: Power BI si integra con Azure Active Directory Business-to-Business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 22328ddd6be697f658301516d05971cdcee0d260
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223903"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B

Power BI si integra con Azure Active Directory Business-to-Business (Azure AD B2B) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione, pur mantenendo il controllo sui dati interni. Inoltre, è possibile consentire agli utenti guest all'esterno dell'organizzazione di modificare e gestire il contenuto all'interno dell'organizzazione.

Questo articolo offre un'introduzione di base a Azure AD B2B in Power BI. Per altre informazioni, vedere [Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure Active Directory B2B](whitepaper-azure-b2b-power-bi.md).

## <a name="enable-access"></a>Abilitare l'accesso

Prima di invitare utenti guest, verificare che la funzionalità [Condividi contenuti con utenti esterni](service-admin-portal.md#export-and-sharing-settings) sia abilitata nel portale di amministrazione di Power BI.

È anche possibile usare la funzionalità [Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization). Consente di selezionare quale utente guest può visualizzare e creare contenuto nelle aree di lavoro, inclusa l'esplorazione di Power BI della propria organizzazione.

## <a name="who-can-you-invite"></a>Chi è possibile invitare?

È possibile invitare utenti guest con la maggior parte degli indirizzi di posta elettronica, inclusi account personali, ad esempio gmail.com, outlook.com e hotmail.com. Azure AD B2B chiama questi indirizzi *identità di social network*.

Non è possibile invitare gli utenti associati a un cloud per enti pubblici, ad esempio [Power BI per il Governo degli Stati Uniti](service-govus-overview.md).

## <a name="invite-guest-users"></a>Invitare gli utenti guest

Gli inviti per gli utenti guest sono richiesti solo per il primo invito nell'organizzazione. Esistono due modi per invitare gli utenti: inviti pianificati e inviti ad hoc.

### <a name="planned-invites"></a>Inviti pianificati

Usare un invito pianificato se si sa quali utenti invitare. È possibile inviare l'invito con il portale di Azure o PowerShell. È necessario essere un amministratore del tenant per invitare altre persone.

Seguire questi passaggi per inviare un invito nel portale di Azure.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Azure Active Directory**.

1. In **Gestisci** selezionare **Utenti** > **Tutti gli utenti** > **Nuovo utente guest**.

    ![Screenshot del portale di Azure con l'opzione Nuovo utente guest evidenziata.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Immettere un **indirizzo di posta elettronica** e un **messaggio personale**.

    ![Screenshot della finestra di dialogo Nuovo utente guest del portale di Azure AD.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Selezionare **Invita**.

Per invitare più utenti guest, usare PowerShell. Per altre informazioni, vedere [Codici ed esempi di PowerShell per Collaborazione B2B di Azure AD](/azure/active-directory/b2b/code-samples/).

L'utente guest deve selezionare **Inizia** nell'invito ricevuto tramite posta elettronica. L'utente guest viene quindi aggiunto al tenant.

![Screenshot dell'invito tramite posta elettronica per l'utente guest.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Inviti ad hoc

Per invitare un utente esterno in qualsiasi momento, aggiungerlo al dashboard o al report tramite l'interfaccia utente condivisa o all'app tramite la pagina di accesso. Di seguito è riportato un esempio delle operazioni da eseguire quando si invita un utente esterno a usare un'app.

![Screenshot dell'aggiunta di un utente esterno all'elenco di accesso dell'app in Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L'utente guest riceverà un messaggio di posta elettronica che indica che l'app è stata condivisa con lui.

![Screenshot del messaggio di posta elettronica per l'app condivisa con l'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

L'utente guest deve accedere con l'indirizzo di posta elettronica dell'organizzazione. Riceverà una richiesta di accettazione dell'invito dopo l'accesso. Dopo l'accesso, l'app viene aperta per l'utente guest. Per tornare all'app, l'utente guest può aggiungere il collegamento ai segnalibri o salvare il messaggio di posta elettronica.

## <a name="licensing"></a>Gestione delle licenze

L'utente guest deve essere in possesso delle licenze appropriate per visualizzare il contenuto condiviso. Esistono tre modi per verificare che l'utente abbia una licenza appropriata: usare Power BI Premium, assegnare una licenza di Power BI Pro o usare la licenza di Power BI Pro del guest.

Quando si usa la funzionalità [Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gli utenti guest che contribuiscono alle aree di lavoro con contenuto o condividono contenuto con altri utenti necessitano di una licenza di Power BI Pro.

### <a name="use-power-bi-premium"></a>Usare Power BI Premium

L'assegnazione dell'area di lavoro alla [capacità di Power BI Premium](service-premium-what-is.md) consente all'utente guest di usare l'app senza che sia necessaria una licenza di Power BI Pro. Power BI Premium consente anche alle app di sfruttare altre funzionalità come maggiori frequenze di aggiornamento, capacità dedicata e modelli di grandi dimensioni.

![Diagramma dell'esperienza dell'utente guest con Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Assegnare una licenza di Power BI Pro all'utente guest

L'assegnazione di una licenza di Power BI Pro a un utente guest, all'interno del tenant, gli consente di visualizzare il contenuto nel tenant. Per altre informazioni sull'assegnazione delle licenze, vedere [Assegnare licenze agli utenti nella pagina Licenze](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Prima di assegnare le licenze Pro agli utenti guest, contattare il rappresentante dell'account Microsoft per assicurarsi della conformità con i termini del contratto con Microsoft.

![Diagramma dell'esperienza dell'utente guest con assegnazione della licenza Pro dal tenant.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>L'utente guest ha una licenza di Power BI Pro

L'utente guest ha già una licenza di Power BI Pro assegnata nel tenant.

![Diagramma dell'esperienza dell'utente guest quando tenta di usare la propria licenza.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Utenti guest che possono modificare e gestire contenuto

Quando si usa la funzionalità [Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization), gli utenti guest specificati ottengono accesso a Power BI dell'organizzazione e possono visualizzare qualsiasi contenuto per cui hanno l'autorizzazione. Possono accedere alla pagina Home, esplorare le aree di lavoro, installare le app disponibili nell'elenco di accesso e aggiungere contenuto alle aree di lavoro. Possono creare aree di lavoro che fanno uso dell'esperienza della nuova area di lavoro o esserne amministratori. Esistono alcune limitazioni. Nella sezione Considerazioni e limitazioni sono elencate queste restrizioni.
 
Per aiutare questi utenti ad accedere a Power BI, fornire loro l'URL del tenant. Per trovare l'URL del tenant, seguire questa procedura.

1. Nel servizio Power BI selezionare la guida ( **?** ) nel menu in alto, quindi **Informazioni su Power BI**.

2. Cercare il valore accanto a **URL tenant**. Il valore è l'URL del tenant che è possibile condividere con gli utenti guest.

    ![Screenshot della finestra di dialogo Informazioni su Power BI con l'URL del tenant dell'utente guest evidenziato.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Per impostazione predefinita, gli utenti guest di Azure AD B2B esterni sono limitati all'utilizzo del contenuto. Gli utenti guest di Azure AD B2B esterni possono visualizzare app, dashboard e report, esportare i dati e creare sottoscrizioni di posta elettronica per i dashboard e i report. Non possono accedere alle aree di lavoro o pubblicare contenuto personale. Tuttavia, queste restrizioni non si applicano agli utenti guest che ottengono l'accesso tramite la funzionalità [Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization).

* Per invitare gli utenti guest è necessaria una licenza di Power BI Pro. Gli utenti della versione di valutazione Pro non possono invitare gli utenti guest in Power BI.

* Alcune esperienze non sono disponibili per gli utenti guest abilitati tramite la funzionalità [Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization). Per aggiornare o pubblicare report, devono usare l'interfaccia utente Web del servizio Power BI, tra cui l'opzione Scarica i dati per caricare i file di Power BI Desktop.  Le esperienze seguenti non sono supportate:
    * Pubblicazione diretta da Power BI Desktop al servizio Power BI
    * Gli utenti guest non possono usare Power BI Desktop per connettersi ai set di dati del servizio nel servizio Power BI
    * Aree di lavoro classiche associate a gruppi di Office 365:
        * Gli utenti guest non possono creare queste aree di lavoro o esserne amministratori
        * Gli utenti guest possono essere membri
    * L'invio di inviti ad hoc non è supportato per gli elenchi di accesso all'area di lavoro
    * Power BI Publisher per Excel non è supportato per gli utenti guest
    * Gli utenti guest non possono installare un Power BI Gateway e connetterlo all'organizzazione
    * Gli utenti guest non possono installare app pubblicate per l'intera organizzazione
    * Gli utenti guest non possono usare, creare, aggiornare o installare pacchetti di contenuto dell'organizzazione
    * Gli utenti guest non possono usare Analizza in Excel
    * Gli utenti guest non possono essere @mentioned nei commenti
    * Gli utenti guest non possono usare le sottoscrizioni
    * Gli utenti guest che usano questa funzionalità dovrebbero avere un account aziendale o dell'istituto di istruzione. 
    
* Gli utenti guest che usano account personali saranno soggetti a maggiori limitazioni a causa di restrizioni di accesso.
    * Possono usare le esperienze nel servizio Power BI tramite un Web browser
    * Non possono usare le app per dispositivi mobili Power BI.
    * Non saranno in grado di accedere per fornire le credenziali quando è richiesto un account aziendale o dell'istituto di istruzione.

* Questa funzionalità non è attualmente disponibile nella Web part Report di SharePoint Online di Power BI.

* Esistono impostazioni di Active Directory che possono limitare le operazioni eseguibili dagli utenti guest esterni all'interno dell'organizzazione. Ciò si applica anche all'ambiente di Power BI. Nella documentazione seguente vengono illustrate le impostazioni:
    * [Gestisci le impostazioni di collaborazione esterna](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [Consentire o bloccare gli inviti agli utenti B2B di organizzazioni specifiche](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni dettagliate, tra cui come funziona la sicurezza a livello di riga, consultare il white paper: [Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Per informazioni su Azure AD B2B, vedere [Informazioni su Collaborazione B2B di Azure AD](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
