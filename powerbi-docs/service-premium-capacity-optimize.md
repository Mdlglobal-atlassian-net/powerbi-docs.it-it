---
title: Ottimizzare le capacità di Microsoft Power BI Premium
description: Vengono descritte le strategie di ottimizzazione per le capacità di Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1fb775bd203fc1e0f6342a0d5cd4d9e382b8342a
ms.sourcegitcommit: 9665997274301b228f45aa7250ba557e90164a4d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70750929"
---
# <a name="optimizing-premium-capacities"></a>Ottimizzare le capacità Premium

Quando si verificano problemi di prestazioni della capacità Premium, un primo approccio comune consiste nell'ottimizzare le soluzioni per ripristinare tempi di risposta accettabili. La logica è quella di evitare di acquistare capacità Premium aggiuntiva, a meno che ciò non sia giustificato.

Quando è necessaria capacità Premium aggiuntiva, ci sono due opzioni, descritte in questo articolo:

- Passare a un piano superiore di capacità Premium
- Aggiungere una nuova capacità Premium

Nella parte finale dell'articolo vengono analizzati gli approcci di test e il dimensionamento della capacità Premium.

## <a name="best-practices"></a>Procedure consigliate

Quando si cerca di ottenere il meglio in termini di prestazioni e utilizzo, ci sono alcune procedure consigliate da seguire, tra cui:

- Usare le aree di lavoro per le app invece delle aree di lavoro personali.
- Separare contenuti business critical e BI in modalità self-service (SSBI) in capacità diverse.

  ![Separare contenuti business critical e BI in modalità self-service in capacità diverse](media/service-premium-capacity-optimize/separate-capacities.png)

- Se si condivide il contenuto solo con utenti di Power BI Pro, potrebbe non essere necessario archiviare il contenuto in una capacità dedicata.
- Usare capacità dedicate quando si vuole ottenere un tempo di aggiornamento specifico o quando sono necessarie funzionalità specifiche. Ad esempio, con set di dati di grandi dimensioni o quando si creano report impaginati.

### <a name="addressing-common-questions"></a>Risposte alle domande frequenti

L'ottimizzazione delle distribuzioni di Power BI Premium è un argomento complesso che richiede la comprensione dei requisiti del carico di lavoro, delle risorse disponibili e del loro utilizzo effettivo.

Questo articolo illustra sette domande di supporto comuni, che descrivono o possibili problemi e le relative spiegazioni, con informazioni su come identificarli e risolverli.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Perché la capacità è lenta e cosa è possibile fare?

Ci sono molti motivi che possono rallentare una capacità Premium. Questa domanda richiede ulteriori informazioni per comprendere cosa si intende per lenta. I report sono lenti da caricare? Oppure i report non vengono caricati? Gli oggetti visivi dei report sono lenti da caricare o aggiornare quando gli utenti interagiscono con il report? Il completamento dell'aggiornamento richiede più tempo del previsto o di quanto avveniva in precedenza?

Dopo aver compreso il motivo, è possibile iniziare a esaminare il problema. Le risposte alle sei domande seguenti aiuteranno a risolvere problemi più specifici.

### <a name="what-content-is-using-up-my-capacity"></a>Quali contenuti stanno usando la capacità?

È possibile usare l'app **Power BI Premium Capacity Metrics** per filtrare in base alla capacità ed esaminare le metriche delle prestazioni per il contenuto dell'area di lavoro. È possibile esaminare le metriche delle prestazioni e l'utilizzo delle risorse per ogni ora negli ultimi sette giorni per tutto il contenuto archiviato in una capacità Premium. Il monitoraggio è spesso il primo passaggio da eseguire per risolvere un problema generale relativo alle prestazioni della capacità Premium.

Le metriche chiave da monitorare includono informazioni su:

- Utilizzo medio della CPU e utilizzo elevato.
- Utilizzo medio della memoria e utilizzo elevato, nonché utilizzo della memoria per set di dati, flussi di dati e report impaginati specifici.
- Set di dati attivi caricati in memoria.
- Durata media e massima delle query.
- Tempi medi di attesa delle query.
- Tempi medi di aggiornamento dei set di dati e dei flussi di dati.

