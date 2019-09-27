---
title: Machine Learning automatizzato in Power BI (anteprima)
description: Informazioni su come usare Machine Learning automatizzato (AutoML) in Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236451"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Machine Learning automatizzato in Power BI (anteprima)

Machine Learning automatizzato (AutoML) per i flussi di lavoro consente agli analisti aziendali di eseguire il training, convalidare e richiamare i modelli di Machine Learning (ML) direttamente in Power BI. Include un'esperienza semplice per la creazione di un nuovo modello di ML in cui gli analisti possono usare i propri flussi di dati per specificare i dati di input per il training del modello. Il servizio estrae automaticamente le funzionalità più rilevanti, seleziona un algoritmo appropriato e ottimizza e convalida il modello di ML. Dopo aver eseguito il training di un modello, Power BI genera automaticamente un report che include i risultati della convalida e spiega le prestazioni e i risultati agli analisti. Il modello può quindi essere richiamato per tutti i dati nuovi o aggiornati all'interno del flusso di dati.

![Schermata di Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Machine Learning automatizzato (AutoML) è disponibile per i flussi di data ospitati solo in Power BI Premium e nelle capacità incorporate. In questa versione di anteprima AutoML consente di eseguire il training dei modelli di Machine Learning per modelli di previsione per dati binari, classificazione e regressione.

## <a name="working-with-automl"></a>Uso di AutoML

[I flussi di dati Power BI](service-dataflows-overview.md) offrono la preparazione dei dati self-service per i Big Data. AutoML consente di sfruttare le attività di preparazione dei dati per la creazione di modelli di Machine Learning, direttamente all'interno di Power BI.

AutoML in Power BI consente agli analisti di dati di usare i flussi di dati per creare modelli di Machine Learning con un'esperienza semplificata, usando solo competenze di Power BI. La maggior parte del data science su cui si basa la creazione dei modelli di Machine Learning è automatizzata da Power BI, con controlli che assicurano la buona qualità del modello prodotto e la visibilità necessaria per visualizzare informazioni complete sul processo usato per creare il modello.

AutoML supporta la creazione di modelli di **previsione per dati binari**, **classificazione**e **regressione** per i flussi di dati. Sono tipi di modelli di Machine Learning con supervisione, ovvero l'apprendimento si basa sui risultati noti delle osservazioni precedenti al fine di prevedere i risultati di altre osservazioni. Il set di dati di input usato per il training di un modello AutoML è un set di record **etichettati** con i risultati noti.

AutoML in Power BI integra il [Machine Learning automatizzato](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) del [servizio Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) per creare i modelli di Machine Learning. Tuttavia, non è necessaria una sottoscrizione di Azure per usare AutoML in Power BI. Il processo di training e hosting dei modelli di Machine Learning è gestito interamente dal servizio Power BI.

Dopo aver eseguito il training di un modello di Machine Learning, AutoML genera automaticamente un report di Power BI in cui vengono spiegate le prestazioni probabili del modello di Machine Learning. AutoML rende più comprensibile la spiegazione evidenziando i fattori di influenza chiave tra gli input che influenzano le previsioni restituite dal modello. Il report include anche le metriche chiave per il modello, a seconda del tipo di modello di Machine Learning.

Altre pagine del report generato contengono un riepilogo statistico del modello e i dettagli del training. Il riepilogo statistico è di particolare interesse per gli utenti che vogliono visualizzare le misure di data science standard delle prestazioni per il modello. I dettagli del training riepilogano tutte le iterazioni eseguite per creare il modello, con i parametri di modellazione associati. Viene inoltre descritto il modo in cui è stato usato ogni input per creare il modello di Machine Learning.

È quindi possibile applicare il modello di Machine Learning ai dati per l'assegnazione dei punteggi. Quando il flusso di dati viene aggiornato, le previsioni del modello di Machine Learning vengono automaticamente applicate ai dati. Power BI include anche una spiegazione specifica per ogni punteggio di previsione prodotto dal modello di Machine Learning.

## <a name="creating-a-machine-learning-model"></a>Creazione di un modello di Machine Learning

Questa sezione descrive la procedura di creazione di un modello di apprendimento AutoML. 

### <a name="data-prep-for-creating-an-ml-model"></a>Preparazione dei dati per la creazione di un modello di Machine Learning

Per creare un modello di Machine Learning in Power BI, è necessario prima creare un flusso di dati per i dati con le informazioni relative ai risultati cronologici, da usare per il training del modello di Machine Learning. Per informazioni dettagliate sulla configurazione del flusso di dati, vedere [Preparazione dei dati self-service in Power BI](service-dataflows-overview.md).

Nella versione corrente Power BI usa solo i dati di una singola entità per eseguire il training del modello di Machine Learning. Quindi, se i dati cronologici sono costituiti da più entità, è necessario creare manualmente un join dei dati in una sola entità del flusso di dati. È inoltre necessario aggiungere colonne calcolate per eventuali metriche aziendali che possono essere predittori forti per il risultato che si sta tentando di prevedere.

AutoML presenta requisiti specifici in termini di dati per eseguire il training di un modello di Machine Learning. Questi requisiti sono descritti nelle sezioni riportate di seguito, in base ai rispettivi tipi di modello.

### <a name="configuring-the-ml-model-inputs"></a>Configurazione degli input del modello di Machine Learning

Per creare un modello AutoML, selezionare l'icona ML nella colonna **Azioni** dell'entità del flusso di dati con i dati cronologici e selezionare **Aggiungi un modello di Machine Learning**.

![Aggiungere un modello di Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Viene avviata un'esperienza semplificata, costituita da una procedura guidata che illustra all'utente i passaggi del processo di creazione del modello di Machine Learning. La procedura guidata include i semplici passaggi riportati di seguito.

1. Selezionare l'entità con i dati dei risultati cronologici e il campo per cui si vuole una previsione
2. Scegliere un tipo di modello in base al tipo di previsione che si vuole visualizzare
3. Selezionare gli input che il modello dovrà usare come segnali predittivi
4. Assegnare un nome al modello e salvare la configurazione

Il campo del risultato cronologico identifica l'attributo dell'etichetta per il training del modello di Machine Learning, come illustra la figura seguente.

![Selezionare i dati del risultato cronologico](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Quando si specifica il campo del risultato cronologico AutoML analizza i dati dell'etichetta per identificare i tipi di modelli di Machine Learning che possono essere sottoposti a training per quei dati e suggerisce il tipo di modello più adatto per il training. 

> [!NOTE]
> Alcuni tipi di modelli possono non essere supportati per i dati selezionati.

AutoML analizza anche tutti i campi dell'entità selezionata per suggerire gli input che possono essere usati per il training del modello di Machine Learning. Questo processo è approssimativo e si basa sull'analisi statistica, quindi è necessario esaminare gli input in uso. Eventuali input che dipendono dal campo del risultato cronologico, o dal campo dell'etichetta, non devono essere usati per il training del modello di Machine Learning, perché influiscono negativamente sulle prestazioni.

![Personalizza i campi di input](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

Nel passaggio finale è possibile assegnare un nome al modello e salvarne le impostazioni.

In questa fase viene richiesto di aggiornare il flusso di dati e viene avviato il processo di training per il modello di Machine Learning.

### <a name="ml-model-training"></a>Training del modello di Machine Learning

Il training dei modelli AutoML fa parte dell'aggiornamento del flusso di dati. AutoML prima prepara i dati per il training.

Suddivide i dati cronologici specificati in set di dati di training e test. Il set di dati di test è un set di dati di controllo usato per convalidare le prestazioni del modello dopo il training. Nel flusso di dati si ottengono come entità di **training e test**. AutoML usa la convalida incrociata per convalidare il modello.

Ogni campo di input viene quindi analizzato e viene applicata l'imputazione, che sostituisce eventuali valori mancanti con valori sostituiti. AutoML usa due strategie di imputazione diverse. Vengono quindi applicati ai dati eventuali campionamenti e normalizzazioni necessari.

AutoML applica diverse trasformazioni a ogni campo di input selezionato in base al relativo tipo di dati e alle relative proprietà statistiche. AutoML usa queste trasformazioni per estrarre le funzionalità da usare per il training del modello di Machine Learning.

Il processo di training per i modelli AutoML è costituito da un massimo di 50 iterazioni con algoritmi di modellazione e impostazioni di iperparametri diversi per trovare il modello con le migliori prestazioni. Le prestazioni di ognuno di questi modelli vengono valutate usando la convalida eseguita con il set di dati di test dei dati di controllo. Durante questo passaggio del training, AutoML crea diverse pipeline per il training e la convalida di queste iterazioni. Il processo di valutazione delle prestazioni dei modelli può richiedere tempo, da diversi minuti a un paio d'ore, a seconda delle dimensioni del set di dati e delle risorse di capacità dedicate disponibili.

In alcuni casi il modello finale generato può usare l'apprendimento di tipo ensemble, in cui vengono usati più modelli per ottimizzare le prestazioni predittive.

### <a name="automl-model-explainability"></a>Spiegazione del modello AutoML

Dopo aver eseguito il training del modello, AutoML analizza la relazione tra le funzionalità di input e l'output del modello. Valuta la magnitudine e la direzione delle modifiche apportate all'output del modello per il set di dati di test dei dati di controllo per ogni funzionalità di input. Questa operazione è nota come *priorità della funzionalità*.

![Priorità funzionalità](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Report sul modello AutoML

AutoML genera un report di Power BI che contiene un riepilogo delle prestazioni del modello durante la convalida e indica la priorità della funzionalità globale. Il report riepiloga i risultati dell'applicazione del modello di Machine Learning ai dati del test dei dati di controllo e del confronto tra le previsioni e i valori dei risultati noti.

È possibile esaminare il report sul modello per comprenderne le prestazioni. È anche possibile verificare che i fattori di influenza chiave del modello siano allineati con le informazioni aziendali dettagliate sui risultati noti.

I grafici e le misure usati per descrivere le prestazioni del modello nel rapporto dipendono dal tipo di modello. I grafici e le misure delle prestazioni sono descritti nelle sezioni seguenti.

Altre pagine del report possono descrivere misure statistiche sul modello da una prospettiva di data science. Ad esempio, il report sulla **previsione per dati binari** include un grafico del guadagno e la curva ROC per il modello.

I report includono inoltre una pagina dei **dettagli del training** che contiene una descrizione del modo in cui è stato eseguito il training del modello e un grafico che descrive le prestazioni del modello per ogni esecuzione di iterazione.

![Dettagli del training](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

In un'altra sezione di questa pagina viene descritto il metodo di imputazione usato per compilare i valori mancanti nei campi di input, nonché il modo in cui ogni campo di input è stato trasformato per estrarre le funzionalità usate nel modello. Sono inclusi inoltre i parametri usati dal modello finale.

![Altre informazioni per il modello](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Se il modello prodotto usa l'apprendimento di tipo ensemble, la pagina dei **dettagli del training** include anche una sezione che descrive il peso di ogni modello costituente dell'ensemble, nonché i relativi parametri.

![Peso nell'ensamble](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Applicazione del modello AutoML

Se si è soddisfatti delle prestazioni del modello di Machine Learning creato, è possibile applicarlo ai dati nuovi o aggiornati quando si aggiorna il flusso di dati. È possibile eseguire questa operazione dal report sul modello, selezionando il pulsante **Applica** nell'angolo superiore destro.

Per applicare il modello di Machine Learning, è necessario specificare il nome dell'entità a cui deve essere applicato e un prefisso per le colonne che verranno aggiunte a questa entità per l'output del modello. Il prefisso predefinito per i nomi delle colonne è il nome del modello. La funzione *Applica* può includere parametri aggiuntivi specifici del tipo di modello.

L'applicazione del modello di Machine Learning crea una nuova entità del flusso di dati con il suffisso **enriched <nome_modello>** . Ad esempio, se si applica il modello _PurchaseIntent_ all'entità _OnlineShoppers_, l'output genera **OnlineShoppers enriched PurchaseIntent**.

Attualmente, l'entità di output non può essere usata per visualizzare l'anteprima dei risultati del modello di Machine Learning nell'editor di Power Query. Nelle colonne di output viene sempre visualizzato null come risultato. Per visualizzare i risultati, viene creata una seconda entità di output con il suffisso **enriched <nome_modello> Preview** quando viene applicato il modello.

Per visualizzare in anteprima i risultati nell'editor di query, è necessario aggiornare il flusso di dati.

![Editor di query](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Quando si applica il modello, AutoML fa in modo che le previsioni siano sempre aggiornate quando viene aggiornato il flusso di dati.

AutoML include anche una spiegazione specifica per ogni riga di cui calcola il punteggio nell'entità di output.

Per usare le informazioni dettagliate e le previsioni del modello di Machine Learning in un report di Power BI, è possibile connettersi all'entità di output da Power BI Desktop usando il connettore di **flussi di dati**.

## <a name="binary-prediction-models"></a>Modelli di previsione per dati binari

I modelli di previsione per dati binari, più formalmente noti come **modelli di classificazione binaria**, vengono usati per classificare un set di dati in due gruppi. Consentono di fare previsioni per eventi che possono avere un risultato binario, ad esempio se un'opportunità di vendita verrà convertita, se un account passa a un'altra azienda, se una fattura verrà pagata in tempo, se una transazione è fraudolenta e così via.

Poiché il risultato è binario, Power BI prevede che l'etichetta di un modello di previsione per dati binari sia un valore booleano, con risultati noti con etichetta **true** o **false**. Ad esempio, in un modello di conversione di opportunità di vendita, le opportunità di vendita sono contrassegnate dall'etichetta true, le opportunità perse dall'etichetta false e le opportunità di vendita aperte dall'etichetta null.

L'output di un modello di previsione per dati binari è un punteggio di probabilità, che identifica la probabilità che venga ottenuto il risultato corrispondente al valore dell'etichetta true.

### <a name="training-a-binary-prediction-model"></a>Training di un modello di previsione per dati binari

Per creare un modello di previsione per dati binari, l'entità di input contenente i dati di training deve avere un campo booleano come campo del risultato cronologico per identificare i risultati noti precedenti.

Prerequisiti:

* Un campo booleano da usare come campo del risultato cronologico
* Sono necessarie almeno 50 righe di dati cronologici per ogni classe di risultati

In generale, se i risultati precedenti sono identificati da campi di un altro tipo di dati, è possibile aggiungere una colonna calcolata per trasformarli in un valore booleano usando Power Query.

Il processo di creazione per un modello di previsione per dati binari segue gli stessi passaggi degli altri modelli AutoML, descritti in precedenza nella sezione **Configurazione degli input del modello di Machine Learning**.

### <a name="binary-prediction-model-report"></a>Report del modello di previsione per dati binari

Il modello di previsione per dati binari produce come output una probabilità che un record ottenga il risultato definito dal valore dell'etichetta booleana come True. Il report include un filtro dei dati per la soglia di probabilità, che influisce sul modo in cui vengono interpretati i punteggi sopra e sotto la soglia di probabilità.

Il report descrive le prestazioni del modello in termini di *veri positivi*, *falsi positivi*, *veri negativi* e *falsi negativi*. I veri positivi e i veri negativi sono risultati previsti correttamente per le due classi nei dati del risultato. I falsi positivi sono i risultati che pur avendo l'etichetta booleana del valore False, sono stati previsti come True. Viceversa, i falsi negativi sono risultati in cui il valore effettivo dell'etichetta booleana era True, ma sono stati previsti come False.

Le misure, ad esempio la precisione e il richiamo, descrivono l'effetto della soglia di probabilità sui risultati previsti. È possibile usare il filtro dei dati della soglia di probabilità per selezionare una soglia che raggiunga una compromesso equilibrato tra precisione e richiamo.

![Anteprima dell'accuratezza](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

La pagina **Report di accuratezza** del report sul modello include il grafico dei *guadagni cumulativi* e la curva ROC per il modello. Si tratta di misure statistiche delle prestazioni del modello. Nei report sono incluse le descrizioni dei grafici illustrati.

![Schermata del report di accuratezza](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Applicazione di un modello di previsione per dati binari

Per applicare un modello di previsione per dati binari, è necessario specificare l'entità con i dati a cui verranno applicate le previsioni dal modello di Machine Learning. Altri parametri includono il prefisso del nome della colonna di output e la soglia di probabilità per la classificazione del risultato previsto.

![Input della previsione](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Quando viene applicato un modello di previsione per dati binari, vengono aggiunte tre colonne di output all'entità di output arricchita. Si tratta di **PredictionScore**, **PredictionOutcome** e **PredictionExplanation**. I nomi delle colonne nell'entità hanno il prefisso specificato quando viene applicato il modello.

La colonna **PredictionOutcome** contiene l'etichetta del risultato previsto. Se le probabilità dei record superano la soglia, probabilmente il risultato verrà raggiunto, mentre se le probabilità sono sotto la soglia, si prevede che il risultato probabilmente non verrà raggiunto.

La colonna **PredictionExplanation** contiene una spiegazione con l'influenza specifica delle funzionalità di input su **PredictionScore**. Si tratta di una raccolta in formato JSON dei pesi delle funzionalità di input per la previsione.

## <a name="classification-models"></a>Modelli di classificazione

I modelli di classificazione vengono usati per classificare un set di dati in più gruppi o classi.  Si usano per prevedere gli eventi che possono avere uno di più risultati possibili, ad esempio se un cliente probabilmente ha un valore di durata molto elevato, elevato, medio o basso, se il rischio di default è alto, moderato, basso o molto basso e così via.

L'output di un modello di classificazione è un punteggio di probabilità, che identifica la probabilità che un record raggiunga i criteri per una determinata classe.

### <a name="training-a-classification-model"></a>Training di un modello di classificazione

L'entità di input contenente i dati di training per un modello di classificazione deve avere un campo stringa o numerico come campo del risultato cronologico che identifica i risultati noti precedenti.

Prerequisiti:

* Sono necessarie almeno 50 righe di dati cronologici per ogni classe di risultati

Il processo di creazione per un modello di classificazione segue gli stessi passaggi degli altri modelli AutoML, descritti in precedenza nella sezione **Configurazione degli input del modello di Machine Learning**.

### <a name="classification-model-report"></a>Report sul modello di classificazione

Il report sul modello di classificazione viene generato applicando il modello di Machine Learning ai dati di test dei dati di controllo e confrontando la classe prevista per un record con la classe nota effettiva.

Il report sul modello include un grafico che illustra la suddivisione dei record classificati in modo corretto e non corretto per ogni classe nota.

![Report sul modello](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Un ulteriore drilldown specifico della classe consente di analizzare il modo in cui vengono distribuite le previsioni per una classe nota. Sono incluse le altre classi in cui i record della classe nota probabilmente sono classificati erroneamente.

![Report sull'analisi](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

La spiegazione del modello nel report include anche i predittori principali per ogni classe.

Il report sul modello di classificazione include anche una pagina di dettagli del training simile alle pagine usate per altri tipi di modello, come descritto in precedenza nella sezione **Report sul modello AutoML** di questo articolo.

### <a name="applying-a-classification-model"></a>Applicazione di un modello di classificazione

Per applicare un modello di classificazione di Machine Learning, è necessario specificare l'entità con i dati di input e il prefisso del nome della colonna di output.

Quando viene applicato un modello di classificazione, vengono aggiunte tre colonne di output all'entità di output arricchita. Si tratta di **PredictionScore**, **PredictionClass** e **PredictionExplanation**. I nomi delle colonne nell'entità hanno il prefisso specificato quando viene applicato il modello.

La colonna **PredictionClass** contiene la classe prevista con maggiore probabilità per il record. La colonna **PredictionScore** contiene l'elenco dei punteggi di probabilità per il record per ogni classe possibile.

La colonna **PredictionExplanation** contiene una spiegazione con l'influenza specifica delle funzionalità di input su **PredictionScore**. Si tratta di una raccolta in formato JSON dei pesi delle funzionalità di input per la previsione.

## <a name="regression-models"></a>Modelli di regressione

I modelli di regressione vengono usati per prevedere un valore, ad esempio i ricavi che probabilmente verranno realizzati da un contratto di vendita, il valore di durata di un account, l'importo di una fattura che probabilmente verrà pagata, la data in cui è possibile che una fattura venga pagata e così via.

L'output di un modello di regressione è il valore previsto.

### <a name="training-a-regression-model"></a>Training di un modello di regressione

L'entità di input contenente i dati di training per un modello di regressione deve avere un campo numerico come campo del risultato cronologico che identifica i valori dei risultati noti precedenti.

Prerequisiti:

* Sono necessarie almeno 100 righe di dati cronologici per un modello di regressione

Il processo di creazione per un modello di regressione segue gli stessi passaggi degli altri modelli AutoML, descritti in precedenza nella sezione **Configurazione degli input del modello di Machine Learning**.

### <a name="regression-model-report"></a>Report sul modello di regressione

Analogamente agli altri report sui modelli AutoML, il report di regressione si basa sui risultati dell'applicazione del modello ai dati di test dei dati di controllo.

Il report sul modello include un grafico che confronta i valori previsti con il valore effettivo. In questo grafico la distanza dalla diagonale indica l'errore nella previsione.

Il grafico degli errori residui indica la distribuzione della percentuale di errore media per valori diversi nel set di dati di test dei dati di controllo. L'asse orizzontale rappresenta la media del valore effettivo per il gruppo, con la dimensione della bolla che indica la frequenza o il numero di valori in quell'intervallo. L'asse verticale è l'errore residuo medio.

![Grafico degli errori residui](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Il report sul modello di regressione include anche una pagina di dettagli del training come i report su altri tipi di modello, come descritto in precedenza nella sezione **Report sul modello AutoML**.

### <a name="applying-a-regression-model"></a>Applicazione di un modello di regressione

Per applicare un modello di regressione di Machine Learning, è necessario specificare l'entità con i dati di input e il prefisso del nome della colonna di output.

![Applicare una regressione](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Quando viene applicato un modello di regressione, vengono aggiunte due colonne di output all'entità di output arricchita. Si tratta di **PredictionValue** e **PredictionExplanation**. I nomi delle colonne nell'entità hanno il prefisso specificato quando viene applicato il modello.

La colonna **PredictionValue** contiene il valore previsto per il record in base ai campi di input. La colonna **PredictionExplanation** contiene una spiegazione con l'influenza specifica delle funzionalità di input su **PredictionValue**. Si tratta di una raccolta in formato JSON dei pesi delle funzionalità di input.

## <a name="next-steps"></a>Passaggi successivi

Questo articolo ha offerto una panoramica su Machine Learning automatizzato per i flussi di dati nel servizio Power BI. Anche gli articoli seguenti possono risultare utili.

* [Esercitazione: Creare un modello di Machine Learning in Power BI (anteprima)](service-tutorial-build-machine-learning-model.md)
* [Esercitazione: Uso di Servizi cognitivi in Power BI](service-tutorial-use-cognitive-services.md)
* [Esercitazione: Richiamare un modello di Machine Learning Studio in Power BI (anteprima)](service-tutorial-invoke-machine-learning-model.md)
* [Servizi cognitivi in Power BI (anteprima)](service-cognitive-services.md)
* [Integrazione di Azure Machine Learning in Power BI (anteprima)](service-machine-learning-integration.md)

Per altre informazioni sui flussi di dati, è possibile leggere questi articoli:
* [Creare e usare flussi di dati in Power BI](service-dataflows-create-use.md)
* [Uso delle entità calcolate in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso di flussi di dati con origini dati locali](service-dataflows-on-premises-gateways.md)
* [Risorse per sviluppatori per i flussi di dati Power BI](service-dataflows-developer-resources.md)
* [Integrazione di flussi di dati e Azure Data Lake (anteprima)](service-dataflows-azure-data-lake-integration.md)


