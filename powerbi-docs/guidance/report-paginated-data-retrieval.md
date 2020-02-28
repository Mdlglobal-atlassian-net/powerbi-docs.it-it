---
title: Linee guida per il recupero dei dati per i report impaginati
description: Linee guida per la creazione di origini dati e set di dati per i report impaginati di Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 1da75b14f628c8c765ea89a34dd2a2665cdf9a4b
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530442"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Linee guida per il recupero dei dati per i report impaginati

Questo articolo è rivolto agli autori di report che progettano [report impaginati](../paginated-reports-report-builder-power-bi.md) di Power BI. Offre indicazioni utili per progettare un recupero dei dati efficace ed efficiente.

## <a name="data-source-types"></a>Tipi di origini dati

I report impaginati supportano in modo nativo le origini dati relazionali e analitiche. Queste origini sono ulteriormente categorizzate, come basate sul cloud o archiviate in locale. Le origini dati locali, ospitate in locale o in una macchina virtuale, richiedono un gateway dati per consentire la connessione di Power BI. Le origini dati basate sul cloud consentono invece a Power BI di connettersi direttamente tramite Internet.

Se è possibile scegliere il tipo di origine dati, ad esempio nel caso di un nuovo progetto, è consigliabile usare origini dati basate sul cloud. I report impaginati possono connettersi con una latenza di rete inferiore, soprattutto quando le origini dati si trovano nella stessa area del tenant di Power BI. È inoltre possibile connettersi a queste origini usando l'accesso Single Sign-On (SSO). Ciò significa che l'identità dell'utente del report può essere passata all'origine dati, consentendo l'applicazione di autorizzazioni a livello di riga per utente. Attualmente, l'accesso SSO non è supportato per le origini dati locali. In altre parole, SQL Server Analysis Services non può applicare autorizzazioni a livello di riga per utente.

> [!NOTE]
> Anche se non è attualmente possibile connettersi a database locali tramite SSO, è comunque possibile applicare autorizzazioni a livello di riga. A tale scopo, passare il campo predefinito **UserID** a un parametro della query del set di dati. L'origine dati dovrà archiviare i valori del nome dell'entità utente (UPN) in modo da poter filtrare correttamente i risultati della query.
>
> Si supponga, ad esempio, che ogni venditore venga archiviato come riga nella tabella **Venditori**.  La tabella contiene colonne per l'UPN e anche per l'area di vendita del venditore. In fase di query, la tabella viene filtrata in base all'UPN dell'utente del report ed è anche correlata ai fatti di vendita tramite un inner join. In questo modo, la query filtra anche le righe dei fatti di vendita in base a quelle dell'area di vendita dell'utente del report.

### <a name="relational-data-sources"></a>Origini dati relazionali

In genere le origini dati relazionali sono ideali per i report di tipo operativo, ad esempio le fatture di vendita. Sono inoltre adatte ai report che devono recuperare set di dati di dimensioni molto grandi (oltre le 10.000 righe). Le origini dati relazionali possono anche definire stored procedure, che possono essere eseguite dai set di dati dei report. Le stored procedure offrono diversi vantaggi:

- Parametrizzazione
- Incapsulamento della logica di programmazione, che consente di preparare i dati più complessi, ad esempio tabelle temporanee, cursori o funzioni scalari definite dall'utente.
- Miglioramento della gestibilità, che consente di semplificare l'aggiornamento della logica delle stored procedure. In alcuni casi può essere eseguita senza dover modificare e ripubblicare i report impaginati, purché i nomi di colonna e i tipi di dati rimangano invariati.
- Prestazioni migliori, perché i piani di esecuzione vengono memorizzati nella cache per essere riutilizzati
- Riutilizzo di stored procedure in più report

In Power BI Report Builder è possibile usare lo strumento di progettazione di query relazionali per creare graficamente un'istruzione di query, ma solo per le origini dati Microsoft.

### <a name="analytic-data-sources"></a>Origini dati analitiche

