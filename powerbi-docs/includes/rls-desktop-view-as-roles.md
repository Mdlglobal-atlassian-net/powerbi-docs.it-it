---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464407"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Convalidare i ruoli in Power BI Desktop
Dopo aver creato i ruoli è possibile testare i risultati corrispondenti all'interno di Power BI Desktop.

1. Dalla scheda **Creazione di modelli** selezionare **Visualizza come ruoli**. 

    ![Selezionare Visualizza come ruoli](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Verrà aperta la finestra **Visualizza come ruoli** in cui sono visualizzati i ruoli creati.

    ![Finestra Visualizza come ruoli](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Selezionare un ruolo creato e quindi scegliere **OK** per applicare il ruolo. 

   Il report esegue il rendering dei dati pertinenti a tale ruolo.

4. È anche possibile selezionare **Altro utente** e indicare un determinato utente. 

    ![Selezionare Altro utente](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   È consigliabile specificare il nome dell'entità utente (UPN), che verrà usato dal servizio Power BI e dal server di report Power BI.

   All'interno di Power BI Desktop l'opzione **Altro utente** visualizza risultati diversi solo se si usa la sicurezza dinamica basata sulle espressioni DAX. 

5. Scegliere **OK**. 

   Il rendering del report viene eseguito in base ai dati visibili all'utente.



