---
title: 'Esercitazione: Creare misure personalizzate in Power BI Desktop'
description: 'Esercitazione: Creare misure personalizzate in Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 8cfa3190acd4ef2ae2e1123f22d8f6221147afb1
ms.sourcegitcommit: e6db826c2f43a69e4c63d5f4920baa8f66bc41be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Esercitazione: Creare misure personalizzate in Power BI Desktop
Con le misure è possibile creare alcune delle soluzioni di analisi dati più potenti in Power BI Desktop. Consentono infatti di eseguire calcoli sui dati durante l'interazione con i report. Questa esercitazione illustra il significato e la modalità di creazione delle misure di base in Power BI Desktop.

### <a name="prerequisites"></a>Prerequisiti
- Questa esercitazione è destinata agli utenti di Power BI che sono già in grado di usare Power BI Desktop per creare modelli più avanzati. L'utente dovrebbe avere già familiarità con l'uso delle funzionalità Recupera dati ed Editor di query per importare i dati, l'uso di più tabelle correlate e l'aggiunta di campi all'area di disegno del report. Se non si ha familiarità con Power BI Desktop, vedere l'articolo [Introduzione a Power BI Desktop](desktop-getting-started.md).
  
- Scaricare il file [Contoso Sales Sample for Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip) che include i dati delle vendite online della società fittizia Contoso, Inc. Questi dati sono stati importati da un database, quindi non sarà possibile connettersi all'origine dati o visualizzare i dati nell'Editor di query. Estrarre il file nel computer in uso e quindi aprirlo in Power BI Desktop.

## <a name="understand-measures"></a>Informazioni sulle misure

Le misure vengono create automaticamente nella maggior parte dei casi. Nel file Contoso Sales Sample selezionare la casella di controllo accanto al campo **SalesAmount** nella tabella **Sales** nell'area Campi oppure trascinare **SalesAmount** nell'area di disegno report. Verrà visualizzata una nuova visualizzazione dell'istogramma che mostra la somma totale di tutti i valori nella colonna SalesAmount della tabella Sales.

