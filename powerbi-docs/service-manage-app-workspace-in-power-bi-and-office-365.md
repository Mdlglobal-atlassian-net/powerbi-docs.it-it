---
title: Gestire l'area di lavoro in Power BI e Office 365
description: Le aree di lavoro in Power BI costituiscono un'esperienza di collaborazione basata sui gruppi di Office 365. È possibile gestire le aree di lavoro sia in Power BI che in Office 365.
author: maggiesMSFT
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 72694ea771950b4a12427e0a0696e221fbe993bf
ms.sourcegitcommit: d65da4738f011beec8f4423085cbd483511cdfb0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2020
ms.locfileid: "78237846"
---
# <a name="manage-your-workspace-in-power-bi-and-office-365"></a>Gestire l'area di lavoro in Power BI e Office 365

Il creatore o l'amministratore di un'[area di lavoro in Power BI](service-create-distribute-apps.md) o in Office 365 può gestire alcuni aspetti dell'area di lavoro in Power BI, mentre altri devono essere gestiti in Office 365.

> [!NOTE]
> La nuova esperienza dell'area di lavoro cambia la relazione tra le aree di lavoro di Power BI e i gruppi di Office 365. Non viene creato automaticamente un gruppo di Office 365 ogni volta che si crea una delle nuove aree di lavoro. Informazioni sulla [creazione di nuove aree di lavoro](service-create-the-new-workspaces.md).

In **Power BI** è possibile:

* Aggiungere o rimuovere membri dell'area di lavoro, nonché impostare un membro dell'area di lavoro come amministratore.
* Modificare il nome dell'area di lavoro.
* Eliminare l'area di lavoro. Viene eliminato anche il gruppo di Office 365.

In **Office 365** è possibile:

* Aggiungere o rimuovere i membri del gruppo dell'area di lavoro, nonché impostare un membro come proprietario.
* Modificare il nome, l'immagine, la descrizione e altre impostazioni del gruppo.
* Visualizzare l'indirizzo di posta elettronica del gruppo.
* Eliminare il gruppo.

Per diventare amministratore o membro di un'area di lavoro è necessaria una [licenza di Power BI Pro](service-features-license-type.md). Anche gli utenti delle app devono avere una licenza di Power BI Pro, a meno che l'area di lavoro non sia inclusa in una capacità di Power BI Premium. Per informazioni dettagliate, leggere [What is Power BI Premium?](service-premium-what-is.md) (Che cos'è Power BI Premium?).

## <a name="edit-your-workspace-in-power-bi"></a>Modificare l'area di lavoro in Power BI

1. Nel servizio Power BI fare clic sulla freccia accanto ad **Aree di lavoro** > selezionare **Altre opzioni** (...) accanto al nome dell'area di lavoro > **Modifica questa area di lavoro**.

   ![Modificare le aree di lavoro in Power BI](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-ellipsis.png)

   > [!NOTE]
   > L'opzione **Modifica questa area di lavoro** viene visualizzata solo se l'utente è un amministratore dell'area di lavoro.

1. In questa schermata è possibile rinominare l'area di lavoro, aggiungere o rimuovere membri o eliminare l'area di lavoro.

   ![Finestra di dialogo Modifica area di lavoro](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-edit-workspace.png)

1. Selezionare **Salva** o **Annulla**.

## <a name="edit-power-bi-workspace-properties-in-office-365"></a>Modificare le proprietà dell'area di lavoro di Power BI in Office 365

È anche possibile modificare gli aspetti di un'area di lavoro direttamente in Outlook per Office 365.

### <a name="edit-the-members-of-the-workspace-group"></a>Modificare i membri del gruppo dell'area di lavoro

1. Nel servizio Power BI selezionare la freccia accanto ad **Aree di lavoro** > selezionare **Altre opzioni** (...) accanto al nome dell'area di lavoro > **Membri**.

   ![Modificare le aree di lavoro in Power BI](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-ellipsis-members.png)

   Verrà aperta la visualizzazione del gruppo di Outlook per Office 365 per l'area di lavoro. Potrebbe essere necessario accedere all'account aziendale.

1. Selezionare il ruolo accanto al nome del collega per impostarlo come **Membro** o **Proprietario**. Selezionare il simbolo **X** per rimuovere la persona dal gruppo.

   ![Modificare un gruppo in Office 365](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_managegroupo365.png)

### <a name="add-an-image-and-set-other-workspace-properties"></a>Aggiungere un'immagine e impostare altre proprietà dell'area di lavoro

Quando si distribuisce l'app dall'area di lavoro, l'immagine aggiunta qui diventa l'immagine dell'app. Vedere [Aggiungere un'immagine all'area di lavoro di Office 365](service-create-workspaces.md#add-an-image-to-your-office-365-workspace-optional) nell'articolo **Creare le nuove aree di lavoro**.

1. Nella visualizzazione Outlook per Office 365 dell'area di lavoro passare alla scheda **Informazioni su** e selezionare **Modifica**.

    ![Icona Modifica gruppo](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_editgroupo365.png)
1. È possibile modificare il nome, la descrizione e la lingua per le notifiche relative al gruppo. È anche possibile aggiungere un'immagine e impostare altre proprietà.

   ![Finestra di dialogo Modifica gruppo](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_editgrpo365dialog.png)

1. Selezionare **Salva** o **Rimuovi**.

## <a name="next-steps"></a>Passaggi successivi

* [Pubblicare un'app in Power BI](service-create-distribute-apps.md)

* Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