Nell'app Power BI Premium Capacity Metrics la memoria attiva indica la quantità totale di memoria assegnata a un report che non può essere rimossa perché è stata usata negli ultimi tre minuti. Un picco elevato nel tempo di attesa dell'aggiornamento potrebbe essere correlato a un set di dati di grandi dimensioni e/o attivo.

Il grafico **Top 5 by Average Duration** (Primi 5 per durata media) evidenzia i primi cinque set di dati, report impaginati e flussi di dati che utilizzano risorse della capacità. Gli elementi indicati tra i primi cinque sono i candidati per l'analisi e una possibile ottimizzazione.

### <a name="why-are-reports-slow"></a>Perché i report sono lenti?

Le tabelle seguenti illustrano i possibili problemi e i modi per identificarli e gestirli.

#### <a name="insufficient-capacity-resources"></a>Risorse della capacità insufficienti

| Possibili spiegazioni | Come identificare il problema | Come risolvere il problema |
| --- | --- | --- |
| Memoria attiva totale elevata (il modello non può essere rimosso perché è stato in uso negli ultimi tre minuti).<br><br> Più picchi elevati nei tempi di attesa delle query.<br><br> Più picchi elevati nei tempi di attesa dell'aggiornamento. | Monitorare le metriche di memoria \[[1](#endnote-1)\] e il numero di rimozioni \[[2](#endnote-2)\]. | Ridurre le dimensioni del modello o passare alla modalità DirectQuery. Vedere la sezione [Ottimizzazione dei modelli](#optimizing-models) in questo articolo.<br><br> Passare a un piano superiore di capacità.<br><br> Assegnare il contenuto a una capacità diversa. |

#### <a name="inefficient-report-designs"></a>Progettazioni dei report non efficienti

