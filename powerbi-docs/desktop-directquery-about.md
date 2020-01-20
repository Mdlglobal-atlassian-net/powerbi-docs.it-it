---
title: Uso di DirectQuery in Power BI
description: Informazioni sull'uso di DirectQuery con Power BI e procedure consigliate su come e quando usare DirectQuery o altre opzioni
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 504b389bdbe50d17f969365d7e4f2e51d206918c
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75837254"
---
# <a name="about-using-directquery-in-power-bi"></a>Informazioni sull'uso di DirectQuery in Power BI

Quando si usa *Power BI Desktop* o il *servizio Power BI* è possibile connettersi a tutti i tipi di origini dati ed effettuare tali connessioni dati in modi diversi. È possibile *importare* dati in Power BI, operazione che rappresenta il modo più comune per ottenere i dati, oppure connettersi direttamente ai dati nel repository di origine tramite *DirectQuery*. Questo articolo descrive le funzionalità di DirectQuery:

* Diverse opzioni di connettività di DirectQuery
* Indicazioni per i casi in cui è opportuno preferire DirectQuery all'importazione
* Svantaggi dell'uso di DirectQuery
* Procedure consigliate per l'uso di DirectQuery

Seguire le procedure consigliate per l'uso dell'importazione rispetto a DirectQuery:

* È opportuno importare i dati in Power BI laddove possibile. L'importazione sfrutta il motore di query con prestazioni elevate di Power BI e offre un'esperienza altamente interattiva e completa.
* Se gli obiettivi non possono essere soddisfatti con l'importazione dei dati, prendere in considerazione l'uso di DirectQuery. Se ad esempio i dati cambiano di frequente e i report devono riflettere i dati più recenti, DirectQuery può essere l'opzione ottimale. L'uso di DirectQuery è tuttavia possibile solo quando l'origine dati sottostante può generare query interattive (meno di 5 secondi per la tipica query di aggregazione) ed è in grado di gestire il carico di query che verrà generato. È anche necessario considerare attentamente le limitazioni relative all'uso di DirectQuery.

Il set di funzionalità offerte da Power BI per l'importazione e per DirectQuery si evolve nel tempo. I cambiamenti includeranno una maggiore flessibilità nell'uso dei dati importati, in modo che l'importazione possa essere usata in un numero più elevato di casi ed eliminando alcuni degli svantaggi di DirectQuery. A prescindere dai miglioramenti, le prestazioni dell'origine dati sottostante rimangono uno degli aspetti più importanti da considerare nell'uso di DirectQuery. Se l'origine dati sottostante è lenta, l'uso di DirectQuery per tale origine continuerà a essere impossibile.

Questo articolo descrive DirectQuery con Power BI e non con *SQL Server Analysis Services*. DirectQuery è anche una funzionalità di SQL Server Analysis Services. Molti dei dettagli descritti in questo articolo si applicano a questa funzionalità, ma esistono alcune differenze importanti. Per informazioni sull'uso di DirectQuery con SQL Server Analysis Services, vedere [DirectQuery in SQL Server 2016 Analysis Services](https://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).

Questo articolo illustra il flusso di lavoro consigliato per DirectQuery, in cui il report viene creato in Power BI Desktop, ma descrive anche la connessione diretta nel servizio Power BI.

## <a name="power-bi-connectivity-modes"></a>Modalità di connettività di Power BI

Power BI si connette a un numero elevato di origini dati diverse, tra cui:

* Servizi online (Salesforce, Dynamics 365 e altri)
* Database (SQL Server, Access, Amazon Redshift e altri)
* File semplici (Excel, JSON e altri)
* Altre origini dati (Spark, siti Web, Microsoft Exchange e altri)

Per queste origini, è possibile importare i dati in Power BI. Per alcune è anche possibile connettersi con DirectQuery. Per un riepilogo delle origini che supportano DirectQuery, vedere [Origini dati supportate da DirectQuery](desktop-directquery-data-sources.md). Altre origini supporteranno DirectQuery in futuro, principalmente quelle che si prevede possano fornire performance soddisfacenti per le query interattive.

SQL Server Analysis Services è un caso particolare. Quando ci si connette a SQL Server Analysis Services, è possibile scegliere di importare i dati o usare una *connessione dinamica*. L'uso di una connessione dinamica è simile all'uso di DirectQuery. Non vengono importati dati e viene sempre eseguita una query sull'origine dati sottostante per aggiornare un oggetto visivo. Una connessione dinamica si differenzia per molti altri aspetti, pertanto viene usato un termine diverso, appunto *connessione dinamica*, rispetto a *DirectQuery*.

Queste sono quindi le tre opzioni per la connessione ai dati: *importazione*, *DirectQuery* e *connessione dinamica*.

### <a name="import-connections"></a>Connessioni di importazione

Per l'importazione, quando si usa **Recupera dati** in Power BI Desktop per connettersi a un'origine dati come SQL Server, il comportamento della connessione è il seguente:

* Durante l'esperienza di recupero dati iniziale, ogni tabella del set selezionato definisce una query che restituisce un set di dati. Queste query possono essere modificate prima di caricare i dati, ad esempio per applicare filtri, aggregare i dati o unire tabelle diverse.
* Durante il caricamento, tutti i dati definiti da tali query verranno importati nella cache di Power BI.
* Durante la compilazione di un oggetto visivo in Power BI Desktop verrà eseguita una query sui dati importati. L'archivio di Power BI assicura che la query sarà rapida. Tutte le modifiche all'oggetto visivo vengono applicate immediatamente.
* Eventuali modifiche ai dati sottostanti non vengono propagate agli oggetti visivi. È necessario selezionare *Aggiorna* per reimportare i dati.
* Al momento della pubblicazione del report come file con estensione *pbix* nel servizio Power BI, viene creato e caricato un set di dati nel servizio Power BI. I dati importati sono inclusi con tale set di dati. È quindi possibile pianificare l'aggiornamento dei dati, ad esempio, per reimportare i dati ogni giorno. A seconda del percorso dell'origine dati potrebbe essere necessario configurare un gateway dati locale.
* Quando si apre un report esistente nel servizio Power BI oppure si crea un nuovo report, viene di nuovo eseguita una query sui dati importati, garantendo l'interattività.
* È possibile aggiungere oggetti visivi o intere pagine del report come riquadri del dashboard. I riquadri vengono aggiornati automaticamente ogni volta che viene aggiornato il set di dati sottostante.

### <a name="directquery-connections"></a>Connessioni DirectQuery

Per DirectQuery, quando si usa **Recupera dati** in Power BI Desktop per connettersi a un'origine dati, il comportamento della connessione è il seguente:

