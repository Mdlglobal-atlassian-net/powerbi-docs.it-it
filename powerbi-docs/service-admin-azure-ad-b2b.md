---
title: Distribuire il contenuto agli utenti guest esterni usando Azure AD B2B
description: Power BI si integra con Azure Active Directory Business-to-business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 7e76f03a3795976aebd1480dc77a579c9245ed9e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282058"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B

Power BI si integra con Azure Active Directory Business to Business (Azure AD B2B) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione, pur mantenendo il controllo sui dati interni.

## <a name="enable-access"></a>Abilitare l'accesso

Prima di invitare utenti guest, verificare che la funzionalità [Impostazioni di esportazione e condivisione](service-admin-portal.md#export-and-sharing-settings) sia abilitata nel portale di amministrazione di Power BI.

## <a name="who-can-you-invite"></a>Chi è possibile invitare?

È possibile invitare utenti guest con qualsiasi indirizzo di posta elettronica, inclusi account personali, ad esempio gmail.com, outlook.com e hotmail.com. In Azure AD B2B questi indirizzi sono chiamati *identità di social network*.

## <a name="invite-guest-users"></a>Invitare gli utenti guest

Gli inviti sono necessari solo per la prima volta che un utente guest esterno viene invitato nell'organizzazione. Esistono due modi per invitare gli utenti: inviti pianificati e inviti ad hoc.

### <a name="planned-invites"></a>Inviti pianificati

Usare un invito pianificato se si sa quali utenti invitare. È possibile inviare l'invito con il portale di Azure o PowerShell. È necessario essere un amministratore del tenant per invitare altre persone.

Seguire questi passaggi per inviare un invito nel portale di Azure.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Azure Active Directory**.

1. In **Gestisci** passare a **Utenti** > **Tutti gli utenti** > **Nuovo utente guest**.

    ![Portale di Azure AD - Nuovo utente Guest](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Immettere un **indirizzo di posta elettronica** e un **messaggio personale**.

    ![Portale di Azure AD - Messaggio di invito al nuovo utente guest](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Selezionare **Invita**.

Per invitare più di utenti guest, usare PowerShell. Per altre informazioni, vedere [Codici ed esempi di PowerShell per Collaborazione B2B in Azure AD](/azure/active-directory/b2b/code-samples/).

L'utente guest deve selezionare **Inizia** nell'invito ricevuto tramite posta elettronica. L'utente guest viene quindi aggiunto al tenant.

![Invito tramite posta elettronica all'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Inviti ad hoc

Per inviare un invito in qualsiasi momento, aggiungere l'utente esterno al dashboard o al report tramite l'interfaccia utente condivisa o all'app tramite la pagina di accesso. Di seguito è riportato un esempio delle operazioni da eseguire quando si invita un utente esterno a usare un'app.

![Utente esterno aggiunto all'elenco di accesso dell'app](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L'utente guest riceverà un messaggio di posta elettronica che indica che l'app è stata condivisa con lui.

![Messaggio di posta elettronica per l'app condivisa con l'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

L'utente guest deve accedere con l'indirizzo di posta elettronica dell'organizzazione. Verrà richiesto di accettare l'invito dopo l'accesso. Dopo l'accesso, l'utente guest viene reindirizzato al contenuto dell'app. Per tornare all'app, può aggiungere il collegamento ai segnalibri o salvare il messaggio di posta elettronica.

## <a name="licensing"></a>Gestione delle licenze

L'utente guest deve essere in possesso delle licenze appropriate per visualizzare l'app condivisa. A questo scopo, sono disponibili tre opzioni: usare Power BI Premium, assegnare una licenza di Power BI Pro o usare la licenza di Power BI Pro dell'utente guest.

### <a name="use-power-bi-premium"></a>Usare Power BI Premium

L'assegnazione dell'area di lavoro per le app alla [capacità di Power BI Premium](service-premium.md) consente all'utente guest di usare l'app senza richiedere una licenza di Power BI Pro. Power BI Premium consente alle app di sfruttare anche altre funzionalità come maggiori frequenze di aggiornamento, capacità dedicata e modelli di grandi dimensioni.

![Usare Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Assegnare una licenza di Power BI Pro all'utente guest

L'assegnazione di una licenza di Power BI Pro all'utente guest, all'interno del tenant, gli consente di visualizzare il contenuto nel tenant.

![Assegnare una licenza Pro dal tenant](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>L'utente guest ha una licenza di Power BI Pro

L'utente guest ha già una licenza di Power BI Pro assegnata nel tenant.

![L'utente guest ha una licenza](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Gli utenti guest B2B esterni possono esclusivamente utilizzare contenuto. Gli utenti B2B esterni possono visualizzare app, dashboard e report, esportare i dati e creare sottoscrizioni di posta elettronica per i dashboard e i report. Non possono accedere alle aree di lavoro o pubblicare contenuto personale.

* Questa funzionalità non è attualmente disponibile nelle app Power BI per dispositivi mobili. In un dispositivo mobile è possibile visualizzare il contenuto di Power BI condiviso tramite Azure AD B2B in un browser.

* Questa funzionalità non è attualmente disponibile nella Web part Report di SharePoint Online di Power BI.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni dettagliate, tra cui come funziona la sicurezza a livello di riga, consultare il white paper: [Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Per informazioni su Azure AD B2B, vedere [Informazioni su Collaborazione B2B di Azure AD](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
