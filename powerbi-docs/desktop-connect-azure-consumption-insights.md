---
title: Connettersi ai dati di Informazioni dettagliate sul consumo di Azure in Power BI Desktop
description: Connettersi ad Azure e ottenere informazioni dettagliate sull'utilizzo con Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c6987c5849fd2f971c1d7bdc7fe6130dcd09ce59
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761727"
---
# <a name="connect-to-azure-consumption-insights-data-in-power-bi-desktop"></a>Connettersi ai dati di Informazioni dettagliate sul consumo di Azure in Power BI Desktop

È possibile usare Power BI Desktop per connettersi ad Azure e ottenere dati approfonditi sull'utilizzo dei servizi di Azure da parte dell'organizzazione. Con questi dati, è possibile creare misure e report personalizzati per comprendere e analizzare meglio le spese correlate ad Azure.

> [!NOTE]
> È disponibile un supporto limitato per le Informazioni dettagliate sul consumo di Microsoft Azure. Per la nuova funzionalità, usare il connettore [Gestione costi di Azure per Power BI](desktop-connect-azure-cost-management.md).

## <a name="connect-with-azure-consumption-insights"></a>Connettersi con Informazioni dettagliate sul consumo di Azure

Informazioni dettagliate sul consumo di Azure consente di connettersi agli account di fatturazione contratto Enterprise di Azure.

Questa sezione illustra come ottenere i dati necessari per eseguire la migrazione usando il connettore di Azure Enterprise. È disponibile anche un mapping delle *colonne dei dettagli sull'utilizzo* nell'API **ACI** (Azure Consumption Insights, Informazioni dettagliate sul consumo di Azure).

Per usare il connettore **Informazioni dettagliate sul consumo di Azure** è necessario avere accesso alle funzionalità Enterprise nel portale di Azure.

Per usare il connettore **Informazioni dettagliate sul consumo di Azure** in **Power BI Desktop**: 

1. Nella scheda **Home** della barra multifunzione selezionare **Recupera dati**.

1. Dalle categorie a sinistra selezionare **Servizi online**.  

1. Selezionare **Informazioni dettagliate sul consumo di Microsoft Azure (Beta)** . 

1. Selezionare **Connetti**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_01b.png)

   Nella finestra di dialogo visualizzata specificare un valore in **Numero di registrazione di Azure**.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_02.png)

   * È possibile ottenere il numero di registrazione da [Azure Enterprise Portal](https://ea.azure.com), nella posizione indicata nella figura seguente:

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_08.png)

   Questa versione del connettore supporta solo le registrazioni Enterprise da https://ea.azure.com. Le registrazioni per la Cina non sono attualmente supportate.

   Specificare quindi la *chiave di accesso* per la connessione.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_03.png)

   * La chiave di accesso per la registrazione è reperibile in [Azure Enterprise Portal](https://ea.azure.com).

  ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_09.png)

Una volta specificata la *chiave di accesso* e selezionato il pulsante **Connetti**, verrà visualizzata la finestra **Strumento di navigazione** con nove tabelle disponibili:

| Tabella        | Descrizione |
|------------- | -------------------------------------------------------------|
| **Budgets** | Dettagli sui budget per visualizzare i costi effettivi o l'utilizzo rispetto ai target di budget esistenti. |
| **MarketPlace** | Addebiti per Azure Marketplace basati sull'utilizzo. |
| **PriceSheets** | Tariffe applicabili in base al contatore per una registrazione. |
| **RICharges** | Addebiti associati alle istanze riservate negli ultimi 24 mesi. |
| **RIRecommendations_Single** | Raccomandazioni per l'acquisto di istanze riservate in base alle tendenze di utilizzo di una sottoscrizione singola negli ultimi 7, 30 o 60 giorni. |
| **RIRecommendations_Shared** | Raccomandazioni per l'acquisto di istanze riservate in base alle tendenze di utilizzo di tutte le sottoscrizioni negli ultimi 7, 30 o 60 giorni. |
| **RIUsage** | Dettagli relativi al consumo per le istanze riservate nell'ultimo mese. |
| **Summaries** | Un riepilogo mensile di saldi, nuovi acquisti, addebiti per il servizio Azure Marketplace, rettifiche e addebiti per la quantità in eccedenza. |
| **UsageDetails** | Dettaglio delle quantità utilizzate e addebiti stimati per una registrazione. |

