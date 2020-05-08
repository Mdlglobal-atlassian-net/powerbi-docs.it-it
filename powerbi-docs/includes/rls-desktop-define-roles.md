---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464455"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definire i ruoli e le regole in Power BI Desktop
È possibile definire i ruoli e le regole in Power BI Desktop. Quando si esegue la pubblicazione in Power BI vengono pubblicate anche le definizioni dei ruoli.

Per definire i ruoli di sicurezza, seguire questa procedura.

1. Importare dati nel report di Power BI Desktop o configurare una connessione DirectQuery.
   
   > [!NOTE]
   > Non è possibile definire i ruoli in Power BI Desktop per connessioni dinamiche di Analysis Services. È necessario eseguire questa operazione nel modello di Analysis Services.
   > 
   > 
2. Dalla scheda **Creazione di modelli** selezionare **Gestisci ruoli**.
   
   ![Selezionare Gestisci ruoli](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. Nella finestra **Gestisci ruoli** selezionare **Crea**.
   
   ![Selezionare Crea](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. In **Ruoli** specificare un nome per il ruolo. 
5. In **Tabelle** selezionare la tabella a cui si vuole applicare una regola DAX.
6. Nella casella **Espressione DAX filtro tabella** immettere le espressioni DAX. Questa espressione restituisce un valore true o false. Ad esempio: ```[Entity ID] = “Value”```.
      
   ![Finestra Gestisci ruoli](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > È possibile usare *username()* in questa espressione. Si noti che *username()* ha il formato *DOMINIO\nomeutente* in Power BI Desktop. Nel servizio Power BI e nel server di report di Power BI ha il formato del Nome entità utente (UPN) dell'utente stesso. In alternativa è possibile usare *userprincipalname()* , che restituisce sempre l'utente nel formato del nome dell'entità utente, *nomeutente\@contoso.com*.
   > 
   > 

7. Dopo la creazione dell'espressione DAX, è possibile selezionare il segno di spunta sopra la casella dell'espressione per convalidarla.
      
   ![Convalidare l'espressione DAX](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > In questa casella dell'espressione si usano le virgole per separare gli argomenti della funzione DAX anche se si usano impostazioni locali che in genere usano il separatore punto e virgola (ad esempio italiano o tedesco). 
   >
   >
   
8. Selezionare **Salva**.

Non è possibile assegnare gli utenti a un ruolo in Power BI Desktop. È necessario assegnarli nel servizio Power BI. È possibile abilitare la sicurezza dinamica in Power BI Desktop usando le funzioni DAX *username()* o *userprincipalname()* e configurando le relazioni appropriate. 

