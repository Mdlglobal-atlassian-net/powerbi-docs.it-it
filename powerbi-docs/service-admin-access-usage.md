---
title: Ricerca di utenti Power BI che hanno eseguito l'accesso
description: Se si è un amministratore tenant e si desidera vedere chi ha effettuato l'accesso a Power BI, è possibile usare i report d'uso e di accesso di Azure Active Directory per ottenere informazioni.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b1ebbfc323698ed8ab092b8396ef22e4199720e
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075871"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Ricerca di utenti Power BI che hanno eseguito l'accesso

Se si è un amministratore del tenant e si vuole vedere chi ha effettuato l'accesso a Power BI, è possibile usare i [report di utilizzo e accesso di Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) per ottenere informazioni.

> [!NOTE]
> Il report degli **accessi** fornisce informazioni utili, ma non identifica il tipo di licenza di ogni utente. Per visualizzare le licenze, usare l'interfaccia di amministrazione di Microsoft 365.

## <a name="requirements"></a>Requisiti

Qualsiasi utente (compresi quelli non amministratori) può visualizzare un report dei propri accessi, ma per visualizzare un report per tutti gli utenti è necessario soddisfare i requisiti seguenti.

* Al tenant deve essere associata una licenza di Azure Active Directory Premium.

* È necessario appartenere a uno dei ruoli seguenti: Amministratore globale, Amministratore della sicurezza o Ruolo con autorizzazioni di lettura per la sicurezza.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Usare il portale di Azure per visualizzare gli accessi

Per visualizzare l'attività di accesso, seguire questa procedura.

1. Nel **portale di Azure** selezionare **Azure Active Directory**.

1. In **Monitoraggio** selezionare **Accessi**.
   
    ![Screenshot dell'interfaccia utente di Azure con le opzioni Azure Active Directory e Accessi evidenziate.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrare l'applicazione in base a **Microsoft Power BI** o **Power BI Gateway** e selezionare **Applica**.

    **Microsoft Power BI** permette di applicare filtri per l'attività di accesso correlata al servizio, mentre **Power BI Gateway** permette di applicare filtri per l'attività di accesso specifica del gateway dati locale.
   
    ![Screenshot del filtro degli accessi con evidenziato il campo Applicazione evidenziato.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Esportazione dei dati

È possibile [scaricare un report degli accessi](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) in uno dei due formati esistenti: file con estensione csv o file con estensione json.

![Screenshot del pulsante di download.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Nella parte superiore del report degli **accessi** selezionare **Scarica** e una delle opzioni seguenti:

* **CSV** per scaricare un file con estensione csv con i dati attualmente filtrati.

* **JSON** per scaricare un file con estensione json con i dati attualmente filtrati.

## <a name="data-retention"></a>Conservazione dei dati

I dati di accesso rimangono disponibili per un massimo di 30 giorni. Per altre informazioni, vedere [Criteri di conservazione dei report di Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Passaggi successivi

[Uso del controllo nell'organizzazione](service-admin-auditing.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)