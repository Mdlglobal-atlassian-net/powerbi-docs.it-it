---
title: Relazioni nei modelli in Power BI Desktop
description: Introduce la teoria sulle relazioni nei modelli in Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 56ff7d09530030d1a1ae046a3439022cbf638b9d
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760573"
---
# <a name="create-model-relationships-in-power-bi-desktop"></a>Creare relazioni di modelli in Power BI Desktop

Questo articolo è destinato all'importazione dei modellatori di dati usati in Power BI Desktop. Si tratta di un importante argomento di progettazione del modello essenziale per la distribuzione di modelli intuitivi, accurati e ottimali.

Per una discussione più approfondita sulla progettazione ottimale del modello, inclusi i ruoli e le relazioni delle tabelle, vedere l'articolo [Informazioni su uno schema a stella e sull'importanza di questo schema per Power BI](guidance/star-schema.md).

## <a name="relationship-purpose"></a>Scopo delle relazioni

In poche parole, le relazioni di Power BI propagano i filtri applicati alle colonne delle tabelle del modello in altre tabelle del modello. I filtri vengono propagati a condizione che esista un percorso di relazione da seguire, che può comportare la propagazione in più tabelle.

I percorsi di relazione sono deterministici, vale a dire che i filtri vengono sempre propagati nello stesso modo e senza variazioni casuali. Tuttavia, le relazioni possono essere disabilitate o avere un contesto di filtro modificato dai calcoli del modello che usano particolari funzioni DAX. Per altre informazioni, vedere l'argomento [Funzioni DAX rilevanti](#relevant-dax-functions) più avanti in questo articolo.