Le origini dati analitiche sono particolarmente adatte ai report operativi e analitici e possono restituire velocemente risultati di query riepilogativi anche su volumi di dati molto grandi. Le misure e gli indicatori KPI del modello possono incapsulare regole di business complesse per ottenere un riepilogo dei dati. Queste origini dati non sono tuttavia adatte ai report che devono recuperare set di dati di dimensioni molto grandi (oltre 10.000 righe).

In Power BI Report Builder è possibile scegliere tra due strumenti di progettazione di query: Lo strumento di progettazione di query DAX di Analysis Services e quello di query MDX di Analysis Services. Questi strumenti di progettazione possono essere usati per le origini dati dei set di dati di Power BI o per qualsiasi modello di SQL Server Analysis Services o Azure Analysis Services, tabulare o multidimensionale.

È consigliabile usare lo strumento di progettazione di query DAX, purché che soddisfi pienamente le proprie esigenze di query. Se il modello non definisce le misure necessarie, è necessario passare alla modalità query. In questa modalità è possibile personalizzare l'istruzione di query aggiungendo espressioni (per il riepilogo dei dati).

Per l'uso dello strumento di progettazione di query MDX è necessario che il modello includa misure. Questo strumento presenta due funzionalità che non sono supportate dallo strumento di progettazione di query DAX. In particolare, consente di eseguire queste operazioni:

- Definire i membri calcolati a livello di query (in MDX).
- Configurare le aree dati in modo da richiedere [aggregati di server](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) in gruppi non di dettaglio. Se il report deve presentare riepiloghi di misure semiadditive o non additive (ad esempio calcoli di Business Intelligence temporali o conteggi distinti), è probabile che l'uso di aggregati di server risulti più efficiente rispetto al recupero di righe di dettaglio di basso livello e al calcolo dei riepiloghi del report.

## <a name="query-result-size"></a>Dimensione dei risultati della query

È in genere consigliabile recuperare solo i dati necessari per il report. Evitare quindi di recuperare le colonne o le righe che non sono necessarie per il report.

Per limitare le righe, si dovrebbero sempre applicare i filtri più restrittivi e definire query di aggregazione. Le query di aggregazione raggruppano e riepilogano i dati di origine per recuperare i risultati con maggiore granularità. Si supponga, ad esempio, che il report debba presentare un riepilogo delle vendite dei venditori. Invece di recuperare tutte le righe degli ordini di vendita, creare una query del set di dati che raggruppa i dati per venditore e riepiloga le vendite per ogni gruppo.

## <a name="expression-based-fields"></a>Campi basati su espressioni

È possibile estendere un set di dati del report con campi basati su espressioni. Se, ad esempio, il set di dati è l'origine del nome e del cognome del cliente, può essere opportuno definire un campo che concatena i due campi per generare il nome completo del cliente. Per ottenere questo calcolo, sono disponibili due opzioni. è possibile:

- Creare un _campo calcolato_, ovvero un campo del set di dati basato su un'espressione.
- Inserire un'espressione direttamente nella query del set di dati (usando la lingua nativa dell'origine dati), che abbia come risultato un normale campo del set di dati.

È consigliabile usare la seconda opzione, quando possibile. Esistono due buoni motivi per cui è preferibile inserire espressioni direttamente nella query del set di dati:

- È possibile che l'origine dati sia ottimizzata per valutare l'espressione in modo più efficiente rispetto a Power BI (in particolare per i database relazionali).
- Le prestazioni del report sono migliori perché Power BI non deve materializzare i campi calcolati prima del rendering del report. I campi calcolati possono aumentare notevolmente il tempo necessario per il rendering del report quando i set di dati recuperano un numero elevato di righe.

## <a name="field-names"></a>Nomi dei campi

Quando si crea un set di dati, ai campi vengono assegnati automaticamente i nomi delle colonne della query. È possibile che questi nomi non siano semplici o intuitivi. È inoltre possibile che i nomi delle colonne della query di origine contengano caratteri non consentiti negli identificatori di oggetto RDL (Report Definition Language), ad esempio spazi e simboli. In questo caso, i caratteri non consentiti vengono sostituiti con un carattere di sottolineatura (_).

