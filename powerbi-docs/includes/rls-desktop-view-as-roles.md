---
ms.openlocfilehash: 0ef0f2e250c61f11cc6418635a8e132242201072
ms.sourcegitcommit: 2c49a7cee9c77f46830ddfa59fdedbf30186d389
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54488994"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Convalidare i ruoli in Power BI Desktop
Dopo aver creato i ruoli è possibile testare i risultati corrispondenti all'interno di Power BI Desktop.

1. Selezionare  **Visualizza come ruoli**. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    In **Visualizza come ruoli** è possibile visualizzare i ruoli creati.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Selezionare un ruolo creato > **OK**  per applicare il ruolo. Il report esegue il rendering dei dati pertinenti a tale ruolo. 

4. È anche possibile selezionare **Altro utente** e indicare un determinato utente. È consigliabile specificare il nome dell'entità utente (UPN), che verrà usato dal servizio Power BI e dal server di report Power BI.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. Selezionare  **OK** . Il rendering del report viene eseguito in base ai dati visibili all'utente. 

All'interno di Power BI Desktop l'opzione **Altro utente** visualizza risultati diversi solo se si usa la sicurezza dinamica basata sulle espressioni DAX. 