* Durante l'esperienza di recupero dati iniziale viene selezionata l'origine. Per le origini relazionali viene selezionato un set di tabelle, ognuna delle quali definisce una query che restituisce un set di dati in modo logico. Per le origini multidimensionali, ad esempio SAP BW, viene selezionata solo l'origine.
* Durante il caricamento non vengono tuttavia importati dati nell'archivio di Power BI. Durante la compilazione di un oggetto visivo in Power BI Desktop vengono invece inviate query all'origine dati sottostante per recuperare i dati necessari. Il tempo impiegato per aggiornare l'oggetto visivo dipende dalle prestazioni dell'origine dati sottostante.
* Eventuali modifiche ai dati sottostanti non vengono propagate immediatamente agli oggetti visivi esistenti. È sempre necessario eseguire l'aggiornamento. Le query necessarie vengono inviate nuovamente per ogni oggetto visivo e questo viene aggiornato nel modo appropriato.
* Al momento della pubblicazione del report nel servizio Power BI, viene anche in questo caso creato un set di dati nel servizio Power BI, come avviene per l'importazione. Il set di dati *non include tuttavia dati*.
* Quando si apre un report esistente nel servizio Power BI oppure si crea un nuovo report, viene di nuovo eseguita una query sull'origine dati sottostante per recuperare i dati necessari. A seconda del percorso dell'origine dati originale, potrebbe essere necessario configurare un gateway dati locale, come nel caso della modalità di importazione se i dati vengono aggiornati.
* È possibile aggiungere oggetti visivi o intere pagine del report come riquadri del dashboard. Per garantire che l'apertura di un dashboard sia rapida, i riquadri vengono aggiornati automaticamente secondo una pianificazione, ad esempio ogni ora. È possibile gestire la frequenza di aggiornamento in modo da riflettere la frequenza di modifica dei dati e in che misura sia importante visualizzare i dati più recenti. Quando si apre un dashboard, i riquadri riflettono i dati al momento dell'ultimo aggiornamento e non necessariamente le modifiche più recenti apportate all'origine sottostante. È possibile aggiornare un dashboard aperto per visualizzare sempre il contenuto più recente.

### <a name="live-connections"></a>Connessioni dinamiche

Quando ci si connette a SQL Server Analysis Services, è disponibile un'opzione per importare dati dal modello di dati selezionato o connettersi dinamicamente al modello stesso. Se si usa l'importazione, si definisce una query su tale origine SQL Server Analysis Services esterna e i dati vengono importati come di consueto. Se si usa la connessione dinamica, non viene definita alcuna query e nell'elenco dei campi viene visualizzato l'intero modello esterno.

La situazione descritta nel paragrafo precedente si applica anche alla connessione alle origini seguenti, ad eccezione del fatto che non è possibile importare i dati:

* Set di dati di Power BI, ad esempio quando ci si connette a un set di dati di Power BI creato in precedenza e pubblicato nel servizio, per creare un nuovo report correlato.
* Common Data Service.

Il comportamento dei report su SQL Server Analysis Services al momento della pubblicazione nel servizio Power BI è simile a quello dei report di DirectQuery sotto gli aspetti seguenti:

* Quando si apre un report esistente nel servizio Power BI oppure si crea un nuovo report, viene eseguita una query sull'origine dati SQL Server Analysis Services sottostante. L'operazione può richiedere un gateway dati locale.
* I riquadri del dashboard vengono aggiornati automaticamente in base a una pianificazione, ad esempio ogni ora.

Esistono anche alcune differenze importanti. Ad esempio, per le connessioni dinamiche l'identità dell'utente che apre il report viene sempre passata all'origine SQL Server Analysis Services sottostante.

Terminati questi confronti, ci si concentrerà ora esclusivamente su DirectQuery per il resto di questo articolo.

## <a name="when-is-directquery-useful"></a>Situazioni in cui è utile DirectQuery

La tabella seguente descrive alcuni scenari in cui la connessione con DirectQuery può essere particolarmente utile. Sono inclusi casi in cui lasciare i dati nell'origine originale è considerato vantaggioso. La descrizione indica anche se lo scenario specificato è disponibile in Power BI.