È consigliabile verificare innanzitutto che tutti i nomi dei campi siano semplici e concisi, benché significativi. In caso contrario, è consigliabile rinominarli _prima_ di avviare la generazione del layout del report. Questo perché i campi rinominati non trasferiscono le modifiche alle espressioni usate nel layout del report. Se si decide di rinominare i campi dopo aver avviato la generazione del layout del report, sarà necessario trovare e aggiornare tutte le espressioni che presentano interruzioni.

## <a name="filter-vs-parameter"></a>Filtri e parametri a confronto

È probabile che le progettazioni di report impaginati includano parametri di report. Questi parametri vengono in genere usati per richiedere all'utente di filtrare il report. Gli autori di report impaginati hanno a disposizione due modi per consentire l'applicazione di filtri ai report. Possono eseguire il mapping di un parametro del report agli elementi seguenti:

- Un _filtro_ del set di dati. In tal caso, i valori del parametro del report vengono usati per filtrare i dati già recuperati dal set di dati.
- Un _parametro_ del set di dati. In tal caso, i valori del parametro del report vengono inseriti nella query nativa inviata all'origine dati.

> [!NOTE]
> Tutti i set di dati del report vengono memorizzati nella cache _a livello di singola sessione_ per un massimo di 10 minuti _dall'ultimo utilizzo_. Un set di dati può essere riutilizzato quando si inviano nuovi valori di parametro (filtro), si esegue il rendering del report in un formato diverso o si interagisce in qualche modo con la progettazione del report, ad esempio attivando la visibilità o modificando l'ordinamento.

Si consideri, ad esempio, un report relativo alle vendite con un solo parametro per filtrare i dati di un singolo anno. Il set di dati recupera le vendite per _tutti gli anni_. Questo avviene perché il parametro del report è mappato ai filtri del set di dati. Nel report vengono visualizzati i dati relativi all'anno richiesto, ovvero un subset del set di dati. Quando l'utente del report modifica il parametro del report impostando un anno diverso e quindi visualizza il report, Power BI non deve recuperare i dati dall'origine, ma semplicemente applicare un filtro diverso al set di dati già memorizzato nella cache. Quando il set di dati è memorizzato nella cache, l'applicazione di filtri può essere molto veloce.

Si consideri ora una diversa progettazione del report. Questa volta viene eseguito il mapping del parametro del report relativo all'anno delle vendite a un parametro del set di dati. Power BI inserisce quindi il valore dell'anno nella query nativa e il set di dati recupera i dati solo per tale anno. Ogni volta che l'utente del report modifica il valore del parametro relativo all'anno, e quindi visualizza il report, il set di dati recupera un nuovo risultato della query solo per tale anno.

Entrambi gli approcci di progettazione possono filtrare i dati del report ed entrambe le soluzioni possono essere usate per le progettazioni di report. La soluzione ottimale, tuttavia, dipenderà dai volumi di dati previsti, dalla volatilità dei dati e dai comportamenti previsti degli utenti del report.

È consigliabile adottare la soluzione basata sull'_applicazione di un filtro al set di dati_ quando si prevede che vengano usati più volte subset diversi di righe del set di dati. Questa soluzione consente di infatti di risparmiare il tempo di rendering perché non comporta il recupero di nuovi dati. In questo scenario è evidente che il costo legato al recupero di un set di dati più grande può essere controbilanciato dal numero di volte in cui verrà riutilizzato. Una soluzione di questo tipo è quindi utile per le query la cui generazione richiede molto tempo. Prestare tuttavia attenzione al fatto che la memorizzazione nella cache di set di dati di grandi dimensioni per singolo utente può influire negativamente sulle prestazioni e sulla velocità effettiva della capacità.

È consigliabile adottare la soluzione basata sulla _parametrizzazione del set di dati_ quando è poco probabile che venga richiesto un subset diverso di righe del set di dati oppure quando il numero di righe da filtrare è presumibilmente molto grande (e quindi la memorizzazione nella cache può risultare poco efficiente). Questo approccio di progettazione è efficace anche quando l'archivio dati è volatile. In questo caso, ogni modifica del valore del parametro del report comporterà il recupero dei dati aggiornati.

## <a name="non-native-data-sources"></a>Origini dati non native

