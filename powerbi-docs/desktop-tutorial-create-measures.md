---
title: 'Esercitazione: Creare misure personalizzate in Power BI Desktop'
description: Le misure in Power BI Desktop consentono di eseguire calcoli sui dati durante l'interazione con i report.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0d2b316b53b4107c86a036cc8a436440dd8bd674
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "74311533"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Esercitazione: Creare misure personalizzate in Power BI Desktop
Con le misure è possibile creare alcune delle soluzioni di analisi dati più potenti in Power BI Desktop. Consentono infatti di eseguire calcoli sui dati durante l'interazione con i report. Questa esercitazione illustra il significato e la modalità di creazione delle misure di base in Power BI Desktop.

## <a name="prerequisites"></a>Prerequisiti

- Questa esercitazione è destinata agli utenti di Power BI che sono già in grado di usare Power BI Desktop per creare modelli più avanzati. L'utente dovrebbe avere già familiarità con l'uso delle funzionalità Recupera dati ed Editor di query per importare i dati, utilizzare più tabelle correlate e aggiungere campi all'area di disegno del report. Se non si ha familiarità con Power BI Desktop, vedere l'articolo [Introduzione a Power BI Desktop](desktop-getting-started.md).
  
- Questa esercitazione usa il file [Contoso Sales Sample for Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), che include dati sulle vendite online della società fittizia Contoso. Poiché questi dati sono stati importati da un database, non è possibile connettersi all'origine dati o visualizzarli nell'Editor di query. Scaricare ed estrarre il file nel computer.

## <a name="automatic-measures"></a>Misure automatiche

La creazione di una misura in Power BI Desktop è molto spesso automatica. Per vedere come Power BI Desktop crea una misura, seguire questa procedura:

1. In Power BI Desktop selezionare **File** > **Apri**, passare al file *Contoso Sales Sample for Power BI Desktop.pbix* e quindi selezionare **Apri**.

