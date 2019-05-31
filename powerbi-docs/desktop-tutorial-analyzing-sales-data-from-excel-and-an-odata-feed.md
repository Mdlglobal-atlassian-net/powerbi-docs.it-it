---
title: 'Esercitazione: Combinare dati da Excel e da un feed OData in Power BI Desktop'
description: 'Esercitazione: Combinare dati da Excel e da un feed OData'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 94e40681d065591db008f8a9062d851e0bd83f61
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61368561"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Esercitazione: Combinare dati di vendita da Excel e da un feed OData

La presenza dei dati in più origini dati diverse, ad esempio le informazioni sui prodotti in un database e le informazioni di vendita in un altro, è abbastanza comune. Con **Power BI Desktop** è possibile combinare dati provenienti da origini diverse per creare analisi e visualizzazioni dei dati interessanti e stimolanti. 

In questa esercitazione viene illustrato come combinare dati da due origini dati: una cartella di lavoro di Excel che include informazioni sui prodotti e un feed OData contenente i dati degli ordini. Dopo avere importato tutti i set di dati e avere eseguito i passaggi per la trasformazione e l'aggregazione, si useranno i dati di entrambe le origini per produrre un report di analisi delle vendite con visualizzazioni interattive. Queste tecniche possono essere applicate anche a query di SQL Server, file CSV e qualsiasi altra origine dati in Power BI Desktop.

>[!NOTE]
>Power BI Desktop offre in genere diversi modi per completare un'attività. Ad esempio, molte selezioni della barra multifunzione sono disponibili anche tramite il pulsante destro del mouse o il menu **Altre opzioni** per una colonna o una cella. Nei passaggi seguenti sono descritti diversi metodi alternativi. 

## <a name="import-the-product-data-from-excel"></a>Importare i dati sui prodotti da Excel

Per prima cosa, importare i dati sui prodotti dalla cartella di lavoro di Excel Products.xlsx in Power BI Desktop.

1. [Scaricare la cartella di lavoro di Excel Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) e salvarla come **Products.xlsx**.
   
