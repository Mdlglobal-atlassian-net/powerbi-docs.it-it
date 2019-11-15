---
title: Azure SQL Data Warehouse con DirectQuery
description: Azure SQL Data Warehouse con DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.custom: ''
ms.date: 06/20/2018
LocalizationGroup: Data from databases
ms.openlocfilehash: 2e96b88963250d7ac11cf9690c63b431279d585a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873255"
---
# <a name="azure-sql-data-warehouse-with-directquery"></a>Azure SQL Data Warehouse con DirectQuery

Azure SQL Data Warehouse con DirectQuery consente di creare report dinamici basati su dati e metriche già presenti in Azure SQL Data Warehouse. Con DirectQuery, le query vengono reinviate ad Azure SQL Data Warehouse in tempo reale durante l'esplorazione dei dati. Le query in tempo reale, unite alla scalabilità di SQL Data Warehouse, consentono agli utenti di creare in pochi minuti report dinamici in base a svariati terabyte di dati. Per di più, l'introduzione del pulsante **Apri in Power BI** consente agli utenti di connettere Power BI direttamente ad SQL Data Warehouse senza dover specificare manualmente le informazioni.

Quando si usa il connettore SQL Data Warehouse:

* Specificare il nome completo del server durante la connessione (vedere di seguito per i dettagli)
* Verificare che le regole firewall per il server siano configurate su "Consenti l'accesso a Servizi di Azure"
* A ogni azione, come la selezione di una colonna o l'aggiunta di un filtro, verrà inviata una query direttamente al data warehouse
* I riquadri vengono aggiornati all'incirca ogni 15 minuti.  È possibile regolare questo intervallo nelle impostazioni avanzate al momento della connessione.
* La funzione Domande e risposte non è disponibile per i set di dati di DirectQuery
* Le modifiche allo schema non vengono selezionate automaticamente

Queste restrizioni e note possono cambiare dal momento che le esperienze vengono costantemente migliorate. La procedura per la connessione è illustrata di seguito.

## <a name="using-the-open-in-power-bi-button"></a>Uso del pulsante "Apri in Power BI"

> [!Important]
> La connettività ad Azure SQL Data Warehouse è stata migliorata.  Per connettersi in modo ottimale all'origine dati di Azure SQL Data Warehouse, usare Power BI Desktop.  Dopo avere compilato il modello e il report, è possibile pubblicarlo nel servizio Power BI.  Il connettore diretto per Azure SQL Data Warehouse nel servizio Power BI ora è deprecato.

Il modo più semplice per spostarsi tra SQL Data Warehouse e Power BI consiste nell'usare il pulsante **Apri in Power BI** nel portale di Azure, che consente di iniziare a creare facilmente nuovi dashboard in Power BI.

1. Per iniziare, passare all'istanza di SQL Data Warehouse nel portale di Azure. Si noti che, al momento, solo SQL Data Warehouse è presente nel portale di Azure.

2. Fare clic sul pulsante **Apri in Power BI**

    ![Apri in Power BI](media/service-azure-sql-data-warehouse-with-direct-connect/openinpowerbi.png)

3. Se non è possibile accedere direttamente oppure non è disponibile un account di Power BI, sarà necessario eseguire l'accesso.

4. Si verrà reindirizzati alla pagina di connessione di SQL Data Warehouse, precompilata con le informazioni relative al proprio SQL Data Warehouse. Immettere le proprie credenziali e premere Connetti per creare una connessione.

## <a name="connecting-through-power-bi"></a>Connessione tramite Power BI

SQL Data Warehouse è elencato anche nella pagina Recupera dati di Power BI. 

1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento.  

    ![Pulsante Recupera dati](media/service-azure-sql-data-warehouse-with-direct-connect/getdatabutton.png)

2. In **Database**, selezionare **Recupera**.

    ![Database](media/service-azure-sql-data-warehouse-with-direct-connect/databases.png)

3. Selezionare **SQL Data Warehouse**\>**Connetti**.

    ![Azure SQL DW con connessione diretta](media/service-azure-sql-data-warehouse-with-direct-connect/azuresqldatawarehouseconnect.png)

4. Immettere le informazioni necessarie per connettersi. La sezione **Trovare i valori dei parametri** indica la posizione di questi dati nel portale di Azure.

    ![Nome del server](media/service-azure-sql-data-warehouse-with-direct-connect/servername.png)

    ![Nome del server avanzato](media/service-azure-sql-data-warehouse-with-direct-connect/servernamewithadvanced.png)

    ![Nome utente](media/service-azure-sql-data-warehouse-with-direct-connect/username.png)

   > [!NOTE]
   > Il nome utente sarà un utente che viene definito nell'istanza di Azure SQL Data Warehouse.

5. Analizzare il set di dati selezionando il nuovo riquadro oppure il set di dati appena creato, indicato dall'asterisco. Questo set di dati avrà lo stesso nome del proprio database.

    ![Set di dati 2](media/service-azure-sql-data-warehouse-with-direct-connect/dataset2.png)

6. È possibile esplorare tutte le tabelle e le colonne. Selezionando una colonna verrà inviata una query all'origine e verrà quindi creato dinamicamente l'oggetto visivo. I filtri verranno anche convertiti in query nel proprio data warehouse. Questi elementi visivi possono essere salvati in un nuovo report e aggiunti al proprio dashboard.

    ![Esplora 3](media/service-azure-sql-data-warehouse-with-direct-connect/explore3.png)

## <a name="finding-parameter-values"></a>Trovare i valori dei parametri

I nomi completi del server e del database sono disponibili nel portale di Azure. Si noti che, al momento, solo SQL Data Warehouse è presente nel portale di Azure.

![Portale di Azure](media/service-azure-sql-data-warehouse-with-direct-connect/azureportal.png)

> [!NOTE]
> Se il tenant di Power BI è nella stessa area di Azure SQL Data Warehouse non saranno applicati costi di uscita. Per sapere dove si trova il tenant di Power BI usare [queste istruzioni](https://docs.microsoft.com/power-bi/service-admin-where-is-my-tenant-located).

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>Passaggi successivi

* [Che cos'è Power BI?](fundamentals/power-bi-overview.md)  
* [Recuperare dati per Power BI](service-get-data.md)  
* [Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is/)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
