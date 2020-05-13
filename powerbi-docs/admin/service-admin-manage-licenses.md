---
title: Visualizzare e gestire le licenze utente di Power BI
description: Informazioni per gli amministratori sulle procedure per la visualizzazione e la gestione delle licenze utente di Power BI nell'organizzazione.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 2d5eab5dbbf600227611cadc870fab1b3e44a4b7
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83138891"
---
# <a name="view-and-manage-power-bi-user-licenses"></a>Visualizzare e gestire le licenze utente di Power BI

Questo articolo illustra come gli amministratori possono usare l'interfaccia di amministrazione di Microsoft 365 o il portale di Azure per visualizzare e gestire le licenze utente.

> [!NOTE]
>
>È possibile che a un utente sia assegnata sia una licenza di Power BI (gratuito) che una licenza di Power BI Pro. Questa situazione può verificarsi quando un utente si iscrive per ottenere una licenza gratuita e successivamente gli viene assegnata una licenza di Power BI Pro. In questo caso diventa effettivo il livello di licenza più elevato.
>

## <a name="view-your-subscriptions"></a>Visualizzare le sottoscrizioni

Per visualizzare le sottoscrizioni di Power BI dell'organizzazione, seguire questa procedura.

1. Accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com).
2. Nel menu di spostamento selezionare **Fatturazione** > **Prodotti e servizi**.

Le sottoscrizioni di Power BI attive vengono elencate insieme a qualsiasi altra sottoscrizione disponibile. È possibile che venga visualizzata una sottoscrizione imprevista per Power BI (gratuito), come nella figura seguente.

  ![Sottoscrizione attivata dall'utente gratuita di Power BI](media/service-admin-manage-licenses/power-bi-free-user-activated.png)

Questo tipo di sottoscrizione viene creata automaticamente quando gli utenti eseguono l'iscrizione in modalità self-service. Per altre informazioni, vedere [Power BI nell'organizzazione](https://docs.microsoft.com/microsoft-365/admin/misc/power-bi-in-your-organization?view=o365-worldwide).

## <a name="manage-user-licenses-in-microsoft-365"></a>Gestire le licenze utente in Microsoft 365

Per usare l'interfaccia di amministrazione di Microsoft 365 per gestire le licenze utente, vedere la [documentazione relativa alle sottoscrizioni aziendali e alla fatturazione](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide).

## <a name="manage-user-licenses-in-azure-portal"></a>Gestire le licenze utente nel portale di Azure

Seguire questa procedura per visualizzare e assegnare le licenze di Power BI usando il portale di Azure.

1. Accedere al [portale di Azure](https://portal.azure.com).

2. Cercare e selezionare **Azure Active Directory**.

3. In **Gestione** nel menu delle risorse di Azure Active Directory selezionare **Licenze**.

4. Selezionare **Tutti i prodotti** dal menu delle risorse e quindi selezionare un tipo di licenza di Power BI per visualizzare l'elenco degli utenti con licenza.

5. Per assegnare una licenza, scegliere **+ Assegna** dalla barra dei comandi. Nella pagina **Assegna licenza** scegliere un utente e quindi selezionare **Opzioni di assegnazione** per attivare una licenza di Power BI Pro per l'account utente selezionato.

6. Per rimuovere una licenza, selezionare la casella di controllo accanto al nome dell'utente e quindi selezionare **Rimuovi licenza**.

## <a name="next-steps"></a>Passaggi successivi

- [Acquistare Power BI Pro](service-admin-purchasing-power-bi-pro.md)
- [Gestione delle licenze per l'organizzazione](service-admin-licensing-organization.md)
