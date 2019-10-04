---
ms.openlocfilehash: 6e48713315b23cf322b635f1650374251b639e4f
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409368"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Definire i ruoli e le regole in Power BI Desktop
È possibile definire i ruoli e le regole in Power BI Desktop. Quando si esegue la pubblicazione in Power BI vengono pubblicate anche le definizioni dei ruoli.

Per definire i ruoli di sicurezza, seguire questa procedura.

1. Importare dati nel report di Power BI Desktop o configurare una connessione DirectQuery.
   
   > [!NOTE]
   > Non è possibile definire i ruoli in Power BI Desktop per connessioni dinamiche di Analysis Services. È necessario eseguire questa operazione nel modello di Analysis Services.
   > 
   > 
1. Selezionare la scheda **Creazione di modelli**.
2. Selezionare **Gestisci ruoli**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Selezionare **Crea**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Specificare un nome per il ruolo. 
6. Selezionare la tabella a cui si vuole applicare una regola DAX.
7. Immettere le espressioni DAX. Questa espressione deve restituire true o false. Ad esempio: [Entity ID] = "Valore".
   
   > [!NOTE]
   > È possibile usare *username()* in questa espressione. Si noti che *username()* ha il formato *DOMINIO\nomeutente* in Power BI Desktop. Nel servizio Power BI e nel server di report di Power BI ha il formato del Nome entità utente (UPN) dell'utente stesso. In alternativa è possibile usare *userprincipalname()* , che restituisce sempre l'utente nel formato del nome dell'entità utente, *nomeutente\@contoso.com*.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. Dopo la creazione dell'espressione DAX, è possibile selezionare il segno di spunta sopra la casella dell'espressione per convalidare l'espressione.
      
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > In questa casella dell'espressione si usano le virgole per separare gli argomenti della funzione DAX anche se si usano impostazioni locali che in genere usano il separatore punto e virgola (ad esempio italiano o tedesco). 
   >
   >
   
9. Selezionare **Salva**.

Non è possibile assegnare gli utenti a un ruolo in Power BI Desktop. È necessario assegnarli nel servizio Power BI. È possibile abilitare la sicurezza dinamica in Power BI Desktop usando le funzioni DAX *username()* o *userprincipalname()* e configurando le relazioni appropriate. 

