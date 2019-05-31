---
title: Distribuire il contenuto agli utenti guest esterni usando Azure AD B2B
description: Power BI si integra con Azure Active Directory Business-to-business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101598"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B

Power BI si integra con Azure Active Directory Business to Business (Azure AD B2B) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione, pur mantenendo il controllo sui dati interni.  

Inoltre, è possibile consentire agli utenti guest all'esterno dell'organizzazione di modificare e gestire il contenuto all'interno dell'organizzazione.

## <a name="enable-access"></a>Abilitare l'accesso

Assicurarsi di abilitare la [condividere contenuto con utenti esterni](service-admin-portal.md#export-and-sharing-settings) funzionalità nel portale di amministrazione di Power BI prima di invitare utenti guest.

È anche possibile usare la [consentire agli utenti guest esterni di modificare e gestire contenuto all'interno dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funzionalità. Consente di selezionare quale utente guest può visualizzare e creare contenuto nelle aree di lavoro, tra cui l'esplorazione Power BI della propria organizzazione.

## <a name="who-can-you-invite"></a>Chi è possibile invitare?

È possibile invitare utenti guest con un indirizzo di posta elettronica, inclusi gli account personali come hotmail.com, gmail.com e outlook.com. Azure AD B2B chiama questi indirizzi *identità di social networking*.

## <a name="invite-guest-users"></a>Invitare gli utenti guest

Gli utenti guest richiedono gli inviti solo la prima volta che è possibile invitare i collaboratori dell'organizzazione. Esistono due modi per invitare gli utenti: pianificato gli inviti e inviti ad hoc.

### <a name="planned-invites"></a>Inviti pianificati

Usare un invito pianificato se si sa quali utenti invitare. È possibile inviare l'invito con il portale di Azure o PowerShell. È necessario essere un amministratore del tenant per invitare altre persone.

Seguire questi passaggi per inviare un invito nel portale di Azure.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Azure Active Directory**.

1. Sotto **Manage**, selezionare **Users** > **tutti gli utenti** > **nuovo utente guest**.

    ![Screenshot del portale di Azure con la nuova opzione di utente guest indicata.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Immettere un **indirizzo di posta elettronica** e un **messaggio personale**.

    ![Screenshot della finestra di dialogo utente Guest di Azure Active Directory portale nuovo.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Selezionare **Invita**.

Per invitare più di utenti guest, usare PowerShell. Per altre informazioni, vedere [Codici ed esempi di PowerShell per Collaborazione B2B in Azure AD](/azure/active-directory/b2b/code-samples/).

L'utente guest deve selezionare **Inizia** nell'invito ricevuto tramite posta elettronica. L'utente guest viene quindi aggiunto al tenant.

![Invito tramite posta elettronica utente screenshot di Guest.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Inviti ad hoc

Per invitare un utente esterno in qualsiasi momento, aggiungere tali al dashboard o report tramite l'interfaccia utente condivisa o l'app tramite la pagina di accesso. Di seguito è riportato un esempio delle operazioni da eseguire quando si invita un utente esterno a usare un'app.

![Utente screenshot di esterno aggiunto all'elenco di accesso delle App in Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L'utente guest riceverà un messaggio di posta elettronica che indica che l'app condivisa con loro.

![Screenshot del messaggio di posta elettronica per l'app condivisa con l'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

L'utente guest deve accedere con l'indirizzo di posta elettronica dell'organizzazione. Si riceverà un prompt dei comandi per accettare l'invito dopo l'accesso. Dopo l'accesso, l'app viene visualizzata per l'utente guest. Per tornare all'app, può aggiungere il collegamento ai segnalibri o salvare il messaggio di posta elettronica.

## <a name="licensing"></a>Gestione delle licenze

L'utente guest deve disporre delle licenze appropriate in grado di visualizzare il contenuto condiviso. Esistono tre modi per verificare che l'utente abbia una licenza appropriata: usare Power BI Premium, assegnare una licenza Power BI Pro o utilizzare licenze di Power BI Pro del guest.

Quando si usa la funzionalità [Consenti agli utenti guest esterni di modificare e gestire il contenuto dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gli utenti guest che contribuiscono alle aree di lavoro con contenuto o condividono contenuto con altri utenti necessitano di una licenza di Power BI Pro.

### <a name="use-power-bi-premium"></a>Usare Power BI Premium

L'area di lavoro di app per l'assegnazione [capacità di Power BI Premium](service-premium-what-is.md) consente all'utente guest di usare l'app senza richiedere una licenza Power BI Pro. Power BI Premium consente anche alle app di sfruttare altre funzionalità come maggiori frequenze di aggiornamento, capacità dedicata e modelli di grandi dimensioni.

![Diagramma dell'esperienza utente guest con Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Assegnare una licenza di Power BI Pro all'utente guest

Assegnare una licenza Power BI Pro all'utente guest, all'interno del tenant, consente a tale contenuto visualizzazione utente guest nel tenant.

![Diagramma dell'esperienza utente guest con licenza assegnare Pro dal tenant.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>L'utente guest ha una licenza di Power BI Pro

L'utente guest ha già una licenza di Power BI Pro assegnata nel tenant.

![Diagramma dell'esperienza utente guest quando si trasferire le proprie licenze.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Utenti guest che possono modificare e gestire contenuto 

Quando si usa la [consentire agli utenti guest esterni di modificare e gestire contenuto all'interno dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funzionalità, gli utenti guest specificato ottengono l'accesso a Power BI dell'organizzazione. È possibile visualizzare qualsiasi contenuto a cui hanno l'autorizzazione. Si può accedere Home, esplorare le aree di lavoro, installare le app, vedere dove si trovano nell'elenco di accesso e contribuire al contenuto per le aree di lavoro. Possono creare aree di lavoro che fanno uso dell'esperienza delle nuove aree di lavoro o esserne amministratori. Si applicano alcune limitazioni. La sezione Considerazioni e limitazioni sono incluse le restrizioni.
 
Per consentire a tali utenti di accedere a Power BI, fornire l'URL del Tenant. Per trovare l'URL del tenant, seguire questa procedura.

1. Nel servizio Power BI selezionare Guida ( **?** ) nel menu in alto, quindi **Informazioni su Power BI**.

2. Cercare il valore accanto a **URL tenant**. Il valore è l'URL del tenant è possibile condividere con gli utenti guest.

    ![Finestra di dialogo screenshot di informazioni su Power BI con il tenant di utente guest che URL indicati.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Per impostazione predefinita, esterno Azure AD B2B limita gli utenti guest di consumo del solo contenuto. Utenti guest di Azure AD B2B esterni possono visualizzare App, dashboard e report, esportare i dati e creare sottoscrizioni tramite posta elettronica per dashboard e report. Non possono accedere alle aree di lavoro o pubblicare contenuto personale. Tuttavia, queste restrizioni non si applicano agli utenti guest l'accesso mediante il [consentire agli utenti guest esterni di modificare e gestire contenuto all'interno dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funzionalità.

* Per gli utenti guest abilitati tramite le [consentire agli utenti guest esterni di modificare e gestire contenuto all'interno dell'organizzazione](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funzionalità, alcune esperienze non sono a loro disposizione. Per aggiornare o pubblicare report, devono usare l'interfaccia utente web del servizio Power BI, tra cui l'opzione Scarica i dati per caricare i file di Power BI Desktop.  Non sono supportate le esperienze seguenti:
    * Pubblicazione diretta da Power BI Desktop al servizio Power BI
    * Gli utenti guest non è possibile usare Power BI desktop per connettersi ai set di dati del servizio nel servizio Power BI
    * Aree di lavoro classiche associate a gruppi di Office 365:
        * Utente guest non è possibile creare o essere amministratori di queste aree di lavoro
        * Gli utenti guest possono essere membri
    * L'invio di inviti ad hoc non è supportata per gli elenchi di accesso dell'area di lavoro
    * Power BI Publisher per Excel non è supportata per gli utenti guest
    * Gli utenti guest non è possibile installare una di Power BI Gateway e connetterlo all'organizzazione
    * Gli utenti guest non è possibile installare le app di pubblicazione per l'intera organizzazione
    * Gli utenti guest non è possibile usare, creare, aggiornare o installare pacchetti di contenuto aziendali
    * Gli utenti guest non è possibile usare analizza in Excel
    * Gli utenti guest non possono essere @mentioned nell'aggiunta di commenti
    * Gli utenti guest non è possibile utilizzare le sottoscrizioni
    * Gli utenti guest che usano questa funzionalità dovrebbero avere un account aziendale o dell'istituto di istruzione. Gli utenti guest usando sia account personali si verificheranno più limitazioni di scadenza per l'accesso con restrizioni.

* Questa funzionalità non è attualmente disponibile con la web part di SharePoint Online di Power BI report.

* Esistono impostazioni di Active Directory che possono limitare operazioni eseguibili dagli utenti guest esterni all'interno dell'organizzazione globale. Che si applica anche all'ambiente di Power BI. Nella documentazione seguente vengono illustrate le impostazioni:
    * [Gestisci le impostazioni di collaborazione esterna](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Consentire o bloccare gli inviti agli utenti B2B di organizzazioni specifiche](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Passaggi successivi

Per informazioni più dettagliate, tra cui funzionamento della protezione di livello di riga, consultare il white paper: [Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Per informazioni su Azure AD B2B, vedere [che cos'è Azure AD B2B collaboration?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
