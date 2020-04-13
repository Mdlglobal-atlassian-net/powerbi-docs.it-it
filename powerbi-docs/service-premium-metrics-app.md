---
title: App Power BI Premium Metrics
description: Informazioni su come usare l'app Power BI Premium Metrics per gestire e risolvere i problemi relativi alla capacità Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/06/2020
LocalizationGroup: Premium
ms.openlocfilehash: c15576ac6ab9b20a3492341c05d2f9d8eb42e107
ms.sourcegitcommit: 2b93c1cc29aaf199ab7441a04c8e5ae49ffca5d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2020
ms.locfileid: "80813053"
---
# <a name="power-bi-premium-metrics-app"></a>App Power BI Premium Metrics

È possibile usare l'**app Power BI Premium Metrics** per gestire l'integrità e la capacità della sottoscrizione Power BI Premium. Gli amministratori usano **Capacity Health Center** (Centro integrità capacità) nell'app per visualizzare e interagire con gli indicatori che monitorano l'integrità della capacità Premium. L'app Metrics è costituita dalla pagina di destinazione, denominata **Capacity Health Center** (Centro integrità capacità), e dalle informazioni dettagliate su tre metriche importanti:

* Memoria attiva
* Attese query
* Attese aggiornamenti

![App Power BI Premium Metrics](media/service-premium-metrics-app/premium-metrics-app-00.png)

Le sezioni seguenti descrivono in dettaglio la pagina di destinazione e le tre pagine di report delle metriche. 