2. Selezionare la freccia dell'elenco a discesa **Dati** nella scheda **Home** della barra multifunzione di Power BI Desktop e quindi selezionare **Excel** dall'elenco a discesa **Più comuni**. 
   
   ![Recupera dati](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >È possibile selezionare direttamente la voce **Dati** oppure selezionare **Recupera dati** nella finestra di dialogo **Attività iniziali** di Power BI, quindi selezionare **Excel** o **File** > **Excel** nella finestra di dialogo **Recupera dati** e infine scegliere **Connetti**.
   
3. Nella finestra di dialogo **Apri** individuare e selezionare il file **Products.xlsx** e quindi scegliere **Apri**.
   
4. Nel riquadro **Strumento di navigazione** selezionare la tabella **Products** e quindi **Modifica**.
   
   ![Strumento di navigazione per Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
Un'anteprima della tabella verrà aperta nell'**Editor di Power Query**, in cui è possibile applicare trasformazioni per pulire i dati. 
   
![Editor di Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>È anche possibile aprire l'**Editor di Power Query** selezionando **Modifica query** > **Modifica query** nella barra multifunzione **Home** in Power BI Desktop oppure facendo clic con il pulsante destro del mouse o scegliendo **Altre opzioni** accanto a qualsiasi query in **Visualizzazione Report** e scegliendo **Modifica query**.

## <a name="clean-up-the-products-columns"></a>Pulire le colonne dei prodotti

Il report combinato userà solo le colonne **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** della cartella di lavoro di Excel, pertanto le altre colonne possono essere rimosse. 

1. Nell'**Editor di Power Query** selezionare le colonne **ProductID**, **ProductName**, **QuantityPerUnit** e **UnitsInStock** (tenendo premuto **CTRL**+**clic** per selezionare più di una colonna oppure **MAIUSC**+**clic** per selezionare colonne contigue).
   
2. Fare clic con il pulsante destro del mouse su una delle intestazioni di colonna selezionate e selezionare **Rimuovi altre colonne** dall'elenco a discesa, per rimuovere dalla tabella tutte le colonne tranne quelle selezionate. 
   È anche possibile selezionare **Rimuovi colonne** > **Rimuovi altre colonne** nel gruppo **Gestisci colonne** nella scheda **Home** della barra multifunzione. 
   
   ![Rimuovi altre colonne](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Importare i dati degli ordini da un feed OData

Successivamente, importare i dati degli ordini dal feed OData del sistema di vendite di esempio Northwind. 

1. Nell'**Editor di Power Query** selezionare **Nuova origine** e quindi selezionare **Feed OData** dall'elenco a discesa **Più comuni**. 
   
   ![Ottenere OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. Nella finestra di dialogo **Feed OData** incollare l'URL del feed Northwind OData, `http://services.odata.org/V3/Northwind/Northwind.svc/`, e scegliere **OK**.
   
   ![Finestra di dialogo Feed OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. Nel riquadro **Strumento di navigazione** selezionare la tabella **Orders** e quindi scegliere **OK** per caricare i dati nell'**Editor di Power Query**.
   
   ![Riquadro Strumento di navigazione per OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >In **Strumento di navigazione** è possibile selezionare un nome di tabella, senza selezionare la casella di controllo, per visualizzare un'anteprima.

## <a name="expand-the-order-data"></a>Espandere i dati degli ordini

Quando ci si connette a origini dati contenenti più tabelle, ad esempio un database relazionale o il feed Northwind OData, è possibile usare i riferimenti tra le tabelle per compilare le query. La tabella **Orders** include riferimenti a diverse tabelle correlate. È possibile aggiungere le colonne **ProductID**, **UnitPrice** e **Quantity** dalla tabella **Order_Details** correlata nella tabella in base all'argomento (**Orders**) usando l'operazione **Espandi**. 

1. Scorrere verso destra la tabella **Orders** finché non viene visualizzata la colonna **Order_Details**. Si noti che al posto dei dati sono contenuti riferimenti a un'altra tabella.
   
   ![Colonna Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Selezionare l'icona di **espansione** (![icona di espansione](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) nell'intestazione di colonna **Order_Details**. 
   
3. Nell'elenco a discesa **Espandi** :
   
   1. Selezionare **(Seleziona tutte le colonne)** per deselezionare tutte le colonne.
      
   2. Selezionare **ProductID**, **UnitPrice** e **Quantity** e quindi scegliere **OK**.
      
      ![Finestra di dialogo Espandi](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Dopo l'espansione della tabella **Order_Details**, la colonna **Order_Details** viene sostituita dalle tre nuove colonne della tabella annidata e sono presenti nuove righe nella tabella per i dati aggiunti da ogni ordine. 

![Colonne espanse](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Creare una colonna calcolata personalizzata

L'Editor di Power Query consente di creare calcoli e campi personalizzati per ottimizzare i dati. Verrà creata una colonna personalizzata che calcola il prezzo totale per ogni voce in un ordine moltiplicando il prezzo unitario per la quantità di articoli.

1. Nella scheda **Aggiungi colonna** della barra multifunzione dell'Editor di Power Query selezionare **Colonna personalizzata**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. Nella finestra di dialogo **Colonna personalizzata** digitare **LineTotal** nel campo **Nome nuova colonna**.

3. Nel campo **Formula colonna personalizzata** dopo **=** immettere **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . È anche possibile selezionare i nomi dei campi dalla casella di scorrimento **Colonne disponibili** e selezionare **<< Inserisci** invece di digitarli. 
3. Selezionare **OK**.
   
   ![Finestra di dialogo Colonna personalizzata](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

Il nuovo campo **LineTotal** viene visualizzato come ultima colonna nella tabella **Orders**.

## <a name="set-the-data-type-for-the-new-field"></a>Impostare il tipo di dati per il nuovo campo

Quando l'Editor di Power Query si connette ai dati, determina il tipo di dati più appropriato per ogni campo e visualizza i dati di conseguenza. È possibile visualizzare i tipi di dati assegnati ai campi dalle icone nelle intestazioni o in **Tipo di dati** nel gruppo **Trasforma** della scheda **Home** della barra multifunzione. 

La nuova colonna **LineTotal** ha un tipo di dati **Qualsiasi**, ma i relativi valori sono di tipo valuta. Per assegnare un tipo di dati, fare clic con il pulsante destro del mouse sull'intestazione di colonna **LineTotal**, selezionare **Cambia tipo di dati** dall'elenco a discesa e quindi selezionare **Numero decimale fisso**. 

![Modificare il tipo di dati](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>È anche possibile selezionare la colonna **LineTotal**, quindi selezionare la freccia a discesa accanto a **Tipo di dati** nell'area **Trasforma** della scheda **Home** della barra multifunzione e quindi selezionare **Numero decimale fisso**.

## <a name="clean-up-the-orders-columns"></a>Pulire le colonne degli ordini

Per semplificare l'uso del modello all'interno dei report, è possibile eliminare, rinominare e riordinare alcune colonne.

Il report userà solo le colonne **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** e **Order_Details.Quantity**. È possibile selezionare queste colonne e usare **Rimuovi altre colonne** come è stato fatto per i dati di Excel oppure è possibile selezionare tutte le colonne ad eccezione di quelle elencate, fare clic con il pulsante destro del mouse su una delle colonne selezionate e selezionare **Rimuovi colonne** per rimuoverle tutte. 

È possibile rendere le colonne **Order_Details.ProductID**, **Order_Details.UnitPrice** e **Order_Details.Quantity** più semplici da identificare rimuovendo i prefissi *Order_Details.* dai nomi delle colonne. Per rinominare le colonne in **ProductID**, **UnitPrice** e **Quantity**, rispettivamente:

1. Fare doppio clic o toccare e tenere premuta ogni intestazione di colonna oppure fare clic con il pulsante destro del mouse sull'intestazione di colonna e scegliere **Rinomina** dall'elenco a discesa. 
2. Eliminare il prefisso *Order_Details.* da ogni nome e quindi premere **INVIO**.

Infine, per rendere la colonna **LineTotal** più accessibile, trascinarla verso sinistra, a destra della colonna **ShipCountry**.

![Tabella pulita](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>Rivedere i passaggi della query

Durante la modifica della forma dei dati e la relativa trasformazione dei dati nell'Editor di Power Query, ogni passaggio viene registrato nell'area **Passaggi applicati** del riquadro **Impostazioni query** sul lato destro dell'Editor di Power Query. È possibile riesaminare i singoli passaggi applicati per rivedere le modifiche apportate ed eventualmente modificarle, eliminarle o riordinarle, anche se ciò può essere rischioso, perché la modifica di passaggi precedenti può invalidare passaggi successivi. 

Selezionare ognuna delle query nell'elenco **Query** sul lato sinistro dell'Editor di Power Query ed esaminare i **Passaggi applicati** in **Impostazioni query**. Dopo avere applicato le trasformazioni dei dati precedenti, i passaggi applicati per le due query dovrebbero essere simili ai seguenti:

![Passaggi applicati per la query Products](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Passaggi applicati per la query Orders](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Per ogni passaggio applicato vi sono le formule sottostanti scritte nel **linguaggio Power Query**, noto anche come linguaggio **M**. Per visualizzare e modificare le formule, selezionare **Editor avanzato** nel gruppo **Query** della scheda Home della barra multifunzione. 

## <a name="import-the-transformed-queries"></a>Importare le query trasformate

Al termine della trasformazione dei dati, selezionare **Chiudi e applica** > **Chiudi e applica** nel gruppo **Chiudi** della scheda **Home** della barra multifunzione per importare i dati nella visualizzazione Report in Power BI Desktop. 

![Chiudi e applica](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Dopo che i dati sono stati caricati, le query vengono visualizzate nell'elenco **Campi** nella visualizzazione Report di Power BI Desktop.

![Query nell'elenco Campi](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Gestire la relazione tra i set di dati

In Power BI Desktop non è necessario combinare query per crearne i report corrispondenti. Tuttavia, è possibile usare le relazioni tra i set di dati, in base ai campi che hanno in comune, per estendere e migliorare i report. Power BI Desktop può rilevare automaticamente le relazioni oppure è possibile crearle nella finestra di dialogo **Gestisci relazioni** di Power BI Desktop. Per maggiori dettagli sulle relazioni in Power BI Desktop, vedere [Creare e gestire le relazioni](desktop-create-and-manage-relationships.md).

I set di dati Orders e Products in questa esercitazione condividono un campo *ProductID* comune, pertanto esiste una relazione tra di essi in base a tale colonna. 

1. Nella visualizzazione Report di Power BI Desktop selezionare **Gestisci relazioni** nell'area **Relazioni** della scheda **Home** della barra multifunzione.
   
   ![Gestisci relazioni - Barra multifunzione](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. Nella finestra di dialogo **Gestisci relazioni** si noti che Power BI Desktop ha già rilevato ed elencato una relazione attiva tra le tabelle Products e Orders. Per visualizzare la relazione, selezionare **Modifica**. 
   
   ![Finestra di dialogo Gestisci relazioni](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   Viene visualizzata la finestra di dialogo **Modifica relazione** con i dettagli relativi alla relazione.  
   
   ![Finestra di dialogo Modifica relazione](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. Power BI Desktop ha rilevato automaticamente la relazione in modo corretto, pertanto è possibile selezionare **Annulla** e quindi **Chiudi** per chiudere le finestre di dialogo della relazione.

È anche possibile visualizzare e gestire le relazioni tra le query selezionando la visualizzazione **Relazioni** sul lato sinistro della finestra di Power BI Desktop. Fare doppio clic sulla freccia sulla linea che collega le due query per aprire la finestra di dialogo **Modifica relazione** e visualizzare o modificare la relazione. 

![Visualizzazione Relazioni](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Per tornare alla visualizzazione Report dalla visualizzazione Relazioni, selezionare l'icona **Visualizzazione Report**. 

![icona Visualizzazione report](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Creare visualizzazioni usando i dati

Nella visualizzazione Report di Power BI Desktop è possibile creare un'ampia gamma di visualizzazioni per ottenere informazioni utili dai dati. È possibile creare report con più pagine e ogni pagina può includere più oggetti visivi. È possibile interagire con le visualizzazioni per semplificare l'analisi e il riconoscimento dei dati. Per altre informazioni sulla visualizzazione e la modifica di report nel servizio Power BI (il sito), vedere [Modificare un report](service-interact-with-a-report-in-editing-view.md).

È possibile usare i set di dati e la relazione esistente tra di essi per semplificare la visualizzazione e l'analisi dei dati di vendita. 

Per prima cosa, creare un istogramma a colonne in pila che usa i campi da entrambe le query per mostrare la quantità di ogni prodotto ordinato. 

1. Selezionare il campo **Quantity** da **Orders** nel riquadro **Campi** a destra oppure trascinarlo in uno spazio vuoto nell'area di disegno. In questo modo viene creato un istogramma a colonne in pila che mostra la quantità totale di tutti i prodotti ordinati. 
   
2. Selezionare **ProductName** da **Products** nel riquadro **Campi** oppure trascinarlo nel grafico per mostrare la quantità di ogni prodotto ordinato. 
   
3. Per ordinare i prodotti dai più ordinati ai meno ordinati, selezionare i puntini di sospensione ( **...** ) **Altre opzioni** in alto a destra nella visualizzazione e quindi selezionare **Ordina per quantità**.
   
4. Usare i punti di controllo negli angoli del grafico per aumentarne le dimensioni in modo che siano visibili più nomi di prodotto. 
   
   ![Grafico a barre Quantity by ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Successivamente, creare un grafico che mostri gli importi in dollari degli ordini (**LineTotal**) nel tempo (**OrderDate**). 

1. Senza selezionare alcun elemento nell'area di disegno, selezionare **LineTotal** da **Orders** nel riquadro **Campi** oppure trascinarlo in uno spazio vuoto nell'area di disegno. L'istogramma a colonne in pila mostra l'importo totale in dollari di tutti gli ordini. 
   
2. Con il grafico selezionato, selezionare **OrderDate** da **Orders** oppure trascinarlo nel grafico. Il grafico mostrerà i totali riga per ogni data dell'ordine. 
   
3. Ridimensionare la visualizzazione trascinando gli angoli in modo da visualizzare un maggior numero di dati. 
   
   ![Grafico a linee LineTotal by OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Se si visualizzano solo gli anni nel grafico (solo tre punti dati), fare clic sulla freccia a discesa accanto a **OrderDate** nel campo **Axis** del riquadro **Visualizzazioni** e selezionare **OrderDate** anziché **Gerarchia data**. 

Infine, creare una visualizzazione mappa che mostri gli importi degli ordini da ogni paese. 

1. Senza selezionare alcun elemento nell'area di disegno, selezionare **ShipCountry** da **Orders** nel riquadro **Campi** oppure trascinarlo in uno spazio vuoto nell'area di disegno. Power BI Desktop rileva che i dati corrispondono a nomi di paesi e crea automaticamente una visualizzazione mappa, con un punto dati per ogni paese a cui sono associati gli ordini. 
   
2. Per fare in modo che le dimensioni dei punti dati rispecchino gli importi degli ordini per ogni paese, trascinare il campo **LineTotal** nella mappa (o trascinarlo in **Trascinare qui i campi di dati** in **Dimensioni** nella parte inferiore del riquadro **Visualizzazioni**). Le dimensioni dei cerchi sulla mappa riflettono gli importi in dollari degli ordini da ogni paese. 
   
   ![Visualizzazione mappa LineTotal by ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagire con gli oggetti visivi del report per un'analisi approfondita

Power BI Desktop permette di rilevare altre tendenze interagendo con gli oggetti visivi che si evidenziano e filtrano a vicenda. Per altre informazioni, vedere [Informazioni su filtri ed evidenziazione nei report di Power BI](power-bi-reports-filters-and-highlighting.md). 

A causa della relazione tra le query, le interazioni con una visualizzazione avrà effetto su tutte le altre visualizzazioni nella pagina. 

Nella visualizzazione mappa selezionare il cerchio centrato in **Canada**. Si noti che le altre due visualizzazioni applicano un filtro per evidenziare i totali riga e i quantitativi degli ordini solo per il Canada.

![Dati di vendita filtrati per il Canada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Se si seleziona uno dei prodotti nel grafico **Quantity by ProductName**, la mappa e il grafico delle date vengono filtrati in modo da rispecchiare i dati per quel prodotto e se si seleziona una delle date nel grafico **LineTotal by OrderDate**, la mappa e il grafico dei prodotti vengono filtrati in modo da mostrare i dati per quella data. 
>[!TIP]
>Per deselezionare una selezione, selezionarla nuovamente oppure selezionare una delle altre visualizzazioni. 

## <a name="complete-the-sales-analysis-report"></a>Completare il report di analisi delle vendite

Il report completato combina i dati dal file di Excel Products.xlsx e dal feed Northwind OData in oggetti visivi che permettono di analizzare le informazioni sugli ordini per diversi paesi, periodi di tempo e prodotti. Quando il report è pronto, è possibile [caricarlo nel servizio Power BI](desktop-upload-desktop-files.md) per condividerlo con altri utenti di Power BI.

## <a name="next-steps"></a>Passaggi successivi
* [Altre esercitazioni su Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Video su Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Forum di Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Blog su Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)