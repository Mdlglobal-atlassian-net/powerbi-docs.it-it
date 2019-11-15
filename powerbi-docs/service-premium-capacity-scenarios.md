---
title: Scenari di capacità di Power BI Premium
description: Descrive i comuni scenari di capacità di Power BI Premium.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 3190645044c930c1c63fd7c199883d784723d6f0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881250"
---
# <a name="premium-capacity-scenarios"></a>Scenari delle capacità Premium

Questo articolo descrive scenari reali in cui sono state implementate capacità di Power BI Premium. Vengono descritti i problemi e le sfide comuni, anche con informazioni su come identificarli e risolverli:

- [Mantenere aggiornati i set di dati](#keeping-datasets-up-to-date)
- [Identificare set di dati lenti a rispondere](#identifying-slow-responding-datasets)
- [Identificare le cause per la sporadica lentezza nella risposta dei set di dati](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinare se la memoria disponibile è sufficiente](#determining-whether-there-is-enough-memory)
- [Determinare se la quantità di CPU disponibile è sufficiente](#determining-whether-there-is-enough-cpu)

I passaggi, insieme agli esempi di grafici e tabelle, derivano dall'**app Power BI Premium Capacity Metrics** a cui avrà accesso un amministratore Power BI.

## <a name="keeping-datasets-up-to-date"></a>Mantenere aggiornati i set di dati

In questo scenario è stata attivata un'indagine in seguito a un reclamo degli utenti, che segnalano che a volte i dati sembrano essere obsoleti o non aggiornati.

Nell'app l'amministratore interagisce con l'oggetto visivo **Refreshes** (Aggiornamenti), ordinando i set di dati in base alla statistica **Max Wait Time** (Tempo massimo di attesa) in senso decrescente. Questo oggetto visivo rivela i set di dati con i tempi di attesa più lunghi, raggruppati per nome dell'area di lavoro.

![Aggiornamenti dei set di dati ordinati per tempo massimo di attesa in senso decrescente, raggruppati per area di lavoro](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Nell'oggetto visivo **Hourly Average Refresh Wait Times** (Tempi medi di attesa di aggiornamenti su base oraria) si nota che i tempi di attesa degli aggiornamenti raggiungono sempre il picco intorno alle ore 16:00 ogni giorno.

![Il picco dei tempi di attesa degli aggiornamenti regolarmente alle 16:00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Per questi risultati sono disponibili diverse spiegazioni possibili:

- Si potrebbe verificare un numero eccessivo di tentativi di aggiornamento contemporanei, superando i limiti definiti dal nodo di capacità. In questo caso, si verificano sei aggiornamenti simultanei in P1 con allocazione di memoria predefinita.

- I set di dati da aggiornare possono avere dimensioni eccessive per la memoria disponibile (richiedono almeno il doppio della memoria necessaria per un aggiornamento completo).
- Una logica di Power Query inefficiente può causare un picco di utilizzo della memoria durante l'aggiornamento dei set di dati. Con un uso intensivo della capacità, questo picco può a volte raggiungere il limite fisico, per cui l'aggiornamento non riesce e possono verificarsi problemi anche in altre operazioni di visualizzazione dei report che usano la capacità.
- I set di dati sottoposti a query frequenti e che devono rimanere in memoria possono influire negativamente sull'aggiornamento di altri set di dati a causa della memoria limitata disponibile.

Per l'indagine, l'amministratore di Power BI può verificare se sussistono queste condizioni:

- Memoria insufficiente al momento degli aggiornamenti dei dati quando la quantità di memoria disponibile è meno del doppio delle dimensioni del set di dati da aggiornare.
- I set di dati non vengono aggiornati e non si trovano in memoria prima dell'aggiornamento, ma sono stati avviati per mostrare il traffico interattivo durante i periodi intensivi di aggiornamenti. Per vedere quali set di dati vengono caricati in memoria in un dato momento, l'amministratore Power BI può esaminare l'area dei set di dati nella scheda **Datasets** (Set di dati) dell'app. L'amministratore può quindi applicare un filtro incrociato a un determinato momento facendo clic su una delle barre in **Hourly Loaded Dataset Counts** (Conteggi orari dei set di dati caricati). Un picco locale, illustrato nell'immagine seguente, indica un'ora in cui sono stati caricati in memoria più set di dati, il che potrebbe ritardare l'avvio degli aggiornamenti pianificati.
- Si verifica un aumento di rimozioni di set di dati nel momento pianificato per l'avvio degli aggiornamenti dei dati. Le rimozioni possono indicare una pressione elevata sulla memoria causata dalla gestione di un numero eccessivo di report interattivi diversi prima del momento dell'aggiornamento. L'oggetto visivo **Hourly Dataset Evictions and Memory Consumption** (Rimozioni di set di dati e utilizzo della memoria su base oraria) indica chiaramente i picchi nelle rimozioni.

L'immagine seguente mostra un picco locale nei set di dati caricati, che suggerisce l'avvio degli aggiornamenti ritardato dalle query interattive. Se si seleziona un periodo di tempo nell'oggetto visivo **Hourly Loaded Dataset Counts** (Conteggio orari dei set di dati caricati), verrà applicato un filtro incrociato all'oggetto visivo **Dataset Sizes** (Dimensioni set di dati).

![Un picco locale nei set di dati caricati suggerisce un avvio degli aggiornamenti ritardato dalle query interattive](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

L'amministratore di Power BI può provare a risolvere il problema adottando misure che assicurino la disponibilità di memoria sufficiente per l'avvio degli aggiornamenti dei dati. Può ad esempio:

- Contattare i proprietari dei set di dati e chiedere di scaglionare e distanziare le pianificazioni degli aggiornamenti dei dati.
- Ridurre il carico di query sui set di dati rimuovendo dashboard o riquadri di dashboard non necessari, in particolare quelli che applicano la sicurezza a livello di riga.
- Velocizzare gli aggiornamenti dei dati ottimizzando la logica di Power Query. Migliorare la modellazione di colonne o tabelle calcolate. Ridurre le dimensioni dei set di dati o configurare set di dati più grandi per eseguire aggiornamenti incrementali dei dati.

## <a name="identifying-slow-responding-datasets"></a>Identificare set di dati lenti a rispondere

In questo scenario viene avviata un'indagine in seguito a un reclamo degli utenti che segnalano tempi troppo lunghi per l'apertura dei report, che a volte si bloccano.

Nell'app l'amministratore di Power BI può usare l'oggetto visivo **Query Durations** (Durate query) per identificare i set di dati con le prestazioni peggiori ordinandoli in senso decrescente in base a **Average Duration** (Durata media). Questo oggetto visivo mostra anche i conteggi delle query sui set di dati, permettendo di verificare la frequenza di tali query.

![Set di dati con le prestazioni peggiori](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

L'amministratore può fare riferimento all'oggetto visivo **Query Duration Distribution** (Distribuzione durate query), che mostra la distribuzione generale delle prestazioni delle query in bucket (< = 30 ms, 0-100 ms) per il periodo di tempo filtrato. In generale, le query che richiedono al massimo un secondo vengono considerate reattive dalla maggior parte degli utenti, mentre quelle che richiedono più tempo tendono a creare una percezione di prestazioni insufficienti.

L'oggetto visivo **Hourly Query Duration Distribution** (Distribuzione oraria durate query) consente all'amministratore di Power BI di identificare i periodi di un'ora in cui le prestazioni della capacità potrebbero essere percepite come insufficienti. I segmenti delle barre più grandi che rappresentano le durate delle query superiori a un secondo aumentano il rischio che gli utenti percepiranno prestazioni insufficienti.

L'oggetto visivo è interattivo e, quando si seleziona un segmento della barra, l'oggetto visivo della tabella **Query Durations** (Durate query) corrispondente nella pagina dei report viene sottoposto a filtro incrociato per mostrare i set di dati che rappresenta. L'applicazione di questo filtro incrociato consente all'amministratore di Power BI di identificare facilmente quali set di dati rispondono lentamente.

L'immagine seguente mostra un oggetto visivo filtrato in base a **Hourly Query Duration Distributions** (Distribuzioni orarie durate query), evidenziando i set di dati con le prestazioni peggiori in bucket di un'ora. 

![L'oggetto visivo Hourly Query Duration Distributions filtrato mostra i set di dati con le prestazioni peggiori](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Una volta identificato il set di dati con prestazioni insufficienti in uno specifico intervallo di un'ora, l'amministratore di Power BI può verificare se il problema è dovuto a un sovraccarico della capacità oppure a una progettazione inefficiente di set di dati o report. Può fare riferimento all'oggetto visivo **Query Wait Times** (Tempi di attesa query) e ordinare i set di dati in base al tempo di attesa medio delle query in senso decrescente. Se un'alta percentuale di query è in attesa, è probabile che la causa sia da attribuire a una domanda elevata per il set di dati. Se il tempo medio di attesa delle query è sostanziale (> 100 ms), potrebbe essere utile esaminare il set di dati e il report per verificare se è possibile apportare ottimizzazioni, ad esempio un numero inferiore di oggetti visivi in determinate pagine del report o l'ottimizzazione di un'espressione DAX.

![L'oggetto visivo Query Wait Times aiuta a identificare i set di dati con prestazioni insufficienti](media/service-premium-capacity-scenarios/query-wait-times.png)

I tempi di attesa delle query possono aumentare nei set di dati per diversi motivi:

- Un livello subottimale nella progettazione di modelli, nelle espressioni delle misure o anche nella progettazione di report, tutte circostanze che possono contribuire all'esecuzione prolungata di query che consumano livelli elevati di CPU. In questo caso le nuove query devono aspettare finché non diventano disponibili thread della CPU e può crearsi un effetto convoglio (paragonabile a un ingorgo stradale), in genere durante gli orari lavorativi di punta. La pagina **Query Waits** (Attese query) sarà la risorsa principale per determinare se i set di dati hanno tempi di attesa delle query elevati.
- Un numero elevato di utenti simultanei della capacità (da centinaia a migliaia) che utilizzano lo stesso report o set di dati. Anche i set di dati ben progettati possono avere prestazioni insufficienti oltre una soglia di concorrenza. Questa situazione è in genere indicata da un singolo set di dati che mostra un valore sensibilmente più alto per i conteggi delle query rispetto ad altri set di dati, ad esempio 300.000 query per un set di dati rispetto a meno di 30.000 per tutti gli altri. A un certo punto, le attese delle query per questo set di dati inizieranno a essere sfalsate, come si può vedere nell'oggetto visivo **Query Durations** (Durate query).
- Le query vengono eseguite simultaneamente su molti set di dati disparati, generando una situazione di thrashing perché i set di dati eseguono cicli frequenti in ingresso e in uscita dalla memoria. Il risultato è che gli utenti riscontrano prestazioni lente quando il set di dati viene caricato in memoria. Per verifica, l'amministratore di Power BI può fare riferimento all'oggetto visivo **Hourly Dataset Evictions and Memory Consumption** (Rimozioni di set di dati e utilizzo della memoria su base oraria), che potrebbe indicare la rimozione ripetuta di un numero elevato di set di dati caricati in memoria.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificare le cause per la sporadica lentezza nella risposta dei set di dati

In questo scenario viene avviata un'indagine quando gli utenti segnalano che a volte gli oggetti visivi dei report sono lenti o potrebbero smettere di rispondere, mentre altre volte sono accettabilmente reattivi.

All'interno dell'app viene usata la sezione **Query Durations** (Durate query) per trovare il set di dati che causa il problema nel modo seguente:

- Nell'oggetto visivo **Query Durations** (Durate query) l'amministratore filtra il set di dati per set di dati (a partire da quelli su cui vengono eseguite più query) ed esamina le barre sottoposte a filtro incrociato nell'oggetto visivo **Hourly Query Distributions** (Distribuzioni orarie query).
- Quando una singola barra di un'ora presenta modifiche significative nel rapporto tra tutti i gruppi di durate delle query e altre barre di un'ora per lo stesso set di dati (ad esempio, i rapporti tra i colori cambiano drasticamente), significa che questo set di dati ha registrato una variazione sporadica nelle prestazioni.
- Le barre di un'ora che mostrano una parte irregolare di query con prestazioni insufficienti, indicano un intervallo di tempo in cui il set di dati subisce l'effetto "noisy neighbor" per cui le attività di altri set di dati monopolizzano le risorse.

L'immagine seguente mostra un'ora il 30 gennaio, in cui si è verificata una riduzione significativa delle prestazioni di un set di dati, indicata dalle dimensioni del bucket di durata dell'esecuzione "(3,10 s]". Facendo clic su questa barra di un'ora vengono visualizzati tutti i set di dati caricati in memoria durante tale periodo di tempo, mostrando i possibili set di dati che causano l'effetto "noisy neighbor".

![Barra che mostra le prestazioni peggiori di un gran parte di set di dati](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Una volta identificato l'intervallo di tempo problematico, ad esempio il 30 gennaio nell'immagine precedente, l'amministratore di Power BI può rimuovere tutti i filtri dei set di dati e quindi applicare solo quello in base a tale intervallo, per determinare quali set di dati vengono attivamente sottoposti a query in questo periodo. Il set di dati responsabile dell'effetto "noisy neighbor" è in genere quello su cui vengono eseguite più query o quello con la durata media delle query più lunga.

Per risolvere questo problema si potrebbe distribuire i set di dati responsabili in diverse aree di lavoro con diverse capacità Premium oppure con una capacità condivisa se le dimensioni del set di dati, i requisiti di utilizzo e i modelli di aggiornamento dei dati sono supportati.

Potrebbe anche essere vero il contrario. L'amministratore di Power BI potrebbe identificare gli intervalli in cui le prestazioni delle query sui set di dati migliorano drasticamente e quindi cercare cosa è scomparso. Se in quel punto mancano determinate informazioni, può essere possibile individuare la causa del problema.

## <a name="determining-whether-there-is-enough-memory"></a>Determinare se la memoria disponibile è sufficiente

Per determinare se la memoria disponibile è sufficiente per completare i carichi di lavoro della capacità, l'amministratore di Power BI può fare riferimento all'oggetto visivo **Consumed Memory Percentages** (Percentuali di memoria consumate) nella scheda **Datasets** (Set di dati) dell'app. **All** (Tutta) rappresenta il totale della memoria consumata dai set di dati caricati in memoria, indipendentemente dal fatto che siano attivamente sottoposti a query o elaborati. **Active** (Attiva) rappresenta la memoria consumata dai set di dati attivamente elaborati.

In una situazione di integrità della capacità, l'oggetto visivo sarà simile al seguente, ossia con un divario tra la memoria totale e quella attiva:

![Una situazione di integrità della capacità mostra un divario tra la memoria totale e quella attiva](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Se si verifica una pressione della memoria sulla capacità, lo stesso oggetto visivo mostrerà una convergenza tra la memoria attiva e quella totale, a indicare che non è possibile caricare altri set di dati in memoria. In questo caso, l'amministratore di Power BI può fare clic su **Capacity Restart** (Riavvio capacità) nell'area **Advanced Options** (Opzioni avanzate) delle impostazioni della capacità nel portale di amministrazione. Con il riavvio della capacità, tutti i set di dati vengono scaricati dalla memoria e possono essere ricaricati se richiesto dalle query o dagli aggiornamenti dei dati.

![Convergenza tra memoria attiva e totale](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determinare se la quantità di CPU disponibile è sufficiente

In generale, l'utilizzo medio della CPU della capacità dovrebbe rimanere al di sotto dell'80%. Se questo valore viene superato, significa che la capacità si sta avvicinando alla saturazione della CPU.

Gli effetti della saturazione della CPU sono espressi da operazioni che richiedono più tempo del necessario, perché la capacità esegue molti cambi di contesto della CPU nel tentativo di elaborare tutte le operazioni. In una capacità Premium con un numero elevato di query simultanee, questo scenario è indicato dai tempi di attesa delle query elevati, con conseguenti tempi di risposta più lenti del solito. L'amministratore di Power BI può identificare facilmente se la CPU è saturata visualizzando l'oggetto visivo **Hourly Query Wait Time Distributions** (Distribuzioni orarie dei tempi di attesa delle query). Picchi periodici delle attese delle query indicano una potenziale saturazione della CPU.

![Picchi periodici delle attese delle query indicano una potenziale saturazione della CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Un modello simile può talvolta essere rilevato nelle operazioni in background se contribuiscono alla saturazione della CPU. L'amministratore di Power BI può cercare un picco periodico nei tempi di aggiornamento per un set di dati specifico, che può indicare una saturazione della CPU in quel momento, probabilmente dovuto ad altri aggiornamenti in corso e/o a query interattive. In questo caso, la visualizzazione **System** (Sistema) dell'app potrebbe non necessariamente rivelare che la CPU è al 100%. La visualizzazione **System** (Sistema) mostra le medie orarie, ma la CPU può diventare satura per diversi minuti di operazioni intensive, come indicato da picchi nei tempi di attesa.

L'effetto della saturazione della CPU presenta altri aspetti. Anche se il numero di query in attesa è importante, il tempo di attesa delle query si verificherà sempre in qualche misura senza causare un calo percepibile delle prestazioni. Alcuni set di dati (con un tempo medio di attesa delle query più lungo, a indicare complessità o dimensioni) sono più soggetti agli effetti della saturazione della CPU rispetto ad altri. Per identificare facilmente questi set di dati, l'amministratore di Power BI può verificare se la composizione dei colori delle barre è cambiata nell'oggetto visivo **Hourly Wait Time Distribution** (Distribuzione oraria dei tempi di attesa). Dopo aver individuato una barra anomala, può cercare i set di dati con attese di query durante quel periodo e anche confrontare il tempo di attesa medio con la durata media delle query. Quando queste due metriche sono dello stesso ordine di grandezza e il carico di lavoro delle query per il set di dati non è trascurabile, è probabile che la CPU insufficiente influisca sul set di dati.

Questo effetto può essere particolarmente evidente quando un set di dati viene utilizzato in brevi picchi di query ad alta frequenza da parte di più utenti (ad esempio, in una sessione di training), causando una saturazione della CPU durante ogni picco. In questo caso, è possibile che si verifichino tempi di attesa delle query significativi in questo set di dati, oltre a effetti negativi su altri set di dati nella capacità (effetto "noisy neighbor").

In alcuni casi, gli amministratori di Power BI possono chiedere ai proprietari di set di dati di creare un carico di lavoro di query meno volatile creando un dashboard (che esegue periodicamente le query con qualsiasi aggiornamento di set di dati per i riquadri memorizzati nella cache) invece di un report. Ciò consente di evitare picchi quando il dashboard viene caricato. Questa soluzione potrebbe non essere sempre possibile per determinati requisiti aziendali, ma può essere un modo efficace per evitare la saturazione della CPU, senza apportare modifiche al set di dati.

## <a name="acknowledgements"></a>Riconoscimenti

Questo articolo è stato scritto da Peter Myers, Data Platform MVP ed esperto indipendente di business intelligence con [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Monitorare le capacità Premium con l'app](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Monitorare le capacità nel portale di amministrazione](service-admin-premium-monitor-portal.md)   

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

||||||