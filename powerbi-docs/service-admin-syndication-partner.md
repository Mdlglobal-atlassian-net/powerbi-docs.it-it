---
title: Impossibile aggiungere Power BI al partner O365
description: Impossibile aggiungere Power BI a un partner di diffusione di Office 365. Il modello diffuso su diversi canali è un modello di acquisto usato da Office 365.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 558d939582b5ac7ec67d64a9f56305326bc34d03
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856660"
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>Impossibile aggiungere Power BI a una sottoscrizione partner di Office 365

Office 365 consente alle aziende di rivendere Office 365 in bundle e integrato con le proprie soluzioni, fornendo ai clienti finali un singolo punto di contatto per l'acquisto, la fatturazione e il supporto.

Se si è interessati a ottenere Power BI, insieme alla sottoscrizione di Office 365, è consigliabile contattare il proprio partner. Se il partner attualmente non offre Power BI, è possibile valutare diverse opzioni.

## <a name="work-with-your-partner-to-purchase-power-bi"></a>Collaborare con il partner per acquistare Power BI

Se si vuole acquistare una sottoscrizione di Power BI Pro o Power BI Premium, collaborare con il proprio partner per verificare le opzioni disponibili:

* Il partner accetta di aggiungere Power BI al proprio portfolio ed è quindi possibile acquistarlo dal partner.

* Il partner è in grado di passare a un modello che consente di acquistare Power BI direttamente da Microsoft o da un altro partner che offre Power BI.

## <a name="purchase-from-microsoft-or-another-channel"></a>Acquisto da Microsoft o un altro canale

A seconda della relazione con il partner, è possibile acquistare Power BI direttamente da Microsoft o da un altro partner. È possibile verificare se è possibile aggiungere sottoscrizioni di Power BI nell'interfaccia di amministrazione di Microsoft 365 (è necessaria l'appartenenza al ruolo Amministratore globale o Amministratore fatturazione).

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Nel menu di sinistra aprire **Fatturazione**:

    * Se viene visualizzata l'opzione **Sottoscrizioni**, è possibile ottenere il servizio direttamente da Microsoft oppure contattare un altro partner che offre Power BI.

        ![Fatturazione con sottoscrizioni](media/service-admin-syndication-partner/billingsub.png)

    * Se l'opzione **Sottoscrizioni** non viene visualizzata, non è possibile effettuare l'acquisto direttamente da Microsoft o da un altro partner.

Se il partner non offre Power BI e non è possibile acquistare direttamente da Microsoft o da un altro partner, valutare la possibilità di effettuare l'iscrizione per una versione di valutazione gratuita.

## <a name="sign-up-for-a-free-trial"></a>Iscriversi per una versione di valutazione gratuita

È possibile iscriversi a una versione di valutazione gratuita di Power BI Pro. Se si non acquista Power BI Pro alla fine del periodo di valutazione, è comunque disponibile una licenza gratuita che offre molte delle funzionalità di Power BI. Per altre informazioni, vedere [Funzionalità di Power BI in base al tipo di licenza](service-features-license-type.md).

### <a name="enable-ad-hoc-subscriptions"></a>Abilitare le sottoscrizioni ad hoc

Per impostazione predefinita, le iscrizioni di persone fisiche (note anche come sottoscrizioni ad hoc) sono disabilitate. In questo caso quando si tenta di iscriversi viene visualizzato il messaggio seguente: *Your IT department has turned off signup for Microsoft Power BI* (Il reparto IT ha disattivato l'iscrizione per Microsoft Power BI).

![Immagine Siamo spiacenti](media/service-admin-syndication-partner/sorry.png)

Per abilitare le sottoscrizioni ad hoc, è possibile contattare il proprio partner e richiederne l'attivazione. Se si è l'amministratore del proprio tenant e si sa come usare i comandi PowerShell per Azure Active Directory, è possibile abilitare personalmente le sottoscrizioni ad hoc. [Azure Active Directory PowerShell per Graph](/powershell/azure/active-directory/install-adv2/)

1. Accedere ad Azure Active Directory usando le credenziali di Office 365. La prima riga dello script seguente richiede le credenziali. La seconda riga si connette ad Azure Active Directory.

    ```powershell
    $msolcred = get-credential
    connect-msolservice -credential $msolcred
    ```

    ![Immettere le credenziali](media/service-admin-syndication-partner/aad-signin.png)

1. Dopo aver effettuato l'accesso, eseguire il comando seguente per controllare l'impostazione corrente per `AllowAdHocSubscriptions`.

    ```powershell
    Get-MsolCompanyInformation
    ```

1. Eseguire il comando seguente per abilitare le iscrizioni gratuite.

    ```powershell
    Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

## <a name="next-steps"></a>Passaggi successivi

[Gestione delle licenze di Power BI nell'organizzazione](service-admin-licensing-organization.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)