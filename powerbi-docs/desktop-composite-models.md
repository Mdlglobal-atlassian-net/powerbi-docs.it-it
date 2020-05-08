---
title: Usare modelli compositi in Power BI Desktop
description: Creare modelli di dati con più connessioni dati e relazioni molti-a-molti in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 45f7ecee11cd57a73ed0e998dad26935b560c8ad
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161228"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Usare modelli compositi in Power BI Desktop

In precedenza, quando si usava DirectQuery in un report in Power BI Desktop, non erano consentite altre connessioni dati per tale report, sia di tipo DirectQuery che Importa. Con i modelli compositi questa restrizione non esiste più. Un report può includere senza problemi connessioni dati da più di una connessione dati DirectQuery o Importa, in qualsiasi combinazione scelta.

La funzionalità dei modelli compositi in Power BI Desktop è costituita da tre funzionalità correlate:

* **Modelli compositi**: Consente a un report di avere più connessioni dati, tra cui connessioni DirectQuery o Importazione, in qualsiasi combinazione. Questo articolo descrive i modelli compositi in dettaglio.

* **Relazioni molti-a-molti**: Con i modelli compositi è possibile stabilire *relazioni molti-a-molti* tra le tabelle. Questo approccio consente di rimuovere i requisiti per i valori univoci nelle tabelle. Annulla anche le soluzioni alternative precedenti, ad esempio l'introduzione di nuove tabelle solo per stabilire relazioni. Per altre informazioni, vedere [Applicare le relazioni molti-a-molti in Power BI Desktop](desktop-many-to-many-relationships.md).

* **Modalità di archiviazione**: Ora è possibile specificare gli oggetti visivi che eseguono query sulle origini dati back-end. Quelli che non la richiedono vengono importati anche se basati su DirectQuery, con conseguente miglioramento delle prestazioni e riduzione del carico per il back-end. In precedenza, anche oggetti visivi semplici, come i filtri dei dati, attivavano query per le origini back-end. Per altre informazioni, vedere [Gestire la modalità di archiviazione in Power BI Desktop](desktop-storage-mode.md).

## <a name="use-composite-models"></a>Usare i modelli compositi

Con i modelli compositi è possibile connettersi a diversi tipi di origini dati quando si usa Power BI Desktop o il servizio Power BI. È possibile effettuare tali connessioni dati in due modi:

* Importando i dati in Power BI, che è il modo più comune per ottenere i dati.
* Connettendosi direttamente ai dati nel relativo repository di origine tramite DirectQuery. Per altre informazioni su DirectQuery, vedere [Uso di DirectQuery in Power BI](desktop-directquery-about.md).

Quando si usa DirectQuery, i modelli compositi consentono di creare un modello di Power BI, ad esempio un singolo file *PBIX* di Power BI Desktop, che consente di eseguire una o entrambe le azioni seguenti:

* Combina i dati da una o più origini DirectQuery.
* Combina i dati da origini DirectQuery e dati importati.

Ad esempio, usando i modelli compositi è possibile creare un modello che combina i tipi di dati seguenti:

* Dati di vendita da un data warehouse aziendale.
* Dati di destinazione delle vendite da un database di SQL Server di reparto.
* Dati importati da un foglio di calcolo.

Un modello che combina dati da più di un'origine DirectQuery o combina origini DirectQuery con dati importati è noto come modello composito.

È possibile creare relazioni tra le tabelle come sempre, anche quando le tabelle provengono da origini diverse. Tutte le relazioni tra origini vengono create con una cardinalità molti-a-molti, indipendentemente dalla cardinalità effettiva. È possibile modificarle in uno-a-molti, molti-a-uno o uno-a-uno. Indipendentemente dalla cardinalità impostata, le relazioni tra origini hanno un comportamento diverso. Non è possibile usare le funzioni DAX (Data Analysis Expressions) per recuperare i valori sul lato `one` dal lato `many`. Si potrebbe anche osservare un impatto sulle prestazioni rispetto alle relazioni molti-a-molti all'interno della stessa origine.

> [!NOTE]
> Nel contesto dei modelli compositi, tutte le tabelle importate rappresentano in effetti una singola origine, indipendentemente dall'effettiva origine dati sottostante.

## <a name="example-of-a-composite-model"></a>Esempio di un modello composito

Per un esempio di modello composito, esaminare un report connesso a un data warehouse aziendale in SQL Server usando DirectQuery. In questo caso, il data warehouse contiene i dati **Sales by Country** (Vendite per paese), **Quarter** (Trimestre) e **Bike (Product)** (Bici - Prodotto), come illustrato nell'immagine seguente:

![Visualizzazione delle relazioni per i modelli compositi](media/desktop-composite-models/composite-models_04.png)