| Possibili spiegazioni | Come identificare il problema | Come risolvere il problema |
| --- | --- | --- |
| Le pagine del report contengono troppi oggetti visivi (il filtro interattivo può attivare almeno una query per ogni oggetto visivo).<br><br> Gli oggetti visivi recuperano più dati del necessario. | Esaminare le progettazioni dei report.<br><br> Rivolgersi agli utenti dei report per capire come interagiscono con i report.<br><br> Monitorare le metriche delle query sui set di dati \[[3](#endnote-3)\]. | Riprogettare i report con un minor numero di oggetti visivi per pagina. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Il set di dati è lento, soprattutto quando le prestazioni dei report in precedenza erano soddisfacenti

| Possibili spiegazioni | Come identificare il problema | Come risolvere il problema |
| --- | --- | --- |
| Volumi sempre maggiori di dati importati.<br><br> Logica di calcolo complessa o non efficiente, inclusi i ruoli per la sicurezza a livello di riga.<br><br> Modello non completamente ottimizzato.<br><br> Latenza del gateway (DirectQuery/Connessione dinamica).<br><br> Tempi di risposta lenti delle query sulle origini DirectQuery. | Esaminare le progettazioni dei modelli.<br><br> Monitorare i contatori delle prestazioni del gateway. | Vedere la sezione [Ottimizzazione dei modelli](#optimizing-models) in questo articolo. |

#### <a name="high-concurrent-report-usage"></a>Utilizzo elevato di report simultanei

| Possibili spiegazioni | Come identificare il problema | Come risolvere il problema |
| --- | --- | --- |
| Tempi di attesa delle query elevati.<br><br> Saturazione della CPU.<br><br> Limiti delle connessioni DirectQuery/Connessione dinamica superati. | Monitorare le metriche relative a utilizzo della CPU \[[4](#endnote-4)\], tempi di attesa delle query e utilizzo di DirectQuery/Connessione dinamica \[[5](#endnote-5)\], nonché la durata delle query. Le fluttuazioni possono indicare problemi di concorrenza. | Passare a un piano superiore di capacità o assegnare il contenuto a una capacità diversa.<br><br> Riprogettare i report con un minor numero di oggetti visivi per pagina. |

**Note:**    
<a name="endnote-1"></a>\[1\] Average Memory Usage (GB) (Utilizzo memoria medio - GB) e Highest Memory Consumption (GB) (Utilizzo memoria massimo - GB).   
<a name="endnote-2"></a>\[2\] Dataset evictions (Rimozioni set di dati).   
<a name="endnote-3"></a>\[3\] Dataset Queries (Query set di dati), Dataset Average Query Duration (ms) (Durata media query set di dati - ms), Dataset Wait Count (Conteggio di attesa set di dati) e Dataset Average Wait Time (ms) (Tempo di attesa medio set di dati - ms).   
<a name="endnote-4"></a>\[4\] CPU High Utilization Count (Utilizzo elevato CPU) e CPU Time of Highest Utilization (past seven days) (Periodo di massimo utilizzo CPU - ultimi sette giorni).   
<a name="endnote-5"></a>\[5\] DQ/LC High Utilization Count (Utilizzo elevato DirectQuery/Connessione dinamica) e DQ/LC Time of Highest Utilization (past seven days) (Periodo di massimo utilizzo DirectQuery/Connessione dinamica - ultimi sette giorni).   

### <a name="why-are-reports-not-loading"></a>Perché i report non vengono caricati?

Quando non è possibile caricare i report, è un chiaro segno del fatto che la capacità non ha memoria sufficiente ed è surriscaldata. Ciò può verificarsi quando sono in corso query attive su tutti i modelli caricati, che quindi non possono essere rimossi, e le operazioni di aggiornamento sono state sospese o ritardate. Il servizio Power BI cercherà di caricare il set di dati per 30 secondi e l'utente riceverà una notifica automatica di errore con un suggerimento di riprovare a breve.

Attualmente non c'è alcuna metrica da monitorare per gli errori di caricamento dei report. È possibile identificare il rischio di questo problema monitorando la memoria di sistema, in particolare l'utilizzo massimo e il periodo di massimo utilizzo. Quantità elevate di rimozioni dei set di dati e lunghi tempi medi di attesa dell'aggiornamento dei set di dati possono indicare il verificarsi di questo problema.

Se ciò accade solo occasionalmente, potrebbe non essere considerato un problema prioritario. Gli utenti del report vengono informati che il servizio è occupato e che devono riprovare dopo un breve periodo di tempo. Se ciò accade troppo spesso, il problema può essere risolto passando a un piano superiore di capacità Premium o assegnando il contenuto a una capacità diversa.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare la metrica **Query Failures** (Errori di query) per determinare quando si verifica questo problema. È anche possibile riavviare la capacità, reimpostando tutte le operazioni in caso di sovraccarico del sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Perché gli aggiornamenti non vengono avviati in base alla pianificazione?

Gli orari di inizio degli aggiornamenti pianificati non sono garantiti. Tenere presente che il servizio Power BI dà sempre la priorità alle operazioni interattive rispetto alle operazioni in background. L'aggiornamento è un'operazione in background che può verificarsi quando vengono soddisfatte due condizioni:

- La memoria è sufficiente
- Il numero di aggiornamenti simultanei supportati per la capacità Premium non è stato superato

Quando queste condizioni non vengono soddisfatte, l'aggiornamento viene messo in coda fino a quando le condizioni non sono favorevoli.

Per un aggiornamento completo, tenere presente che è necessario almeno il doppio delle dimensioni di memoria dei set di dati correnti. Se non è disponibile memoria sufficiente, l'aggiornamento non può iniziare fino a quando la rimozione dei modelli non libera memoria, ovvero viene ritardato finché uno o più set di dati non diventano inattivi e possono essere rimossi.

Tenere presente che il numero massimo supportato di aggiornamenti simultanei è impostato su 1,5 volte le memorie centrali virtuali del back-end, arrotondato per eccesso.

Un aggiornamento pianificato non riesce quando non può essere avviato prima dell'ora prevista per l'aggiornamento pianificato successivo. Per un aggiornamento su richiesta attivato manualmente dall'interfaccia utente verranno eseguiti fino a tre tentativi prima di determinare l'esito negativo.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare la metrica **Average Refresh Wait Time (minutes)** (Tempo di attesa medio aggiornamenti - minuti) per determinare il ritardo medio tra l'ora pianificata e l'inizio dell'operazione.

Anche se non si tratta in genere di una priorità amministrativa, facendo in modo che gli aggiornamenti dei dati avvengano quando previsto si garantisce la disponibilità di memoria sufficiente. Ciò può richiedere l'isolamento dei set di dati in capacità con risorse sufficienti note. Gli amministratori possono anche coordinarsi con i proprietari dei set di dati per sfalsare o ridurre gli orari degli aggiornamenti dei dati pianificati, in modo da ridurre al minimo i conflitti. Si noti che non è possibile per un amministratore visualizzare la coda di aggiornamento né recuperare le pianificazioni dei set di dati.

### <a name="why-are-refreshes-slow"></a>Perché gli aggiornamenti sono lenti?

Gli aggiornamenti possono essere lenti o percepiti come lenti (come spiegato nella domanda precedente).

Quando l'aggiornamento è effettivamente lento, le cause possono essere diverse:

- CPU insufficiente (l'aggiornamento può richiedere un utilizzo molto elevato della CPU).
- Memoria insufficiente, con conseguente sospensione dell'aggiornamento (che richiede l'avvio dell'aggiornamento dall'inizio quando le condizioni sono favorevoli).
- Motivi non legati alla capacità, tra cui velocità di risposta del sistema dell'origine dati, latenza di rete, autorizzazioni non valide o velocità effettiva del gateway.
- Volume di dati. In questo caso, è consigliabile configurare l'aggiornamento incrementale, come descritto di seguito.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare la metrica **Average Refresh Duration (minutes)** (Durata media aggiornamenti - minuti) per determinare un benchmark per il confronto nel tempo e la metrica **Average Refresh Wait Time (minutes)** (Tempo di attesa medio aggiornamenti - minuti) per determinare il ritardo medio tra l'ora pianificata e l'inizio dell'operazione.

L'aggiornamento incrementale può ridurre significativamente la durata dell'aggiornamento dei dati, in particolare per le tabelle di modelli di grandi dimensioni. L'aggiornamento incrementale offre quattro vantaggi:

- **Gli aggiornamenti sono più veloci**: deve essere caricato solo un subset di una tabella, riducendo l'utilizzo di CPU e memoria, e il parallelismo può essere maggiore quando si aggiornano più partizioni.
- **Gli aggiornamenti vengono eseguiti solo quando è necessario**: è possibile configurare criteri di aggiornamento incrementale per il caricamento solo quando i dati sono stati modificati.
- **Gli aggiornamenti sono più affidabili**: le connessioni di più breve durata ai sistemi delle origini dati volatili sono meno suscettibili alla disconnessione.
- **Le dimensioni dei modelli rimangono contenute**: è possibile configurare criteri di aggiornamento incrementale per rimuovere automaticamente la cronologia oltre una finestra temporale scorrevole.

Per altre informazioni, vedere [Aggiornamento incrementale in Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Perché gli aggiornamenti dei dati non vengono completati?

Quando un aggiornamento dei dati inizia ma non viene completato, le cause possono essere diverse:

- Memoria insufficiente, anche se c'è un solo modello nella capacità Premium, ad esempio se le dimensioni del modello sono molto grandi.
- Motivi non legati alla capacità, tra cui disconnessione del sistema dell'origine dati, autorizzazioni non valide o errore del gateway.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare la metrica **Refresh Failures due to out of Memory** (Errori di aggiornamento per memoria insufficiente).

## <a name="optimizing-models"></a>Ottimizzazione dei modelli

La progettazione ottimale del modello è fondamentale per offrire una soluzione efficiente e scalabile. Tuttavia, una discussione completa esula dall'ambito di questo articolo. Questa sezione illustra invece le aree principali da tenere in considerazione per l'ottimizzazione dei modelli.

### <a name="optimizing-power-bi-hosted-models"></a>Ottimizzazione dei modelli ospitati in Power BI

L'ottimizzazione dei modelli ospitati in una capacità Premium può essere eseguita a livello di origine dati e di modello.

Prendere in considerazione le possibilità di ottimizzazione per un modello di importazione:

![Possibilità di ottimizzazione per un modello di importazione](media/service-premium-capacity-optimize/import-model-optimizations.png)

A livello di origine dati:

- Le origini dati relazionali possono essere ottimizzate per garantire l'aggiornamento più rapido possibile tramite la pre-integrazione dei dati, l'applicazione di indici appropriati, la definizione di partizioni di tabella allineate ai periodi di aggiornamento incrementale e la materializzazione dei calcoli (al posto di colonne e tabelle dei modelli calcolate) o l'aggiunta di logica di calcolo alle viste.
- Le origini dati non relazionali possono essere pre-integrate con archivi relazionali.
- Assicurarsi che i gateway abbiano risorse sufficienti, preferibilmente in computer dedicati, con una larghezza di banda di rete sufficiente e in prossimità delle origini dati.

A livello di modello:

- Le progettazioni delle query Power Query possono ridurre o rimuovere le trasformazioni complesse, in particolare quelle che uniscono origini dati diverse (i data warehouse ottengono questo risultato durante la fase di estrazione, trasformazione e caricamento). Assicurarsi inoltre che siano impostati i livelli di privacy dell'origine dati appropriati. In questo modo, è possibile evitare di richiedere a Power BI di caricare i risultati completi per produrre un risultato combinato tra le query.
- La struttura del modello determina i dati da caricare e influisce direttamente sulle dimensioni del modello. Può essere progettata per evitare di caricare dati non necessari mediante la rimozione di colonne, la rimozione di righe (in particolare i dati cronologici) o il caricamento di dati riepilogati (a scapito del caricamento di dati dettagliati). È possibile ottenere una riduzione significativa delle dimensioni rimuovendo le colonne con cardinalità elevata, in particolare quelle di testo, che non consentono l'archiviazione o la compressione in modo molto efficiente.
- È possibile migliorare le prestazioni delle query sui modelli configurando relazioni a direzione singola, a meno che non ci sia un motivo valido per consentire il filtro bidirezionale. Provare anche a usare la funzione [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) invece del filtro bidirezionale.
- Le tabelle delle aggregazioni possono ottenere risposte rapide alle query caricando dati pre-riepilogati, tuttavia ciò comporta un aumento delle dimensioni del modello e quindi tempi di aggiornamento più lunghi. In genere, le tabelle delle aggregazioni devono essere riservate per i modelli di dimensioni molto grandi o le progettazioni di modelli compositi.
- Le tabelle e le colonne calcolate causano un aumento delle dimensioni del modello e quindi tempi di aggiornamento più lunghi. In genere, è possibile ottenere una dimensione di archiviazione inferiore e un tempo di aggiornamento più rapido quando i dati vengono materializzati o calcolati nell'origine dati. Se ciò non è possibile, l'uso di colonne personalizzate di Power Query può offrire una migliore compressione dello spazio di archiviazione.
- Potrebbe essere possibile ottimizzare le espressioni DAX per le misure e le regole per la sicurezza a livello di riga, ad esempio riscrivendo la logica per evitare formule costose.
- L'aggiornamento incrementale può ridurre notevolmente il tempo di aggiornamento e conservare memoria e CPU. È anche possibile configurare l'aggiornamento incrementale per rimuovere i dati cronologici mantenendo contenute le dimensioni del modello.
- Un modello può essere riprogettato come due modelli in presenza di modelli di query diversi e in conflitto. Alcuni report, ad esempio, presentano aggregazioni di alto livello su tutta la cronologia e possono tollerare una latenza di 24 ore. Altri report riguardano i dati odierni e necessitano di un accesso granulare alle singole transazioni. Invece di progettare un singolo modello per soddisfare le esigenze di tutti i report, creare due modelli ottimizzati per i singoli requisiti.

Prendere in considerazione le possibilità di ottimizzazione per un modello DirectQuery. Quando il modello invia richieste di query all'origine dati sottostante, l'ottimizzazione dell'origine dati è fondamentale per garantire tempi di risposta rapidi delle query sul modello.

 ![Possibilità di ottimizzazione per un modello DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

A livello di origine dati:

- L'origine dati può essere ottimizzata per garantire l'esecuzione delle query più rapida possibile tramite la pre-integrazione dei dati (non possibile a livello di modello), l'applicazione di indici appropriati, la definizione di partizioni di tabella, la materializzazione di dati riepilogati (con viste indicizzate) e la riduzione della quantità di calcoli. L'esperienza ottimale si ottiene quando le query pass-through devono solo filtrare ed eseguire inner join tra viste o tabelle indicizzate.
- Assicurarsi che i gateway abbiano risorse sufficienti, preferibilmente in computer dedicati, con una larghezza di banda di rete sufficiente e in prossimità delle origini dati.

A livello di modello:

- Le progettazioni di query Power Query devono preferibilmente non applicare trasformazioni. Se le trasformazioni sono necessarie, cercare di ridurle al minimo.
- È possibile migliorare le prestazioni delle query sui modelli configurando relazioni a direzione singola, a meno che non ci sia un motivo valido per consentire il filtro bidirezionale. Le relazioni tra i modelli devono inoltre essere configurate in modo da presupporre che l'integrità referenziale venga applicata (quando necessario) e in questo modo le query sulle origini dati useranno inner join più efficienti, invece di outer join.
- Evitare di creare colonne personalizzate di query Power Query o una colonna calcolata del modello: materializzarle nell'origine dati, quando possibile.
- Potrebbe essere possibile ottimizzare le espressioni DAX per le misure e le regole per la sicurezza a livello di riga, ad esempio riscrivendo la logica per evitare formule costose.

Prendere in considerazione le possibilità di ottimizzazione per un modello composito. Tenere presente che un modello composito consente una combinazione di tabelle di importazione e DirectQuery.

![Possibilità di ottimizzazione per un modello composito](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- In genere, l'ottimizzazione per i modelli di importazione e DirectQuery si applica alle tabelle dei modelli compositi che usano queste modalità di archiviazione.
- Solitamente, è possibile cercare di ottenere una progettazione bilanciata configurando le tabelle delle dimensioni (che rappresentano le entità aziendali) con modalità di archiviazione doppia e le tabelle dei fatti (tabelle spesso di grandi dimensioni che rappresentano fatti operativi) con modalità di archiviazione DirectQuery. La modalità di archiviazione doppia include sia la modalità di archiviazione DirectQuery che quella di importazione e ciò consente al servizio Power BI di determinare la modalità di archiviazione più efficiente da usare quando viene generata una query nativa per il pass-through.
- Assicurarsi che i gateway abbiano risorse sufficienti, preferibilmente in computer dedicati, con una larghezza di banda di rete sufficiente e in prossimità delle origini dati.
- Le tabelle delle aggregazioni configurate con la modalità di archiviazione di importazione possono offrire miglioramenti significativi delle prestazioni di query quando vengono usate per riepilogare le tabelle dei fatti in modalità di archiviazione DirectQuery. In questo caso, le tabelle delle aggregazioni fanno aumentare le dimensioni del modello e il tempo di aggiornamento, ma spesso si tratta di un compromesso accettabile per query più veloci.

### <a name="optimizing-externally-hosted-models"></a>Ottimizzazione dei modelli ospitati all'esterno

Molte possibilità di ottimizzazione illustrate nella sezione [Ottimizzazione dei modelli ospitati in Power BI](#optimizing-power-bi-hosted-models) si applicano anche ai modelli sviluppati con Azure Analysis Services e SQL Server Analysis Services. Fanno chiaramente eccezione alcune funzionalità che non sono attualmente supportate, inclusi i modelli compositi e le tabelle delle aggregazioni.

Un'ulteriore considerazione per i set di dati ospitati esternamente riguarda l'hosting del database in relazione al servizio Power BI. Per Azure Analysis Services, ciò significa creare la risorsa di Azure nella stessa area del tenant di Power BI (area iniziale). Per SQL Server Analysis Services, per IaaS, ciò significa ospitare la macchina virtuale nella stessa area e per l'ambiente locale significa garantire una configurazione efficiente del gateway.

Può essere anche interessante notare che i database di Azure Analysis Services e i database tabulari di SQL Server Analysis Services richiedono che i relativi modelli vengano caricati completamente in memoria e che rimangano sempre in memoria per supportare le query. Analogamente al servizio Power BI, è necessario che ci sia memoria sufficiente per l'aggiornamento se il modello deve rimanere online durante l'aggiornamento. A differenza del servizio Power BI, non è previsto che i modelli vengano resi automaticamente obsoleti e tolti dalla memoria in base all'utilizzo. Power BI Premium offre quindi un approccio più efficiente per ottimizzare le query sui modelli con un utilizzo di memoria inferiore.

## <a name="capacity-planning"></a>Pianificazione della capacità

Le dimensioni di una capacità Premium determinano le risorse di memoria e del processore disponibili e i limiti imposti alla capacità. È necessario considerare anche il numero di capacità Premium, poiché la creazione di più capacità Premium può aiutare a isolare i carichi di lavoro l'uno dall'altro. Si noti che lo spazio di archiviazione è di 100 TB per nodo di capacità, quantità probabilmente più che sufficiente per qualsiasi carico di lavoro.

Determinare le dimensioni e il numero di capacità Premium può risultare complesso, soprattutto per le capacità iniziali create. Il primo passaggio per stabilire le dimensioni della capacità è comprendere il carico di lavoro medio che rappresenta l'utilizzo giornaliero previsto. È importante comprendere che non tutti i carichi di lavoro sono uguali. Ad esempio, da un lato 100 utenti simultanei che accedono a una singola pagina di un report che contiene un singolo oggetto visivo è uno scenario le cui esigenze possono essere soddisfatte facilmente. Dall'altro lato, 100 utenti simultanei che accedono a 100 report diversi, ognuno con 100 oggetti visivi nella pagina del report è uno scenario che richiede risorse di capacità molto diverse.

Gli amministratori della capacità dovranno quindi considerare molti fattori specifici dell'ambiente, del contenuto e dell'utilizzo previsto. L'obiettivo principale è ottimizzare l'utilizzo della capacità offrendo tempi di query coerenti, tempi di attesa accettabili e frequenze di rimozione. Ecco alcuni fattori da considerare:

- **Dimensioni del modello e caratteristiche dei dati**: i modelli di importazione devono essere caricati completamente in memoria per consentire l'esecuzione di query o l'aggiornamento. I set di dati DirectQuery/Connessione dinamica possono richiedere un tempo di elaborazione significativo e probabilmente una quantità di memoria significativa per valutare misure complesse o regole di sicurezza a livello di riga. Le dimensioni della memoria e del processore e la velocità effettiva delle query DirectQuery/Connessione dinamica sono limitate dalle dimensioni della capacità.
- **Modelli attivi simultanei**: l'esecuzione di query simultanee su modelli di importazione diversi offrirà tempi di risposta e prestazioni ottimali quando i modelli rimangono in memoria. È necessario disporre di memoria sufficiente per ospitare tutti i modelli su cui vengono spesso eseguite query, con memoria aggiuntiva per consentirne l'aggiornamento.
- **Aggiornamento dei modelli di importazione**: il tipo di aggiornamento (completo o incrementale), la durata e la complessità delle query Power Query e la logica di tabelle e colonne calcolate possono avere un impatto sulla memoria e soprattutto sull'utilizzo del processore. Gli aggiornamenti simultanei sono limitati dalle dimensioni della capacità (1,5 x memorie centrali virtuali del back-end, con arrotondamento per eccesso.).
- **Query simultanee**: molte query simultanee possono comportare la mancata risposta dei report quando le connessioni del processore o di DirectQuery/Connessione dinamica superano il limite di capacità. Ciò si verifica in particolare per le pagine dei report che includono molti oggetti visivi.
- **Flussi di dati e report impaginati**: la capacità può essere configurata in modo da supportare i flussi di dati e i report impaginati, ognuno dei quali richiede una percentuale massima configurabile di memoria della capacità. La memoria viene allocata in modo dinamico ai flussi di dati e in modo statico ai report impaginati.

Oltre a questi fattori, gli amministratori della capacità possono prendere in considerazione la creazione di più capacità. Più capacità consentono l'isolamento dei carichi di lavoro ed è possibile eseguire la configurazione in modo da garantire le risorse per i carichi di lavoro prioritari. È ad esempio possibile creare due capacità per separare i carichi di lavoro business-critical da quelli BI in modalità self-service (SSBI). La capacità business-critical può essere usata per isolare modelli aziendali di grandi dimensioni offrendo risorse garantite e concedendo l'accesso per la creazione solo al reparto IT. La capacità SSBI può essere usata per ospitare un numero sempre maggiore di modelli più piccoli, concedendo l'accesso ai business analyst. Per la capacità SSBI possono a volte verificarsi attese per l'aggiornamento o le query, che sono tollerabili.

Nel tempo, gli amministratori della capacità possono bilanciare le aree di lavoro tra le capacità spostando i contenuti tra le aree di lavoro oppure le aree di lavoro tra le capacità e passando a un piano superiore o inferiore della capacità. In genere, per ospitare modelli di grandi dimensioni si passa a un piano superiore di capacità, mentre per una concorrenza maggiore si aumenta la capacità.

Tenere presente che l'acquisto di una licenza fornisce al tenant memorie centrali virtuali. L'acquisto di una sottoscrizione **P3** può essere usato per creare da una a quattro capacità Premium, ad esempio 1 x P3, 2 x P2 o 4 x P1. Prima di passare da una capacità P2 a una capacità P3, inoltre, valutare se può essere opportuno dividere le memorie centrali virtuali per creare due capacità P1.

## <a name="testing-approaches"></a>Approcci di test

Una volta decise le dimensioni della capacità, è possibile eseguire test creando un ambiente controllato. Un'opzione pratica ed economica consiste nel creare una capacità di Azure (SKU A), tenendo presente che la capacità P1 ha le stesse dimensioni di una capacità A4 e le capacità P2 e P3 hanno, rispettivamente, le stesse dimensioni delle capacità A5 e A6. Le capacità di Azure possono essere create rapidamente e vengono fatturate su base oraria. Una volta completati i test, è quindi possibile eliminarle facilmente affinché non vengano addebitati ulteriori costi.

Il contenuto dei test può essere aggiunto alle aree di lavoro create nella capacità di Azure e quindi un singolo utente può eseguire i report per generare un carico di lavoro realistico e rappresentativo delle query. Se sono presenti modelli di importazione, è necessario eseguire anche un aggiornamento per ogni modello. È possibile usare gli strumenti di monitoraggio per esaminare tutte le metriche e comprendere l'utilizzo delle risorse.

È importante che i test siano ripetibili. I test devono essere eseguiti più volte e devono restituire ogni volta approssimativamente lo stesso risultato. È possibile usare una media di questi risultati per estrapolare e stimare un carico di lavoro in condizioni di produzione reali.

Se si dispone già di una capacità e dei report per i quali si vuole eseguire i test di carico, usare lo [strumento di generazione del carico di PowerShell](https://aka.ms/PowerBILoadTestingTool) per generare rapidamente un test di carico. Lo strumento consente di stimare il numero di istanze di ogni report che la capacità può eseguire in un'ora. È possibile usare lo strumento per valutare le prestazioni della capacità per il rendering di un singolo report o per il rendering di più report diversi in parallelo. Per altre informazioni, vedere il video [Microsoft Power BI: capacità Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Per generare un test più complesso, sviluppare un'applicazione di test di carico che simula un carico di lavoro realistico. Per altre informazioni, vedere il webinar [Test di carico di applicazioni Power BI con Visual Studio Load Test](https://powerbi.microsoft.com/en-us/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/).

## <a name="acknowledgements"></a>Riconoscimenti

Questo articolo è stato scritto da Peter Myers, Data Platform MVP ed esperto indipendente di business intelligence con [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Scenari delle capacità Premium](service-premium-capacity-scenarios.md)   
  
Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

||||||