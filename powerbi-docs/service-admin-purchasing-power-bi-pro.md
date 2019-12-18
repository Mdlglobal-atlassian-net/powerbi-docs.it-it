---
title: Acquistare e assegnare licenze Power BI Pro
description: Informazioni su come acquistare e assegnare licenze utente di Power BI Pro in modo che gli utenti possano accedere al contenuto e collaborare con i colleghi nel servizio Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 55cdfad221aef276c790e98de83dd844bc13aafe
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958700"
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

2. Nel riquadro di spostamento selezionare **Fatturazione** > **Sottoscrizioni**.

    ![Riquadro di spostamento](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Nell'angolo superiore destro della pagina **Sottoscrizioni** selezionare **Aggiungi abbonamenti**.

    ![Sottoscrizione](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Individuare l'offerta di sottoscrizione desiderata:

    In **Enterprise Suite** selezionare **Office 365 Enterprise E5**.

    ![sottoscrizione a Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    In **Altri piani** selezionare **Power BI Pro**.

    ![Sottoscrizione di Power BI](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Passare il mouse sui puntini di sospensione ( **...** ) per la sottoscrizione richiesta e selezionare **Acquista ora**.

    ![Buy Now (Acquista)](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Scegliere **Pagamento mensile** o **Pagamento per un intero anno** in base alle proprie preferenze di fatturazione.

7. In **How many users do you want?** (Numero di utenti) specificare il numero di licenze desiderato e quindi selezionare **Procedi al pagamento** per completare la transazione.

8. Verificare che la sottoscrizione acquisita sia ora indicata nella pagina **Sottoscrizioni**.

   ![Sottoscrizione acquisita](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Per aggiungere altre licenze dopo l'acquisto iniziale, selezionare **Power BI Pro** nella pagina **Sottoscrizioni** e fare clic su **Aggiungi/rimuovi licenze**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Assegnare licenze nell'interfaccia di amministrazione di Microsoft 365

Seguire questi passaggi per assegnare licenze di Power BI Pro a singoli account utente:

1. Aprire l'[interfaccia di amministrazione di Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. Nel riquadro di spostamento espandere **Utenti** e quindi selezionare **Utenti attivi**.

    ![Utenti attivi](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selezionare un utente, quindi in **Licenze di prodotto** selezionare **Modifica**.

    ![Modificare le licenze di prodotto](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. In **Power BI Pro** attivare l'impostazione **Sul** quindi fare clic su **Salva**.

    ![Licenze di prodotto attivate](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Nello **Stato** dell'account selezionato verificare che la licenza di Power BI Pro sia stata assegnata correttamente.

    ![Verificare lo stato della licenza](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Assegnare licenze nel portale di Azure

Seguire questi passaggi per assegnare licenze di Power BI Pro a singoli account utente:

1. Aprire il [portale di Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Nel riquadro di spostamento selezionare **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. In **Azure Active Directory** selezionare **Licenze**.

    ![Licenses](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. In **Licenze** selezionare **Tutti i prodotti** e quindi selezionare **Power BI Pro** per visualizzare l'elenco degli utenti con licenza.

    ![Licenze - Tutti i prodotti](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selezionare **Assegna** per aggiungere una licenza di Power BI Pro a un account utente.

    ![Assegnare la licenza](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Passaggi successivi

Ora che le licenze sono state assegnate, seguire i collegamenti per altre informazioni su Power BI Pro.

[Gestione delle licenze di Power BI nell'organizzazione](service-admin-licensing-organization.md)

[Ricerca di utenti Power BI che hanno eseguito l'accesso](service-admin-access-usage.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