A questo punto è possibile creare oggetti visivi semplici usando i campi da questa origine. L'immagine seguente illustra il totale delle vendite per *ProductName*, per un trimestre selezionato.

![Oggetto visivo basato sui dati](media/desktop-composite-models/composite-models_05.png)

E se fossero disponibili dati in un foglio di calcolo di Office Excel sul responsabile del prodotto assegnato a ogni prodotto insieme alla relativa priorità di marketing? Se si vuole visualizzare l'importo delle vendite (**Sales Amount**) in base al responsabile del prodotto (**Product Manager**), potrebbe non essere possibile aggiungere questi dati locali nel data warehouse aziendale o nella migliore delle ipotesi potrebbero essere necessari dei mesi.

Potrebbe essere possibile importare i dati sulle vendite dal data warehouse, invece di usare DirectQuery. E i dati sulle vendite potrebbero quindi essere combinati con i dati importati dal foglio di calcolo. Tuttavia, questo approccio è irragionevole, per i motivi che conducono all'uso di DirectQuery in primo luogo. I motivi possono includere i seguenti:

* Una combinazione delle regole di sicurezza applicate nell'origine sottostante.
* La necessità di essere in grado di visualizzare i dati più recenti.
* L'enorme quantità di dati.

Questi sono gli scenari in cui entrano in gioco i modelli compositi. I modelli compositi consentono di connettersi al data warehouse usando DirectQuery e quindi di usare **Recupera dati** per origini aggiuntive. In questo esempio, viene prima di tutto stabilita una connessione DirectQuery al data warehouse aziendale. Si usa **Recupera dati**, si sceglie **Excel** e quindi si passa al foglio di calcolo che contiene i dati locali. Infine, si importa il foglio di calcolo che contiene i nomi dei prodotti (*ProductName*), il responsabile del prodotto assegnato (**Product Manager**) e la priorità (**Priority**).  

![Finestra Strumento di navigazione](media/desktop-composite-models/composite-models_06.png)

Nell'elenco **Campi** è possibile visualizzare due tabelle: la tabella **Bike** originale da SQL Server e una nuova tabella **ProductManagers**. La nuova tabella contiene i dati importati da Excel.

![Visualizzazione dei campi delle tabelle](media/desktop-composite-models/composite-models_07.png)

Allo stesso modo, nella visualizzazione **Relazioni** in Power BI Desktop è ora disponibile una tabella aggiuntiva denominata **ProductManagers**.

![Visualizzazione delle relazioni delle tabelle](media/desktop-composite-models/composite-models_08.png)

È ora necessario mettere in relazione le tabelle con le altre tabelle nel modello. Come sempre, si crea una relazione tra la tabella **Bike** da SQL Server e la tabella **ProductManagers** importata. La relazione è tra **Bike[ProductName]** e **ProductManagers[ProductName]** . Come illustrato in precedenza, tutte le relazioni che attraversano l'origine sono impostate sulla cardinalità predefinita molti-a-molti.

![Finestra "Crea relazione"](media/desktop-composite-models/composite-models_09.png)

La relazione così stabilita è ora inclusa nella visualizzazione **Relazione** in Power BI Desktop, come prevedibile.

![Visualizzazione della nuova relazione](media/desktop-composite-models/composite-models_10.png)

È ora possibile creare oggetti visivi usando uno qualsiasi dei campi nell'elenco **Campi**. Questo approccio consente di unire facilmente i dati da più origini. Ad esempio, l'importo totale *SalesAmount* per ogni *Product Manager* viene visualizzato nell'immagine seguente:

![Riquadro Campi](media/desktop-composite-models/composite-models_11.png)

L'esempio seguente mostra un caso comune di una tabella delle *dimensioni*, ad esempio **Product** oppure **Customer**, che viene estesa con dati aggiuntivi importati da altre origini. È anche possibile configurare le tabelle per l'uso di DirectQuery per connettersi a varie origini. Per continuare con questo esempio, si immagini che i valori di **SalesTargets** per ogni **Country** e **Period** siano archiviati in un database di reparto separato. È possibile usare **Recupera dati** per connettersi a tali dati come di consueto, come illustrato nell'immagine seguente:

![Finestra Strumento di navigazione](media/desktop-composite-models/composite-models_12.png)

Come in precedenza, è possibile creare relazioni tra la nuova tabella e altre tabelle nel modello e quindi creare oggetti visivi che combinano i dati delle tabelle. Di seguito è raffigurata di nuovo la visualizzazione **Relazioni** in cui sono state stabilite nuove relazioni:

![Visualizzazione Relazioni con molte tabelle](media/desktop-composite-models/composite-models_13.png)

