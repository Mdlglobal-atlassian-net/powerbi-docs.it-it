---
title: Acquistare e assegnare licenze Power BI Pro
description: Informazioni su come acquistare e assegnare licenze Power BI Pro in modo che gli utenti possano accedere a tutto il contenuto e a tutte le funzionalità del servizio Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/21/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 76288ca77f184b27b5839377190a1708c69567af
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430695"
---
# <a name="purchase-and-assign-power-bi-pro-licenses"></a>Acquistare e assegnare licenze Power BI Pro

Power BI Pro è una licenza singola che consente di accedere a tutto il contenuto e a tutte le funzionalità del servizio Power BI, inclusa la possibilità di condividere contenuto e collaborare con altri utenti Pro. Solo gli utenti della versione Pro possono pubblicare e usare contenuti nelle aree di lavoro delle app, condividere i dashboard e sottoscrivere dashboard e report. Per altre informazioni, vedere [Funzionalità di Power BI in base al tipo di licenza](service-features-license-type.md).

Nella prima parte di questo articolo viene illustrato come acquistare licenze Power BI Pro in Office 365. In seguito vengono descritte le due opzioni disponibili per assegnare le licenze per singoli utenti: Office 365 e Azure (scegliere un'opzione).

## <a name="prerequisites"></a>Prerequisiti

È necessario essere membro del ruolo [**Amministratore globale** o **Amministratore fatturazione**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) in Office 365.

Per assegnare le licenze in Azure, è necessario essere proprietario della sottoscrizione di Azure usata da Power BI per le ricerche di Active Directory.

## <a name="purchase-licenses-in-office-365"></a>Acquistare licenze in Office 365

Seguire questi passaggi per acquistare licenze di Power BI Pro:

1. Aprire l'[interfaccia di amministrazione di Office 365](https://portal.office.com/adminportal/home#/homepage).

2. Nel riquadro di spostamento a sinistra selezionare **Fatturazione** > **Abbonamenti**.

    ![Riquadro di spostamento](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Nell'angolo superiore destro della pagina **Sottoscrizioni** selezionare **Aggiungi abbonamenti**.

    ![Sottoscrizione](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Individuare l'offerta di sottoscrizione desiderata:

    In **Enterprise Suite** selezionare **Office 365 Enterprise E5**.

    ![sottoscrizione a Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    In **Altri piani** selezionare **Power BI Pro**.

    ![Sottoscrizione di Power BI](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Passare il mouse sui puntini di sospensione (**...**) per la sottoscrizione richiesta e selezionare **Acquista ora**.

    ![Buy Now (Acquista)](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Scegliere **Pagamento mensile** o **Pagamento per un intero anno** in base alle proprie preferenze di fatturazione.

7. In **How many users do you want?** (Numero di utenti) specificare il numero di licenze desiderato e quindi selezionare **Procedi al pagamento** per completare la transazione.

8. Verificare che la sottoscrizione acquisita sia ora indicata nella pagina **Sottoscrizioni**.

   ![Sottoscrizione acquisita](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Per aggiungere altre licenze dopo l'acquisto iniziale, selezionare **Power BI Pro** nella pagina **Sottoscrizioni** e fare clic su **Aggiungi/rimuovi licenze**.

## <a name="assign-licenses-in-office-365"></a>Assegnare licenze in Office 365

Seguire questi passaggi per assegnare licenze di Power BI Pro a singoli account utente:

1. Aprire l'[interfaccia di amministrazione di Office 365](https://portal.office.com/adminportal/home#/homepage).

2. Nel riquadro di spostamento a sinistra espandere **Utenti** e quindi selezionare **Utenti attivi**.

    ![Utenti attivi](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selezionare un utente, quindi in **Licenze di prodotto** selezionare **Modifica**.

    ![Modificare le licenze di prodotto](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. In **Power BI Pro** attivare l'impostazione **Sul** quindi fare clic su **Salva**.

    ![Licenze di prodotto attivate](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Nello **Stato** dell'account selezionato verificare che la licenza di Power BI Pro sia stata assegnata correttamente.

    ![Verificare lo stato della licenza](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

## <a name="assign-licenses-in-azure"></a>Assegnare licenze in Azure

Seguire questi passaggi per assegnare licenze di Power BI Pro a singoli account utente:

1. Aprire il [portale di Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Nella barra di spostamento a sinistra selezionare **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. In **Azure Active Directory** selezionare **Licenze**.

    ![Licenses](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. In **Licenze** selezionare **Tutti i prodotti** e quindi selezionare **Power BI Pro** per visualizzare l'elenco degli utenti con licenza.

    ![Licenze - Tutti i prodotti](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selezionare **Assegna** per aggiungere una licenza di Power BI Pro a un altro account utente.

    ![Assegnare la licenza](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Passaggi successivi

Ora che le licenze sono state assegnate, seguire i collegamenti per altre informazioni su Power BI Pro.

[Gestione delle licenze di Power BI nell'organizzazione](service-admin-licensing-organization.md)

[Ricerca di utenti Power BI che hanno eseguito l'accesso](service-admin-access-usage.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
