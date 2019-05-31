---
title: Ottimizzare le capacità di Microsoft Power BI Premium
description: Descrive le strategie di ottimizzazione per la capacità di Power BI Premium.
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
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565353"
---
# <a name="optimizing-premium-capacities"></a>Ottimizzazione della capacità Premium

Quando si verificano problemi di prestazioni della capacità Premium, un primo approccio comune è ottimizzare o ottimizzare le soluzioni per ripristinare i tempi di risposta accettabili. La logica alla base di evitare l'acquisto di ulteriore capacità Premium a meno che non giustificato.

Quando è necessaria ulteriore capacità Premium, sono disponibili due opzioni descritte in questo articolo:

- Scalabilità verticale una capacità Premium esistente
- Aggiungere una nuova capacità Premium

Infine, il test approcci e ridimensionamento delle capacità Premium concludere questo articolo.

## <a name="best-practices"></a>Procedure consigliate

Quando si tenta di ottenere l'utilizzo e le prestazioni migliori, esistono alcune procedure consigliate, tra cui:

- Usando le aree di lavoro di app anziché le aree di lavoro personale.
- Separazione di BI self-service (SSBI) e aziendali critici in capacità differenti.

  ![La separazione aziendali critici e BI self-service in capacità differenti](media/service-premium-capacity-optimize/separate-capacities.png)

- Se la condivisione del contenuto solo con gli utenti di Power BI Pro, è non possibile alcuna necessità di archiviare il contenuto in una capacità dedicata.
- Usare le capacità dedicate durante la ricerca per ottenere un tempo di aggiornamento specifico, o quando sono necessarie funzionalità specifiche. Ad esempio, con grandi set di dati o report impaginati.

### <a name="addressing-common-questions"></a>Indirizzamento delle domande più comuni

Ottimizzazione delle distribuzioni di Power BI Premium è un argomento complesso che interessa la comprensione dei requisiti del carico di lavoro, le risorse disponibili e l'uso effettivo.

Questo articolo affronta sette domande comuni sul supporto, che descrive i possibili problemi e spiegazioni e informazioni su come identificare e risolvere i problemi.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Perché è la capacità lenta e che cosa può fare?

Esistono molti motivi che possono contribuire a una lenta capacità Premium. Questa domanda richiede ulteriore informazioni utili per comprendere cosa si intende per lento. Sono lente caricare i report? O non vengono caricati per? Sono oggetti visivi del report lente caricare o aggiornare quando gli utenti interagiscono con il report? Vengono aggiornati richiede più tempo del previsto o si è verificato in precedenza?

Avendo compreso del motivo, è possibile iniziare a esaminare. Le risposte alle domande seguenti sei consente di risolvere più problemi specifici.

### <a name="what-content-is-using-up-my-capacity"></a>Il tipo di contenuto Usa la capacità?

È possibile usare la **le metriche della capacità di Power BI Premium** Filtra per capacità ed esaminare le metriche delle prestazioni per il contenuto dell'area di lavoro dell'app. È possibile esaminare l'uso di risorse e le metriche delle prestazioni per ora negli ultimi sette giorni per tutto il contenuto archiviato all'interno di una capacità Premium. Il monitoraggio è spesso il primo passaggio da eseguire quando la risoluzione dei problemi di interesse generale sulle prestazioni della capacità Premium.

Le metriche chiave per il monitoraggio includono:

- Medio della CPU e il conteggio di utilizzo elevato.
- Media di memoria e il conteggio di utilizzo elevato e utilizzo della memoria per i set di dati specifico, flussi di dati e i report impaginati.
- Attiva set di dati caricati in memoria.
- Durate delle query medi e massimi.
- Tempi di attesa media della query.
- Flusso di dati e set di dati medio aggiornamento volte.

Nell'app per le metriche della capacità di Power BI Premium, active memoria Mostra la quantità totale di memoria assegnata a un report che non può essere rimosso perché è stato in uso entro gli ultimi tre minuti. Un picco nel tempo di attesa di aggiornamento elevato potrebbe essere correlato con un set di dati di grandi dimensioni e/o attivo.

Il **primi 5 per durata media** grafico evidenzia i primi cinque set di dati, i report impaginati e flussi di dati utilizzano la capacità di risorse. Contenuto tra i primi cinque elenchi è candidati per l'ottimizzazione di indagine e la possibile.