L'immagine successiva si basa sui nuovi dati e sulle nuove relazioni creati. L'oggetto visivo in basso a sinistra mostra il totale di *Sales Amount* rispetto al *Target* e il calcolo della varianza mostra la differenza. I dati **Sales Amount** e **Target** provengono da due database di SQL Server diversi.

![Immagine che mostra altri dati](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Impostare la modalità di archiviazione

Ogni tabella in un modello composito ha una modalità di archiviazione che indica se la tabella è basata su DirectQuery o importazione. La modalità di archiviazione può essere visualizzata e modificata nel riquadro **Proprietà**. Per visualizzare la modalità di archiviazione, fare clic con il pulsante destro del mouse su una tabella nell'elenco **Campi** e quindi scegliere **Proprietà**. L'immagine seguente illustra la modalità di archiviazione per la tabella **SalesTargets**.

La modalità di archiviazione può anche essere visualizzata nella descrizione comando per ogni tabella.

![Descrizione comando che visualizza la modalità di archiviazione](media/desktop-composite-models/composite-models_16.png)

Per qualsiasi file di Power BI Desktop (*PBIX*) che contiene alcune tabelle da DirectQuery e alcune tabelle importate importazione, la barra di stato visualizza la modalità di archiviazione **Mista**. È possibile fare clic su tale termine nella barra di stato e passare facilmente a tutte le tabelle da importare.

Per altre informazioni sulla modalità di archiviazione, vedere [Gestire la modalità di archiviazione in Power BI Desktop](desktop-storage-mode.md).  

> [!NOTE]
> È possibile usare la modalità di archiviazione *Mista* in Power BI Desktop e nel servizio Power BI.

## <a name="calculated-tables"></a>Tabelle calcolate

È possibile aggiungere tabelle calcolate a un modello che usa DirectQuery. Le espressioni DAX (Data Analysis Expression) che definiscono la tabella calcolata possono fare riferimento a tabelle importate o che usano DirectQuery o a una combinazione delle due.

Le tabelle calcolate vengono sempre importate e i dati vengono aggiornati quando si aggiornano le tabelle. Se una tabella calcolata fa riferimento a una tabella DirectQuery, gli oggetti visivi che fanno riferimento alla tabella DirectQuery mostrano sempre i valori più recenti nell'origine sottostante. In alternativa, gli oggetti visivi che fanno riferimento alla tabella calcolata mostrano i valori al momento dell'ultimo aggiornamento della tabella calcolata.

## <a name="security-implications"></a>Implicazioni per la sicurezza

Per i modelli compositi esistono alcune implicazioni per la sicurezza. Una query inviata a un'origine dati può includere valori di dati recuperati da un'altra origine. Nell'esempio precedente l'oggetto visivo che rappresenta **(Sales Amount)** per **Product Manager** invia una query SQL al database relazionale Sales. Tale query SQL potrebbe contenere i nomi dei Product Manager e dei Product a loro associati.

![Script che mostra le implicazioni per la sicurezza](media/desktop-composite-models/composite-models_17.png)

Per questo motivo, le informazioni archiviate nel foglio di calcolo vengono ora incluse in una query inviata al database relazionale. Se queste informazioni sono riservate, è necessario considerare le implicazioni per la sicurezza. In particolare, tenere conto dei punti seguenti:

* Qualsiasi amministratore del database che può visualizzare le tracce o i log di controllo può visualizzare queste informazioni, anche senza autorizzazioni per i dati nell'origine iniziale. In questo esempio, l'amministratore dovrebbe avere le autorizzazioni per il file di Excel.

* Devono essere considerate le impostazioni di crittografia per ogni origine. È opportuno evitare il recupero di informazioni da un'origine usando una connessione crittografata per poi includerle inavvertitamente in una query che viene inviata a un'altra origine usando una connessione non crittografata.

Per ottenere una conferma che sono state prese in considerazione le implicazioni per la sicurezza, Power BI Desktop visualizza un messaggio di avviso quando viene creato un modello composito.  

Per motivi analoghi, prestare attenzione quando si apre un file di Power BI Desktop inviato da un'origine non attendibile. Se il file contiene modelli compositi, le informazioni recuperate da qualcuno da un'origine con le credenziali dell'utente che apre il file verrebbero inviate a un'altra origine dati come parte della query. Le informazioni potrebbero essere visualizzate dall'autore malintenzionato del file di Power BI Desktop. Quando si apre inizialmente un file di Power BI Desktop che contiene più origini, Power BI Desktop visualizza un avviso. Questo avviso è simile a quello visualizzato quando si apre un file che contiene query SQL native.  

## <a name="performance-implications"></a>Implicazioni per le prestazioni  

Quando si usa DirectQuery, occorre tenere sempre conto delle prestazioni, principalmente per garantire che l'origine back-end abbia risorse sufficienti per offrire una buona esperienza agli utenti. Un'esperienza ottimale significa che gli oggetti visivi vengono aggiornati in massimo cinque secondi. Per altri consigli per le prestazioni, vedere [Informazioni sull'uso di DirectQuery in Power BI](desktop-directquery-about.md).

Esistono considerazioni aggiuntive per le prestazioni di cui tenere conto quando si usano i modelli compositi. Un singolo oggetto visivo può comportare l'invio di query a più origini, operazione che implica spesso il passaggio dei risultati da una query attraverso una seconda origine. Questa situazione può portare alle forme di esecuzione seguenti:

* **Una query SQL che include un numero elevato di valori letterali**: ad esempio, un oggetto visivo che richiede il totale di **Sales Amount** per un set di **Product Manager** selezionati dovrebbe prima di tutto trovare i **Product** gestiti da tali responsabili di prodotto. Questa sequenza deve essere eseguita prima che l'oggetto visivo invii una query SQL che include tutti gli ID di prodotto in una clausola `WHERE`.

* **Una query SQL che esegue una query a un livello inferiore di granularità, con i dati aggregati in locale in un secondo tempo**: Man mano che aumenta il numero di **Product** che soddisfano i criteri di filtro per **Product Manager**, può diventare inefficiente o non fattibile includere tutti i prodotti in una clausola `WHERE`. È invece possibile eseguire una query sull'origine relazionale al livello inferiore di **Product** e quindi aggregare i risultati in locale. Se la cardinalità di **Product** supera il limite di 1 milione, la query ha esito negativo.

* **Più query SQL, una per ogni valore di raggruppamento**: Quando l'aggregazione usa **DistinctCount**, con raggruppamento in base a una colonna dall'altra origine, se l'origine esterna non supporta il passaggio efficiente di molti valori letterali che definiscono il raggruppamento, è necessario inviare una query SQL per ogni valore di raggruppamento.

   Un oggetto visivo che richiede il conteggio di valori univoci per **CustomerAccountNumber** (dalla tabella di SQL Server) in base a **Product Manager** (importato dal foglio di calcolo) dovrebbe passare i dettagli dalla tabella **Product Managers** nella query inviata a SQL Server. Su altre origini, ad esempio Redshift, questa azione non è fattibile. Verrebbe invece inviata una query SQL per ogni **Sales Manager** fino a un limite pratico e la query avrebbe poi esito negativo.

Per ognuno di questi casi esistono implicazioni specifiche per le prestazioni e i dettagli esatti variano per ogni origine dati. Anche se la cardinalità delle colonne usate nella relazione che unisce le due origini resta ridotta (alcune migliaia), non dovrebbero esserci effetti sulle prestazioni. Man mano che aumenta la cardinalità, è necessario prestare maggiore attenzione all'impatto sulle prestazioni risultanti.

Inoltre, l'uso delle relazioni molti-a-molti significa che è necessario inviare query separate all'origine sottostante per ogni livello totale o subtotale, anziché aggregare i valori dettagliati in locale. Un oggetto visivo tabella semplice con totali invierebbe due query SQL, anziché una.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Esistono alcune limitazioni per questa versione dei modelli compositi:

Attualmente l'[aggiornamento incrementale](service-premium-incremental-refresh.md) è supportato solo per i modelli compositi che si connettono a origini dati SQL, Oracle e Teradata.

Le seguenti origini Live Connect multidimensionali non possono essere usate con i modelli compositi:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Set di dati Power BI
* Azure Analysis Services

Quando ci si connette a queste origini multidimensionali usando DirectQuery, non è possibile connettersi a un'altra origine DirectQuery o attuare combinazioni con dati importati.

Le limitazioni esistenti per DirectQuery sono valide anche quando si usano i modelli compositi. Molte di queste limitazioni si riferiscono attualmente a ogni singola tabella, a seconda della modalità di archiviazione della tabella. Ad esempio, una colonna calcolata per una tabella di importazione può fare riferimento ad altre tabelle, ma una colonna calcolata per una tabella di DirectQuery può fare riferimento solo alle colonne nella stessa tabella. Altre limitazioni si applicano al modello nel suo complesso, se una qualsiasi delle tabelle all'interno del modello è in modalità DirectQuery. Ad esempio, le funzionalità Informazioni rapide e Domande e risposte non sono disponibili per un modello se per una delle tabelle all'interno di esso è impostata la modalità di archiviazione DirectQuery.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui modelli compositi e DirectQuery, vedere gli articoli seguenti:

* [Relazioni molti-a-molti in Power BI Desktop](desktop-many-to-many-relationships.md)
* [Modalità di archiviazione in Power BI Desktop](desktop-storage-mode.md)
* [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
* [Origini dati supportate da DirectQuery in Power BI](desktop-directquery-data-sources.md)

