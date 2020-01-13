---
title: Acquistare e assegnare licenze Power BI Pro
description: Informazioni su come acquistare e assegnare licenze utente di Power BI Pro in modo che gli utenti possano accedere al contenuto e collaborare con i colleghi nel servizio Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 12/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 01eb30857b0b76f96e7e18115d92fb1d68dbef0c
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223838"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Acquistare e assegnare licenze utente di Power BI Pro

Power BI Pro è una licenza utente singola che consente agli utenti di leggere i report e i dashboard pubblicati da altri utenti nel servizio Power BI e di interagire con essi, nonché di condividere contenuto e collaborare con altri utenti di Power BI Pro. Solo gli utenti con una licenza utente di Power BI Pro possono pubblicare o condividere contenuto con altri utenti o utilizzare contenuto creato da altri utenti, a meno che il contenuto non sia ospitato in una capacità Power BI Premium. Per altre informazioni, vedere la sezione _Confronto tra funzionalità di Power BI_ di [Prezzi di Power BI](https://powerbi.microsoft.com/pricing/).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Acquistare e assegnare licenze utente di Power BI Pro

Questo articolo spiega come acquistare licenze utente di Power BI Pro nell'interfaccia di amministrazione di Microsoft 365 e quindi illustra due opzioni disponibili per gli amministratori per l'assegnazione di tali licenze a singoli utenti: nell'interfaccia di amministrazione di Microsoft 365 e nel portale di Azure (scegliere un'opzione).

### <a name="prerequisites"></a>Prerequisiti

Per acquistare e assegnare licenze nell'interfaccia di amministrazione di Microsoft 365, è necessario essere membro del ruolo **[Amministratore globale o Amministratore fatturazione](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** in Microsoft 365.

Per assegnare le licenze nel portale di Azure, è necessario essere proprietario della sottoscrizione di Azure usata da Power BI per le ricerche con Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Acquistare licenze in Microsoft 365

Seguire questa procedura per acquistare licenze di Power BI Pro nell'interfaccia di amministrazione di Microsoft 365:

1. Aprire l'[interfaccia di amministrazione di Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. Nel riquadro di spostamento selezionare **Fatturazione** e quindi selezionare **Sottoscrizioni**.

3. Nell'angolo superiore destro della pagina **Sottoscrizioni** selezionare **Aggiungi abbonamenti**.

4. Individuare l'offerta di sottoscrizione desiderata:

    - In **Enterprise Suite** selezionare **Office 365 Enterprise E5**.

    - In **Altri piani** selezionare **Power BI Pro**.

5. Passare il mouse sui puntini di sospensione ( **...** ) per la sottoscrizione richiesta e selezionare **Acquista ora**.

6. Scegliere **Pagamento mensile** o **Pagamento per un intero anno** in base alle proprie preferenze di fatturazione.

7. In **How many users do you want?** (Numero di utenti) specificare il numero di licenze desiderato e quindi selezionare **Procedi al pagamento** per completare la transazione.

8. Verificare che la sottoscrizione acquisita sia ora indicata nella pagina **Sottoscrizioni**.

9. Per aggiungere altre licenze dopo l'acquisto iniziale, selezionare **Power BI Pro** nella pagina **Sottoscrizioni** e quindi selezionare **Cambia la quantità di licenze**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Assegnare licenze nell'interfaccia di amministrazione di Microsoft 365

Per informazioni sull'assegnazione di licenze nell'interfaccia di amministrazione di Microsoft 365, vedere [Assegnare licenze agli utenti](/office365/admin/manage/assign-licenses-to-users).

Per gli utenti guest, vedere [Assegnare licenze agli utenti nella pagina Licenze](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Prima di assegnare le licenze Pro agli utenti guest, contattare il rappresentante dell'account Microsoft per assicurarsi della conformità con i termini del contratto con Microsoft.

### <a name="assign-licenses-in-the-azure-portal"></a>Assegnare licenze nel portale di Azure

Seguire questi passaggi per assegnare licenze di Power BI Pro a singoli account utente:

1. Aprire il [portale di Azure](https://portal.azure.com/).

2. Cercare e selezionare **Azure Active Directory**.

3. In **Azure Active Directory** selezionare **Licenze**.

4. In **Licenze** selezionare **Tutti i prodotti** e quindi selezionare **Power BI Pro** per visualizzare l'elenco degli utenti con licenza.

5. Selezionare **Assegna** per aggiungere una licenza di Power BI Pro a un account utente.

## <a name="next-steps"></a>Passaggi successivi

Ora che le licenze sono state assegnate, seguire i collegamenti per altre informazioni su Power BI Pro.

[Gestione delle licenze di Power BI nell'organizzazione](service-admin-licensing-organization.md)

[Ricerca di utenti Power BI che hanno eseguito l'accesso](service-admin-access-usage.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