### <a name="why-are-reports-slow"></a>Perché i report di rallentamento?

Le tabelle seguenti illustrano i possibili problemi e sui modi per identificare e gestirli.

#### <a name="insufficient-capacity-resources"></a>Risorse di capacità insufficiente

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Memoria attive totali elevata (modello non può essere rimosso perché è in uso entro gli ultimi tre minuti).<br><br> Tempi di attesa più elevati picchi nella query.<br><br> Tempi di attesa più elevati picchi di aggiornamento. | Monitorare le metriche della memoria \[ [1](#endnote-1)\]e i conteggi di rimozione \[ [2](#endnote-2)\]. | Ridurre la dimensione del modello o convertire alla modalità DirectQuery. Vedere le [ottimizzare i modelli](#optimizing-models) sezione in questo articolo.<br><br> Aumentare la capacità.<br><br> Assegnare il contenuto a una capacità diversa. |

#### <a name="inefficient-report-designs"></a>Progettazioni di report inefficiente

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Le pagine del report contengono troppi oggetti visivi (applicazione di filtri interattiva può attivare almeno una query per ogni oggetto visivo).<br><br> Gli oggetti visivi recuperano più dati rispetto al necessario. | Esaminare le progettazioni di report.<br><br> Intervista agli utenti di report per comprendere come interagiscono con i report.<br><br> Monitorare le metriche di query di set di dati \[ [3](#endnote-3)\]. | Report di riprogettazione con oggetti visivi di un numero inferiore per ogni pagina. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Set di dati è lento, specialmente quando i report già stato eseguito correttamente

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Sempre più grandi volumi di dati di importazione.<br><br> Logica di calcolo complesso o inefficiente, inclusi i ruoli a livello di riga.<br><br> Modello non completamente ottimizzato.<br><br> (DQ/LC) Latenza di gateway.<br><br> Tempi di risposta query di origine di rallentamento DQ. | Esaminare le progettazioni di modello.<br><br> Monitorare i contatori delle prestazioni del gateway. | Vedere le [ottimizzare i modelli](#optimizing-models) sezione in questo articolo. |

#### <a name="high-concurrent-report-usage"></a>Utilizzo elevato rapporto simultanee

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Tempi di attesa di query elevati.<br><br> Saturazione della CPU.<br><br> Limiti di connessione DQ/LC superati. | Monitorare l'utilizzo della CPU \[ [4](#endnote-4)\], tempi di attesa di query e l'utilizzo di DQ/LC \[ [5](#endnote-5) \] metriche + durate delle Query. Se ripristinarne, possono indicare problemi di concorrenza. | Aumentare la capacità o assegnare il contenuto a una capacità diversa.<br><br> Report di riprogettazione con oggetti visivi di un numero inferiore per ogni pagina. |

**Note:**    
<a name="endnote-1"></a>\[1\] medio di utilizzo della memoria (GB) e il consumo di memoria massima (GB).   
<a name="endnote-2"></a>\[2\] eliminazioni di set di dati.   
<a name="endnote-3"></a>\[3\] attesa di query di set di dati, durata Query di set di dati Media (ms), set di dati di conteggio e tempo medio di set di dati di attesa (ms).   
<a name="endnote-4"></a>\[4\] conteggio di utilizzo elevato della CPU e il tempo di CPU di massimo utilizzo (ultimi sette giorni).   
<a name="endnote-5"></a>\[5\] DQ/LC conteggio di utilizzo elevato e l'ora DQ/LC di massimo utilizzo (ultimi sette giorni).   

### <a name="why-are-reports-not-loading"></a>Perché i report non stia caricando?

Quando i report non riesce a caricare, è un chiaro indizio la capacità di memoria insufficiente ed è eccessiva riscaldata. Ciò può verificarsi quando tutti i modelli caricati vengono sottoposte a attivamente e pertanto non è possibile eliminarle e qualsiasi operazione di aggiornamento sono stato messo in pausa o posticipate. Il servizio Power BI proverà a caricare il set di dati per 30 secondi e l'utente normalmente viene avvisato dell'errore con un suggerimento per riprovare più tardi.

Non è attualmente disponibile alcuna metrica da monitorare per il report errori di caricamento. Monitoraggio memoria del sistema, specificamente più alto utilizzo e tempo di utilizzo più elevato, è possibile identificare il potenziale per risolvere questo problema. Eliminazioni di set di dati elevata e lungo tempo di attesa medio aggiornamento set di dati è stato possibile suggerire che questo problema è in corso.

Se ciò si verifica molto raramente, questo potrebbe non essere considerato un problema di priorità. Gli utenti del report vengono informati che il servizio è occupato e che è opportuno ritentare dopo un breve periodo di tempo. In questo caso troppa frequenza, il problema può essere risolto aumentando la capacità Premium oppure tramite l'assegnazione del contenuto a una capacità diversa.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **errori di Query** metrica per determinare in questo caso. È anche possibile riavviare la capacità, la reimpostazione di tutte le operazioni in caso di sovraccarico del sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Il motivo per cui gli aggiornamenti non vengono avviato su pianificazione?

Ore di inizio aggiornamento pianificato non è garantite. È importante ricordare che il servizio Power BI avrà sempre la priorità operazioni interattive su operazioni in background. L'aggiornamento è un'operazione in background che può verificarsi quando due condizioni sono soddisfatte:

- È disponibile memoria sufficiente
- Non viene superato il numero di aggiornamenti simultanei supportati per la capacità Premium

Quando non vengono soddisfatte le condizioni, l'aggiornamento viene accodata fino a quando le condizioni sono soddisfacenti.

Per un aggiornamento completo, è importante ricordare che sono necessaria almeno raddoppierà le dimensioni di memoria corrente del set di dati. Se non è disponibile memoria sufficiente, non è possibile iniziare l'aggiornamento fino a quando non la rimozione del modello consente di liberare memoria: questo significa che ritarda fino a quando uno o più set di dati diventa inattiva e può essere eliminata.

È importante ricordare che il numero di aggiornamenti simultanei massimi supportato è impostato su 1,5 volte i back-end memorie centrali, arrotondati per eccesso.

Un aggiornamento pianificato non riuscirà quando che non può cominciare prima della scadenza di inizio dell'aggiornamento pianificato successivo. Un aggiornamento su richiesta attivato manualmente dall'interfaccia utente tenterà di eseguire fino a tre volte prima che si verifichi.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **medio aggiornamento tempo di attesa (minuti)** metrica per determinare il ritardo medio tra l'orario pianificato e l'inizio dell'operazione.

Anche se non viene in genere una priorità di amministrazione per influenzare i dati in fase di aggiornamento, assicurarsi che sia disponibile memoria sufficiente. Questa operazione potrebbe comportare l'isolamento del set di dati per le capacità con sufficienti risorse note. È anche possibile che gli amministratori è stato possibile coordinare con i proprietari dei set di dati per scaglionare o ridurre i tempi di aggiornamento dati pianificato per ridurre al minimo i conflitti. Si noti che non è possibile che un amministratore di visualizzare la coda di aggiornamento o per recuperare le pianificazioni di set di dati.

### <a name="why-are-refreshes-slow"></a>Il motivo per cui vengono aggiornati lenta?

Gli aggiornamenti possono essere lento - o percepita lenta (come gli indirizzi di domanda comune precedente).

Quando in realtà, l'aggiornamento è lenta, può essere dovuto a diversi motivi:

- CPU insufficiente (l'aggiornamento può essere elevato della CPU).
- Memoria insufficiente, causando la sospensione di aggiornamento (che richiede l'aggiornamento ricominciare da capo quando le condizioni sono favorevoli per riprendere).
- Non-capacità motivi, tra cui la reattività del sistema dell'origine dati, la latenza di rete, autorizzazioni non valide o velocità effettiva del gateway.
- Volume di dati - un buon motivo per configurare incrementale aggiorna, come descritto di seguito.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **durata media di aggiornamento (minuti)** metrica per determinare un benchmark per il confronto nel corso del tempo e il **medio aggiornamento tempo di attesa (minuti)** metriche per determinare il ritardo medio tra medio di ritardo tra l'orario pianificato e l'inizio dell'operazione.

L'aggiornamento incrementale può ridurre notevolmente durata di aggiornamento dati, in particolare per tabelle di modelli di grandi dimensioni. Esistono quattro vantaggi associati con l'aggiornamento incrementale:

- **Gli aggiornamenti sono più veloci** : solo un subset di una tabella richiede il caricamento, riducendo l'utilizzo della CPU e memoria e il parallelismo può essere superiore quando l'aggiornamento di più partizioni.
- **Gli aggiornamenti si verificano solo quando necessario** -criteri di aggiornamento incrementale possono essere configurati per caricare solo quando vengono modificati dati.
- **Gli aggiornamenti sono più affidabili** -connessioni in esecuzione più brevi per i sistemi di origine dati volatili sono meno soggette a disconnessione.
- **I modelli rimangono trim** -criteri di aggiornamento incrementale possono essere configurati per Rimuovi automaticamente cronologia oltre a una finestra temporale scorrevole di tempo.

Per altre informazioni, vedere [Incremental aggiornamento in Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Perché i dati viene aggiornato non è stato completato?

Quando l'aggiornamento dei dati verrà avviata ma non viene completato, può essere dovuto a diversi motivi:

- Memoria insufficiente, anche se è presente un solo modello la capacità Premium, ad esempio la dimensione del modello è molto elevata.
- Capacità non motivi, tra cui la disconnessione di sistema di origine dati, le autorizzazioni non è valide o errore di gateway.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **Aggiorna gli errori dovuti a memoria insufficiente** metrica.

## <a name="optimizing-models"></a>Ottimizzare i modelli

Progettazione modello ottimale è fondamentale nell'offrire una soluzione efficiente e scalabile. Tuttavia, è oltre l'ambito di questo articolo per fornire una descrizione completa. Al contrario, questa sezione fornisce le aree principali da tenere in considerazione quando ottimizzare i modelli.

### <a name="optimizing-power-bi-hosted-models"></a>Ottimizzazione di Power BI ospitati modelli

Ottimizzare i modelli ospitati in una capacità Premium può essere ottenuto a livello di modello e le origini dati.

Prendere in considerazione la possibilità di ottimizzazione per un modello di importazione:

![Possibilità di ottimizzazione per un modello di importazione](media/service-premium-capacity-optimize/import-model-optimizations.png)

A livello di origine dati:

- Origini dati relazionali possono essere ottimizzate per garantire l'aggiornamento più rapido possibile da pre-l'integrazione di dati, applicare indici appropriati, la definizione di partizioni della tabella che si allineano ai periodi di aggiornamento incrementale e materializzare i calcoli (invece di calcolato tabelle e colonne del modello) o l'aggiunta di logica di calcolo per le visualizzazioni.
- Origini dati relazionali possono essere pre-integrate con archivi relazionali.
- Assicurarsi che i gateway sono risorse sufficienti, preferibilmente prevede computer dedicati con sufficiente larghezza di banda di rete e in stretta vicinanza alle origini dati.

A livello del modello:

- Progettazioni query di Power Query possono ridurre al minimo o rimuovere trasformazioni complesse e in particolare quelli che uniscono diverse origini dati (data warehouse ottenere questo risultato durante la fase di Extract-Transform-Load). Inoltre, garantire tale origine dati appropriata i livelli di privacy sono impostate, ciò consente di evitare che richiedono Power BI caricare tutti i risultati per produrre un risultato combinato per tutte le query.
- La struttura del modello determina i dati da caricare e ha un impatto diretto sulle dimensioni del modello. Si può essere progettato per evitare il caricamento di dati non necessari, rimuovendo le colonne, la rimozione di righe (in particolare i dati cronologici) oppure caricando i dati di riepilogo (a scapito di caricamento di dati dettagliati). Tramite la rimozione di colonne con cardinalità elevata (in particolare sulle colonne di testo) che non archiviare né comprimere in modo molto efficiente, è possibile riduzione delle dimensioni notevoli.
- Le prestazioni delle query del modello possono essere migliorate tramite la configurazione di relazioni per direzione singola a meno che non è presente un motivo valido per consentire il filtro bidirezionale. È consigliabile usare anche il [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) (funzione) anziché il filtro bidirezionale.
- Tabelle di aggregazione possono ottenere query più veloci le risposte caricando pre-riepilogo dati, tuttavia, ciò aumenta la dimensione del modello e risultato in tempi più lunghi di aggiornamento. In genere, le tabelle di aggregazione devono essere riservate per i modelli di dimensioni molto grandi o progetti di modelli composto.
- Tabelle e colonne calcolate aumentano le dimensioni del modello e comportare tempi di aggiornamento. In generale, una dimensioni di archiviazione inferiori e tempi di aggiornamento può essere ottenute quando i dati viene materializzati o calcolati nell'origine dati. In caso contrario, utilizzano colonne personalizzate di Power Query può offrire la compressione di archiviazione migliorata.
- Potrebbero esserci opportunità per ottimizzare le espressioni DAX per misure e le regole a livello di riga, ad esempio la riscrittura per la logica per evitare costose formule
- L'aggiornamento incrementale può notevolmente ridurre i tempi di aggiornamento e conservare la memoria e CPU. L'aggiornamento incrementale può essere configurato anche per rimuovere i dati cronologici mantenendo le dimensioni dei modelli trim.
- Un modello può essere riprogettato come due modelli quando sono presenti modelli di query diversi e in conflitto. Ad esempio, alcuni report le aggregazioni di alto livello presente sulle tutti cronologia e può tollerare la latenza di 24 ore. Altri report sono in questione con i dati di oggi e richiedono l'accesso granulare a singole transazioni. Invece di progettazione un solo modello per soddisfare tutti i report, creare due modelli ottimizzati per ogni requisito.

Prendere in considerazione la possibilità di ottimizzazione per un modello DirectQuery. Come il modello genera richieste di query all'origine dati sottostante, ottimizzazione dell'origine dati è essenziale alla fornitura di query del modello reattivo.

 ![Possibilità di ottimizzazione per un modello DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

A livello di origine dati:

- L'origine dati può essere ottimizzato per garantire il più rapido possibile l'esecuzione di query da pre-integrazione di dati (che non sono possibili a livello del modello), applicare indici appropriati, la definizione di partizioni della tabella, la materializzazione riepilogo dati (con le viste indicizzate), e riducendo al minimo la quantità di calcolo. Un'esperienza ottimale si ottiene quando le query pass-through è necessario filtrare solo ed eseguire degli inner join tra tabelle indicizzate o le viste.
- Assicurarsi che i gateway sono risorse sufficienti, preferibilmente prevede computer dedicati con sufficiente larghezza di banda di rete e in stretta vicinanza all'origine dati.

A livello del modello:

- Query di Power Query progettazioni preferibilmente non applicare alcuna trasformazione - tentare in altro modo mantenere le trasformazioni di inattività minimo.
- Le prestazioni delle query del modello possono essere migliorate tramite la configurazione di relazioni per direzione singola a meno che non è presente un motivo valido per consentire il filtro bidirezionale. Inoltre, modellare relazioni devono essere configurate per presupporre viene applicata l'integrità referenziale (in questo caso) e comporterà la query di origine dati usando gli inner join più efficiente (invece di outer join).
- Evitare di creare colonne personalizzate di query di Power Query o una colonna calcolata del modello - materializzare questi criteri nell'origine dati, quando possibile.
- Potrebbero esserci opportunità per ottimizzare le espressioni DAX per misure e le regole a livello di riga, ad esempio la riscrittura per la logica per evitare costose formule.

Prendere in considerazione la possibilità di ottimizzazione per un modello composito. È importante ricordare che un modello composito consente una combinazione di importazione e DirectQuery tabelle.

![Possibilità di ottimizzazione per un modello composito](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- In genere, l'ottimizzazione per i modelli di Import che di DirectQuery si applicano per le tabelle del modello composito che usano queste modalità di archiviazione.
- In genere, possono ottenere una progettazione bilanciata configurando tabelle tipo di dimensione, che rappresentano le entità aziendali, come Dual-tipo di fact e modalità di tabelle di archiviazione (spesso tabelle di grandi dimensioni che rappresentano informazioni operative) come modalità di archiviazione DirectQuery. Modalità di archiviazione duale significa entrambi importazione e DirectQuery le modalità di archiviazione e ciò consente al servizio Power BI determinare la modalità di archiviazione più efficiente da usare durante la generazione di una query nativa per pass-through.
- Assicurarsi che i gateway avere risorse sufficienti, preferibilmente prevede computer dedicati con sufficiente larghezza di banda di rete e in stretta vicinanza alle origini dati
- Le tabelle con aggregazioni configurate come modalità di archiviazione di importazione è in grado di offrire miglioramenti delle prestazioni di query significativo quando utilizzato per riepilogare le tabelle dei fatti-type con modalità archiviazione DirectQuery. In questo caso, le tabelle di aggregazione aumenterà le dimensioni del modello e aumentare la durata dell'aggiornamento, e spesso si tratta di un compromesso accettabile per le query più veloci.

### <a name="optimizing-externally-hosted-models"></a>Ottimizzazione esternamente ospitati modelli

Molte possibilità di ottimizzazione illustrati nel [ottimizzazione di Power BI ospitati modelli](#optimizing-power-bi-hosted-models) sezione si applicano anche ai modelli sviluppati con Azure Analysis Services e SQL Server Analysis Services. Le eccezioni non crittografate sono determinate funzionalità che non sono attualmente supportate, inclusi i modelli compositi e tabelle di aggregazione.

Un'altra considerazione per i set di dati ma ospitato è il database di hosting in relazione al servizio Power BI. Per Azure Analysis Services, ciò significa creare la risorsa di Azure nella stessa area come tenant di Power BI (area iniziale). Per SQL Server Analysis Services, per IaaS, ciò significa che ospita la VM nella stessa area e in locale, significa assicurare un programma di installazione di gateway efficiente.

Per inciso, potrebbe essere interessante notare che i database di Azure Analysis Services e i database tabulari di SQL Server Analysis Services richiedono che i propri modelli caricare completamente in memoria e che rimangano presenti in qualsiasi momento per supportare l'esecuzione di query. Analogamente al servizio Power BI, dovrà essere memoria sufficiente per l'aggiornamento se il modello deve rimanere online durante l'aggiornamento. A differenza del servizio Power BI, non è previsto che i modelli sono obsoleti automaticamente da e verso memoria in base all'utilizzo. Power BI Premium, di conseguenza, offre un approccio più efficiente per massimizzare l'esecuzione di query del modello con l'utilizzo di memoria inferiore.

## <a name="capacity-planning"></a>Pianificazione della capacità

La dimensione di una capacità Premium determina la memoria disponibile e le risorse del processore e limiti imposti per la capacità. Anche il numero di capacità Premium è un fattore importante, come la creazione di Premium più capacità può consentire di isolare i carichi di lavoro tra loro. Si noti che l'archiviazione è di 100 TB per ogni nodo di capacità e questa condizione potrebbe essere più che sufficiente per qualsiasi carico di lavoro.

Determinazione della dimensione e il numero di capacità Premium può essere difficile, soprattutto per le capacità iniziale, che si crea. Il primo passaggio quando il ridimensionamento delle capacità consiste nel comprendere la media del carico di lavoro che rappresentano previsto l'utilizzo quotidiano. È importante comprendere che non tutti i carichi di lavoro sono uguali. Ad esempio, a un estremo di una gamma - 100 utenti simultanei, l'accesso a una singola pagina che contiene un singolo oggetto visivo è facile ottenere. Ancora - a altra estremità dello spettro - 100 utenti simultanei che accedono ai 100 report diversi, ognuno con 100 oggetti visivi nella pagina del report, sta per effettuare richieste molto diverse delle risorse di capacità.

Gli amministratori della capacità, pertanto è necessario prendere in considerazione molti fattori specifici per l'ambiente, contenuto e l'utilizzo previsto. L'obiettivo di override è ottimizzare l'utilizzo della capacità e offrire tempi di query coerenti, tempi di attesa accettabile e percentuali di rimozione. Fattori da prendere in considerazione possono includere:

- **Le caratteristiche di dimensioni e i dati del modello** -modelli di importazione devono essere completamente caricati nella memoria per consentire l'esecuzione di query o l'aggiornamento. I set di dati di LC/DQ può richiedere tempi significativi del processore e memoria probabilmente significativa a valutare misure complesse o le regole a livello di riga. Velocità effettiva delle query LC/DQ, memoria e processore dimensione sono vincolate dalle dimensioni della capacità.
- **Modelli attivi simultanei** -l'esecuzione di query simultanee di importazione diversi modelli distribuirà migliore della velocità di risposta e le prestazioni quando rimangono in memoria. Deve essere presente memoria sufficiente per ospitare tutti i modelli sottoposti frequentemente a query, con ulteriore memoria per consentire loro l'aggiornamento.
- **Aggiornamento dei modelli importazione** -il tipo di aggiornamento (completa o incrementale), durata e la complessità delle query di Power Query e tabella/colonna calcolata per la logica può influire sulla memoria e in particolare l'utilizzo del processore. Gli aggiornamenti simultanei sono limitati dalle dimensioni della capacità (1,5 x backend v-core, arrotondati per eccesso).
- **Query simultanee** -numerose query simultanee può causare in risponde segnala quando processore o LC/DQ connessioni supera il limite di capacità. Questo avviene soprattutto per le pagine del report che includono numerosi oggetti visivi.
- **Flussi di dati e report impaginati** -la capacità può essere configurata per supportare flussi di dati e report impaginati con ognuno dei quali richiede una configurabile percentuale massima di memoria di capacità. Memoria viene allocata dinamicamente per flussi di dati, ma viene allocata in modo statico per i report impaginati.

Oltre a questi fattori, gli amministratori della capacità possono provare a creare più capacità. Le capacità più consentono l'isolamento dei carichi di lavoro e possono essere configurate per verificare che i carichi di lavoro con priorità hanno garantito di risorse. Ad esempio, le capacità di due possono essere create per separare i carichi di lavoro cruciali da carichi di lavoro di BI (SSBI) self-service. La capacità di business-critical è utilizzabile per isolare i modelli di grandi dimensioni aziendali fornendo loro con risorse garantite, con accesso consentita solo ai reparti IT di creazione. La capacità SSBI utilizzabile per ospitare un numero crescente di modelli più piccoli, con accesso concesso ai business analyst. La capacità SSBI potrebbe verificarsi in momenti attese query o aggiornamento sono tollerabile.

Nel corso del tempo, gli amministratori della capacità possono bilanciare le aree di lavoro tra le capacità per lo spostamento del contenuto tra le aree di lavoro o le aree di lavoro tra le capacità e aumentando le capacità verso l'alto o verso il basso. In generale, per modelli più grandi di host scalabilità verticale e per una concorrenza più elevata è scalare orizzontalmente.

È importante ricordare che l'acquisto di una licenza fornisce al tenant memorie centrali virtuali. L'acquisto di una **P3** sottoscrizione può essere utilizzata per crearne uno, o fino a quattro le capacità Premium, vale a dire 1 x P3 o 2x P2 o 4 x P1. Inoltre, prima upsizing una capacità di P2 a una capacità di P3, possa essere presi in considerazione la suddivisione di memorie centrali virtuali per creare due le capacità di P1.

## <a name="testing-approaches"></a>Test di approcci

Una volta che viene stabilita una dimensioni della capacità, il test può essere eseguito mediante la creazione di un ambiente controllato. Un'opzione economica e pratica consiste nel creare una capacità di Azure (SKU), notare che una capacità di P1 è la stessa dimensione una capacità A4, con P2 e P3 capacità le stesse dimensioni di capacità di A5 e A6, rispettivamente. Funzionalità di Azure è possibile creare rapidamente e vengono fatturati su base oraria. Pertanto, una volta completato il test, possano essere facilmente eliminate per arrestare l'addebito dei costi.

Il contenuto di prova può essere aggiunto a aree di lavoro create la capacità di Azure e come un singolo utente può quindi eseguire i report per generare un carico di lavoro realistico e rappresentativo di query. Se sono presenti modelli di importazione, un aggiornamento per ogni modello deve essere eseguito anche. Strumenti di monitoraggio sono quindi utilizzabile per esaminare tutte le metriche per comprendere l'utilizzo delle risorse.

È importante che i test siano ripetibili. Test da eseguire più volte e deve recapitare approssimativamente lo stesso risultato ogni volta. Una media di questi risultati è utilizzabile per estrapolare e stimare il carico di lavoro in condizioni di produzione reale.

Per generare un test di stress, si consiglia di sviluppare un'applicazione per simulare un carico di lavoro realistico di test di carico. Le specifiche di come ottenere questo risultato non rientrano nell'ambito di questo articolo. Per altre informazioni con un esempio di codice, vedere la [caricare il test delle applicazioni Power BI con Visual Studio load test](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinar.

## <a name="acknowledgements"></a>Riconoscimenti

Questo articolo è stato scritto da Peter Myers, MVP di piattaforma dei dati e indipendenti esperti di Business Intelligence con [bit per bit soluzioni](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Scenari di capacità Premium](service-premium-capacity-scenarios.md)   
  
Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

||||||