> [!IMPORTANT]
> È importante comprendere che le relazioni dei modelli non applicano l'integrità dei dati. Per altre informazioni, vedere l'argomento [Valutazione delle relazioni](#relationship-evaluation) più avanti in questo articolo. In questo argomento viene illustrato il comportamento delle relazioni dei modelli quando si verificano problemi di integrità dei dati.

Vediamo come le relazioni propagano i filtri con un esempio animato.

![Esempio animato della propagazione dei filtri delle relazioni](media/desktop-relationships-understand/animation-filter-propagation.gif)

In questo esempio il modello è costituito da quattro tabelle: **Category**, **Product**, **Year** e **Sales**. La tabella **Category** è correlata alla tabella **Product** e la tabella **Product** è correlata alla tabella **Sales**. Anche la tabella **Year** è correlata alla tabella **Sales**. Tutte le relazioni sono uno-a-molti (i cui dettagli vengono descritti più avanti in questo articolo).

Una query, forse generata da un oggetto visivo scheda di Power BI, richiede la quantità totale di vendite per gli ordini di vendita effettuati per una singola categoria, **Cat-A**e per un singolo anno **CY2018**. Questo è il motivo per cui è possibile visualizzare i filtri applicati alle tabelle **Category** e **Year**. Il filtro sulla tabella **Category** viene propagato alla tabella **Product** per isolare due prodotti assegnati alla categoria **Cat-A**. I filtri della tabella **Product** vengono quindi propagati alla tabella **Sales** per isolare solo due righe di vendita per questi prodotti. Queste due righe di vendita rappresentano le vendite di prodotti assegnati alla categoria **Cat-A**. La relativa quantità combinata è di 14 unità. Allo stesso tempo, il filtro della tabella **Year** viene propagato per filtrare ulteriormente la tabella **Sales**, ottenendo solo una riga di vendita relativa ai prodotti assegnati alla categoria **Cat-A** e che è stata ordinata nell'anno **CY2018**. Il valore della quantità restituito dalla query è di 11 unità. Si noti che quando si applicano più filtri a una tabella, come la tabella **Sales** in questo esempio, si tratta sempre di un'operazione AND, che richiede che tutte le condizioni siano vere (true).

### <a name="disconnected-tables"></a>Tabelle disconnesse

È insolito che una tabella del modello non sia correlata a un'altra tabella del modello. Una tabella di questo tipo in una progettazione di un modello valida può essere descritta come _tabella disconnessa_. Una tabella disconnessa non è progettata per propagare i filtri ad altre tabelle del modello. Viene invece usata per accettare l'input dell'utente (ad esempio con un oggetto visivo filtro dei dati), consentendo ai calcoli del modello di usare il valore di input in modo significativo. Si consideri, ad esempio, una tabella disconnessa caricata con un intervallo di valori di tassi di cambio. Se un filtro viene applicato per filtrare in base a un singolo valore di tasso, il valore può essere usato da un'espressione di misura per convertire i valori delle vendite.

Il parametro analisi di simulazione di Power BI Desktop è una funzionalità che consente di creare una tabella disconnessa. Per altre informazioni, vedere l'articolo [Creare e usare un parametro analisi di simulazione per visualizzare le variabili in Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Proprietà della relazione

Una relazione del modello consente di correlare una colonna di una tabella a una colonna di un'altra tabella. Esiste un unico caso specifico in cui questo requisito non è vero e vale solo per le relazioni tra più colonne nei modelli DirectQuery. Per altre informazioni, vedere l'articolo sulla funzione DAX [COMBINEVALUES](/dax/combinevalues-function-dax).

> [!NOTE]
> Non è possibile correlare una colonna a un'altra colonna _della stessa tabella_. Ciò è talvolta confuso con la possibilità di definire un vincolo di chiave esterna di un database relazionale, ovvero una tabella autoreferenziale. Questo concetto di database relazionale può essere usato per archiviare le relazioni padre-figlio (ad esempio, ogni record di un dipendente è correlato al diretto superiore del dipendente). La generazione di una gerarchia del modello basata su questo tipo di relazione non può essere risolta creando relazioni del modello. Per ottenere questo risultato, vedere l'articolo relativo alle [funzioni padre e figlio](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Cardinalità

Ogni relazione del modello deve essere definita con un tipo di cardinalità. Sono disponibili quattro opzioni per il tipo di cardinalità, che rappresentano le caratteristiche dei dati delle colonne correlate con "da" e "a". Il lato "uno" indica che la colonna contiene valori univoci. Il lato "due" indica che la colonna può contenere valori duplicati.

> [!NOTE]
> Se un'operazione di aggiornamento dati prova a caricare valori duplicati in una colonna lato "uno", l'intero aggiornamento dei dati avrà esito negativo.

Le quattro opzioni, insieme alle relative notazioni abbreviate, sono descritte nell'elenco puntato seguente:

- Uno-a-molti (1:\*)
- Molti-a-uno (\*:1)
- Uno-a-uno (1:1)
- Molti-a-molti (\*:\*)

Quando si crea una relazione in Power BI Desktop la finestra di progettazione rileva e imposta automaticamente il tipo di cardinalità. La finestra di progettazione può eseguire questa operazione perché esegue una query sul modello per sapere quali colonne contengono valori univoci. Per i modelli di importazione usa le statistiche di archiviazione interna; per i modelli DirectQuery invia query di profilatura all'origine dati. A volte, tuttavia, può sbagliare. Ciò si verifica perché le tabelle devono essere ancora caricate con i dati o perché le colonne che si prevede contengono valori duplicati contengono attualmente valori univoci. In entrambi i casi, è possibile aggiornare il tipo di cardinalità a condizione che le colonne lato "uno" contengano valori univoci (o che la tabella debba ancora essere caricata con le righe di dati).

Le opzioni di cardinalità **Uno-a-molti** e **Molti-a-uno** sono essenzialmente identiche e sono anche i tipi di cardinalità più comuni.

Quando si configura una relazione Uno-a-molti o Molti-a-uno, si sceglie quello che corrisponde all'ordine in cui sono state correlate le colonne. Si consideri come configurare la relazione dalla tabella **Product** alla tabella **Sales** usando la colonna **ProductID** presente in ogni tabella. Il tipo di cardinalità sarà _Uno-a-molti_, perché la colonna **ProductID** nella tabella **Product** contiene valori univoci. Se le tabelle vengono correlate nella direzione inversa, da **Sales** a **Product**, la cardinalità sarà _Molti-a-uno_.

Un relazione **Uno-a-uno** indica che entrambe le colonne contengono valori univoci. Questo tipo di cardinalità non è comune ed è probabile che rappresenti una progettazione del modello non ottimale a causa dell'archiviazione di dati ridondanti.<!-- For guidance on using this cardinality type, see the [One-to-one relationship guidance](guidance/relationships-one-to-one) article.-->

Un relazione **Molti-a-molti** indica che entrambe le colonne possono contenere valori duplicati. Questo tipo di cardinalità viene usato raramente. È in genere utile quando si progettano requisiti di modelli complessi. Per istruzioni sull'uso di questo tipo di cardinalità, vedere [Linee guida per le relazioni molti-a-molti](guidance/relationships-many-to-many.md).

> [!NOTE]
> Il tipo di cardinalità Molti-a-molti non è attualmente supportato per i modelli sviluppati per il Server di report di Power BI.

> [!TIP]
> Nella visualizzazione modello di Power BI Desktop è possibile interpretare il tipo di cardinalità di una relazione esaminando gli indicatori (1 o \*) su entrambi i lati della linea della relazione. Per determinare quali colonne sono correlate, è necessario selezionare o passare il puntatore del mouse sulla linea della relazione per evidenziare le colonne.

### <a name="cross-filter-direction"></a>Direzione filtro incrociato

Ogni relazione del modello deve essere definita con una direzione filtro incrociato. La selezione determina la direzione o le direzioni in cui i filtri verranno propagati. Le opzioni di filtro incrociato possibili dipendono dal tipo di cardinalità.

| Tipo di cardinalità | Opzioni di filtro incrociato |
| --- | --- |
| Uno-a-molti (o Molti-a-uno) | Singola<br>Entrambi |
| Uno-a-uno | Entrambi |
| Molti-a-molti | Single (da Table1 a Table2)<br>Single (da Table2 a Table1)<br>Entrambi |

La direzione filtro incrociato _Singola_ significa "singola direzione" e _Entrambe_ significa "entrambe le direzioni". Una relazione che consente di filtrare in entrambe le direzioni viene comunemente descritta come _bidirezionale_.

Per le relazioni Uno-a-molti, la direzione filtro incrociato è sempre dal lato "uno" e, facoltativamente, dal lato "molti" (bidirezionale). Per le relazioni Uno-a-uno, la direzione filtro incrociato è sempre da entrambe le tabelle. Infine, per le relazioni Molti-a-molti, la direzione filtro incrociato può essere da una delle due tabelle o da entrambe le tabelle. Si noti che quando il tipo di cardinalità include un lato "uno", i filtri vengono sempre propagati da tale lato.

Quando la direzione filtro incrociato è impostata su **Entrambe**, è disponibile una proprietà aggiuntiva per applicare il filtro bidirezionale quando vengono applicate le regole di sicurezza a livello di riga. Per altre informazioni sulla sicurezza a livello di riga, vedere l'articolo [Sicurezza a livello di riga con Power BI Desktop](desktop-rls.md).

La modifica della direzione filtro incrociato della relazione, inclusa la disabilitazione della propagazione del filtro, può essere eseguita anche tramite un calcolo del modello. Per ottenere questo risultato, è possibile usare la funzione DAX [CROSSFILTER](/dax/crossfilter-function).

Le relazioni bidirezionali possono avere un impatto negativo sulle prestazioni. Inoltre, il tentativo di configurare una relazione bidirezionale potrebbe provocare percorsi di propagazione del filtro ambigui. In questo caso, Power BI Desktop potrebbe non riuscire a eseguire il commit della modifica della relazione e verrà generato un avviso con un messaggio di errore. In alcuni casi, tuttavia, Power BI Desktop può consentire di definire percorsi di relazione ambigui tra le tabelle. Le regole di precedenza che influiscono sul rilevamento dell'ambiguità e sulla risoluzione del percorso sono descritte più avanti in questo articolo nell'argomento [Regole di precedenza](#precedence-rules).

Si consiglia di usare il filtro bidirezionale solo se necessario.<!-- For guidance on bi-directional filtering, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

> [!TIP]
> Nella visualizzazione modello di Power BI Desktop è possibile interpretare la direzione filtro incrociato di una relazione notando le frecce lungo la linea della relazione. Una singola freccia rappresenta un filtro a direzione singola nella direzione della freccia; una doppia freccia rappresenta una relazione bidirezionale.

### <a name="make-this-relationship-active"></a>Imposta come relazione attiva

Tra due tabelle del modello può essere presente un solo percorso di propagazione del filtro attivo. Tuttavia, è possibile introdurre percorsi di relazione aggiuntivi, anche se queste relazioni devono essere tutte configurate come _inattive_. Le relazioni inattive possono essere rese attive solo durante la valutazione del calcolo di un modello. Per ottenere questo risultato, è possibile usare la funzione DAX [USERELATIONSHIP](/dax/userelationship-function-dax).

<!--For guidance on defining inactive relationships, see the [Active vs inactive relationship guidance](guidance/relationships-active-inactive) article.-->

> [!TIP]
> Nella visualizzazione modello di Power BI Desktop è possibile interpretare lo stato attivo o inattivo di una relazione. Una relazione attiva è rappresentata da una linea continua; una relazione inattiva è rappresentata da una linea tratteggiata.

### <a name="assume-referential-integrity"></a>Considera integrità referenziale

La proprietà _Considera integrità referenziale_ è disponibile solo per le relazioni Uno-a-molti e Uno-a-uno tra due tabelle in modalità di archiviazione DirectQuery basate sulla stessa origine dati. Se abilitata, le query native inviate all'origine dei dati creeranno un join tra le due tabelle usando un INNER JOIN anziché un OUTER JOIN. In generale, l'abilitazione di questa proprietà migliora le prestazioni delle query, anche se ciò dipende dalle specifiche dell'origine dati.

Questa proprietà deve essere sempre abilitata quando esiste un vincolo di chiave esterna del database tra le due tabelle. Quando non esiste un vincolo di chiave esterna, è comunque possibile abilitare la proprietà, a condizione che esista l'integrità dei dati.

> [!IMPORTANT]
> Se l'integrità dei dati dovesse essere compromessa, l'inner join eliminerà le righe non corrispondenti tra le tabelle. Si consideri, ad esempio, la tabella **Sales** di un modello con un valore di colonna **ProductID** che non esisteva nella tabella **Product** correlata. La propagazione del filtro dalla tabella **Product** alla tabella **Sales** eliminerà le righe di vendita per i prodotti sconosciuti. Questo comporterebbe una sottovalutazione dei risultati delle vendite.
>
> Per altre informazioni, vedere l'articolo [Considerare le impostazioni di integrità referenziale in Power BI Desktop](desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Funzioni DAX rilevanti

Sono disponibili diverse funzioni DAX rilevanti per le relazioni del modello. Ogni funzione è descritta brevemente nell'elenco puntato seguente:

- [RELATED](/dax/related-function-dax): recupera il valore dal lato "uno".
- [RELATEDTABLE](/dax/relatedtable-function-dax): recupera una tabella di righe dal lato "molti".
- [USERELATIONSHIP](/dax/userelationship-function-dax): impone l'utilizzo di una relazione del modello inattiva specifica.
- [CROSSFILTER](/dax/crossfilter-function): modifica la direzione filtro incrociato della relazione (in una o entrambe) oppure disabilita la propagazione del filtro (nessuno).
- [COMBINEVALUES](/dax/combinevalues-function-dax): unisce due o più stringhe di testo in una sola. Lo scopo di questa funzione è supportare le relazioni a più colonne nei modelli DirectQuery.
- [TREATAS](/dax/treatas-function): applica il risultato di un'espressione di tabella come i filtri alle colonne di una tabella non correlata.
- [Funzioni padre e figlio](/dax/parent-and-child-functions-dax): famiglia di funzioni correlate che è possibile usare per generare colonne calcolate per naturalizzare una gerarchia padre-figlio. Queste colonne possono quindi essere usate per creare una gerarchia a livello fisso.

## <a name="relationship-evaluation"></a>Valutazione della relazione

Le relazioni del modello, dal punto di vista della valutazione, vengono classificate come _forti_ o _deboli_. Non si tratta di una proprietà della relazione configurabile. Viene infatti dedotta dal tipo di cardinalità e dall'origine dati delle due tabelle correlate. È importante comprendere il tipo di valutazione poiché potrebbero verificarsi implicazioni o conseguenze sulle prestazioni in caso di compromissione dell'integrità dei dati. Queste implicazioni e conseguenze sull'integrità sono descritte in questo argomento.

Per prima cosa, è necessaria una teoria di modellazione per comprendere completamente le valutazioni delle relazioni.

Un modello di importazione o DirectQuery genera tutti i dati dalla cache Vertipaq o dal database di origine. In entrambi i casi, Power BI è in grado di determinare l'esistenza di un lato "uno" di una relazione.

Un modello composito, tuttavia, può essere costituito da tabelle che usano diverse modalità di archiviazione (importazione, DirectQuery o doppia) o più origini DirectQuery. Ogni origine, inclusa la cache Vertipaq dei dati di importazione, viene considerata un'_isola di dati_. Le relazioni tra modelli possono quindi essere classificate come _all'interno dell'isola_ o _tra isole_. Una relazione all'interno dell'isola è una relazione che mette in correlazione due tabelle all'interno di un'isola di dati, mentre una relazione tra isole mette in correlazione le tabelle di isole di dati diverse. Si noti che le relazioni nei modelli di importazione o DirectQuery sono sempre all'interno dell'isola.

Vediamo un esempio di un modello composito.

![Esempio di modello composito costituito da due isole](media/desktop-relationships-understand/data-island-example.png)

In questo esempio, il modello composito è costituito da due isole: un'isola di dati Vertipaq e un'isola di dati di origine DirectQuery. L'isola di dati Vertipaq contiene tre tabelle e l'isola di dati di origine DirectQuery contiene due tabelle. Esiste una relazione tra isole per correlare una tabella nell'isola di dati Vertipaq a una tabella nell'isola di dati di origine DirectQuery.

### <a name="strong-relationships"></a>Relazioni forti

Una relazione del modello è _forte_ quando il motore di query è in grado di determinare il lato "uno" della relazione. Ha la conferma che la colonna lato "uno" contiene valori univoci. Tutte le relazioni Uno-a-molti all'interno dell'isola sono relazioni forti.

Nell'esempio seguente sono presenti due relazioni forti, entrambe contrassegnate come **S**. Le relazioni includono la relazione Uno-a-molti contenuta nell'isola Vertipaq e la relazione Uno-a-molti contenuta nell'origine DirectQuery.

![Esempio di modello composito costituito da due isole con relazioni forti contrassegnate](media/desktop-relationships-understand/data-island-example-strong.png)

Per i modelli di importazione, in cui tutti i dati vengono archiviati nella cache Vertipaq, viene creata una struttura dei dati per ogni relazione forte al momento dell'aggiornamento dati. Le strutture dei dati sono costituite da mapping indicizzati di tutti i valori da colonna a colonna e hanno lo scopo di accelerare l'unione di tabelle in fase di query.

In fase di query, le relazioni forti consentono l'_espansione della tabella_. L'espansione della tabella comporta la creazione di una tabella virtuale includendo le colonne native della tabella di base e quindi espandendosi in tabelle correlate. Per le tabelle di importazione, questa operazione viene eseguita nel motore di query; per le tabelle DirectQuery viene eseguita nella query nativa inviata al database di origine (purché la proprietà "Considera integrità referenziale" non sia abilitata). Il motore di query agisce quindi sulla tabella espansa applicando filtri e raggruppando i risultati in base ai valori nelle colonne della tabella espansa.

> [!NOTE]
> Le relazioni inattive vengono espanse anche quando la relazione non viene usata da un calcolo. Le relazioni bidirezionali non hanno alcun effetto sull'espansione della tabella.

Per le relazioni uno-a-molti, l'espansione della tabella si verifica dal lato "molti" al lato "uno" usando la semantica LEFT OUTER JOIN. Quando non esiste un valore corrispondente dal lato "molti" al lato "uno", viene aggiunta una riga virtuale vuota alla tabella lato "uno".

L'espansione della tabella si verifica anche per le relazioni Uno-a-uno all'interno dell'isola, ma usando la semantica FULL OUTER JOIN. Garantisce che le righe virtuali vuote vengano aggiunte su entrambi i lati, quando necessario.

Le righe virtuali vuote sono effettivamente _membri sconosciuti_. I membri sconosciuti rappresentano violazioni di integrità referenziale in cui il valore del lato "molti" non ha un valore corrispondente del lato "uno". Idealmente, questi spazi vuoti non devono esistere e possono essere eliminati tramite la pulizia o il ripristino dei dati di origine.

Vediamo come funziona l'espansione della tabella con un esempio animato.

![Esempio animato dell'espansione della tabella](media/desktop-relationships-understand/animation-expanded-table.gif)

In questo esempio il modello è costituito da tre tabelle: **Category**, **Product** e **Sales**. La tabella **Category** è correlata alla tabella **Product** con una relazione Uno-a-molti e la tabella **Product** è correlata alla tabella **Sales** con una relazione Uno-a-molti. La tabella **Category** contiene due righe, la tabella **Product** contiene tre righe e le tabelle **Sales** contiene cinque righe. Sono presenti valori corrispondenti in entrambi i lati di tutte le relazioni, il che significa che non esistono violazioni di integrità referenziale. Viene rilevata una tabella espansa in fase di query. La tabella è costituita dalle colonne di tutte e tre le tabelle. Si tratta in realtà di una prospettiva denormalizzata dei dati contenuti nelle tre tabelle. Una nuova riga viene aggiunta alla tabella **Sales** e ha un valore identificatore produzione (9) che non ha un valore corrispondente nella tabella **Product**. Si tratta di una violazione dell'integrità referenziale. Nella tabella espansa la nuova riga contiene valori (vuoti) per le colonne della tabella **Category** e **Product**.

### <a name="weak-relationships"></a>Relazioni deboli

Una relazione del modello è _debole_ quando non esiste un lato "uno" garantito. Ciò può avvenire per due motivi:

- La relazione usa un tipo di cardinalità Molti-a-molti (anche se una o entrambe le colonne contengono valori univoci)
- La relazione è tra le isole (che può avvenire solo per i modelli compositi)

Nell'esempio seguente sono presenti due relazioni deboli, entrambe contrassegnate come **W**. Le due relazioni includono la relazione Molti-a-molti contenuta nell'isola Vertipaq e la relazione Uno-a-molti tra le isole.

![Esempio di modello composito costituito da due isole con relazioni deboli contrassegnate](media/desktop-relationships-understand/data-island-example-weak.png)

Per i modelli di importazione, le strutture dei dati non vengono mai create per le relazioni deboli. Ciò significa che i join di tabella devono essere risolti in fase di query.

L'espansione della tabella non viene mai eseguita per le relazioni deboli. I join di tabella vengono realizzati usando la semantica INNER JOIN e per questo motivo non vengono aggiunte righe virtuali vuote per compensare le violazioni di integrità referenziale.

Sono presenti ulteriori restrizioni relative alle relazioni deboli:

- Non è possibile usare la funzione RELATED DAX per recuperare i valori della colonna lato "uno"
- L'applicazione della sicurezza a livello di riga ha restrizioni topologiche

> [!NOTE]
> Nella visualizzazione modello di Power BI Desktop non è sempre possibile determinare se una relazione del modello è forte o debole. Una relazione Molti-a-molti sarà sempre debole, così come una relazione Uno-a-molti quando è una relazione tra isole. Per determinare se si tratta di una relazione tra isole, sarà necessario esaminare le modalità di archiviazione delle tabelle e le origini dati per ottenere la corretta determinazione.

### <a name="precedence-rules"></a>Regole di precedenza

Le relazioni bidirezionali possono introdurre più percorsi di propagazione del filtro, e pertanto ambigui, tra le tabelle del modello. Nell'elenco seguente vengono illustrate le regole di precedenza usate da Power BI per il rilevamento dell'ambiguità e la risoluzione del percorso:

1. Relazioni Molti-a-uno e Uno-a-uno, incluse le relazioni deboli
2. Relazioni molti-a-molti
3. Relazioni bidirezionali, in direzione inversa (ovvero dal lato "molti")

### <a name="performance-preference"></a>Preferenza per le prestazioni

Nell'elenco seguente vengono ordinate le prestazioni di propagazione del filtro, dalle prestazioni più veloci a quelle più lente:

1. Relazioni Uno-a-molti tra isole
2. Relazioni di cardinalità Molti-a-molti
3. Relazioni del modello Molti-a-molti ottenute con una tabella intermedia e che implica almeno una relazione bidirezionale
4. Relazioni tra isole

<!--For further information and guidance on many-to-many relationships, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

## <a name="next-steps"></a>Passaggi successivi

- [Informazioni su uno schema star e sull'importanza di questo schema per Power BI](guidance/star-schema.md)
- [Linee guida per le relazioni molti-a-molti](guidance/relationships-many-to-many.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