È possibile selezionare una casella di controllo accanto a qualsiasi tabella per visualizzare un'anteprima. È possibile selezionare una o più tabelle selezionando la casella di controllo accanto al nome, quindi selezionare **Carica**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_04b.png)

> [!NOTE]
> Le tabelle *Summary* e *PriceSheets* sono disponibili solo per la chiave API a livello di registrazione. I dati in queste tabelle sono per impostazione predefinita i dati del mese corrente per *UsageDetails* e *PriceSheets*. Le tabelle *Summaries* e *MarketPlace* non sono vincolate al mese corrente.
>
>

Quando si seleziona **Carica**, i dati vengono caricati in **Power BI Desktop**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_05.png)

Dopo aver caricato i dati selezionati, è possono visualizzare le tabelle e campi selezionati nel riquadro **Campi**.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_06.png)

## <a name="using-azure-consumption-insights"></a>Uso di Azure Consumption Insights
Per usare il connettore **Informazioni dettagliate sul consumo di Azure** è necessario accedere alle funzionalità Enterprise nel portale di Azure.

Dopo aver caricato correttamente i dati usando il connettore **Informazioni dettagliate sul consumo di Azure**, è possibile creare misure e colonne personalizzate usando l'**Editor di query**. È inoltre possibile creare oggetti visivi, report e dashboard da condividere nel **servizio Power BI**.

Con una query vuota è possibile recuperare una raccolta di query personalizzate di Azure di esempio. L'operazione può essere eseguita in due modi: 

In **Power BI Desktop**: 

1. Selezionare la scheda **Home** della barra multifunzione 
2. Selezionare **Recupera dati** > **Query vuota** 

In alternativa, nell'**Editor di query**: 

1. Fare clic con il pulsante destro del mouse nel riquadro **Query** a sinistra 
2. Selezionare **Nuova query > Query vuota** dal menu visualizzato

Nella **barra della formula** digitare:

    = MicrosoftAzureConsumptionInsights.Contents

L'immagine seguente mostra una raccolta di esempi visualizzata.

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_07.png)

Per usare report e creare query, è possibile eseguire queste operazioni:

* Per definire il numero di mesi a partire dalla data corrente, usare *numberOfMonth*
  * Usare un valore compreso tra 1 e 36. Rappresentare il numero di mesi da importare, a partire dalla data corrente. È consigliabile recuperare non più di 12 mesi di dati. Questo limite consente di evitare di superare le soglie dei vincoli di importazione e il massimo volume di dati consentito per le query in Power BI.
* Per definire un periodo di mesi in una finestra di tempo cronologica, usare *startBillingDataWindow* e *endBillingDataWindow*
* Non usare *numberOfMonth* insieme a *startBillingDataWindow* o *endBillingDataWindow*

## <a name="migrate-from-the-azure-enterprise-connector"></a>Eseguire la migrazione dal connettore di Azure Enterprise

Alcuni clienti hanno creato oggetti visivi con il *connettore di Azure Enterprise (Beta)* che alla fine verrà sostituito con il connettore **Informazioni dettagliate sul consumo di Azure.** Il nuovo connettore offre funzionalità e miglioramenti, tra cui:

* Origini dati aggiuntive disponibili per *Riepilogo saldi* e *Acquisti del Marketplace*
* Nuovi parametri avanzati, ad esempio *startBillingDataWindow* e *endBillingDataWindow*
* Prestazioni e velocità di risposta migliori

I passaggi seguenti mostrano come eseguire la transizione al connettore **Informazioni dettagliate sul consumo di Azure**, conservando il lavoro già svolto con la creazione di dashboard o report personalizzati.