Se è necessario sviluppare report impaginati basati su origini dati che non sono [supportate in modo nativo dai report impaginati](../paginated-reports-data-sources.md), è possibile sviluppare prima di tutto un modello di dati di Power BI Desktop. In questo modo, è possibile connettersi a più di 100 [origini dati di Power BI](../power-bi-data-sources.md). Dopo la pubblicazione nel servizio Power BI, è possibile sviluppare un report impaginato che si connette al set di dati di Power BI.

## <a name="data-integration"></a>Integrazione dei dati

Se è necessario combinare dati da più origini dati, sono disponibili due opzioni:

- **Combinare i set di dati del report**: se le origini dati sono [supportate in modo nativo dai report impaginati](../paginated-reports-data-sources.md), è possibile creare campi calcolati che usano le funzioni [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) o [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) di Report Builder.
- **Sviluppare un modello di Power BI Desktop**: è tuttavia probabilmente più efficiente sviluppare un modello di dati in Power BI Desktop. È possibile usare Power Query per combinare query basate su qualsiasi [origine dati supportata](../power-bi-data-sources.md). Dopo la pubblicazione nel servizio Power BI, è possibile sviluppare un report impaginato che si connette al set di dati di Power BI.

## <a name="sql-server-complex-data-types"></a>Tipi di dati complessi di SQL Server

Poiché SQL Server è un'origine dati locale, Power BI deve connettersi tramite un gateway. Quest'ultimo, tuttavia, non supporta il recupero di dati per tipi di dati complessi, tra cui i [tipi di dati spaziali](/sql/relational-databases/spatial/spatial-data-sql-server) GEOMETRY e GEOGRAPHY e [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). Sono anche inclusi i tipi definiti dall'utente implementati tramite una classe di un assembly in Microsoft .NET Framework Common Language Runtime (CLR).

Per tracciare i dati spaziali e le analisi nella visualizzazione mappa sono necessari i dati spaziali di SQL Server. Non è quindi possibile usare la visualizzazione mappa quando SQL Server è l'origine dati. Questo è invece possibile se l'origine dati è il database SQL di Azure, perché in tal caso Power BI non si connette tramite un gateway.

## <a name="data-related-images"></a>Immagini correlate ai dati

È possibile usare le immagini per aggiungere logo o foto al layout del report. Quando le immagini sono correlate alle righe recuperate da un set di dati del report, sono disponibili due opzioni:

- È possibile che i dati dell'immagine siano recuperabili anche dall'origine dati, se già archiviati in una tabella.
- Quando le immagini vengono archiviate in un server Web, è possibile usare un'espressione dinamica per creare il percorso dell'URL dell'immagine.

Per altre informazioni e suggerimenti, vedere [Linee guida per l'uso di immagini nei report impaginati](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Recupero dei dati ridondanti

È possibile che il report recuperi dati ridondanti. Questo può verificarsi quando si eliminano campi di query del set di dati o se nel report sono presenti set di dati inutilizzati. Evitare situazioni di questo tipo, perché comportano un carico di lavoro superfluo sulle origini dati, la rete e le risorse di capacità di Power BI.

### <a name="deleted-query-fields"></a>Campi della query eliminati

Nella pagina **Campi** della finestra **Proprietà set di dati** è possibile eliminare i _campi della query_ del set di dati (i campi della query sono mappati alle colonne recuperate dalla query del set di dati). In questo caso, tuttavia, Report Builder non rimuove le colonne corrispondenti dalla query del set di dati.

Se è necessario eliminare campi della query dal set di dati, è consigliabile rimuovere le colonne corrispondenti dalla query. Report Builder eliminerà automaticamente eventuali campi della query ridondanti. Se si eliminano i campi della query, assicurarsi di modificare anche l'istruzione della query del set di dati in modo da rimuovere le colonne.

### <a name="unused-datasets"></a>Set di dati inutilizzati

Quando si esegue un report, vengono valutati tutti i set di dati, anche se non sono associati a oggetti di report. Per questo motivo, assicurarsi di rimuovere tutti i set di dati di test o di sviluppo prima di pubblicare un report.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Origini dati supportate per i report impaginati di Power BI](../paginated-reports-data-sources.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
