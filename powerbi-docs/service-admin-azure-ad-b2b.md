---
title: Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B
description: Power BI si integra con Azure Active Directory Business-to-business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione.
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: asaxton
ms.openlocfilehash: 5dabaa09923203c31572b413f8674b76028b7483
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuire il contenuto di Power BI agli utenti guest esterni usando Azure AD B2B

Power BI si integra con Azure Active Directory Business-to-business (AD B2B Azure) per consentire la distribuzione sicura di contenuto di Power BI agli utenti guest all'esterno dell'organizzazione, pur mantenendo il controllo sui dati interni.

> [!VIDEO https://www.youtube.com/embed/xxQWEQ1NnlY]

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

Per invitare più di utenti guest, usare PowerShell. Per altre informazioni, vedere [Codici ed esempi di PowerShell per Collaborazione B2B in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-code-samples).

L'utente guest deve selezionare **Inizia** nell'invito ricevuto tramite posta elettronica. L'utente guest viene quindi aggiunto al tenant.

![Invito tramite posta elettronica all'utente guest](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Inviti ad hoc

Per eseguire un invito in qualsiasi momento, è possibile aggiungere l'utente esterno all'elenco di accesso di un'app durante la pubblicazione.

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

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni dettagliate, tra cui come funziona la sicurezza a livello di riga, consultare il [white paper](https://aka.ms/powerbi-b2b-whitepaper).

Per informazioni su Azure Active Directory B2B, vedere [Informazioni su Collaborazione B2B di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)