> [!IMPORTANT]
> Se per la capacità Power BI Premium si riscontra un utilizzo elevato delle risorse, con conseguenti problemi di prestazioni o affidabilità, è possibile ricevere messaggi di posta elettronica di notifica per identificare e risolvere il problema. Per altre informazioni, vedere [Notifiche per capacità e affidabilità](service-interruption-notifications.md#capacity-and-reliability-notifications).

## <a name="premium-capacity-health-center"></a>Capacity health center (Centro integrità capacità) per la capacità Premium

Quando si apre l'app **Power BI Premium Metrics** viene visualizzata la pagina **Capacity health center** (Centro integrità capacità) che offre una panoramica dell'integrità della capacità Power BI Premium.

![Capacity health center (Centro integrità capacità) nell'app Premium Metrics](media/service-premium-metrics-app/premium-metrics-app-01.png)

Dalla pagina di destinazione è possibile selezionare la capacità Power BI Premium che si vuole visualizzare, nel caso in cui l'organizzazione abbia più sottoscrizioni Premium. Per visualizzare una capacità Premium, selezionare l'elenco a discesa nella parte superiore della pagina denominata **Select a capacity to see its metrics** (Selezionare una capacità per visualizzarne le metriche).

I tre indicatori KPI mostrano l'integrità corrente della capacità Premium selezionata, in base alle impostazioni applicate a ognuno dei tre indicatori KPI. 

Per visualizzare le specifiche relative a ogni indicatore KPI, selezionare il pulsante **Explore** (Esplora) nella parte inferiore dell'oggetto visivo di ogni indicatore KPI per visualizzare la relativa pagina dei dettagli. Nelle sezioni seguenti sono descritti gli indicatori KPI e i dettagli visualizzati dalla pagina corrispondente.

## <a name="the-active-memory-metric"></a>Metrica della memoria attiva

Poiché la metrica della **memoria attiva** è inclusa nella categoria di *pianificazione della capacità* che rappresenta un indicatore dell'integrità utile per valutare l'utilizzo delle risorse della capacità, è possibile modificare la capacità in base alle esigenze per pianificare la scalabilità della capacità. 

![KPI della memoria attiva](media/service-premium-metrics-app/premium-metrics-app-02.png)

La **memoria attiva** è la memoria usata per elaborare i set di dati attualmente in uso e che non verranno eliminati quando viene richiesta memoria. La metrica della memoria attiva indica se la capacità è in grado di gestire un carico aggiuntivo o, prossimo o superiore alla capacità, il carico corrente della capacità. La memoria attiva attualmente utilizzata indica che è disponibile una quantità minore di memoria per supportare aggiornamenti e query aggiuntivi. 

L'indicatore KPI della **memoria attiva** misura il numero di volte in cui la memoria attiva della capacità ha superato per 50 volte la soglia del 70% (il marcatore è impostato sul 30% degli ultimi sette giorni) che indica che la capacità sta per raggiungere un punto in cui gli utenti potrebbero iniziare a rilevare problemi di prestazioni con le query.

L'oggetto visivo del misuratore illustrato in questa sezione indica che negli ultimi sette giorni dall'ultima volta in cui il report è stato aggiornato la capacità ha superato la soglia del 70% quattro volte, suddivisa per bucket orari. Il valore massimo del misuratore, 168, rappresenta gli ultimi sette giorni, in ore.

Per informazioni dettagliate sull'indicatore KPI della memoria attiva, fare clic sul pulsante **Explore** (Esplora) per visualizzare una pagina del report in cui sono disponibili visualizzazioni specifiche delle metriche dettagliate, oltre a una guida alla risoluzione dei problemi visualizzata nella colonna di destra della pagina. 

Sono illustrati due scenari che è possibile visualizzare nella pagina del report selezionando **Scenario 1** o **Scenario 2** nella pagina. 

![Pagina dei dettagli della memoria attiva](media/service-premium-metrics-app/premium-metrics-app-03.png)

Le guide alla risoluzione dei problemi, associate a ogni scenario, offrono le descrizioni delle metriche in modo che sia possibile comprendere meglio lo stato della capacità e individuare le azioni possibili per attenuare eventuali problemi. 

Questi due scenari sono descritti nelle sezioni seguenti.

### <a name="scenario-one---current-load-is-too-high"></a>Scenario 1: il carico corrente è troppo elevato 

Per determinare se è disponibile memoria sufficiente per la capacità per completare i carichi di lavoro, vedere il primo oggetto visivo nella pagina, **A: Consumed Memory Percentages** (Percentuali memoria utilizzata), che visualizza la memoria utilizzata dai set di dati attualmente in elaborazione e che non possono essere eliminati.

La soglia di allarme, ovvero la linea rossa tratteggiata, contrassegna gli eventi imprevisti di consumo di memoria pari al 90%.

La soglia di avviso, ovvero la linea gialla tratteggiata, contrassegna gli eventi imprevisti di consumo di memoria pari al 70%. 

La linea nera tratteggiata indica la linea di tendenza di utilizzo della memoria, in base all'utilizzo della memoria della capacità corrente nel corso della sequenza temporale del grafico.

Le occorrenze di memoria attiva elevate che superano la soglia di allarme (linea rossa tratteggiata) e la linea di tendenza della memoria (linea nera tratteggiata) indicano una condizione di utilizzo elevato della capacità di memoria che potrebbe impedire il caricamento in memoria di altri set di dati nel periodo specifico. 

Quando vengono visualizzati questi casi, è opportuno esaminare attentamente gli altri grafici della pagina per determinare i motivi per cui viene utilizzata di frequente una quantità di memoria così elevata e come bilanciare il carico o ottimizzarlo oppure, se necessario, aumentare la capacità. 

Il secondo oggetto visivo nella pagina, **B: Hourly loaded active datasets** (Set di dati attivi caricati ogni ora), visualizza i conteggi del numero massimo di set di dati caricati in memoria, in bucket orari. 

Il terzo oggetto visivo, **C: Why datasets are in memory** (Perché i set di dati sono in memoria), è una tabella che visualizza il set di dati in base al nome dell'area di lavoro, al nome del set di dati, alle dimensioni non compresse del set di dati in memoria, e descrive il motivo per cui viene caricato in memoria (ad esempio, un aggiornamento o una query o entrambi).

#### <a name="diagnosing-scenario-one"></a>Diagnosi dello Scenario 1

Un utilizzo della memoria attiva elevato costante può comportare l'eliminazione forzata dei set di dati utilizzati attivamente o impedire il caricamento di nuovi set di dati. I passaggi seguenti possono contribuire alla diagnosi dei problemi

1. Osservare il grafico *A: Consumed memory percentages* (Percentuali memoria utilizzata)

    **a.** Se il Grafico A mostra che la soglia di allarme (90%) viene superata più volte e/o per ore consecutive, significa che la memoria della capacità è insufficiente troppo di frequente. Nel grafico seguente è possibile osservare che la soglia di avviso (70%) è stata superata quattro volte.

    ![Grafico A, percentuali di memoria utilizzata](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** Il grafico denominato *B: Hourly loaded active datasets* (Set di dati attivi caricati ogni ora) mostra il numero massimo di set di dati univoci caricati in memoria in bucket orari. Se si seleziona una barra nell'oggetto visivo, viene applicato un filtro incrociato sui motivi per cui i set di dati si trovano in un oggetto visivo in memoria.  

    ![Grafico B, memoria utilizzata per ora](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** Per visualizzare un elenco dei set di dati caricati in memoria, vedere la tabella **Why datasets are in memory** (Perché i set di dati sono in memoria). Ordinare per *Dataset Size (MB)* (Dimensioni set di dati (MB)) per evidenziare i set di dati che occupano la maggior parte della memoria. Le operazioni della capacità sono classificate come *interattive* o *in background*. Le operazioni interattive includono il rendering delle richieste e la risposta alle interazioni dell'utente (applicazione di filtri, query su Domande e risposte e così via). Le query totali e gli aggiornamenti totali indicano se sono presenti operazioni interattive (query) pesanti o in background (aggiornamenti) eseguite sul set di dati. È importante sapere che le operazioni interattive hanno sempre priorità sulle operazioni in background per garantire la miglior esperienza utente. Se le risorse sono insufficienti, le operazioni in background vengono aggiunte a una coda per essere elaborate quando si liberano le risorse. Le operazioni in background, ad esempio gli aggiornamenti dei set di dati e le funzioni di intelligenza artificiale, possono essere arrestate durante l'elaborazione dal servizio Power BI e aggiunte a una coda.
    
    ![Tabella C, elenco dei set di dati](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Rimedi per lo Scenario 1

Per risolvere i problemi associati allo Scenario 1, è possibile eseguire le operazioni seguenti:

1. **Aumentare la capacità**: l'aumento della capacità allo SKU successivo rende disponibile il doppio della quantità di memoria dello SKU corrente, risolvendo tutte le condizioni correnti di utilizzo elevato della memoria della capacità.

2. **Spostare i set di dati in un'altra capacità**: se è presente un'altra capacità con una maggiore quantità di memoria disponibile, è possibile spostare le aree di lavoro che contengono i set di dati di maggiori dimensioni nella capacità.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Scenario 2: il carico futuro supererà i limiti

Per determinare se è disponibile memoria sufficiente per consentire alla capacità di completare i carichi di lavoro, vedere l'oggetto visivo **A: Consumed Memory Percentages** (Percentuali memoria utilizzata) nella parte superiore della pagina che indica la memoria utilizzata dai set di dati attualmente in elaborazione che non possono essere eliminati. La linea nera tratteggiata evidenzia le tendenze. In una capacità in cui si verifica una condizione di utilizzo elevato della memoria, lo stesso oggetto visivo mostra chiaramente la linea di tendenza della memoria (linea nera tratteggiata) in aumento che indica che è possibile che venga impedito il caricamento di ulteriori set di dati in memoria nel periodo specifico. La linea di tendenza, la linea nera tratteggiata, mostra la tendenza dell'aumento, in base ai sette giorni di dati. 

![Pagina dei dettagli della memoria attiva](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosi dello Scenario 2

Per eseguire la diagnosi dello Scenario 2, determinare se la linea di tendenza mostra una tendenza in aumento verso la soglia di avviso o allarme. 

1. Osservare il **Grafico A:**

    ![Grafico della memoria utilizzata](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Se il grafico mostra un'inclinazione verso l'alto, significa che l'utilizzo della memoria è aumentato negli ultimi sette giorni.

    **b.** Considerare la crescita corrente e prevedere quando la linea di tendenza supererà la soglia di avviso (linea gialla tratteggiata).

    **c.** Controllare la linea di tendenza almeno ogni due giorni per verificare se la tendenza continua.

#### <a name="remedies-for-scenario-two"></a>Rimedi per lo Scenario 2

Per risolvere i problemi associati allo Scenario 2, è possibile eseguire le operazioni seguenti:

1. **Aumentare la capacità**: l'aumento della capacità allo SKU successivo rende disponibile il doppio della quantità di memoria dello SKU corrente, risolvendo tutte le condizioni correnti di utilizzo elevato della memoria della capacità.

2. **Spostare i set di dati in un'altra capacità**: se è presente un'altra capacità con una maggiore quantità di memoria disponibile, è possibile spostare le aree di lavoro che contengono i set di dati di maggiori dimensioni nella capacità.


## <a name="the-query-waits-metric"></a>Metrica delle attese delle query

La categoria **Queries** (Query) indica se è possibile che gli utenti rilevino oggetti visivi dei report con tempi di risposta lunghi o che potrebbero non rispondere. **Query waits** (Attese query) è il tempo richiesto dalla query per essere avviata a partire dal momento dell'attivazione. L'indicatore KPI misura se il 25% o più delle query della capacità selezionata richiede un'attesa di 100 millisecondi o più per l'esecuzione. Le attese delle query si verificano quando la CPU disponibile non è sufficiente per l'esecuzione di tutte le query in sospeso. 

![Misuratore delle attese delle query](media/service-premium-metrics-app/premium-metrics-app-09.png)

Il misuratore in questo oggetto visivo indica che negli ultimi sette giorni dall'ultimo aggiornamento del report, il 17,32% delle query ha un'attesa superiore a 100 millisecondi. 

Per informazioni dettagliate sull'indicatore KPI delle attese delle query, fare clic sul pulsante **Explore** (Esplora) per visualizzare una pagina del report con la visualizzazione delle metriche rilevanti e una guida alla risoluzione dei problemi nella colonna di destra della pagina. La guida alla risoluzione dei problemi presenta due scenari, ognuno dei quali offre descrizioni dettagliate della metrica, lo stato della capacità e le operazioni che è possibile eseguire per ridurre il problema.

Nelle sezioni seguenti sono descritti in sequenza i due scenari delle attese delle query.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Scenario 1: utilizzo della CPU per query a esecuzione prolungata

Nello Scenario 1 le query a esecuzione prolungata utilizzano una quantità eccessiva di CPU. 

È possibile verificare se le prestazioni scarse del report sono dovute a una capacità in sovraccarico o a un set di dati o un report progettato in modo non corretto. Esistono diversi motivi per cui il completamento dell'esecuzione di una query può richiedere un periodo di tempo prolungato, ovvero superiore a 10 secondi. Le dimensioni e la complessità del set di dati, oltre alla complessità della query, sono solo alcuni esempi che possono causare l'esecuzione prolungata di una query. 

Nella pagina del report vengono visualizzati gli oggetti visivi seguenti: 

* La tabella nella parte superiore denominata **A: High wait times** (Tempi di attesa elevati) elenca i set di dati con query in attesa. 
* **B: Hourly high wait time distributions** (Distribuzioni con tempi di attesa orari elevati) mostra la distribuzione dei tempi di attesa elevati. 
* Il grafico denominato **C: Hourly long query counts** (Numero query a esecuzione prolungata all'ora) visualizza il numero di query a esecuzione prolungata eseguite, suddivise in bucket orari.
* L'ultimo oggetto visivo, la tabella **D: Long running queries** (Query a esecuzione prolungata), elenca le query a esecuzione prolungata e il relativo stato.

![Pagina dei dettagli delle attese delle query](media/service-premium-metrics-app/premium-metrics-app-10.png)

Per diagnosticare e risolvere i problemi dei tempi di attesa delle query, eseguire le operazioni descritte di seguito.

#### <a name="diagnosing-scenario-one"></a>Diagnosi dello Scenario 1

È possibile innanzitutto determinar se le query a esecuzione prolungata si verificano con le query in attesa. 

![Tabella dei tempi di attesa elevati](media/service-premium-metrics-app/premium-metrics-app-11.png)

Osservare il **Grafico B** che mostra il numero di query con tempi di attesa superiori a 100 ms. Selezionare una delle colonne che mostra un numero di attese elevato.

![Distribuzione dei tempi di attesa elevati](media/service-premium-metrics-app/premium-metrics-app-12.png)

Quando si fa clic su una colonna con tempi di attesa elevati, viene applicato un filtro al **Grafico C** per visualizzare il numero di query a esecuzione prolungata eseguite nel periodo di tempo specifico, mostrato nell'immagine seguente:

![Numero di query a esecuzione prolungata all'ora](media/service-premium-metrics-app/premium-metrics-app-13.png)

Viene anche applicato un filtro al **Grafico D** per visualizzare le query a esecuzione prolungata durante il periodo di tempo selezionato.

![Query a esecuzione prolungata](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Rimedi per lo Scenario 1

Per risolvere i problemi dello Scenario 1, è possibile eseguire le operazioni seguenti:

1. **Eseguire PerfAnalyzer per ottimizzare i report e i set di dati**: l'analizzatore di prestazioni per i report mostra l'effetto di ogni interazione in una pagina, incluso il tempo necessario per l'aggiornamento di ogni oggetto visivo e dove viene impiegato il tempo.

2. **Aumentare la capacità**: l'aumento della capacità allo SKU successivo renderà disponibile il doppio della quantità di CPU, limitando in questo modo le condizioni di utilizzo elevato della CPU che potrebbero causare un'esecuzione prolungata delle query.

3. **Spostare i set di dati in un'altra capacità**: se è presente un'altra capacità con una maggiore quantità di CPU, è possibile spostare le aree di lavoro che contengono set di dati con query in attesa nell'altra capacità.

### <a name="scenario-two---too-many-queries"></a>Scenario 2: numero di query eccessivo

Nello scenario 2 è in esecuzione un numero di query eccessivo.

Quando il numero di query da eseguire supera i limiti della capacità, le query vengono inserite in una coda fino a quando le risorse non sono disponibili per eseguirle. Se la coda cresce eccessivamente, le query in coda possono richiedere un'attesa superiore ai 100 millisecondi.

![Scenario 2](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnosi dello Scenario 2

Dalla **Tabella A** selezionare un set di dati con una percentuale elevata di tempi di attesa.

![Tabella dei tempi di attesa elevati](media/service-premium-metrics-app/premium-metrics-app-16.png)

Dopo aver selezionato un set di dati con tempi di attesa elevati, viene applicato un filtro al **Grafico B** per visualizzare le distribuzioni dei tempi di attesa per le query eseguite nel set di dati negli ultimi sette giorni. Selezionare quindi una delle colonne del **Grafico B**.

![Grafico di distribuzione dei tempi di attesa elevati all'ora](media/service-premium-metrics-app/premium-metrics-app-17.png)

Viene quindi applicato un filtro al **Grafico C** per visualizzare la lunghezza della coda nell'ora selezionata nel Grafico B.

![Lunghezza oraria della coda delle query](media/service-premium-metrics-app/premium-metrics-app-18.png)

Se la lunghezza della coda supera la soglia di 20, è probabile che le query nel set di dati selezionato vengano ritardate a causa di un numero eccessivo di query eseguite contemporaneamente.

![Tabella delle query in esecuzione](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Rimedi per lo Scenario 2

Per risolvere i problemi associati allo Scenario 2, è possibile eseguire le operazioni seguenti:

1. **Aumentare la capacità**: l'aumento della capacità allo SKU successivo rende disponibile il doppio della quantità di memoria dello SKU corrente, risolvendo tutte le condizioni correnti di utilizzo elevato della memoria della capacità.

2. **Spostare i set di dati in un'altra capacità**: se è presente un'altra capacità con una maggiore quantità di memoria disponibile, è possibile spostare le aree di lavoro che contengono i set di dati di maggiori dimensioni nella capacità.


## <a name="the-refresh-waits-metric"></a>Metrica delle attese degli aggiornamenti

La metrica **Refresh waits** (Attese aggiornamenti) offre informazioni dettagliate su quando gli utenti potrebbero riscontrare dati del report obsoleti o non aggiornati. **Refresh waits** (Attese aggiornamenti) è il tempo di attesa per l'esecuzione di uno specifico aggiornamento dati, dal momento dell'attivazione su richiesta o della pianificazione dell'esecuzione. Questo indicatore KPI misura se il 10% o più delle richieste di aggiornamento in sospeso hanno un'attesa di 10 minuti o superiore. In genere l'attesa si verifica quando la memoria o la CPU disponibile non è sufficiente.

![Misuratore delle attese degli aggiornamenti](media/service-premium-metrics-app/premium-metrics-app-20.png)

Questo misuratore mostra che negli ultimi sette giorni dall'ultimo aggiornamento del report di aggiornamento, il 3,18% degli aggiornamenti è rimasto in attesa per più di 10 minuti. 

Per informazioni dettagliate sull'indicatore KPI **Refresh waits** (Attese aggiornamenti), fare clic sul pulsante **Explore** (Esplora) che visualizza una pagina con le metriche e una guida alla risoluzione dei problemi nella colonna di destra della pagina del report. La guida offre descrizioni dettagliate delle metriche nella pagina e consente di determinare lo stato della capacità e individuare le operazioni possibili per ridurre eventuali problemi.

![Visualizzazione delle metriche delle attese degli aggiornamenti](media/service-premium-metrics-app/premium-metrics-app-21.png)

Sono illustrati due scenari che è possibile visualizzare nella pagina del report selezionando Scenario 1 o Scenario 2 nella pagina. Nelle sezioni seguenti sono descritti in sequenza i due scenari.

### <a name="scenario-one---not-enough-memory"></a>Scenario 1: memoria insufficiente

Nello scenario 1 la memoria disponibile non è sufficiente per caricare il set di dati. Esistono due situazioni che comportano una limitazione dell'aggiornamento in caso di memoria insufficiente:

1. Memoria insufficiente per il caricamento del set di dati.
2. L'aggiornamento è stato annullato a causa di un'operazione con priorità più elevata. 

La priorità per il caricamento dei set di dati è la seguente:

1. Query interattiva
2. Aggiornamento su richiesta
3. Aggiornamento pianificato

Se non è disponibile memoria sufficiente per caricare un set di dati per una query interattiva, gli aggiornamenti pianificati vengono arrestati e i set di dati non vengono caricati finché non è disponibile memoria sufficiente. Se non viene liberata una quantità di memoria sufficiente, gli aggiornamenti su richiesta vengono arrestati e i relativi set di dati non vengono caricati.

#### <a name="diagnosing-scenario-one"></a>Diagnosi dello Scenario 1

Per diagnosticare lo Scenario 1, determinare innanzitutto se la limitazione è dovuta a memoria insufficiente. A tale scopo, eseguire le operazioni seguenti.

1.    Selezionare il set di dati a cui si è interessati dalla **Tabella A** facendo clic su di esso: 

    ![Tabella A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Quando si seleziona un set di dati nella **Tabella A**, viene applicato un filtro al **Grafico B** per visualizzare quando si è verificata l'attesa.

    ![Grafico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. Viene quindi applicato un filtro al **Grafico C** per visualizzare eventuali limitazioni, descritte nel passaggio successivo. 

2. Esaminare i risultati nel **Grafico C** filtrato. Se il grafico mostra che si è verificata una limitazione causata da memoria insufficiente durante l'attesa del set di dati, significa che il set di dati è rimasto in attesa a causa di memoria insufficiente.

    ![Grafico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Infine, esaminare il **Grafico D** che mostra i tipi di aggiornamenti in esecuzione, pianificati e su richiesta. Eventuali aggiornamenti su richiesta nello stesso momento potrebbero essere la causa della limitazione.

    ![Grafico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Rimedi per lo Scenario 1

Per risolvere i problemi associati allo Scenario 1, è possibile eseguire le operazioni seguenti:

1. **Aumentare la capacità**: l'aumento della capacità allo SKU successivo rende disponibile il doppio della quantità di memoria dello SKU corrente, risolvendo tutte le condizioni correnti di utilizzo elevato della memoria e della CPU della capacità.

2. **Spostare i set di dati in un'altra capacità**: se i tempi di attesa sono causati da una condizione di utilizzo elevato della memoria ed è presente un'altra capacità con più memoria disponibile, è possibile spostare le aree di lavoro che contengono i set di dati in attesa nell'altra capacità.

3. **Distribuire gli aggiornamenti pianificati**: la distribuzione degli aggiornamenti pianificati consentirà di evitare l'esecuzione contemporanea di un numero eccessivo di aggiornamenti.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Scenario 2: CPU insufficiente per l'aggiornamento

Nello Scenario 2, la CPU disponibile non è sufficiente per eseguire l'aggiornamento. 

Per le capacità dedicate, Power BI limita il numero di aggiornamenti che possono verificarsi contemporaneamente. Il numero corrisponde al numero di memorie centrali back-end moltiplicato per 1,5. Ad esempio, una capacità dedicata P1 con quattro memorie centrali back-end può eseguire 6 aggiornamenti contemporaneamente. Una volta raggiunto il numero massimo di aggiornamenti simultanei, gli altri aggiornamenti vengono messi in attesa fino al completamento di un aggiornamento in esecuzione.

![Scenario 2 per l'aggiornamento](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnosi dello Scenario 2

Per diagnosticare lo Scenario 2, determinare innanzitutto se la limitazione è dovuta al raggiungimento del numero massimo di aggiornamenti simultanei. A tale scopo, eseguire le operazioni seguenti.

1.    Selezionare il set di dati a cui si è interessati dalla **Tabella A** facendo clic su di esso: 

    ![Tabella A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Quando si seleziona un set di dati nella **Tabella A**, viene applicato un filtro al **Grafico B** per visualizzare quando si è verificata l'attesa.

    ![Grafico B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. Viene quindi applicato un filtro al **Grafico C** per visualizzare eventuali limitazioni, descritte nel passaggio successivo. 

2. Esaminare i risultati nel **Grafico C** filtrato. Se il grafico mostra che è stato raggiunto il *numero massimo di aggiornamenti simultanei* durante l'attesa del set di dati, significa che l'attesa del set di dati è dovuta a CPU insufficiente.

    ![Grafico C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Infine, esaminare il **Grafico D** che mostra i tipi di aggiornamenti in esecuzione, pianificati e su richiesta. Eventuali aggiornamenti su richiesta nello stesso momento potrebbero essere la causa della limitazione.

    ![Grafico D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Rimedi per lo Scenario 2

1. **Aumentare la capacità**: l'aumento della capacità allo SKU successivo rende disponibile il doppio della quantità di memoria e il doppio degli aggiornamenti simultanei dello SKU corrente, risolvendo tutte le condizioni correnti di utilizzo elevato della memoria e della CPU della capacità.

2. **Spostare i set di dati in un'altra capacità**: se i tempi di attesa sono causati dal raggiungimento del numero massimo di aggiornamenti simultanei ed è presente un'altra capacità con la possibilità di eseguire ulteriori aggiornamenti simultanei, è possibile spostare le aree di lavoro che contengono i set di dati in attesa nell'altra capacità.

3. **Distribuire gli aggiornamenti pianificati**: la distribuzione degli aggiornamenti pianificati consentirà di evitare l'esecuzione contemporanea di un numero eccessivo di aggiornamenti.



## <a name="next-steps"></a>Passaggi successivi

* [Che cos'è Power BI Premium?](service-premium-what-is.md)
* [Power BI Premium release notes](service-premium-release-notes.md) (Note sulla versione di Power BI Premium)
* [Microsoft Power BI Premium whitepaper](https://aka.ms/pbipremiumwhitepaper) (White paper su Microsoft Power BI Premium)
* [Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendale di Power BI)
* [Extended Pro Trial activation](service-extended-pro-trial.md) (Attivazione della versione di valutazione Pro estesa)
* [Domande frequenti su Power BI Embedded](developer/embedded/embedded-faq.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)