![Grafico SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Qualsiasi campo visualizzato nell'area Campi con l'icona Sigma ![icona Sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) è di tipo numerico e i relativi valori possono essere aggregati. Invece di visualizzare una tabella con tutti i due milioni di righe di valori SalesAmount, Power BI Desktop ha rilevato un tipo di dati numerico e ha creato e calcolato automaticamente una misura per aggregare i dati. La somma è l'aggregazione predefinita per un tipo di dati numerico, ma è possibile applicare facilmente aggregazioni diverse, ad esempio media o conteggio. Comprendere l'uso delle aggregazioni è di fondamentale importanza per comprendere le misure, perché ogni misura esegue un tipo di aggregazione. 

Per impostare la media come aggregazione per il grafico, nell'area **Valore** del riquadro Visualizzazioni, fare clic sulla freccia in giù accanto a **SalesAmount** e selezionare **Media**. La visualizzazione cambia e mostra la media di tutti i valori delle vendite nel campo SalesAmount.

![Grafico della media di SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

È possibile modificare il tipo di aggregazione in base al risultato che si vuole ottenere, ma non tutti i tipi di aggregazione sono validi con qualsiasi tipo di dati numerico. Ad esempio, per il campo SalesAmount i tipi di aggregazione Somma e Media sono significativi, così come Minimo e Massimo, mentre Conteggio non è rilevante per questo campo perché, pur se numerici, i relativi valori sono di tipo valuta.

I valori calcolati dalle misure cambiano in risposta alle interazioni con il report. Ad esempio, se si trascina nel grafico il campo **RegionCountryName** dalla tabella **Geography**, viene mostrata la media degli importi delle vendite per ogni paese.

![SaleAmount per paese](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando il risultato di una misura cambia in seguito a un'interazione con il report, l'operazione ha effetto sul *contesto* della misura. Ogni volta che si interagisce con le visualizzazioni del report, si modifica il contesto in cui una misura calcola e visualizza i risultati.

## <a name="create-and-use-your-own-measures"></a>Creare e usare misure personalizzate

Nella maggior parte dei casi, Power BI calcola e restituisce automaticamente i valori in base ai tipi di campi e aggregazioni scelti, ma in alcuni casi si potrebbe voler creare misure personalizzate per eseguire calcoli più complessi e univoci. Con Power BI Desktop è possibile creare misure personalizzate con il linguaggio delle formule DAX (Data Analysis Expressions). 

Le formule DAX usano in molti casi funzioni, operatori e sintassi simili a quelli delle formule di Excel. Le funzioni di DAX sono però concepite in modo da funzionare con dati relazionali ed eseguire calcoli più dinamici durante l'interazione con i report. Sono disponibili oltre 200 funzioni DAX che eseguono vari tipi di operazioni, dalle aggregazioni semplici, come somma e media, fino a funzioni statistiche e di filtro più complesse. Sono disponibili molte risorse per approfondire DAX. Al termine di questa esercitazione, vedere l'articolo [Nozioni di DAX in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando si crea una misura personalizzata, questa viene aggiunta all'elenco Campi per la tabella selezionata e viene chiamata misura *modello*. Alcuni vantaggi delle misure modello sono la possibilità di assegnare il nome preferito rendendole più identificabili, di usarle come argomenti in altre espressioni DAX e di usarle per eseguire calcoli complessi molto velocemente.

>[!TIP]
>A partire dalla versione di febbraio 2018 di Power BI Desktop, molti calcoli comuni sono disponibili in forma di **misure rapide**, che scrivono automaticamente le formule DAX in base all'input dell'utente in una finestra di dialogo. Questi calcoli potenti e veloci sono anche molto utili per imparare il linguaggio DAX o come base per misure personalizzate. Per creare o esplorare misure rapide, selezionare **Nuova misura rapida** nell'elenco **Altre opzioni** per una tabella o in **Calcoli** nella scheda Home della barra multifunzione. Vedere [Usare le misure rapide](desktop-quick-measures.md) per altre informazioni sulla creazione e l'uso delle misure rapide.

### <a name="create-a-measure"></a>Creare una misura

Si supponga di voler analizzare il fatturato netto sottraendo sconti e resi dagli importi delle vendite totali. Per qualsiasi contesto esistente in una visualizzazione, è necessaria una misura che sottrae la somma di DiscountAmount e ReturnAmount dalla somma di SalesAmount. Non è disponibile un campo per Net Sales nell'elenco Campi, ma sono disponibili i blocchi predefiniti per creare una misura personalizzata per calcolare il fatturato netto. 

1.  Fare clic con il pulsante destro del mouse sulla tabella **Sales** nell'area Campi oppure passare il mouse sulla tabella e selezionare i puntini di sospensione (...) **Altre opzioni**, quindi selezionare **Nuova misura**. In questo modo la nuova misura verrà salvata nella tabella Sales, dove sarà più facilmente individuabile.
    
    ![Nuova misura](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    È anche possibile creare una nuova misura selezionando **Nuova misura** nel gruppo Calcoli nella scheda Home della barra multifunzione di Power BI Desktop.
    
    ![Nuova misura sulla barra multifunzione](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Quando si crea una misura dalla barra multifunzione, può essere creata in qualsiasi tabella, ma sarà più semplice individuarla se viene creata dove si prevede di usarla. In questo caso, selezionare prima di tutto la tabella Sales per renderla attiva e quindi selezionare **Nuova misura**. 
    
    La barra della formula viene visualizzata nella parte superiore dell'area di disegno Report e al suo interno è possibile rinominare la misura e immettere una formula DAX.
    
    ![Barra della formula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  Per impostazione predefinita, a una nuova misura viene assegnato il nome Misura. Se non la si rinomina, le nuove misure aggiuntive verranno denominate Misura 2, Misura 3 e così via. Per questa esercitazione si vogliono usare misure più facilmente identificabili, quindi evidenziare **Misura** nella barra della formula e digitare **Net Sales**.
    
3.  A questo punto, è possibile iniziare a immettere la formula. Dopo il segno di uguale, iniziare a digitare **Sum**. Durante la digitazione, viene visualizzato un elenco a discesa di suggerimenti, che mostra tutte le funzioni DAX che iniziano con le lettere digitate. Scorrere verso il basso se necessario per selezionare **SUM** nell'elenco e quindi premere INVIO.
    
    ![Scegliere SUM](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Viene visualizzata una parentesi aperta, con un altro elenco a discesa di suggerimenti con tutte le colonne disponibili che è possibile passare alla funzione SUM.
    
    ![Scegliere la colonna](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    Le espressioni sono sempre racchiuse tra una parentesi aperta e una chiusa. L'espressione conterrà un solo argomento da passare alla funzione SUM, ovvero la colonna SalesAmount. Iniziare a digitare "SalesAmount" fino a quando non rimane un solo valore nell'elenco, ovvero Sales(SalesAmount). Il nome della colonna preceduto dal nome della tabella viene chiamato *nome completo* della colonna. I nomi di colonna completi semplificano la lettura delle formule. 
    
    ![Selezionare SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. Selezionare **Sales[SalesAmount]**, quindi digitare una parentesi chiusa.
    
    > [!TIP]
    > Gli errori di sintassi sono spesso causati da parentesi chiuse mancanti o nella posizione sbagliata.
    
    
    
5.  Per sottrarre le altre due colonne:
    1. Dopo la parentesi chiusa della prima espressione digitare uno spazio, un operatore di sottrazione (**-**) e un altro spazio. 
    2. Immettere un'altra funzione SUM e iniziare a digitare "DiscountAmount" fino a quando non è possibile scegliere la colonna **Sales[DiscountAmount]** come argomento. Aggiungere una parentesi di chiusura. 
    3. Digitare uno spazio, un altro operatore di sottrazione, uno spazio, un'altra funzione SUM con **Sales[ReturnAmount]** come argomento e una parentesi di chiusura.
    
    ![Formula completa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  Per completare e convalidare la formula, premere INVIO oppure fare clic sul segno di spunta nella barra della formula. La misura convalidata è ora pronta per l'uso nell'elenco Campi per la tabella Sales. 
    
    ![Misura nell'elenco Campi](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
Se si esaurisce lo spazio disponibile per l'immissione di una formula o si vuole immetterla in righe separate, selezionare la freccia di espansione verso il basso sul lato destro della barra della formula per aumentare lo spazio.

![Freccia di espansione della formula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

È possibile separare le parti della formula su diverse righe premendo **ALT+INVIO** oppure spostare gli elementi con **TAB**.

![Formula espansa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Usare la misura nel report
È ora possibile aggiungere la misura Net Sales nell'area di disegno report e calcolare il fatturato netto per qualsiasi altro campo aggiunto al report. Per visualizzare il fatturato netto per paese:

1. Selezionare la misura **Net Sales** dalla tabella **Sales** o trascinarla sull'area di disegno report.
    
2. Selezionare il campo **RegionCountryName** della tabella **Geography** o trascinarlo nel grafico.
    
    ![Fatturato netto per paese](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
Per visualizzare la differenza tra fatturato netto e vendite totali in base al paese, selezionare il campo **SalesAmount** oppure trascinarlo nel grafico. 

![Importo delle vendite e fatturato netto per paese](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

Il grafico usa ora due misure: SalesAmount, sommata automaticamente e la misura Net Sales creata. Ogni misura è stata calcolata nel contesto di un altro campo, RegionCountryName.
    
### <a name="use-your-measure-with-a-slicer"></a>Usare la misura con un filtro dei dati

È possibile aggiungere un filtro dei dati per filtrare ulteriormente il fatturato netto e l'importo delle vendite in base all'anno di calendario.
    
1.  Fare clic su un'area vuota accanto al grafico, quindi in **Visualizzazioni** selezionare la visualizzazione **Tabella**. Verrà creata una visualizzazione di tabella vuota nell'area di disegno report.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  Trascinare il campo **Year** dalla tabella **Calendar** nella nuova visualizzazione di tabella vuota. Dato che Year è un campo numerico, Power BI Desktop somma i relativi valori, ma questo calcolo non ha molto senso come aggregazione. 
    
    ![Aggregazione in base all'anno](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  In **Valori** nel riquadro Visualizzazioni selezionare la freccia in giù accanto a **Year** e quindi selezionare **Non riepilogare**. Nella tabella sono ora elencati singoli anni.
    
    ![Non riepilogare](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Selezionare l'icona **Filtro dei dati** nel riquadro Visualizzazioni per convertire la tabella in un filtro dei dati.

    ![Conversione in filtro dei dati](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Selezionare qualsiasi valore nel filtro dei dati **Year** per filtrare il grafico **Net Sales and Sales Amount by RegionCountryName** di conseguenza. Le misure Net Sales e SalesAmount vengono ricalcolate e vengono visualizzati i risultati nel contesto del campo Year selezionato. 
    
    ![Grafico filtrato in base all'anno](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Usare la misura in un'altra misura

Si supponga di voler scoprire quali prodotti registrano il fatturato netto maggiore per unità. A tale scopo serve una misura per dividere il fatturato netto per la quantità di unità vendute. È possibile creare una nuova misura che divide il risultato della misura Net Sales per la somma di Sales[SalesQuantity].

1.  Creare una nuova misura denominata **Net Sales per Unit** nella tabella Sales.
    
2.  Nella barra della formula iniziare a digitare **Net Sales**. L'elenco di suggerimenti mostrerà gli elementi che è possibile aggiungere. Selezionare **[Net Sales]**.
    
    ![Formula che usa Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    È anche possibile fare riferimento alle misure semplicemente digitando una parentesi aperta (**[**). L'elenco di suggerimenti mostrerà solo le misure per l'aggiunta alla formula.
    
    ![Con la parentesi quadra vengono visualizzate solo le misure](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Immettere uno spazio, un operatore di divisione (**/**), un altro spazio, una funzione SUM e quindi digitare **Quantity**. L'elenco dei suggerimenti mostra tutte le colonne il cui nome contiene il termine Quantity. Selezionare **Sales[SalesQuantity]**, digitare la parentesi di chiusura e premere INVIO o selezionare il segno di spunta per convalidare la formula. La formula dovrebbe essere simile alla seguente:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. Selezionare la misura **Net Sales per Unit** dalla tabella Sales o trascinarla in un'area vuota nell'area di disegno report. Il grafico mostra l'importo del fatturato netto per unità per tutti i prodotti venduti, non molto informativo. 
    
    ![Fatturato netto complessivo per unità](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. Per ottenere un aspetto diverso, modificare il tipo di visualizzazione del grafico in **Mappa ad albero**.
    
    ![Passare alla mappa ad albero](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Selezionare il campo **Product Category** oppure trascinarlo nella mappa ad albero o nel campo Gruppo del riquadro Visualizzazioni. A questo punto sono disponibili informazioni utili.
    
    ![Mappa ad albero in base alla categoria di prodotto](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Provare a rimuovere il campo **ProductCategory** e a trascinare invece il campo **ProductName** nel grafico. 
    
    ![Mappa ad albero in base al nome del prodotto](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
È stato illustrato solo un esempio, ma comunque molto interessante. Sperimentare altri modi per filtrare e formattare la visualizzazione.

## <a name="what-youve-learned"></a>Informazioni apprese
Le misure costituiscono un potente strumento per ottenere le informazioni desiderate dai dati. Si è imparato a creare misure usando la barra della formula, ad assegnare loro un nome significativo, nonché a trovare e selezionare gli elementi della formula appropriati usando gli elenchi di suggerimenti DAX. È stato anche presentato il concetto di contesto, in cui il risultato dei calcoli nelle misure cambia in base ad altri campi o ad altre espressioni nella formula.

## <a name="next-steps"></a>Passaggi successivi
- Per altre informazioni sulle misure rapide di Power BI Desktop, che forniscono numerosi calcoli su misure comuni, vedere [Usare Misure rapide per eseguire facilmente calcoli comuni e avanzati](desktop-quick-measures.md).
  
- Per approfondire i concetti relativi alle formule DAX e creare misure più complesse, vedere [Nozioni di DAX in Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Questo articolo illustra i concetti fondamentali in DAX, ad esempio sintassi, funzioni e una maggiore comprensione del contesto.
  
- Non dimenticare di aggiungere ai Preferiti la pagina [Riferimento a Data Analysis Expressions (DAX)](https://msdn.microsoft.com/library/gg413422.aspx). che include informazioni dettagliate sulla sintassi e sugli operatori DAX, nonché sulle oltre 200 funzioni DAX disponibili.

