---
title: Ricerca di utenti Power BI che hanno eseguito l'accesso
description: Se si è un amministratore tenant e si desidera vedere chi ha effettuato l'accesso a Power BI, è possibile usare i report d'uso e di accesso di Azure Active Directory per ottenere informazioni.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 26cf9b10d2a7bfffca151fe36cd45626487b6eef
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383647"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Ricerca di utenti Power BI che hanno eseguito l'accesso

Se si è un amministratore del tenant e si vuole vedere chi ha effettuato l'accesso a Power BI, è possibile usare i [report di utilizzo e accesso di Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) per ottenere informazioni.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Il report delle attività fornisce informazioni utili, ma non identifica il tipo di licenza di ogni utente. Per visualizzare le licenze, usare l'interfaccia di amministrazione di Microsoft 365.

## <a name="requirements"></a>Requisiti

Qualsiasi utente (compresi quelli non amministratori) può visualizzare un report dei propri accessi, ma per visualizzare un report per tutti gli utenti è necessario soddisfare i requisiti seguenti.

* Al tenant deve essere associata una licenza di Azure AD Premium.

* È necessario appartenere a uno dei ruoli seguenti: Amministratore globale, Amministratore della sicurezza o Ruolo con autorizzazioni di lettura per la sicurezza.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Usare il portale di Azure per visualizzare gli accessi

Per visualizzare l'attività di accesso, seguire questa procedura.

1. Nel **portale di Azure** selezionare **Azure Active Directory**.

1. In **Monitoraggio** selezionare **Accessi**.
   
    ![Accessi di Azure AD](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrare l'applicazione in base a **Microsoft Power BI** o **Power BI Gateway** e selezionare **Applica**.

    **Microsoft Power BI** permette di applicare filtri per l'attività di accesso correlata al servizio, mentre **Power BI Gateway** permette di applicare filtri per l'attività di accesso specifica del gateway dati locale.
   
    ![Filtrare gli accessi](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Esportazione dei dati

Per esportare i dati di accesso sono disponibili due opzioni: scaricare un file CSV o usare PowerShell. Nella parte superiore del report di accesso selezionare una delle opzioni seguenti:

* **Scarica** per scaricare un file CSV per i dati attualmente filtrati.

* **Script** per scaricare uno script di PowerShell per i dati attualmente filtrati. È possibile aggiornare il filtro nello script in base alle esigenze.

![Scaricare un file CSV o uno script](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Conservazione dei dati

I dati di accesso rimangono disponibili per un massimo di 30 giorni. Per altre informazioni, vedere [Azure Active Directory report retention policies](/azure/active-directory/reports-monitoring/reference-reports-data-retention) (Criteri di conservazione dei report di Azure Active Directory).

## <a name="next-steps"></a>Passaggi successivi

[Uso del controllo nell'organizzazione](service-admin-auditing.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

