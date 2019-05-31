---
title: Ricerca di utenti Power BI che hanno eseguito l'accesso
description: Se si ha un amministratore del tenant e si desidera vedere chi ha eseguito l'accesso a Power BI, è possibile utilizzare i report di accesso e utilizzo di Azure Active Directory per ottenere visibilità.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906710"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Ricerca di utenti Power BI che hanno eseguito l'accesso

Se si è un amministratore di tenant e si desidera vedere chi ha eseguito l'accesso a Power BI, usare il [report di accesso e utilizzo di Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) abbiano visibilità.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Il **accessi** report fornisce informazioni utili, ma non identifica il tipo di ogni utente dispone di licenza. Per visualizzare le licenze, usare l'interfaccia di amministrazione di Microsoft 365.

## <a name="requirements"></a>Requisiti

Qualsiasi utente (compresi quelli non amministratori) può visualizzare un report dei propri accessi, ma per visualizzare un report per tutti gli utenti è necessario soddisfare i requisiti seguenti.

* Il tenant deve avere una licenza di Azure Active Directory Premium è associata.

* È necessario appartenere a uno dei ruoli seguenti: Amministratore globale, Amministratore della sicurezza o Ruolo con autorizzazioni di lettura per la sicurezza.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Usare il portale di Azure per visualizzare gli accessi

Per visualizzare l'attività di accesso, seguire questa procedura.

1. Nel **portale di Azure** selezionare **Azure Active Directory**.

1. In **Monitoraggio** selezionare **Accessi**.
   
    ![Screenshot dell'interfaccia utente di Azure con le opzioni di Azure Active Directory e accessi evidenziate.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrare l'applicazione in base a **Microsoft Power BI** o **Power BI Gateway** e selezionare **Applica**.

    **Microsoft Power BI** i filtri per attività di accesso relative al servizio, mentre **Power BI Gateway** i filtri per attività di accesso specifico al gateway dati locale.
   
    ![Screenshot del filtro degli accessi con evidenziato il campo di applicazioni.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Esportazione dei dati

È possibile [scarica un report sugli accessi](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) in uno dei due formati: un file CSV o un file JSON.

![Screenshot del pulsante di download.](media/service-admin-access-usage/download-sign-in-data-csv.png)

In cima il **accessi** report, selezionare **scaricare** e quindi selezionare una delle opzioni seguenti:

* **CSV** per scaricare un file CSV per i dati attualmente filtrati.

* **JSON** per scaricare un file JSON per i dati attualmente filtrati.

## <a name="data-retention"></a>Conservazione dei dati

I dati di accesso rimangono disponibili per un massimo di 30 giorni. Per altre informazioni, vedi [criteri di conservazione dei report di Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Passaggi successivi

[Uso del controllo nell'organizzazione](service-admin-auditing.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)