### <a name="step-1-connect-to-azure-using-the-new-connector"></a>Passaggio 1: Connettersi ad Azure usando il nuovo connettore
Il primo passaggio consiste nel connettersi usando il connettore **Informazioni dettagliate sul consumo di Azure**, descritto in dettaglio in una sezione precedente di questo articolo. Selezionare **Recupera dati > Query vuota** nella barra multifunzione **Home** in **Power BI Desktop**.

### <a name="step-2-create-a-query-in-advanced-editor"></a>Passaggio 2: Creare una query nell'Editor avanzato
Nell'**Editor di query** selezionare **Editor avanzato** dalla sezione **Query** della scheda **Home** della barra multifunzione. Nella finestra **Editor avanzato** visualizzata immettere questa query:

    let    
        enrollmentNumber = "100",
        optionalParameters = [ numberOfMonth = 6, dataType="DetailCharges" ],
        data = MicrosoftAzureConsumptionInsights.Contents(enrollmentNumber, optionalParameters)   
    in     
        data

![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_10.png)

È necessario sostituire il valore *enrollmentNumber* con il numero di registrazione. È possibile ottenere il numero dal [portale di Azure Enterprise](https://ea.azure.com). Il parametro *numberOfMonth* indica il numero di mesi di dati da recuperare a partire dai dati correnti. Usare zero (0) per il mese corrente.

Dopo la selezione di **Fine** nella finestra **Editor avanzato** l'anteprima viene aggiornata e nella tabella vengono visualizzati i dati dell'intervallo di mesi specificato. Selezionare **Chiudi e applica** e tornare indietro.

### <a name="step-3-move-measures-and-custom-columns-to-the-new-report"></a>Passaggio 3: Spostare misure e colonne personalizzate nel nuovo report
Successivamente è necessario spostare nella nuova tabella dei dettagli le colonne personalizzate o le misure create. Di seguito sono riportati i passaggi necessari.

1. Aprire Blocco note o un altro editor di testo.
2. Selezionare la misura da spostare, copiare il testo dal campo *Formula* e inserirlo nel Blocco note.

   ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_11.png)
3. Rinominare *Query1* la tabella dei dettagli originale.
4. Per creare nuove misure e colonne personalizzate nella tabella, fare clic con il pulsante destro del mouse sulla tabella e scegliere **Nuova misura**. Quindi tagliare e incollare tutte le misure e le colonne archiviate.

### <a name="step-4-relink-tables-that-had-relationships"></a>Passaggio 4: Collegare nuovamente le tabelle con relazioni
Molti dashboard hanno tabelle aggiuntive che vengono usate per operazioni di ricerca o filtro, ad esempio le tabelle di date o le tabelle usate per progetti personalizzati. Ristabilendo tali relazioni si risolve la maggior parte dei problemi rimanenti. Seguire questa procedura.

- Nella scheda **Creazione di modelli** di **Power BI Desktop** selezionare **Gestisci relazioni** per visualizzare una finestra che consente di gestire le relazioni nel modello. Collegare nuovamente le tabelle in base alle esigenze.

    ![](media/desktop-connect-azure-consumption-insights/azure-consumption-insights_12.png)

### <a name="step-5-verify-your-visuals-and-adjust-field-formatting-as-needed"></a>Passaggio 5: Verificare gli oggetti visivi e modificare la formattazione dei campi in base alle esigenze
A questo punto della procedura, la maggior parte degli oggetti visivi, delle tabelle e dei drill-down originali dovrebbe funzionare come previsto. Potrebbero tuttavia essere necessarie alcune modifiche minime per formattare con precisione l'aspetto. Esaminare ogni dashboard e oggetto visivo per verificare che l'aspetto sia quello desiderato.

## <a name="using-the-azure-consumption-and-insights-aci-api-to-get-consumption-data"></a>Uso dell'API Azure Consumption Insights (ACI) per ottenere dati sul consumo
Azure offre anche l'[**API Azure Consumption Insights (ACI)** ](https://azure.microsoft.com/blog/announcing-general-availability-of-consumption-and-charge-apis-for-enterprise-azure-customers/). È possibile creare soluzioni personalizzate per la raccolta, la creazione di report e la visualizzazione di dati di consumo di Azure tramite l'API ACI.

