---
title: 'Esercitazione: Esplorare Server di report di Power BI in una macchina virtuale'
description: In questa esercitazione si crea una macchina virtuale con Server di Report di Power BI già installato e si esplora il portale Web.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: tutorial
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 38985014407a4d64998e25f6944f57aedcc67309
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445004"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Esercitazione: Esplorare il portale Web di Server di report di Power BI in una macchina virtuale
In questa esercitazione si crea una macchina virtuale di Azure con Server di Report di Power BI già installato per imparare a visualizzare, modificare e gestire report impaginati e indicatori KPI di esempio di Power BI.

![Portale Web del server di report](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

Ecco le attività che si eseguiranno in questa esercitazione:

> [!div class="checklist"]
> * Creare e connettersi a una macchina virtuale
> * Avviare ed esplorare il portale Web di Server di report di Power BI
> * Contrassegnare un elemento preferito
> * Visualizzare e modificare un report di Power BI
> * Visualizzare, gestire e modificare un report impaginato
> * Visualizzare una cartella di lavoro di Excel in Excel Online

Per questa esercitazione è necessaria una sottoscrizione di Azure. Se non se ne ha una, creare un [account gratuito](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) prima di iniziare.

## <a name="create-a-power-bi-report-server-vm"></a>Creare una macchina virtuale per Server di report di Power BI

Il team di Power BI ha creato una macchina virtuale che viene fornita con Server di report di Power BI già installato.

1. In Azure Marketplace aprire [Server di Report di Power BI](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Selezionare **Scarica adesso**.
3. Per accettare le condizioni per l'utilizzo e l'informativa sulla privacy del provider, selezionare **Continua**.

    ![Creare una macchina virtuale per Server di report di Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-virtual-machine-create.png)

4. **Passaggio 1 Informazioni di base**: in **Nome macchina virtuale** inserire **reportservervm**.

5. Creare un nome utente e una password.

6. Per **Gruppo di risorse** mantenere **Crea nuovo** e assegnare il nome **reportserverresourcegroup**.

    Se si visualizza l'esercitazione più di una volta, è necessario assegnare al gruppo di risorse un nome diverso dopo la prima volta. Non è possibile usare lo stesso nome di gruppo di risorse due volte in una sottoscrizione. 

7. Mantenere le altre impostazioni predefinite > **OK**.

    ![Assegnare il nome alla macchina virtuale e al gruppo di risorse](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

8. **Passaggio 2 Impostazioni**: mantenere le impostazioni predefinite > **OK**.

9. **Passaggio 3 Riepilogo** > **OK**.

10. **Passaggio 4**, rivedere le condizioni per l'utilizzo e l'informativa sulla privacy > **Crea**.

    Il processo **Invio della distribuzione per Server di report di Power BI** richiede alcuni minuti.

## <a name="connect-to-your-virtual-machine"></a>Connettersi alla macchina virtuale

1. Nel riquadro di spostamento a sinistra di Azure selezionare **Macchine virtuali**. 

2. Nella casella **Filtra per nome** digitare "report". 

3. Selezionare la macchina virtuale denominata **REPORTSERVERVM**.

    ![Visualizzare la macchina virtuale](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Nella macchina virtuale REPORTSERVERVM selezionare **Connetti**.

    ![Connettersi alla macchina virtuale](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. Nella finestra di dialogo Connessione desktop remoto selezionare **Connetti**.

6. Immettere il nome e la password create per la macchina virtuale > **OK**.

7. La finestra di dialogo successiva indica che non è possibile identificare l'identità del computer remoto. Selezionare **Sì**.

   La nuova macchina virtuale viene aperta.

## <a name="power-bi-report-server-on-the-vm"></a>Server di report di Power BI nella macchina virtuale

Ecco gli elementi che compaiono sul desktop all'apertura della macchina virtuale.

![Avvio della macchina virtuale per Server di report di Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-start-vm-numbered.png)

|Numero  |Descrizione  |
|---------|---------|
|![Numero 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Avvia SQL Server Data Tools per la creazione di report impaginati (con estensione RDL) |
|![Numero 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Report di Power BI di esempio (con estensione PBIX)  |
|![Numero 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Collegamento alla documentazione di Server di Report di Power BI   |
|![Numero 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Avvia Power BI Desktop ottimizzato per Server di report di Power BI (marzo 2018)  |
|![Numero 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Apre il portale Web di Server di report di Power BI nel browser   |

Fare doppio clic sull'icona del **portale Web del server di report**. Il browser apre http://localhost/reports/browse. Nel portale Web sono visibili vari file raggruppati per tipo. 

![Portale Web del server di report di Power BI](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Numero  |Descrizione  |
|---------|---------|
|![Numero 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Indicatori KPI creati nel portale Web |
|![Numero 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Report di Power BI (con estensione PBIX)  |
|![Numero 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Report per dispositivi mobili creati in SQL Server Mobile Report Publisher  |
|![Numero 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Report impaginati creati in Generatore report o SQL Server Data Tools  |
|![Numero 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Cartelle di lavoro di Excel   | 
|![Numero 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Origini dati dei report impaginati | 


## <a name="tag-your-favorites"></a>Contrassegnare gli elementi preferiti
È possibile contrassegnare i report e gli indicatori KPI come preferiti. Sono più semplici da trovare perché sono tutti raccolti in una singola cartella Preferiti nel portale Web e nelle app Power BI per dispositivi mobili. 

1. Selezionare i puntini di sospensione (**...**) nell'angolo superiore destro dell'indicatore KPI **Profit Margin** > **Aggiungi a Preferiti**.
   
    ![Aggiungi a Preferiti](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Selezionare **Preferiti** sulla barra multifunzione del portale Web per visualizzarlo insieme agli altri preferiti nella pagina Preferiti nel portale Web.
   
    ![Visualizzare i preferiti](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Selezionare **Sfoglia** per tornare al portale Web.
   
## <a name="view-items-in-list-view"></a>Visualizzare gli elementi in visualizzazione Elenco
Per impostazione predefinita, il portale Web visualizza il relativo contenuto nella Visualizzazione affiancata.

È possibile passare alla Visualizzazione elenco, in cui è facile spostare o eliminare più elementi contemporaneamente. 

1. Selezionare **Riquadri** > **Elenco**.
   
    ![Cambiare la visualizzazione](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Tornare alla visualizzazione affiancata: selezionare **Elenco** > **Riquadri**.

## <a name="power-bi-reports"></a>Report di Power BI

È possibile visualizzare e interagire con i report di Power BI nel portale Web e avviare Power BI Desktop direttamente dal portale Web.

### <a name="view-power-bi-reports"></a>Visualizzare report di Power BI

1. Nel portale Web in **Report di Power BI** selezionare **Sample Customer Overview Report**. Il report si apre nel browser.

1. Selezionare il blocco United States nella mappa ad albero per vedere come vengono evidenziati i valori correlati negli altri oggetti visivi.

    ![Report di Power BI evidenziato](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Modifica in Power BI Desktop

1. Selezionare **Modifica in Power BI Desktop**.

1. Selezionare **Consenti** per consentire al sito Web di aprire un programma nel computer. 

     Il report si apre in Power BI Desktop. Si noti il nome nella barra superiore, "Power BI Desktop (marzo 2018)". Si tratta della versione ottimizzata per Server di report di Power BI.

    ![Power BI Desktop](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-desktop.png)

     Usare la versione di Power BI Desktop che viene installata nella macchina virtuale. Non è possibile passare da un dominio all'altro per caricare un report.

3. Nel riquadro Campi espandere la tabella Customers e trascinare il campo Occupation nei filtri a livello di report.

    ![Trascinare un campo nel riquadro Filtri](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Salvare il report.

1. Tornare al report nel browser e selezionare l'icona **Aggiorna** del browser.

    ![Icona di aggiornamento del browser](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Espandere il riquadro **Filtri** per visualizzare il filtro **Occupation** aggiunto. Selezionare **Professional**.

    ![Report di Power BI filtrato](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Selezionare **Sfoglia** per tornare al portale Web.

## <a name="paginated-rdl-reports"></a>Report impaginati (RDL)

È possibile visualizzare e gestire report impaginati e avviare Generatore report tramite il portale Web.

### <a name="manage-a-paginated-report"></a>Gestire un report impaginato

1. Nel portale Web, in **Report impaginati**, selezionare i puntini di sospensione (...) accanto a **Sales Order** > **Gestisci**.

1. Selezionare **Parametri**, modificare il valore predefinito per **SalesOrderNumber** in **SO50689** > **Applica**.

   ![Impostare i parametri del report](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Selezionare **Sfoglia** per tornare al portale Web.

### <a name="view-a-paginated-report"></a>Visualizzare un report impaginato

1. Selezionare **Sales Order** nel portale Web.
 
3.  Il report si apre sul parametro **Order** impostato, **SO50689**. 

    ![Parametro del report impaginato](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Qui è possibile modificare questo e altri parametri senza modificare le impostazioni predefinite.

1. Selezionare **ordine** **SO48339** > **visualizzare Report**.

4. Si noti che questa è la pagina 1 di 2. Selezionare la freccia a destra per vedere la seconda pagina. La tabella continua a pagina 2.

    ![Pagina 2 di 2 del report impaginato](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Selezionare **Sfoglia** per tornare al portale Web.

### <a name="edit-a-paginated-report"></a>Modificare un report impaginato

È possibile modificare i report impaginati in Generatore report, che si può avviare direttamente dal browser.

1. Nel portale Web selezionare i puntini di sospensione (...) accanto a **Sales Order** > **Modifica in Generatore report**.

1. Selezionare **Consenti** per consentire al sito Web di aprire un programma nel computer.

1. Il report Sales Order si apre in Generatore report in visualizzazione Progettazione.

    ![Visualizzazione Progettazione, report impaginato](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Selezionare **Esegui** per visualizzare in anteprima il report.

    ![Visualizzare in anteprima un report impaginato](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Chiudere Generatore Report e tornare al browser.

## <a name="view-excel-workbooks"></a>Visualizzare cartelle di lavoro di Excel

È possibile visualizzare e interagire con le cartelle di lavoro di Excel in Excel Online in Server di Report di Power BI. 

1. Selezionare la cartella di lavoro di Excel **Office Liquidation Sale.xlsx**. È possibile che vengano chieste le credenziali. Selezionare **Annulla**. 
    La cartella di lavoro si apre nel portale Web.
1. Selezionare **Appliance** nel filtro dei dati.

    ![Excel Online nel portale Web](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Selezionare **Sfoglia** per tornare al portale Web.

## <a name="clean-up-resources"></a>Pulire le risorse

Una volta completata l'esercitazione, eliminare il gruppo di risorse, la macchina virtuale e tutte le risorse correlate. 

- A questo scopo, selezionare il gruppo di risorse per la macchina virtuale e quindi selezionare **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stata creata una macchina virtuale con Server di Report di Power BI. Si è provato a usare alcune delle funzionalità del portale Web e si sono aperti un report di Power BI e un report impaginato nei rispettivi editor. Questa macchina virtuale possiede origini dati di SQL Server Analysis Services installate, pertanto è possibile provare a creare la propria Power BI e report impaginati con le stesse origini dati. 

Per altre informazioni sulla creazione di report per Server di Report di Power BI, continuare a leggere.

> [!div class="nextstepaction"]
> [Creare un report di Power BI per Server di report di Power BI](./quickstart-create-powerbi-report.md)



