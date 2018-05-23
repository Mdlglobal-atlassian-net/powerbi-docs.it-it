---
title: Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B
description: Power BI si integra con Azure Active Directory Business-to-business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2cd096303412ef2ecbf65d818cfa70a007767da9
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B

Power BI si integra con Azure Active Directory Business-to-business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione, pur mantenendo il controllo sui dati interni.

> [!VIDEO https://www.youtube.com/embed/xxQWEQ1NnlY]

> [!NOTE]
> Prima di invitare utenti guest è necessario **abilitare** la funzionalità [Impostazioni di esportazione e condivisione](service-admin-portal.md#export-and-sharing-settings) nelle impostazioni del tenant del portale di amministrazione di Power BI.

> [!NOTE]
> Questa funzionalità non è attualmente disponibile nelle app Power BI per dispositivi mobili. In un dispositivo mobile è possibile visualizzare il contenuto di Power BI condiviso tramite Azure AD B2B in un browser. 

## <a name="who-can-you-invite"></a>Chi è possibile invitare?

È possibile invitare utenti guest che usano qualsiasi indirizzo di posta elettronica, inclusi account personali, ad esempio gmail.com, outlook.com o hotmail.com. In Azure B2B questi sono noti come "ID social". Per altre informazioni, vedere [Azure B2B](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b).

## <a name="invite-guest-users"></a>Invitare gli utenti guest

Esistono due modi per invitare gli utenti guest nei tenant di Power BI: inviti pianificati o inviti ad hoc. Gli inviti sono necessari solo la prima volta che un utente esterno viene invitato nell'organizzazione.

### <a name="planned-invites"></a>Inviti pianificati

Un invito pianificato viene eseguito all'interno del Portale di Microsoft Azure in Azure AD o con PowerShell. Questa è l'opzione da scegliere se si conoscono gli utenti che devono essere invitati. 

**Per creare gli utenti guest nel portale di Azure AD è necessario essere un amministratore del tenant.**

1. Andare al [portale di Azure](https://portal.azure.com) e selezionare **Azure Active Directory**.

2. Passare a **Utenti e gruppi** > **Tutti gli utenti** > **Nuovo utente guest**.

    ![Portale di Azure AD - Nuovo utente Guest](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

3. Immettere l'**indirizzo di posta elettronica** e un **messaggio personale**.

    ![Portale di Azure AD - Messaggio di invito al nuovo utente guest](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

4. Selezionare **Invita**.

Per invitare più di utenti guest, usare PowerShell. Per altre informazioni, vedere [Codici ed esempi di PowerShell per Collaborazione B2B in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/b2b/code-samples).

L'utente guest deve selezionare **Inizia** nell'invito ricevuto tramite posta elettronica. L'utente guest viene quindi aggiunto al tenant.

![Invito tramite posta elettronica all'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Inviti ad hoc

Per inviare un invito in qualsiasi momento, aggiungere l'utente esterno al dashboard o al report tramite l'interfaccia utente condivisa o all'app tramite la pagina di accesso.

Di seguito è riportato un esempio delle operazioni da eseguire quando si invita un utente esterno a usare un'app.
![Utente esterno aggiunto all'elenco di accesso dell'app](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L'utente guest riceverà un messaggio di posta elettronica che indica che l'app è stata condivisa con lui.

![Messaggio di posta elettronica per l'app condivisa con l'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

L'utente guest deve accedere con l'indirizzo di posta elettronica dell'organizzazione. Verrà richiesto di accettare l'invito dopo l'accesso. Dopo l'accesso, l'utente guest viene reindirizzato al contenuto dell'app. Per tornare all'app, aggiungere il collegamento ai segnalibri o salvare il messaggio di posta elettronica.

## <a name="licensing"></a>Gestione delle licenze

L'utente guest dovrà essere in possesso delle licenze appropriate per visualizzare l'app condivisa. Sono disponibili tre opzioni per eseguire questa operazione.

### <a name="use-power-bi-premium"></a>Usare Power BI Premium

L'assegnazione dell'area di lavoro per le app alla capacità di Power BI Premium consente all'utente guest di usare l'app senza richiedere una licenza di Power BI Pro. Power BI Premium consente alle app di sfruttare anche altre funzionalità come maggiori frequenze di aggiornamento, capacità dedicata e modelli di grandi dimensioni.

![Usare Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-power-bi-pro-license-to-guest-user"></a>Assegnare una licenza di Power BI Pro all'utente guest

L'assegnazione di una licenza di Power BI Pro all'utente guest, all'interno del tenant, gli consente di visualizzare il contenuto.

> [!NOTE]
> Una licenza di Power BI Pro dal tenant si applica agli utenti guest solo quando accedono al contenuto all'interno del tenant.

![Assegnare una licenza Pro dal tenant](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>L'utente guest ha una licenza di Power BI Pro

L'utente guest ha già una licenza di Power BI Pro assegnata nel tenant.

![L'utente guest ha una licenza](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Quando si invitano utenti guest che usano account di posta elettronica personali, ad esempio gmail.com, outlook.com o hotmail.com, è possibile seguire questo [video incorporato](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-redemption-experience) per vedere un esempio della procedura di iscrizione di un utente.
* Gli utenti guest B2B esterni possono esclusivamente utilizzare contenuto. Gli utenti B2B esterni possono visualizzare app, dashboard e report, esportare i dati e creare sottoscrizioni di posta elettronica per i dashboard e i report. Non possono accedere alle aree di lavoro o pubblicare contenuto personale.
* Questa funzionalità non è attualmente disponibile nelle app Power BI per dispositivi mobili. In un dispositivo mobile è possibile visualizzare il contenuto di Power BI condiviso tramite Azure AD B2B in un browser.
* Questa funzionalità non è attualmente disponibile nella Web part Report di SharePoint Online di Power BI.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni dettagliate, tra cui come funziona la sicurezza a livello di riga, consultare il [white paper](https://aka.ms/powerbi-b2b-whitepaper).

Per informazioni su Azure Active Directory B2B, vedere [Informazioni su Collaborazione B2B di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)