### <a name="mapping-names-and-usage-details-between-the-portal-the-connector-and-the-api"></a>Mapping di nomi e dettagli di utilizzo tra il portale, il connettore e l'API
I nomi delle colonne e dei dettagli nel portale di Azure sono simili a quelli nell'API e nel connettore, ma non sono sempre identici. Per maggiore chiarezza, nella tabella seguente è riportato il mapping dei nomi. La tabella indica anche se la colonna è obsoleta. Per altre informazioni e definizioni di questi termini, vedere il [dizionario dei dati di fatturazione di Azure](https://docs.microsoft.com/azure/billing/billing-enterprise-api-usage-detail).

| Connettore ACI / ContentPack ColumnName | Nome colonna API ACI | Nome colonna EA | Obsoleta/presente per compatibilità con le versioni precedenti |
| --- | --- | --- | --- |
| AccountName |accountName |Nome account |No |
| AccountId |accountId | |Sì |
| AcccountOwnerId |accountOwnerEmail |AccountOwnerId |No |
| AdditionalInfo |additionalInfo |AdditionalInfo |No |
| AdditionalInfold | | |Sì |
| Quantità consumata |consumedQuantity |Quantità consumata |No |
| Servizio utilizzato |consumedService |Servizio utilizzato |No |
| ConsumedServiceId |consumedServiceId | |Sì |
| Costi |cost |ExtendedCost |No |
| Cost Center |costCenter |Cost Center |No |
| Data |Data |Data |No |
| Giorno | |Giorno |No |
| DepartmentName |departmentName |Department Name |No |
| DepartmentID |departmentId | |Sì |
| ID istanza | | |Sì |
| InstanceId |instanceId |ID istanza |No |
| Location | | |Sì |
| Categoria misuratore |meterCategory |Categoria misuratore |No |
| ID misuratore | | |Sì |
| Nome misuratore |meterName |Nome misuratore |No |
| Area misuratore |meterRegion |Area misuratore |No |
| Sottocategoria misuratore |meterSubCategory |Sottocategoria misuratore |No |
| ID contatore |meterId |ID misuratore |No |
| Month | |Month |No |
| Prodotto |product |Prodotto |No |
| ProductId |productId | |Sì |
| Gruppo di risorse |resourceGroup |Gruppo di risorse |No |
| Percorso della risorsa |resourceLocation |Percorso della risorsa |No |
| ResourceGroupId | | |Sì |
| ResourceLocationId |resourceLocationId | |Sì |
| ResourceRate |resourceRate |ResourceRate |No |
| ServiceAdministratorId |serviceAdministratorId |ServiceAdministratorId |No |
| ServiceInfo1 |serviceInfo1 |ServiceInfo1 |No |
| ServiceInfo1Id | | |Sì |
| ServiceInfo2 |serviceInfo2 |ServiceInfo2 |No |
| ServiceInfo2Id | | |Sì |
| Identificatore del servizio di archiviazione |storeServiceIdentifier |Identificatore del servizio di archiviazione |No |
| StoreServiceIdentifierId | | |Sì |
| Nome sottoscrizione |subscriptionName |Nome sottoscrizione |No |
| Tag |tags |Tag |No |
| TagsId | | |Sì |
| Unit Of Measure |unitOfMeasure |Unit Of Measure |No |
| Year | |Year |No |
| SubscriptionId |subscriptionId |SubscriptionId |Sì |
| SubscriptionGuid |subscriptionGuid |SubscriptionGuid |No |


## <a name="next-steps"></a>Passaggi successivi

È possibile connettersi a molte origini dati diverse usando Power BI Desktop. Per altre informazioni, vedere gli articoli seguenti:

* [Connettersi ai dati di Gestione costi di Azure in Power BI Desktop](desktop-connect-azure-cost-management.md)
* [Che cos'è Power BI Desktop?](desktop-what-is-desktop.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