2. Nel riquadro **Campi** espandere la tabella **Sales**, quindi selezionare la casella di controllo accanto al campo **SalesAmount** o trascinare **SalesAmount** nell'area di disegno del report.

    Verrà visualizzata una nuova visualizzazione dell'istogramma che mostra la somma totale di tutti i valori nella colonna **SalesAmount** della tabella **Sales**.

    ![Istogramma SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

I campi (colonne) del riquadro **Campi** con un'icona Sigma ![icona Sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) sono di tipo numerico e i relativi valori possono essere aggregati. Invece di visualizzare una tabella con molti valori (due milioni di righe per **SalesAmount**), Power BI Desktop crea e calcola automaticamente una misura per aggregare i dati se rileva un tipo di dati numerico. La somma è l'aggregazione predefinita per un tipo di dati numerico, ma è possibile applicare facilmente aggregazioni diverse, ad esempio media o conteggio. Comprendere l'uso delle aggregazioni è di fondamentale importanza per comprendere le misure, perché ogni misura esegue un tipo di aggregazione. 

Per modificare l'aggregazione del grafico, seguire questa procedura:

1. Selezionare la visualizzazione **SalesAmount** nell'area di disegno del report.  

1. Nell'area **Valore** del riquadro **Visualizzazioni** selezionare la freccia verso il basso a destra di **SalesAmount**. 

1. Nel menu visualizzato selezionare **Media**. 

    La visualizzazione cambia e mostra la media di tutti i valori delle vendite nel campo **SalesAmount**.

    ![Grafico della media di SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

A seconda del risultato desiderato, è possibile modificare il tipo di aggregazione, ma non tutti i tipi di aggregazione si applicano a ogni tipo di dati numerico. Per il campo **SalesAmount**, ad esempio, Somma e Media sono utili, così come Minimo e Massimo, mentre Conteggio non è rilevante per il campo **SalesAmount** perché, pur se numerici, i relativi valori sono di tipo valuta.

I valori calcolati dalle misure cambiano in risposta alle interazioni con il report. Se ad esempio si trascina il campo **RegionCountryName** dalla tabella **Geography** al grafico **SalesAmount** esistente, viene mostrata la media degli importi delle vendite per ogni paese.

![SaleAmount per paese](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quando il risultato di una misura cambia in seguito a un'interazione con il report, l'operazione ha effetto sul *contesto* della misura. Ogni volta che si interagisce con le visualizzazioni del report, si modifica il contesto in cui una misura calcola e visualizza i risultati.

## <a name="create-and-use-your-own-measures"></a>Creare e usare misure personalizzate

Nella maggior parte dei casi, Power BI Desktop calcola e restituisce automaticamente i valori in base ai tipi di campi e aggregazioni scelti, ma in alcuni casi potrebbe essere necessario creare misure personalizzate per eseguire calcoli più complessi e univoci. Con Power BI Desktop è possibile creare misure personalizzate con il linguaggio delle formule DAX (Data Analysis Expressions). 

Le formule DAX usano in molti casi funzioni, operatori e sintassi simili a quelli delle formule di Excel. Le funzioni di DAX sono però concepite in modo da funzionare con dati relazionali ed eseguire calcoli più dinamici durante l'interazione con i report. Sono disponibili oltre 200 funzioni DAX che eseguono vari tipi di operazioni, dalle aggregazioni semplici, come somma e media, fino a funzioni statistiche e di filtro più complesse. Sono disponibili molte risorse per approfondire DAX. Al termine di questa esercitazione, vedere l'articolo [Nozioni di DAX in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Quando si crea una misura personalizzata, questa viene chiamata misura *modello* e viene aggiunta all'elenco **Campi** per la tabella selezionata. Alcuni vantaggi delle misure modello sono la possibilità di assegnare il nome preferito rendendole più identificabili, di usarle come argomenti in altre espressioni DAX e di usarle per eseguire calcoli complessi velocemente.

### <a name="quick-measures"></a>Misura rapida

A partire dalla versione di febbraio 2018 di Power BI Desktop, molti calcoli comuni sono disponibili in forma di *misure rapide*, che scrivono automaticamente le formule DAX in base all'input dell'utente in una finestra. Questi calcoli potenti e veloci sono anche molto utili per imparare il linguaggio DAX o come base per misure personalizzate. 

Creare una misura rapida usando uno di questi metodi: 
 - In una tabella del riquadro **Campi** fare clic con il pulsante destro del mouse o selezionare **Altre opzioni** ( **...** ) e quindi selezionare **Nuova misura rapida** dall'elenco.

 - In **Calcoli** nella scheda **Home** della barra multifunzione di Power BI Desktop selezionare **Nuova misura rapida**.

Per altre informazioni sulla creazione e l'uso delle misure rapide, vedere [Usare le misure rapide](desktop-quick-measures.md).

### <a name="create-a-measure"></a>Creare una misura

Si supponga di voler analizzare il fatturato netto sottraendo sconti e resi dagli importi delle vendite totali. Per il contesto esistente in una visualizzazione, è necessaria una misura che sottrae la somma di DiscountAmount e ReturnAmount dalla somma di SalesAmount. Non è disponibile un campo per Net Sales nell'elenco **Campi**, ma sono disponibili i blocchi predefiniti per creare una misura personalizzata per calcolare il fatturato netto. 

Per creare una misura, seguire questa procedura:

1. Nel riquadro **Campi** fare clic con il pulsante destro del mouse sulla tabella **Sales** oppure passare il mouse sulla tabella e selezionare **Altre opzioni** ( **...** ). 

1. Nel menu visualizzato selezionare **Nuova misura**. 

    Questa azione salva la nuova misura nella tabella **Sales**, dove può essere trovata facilmente.
    
    ![Nuova misura nell'elenco](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    È anche possibile creare una nuova misura selezionando **Nuova misura** nel gruppo **Calcoli** nella scheda **Home** della barra multifunzione di Power BI Desktop.
    
    ![Nuova misura sulla barra multifunzione](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Quando si crea una misura dalla barra multifunzione, è possibile crearla in qualsiasi tabella, ma è più semplice trovarla se viene creata dove si prevede di usarla. In questo caso, selezionare prima di tutto la tabella **Sales** per renderla attiva e quindi selezionare **Nuova misura**. 
    
    La barra della formula viene visualizzata nella parte superiore dell'area di disegno del report e al suo interno è possibile rinominare la misura e immettere una formula DAX.
    
    ![Barra della formula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
1. Per impostazione predefinita, a ogni nuova misura viene assegnato il nome *Misura*. Se non la si rinomina, le nuove misure aggiuntive vengono denominate *Misura 2*, *Misura 3* e così via. Poiché si vuole che questa misura sia più facilmente identificabile, evidenziare *Misura* nella barra della formula e impostare il nome *Net Sales*.
    
1. Iniziare a immettere la formula. Dopo il segno di uguale, iniziare a digitare *Sum*. Durante la digitazione, viene visualizzato un elenco a discesa di suggerimenti, che mostra tutte le funzioni DAX che iniziano con le lettere digitate. Scorrere verso il basso se necessario per selezionare **SUM** nell'elenco e quindi premere **INVIO**.
    
    ![Scegliere SUM dall'elenco](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Viene visualizzata una parentesi aperta, con un elenco a discesa di suggerimenti con le colonne disponibili che è possibile passare alla funzione SUM.
    
    ![Scegliere la colonna](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
1. Le espressioni sono sempre racchiuse tra una parentesi aperta e una chiusa. Per questo esempio, l'espressione contiene un solo argomento da passare alla funzione SUM, ovvero la colonna **SalesAmount**. Iniziare a digitare *SalesAmount* fino a quando non rimane nell'elenco solo il valore **Sales(SalesAmount)** . 

    Il nome della colonna preceduto dal nome della tabella viene chiamato nome completo della colonna. I nomi di colonna completi semplificano la lettura delle formule.
    
    ![Selezionare SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
1. Selezionare **Sales[SalesAmount]** dall'elenco, quindi immettere una parentesi chiusa.
    
    > [!TIP]
    > Gli errori di sintassi sono spesso causati da parentesi chiuse mancanti o nella posizione sbagliata.
    
    
    
1. Sottrarre le altre due colonne all'interno della formula:

    a. Dopo la parentesi chiusa della prima espressione digitare uno spazio, un operatore di sottrazione (-) e quindi un altro spazio. 

    b. Immettere un'altra funzione SUM e iniziare a digitare *DiscountAmount* fino a quando non è possibile scegliere la colonna **Sales[DiscountAmount]** come argomento. Aggiungere una parentesi di chiusura. 

    c. Digitare uno spazio, un operatore di sottrazione, uno spazio, un'altra funzione SUM con **Sales[ReturnAmount]** come argomento e infine una parentesi di chiusura.
    
    ![Formula completa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
1. Per completare e convalidare la formula, premere **INVIO** oppure selezionare **Commit** (icona del segno di spunta) nella barra della formula. 

    La misura **Net Sales** convalidata è ora pronta per l'uso nella tabella **Sales** del riquadro **Campi**.
    
    ![Misura Net Sales nell'elenco di campi della tabella Sales](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
1. Se si esaurisce lo spazio disponibile per l'immissione di una formula o si vuole immetterla in righe separate, selezionare la freccia verso il basso sul lato destro della barra della formula per aumentare lo spazio. 

    La freccia verso il basso si trasforma in una freccia verso l'alto e viene visualizzata una finestra di dialogo di grandi dimensioni.

    ![Freccia verso l'alto per la formula](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

1. Separare le diverse parti della formula premendo **ALT** + **INVIO** per separare le righe oppure premendo **TAB** per aggiungere la spaziatura di tabulazione.

   ![Formula espansa](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Usare la misura nel report
Aggiungere la nuova misura **Net Sales** nell'area di disegno report e calcolare il fatturato netto per qualsiasi altro campo aggiunto al report. 

Per visualizzare il fatturato netto per paese:

1. Selezionare la misura **Net Sales** dalla tabella **Sales** o trascinarla sull'area di disegno report.
    
1. Selezionare il campo **RegionCountryName** della tabella **Geography** o trascinarlo nel grafico **Net Sales**.
    
    ![Fatturato netto per paese](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
1. Per visualizzare la differenza tra fatturato netto e vendite totali in base al paese, selezionare il campo **SalesAmount** oppure trascinarlo nel grafico. 

    ![Importo delle vendite e fatturato netto per paese](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

    Il grafico usa ora due misure: **SalesAmount**, sommato automaticamente da Power BI, e la misura **Net Sales** creata manualmente. Ogni misura è stata calcolata nel contesto di un altro campo, **RegionCountryName**.
    
### <a name="use-your-measure-with-a-slicer"></a>Usare la misura con un filtro dei dati

Aggiungere un filtro dei dati per filtrare ulteriormente il fatturato netto e l'importo delle vendite in base all'anno di calendario:
    
1. Selezionare un'area vuota accanto al grafico. Nel riquadro **Visualizzazioni** selezionare la visualizzazione **Tabella**. 

    Questa azione crea una visualizzazione di tabella vuota nell'area di disegno report.
    
    ![Nuova visualizzazione di tabella vuota](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
1. Trascinare il campo **Year** dalla tabella **Calendar** nella nuova visualizzazione di tabella vuota. 
    
    Dal momento che **Year** è un campo numerico, Power BI Desktop ne somma i valori. Questa somma non funziona bene quanto un'aggregazione, ma questo problema verrà affrontato nel passaggio successivo.

    ![Aggregazione in base all'anno](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3. Nella casella **Valori** nel riquadro **Visualizzazioni** selezionare la freccia verso il basso accanto a **Year** e quindi selezionare **Non riepilogare** nell'elenco. Nella tabella sono ora elencati singoli anni.
    
    ![Selezionare Non riepilogare](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Selezionare l'icona **Filtro dei dati** nel riquadro **Visualizzazioni** per convertire la tabella in un filtro dei dati. Se viene visualizzato un dispositivo di scorrimento invece di un elenco, selezionare **Elenco** dalla freccia verso il basso nel dispositivo di scorrimento.

    ![Convertire la tabella in un dispositivo di scorrimento](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Selezionare qualsiasi valore nel filtro dei dati **Year** per filtrare il grafico **Net Sales and Sales Amount by RegionCountryName** di conseguenza. Le misure **Net Sales** e **SalesAmount** vengono ricalcolate e vengono visualizzati i risultati nel contesto del campo **Year** selezionato. 
    
    ![Grafico filtrato in base all'anno](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Usare la misura in un'altra misura

Si supponga di voler scoprire quali prodotti registrano il fatturato netto maggiore per unità. Servirà una misura per dividere il fatturato netto per la quantità di unità vendute. Creare una nuova misura che divide il risultato della misura **Net Sales** per la somma di **Sales[SalesQuantity]** .

1.  Nel riquadro **Campi** creare una nuova misura denominata **Net Sales per Unit** nella tabella **Sales**.
    
1. Nella barra della formula iniziare a digitare *Net Sales*. L'elenco di suggerimenti mostra gli elementi che è possibile aggiungere. Selezionare **[Net Sales]** .
    
    ![Formula che usa Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
1. È anche possibile fare riferimento alle misure semplicemente digitando una parentesi aperta ( **[** ). L'elenco di suggerimenti mostra solo le misure per l'aggiunta alla formula.
    
    ![Con la parentesi quadra vengono visualizzate solo le misure](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
1. Immettere uno spazio, un operatore di divisione (/), un altro spazio, una funzione SUM e quindi digitare *Quantity*. L'elenco dei suggerimenti mostra tutte le colonne il cui nome contiene il termine *Quantity*. Selezionare **Sales[SalesQuantity]** , digitare la parentesi di chiusura e premere **INVIO** o selezionare **Commit** (icona del segno di spunta) per convalidare la formula. 

    La formula risultante dovrebbe essere simile alla seguente:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
1. Selezionare la misura **Net Sales per Unit** dalla tabella **Sales** o trascinarla in un'area vuota nell'area di disegno report. 

    Il grafico mostra l'importo del fatturato netto per unità per tutti i prodotti venduti. Questo grafico non fornisce molte informazioni, ma il problema verrà affrontato nel passaggio successivo.
    
    ![Fatturato netto complessivo per unità](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
1. Per ottenere un aspetto diverso, modificare il tipo di visualizzazione del grafico in **Mappa ad albero**.
    
    ![Passare alla mappa ad albero](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
1. Selezionare il campo **Product Category** oppure trascinarlo nella mappa ad albero o nel campo **Gruppo** del riquadro **Visualizzazioni**. A questo punto sono disponibili informazioni utili.
    
    ![Mappa ad albero in base alla categoria di prodotto](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Provare a rimuovere il campo **ProductCategory** e a trascinare invece il campo **ProductName** nel grafico. 
    
    ![Mappa ad albero in base al nome del prodotto](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
   È stato illustrato solo un esempio, ma comunque molto interessante. Sperimentare altri modi per filtrare e formattare la visualizzazione.

## <a name="what-youve-learned"></a>Informazioni apprese
Le misure costituiscono un potente strumento per ottenere le informazioni desiderate dai dati. Si è imparato a creare misure usando la barra della formula, ad assegnare loro un nome significativo, nonché a trovare e selezionare gli elementi della formula appropriati usando gli elenchi di suggerimenti DAX. È stato anche presentato il concetto di contesto, in cui il risultato dei calcoli nelle misure cambia in base ad altri campi o ad altre espressioni nella formula.

## <a name="next-steps"></a>Passaggi successivi
- Per altre informazioni sulle misure rapide di Power BI Desktop, che forniscono numerosi calcoli su misure comuni, vedere [Usare Misure rapide per eseguire facilmente calcoli comuni e avanzati](desktop-quick-measures.md).
  
- Per approfondire i concetti relativi alle formule DAX e creare misure più complesse, vedere [Nozioni di DAX in Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Questo articolo illustra i concetti fondamentali in DAX, ad esempio sintassi, funzioni e una maggiore comprensione del contesto.
  
- Non dimenticare di aggiungere ai Preferiti la pagina [Riferimento a Data Analysis Expressions (DAX)](https://docs.microsoft.com/dax/index). Questo riferimento include informazioni dettagliate sulla sintassi e sugli operatori DAX, nonché sulle oltre 200 funzioni DAX disponibili.

