---
title: Linee guida per le relazioni molti-a-molti
description: Linee guida per lo sviluppo di relazioni nei modelli molti-a-molti.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 8718c67c592bf96d50efed475c0d27b4ec80ca04
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278331"
---
# <a name="many-to-many-relationship-guidance"></a>Linee guida per le relazioni molti-a-molti

Questo articolo è destinato agli autori di modelli di dati che usano Power BI Desktop. Descrive tre diversi scenari di modellazione molti-a-molti. Vengono inoltre fornite indicazioni per la corretta progettazione all'interno dei modelli.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

Esistono, di fatto, tre scenari molti-a-molti, che possono verificarsi quando è necessario:

- [Correlare due tabelle di tipo dimensione](#relate-many-to-many-dimensions)
- [Correlare due tabelle di tipo fatto](#relate-many-to-many-facts)
- [Correlare tabelle di tipo fatto con una granularità più elevata](#relate-higher-grain-facts), quando la tabella di tipo fatto archivia righe con un livello di granularità superiore rispetto alle righe della tabella di tipo dimensione

## <a name="relate-many-to-many-dimensions"></a>Correlare dimensioni molti-a-molti

Si prenda in considerazione il primo tipo di scenario molti-a-molti con un esempio. Lo scenario classico mette in relazione due entità, ovvero clienti bancari e conti bancari. Tenere presente che i clienti possono avere più conti e i conti possono avere più clienti. Quando un conto ha più clienti, questi vengono comunemente definiti _titolari di conti cointestati_.

La creazione di modelli per queste entità è semplice. Una tabella di tipo dimensione archivia i conti e un'altra tabella di tipo dimensione archivia i clienti. Come è tipico delle tabelle di tipo dimensione, in ogni tabella è presente una colonna ID. Per modellare la relazione tra le due tabelle, è necessaria una terza tabella, che viene comunemente detta _tabella di bridging_. In questo esempio lo scopo è archiviare una riga per ogni associazione cliente-conto. È interessante notare che, quando questa tabella contiene solo colonne ID, viene chiamata [_tabella dei fatti senza fatti_](star-schema.md#factless-fact-tables).

Ecco un diagramma del modello semplicistico delle tre tabelle.

![Un diagramma del modello contiene tre tabelle. La progettazione è descritta nel paragrafo seguente.](media/relationships-many-to-many/bank-account-customer-model-example.png)

La prima tabella è denominata **Account** e contiene due colonne: **AccountID** e **Account**. La seconda tabella è denominata **AccountCustomer** e contiene due colonne: **AccountID** e **CustomerID**. La terza tabella è denominata **Customer** e contiene due colonne: **CustomerID** e **Customer**. Non esistono relazioni tra nessuna delle tabelle.

Per correlare le tabelle vengono aggiunte due relazioni uno-a-molti. Di seguito è riportato un diagramma del modello aggiornato delle tabelle correlate. È stata aggiunta una tabella di tipo fatto denominata **Transaction**, che registra le transazioni del conto. La tabella di bridging e tutte le colonne ID sono state nascoste.

![Il diagramma del modello ora contiene quattro tabelle. Per correlare tutte le tabelle sono state aggiunte relazioni uno-a-molti.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

Per semplificare la descrizione del funzionamento della propagazione del filtro delle relazioni, il diagramma del modello è stato modificato in modo da mostrare le righe della tabella.

> [!NOTE]
> Non è possibile visualizzare le righe della tabella nel diagramma del modello di Power BI Desktop. Questa operazione viene eseguita in questo articolo solo per supportare la discussione con esempi chiari.

![Il diagramma del modello visualizza ora le righe della tabella. Nel paragrafo riportato di seguito sono descritti i dettagli delle righe.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

I dettagli delle righe per le quattro tabelle sono descritti nell'elenco puntato seguente:

- La tabella **Account** contiene due righe:
  - **AccountID** 1 per Account-01
  - **AccountID** 2 per Account-02
- La tabella **Customer** contiene due righe:
  - **CustomerID** 91 per Customer-91
  - **CustomerID** 92 per Customer-92
- La tabella **AccountCustomer** contiene tre righe:
  - **AccountID** 1 è associato a **CustomerID** 91
  - **AccountID** 1 è associato a **CustomerID** 92
  - **AccountID** 3 è associato a **CustomerID** 92
- La tabella **Transaction** include tre righe:
  - **Date** 1 gennaio 2019, **AccountID** 1, **Amount** 100
  - **Date** 2 febbraio 2019, **AccountID** 2, **Amount** 200
  - **Date** 3 marzo 2019, **AccountID** 1, **Amount** -25

Si vedrà ora cosa accade quando viene eseguita una query sul modello.

Di seguito sono riportati due oggetti visivi che riepilogano la colonna **Amount** della tabella **Transaction**. Il primo oggetto visivo raggruppa in base all'account, quindi la somma delle colonne **Amount** rappresenta il _saldo del conto_. Il secondo oggetto visivo raggruppa in base al cliente, quindi la somma delle colonne **Amount** rappresenta il _saldo del cliente_.

![I due oggetti visivi del report sono affiancati. Gli oggetti visivi sono descritti nel paragrafo seguente.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

Il primo oggetto visivo è denominato **Account Balance** e contiene due colonne: **Account** e **Amount**. Visualizza il risultato seguente:

- L'importo del saldo di Account-01 è 75
- L'importo del saldo di Account-02 è 200
- Il totale è 275

Il secondo oggetto visivo è denominato **Customer Balance** e contiene due colonne: **Customer** e **Amount**. Visualizza il risultato seguente:

- L'importo del saldo di Customer-91 è 275
- L'importo del saldo di Customer-92 è 275
- Il totale è 275

Una rapida occhiata alle righe della tabella e all'oggetto visivo **Account Balance** rivela che il risultato è corretto, per ogni conto e per l'importo totale, dal momento che ogni raggruppamento di conto comporta una propagazione del filtro alla tabella **Transaction** per tale conto.

Tuttavia, c'è qualcosa di errato nell'oggetto visivo **Customer Balance**. Ogni cliente nell'oggetto visivo **Customer Balance** ha lo stesso saldo del saldo totale. Questo risultato può essere corretto solo se ogni cliente è il titolare di un conto cointestato per ogni conto. Ma non è il caso di questo esempio. Il problema è correlato alla propagazione del filtro, che non arriva alla tabella **Transaction**.

Seguire la direzione del filtro della relazione dalla tabella **Customer** alla tabella **Transaction**. Dovrebbe essere evidente che la relazione tra le tabelle **Account** e **AccountCustomer** si propaga nella direzione errata. La direzione del filtro per questa relazione deve essere impostata su **Entrambi**.

![Il diagramma del modello è stato aggiornato. È stata apportata una sola modifica alla relazione tra le tabelle Account e AccountCustomer. Il filtro si propaga ora in entrambe le direzioni.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![I due stessi oggetti visivi del report sono affiancati. Il primo oggetto visivo non è stato modificato. Il secondo oggetto visivo rivela un risultato diverso ed è descritto nei paragrafi seguenti.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Come previsto, non sono state apportate modifiche all'oggetto visivo **Account Balance**.

L'oggetto visivo **Customer Balance**, tuttavia, visualizza ora il risultato seguente:

- L'importo del saldo di Customer-91 è 75
- L'importo del saldo di Customer-92 è 275
- Il totale è 275

L'oggetto visivo **Customer Balance** ora visualizza un risultato corretto. Seguire la direzione del filtro e verificare autonomamente come sono stati calcolati i saldi del cliente. È inoltre importante comprendere che il totale visualizzato si riferisce a _tutti i clienti_.

Un utente che non ha familiarità con le relazioni del modello potrebbe concludere che il risultato non è corretto e potrebbe chiedersi: _Perché il saldo totale per **Customer-91** e **Customer-92** non è uguale a 350 (75 + 275)?_

Per rispondere a questa domanda occorre comprendere la relazione molti-a-molti. Ogni saldo del cliente può rappresentare l'addizione di più saldi dei conti, quindi i saldi dei clienti _non sono additivi_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Indicazioni per la correlazione di dimensioni molti-a-molti

Per una relazione molti-a-molti tra tabelle di tipo dimensione, sono disponibili le indicazioni seguenti:

- Aggiungere ogni entità correlata molti-a-molti come tabella del modello, assicurandosi che abbia una colonna identificatore univoco (ID)
- Aggiungere una tabella di bridging per archiviare le entità associate
- Creare relazioni uno-a-molti tra le tre tabelle
- Configurare **una** relazione bidirezionale per consentire la propagazione del filtro fino alle tabelle di tipo fatto
- Quando non è appropriato avere valori ID mancanti, impostare la proprietà **Is Nullable** delle colonne ID su FALSE. L'aggiornamento dei dati avrà esito negativo se vengono originati valori mancanti.
- Nascondere la tabella di bridging (a meno che non contenga colonne o misure aggiuntive necessarie per la creazione di report)
- Nascondere eventuali colonne ID non adatte per la creazione di report (ad esempio, quando gli ID sono chiavi sostitutive)
- Se è opportuno lasciare visibile una colonna ID, assicurarsi che si trovi dal lato "uno" della relazione. Nascondere sempre la colonna dal lato "molti". In questo modo si garantiscono prestazioni ottimali per il filtro.
- Per evitare confusione o interpretazioni errate, comunicare le spiegazioni agli utenti del report: è possibile aggiungere descrizioni con caselle di testo o [descrizioni comando dell'intestazione dell'oggetto visivo](report-page-tooltips.md)

Non è consigliabile correlare direttamente tabelle di tipo dimensione molti-a-molti. Questo approccio di progettazione richiede la configurazione di una relazione con una cardinalità molti-a-molti. A livello concettuale, è possibile metterlo in atto, ma implica che le colonne correlate conterranno valori duplicati. Si tratta di una pratica di progettazione ben accettata, tuttavia, che le tabelle di tipo dimensione abbiano una colonna ID. Le tabelle di tipo dimensione devono sempre usare la colonna ID come lato "uno" di una relazione.

## <a name="relate-many-to-many-facts"></a>Correlare fatti molti-a-molti

Il secondo tipo di scenario molti-a-molti implica la correlazione tra due tabelle di tipo fatto. Due tabelle di tipo fatto possono essere correlate direttamente. Questa tecnica di progettazione può essere utile per un'esplorazione dati semplice e rapida. Tuttavia, per maggiore chiarezza, questo approccio di progettazione in genere non è consigliabile. Il motivo sarà illustrato più avanti in questa sezione.

Si prenda in considerazione un esempio che include due tabelle di tipo fatto: **Order** e **Fulfillment**. La tabella **Order** contiene una riga per ogni riga dell'ordine e la tabella **Fulfillment** può contenere zero o più righe per riga dell'ordine. Le righe nella tabella **Order** rappresentano gli ordini di vendita. Le righe nella tabella **Fulfillment** rappresentano gli articoli degli ordini che sono stati spediti. Una relazione molti-a-molti mette in correlazione le due colonne **OrderID**, con propagazione del filtro solo dalla tabella **Order** (**Order** filtra **Fulfillment**).

![Un diagramma del modello contiene due tabelle: Order e Fulfillment. Una relazione molti-a-molti mette in correlazione le due colonne OrderID, filtrando da Order a Fulfillment.](media/relationships-many-to-many/order-fulfillment-model-example.png)

La cardinalità della relazione è impostata su molti-a-molti per supportare l'archiviazione di valori **OrderID** duplicati in entrambe le tabelle. Nella tabella **Order** possono essere presenti valori **OrderID** duplicati perché un ordine può avere più righe. Nella tabella **Fulfillment** possono essere presenti valori **OrderID** duplicati perché gli ordini possono avere più righe e le righe degli ordini possono essere evase da più spedizioni.

Verranno ora esaminate le righe della tabella. Nella tabella **Fulfillment** si noti che le righe degli ordini possono essere evase da più spedizioni (l'assenza di una riga dell'ordine indica che l'ordine è ancora da evadere).

![Il diagramma del modello visualizza ora le righe della tabella. Nel paragrafo riportato di seguito sono descritti i dettagli delle righe.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

I dettagli delle righe per le due tabelle sono descritti nell'elenco puntato seguente:

- La tabella **Order** ha cinque righe:
  - **OrderDate** 1 gennaio 2019, **OrderID** 1, **OrderLine** 1, **ProductID** Prod-A, **OrderQuantity** 5, **Sales** 50
  - **OrderDate** 1 gennaio 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Sales** 80
  - **OrderDate** 2 febbraio 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Sales** 40
  - **OrderDate** 2 febbraio 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Sales** 20
  - **OrderDate** 3 marzo 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Sales** 100
- La tabella **Fulfillment** ha quattro righe:
  - **FulfillmentDate** 1 gennaio 2019, **FulfillmentID** 50, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 2
  - **FulfillmentDate** 2 febbraio 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** 2 febbraio 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** 1 gennaio 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

Si vedrà ora cosa accade quando viene eseguita una query sul modello. Di seguito è riportato un oggetto visivo tabella che confronta le quantità di ordini ed evasioni in base alla colonna **OrderID** della tabella **Order**.

![In un oggetto visivo tabella sono presenti tre colonne: OrderID, OrderQuantity e FulfillmentQuantity. Sono visibili tre righe, una per ogni ordine. OrderID 2 e 3 non sono completamente evase.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

L'oggetto visivo presenta un risultato accurato. Tuttavia, l'utilità del modello è limitata, dal momento che è possibile filtrare o raggruppare solo in base alla colonna **OrderID** della tabella **Order**.

### <a name="relate-many-to-many-facts-guidance"></a>Indicazioni per la correlazione di fatti molti-a-molti

In genere, non è consigliabile correlare due tabelle di tipo fatto direttamente usando la cardinalità molti-a-molti. Il motivo principale è che il modello non garantirà flessibilità nelle modalità di filtro o raggruppamento degli oggetti visivi dei report. Nell'esempio, negli oggetti visivi è possibile filtrare o raggruppare solo in base alla colonna **OrderID** della tabella **Order**. Un ulteriore motivo è correlato alla qualità dei dati. Se i dati sono soggetti a problemi di integrità, è possibile che alcune righe vengano omesse durante l'esecuzione di query a causa della natura della _relazione debole_. Per altre informazioni, vedere [Relazioni di modelli in Power BI Desktop (valutazione della relazione)](../transform-model/desktop-relationships-understand.md#relationship-evaluation).

Anziché correlare direttamente le tabelle di tipo fatto, è consigliabile adottare i principi di progettazione dello [schema star](star-schema.md). A tale scopo, aggiungere tabelle di tipo dimensione. Le tabelle di tipo dimensione vengono quindi correlate alle tabelle di tipo fatto usando relazioni uno-a-molti. Questo approccio di progettazione è affidabile perché offre opzioni di reporting flessibili. Consente infatti di filtrare o raggruppare in base a una qualsiasi delle colonne di tipo dimensione e di riepilogare qualsiasi tabella di tipo fatto correlata.

Si prenda in considerazione una soluzione migliore.

![Un diagramma del modello include sei tabelle: OrderLine, OrderDate, Order, Fulfillment, Product e FulfillmentDate. Tutte le tabelle sono correlate. La progettazione è descritta nel paragrafo seguente.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Tenere presenti le modifiche di progettazione seguenti:

- Il modello ora ha quattro tabelle aggiuntive: **OrderLine**, **OrderDate**, **Product** e **FulfillmentDate**
- Le quattro tabelle aggiuntive sono tutte tabelle di tipo dimensione e le relazioni uno-a-molti mettono in correlazione queste tabelle alle tabelle di tipo fatto
- La tabella **OrderLine** contiene una colonna **OrderLineID**, che rappresenta il valore **OrderID** moltiplicato per 100, più il valore **OrderLine**, un identificatore univoco per ogni riga dell'ordine
- Le tabelle **Order** e **Fulfillment** contengono ora una colonna **OrderLineID** e non contengono più le colonne **OrderID** e **OrderLine**
- La tabella **Fulfillment** contiene ora le colonne **OrderDate** e **ProductID**
- La tabella **FulfillmentDate** è correlata solo alla tabella **Fulfillment**
- Tutte le colonne identificatore univoco sono nascoste

L'applicazione dei principi di progettazione di uno schema star offre i vantaggi seguenti:

- Gli oggetti visivi del report possono _filtrare o raggruppare_ in base a qualsiasi colonna visibile delle tabelle di tipo dimensione
- Gli oggetti visivi del report possono _riepilogare_ qualsiasi colonna visibile delle tabelle di tipo fatto
- I filtri applicati alle tabelle **OrderLine**, **OrderDate** o **Product** verranno propagati a entrambe le tabelle di tipo fatto
- Tutte le relazioni sono uno-a-molti e ogni relazione è una _relazione forte_. I problemi di integrità dei dati non verranno mascherati. Per altre informazioni, vedere [Relazioni di modelli in Power BI Desktop (valutazione della relazione)](../transform-model/desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Correlare fatti con granularità più elevata

Questo scenario molti-a-molti è estremamente diverso dagli altri due già descritti in questo articolo.

Si consideri un esempio che implica l'uso di quattro tabelle: **Date**, **Sales**, **Product** e **Target**. **Date** e **Product** sono tabelle di tipo dimensione e le relazioni uno-a-molti le mettono in correlazione alla tabella di tipo fatto **Sales**. Fino a questo punto, si tratta di una progettazione valida con schema star. Tuttavia, la tabella **Target** deve essere ancora correlata alle altre tabelle.

![Un diagramma del modello include quattro tabelle: Date, Sales, Product e Target. La tabella Target non è correlata a nessun'altra tabella. La progettazione è descritta nel paragrafo seguente.](media/relationships-many-to-many/sales-targets-model-example.png)

La tabella **Target** contiene tre colonne: **Category**, **TargetQuantity** e **TargetYear**. Le righe della tabella rivelano una granularità dell'anno e della categoria di prodotto. In altre parole, le destinazioni, usate per misurare le prestazioni di vendita, vengono impostate ogni anno per ogni categoria di prodotto.

![La tabella Target contiene tre colonne: TargetYear, Category e TargetQuantity. Sei righe registrano le destinazioni per gli anni 2019 e 2020, ognuna per tre categorie.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Poiché la tabella **Target** archivia i dati a un livello superiore rispetto alle tabelle di tipo dimensione, non è possibile creare una relazione uno-a-molti. O meglio, è vero solo per una delle relazioni. Verrà ora illustrato in che modo la tabella **Target** può essere correlata alle tabelle di tipo dimensione.

### <a name="relate-higher-grain-time-periods"></a>Correlare periodi di tempo con granularità più elevata

Una relazione tra le tabelle **Date** e **Target** deve essere una relazione uno-a-molti, poiché i valori della colonna **TargetYear** sono date. In questo esempio ogni valore della colonna **TargetYear** è la prima data dell'anno di destinazione.

> [!TIP]
> Quando si archiviano fatti con una granularità temporale superiore a giorno, impostare il tipo di dati della colonna su **Data** (o **Numero intero** se si usano chiavi relative alle date). Nella colonna archiviare un valore che rappresenta il primo giorno del periodo di tempo. Ad esempio, un periodo di un anno viene registrato come 1 gennaio dell'anno, mentre periodo di un mese viene registrato come primo giorno di quel mese.

È tuttavia necessario prestare attenzione per garantire che i filtri a livello di mese o data producano un risultato significativo. Senza alcuna logica di calcolo specifica, gli oggetti visivi del report possono segnalare che le date di destinazione sono letteralmente il primo giorno di ogni anno. Tutti gli altri giorni, e tutti i mesi ad eccezione di gennaio, riepilogheranno la quantità di destinazione come BLANK.

L'oggetto visivo matrice seguente illustra cosa accade quando l'utente del report esegue il drill-down da un anno ai relativi mesi. L'oggetto visivo sta riepilogando la colonna **TargetQuantity** (l'opzione [Mostra elementi senza dati](../create-reports/desktop-show-items-no-data.md) è stata abilitata per le righe della matrice).

![Un oggetto visivo matrice mostra che la quantità di destinazione dell'anno 2020 è pari a 270. Se espanso per mostrare i mesi del 2020, gennaio è pari a 270 e ogni altra quantità di destinazione a livello di mese è BLANK.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

Per evitare questo comportamento, è consigliabile controllare il riepilogo dei dati dei fatti usando le misure. Un modo per controllare il riepilogo consiste nel restituire un valore BLANK quando viene eseguita una query sui periodi di tempo di livello inferiore. Un altro modo, definito con un linguaggio DAX sofisticato, consiste nel ripartire i valori in periodi di tempo di livello inferiore.

Si consideri la definizione di misura seguente che usa la funzione DAX [ISFILTERED](/dax/isfiltered-function-dax). Restituisce un valore solo quando le colonne **Date** o **Month** non vengono filtrate.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

Nell'oggetto visivo matrice seguente si userà ora la misura **Target Quantity**, che mostra che tutte le quantità di destinazione mensili sono BLANK.

![Un oggetto visivo matrice mostra che la quantità di destinazione dell'anno 2020 è pari a 270. Se espanso per mostrare i mesi del 2020, ogni quantità di destinazione a livello di mese è BLANK.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Correlare granularità più elevata (non date)

Occorre un approccio di progettazione diverso quando si correla una colonna non data di una tabella di tipo dimensione a una tabella di tipo fatto (e il livello di granularità è superiore rispetto alla tabella di tipo dimensione).

Le colonne **Category** (di entrambe le tabelle **Product** e **Target**) contengono valori duplicati. Quindi, non esiste un "uno" per una relazione uno-a-molti. In questo caso è necessario creare una relazione molti-a-molti. La relazione deve propagare i filtri in un'unica direzione, dalla tabella di tipo dimensione alla tabella di tipo fatto.

![Un frammento di diagramma del modello mostra le tabelle Target e Product. Una relazione molti-a-molti mette in correlazione le due tabelle. La direzione del filtro è da Product a Target.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Verranno ora esaminate le righe della tabella.

![Un diagramma del modello contiene due tabelle: Target e Product. Una relazione molti-a-molti mette in correlazione le due colonne Category. Nel paragrafo riportato di seguito sono descritti i dettagli delle righe.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

Nella tabella **Target** sono presenti quattro righe: due righe per ogni anno di destinazione (2019 e 2020) e due categorie (Clothing e Accessories). Nella tabella **Product** ci sono tre prodotti. Due appartengono alla categoria Clothing e uno appartiene alla categoria Accessories. Uno dei colori dell'abbigliamento è verde e gli altri due sono blu.

Un oggetto visivo tabella che raggruppa in base alla colonna **Category** della tabella **Product** produce il risultato seguente.

![In un oggetto visivo tabella sono presenti due colonne: Category e TargetQuantity. Accessories è pari a 60, Clothing è pari a 40 e il totale è 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Questo oggetto visivo produce il risultato corretto. A questo punto, si consideri cosa accade quando viene usata la colonna **Color** della tabella **Product** per raggruppare la quantità di destinazione.

![In un oggetto visivo tabella sono presenti due colonne: Color e TargetQuantity. Blue è pari a 100, Green è pari a 40 e il totale è 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

L'oggetto visivo produce una rappresentazione errata dei dati. Cosa sta succedendo?

Un filtro sulla colonna **Color** della tabella **Product** restituisce due righe. Una delle righe è per la categoria Clothing e l'altra per la categoria Accessories. Questi due valori di categoria vengono propagati come filtri alla tabella **Target**. In altre parole, poiché il colore blu viene usato dai prodotti di due categorie, _tali categorie_ vengono usate per filtrare le destinazioni.

Per evitare questo comportamento, come descritto in precedenza, è consigliabile controllare il riepilogo dei dati dei fatti usando le misure.

Si consideri la seguente definizione di misure. Si noti che tutte le colonne della tabella **Product** che si trovano al di sotto del livello della categoria vengono testate per i filtri.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

Nell'oggetto visivo tabella seguente si userà ora la misura **Target Quantity**, che mostra che tutte le quantità di destinazione dei colori sono BLANK.

![In un oggetto visivo tabella sono presenti due colonne: Color e TargetQuantity. Blue è BLANK, Green è BLANK e il totale è 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

La progettazione del modello finale avrà un aspetto simile al seguente.

![Il diagramma del modello mostra che le tabelle Date e Target sono correlate con una relazione uno-a-molti. Le tabelle Product e Target sono correlate con una relazione molti-a-molti, con un filtro da Product a Target.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Indicazioni per la correlazione di fatti con granularità più elevata

Quando occorre correlare una tabella di tipo dimensione a una tabella di tipo fatto e la tabella di tipo fatto archivia le righe con una granularità più elevata rispetto alle righe della tabella di tipo dimensione, vengono fornite le indicazioni seguenti:

- Per date di fatti con granularità più elevata:
  - Nella tabella di tipo fatto archiviare la prima data del periodo di tempo
  - Creare una relazione uno-a-molti tra la tabella data e la tabella di tipo fatto
- Per altri fatti con granularità più elevata:
  - Creare una relazione molti-a-molti tra la tabella di tipo dimensione e la tabella di tipo fatto
- Per entrambi i tipi:
  - Controllare il riepilogo con la logica della misura: restituisce BLANK quando si usano colonne di tipo dimensione di livello inferiore per filtrare o raggruppare
  - Nascondere le colonne della tabella di tipo fatto riepilogabili: in questo modo, potranno essere usate solo le misure per riepilogare la tabella di tipo fatto

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Relazioni nei modelli in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [Informazioni su uno schema star e sull'importanza di questo schema per Power BI](star-schema.md)
- [Linee guida per la risoluzione dei problemi relativi alle relazioni](relationships-troubleshoot.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