| Limitazione | Descrizione |
| --- | --- |
| I dati cambiano di frequente e sono necessari report quasi in tempo reale |I modelli con dati importati possono essere aggiornati al massimo ogni ora. Se i dati cambiano continuamente ed è necessario che i report visualizzino i dati più recenti, l'importazione con l'aggiornamento pianificato potrebbe non soddisfare questi requisiti. È possibile trasmettere dati direttamente in Power BI, anche se esistono limiti ai volumi di dati supportati in questo caso. <br/> <br/> Se si usa DirectQuery, invece, aprendo o aggiornando un report o un dashboard vengono sempre visualizzati i dati più recenti dell'origine. Inoltre, i riquadri del dashboard possono essere aggiornati più frequentemente, anche ogni 15 minuti. |
| Dati di dimensioni molto grandi |Se i dati hanno dimensioni molto grandi, non è fattibile importarli tutti. DirectQuery, al contrario, non richiede il trasferimento di molti dati perché le query vengono eseguite localmente. <br/> <br/> I dati di grandi dimensioni possono tuttavia anche comportare che le query sull'origine sottostante risultino troppo lente, come descritto in [Implicazioni dell'uso di DirectQuery](#implications-of-using-directquery). Non è sempre necessario importare i dati dettagliati completi. È invece possibile preaggregare i dati durante l'importazione. L'*editor di query* semplifica la preaggregazione durante l'importazione. In casi estremi è possibile importare esattamente i dati di aggregazione necessari per ogni oggetto visivo. Anche se DirectQuery è l'approccio più semplice per i dati di grandi dimensioni, l'importazione di dati aggregati può rappresentare una soluzione se l'origine sottostante è troppo lenta. |
| Le regole di sicurezza vengono definite nell'origine sottostante |Quando i dati vengono importati, Power BI si connette all'origine dati usando le credenziali dell'utente corrente da Power BI Desktop oppure le credenziali definite nell'ambito della configurazione dell'aggiornamento pianificato dal servizio Power BI. Quando si pubblica e si condivide questo report è necessario prestare attenzione a condividerlo solo con gli utenti autorizzati a visualizzare gli stessi dati oppure definire la sicurezza a livello di riga nell'ambito del set di dati. <br/> <br/> Dato che DirectQuery esegue sempre query sull'origine sottostante, idealmente questa configurazione consente l'applicazione di qualunque criterio di sicurezza nell'origine stessa. Attualmente Power BI si connette tuttavia all'origine sottostante usando sempre le stesse credenziali usate per l'importazione. <br/> <br/> Finché Power BI consente all'identità dell'utente finale del report di raggiungere l'origine sottostante, DirectQuery non offre vantaggi per la sicurezza dell'origine dati. |
| Limitazioni di sovranità dei dati |Alcune organizzazioni hanno criteri di sovranità dei dati, ovvero i dati non possono uscire dall'organizzazione. Una soluzione basata sull'importazione potrebbe chiaramente presentare problemi. Con DirectQuery, al contrario, i dati rimangono nell'origine sottostante. <br/> <br/> Tuttavia, anche con DirectQuery, alcune cache di dati a livello di oggetto visivo vengono conservate nel servizio Power BI a causa dell'aggiornamento pianificato dei riquadri. |
| L'origine dati sottostante è un'origine OLAP contenente misure |Se l'origine dati sottostante contiene *misure*, come SAP HANA o SAP Business Warehouse, l'importazione dei dati presenta altri problemi. Ciò significa che i dati importati si trovano a un determinato livello di aggregazione come definito dalla query, ad esempio la misurazione di **TotalSales** per **classe**, **anno** e **città**. Quindi, se viene creato un oggetto visivo che richiede dati a un livello di aggregazione superiore, ad esempio **TotalSales** per **anno**, il valore di aggregazione verrà ulteriormente aggregato. Questa aggregazione funziona per le misure additive, come **Sum** e **Min**, ma rappresenta un problema per le misure non additive, come **Average** e **DistinctCount**. <br/> <br/> Per ottenere facilmente i dati aggregati corretti, in base a quanto richiesto dall'oggetto visivo specifico, direttamente dall'origine, si dovrebbe inviare query per ogni oggetto visivo, come in DirectQuery. <br/> <br/> Quando ci si connette a SAP Business Warehouse (BW), la scelta di DirectQuery consente questo trattamento delle misure. Per informazioni su SAP BW, vedere [DirectQuery e SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> Tuttavia, al momento DirectQuery in SAP HANA tratta le misure come un'origine relazionale e offre un comportamento simile all'importazione. Questo approccio è illustrato nei dettagli in [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md). |

Riepilogando, date le attuali funzionalità di DirectQuery in Power BI, gli scenari in cui offre vantaggi sono i seguenti:

* I dati cambiano di frequente e sono necessari report quasi in tempo reale.
* Vengono gestiti dati di dimensioni molto grandi, senza la necessità di preaggregare.
* Si applicano limitazioni a livello di sovranità dei dati.
* L'origine è multidimensionale e contiene misure, ad esempio SAP BW.

I dettagli nell'elenco precedente si riferiscono all'uso del solo Power BI. In alternativa, si potrebbe usare un modello esterno di SQL Server Analysis Services o Azure Analysis Services per importare i dati, usando quindi Power BI per connettersi al modello. Anche se questo approccio richiede un'ulteriore configurazione, offre maggiore flessibilità. È possibile importare volumi di dati molto più grandi. Non esistono limitazioni alla frequenza di aggiornamento dei dati.

## <a name="implications-of-using-directquery"></a>Implicazioni dell'uso di DirectQuery

L'uso di DirectQuery ha implicazioni potenzialmente negative, come descritto in questa sezione. Alcune di queste limitazioni differiscono leggermente a seconda dell'origine usata. Queste limitazioni vengono illustrate laddove applicabile e le origini sostanzialmente diverse vengono trattate in altri articoli.

### <a name="performance-and-load-on-the-underlying-source"></a>Prestazioni e carico sull'origine sottostante

Quando si usa DirectQuery, l'esperienza complessiva dipende molto dalle prestazioni dell'origine dati sottostante. Se l'aggiornamento di ogni oggetto visivo, ad esempio dopo la modifica del valore di un filtro dei dati, impiega pochi secondi, in genere meno di cinque, l'esperienza è ragionevole. Potrebbe però apparire lenta rispetto alla risposta immediata quando si importano i dati in Power BI. Se a causa della lentezza dell'origine l'aggiornamento dei singoli oggetti visivi impiega più di dieci secondi, l'esperienza diventa decisamente insufficiente. Può persino verificarsi il timeout delle query.

Oltre alle prestazioni dell'origine sottostante, prestare attenzione al carico posto sull'origine. Il carico ha infatti un impatto sulle prestazioni. Per ogni utente che apre un report condiviso e ogni riquadro del dashboard che viene aggiornato viene inviata almeno una query per oggetto visivo all'origine sottostante. L'origine deve quindi poter gestire questo carico di query pur mantenendo prestazioni accettabili.

### <a name="security-implications-when-combining-data-sources"></a>Implicazioni per la sicurezza in caso di combinazione di origini dati

È possibile usare più origini dati in un modello DirectQuery, esattamente come quando si importano i dati, tramite la funzionalità [Modelli compositi](desktop-composite-models.md). Quando si usano più origini dati, è importante comprendere il modo in cui i dati vengono spostati tra le origini dati sottostanti, oltre alle [implicazioni per la sicurezza](desktop-composite-models.md#security-implications).

### <a name="limited-data-transformations"></a>Trasformazione dei dati limitata

Analogamente, sono presenti limitazioni nelle trasformazioni dei dati che possono essere applicate all'interno dell'editor di query. Con i dati importati è possibile applicare facilmente un set di trasformazioni avanzato per pulire e modificare la forma dei dati prima di usarli per creare oggetti visivi, ad esempio per l'analisi di documenti JSON o la trasformazione tramite Pivot da un modulo basato su colonne a un modulo basato su righe. Queste trasformazioni sono più limitate in DirectQuery.

Quando ci si connette a un'origine OLAP come SAP Business Warehouse, non è possibile definire alcuna trasformazione e l'intero modello esterno proviene dall'origine. Per le origini relazionali, come SQL Server, è comunque possibile definire un set di trasformazioni per ogni query, ma tali trasformazioni sono limitate per motivi di prestazioni.

Qualsiasi trasformazione di questo tipo dovrà essere applicata a ogni query per l'origine sottostante, anziché una sola volta al momento dell'aggiornamento dei dati, quindi saranno possibili solo le trasformazioni che possono essere ragionevolmente convertite in una singola query nativa. Se si usa una trasformazione troppo complessa, si riceve un errore che indica che la trasformazione deve essere eliminata oppure che è necessario impostare l'importazione del modello.

Inoltre, la query ottenuta dalla finestra di dialogo **Recupera dati** o dall'editor di query verrà usata in una selezione secondaria delle query generate e inviata per recuperare i dati necessari per un oggetto visivo. La query definita nell'editor di query deve essere valida in questo contesto. In particolare, non è possibile usare una query con espressioni di tabella comuni o che richiami stored procedure.

### <a name="modeling-limitations"></a>Limitazioni di modellazione

In questo contesto il termine *modellazione* indica l'azione di modifica e arricchimento dei dati non elaborati, nell'ambito della creazione di un report che usa tali dati. Alcuni esempi:

* Definizione di relazioni tra tabelle
* Aggiunta di nuovi calcoli (colonne calcolate e misure)
* Ridenominazione e disattivazione della visualizzazione di colonne e misure
* Definizione di gerarchie
* Definizione della formattazione, dell'esecuzione del riepilogo predefinita e dell'ordinamento di una colonna
* Raggruppamento o clustering dei valori

Quando si usa DirectQuery è comunque possibile apportare molti di questi miglioramenti ai modelli e vale sempre il principio di arricchire i dati non elaborati per migliorare l'uso in un momento successivo. Tuttavia, quando si usa DirectQuery alcune funzionalità di modellazione non sono disponibili o sono limitate. Le limitazioni vengono in genere applicate per evitare problemi di prestazioni. Le limitazioni comuni a tutte le origini DirectQuery sono elencate di seguito. Per alcune origini potrebbero valere ulteriori limitazioni, come descritto in [Passaggi successivi](#next-steps).

* **Nessuna gerarchia di data predefinita:** quando si importano dati, per impostazione predefinita ogni colonna date/datetime ha anche una gerarchia di data predefinita. Se ad esempio si importa una tabella di ordini di vendita che include una colonna **OrderDate**, quando si usa **OrderDate** in un oggetto visivo è possibile scegliere il livello appropriato (anno, mese, giorno) da usare. Questa gerarchia di data predefinita non è disponibile quando si usa DirectQuery. Se nell'origine sottostante è disponibile una tabella **Date**, come avviene spesso in molti data warehouse, è possibile usare le funzioni DAX di Business Intelligence per le gerarchie temporali come di consueto.
* **Supporto di data/ora solo con precisione al secondo:** quando si usano le colonne temporali nel set di dati, Power BI invia le query all'origine sottostante a un livello di dettaglio di secondi. Le query non vengono inviate all'origine DirectQuery per millisecondi. Rimuovere questa parte temporale dalle colonne di origine.
* **Limitazioni nelle colonne calcolate:** le colonne calcolate possono essere solo intrariga, ovvero possono fare riferimento solo ai valori delle altre colonne della stessa tabella, senza usare funzioni di aggregazione. Inoltre, le funzioni scalari DAX, come `LEFT()`, che sono consentite sono limitate a quelle di cui è possibile eseguire il push nell'origine sottostante. Le funzioni variano a seconda delle funzionalità esatte dell'origine. Le funzioni non supportate non vengono elencate nel completamento automatico quando si crea la funzione DAX per una colonna calcolata e generano un errore se usate.
* **Nessun supporto per le funzioni DAX padre-figlio:** nella modalità DirectQuery non è possibile usare la famiglia di funzioni `DAX PATH()` che in genere gestiscono strutture padre-figlio, ad esempio piani dei conti o gerarchie dei dipendenti.
* **Tabelle calcolate non supportate:** la possibilità di definire una tabella calcolata usando un'espressione DAX non è supportata nella modalità DirectQuery.
* **Filtro delle relazioni:** per informazioni sul filtro bidirezionale, vedere [Filtro incrociato bidirezionale](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx). Questo white paper presenta esempi nel contesto di SQL Server Analysis Services. I punti fondamentali si applicano ugualmente a Power BI.
* **Nessun clustering:** con DirectQuery non è possibile usare la funzionalità di clustering per trovare automaticamente i gruppi.

### <a name="reporting-limitations"></a>Limitazioni della creazione di report

Quasi tutte le funzionalità di creazione di report sono supportate per i modelli DirectQuery. È quindi possibile usare lo stesso set di visualizzazioni finché l'origine sottostante offre un livello di prestazioni adeguato. Esistono importanti limitazioni in alcune delle altre funzionalità disponibili nel servizio Power BI dopo la pubblicazione di un report:

* **Informazioni rapide non è supportato:** Informazioni rapide di Power BI esegue ricerche in diversi subset del set di dati applicando una serie di algoritmi complessi per individuare informazioni potenzialmente interessanti. Data la necessità di query con prestazioni molto elevate, questa funzionalità non è disponibile nei set di dati con DirectQuery.
* **Domande e risposte non è supportato:** Domande e risposte di Power BI consente di esplorare i dati tramite funzionalità intuitive basate sul linguaggio naturale e di ricevere le risposte sotto forma di grafici. Non è tuttavia attualmente supportato nei set di dati con DirectQuery.
* **L'uso di Esplora in Excel determinerà probabilmente un calo di prestazioni:** è possibile esplorare i dati usando la funzionalità Esplora in Excel in un set di dati. Questo approccio consente di creare tabelle e grafici pivot in Excel. Anche se questa funzionalità è supportata nei set di dati con DirectQuery, le prestazioni sono in genere più lente rispetto alla creazione di oggetti visivi in Power BI ed è necessario tener conto di questo aspetto nella decisione di usare DirectQuery se l'uso di Excel è importante per i propri scenari.

### <a name="security"></a>Sicurezza

Come illustrato in precedenza in questo articolo, un report di DirectQuery usa sempre le stesse credenziali fisse per la connessione all'origine dati sottostante, dopo la pubblicazione nel servizio Power BI. Questo comportamento si applica a DirectQuery, non alle connessioni dinamiche a SQL Server Analysis Services, che sono diverse sotto questo aspetto. Subito dopo la pubblicazione di un report di DirectQuery è necessario configurare le credenziali dell'utente che verranno usate. Finché non si configurano le credenziali, l'apertura del report nel servizio Power BI genererà un errore.

Dopo aver specificato le credenziali dell'utente, queste verranno usate *indipendentemente dall'utente che apre il report*. Sotto questo aspetto non c'è differenza rispetto ai dati importati. Ogni utente vede gli stessi dati, a meno che nell'ambito del report non sia stata definita la sicurezza a livello di riga. È necessario prestare la stessa attenzione alla condivisione del report, se sono presenti regole di sicurezza definite nell'origine sottostante.

### <a name="behavior-in-the-power-bi-service"></a>Comportamento nel servizio Power BI

Questa sezione descrive il comportamento di un report di DirectQuery nel servizio Power BI, per spiegare l'entità del carico applicato all'origine dati back-end dato il numero di utenti con i quali verranno condivisi il report e il dashboard, la complessità del report e a seconda che sia stata definita la sicurezza a livello di riga nel report.

#### <a name="reports--opening-interacting-with-editing"></a>Report: apertura, interazione, modifica

Quando si apre un report, tutti gli oggetti visivi presenti nella pagina visualizzata vengono aggiornati. Ciascun oggetto visivo richiede in genere almeno una query sull'origine dati sottostante. Alcuni oggetti visivi potrebbero richiedere più query. Ad esempio, un oggetto visivo potrebbe visualizzare valori aggregati di due tabelle dei fatti diverse oppure contenere una misura più complessa o totali di una misura non additiva come Count Distinct. Se ci si sposta su una nuova pagina, questi oggetti visivi vengono aggiornati. L'aggiornamento invia un nuovo set di query all'origine sottostante.

Ogni interazione dell'utente con il report può comportare l'aggiornamento degli oggetti visivi. La selezione di un valore diverso in un filtro dei dati richiede ad esempio l'invio di un nuovo set di query per aggiornare tutti gli oggetti visivi interessati. Lo stesso vale quando si fa clic su un oggetto visivo per l'evidenziazione incrociata di altri oggetti visivi oppure quando si modifica il filtro.

In modo analogo, la modifica di un nuovo report richiede l'invio di query per ogni passaggio necessario per produrre l'oggetto visivo finale.

I risultati vengono memorizzati nella cache, in modo che l'aggiornamento di un oggetto visivo sia istantaneo se di recente sono stati ottenuti gli stessi identici risultati. Se non è stata definita la sicurezza a livello di riga, queste cache non vengono condivise tra gli utenti.

#### <a name="dashboard-refresh"></a>Aggiornamento del dashboard

È possibile aggiungere singoli oggetti visivi o intere pagine come riquadri del dashboard. I riquadri basati su set di dati di DirectQuery vengono aggiornati automaticamente in base a una pianificazione. I riquadri inviano query all'origine dati back-end. Per impostazione predefinita, i set di dati vengono aggiornati ogni ora, ma è possibile definire un intervallo di aggiornamento compreso tra una volta alla settimana e ogni 15 minuti nelle impostazioni del set di dati.

Se non è stata definita la sicurezza a livello di riga nel modello, ogni riquadro viene aggiornato una sola volta e i risultati vengono condivisi tra tutti gli utenti. In caso contrario, l'effetto moltiplicatore può essere notevole. Ogni riquadro richiede l'invio di query separate per ogni utente all'origine sottostante.

Un dashboard con 10 riquadri condivisi con 100 utenti e creato su un set di dati con DirectQuery, dotato di sicurezza a livello di riga e configurato per l'aggiornamento ogni 15 minuti, comporterà l'invio di almeno 1000 query ogni 15 minuti all'origine back-end.

È quindi necessario valutare attentamente l'uso della sicurezza a livello di riga e la configurazione della frequenza di aggiornamento.

#### <a name="time-outs"></a>Timeout

Alle singole query nel servizio Power BI viene applicato un timeout di quattro minuti. Le query che superano questo tempo hanno esito negativo. Come sottolineato in precedenza, è consigliabile usare DirectQuery per le origini che forniscono prestazioni di query quasi interattive. Questo limite ha lo scopo di prevenire i problemi dati da tempi di esecuzione eccessivamente lunghi.

### <a name="other-implications"></a>Altre implicazioni

Alcune altre implicazioni generali dell'uso di DirectQuery sono descritte di seguito:

* **Se i dati cambiano, è necessario aggiornare per assicurarsi che vengano visualizzati i dati più recenti:** dato l'uso di cache, non c'è garanzia che l'oggetto visivo visualizzi sempre i dati più recenti. Un oggetto visivo può ad esempio visualizzare le transazioni dell'ultimo giorno. A causa della modifica di un filtro dei dati, potrebbe venire aggiornato per visualizzare le transazioni degli ultimi due giorni. Le transazioni potrebbero includere le transazioni recenti e appena arrivate. Reimpostando il filtro dei dati sul valore originale, l'oggetto visualizzerà di nuovo il valore ottenuto in precedenza e memorizzato nella cache.

  Selezionando **Aggiorna**, le cache vengono cancellate e tutti gli oggetti visivi presenti nella pagina vengono aggiornati per visualizzare i dati più recenti.

* **Se i dati cambiano, non c'è garanzia di coerenza tra gli oggetti visivi:** oggetti visivi diversi, indipendentemente dal fatto che si trovino nella stessa pagina o in pagine diverse, potrebbero essere aggiornati in momenti diversi. Se i dati nell'origine sottostante cambiano, non è certo che ogni oggetto visivo visualizzi i dati dello stesso identico momento. Dato che in alcuni casi sono necessarie più query per un singolo oggetto visivo, ad esempio per ottenere i dettagli e i totali, la coerenza non è in realtà garantita neanche all'interno di un singolo oggetto visivo. Per garantire la coerenza sarebbe necessario aggiornare tutti gli oggetti visivi quando ne viene aggiornato uno qualsiasi, oltre all'uso di costose funzioni quali l'isolamento snapshot nell'origine dati sottostante.

  Questo problema può essere in gran parte risolto selezionando di nuovo **Aggiorna** per aggiornare tutti gli oggetti visivi presenti nella pagina. Anche la modalità di importazione comporta un problema di coerenza simile quando si importano dati da più tabelle.

* **L'aggiornamento in Power BI Desktop è necessario in modo da riflettere le modifiche dei metadati:** dopo la pubblicazione di un report, selezionando **Aggiorna** vengono aggiornati gli oggetti visivi nel report. Se lo schema dell'origine sottostante è stato modificato, tali modifiche non vengono applicate automaticamente per modificare i campi disponibili nell'elenco dei campi. Se sono state rimosse tabelle o colonne dall'origine sottostante, la query potrebbe restituire un errore durante l'aggiornamento. Per aggiornare i campi nel modello e applicare le modifiche, è necessario aprire il report in Power BI Desktop e scegliere **Aggiorna**.

* **Limite di un milione di righe restituite in una query:** è previsto un limite predefinito di un milione per il numero di righe che possono essere restituite in una singola query sull'origine sottostante. Questo limite non ha generalmente implicazioni pratiche e gli oggetti visivi in sé non visualizzano così tanti punti. Il limite può essere tuttavia violato nei casi in cui Power BI non ottimizzi completamente le query inviate e alcuni risultati intermedi richiesti superino il limite. Il superamento del limite può anche verificarsi durante la creazione di un oggetto visivo, prima di ottenere uno stato finale più ragionevole. L'inclusione di **Customer** e **TotalSalesQuantity** violerebbe ad esempio questo limite se fossero presenti più di 1 milione di clienti, finché non viene applicato un filtro.

  Verrebbe restituito questo errore: "Il set di risultati di una query sull'origine dati esterna ha superato le dimensioni massime consentite di '1000000' righe".

* **Non è possibile passare dalla modalità di importazione alla modalità DirectQuery:** è in genere possibile passare dalla modalità DirectQuery alla modalità di importazione per un modello, ma tutti i dati necessari devono essere importati. Non è invece possibile tornare alla modalità precedente, principalmente a causa del set di funzionalità non supportate nella modalità DirectQuery. Non è possibile passare dalla modalità DirectQuery alla modalità di importazione nemmeno per i modelli DirectQuery su origini multidimensionali come SAP BW, a causa del diverso trattamento delle misure esterne.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery nel servizio Power BI

Tutte le origini sono supportate da Power BI Desktop. Alcune origini sono anche disponibili direttamente all'interno del servizio Power BI. Un utente aziendale può ad esempio usare Power BI per connettersi ai propri dati in Salesforce e ottenere immediatamente un dashboard senza usare Power BI Desktop.

Nel servizio sono direttamente disponibili solo due delle origini supportate da DirectQuery:

* Spark
* Azure SQL Data Warehouse

È tuttavia consigliabile iniziare a usare DirectQuery con queste due origini dall'interno di Power BI Desktop, perché quando viene inizialmente stabilita la connessione nel servizio Power BI vengono applicate molte limitazioni chiave. Anche se il punto di partenza è semplice (l'avvio nel servizio Power BI), l'ulteriore miglioramento del report ottenuto è soggetto a limitazioni. Non è ad esempio possibile creare calcoli o usare molte funzioni di analisi o persino aggiornare i metadati per applicare le modifiche apportate allo schema sottostante.

## <a name="guidance-for-using-directquery-successfully"></a>Indicazioni per un uso ottimale di DirectQuery

Se si intende usare DirectQuery, questa sezione offre alcune indicazioni generali su come ottenere risultati ottimali. Le indicazioni fornite in questa sezione derivano dalle implicazioni dell'uso di DirectQuery descritte in questo articolo.

### <a name="back-end-data-source-performance"></a>Prestazioni dell'origine dati back-end

Verificare che gli oggetti visivi semplici vengano aggiornati in un tempo ragionevole, ovvero entro 5 secondi per un'esperienza interattiva soddisfacente. Se l'aggiornamento degli oggetti visivi impiega più di 30 secondi, è molto probabile che dopo la pubblicazione del report si verifichino altri problemi, che possono rendere la soluzione impraticabile.

Se le query sono lente, esaminare le query inviate all'origine sottostante e il motivo delle loro prestazioni. Questo articolo non tratta l'ampia gamma di procedure consigliate per l'ottimizzazione dei database nel set completo delle possibili origini sottostanti, ma è applicabile alle procedure standard per i database valide per la maggior parte delle situazioni:

* Le relazioni basate su colonne di tipo Integer hanno in genere prestazioni migliori rispetto ai join su colonne di altri tipi di dati.
* È necessario creare gli indici appropriati. Ciò implica generalmente l'uso di indici dell'archivio colonne nelle origini che li supportano, ad esempio SQL Server.
* Devono essere aggiornate tutte le statistiche necessarie nell'origine.

### <a name="model-design-guidance"></a>Indicazioni per la progettazione del modello

Quando si definisce il modello è consigliabile seguire queste indicazioni:

* **Evitare query complesse nell'editor di query.** L'editor di query converte una query complessa in una singola query SQL. La singola query viene visualizzata nella selezione secondaria di ogni query inviata alla tabella. Se la query è complessa potrebbero verificarsi problemi di prestazioni per ogni query inviata. La query SQL effettiva per un set di passaggi può essere ottenuta selezionando l'ultimo passaggio nell'editor di query e scegliendo **Visualizza query nativa** dal menu di scelta rapida.
* **Mantenere le misure semplici.** Almeno inizialmente, è consigliabile limitare le misure ad aggregazioni semplici. Se le misure offrono prestazioni soddisfacenti, è possibile definire misure più complesse, ma prestando attenzione alle prestazioni di ognuna.
* **Evitare relazioni sulle colonne calcolate.** Questa indicazione è valida per i database in cui è necessario eseguire join multicolonna. Power BI non consente attualmente relazioni basate su più colonne come chiavi di riferimento/chiavi primarie. La soluzione comune consiste nel concatenare le colonne usando una colonna calcolata e basare il join su tale colonna. Questa soluzione alternativa è ragionevole per i dati importati, ma per DirectQuery produce un join in un'espressione. Questo risultato impedisce generalmente l'uso degli indici e comporta una riduzione delle prestazioni. L'unica soluzione alternativa è materializzare effettivamente più colonne in una singola colonna nel database sottostante.
* **Evitare relazioni sulle colonne uniqueidentifier.** Power BI non supporta dati di tipo `uniqueidentifier` in modo nativo. La definizione di una relazione tra colonne di tipo `uniqueidentifier` produce una query con un join che prevede un cast. Anche questo approccio provoca generalmente una riduzione delle prestazioni. Fino a quando questo caso d'uso non viene espressamente ottimizzato, l'unica soluzione consiste nel materializzare colonne di un tipo alternativo nel database sottostante.
* **Nascondere la colonna "to" nelle relazioni.** La colonna *to* nelle relazioni è in genere la chiave primaria della tabella *to*. Questa colonna deve essere nascosta. Se è nascosta, non compare nell'elenco dei campi e non può essere usata negli oggetti visivi. Le colonne su cui si basano le relazioni sono di fatto spesso *colonne di sistema*, ad esempio chiavi sostitutive in un data warehouse, ed è comunque consigliabile nascondere tali colonne. Se la colonna è significativa, introdurre una colonna calcolata visibile e avente un'espressione semplice equivalente alla chiave primaria, come nell'esempio seguente:

  ```sql  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  ```

* **Esaminare tutti gli usi delle colonne calcolate e le modifiche ai tipi di dati.** L'uso di queste funzionalità non è necessariamente dannoso. Implica che le query inviate all'origine sottostante contengano espressioni anziché semplici riferimenti a colonne. Ciò può anche in questo caso impedire l'uso degli indici.
* **Evitare l'uso di filtri incrociati bidirezionali per le relazioni.** L'uso di filtri incrociati bidirezionali può determinare istruzioni di query che non offrono prestazioni ottimali.
* **Provare l'impostazione *Considera integrità referenziale*.** L'impostazione Considera integrità referenziale nelle relazioni consente alle query di usare istruzioni `INNER JOIN` invece di `OUTER JOIN`. Le prestazioni delle query generalmente migliorano seguendo queste indicazioni, anche se ciò dipende dalle specifiche dell'origine dati.
* **Non usare filtri data relativi nell'editor di query.** È possibile definire filtri data relativi nell'editor di query, ad esempio per filtrare le righe in cui la data è negli ultimi 14 giorni.
  
  ![Filtro delle righe per gli ultimi 14 giorni](media/desktop-directquery-about/directquery-about_02.png)
  
  Questo filtro viene tuttavia convertito in un filtro basato sulla data fissa, come al momento in cui è stata creata la query. Questo risultato può essere visto esaminando la query nativa.
  
  ![Filtro delle righe nella query SQL nativa](media/desktop-directquery-about/directquery-about_03.png)
  
  Questo risultato non è probabilmente quello desiderato. Per assicurarsi che il filtro venga applicato in base alla data in cui viene eseguito il report, applicare invece il filtro nel report come filtro report. Questa operazione viene attualmente eseguita creando una colonna calcolata per il calcolo del numero di giorni trascorsi, tramite la funzione `DAX DATE()`, e quindi usando tale colonna calcolata in un filtro.

### <a name="report-design-guidance"></a>Indicazioni per la progettazione del report

Quando si crea un report tramite una connessione DirectQuery, seguire queste indicazioni:

* **Provare a usare le opzioni di Riduzione query:** Power BI include opzioni nel report per inviare un minor numero di query e per disabilitare alcune interazioni che comporterebbero un'esperienza insoddisfacente se le query risultanti richiedessero tempi di esecuzione lunghi. Per accedere a queste opzioni in Power BI Desktop, passare a **File** > **Opzioni e impostazioni** > **Opzioni** e selezionare **Riduzione query**.

   ![Opzioni di Riduzione query](media/desktop-directquery-about/directquery-about_03b.png)

    La selezione delle opzioni in **Riduzione query** consente di disabilitare l'evidenziazione incrociata nell'intero report. È anche possibile mostrare un pulsante **Applica** per filtri dei dati o selezioni di filtri. Questo approccio consente di effettuare diverse selezioni di filtri e filtri dei dati prima di applicarle. Non viene inviata alcuna query finché non si seleziona il pulsante **Applica** sul filtro dei dati. Le selezioni possono quindi essere usate per filtrare i dati.

    Queste opzioni si applicano al report mentre si interagisce con esso in Power BI Desktop, oltre che quando gli utenti utilizzano il report nel servizio Power BI.

* **Applicare prima i filtri:** applicare sempre eventuali filtri all'inizio della creazione di un oggetto visivo. Ad esempio, invece di trascinare **TotalSalesAmount** e **ProductName** e quindi filtrare in base a un anno specifico, applicare il filtro su **anno** fin dall'inizio. Ogni passaggio della creazione di un oggetto visivo invia una query. Anche se è possibile apportare un'altra modifica prima del completamento della prima query, questo approccio lascia comunque un carico superfluo sull'origine sottostante. Applicando subito i filtri, le query intermedie diventano generalmente meno impegnative. Inoltre, se non si applicano subito i filtri è possibile che venga raggiunto il limite di 1 milione di righe.
* **Limitare il numero di oggetti visivi in una pagina:** quando si apre una pagina o si modifica un filtro dei dati o un filtro a livello di pagina, tutti gli oggetti visivi presenti in una pagina vengono aggiornati. È anche previsto un limite al numero di query inviate in parallelo. Con l'aumentare del numero di oggetti visivi, alcuni di essi verranno aggiornati in modo seriale, con il conseguente incremento del tempo necessario per aggiornare l'intera pagina. Per questo motivo, è consigliabile limitare il numero di oggetti visivi presenti in una singola pagina e optare per più pagine semplici.
* **Considerare la disattivazione dell'interazione tra oggetti visivi:** Per impostazione predefinita, le visualizzazioni in una pagina di report possono essere usate per applicare un filtro incrociato e un'evidenziazione incrociata nelle altre visualizzazioni nella pagina. Selezionando ad esempio **1999** nel grafico a torta, all'istogramma verrà applicata l'evidenziazione incrociata per visualizzare le vendite per categoria per l'anno **1999**.
  
  ![Più oggetti visivi con filtro incrociato ed evidenziazione incrociata](media/desktop-directquery-about/directquery-about_04.png)
  
  Il filtro incrociato e l'evidenziazione incrociata in DirectQuery richiedono l'invio di query all'origine sottostante. Se il tempo necessario per rispondere alle selezioni degli utenti diventa eccessivamente lungo, è possibile disattivare questa interazione. È possibile farlo per l'intero report, come descritto in precedenza per le opzioni di Riduzione query, o caso per caso. Per altre informazioni, vedere [Filtro incrociato per gli oggetti visivi in un report di Power BI](consumer/end-user-interactions.md).

Oltre ai suggerimenti precedenti, ognuna delle funzionalità di creazione di report seguenti può causare problemi di prestazioni:

* **Filtri di misure:** gli oggetti visivi che contengono misure, o aggregazioni di colonne, possono contenere filtri in tali misure. L'immagine grafica seguente visualizza ad esempio il valore di **SalesAmount** per **categoria**, ma includendo solo le categorie con oltre **20 milioni** di vendite.
  
  ![Oggetto visivo con misure che contengono filtri](media/desktop-directquery-about/directquery-about_05.png)
  
  Questo approccio comporta l'invio di due query all'origine sottostante:
  
  * La prima query recupera le categorie che soddisfano la condizione **SalesAmount** maggiore di 20 milioni.
  * La seconda query recupera quindi i dati necessari per l'oggetto visivo, incluse le categorie che soddisfano la condizione presente nella clausola `WHERE`.
  
  Questo approccio in genere funziona bene in presenza di centinaia o migliaia di categorie, come in questo esempio. Se il numero di categorie è molto più elevato, le prestazioni possono peggiorare. La query non riesce se più di un milione di categorie soddisfano la condizione. Il limite di un milione di righe è stato descritto in precedenza.

* **Filtri PrimiN:** è possibile definire filtri avanzati in modo da filtrare solo i primi o ultimi N valori classificati in base a una determinata misura. Ad esempio, i filtri possono includere le prime 10 categorie nell'oggetto visivo precedente. Anche questo approccio comporta l'invio di due query all'origine sottostante: La prima query restituirà tuttavia tutte le categorie dell'origine sottostante; le prime N verranno determinate in base ai risultati restituiti. A seconda della cardinalità della colonna interessata, questo approccio può causare problemi di prestazioni oppure l'esito negativo delle query a causa del limite di 1 milione di righe.

* **Mediana:** per le aggregazioni, come `Sum` o `Count Distinct`, viene in genere eseguito il push nell'origine sottostante. Questo non vale tuttavia per la mediana, perché questa aggregazione non è in genere supportata dall'origine sottostante. In questi casi, i dati di dettaglio vengono recuperati dall'origine sottostante e la mediana viene calcolata dai risultati restituiti. Questo approccio è appropriato quando la mediana deve essere calcolata su un numero relativamente ridotto di risultati, mentre si verificheranno problemi di prestazioni o errori di query a causa del limite di 1 milione di righe, se la cardinalità è di grandi dimensioni. La **mediana della popolazione nazionale** potrebbe essere ad esempio un'operazione ragionevole, mentre la **mediana del prezzo di vendita** potrebbe non esserlo.

* **Filtri di testo avanzati (* contiene* e simili):* * quando si filtra una colonna di testo, il filtro avanzato accetta parametri come *contiene*, *inizia con* e così via. Questi filtri possono certamente comportare prestazioni ridotte per alcune origini dati. In particolare, il filtro *contiene* predefinito non deve essere usato se si vuole ottenere una corrispondenza esatta. Anche se i risultati possono essere gli stessi, a seconda dei dati effettivi, le prestazioni potrebbero differire notevolmente a causa dell'uso degli indici.

* **Filtri dei dati di selezione multipla:** per impostazione predefinita, i filtri dei dati consentono una sola selezione. Consentire la selezione multipla nei filtri può causare problemi di prestazioni, in quanto l'utente seleziona un set di elementi nel filtro dei dati. Ad esempio, se l'utente seleziona i 10 prodotti di interesse, ogni nuova selezione comporta l'invio di query all'origine. Anche se l'utente può selezionare l'elemento successivo prima che la query venga completata, questo approccio comporta in ogni caso un carico aggiuntivo sull'origine sottostante.

* **Considerare la disattivazione dei totali negli oggetti visivi:** per impostazione predefinita, le tabelle e le matrici visualizzano totali e subtotali. In molti casi, è necessario inviare query separate all'origine sottostante per ottenere i valori per tali totali. Questo vale ogni volta che si usa l'aggregazione *DistinctCount* o in tutti i casi in cui si usa DirectQuery su SAP BW o SAP HANA. È consigliabile disattivare questi totali tramite il riquadro **Formato**.

### <a name="maximum-number-of-connections-option-for-directquery"></a>Opzione relativa al numero massimo di connessioni per DirectQuery

È possibile impostare il numero massimo di connessioni che DirectQuery può aprire per ogni origine dati sottostante e controllare così il numero di query inviate simultaneamente a ogni origine dati.

Il numero massimo predefinito di connessioni simultanee che DirectQuery può aprire è 10. È possibile cambiare il numero massimo per il file corrente in Power BI Desktop. Passare a **File** > **Opzioni e impostazioni** > **Opzioni**. Nella sezione **File corrente** nel riquadro sinistro selezionare **DirectQuery**.

![Impostazione del numero massimo di connessioni DirectQuery](media/desktop-directquery-about/directquery-about_05b.png)

L'impostazione è abilitata solo se nel report corrente è presente almeno un'origine DirectQuery. Il valore si applica a tutte le origini DirectQuery e a tutte le nuove origini DirectQuery aggiunte allo stesso report.

Se si aumenta il valore di **Numero massimo di connessioni per origine dati**, è possibile inviare un numero maggiore di query, fino al numero massimo specificato, all'origine dati sottostante. Questo approccio è utile se in un'unica pagina sono presenti numerosi oggetti visivi o se molti utenti accedono a un report contemporaneamente. Quando viene raggiunto il numero massimo di connessioni, le query in eccesso vengono accodate fino a quando non diventa disponibile una connessione. L'aumento di questo limite comporta un carico maggiore dell'origine sottostante. L'impostazione quindi non garantisce il miglioramento delle prestazioni complessive.

Dopo la pubblicazione di un report, il numero massimo di query simultanee inviate all'origine dati sottostante dipende anche da limiti fissi, che dipendono dall'ambiente di destinazione in cui il report viene pubblicato. Ambienti diversi, come Power BI, Power BI Premium o Server di report di Power BI, possono imporre ognuno limiti diversi.

### <a name="diagnosing-performance-issues"></a>Diagnosi dei problemi di prestazioni

Questa sezione descrive come diagnosticare i problemi di prestazioni o come ottenere informazioni più dettagliate per consentire l'ottimizzazione dei report.

È consigliabile avviare la diagnosi dei problemi di prestazioni in Power BI Desktop piuttosto che nel servizio Power BI. I problemi di prestazioni sono spesso basati sulle prestazioni dell'origine sottostante. Identificare e diagnosticare i problemi è più facile nell'ambiente più isolato di Power BI Desktop. Questo approccio elimina inizialmente alcuni componenti, come Power BI Gateway. Se i problemi di prestazioni sono assenti da Power BI Desktop, esaminare le specifiche del report nel servizio Power BI. L'[analizzatore prestazioni](desktop-performance-analyzer.md) è uno strumento utile per identificare i problemi durante il processo.

È allo stesso modo consigliabile provare in prima battuta a isolare eventuali problemi per un singolo oggetto visivo, piuttosto che per molti oggetti visivi di una pagina.

Supponendo di aver eseguito i passaggi descritti nei paragrafi precedenti di questa sezione, si ha ora un singolo oggetto visivo in una pagina in Power BI Desktop che è ancora lento. Per determinare le query inviate all'origine sottostante da Power BI Desktop, usare l'[analizzatore prestazioni](desktop-performance-analyzer.md). È anche possibile visualizzare tracce e informazioni di diagnostica che possono essere emesse dall'origine dati sottostante. Le tracce possono anche contenere dettagli utili sull'esecuzione della query e su come migliorarla.

Inoltre, anche in assenza di tali tracce nell'origine, è possibile visualizzare le query inviate da Power BI e i relativi tempi di esecuzione, come descritto nella sezione seguente.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Determinazione delle query inviate da Power BI Desktop

Per impostazione predefinita, Power BI Desktop registra gli eventi di una sessione specifica in un file di traccia denominato *FlightRecorderCurrent.trc*.

Per alcune origini DirectQuery, questo log include tutte le query inviate all'origine dati sottostante. Le origini DirectQuery rimanenti verranno incluse in futuro. Le origini che inviano query al log sono le seguenti:

* SQL Server
* Database SQL di Azure
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

Il file di traccia si trova nella cartella *AppData* dell'utente corrente:

*\<Utente>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces*

Per accedere a questa cartella, in Power BI Desktop selezionare **File** > **Opzioni e impostazioni** > **Opzioni** e quindi **Diagnostica**. Viene visualizzata la finestra di dialogo seguente:

![Collegamento per aprire la cartella delle tracce](media/desktop-directquery-about/directquery-about_06.png)

Quando si seleziona **Apre la cartella delle tracce o dei dump di arresto anomalo del sistema** in **Opzioni di diagnostica** si aprirà la cartella seguente: *\<Utente>\AppData\Local\Microsoft\Power BI Desktop\Traces*.

Passando alla cartella padre di tale cartella, verrà visualizzata la cartella contenente *AnalysisServicesWorkspaces*, che conterrà una cartella dell'area di lavoro per ogni istanza aperta di Power BI Desktop. Queste cartelle sono denominate con un suffisso intero, ad esempio *AnalysisServicesWorkspace2058279583*.

All'interno di questa cartella c'è una cartella *\\Data*. Contiene il file di traccia *FlightRecorderCurrent.trc* per la sessione corrente di Power BI. La cartella dell'area di lavoro corrispondente viene eliminata al termine della sessione di Power BI Desktop associata.

I file di traccia possono essere letti con lo strumento *SQL Server Profiler*, incluso nel download gratuito di [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).

Dopo aver scaricato e installato SQL Server Management Studio, eseguire SQL Server Profiler.

![SQL Server Profiler](media/desktop-directquery-about/directquery-about_07.png)

Per aprire il file di traccia eseguire questa procedura:

1. In SQL Server Profiler selezionare **File** > **Apri** > **File di traccia**.

1. Immettere il percorso del file di traccia per la sessione di Power BI attualmente aperta, ad esempio: *C:\Utenti\<utente>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data*.

1. Aprire *FlightRecorderCurrent.trc*.

Vengono visualizzati tutti gli eventi dalla sessione corrente. L'esempio con annotazioni illustrato di seguito evidenzia i gruppi di eventi. Ogni gruppo presenta gli eventi seguenti:

* Un evento `Query Begin` e `Query End`, che rappresenta l'inizio e la fine di una query DAX generata dall'interfaccia utente, ad esempio da un oggetto visivo o dalla compilazione di un elenco di valori nell'interfaccia utente del filtro.
* Una o più coppie di eventi `DirectQuery Begin` e `DirectQuery End`, che rappresentano una query inviata all'origine dati sottostante, nell'ambito della valutazione della query DAX.

È possibile eseguire più query DAX in parallelo, quindi con possibilità di interfoliazione degli eventi di diversi gruppi. Il valore di `ActivityID` può essere usato per determinare gli eventi appartenenti allo stesso gruppo.

![SQL Server Profiler con gli eventi Query Begin e Query End](media/desktop-directquery-about/directquery-about_08.png)

Di seguito sono riportate altre colonne di interesse:

* **TextData:** dettagli testuali dell'evento. I dettagli degli eventi `Query Begin/End` costituiscono la query DAX. I dettagli degli eventi `DirectQuery Begin/End` costituiscono la query SQL inviata all'origine sottostante. Nell'area in basso viene anche visualizzato l'elemento **TextData** per l'evento selezionato.
* **EndTime:** data/ora in cui l'evento è terminato.
* **Duration:** tempo in millisecondi impiegato per eseguire la query DAX o SQL.
* **Error:** indica se si è verificato un errore. In quel caso l'evento verrà anche visualizzato in rosso.

Nell'immagine precedente alcune delle colonne meno interessanti sono state ristrette per consentire una visualizzazione più agevole di altre colonne.

L'approccio consigliato per l'acquisizione di una traccia utile per la diagnosi di un potenziale problema di prestazioni è il seguente:

* Aprire una singola sessione di Power BI Desktop per evitare la confusione di più cartelle di aree di lavoro.
* Eseguire il set di azioni di interesse in Power BI Desktop. Includere alcune azioni aggiuntive per assicurare che gli eventi di interesse vengano scaricati nel file di traccia.
* Aprire SQL Server Profiler ed esaminare la traccia, come descritto in precedenza. Tenere presente che se si chiude Power BI Desktop il file di traccia viene eliminato. Inoltre, le ulteriori azioni in Power BI Desktop non vengono visualizzate immediatamente: è necessario chiudere e riaprire il file di traccia per vedere i nuovi eventi.
* Mantenere le singole sessioni relativamente ridotte (10 secondi di azioni, non centinaia), per semplificare l'interpretazione del file di traccia. C'è anche un limite applicato alle dimensioni del file stesso, dal quale, nel caso di sessioni di lunga durata, possono essere eliminati gli eventi meno recenti.

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Informazioni sul formato delle query inviate da Power BI Desktop

Il formato generale delle query create e inviate da Power BI Desktop usa selezioni secondarie per ognuna delle tabelle a cui si fa riferimento. La query dell'editor di query definisce la selezione secondaria. Si supponga ad esempio che siano presenti le tabelle TPC-DS seguenti in SQL Server:

![Tabelle TPC-DS in SQL Server](media/desktop-directquery-about/directquery-about_09.png)

Si consideri la query seguente:

![Query di esempio](media/desktop-directquery-about/directquery-about_10.png)

La query avrà come risultato l'oggetto visivo seguente:

![Risultato visivo di una query](media/desktop-directquery-about/directquery-about_11.png)

L'aggiornamento dell'oggetto visivo avrà come risultato la query SQL illustrata qui. Come si può vedere sono disponibili tre selezioni secondarie per `Web Sales`, `Item` e `Date_dim` e ognuna restituisce tutte le colonne nella rispettiva tabella, anche se l'oggetto visivo fa effettivamente riferimento solo a quattro colonne. Le query ombreggiate nelle selezioni secondarie sono esattamente il risultato delle query definite nell'editor di query. Questo uso delle selezioni secondarie non sembra influire sulle prestazioni per le origini dati supportate finora per DirectQuery. Origini dati come SQL Server ottimizzano i riferimenti alle altre colonne.

Power BI usa questo modello perché la query SQL usata può essere fornita direttamente dall'analista. La query viene usata "così come è", senza riscriverla.

![Query SQL usata così com'è](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Passaggi successivi

Questo articolo descrive aspetti di DirectQuery comuni a tutte le origini dati. Alcuni dettagli sono specifici delle singole origini. Vedere gli articoli seguenti relativi a origini specifiche:

* [DirectQuery and SAP HANA](desktop-directquery-sap-hana.md) (DirectQuery e SAP HANA)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)

Per altre informazioni su DirectQuery, vedere la risorsa seguente:

* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
