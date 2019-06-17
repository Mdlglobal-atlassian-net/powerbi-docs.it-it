---
title: Che cos'è Microsoft Power BI Premium?
description: Power BI Premium offre capacità dedicate all'organizzazione o al team, con prestazioni più affidabili e volumi di dati superiori, senza richiedere l'acquisto di licenze per ogni utente.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/22/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1c2f867140c5a717c80d39db75b3a54e40bd1e34
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721060"
---
# <a name="what-is-power-bi-premium"></a>Che cos'è Power BI Premium?

Power BI Premium offre risorse dedicate e avanzate per l'esecuzione del servizio Power BI per l'organizzazione. ad esempio:

- Maggiore scalabilità e prestazioni migliori
- Flessibilità di acquisire le licenze in base alla capacità
- Unificazione della business intelligence self-service e aziendale
- Estensione della business intelligence locale con Server di report di Power BI
- Supporto della residenza dei dati per area (Multi-Geo)
- Condivisione dei dati con tutti gli utenti senza la necessità di acquistare una licenza per utente

Questo articolo non offre informazioni dettagliate su ogni funzione di Power BI Premium ma ne offre una panoramica. Dove necessario, sono forniti collegamenti a ulteriori articoli con informazioni più dettagliate.

## <a name="subscriptions-and-licensing"></a>Sottoscrizioni e licenze

Power BI Premium è una sottoscrizione di Office 365 a livello di tenant disponibile in due famiglie di SKU (Stock-Keeping Unit):

- SKU **EM** (EM1-EM3) per l'incorporamento, richiedono un impegno annuale, con fatturazione mensile. Le SKU EM1 ed EM2 sono disponibili solo attraverso piani di contratti multilicenza. L'acquisto diretto non è possibile.
- SKU **P** (P1-P3) per l'incorporamento e funzionalità Enterprise, richiedono un impegno mensile o annuale, con fatturazione mensile e includono una licenza per l'installazione di Server di report di Power BI in locale.

Un approccio alternativo consiste nell'acquistare una sottoscrizione **Azure Power BI Embedded** con una singola famiglia di SKU **A** (A1-A6) per l'incorporamento e a solo scopo di test delle capacità. Sebbene tutte le SKU offrano memorie centrali virtuali per creare le capacità, le SKU EM sono limitati a un incorporamento di scalabilità minore. Le SKU EM1, EM2, A1 e A2 con meno di quattro memorie centrali virtuali non vengono eseguite in un'infrastruttura dedicata.

Sebbene in questo articolo siano descritte le SKU P, molte delle informazioni fornite si applicano anche alle SKU A. A differenza delle SKU della sottoscrizione Premium, le SKU di Azure non richiedono un impegno per un periodo di tempo e vengono fatturare su base oraria. Offrono la massima elasticità permettendo aumenti, riduzioni, sospensioni, ripristini ed eliminazioni. 

Azure Power BI Embedded esula dall'argomento di questo articolo, ma è descritto nella sezione [Approcci per i test](service-premium-capacity-optimize.md#testing-approaches) dell'articolo Ottimizzazione delle capacità Premium come opzione pratica ed economica per eseguire test e misurare i carichi di lavoro. Per altre informazioni sulle SKU di Azure, vedere la [documentazione di Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Acquisto

Le sottoscrizioni di Power BI Premium vengono acquistate dagli amministratori nell'interfaccia di amministrazione di Microsoft 365. In particolare, solo gli amministratori globali di Office 365 o gli amministratori fatturazione possono acquistare le SKU. Dopo l'acquisto, il tenant riceve un numero corrispondente di memorie centrali virtuali per l'assegnazione delle capacità, chiamati *pool di vCore*. Ad esempio, l'acquisto di una SKU P3 fornisce al tenant 32 memorie centrali virtuali. Per altre informazioni, vedere [Come acquistare Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Capacità dedicate

Con Power BI Premium si ottengono *capacità dedicate*. A differenza di una capacità condivisa in cui i carichi di lavoro vengono eseguiti in risorse di elaborazione condivise con altri clienti, una capacità dedicata è destinata all'uso esclusivo da parte di un'organizzazione. La capacità dedicata è isolata con risorse di elaborazione dedicate che offrono prestazioni affidabili e coerenti per il contenuto ospitato. 

Le aree di lavoro si trovano all'interno delle capacità. Ogni utente di Power BI ha un'area di lavoro chiamata **Area di lavoro personale**. È possibile creare aree di lavoro aggiuntive per la collaborazione e la distribuzione. Queste aree di lavoro sono chiamate **Aree di lavoro per le app**. Per impostazione predefinita, le aree di lavoro, incluse le aree di lavoro personale, vengono create nella capacità condivisa. Quando si hanno le capacità Premium, le aree di lavoro personali e le aree di lavoro per le app possono essere assegnate alle capacità Premium.

### <a name="capacity-nodes"></a>Nodi delle capacità

Come descritto nella sezione [Sottoscrizioni e licenze](#subscriptions-and-licensing), sono disponibili due famiglie di SKU di Power BI Premium: **EM** e **P**. Tutte le SKU di Power BI Premium sono disponibili come *nodi* delle capacità e ogni nodo rappresenta una quantità impostata di risorse costituite da processore, memoria e archiviazione. Oltre alle risorse, ogni SKU ha limiti operativi relativi al numero di connessioni DirectQuery e dinamiche al secondo e al numero di aggiornamenti di modello paralleli.

L'elaborazione avviene tramite un determinato numero di vCore, suddiviso equamente tra back-end e front-end.

I **vCore di back-end** sono responsabili della funzionalità di Power BI relativa alla memoria centrale che include elaborazione delle query, gestione della cache, esecuzione dei servizi R, aggiornamento dei modelli, elaborazione del linguaggio naturale (Domande e risposte) e rendering lato server di report e immagini. Ai vCore di back-end viene assegnata una quantità fissa di memoria che viene usata principalmente per ospitare i modelli, chiamati anche set di dati attivi.

I **vCore di front-end** sono responsabili della gestione dei documenti relativi a servizio Web, dashboard e report, della gestione dei diritti di accesso, della pianificazione, delle API, dei caricamenti e dei download e in genere di tutto ciò che riguarda l'esperienza utente.

L'archiviazione è impostata su **100 TB per nodo di capacità**.

Le risorse e i limiti di ogni SKU Premium (e della SKU A di dimensioni equivalenti) sono descritti nella tabella seguente:

| Nodi delle capacità | Totale vCore | vCore back-end | RAM (GB) | vCore front-end | Connessione dinamica/DirectQuery (al secondo) | Parallelismo di aggiornamento dei modelli |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>Carichi di lavoro delle capacità

I carichi di lavoro delle capacità sono servizi resi disponibili agli utenti. Per impostazione predefinita, le capacità Premium e Azure supportano solo il carico di lavoro di un set di dati associato all'esecuzione delle query di Power BI. Il carico di lavoro del set di dati non può essere disabilitato. È possibile abilitare carichi di lavoro aggiuntivi per [intelligenza artificiale (Servizi cognitivi)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [flussi di dati](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) e [report impaginati](paginated-reports-save-to-power-bi-service.md). Questi carichi di lavoro sono supportati solo nelle sottoscrizioni Premium. 

Ogni carico di lavoro aggiuntivo consente di configurare la memoria massima (come percentuale della memoria totale disponibile) che può essere usata dal carico di lavoro. I valori predefiniti per la memoria massima sono determinati dalla SKU. È possibile ottimizzare le risorse disponibili della capacità abilitando solo i carichi di lavoro aggiuntivi in uso. È possibile modificare le impostazioni della memoria solo quando le impostazioni predefinite determinate non soddisfano i requisiti relativi alle risorse della capacità. Gli amministratori delle capacità possono abilitare e configurare i carichi di lavoro per una capacità usando **Impostazioni di capacità** nel [portale di amministrazione](service-admin-portal.md) o usando le [API REST Capacità](https://docs.microsoft.com/rest/api/power-bi/capacities).  

![Abilitare i carichi di lavoro](media/service-admin-premium-workloads/admin-portal-workloads.png)

Per altre informazioni, vedere [Configurare i carichi di lavoro in una capacità Premium](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Come funzionano le capacità

Il servizio Power BI usa sempre al meglio le risorse delle capacità senza superare i limiti imposti sulla capacità.

Le operazioni della capacità sono classificate come *interattive* o *in background*. Le operazioni interattive includono il rendering delle richieste e la risposta alle interazioni dell'utente (applicazione di filtri, query su Domande e risposte e così via). In generale, l'esecuzione di query su un modello di importazione ha un utilizzo elevato delle risorse di memoria, mentre l'esecuzione di query su modelli di connessione DirectQuery e dinamica ha un utilizzo elevato della CPU. Le operazioni in background includono gli aggiornamenti dei flussi di dati e dei modelli di importazione e la memorizzazione nella cache delle query sui dashboard.

È importante sapere che le operazioni interattive hanno sempre priorità sulle operazioni in background per garantire la miglior esperienza utente. Se non sono presenti risorse sufficienti, le operazioni in background vengono aggiunte a una coda per essere elaborate quando si liberano le risorse. Le operazioni in background, come gli aggiornamenti dei set di dati, possono essere arrestate durante l'elaborazione dal servizio Power BI e aggiunte a una coda.

I modelli di importazione devono essere caricati completamente nella memoria per poter essere sottoposti a query o aggiornati. Il servizio Power BI gestisce l'utilizzo della memoria con algoritmi sofisticati per garantire il massimo utilizzo della memoria disponibile e può causare un commit eccessivo della capacità: Sebbene sia possibile per una capacità archiviare più modelli di importazione (fino a 100 TB per capacità Premium), quando l'archiviazione su disco combinata supera la memoria supportata (ed è necessario memoria aggiuntiva per le query e l'aggiornamento), non è possibile caricare tutti i modelli in memoria contemporaneamente.

Per questa ragione, i modelli di importazione vengono caricati e rimossi dalla memoria in base all'utilizzo. Un modello di importazione viene caricato quando vengono eseguite query (operazione interattiva) e non è ancora stato caricato in memoria o quando deve essere aggiornato (operazione in background).

L'eliminazione di un modello dalla memoria è chiamata *rimozione*. È un'operazione che Power BI può eseguire rapidamente a seconda delle dimensioni dei modelli. Se non si verifica alcun problema di memoria per la capacità, i modelli vengono semplicemente caricati e mantenuti in memoria. Tuttavia, quando la memoria non è sufficiente per caricare un modello, il servizio Power BI dovrà innanzitutto liberare memoria. Il servizio libera la memoria individuando i modelli inattivi cercando i modelli che non sono stati usati negli ultimi tre minuti \[[1](#endnote-1)\] e quindi rimuovendoli. Se non sono presenti modelli inattivi da rimuovere, il servizio Power BI effettua una ricerca per rimuovere i modelli caricati per le operazioni in background. Un'ultima possibilità, dopo 30 secondi di tentativi non riusciti \[[1](#endnote-1)\], consiste nel bloccare l'operazione interattiva. In questo caso, l'utente del report riceve una notifica di errore con il suggerimento di riprovare più tardi. In alcuni casi è possibile che i modelli vengano scaricati dalla memoria a causa di operazioni del servizio.

È importante sottolineare che la rimozione dei set di dati è un comportamento normale e previsto. Questo comportamento mira a ottimizzare l'utilizzo della memoria tramite il caricamento e lo scaricamento dei modelli con dimensioni combinate che possono superare la memoria disponibile. Si tratta di un comportamento legato alla progettazione e completamente trasparente agli utenti dei report. Percentuali di rimozione elevate non indicano necessariamente che la capacità non include risorse sufficienti. Potrebbero tuttavia rappresentare un problema nel caso in cui abbiano effetti negativi sulla velocità di risposta alle query o agli aggiornamenti.

Gli aggiornamenti dei modelli di importazione comportano sempre un utilizzo intensivo della memoria poiché i modelli devono essere caricati in memoria. Per l'elaborazione è necessaria memoria aggiuntiva. Un aggiornamento completo può usare circa il doppio della quantità di memoria necessaria per il modello. Ciò garantisce la possibilità di eseguire query sul modello anche durante l'elaborazione (poiché le query vengono inviate al modello esistente) fino a quando non viene completato l'aggiornamento e non sono disponibili i nuovi dati del modello. L'aggiornamento incrementale richiederà meno memoria e potrà essere completato più rapidamente riducendo sostanzialmente l'utilizzo elevato delle risorse della capacità. Anche gli aggiornamenti possono richiedere un utilizzo elevato della CPU per i modelli, in particolari quelli con trasformazioni Power Query complesse o tabelle/colonne calcolate complesse o basate su tabelle di grandi dimensioni.

Gli aggiornamenti, analogamente alle query, richiedono il caricamento del modello in memoria. Se la memoria non è sufficiente, il servizio Power BI tenta di rimuovere i modelli inattivi e, se l'operazione non è possibile (poiché tutti i modelli sono attivi), il processo di aggiornamento viene inserito in coda. Gli aggiornamenti richiedono in genere un utilizzo elevato della CPU, ancora di più delle query. Per questa ragione, sono presenti limiti della capacità relativi al numero di aggiornamenti simultanei che è impostato su 1,5 moltiplicato per il numero di vCore di back-end arrotondato. Se è presente un numero eccessivo di aggiornamenti simultanei, un aggiornamento pianificato verrà inserito in coda. Quando si verificano queste situazioni, il completamento dell'aggiornamento richiede più tempo. Gli aggiornamenti su richiesta, ad esempio quelli attivati da una richiesta utente o una chiamata API, eseguono tre tentativi \[[1](#endnote-1)\]. Se le risorse non sono ancora sufficienti, l'aggiornamento non viene eseguito.

Note della sezione:   
<a name="endnote-1"></a>\[1\] Soggetto a modifiche.

### <a name="regional-support"></a>Supporto locale

Quando si crea una nuova capacità, gli amministratori globali di Office 365 e gli amministratori del servizio Power BI possono specificare un'area in cui si trovano le aree di lavoro assegnate alla capacità. Questa funzionalità è chiamata **Multi-Geo**. Con Multi-Geo, le organizzazioni possono soddisfare i requisiti di residenza dei dati distribuendo il contenuto ai data center in un'area specifica, anche se l'area non corrisponde all'area della sottoscrizione Office 365. Per altre informazioni, vedere [Supporto Multi-Geo per Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Gestione delle capacità

La gestione delle capacità Premium comporta creazione o eliminazione delle capacità, assegnazione degli amministratori, assegnazione delle aree di lavoro, configurazione dei carichi di lavoro, monitoraggio e modifiche per l'ottimizzazione delle prestazioni della capacità. 

Gli amministratori globali di Office 365 e gli amministratori del servizio Power BI possono creare le capacità Premium dai vCore disponibili o modificare le capacità Premium esistenti. Quando viene creata una capacità, vengono specificate le dimensioni e l'area geografica della capacità e viene assegnato almeno un amministratore della capacità. 

Quando vengono create le capacità, la maggior parte delle attività amministrative vengono eseguite nel [portale di amministrazione](service-admin-portal.md).

![Portale di amministrazione](media/service-premium-what-is/premium-admin-portal.png)

Gli amministratori della capacità possono assegnare le aree di lavoro alla capacità, gestire le autorizzazioni utente e assegnare altri amministratori. Gli amministratori della capacità possono anche configurare i carichi di lavoro, modificare le allocazioni di memoria e, se necessario, riavviare una capacità reimpostando le operazioni in caso di overload della capacità.

![Portale di amministrazione](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Gli amministratori della capacità possono anche verificare che una capacità venga eseguita correttamente. Possono monitorare l'integrità della capacità direttamente nel portale di amministrazione o usando l'app per le metriche delle capacità Premium.

Per altre informazioni sulla creazione delle capacità, sull'assegnazione degli amministratori e sull'assegnazione delle aree di lavoro, vedere [Gestione delle capacità Premium](service-premium-capacity-manage.md). Per altre informazioni sui ruoli, vedere [Ruoli di amministratore correlati a Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Monitoraggio

Il monitoraggio delle capacità Premium consente agli amministratori di verificare le prestazioni delle capacità. È possibile monitorare le capacità nel portale di amministrazione o tramite l'[app per le metriche delle capacità Premium di Power BI](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

Il monitoraggio nel portale offre una visualizzazione rapida con metriche di alto livello che indicano i carichi e l'utilizzo medio delle risorse da parte della capacità negli ultimi sette giorni. 

![Portale di amministrazione](media/service-premium-what-is/premium-admin-portal-health.png)

L'app per le **metriche delle capacità Premium di Power BI** offre informazioni dettagliate sulle prestazioni delle capacità. L'app include un dashboard di alto livello e report più dettagliati.

![Dashboard dell'app per le metriche](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Nel dashboard dell'app è possibile fare clic sulla cella di una metrica per aprire un report dettagliato. I report offrono metriche dettagliate e una funzionalità di filtro per eseguire il drill-down sulle informazioni più importanti necessarie per eseguire correttamente le capacità.

![Picchi periodici delle attese delle query indicano una potenziale saturazione della CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Per altre informazioni sul monitoraggio delle capacità, vedere [Monitoraggio nel portale di amministrazione di Power BI](service-admin-premium-monitor-portal.md) e [Monitoraggio con l'app per le metriche delle capacità Premium di Power BI](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Ottimizzazione delle capacità

Usare al meglio le capacità è fondamentale per garantire le migliori prestazioni agli utenti e ottenere il maggior valore dall'investimento Premium. Il monitoraggio delle metriche chiave consente agli amministratori di individuare il modo migliore per risolvere i colli di bottiglia ed eseguire le azioni necessarie. Per altre informazioni, vedere [Ottimizzazione delle capacità Premium](service-premium-capacity-optimize.md) e [Scenari delle capacità Premium](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>API REST delle capacità

Le API REST di Power BI includono una raccolta di [API Capacità](https://docs.microsoft.com/rest/api/power-bi/capacities). Le API consentono agli amministratori di gestire a livello di codice molti aspetti delle capacità Premium, tra cui l'abilitazione e la disabilitazione dei carichi di lavoro, l'assegnazione di aree di lavoro a una capacità e altro ancora.

## <a name="large-datasets"></a>Set di dati di grandi dimensioni

A seconda della SKU, Power BI Premium supporta il caricamento di file modello di Power BI Desktop (file con estensione pbix) fino alle dimensioni massime di **10 GB**. Dopo il caricamento, il modello può essere pubblicato in un'area di lavoro assegnata a una capacità Premium. È quindi possibile aggiornare il set di dati fino alle dimensioni massime di **12 GB**.

### <a name="size-considerations"></a>Considerazioni sulle dimensioni

I modelli di grandi dimensioni possono richiedere un utilizzo elevato di risorse. Per i modelli con dimensioni maggiori di 1 GB è necessario avere almeno una SKU P1. Anche se la pubblicazione di modelli di grandi dimensioni in aree di lavoro supportate da SKU A fino ad A3 può funzionare, il relativo aggiornamento non funzionerà.

La tabella seguente descrive gli SKU consigliati in base alle dimensioni del file PBIX:

   |SKU  |Dimensioni PBIX   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | fino a 10 GB   |

Lo SKU A4 di Power BI Embedded equivale allo SKU P1, A5 = P2 e A6 = P3. Tenere presente che la pubblicazione di modelli di grandi dimensioni in SKU A ed EM può restituire errori non specifici dell'errore di limitazione delle dimensioni del modello nella capacità condivisa. È probabile che gli errori di aggiornamento per i modelli di grandi dimensioni in SKU A ed EM indichino il timeout. 

I file con estensione pbix rappresentano i dati in *stato di compressione molto elevata*. I dati si espanderanno più volte una volta caricati nella memoria e si espanderanno ulteriormente durante l'aggiornamento dei dati.

L'aggiornamento pianificato dei set di dati di grandi dimensioni può richiedere molto tempo e usare una quantità elevata di risorse. È importante evitare di pianificare un numero eccessivo di aggiornamenti sovrapposti. È consigliabile configurare l'[aggiornamento incrementale](service-premium-incremental-refresh.md) perché è più veloce, più affidabile e usa una quantità minore di risorse.

Il caricamento del report iniziale dei set di dati di grandi dimensioni può richiedere molto tempo se il set di dati non è stato usato di recente. La barra di caricamento per i report a caricamento prolungato visualizza lo stato di avanzamento dell'operazione.

Sebbene i vincoli di tempo e memoria per query siano molto più elevati nella capacità Premium, è consigliabile usare filtri e filtri dei dati per limitare la visualizzazione degli oggetti visivi solo a quelli necessari.

## <a name="incremental-refresh"></a>Aggiornamento incrementale

L'aggiornamento incrementale è parte integrante della gestione di set di dati di grandi dimensioni in Power BI Premium. L'aggiornamento incrementale offre diversi vantaggi. Ad esempio, gli aggiornamenti sono più rapidi poiché è necessario aggiornare solo i dati che sono stati modificati. Gli aggiornamenti sono più affidabili poiché non è necessario mantenere connessioni con esecuzione prolungata a origini dati volatili. L'utilizzo delle risorse risulta ridotto poiché l'aggiornamento di una minor quantità di dati riduce l'utilizzo complessivo della memoria e di altre risorse. I criteri di aggiornamento incrementale sono definiti in **Power BI Desktop** e vengono applicati quando vengono pubblicati in un'area di lavoro in una capacità Premium. 

![Dettagli aggiornamento dati](media/service-premium-incremental-refresh/refresh-details.png)

Per altre informazioni, vedere [Aggiornamento incrementale in Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Report impaginati

I report impaginati, supportati nelle SKU P1-P3 e A4_A6, sono basati sulla tecnologia Report Definition Language (RDL) in SQL Server Reporting Services. Sebbene basato sulla tecnologia RDL, non equivale a Server di report di Power BI che è una piattaforma di report scaricabile che è possibile installare in locale, inclusa anche in Power BI Premium. I report impaginati sono formattati per essere contenuti in una pagina che può essere stampata o condivisa. I dati sono visualizzati in una tabella, anche se la tabella si estende su più pagine. Usando l'applicazione desktop di Windows gratuita [**Generatore report di Power BI**](https://go.microsoft.com/fwlink/?linkid=2086513), gli utenti creano i report impaginati e li pubblicano nel servizio.

In Power BI Premium i report impaginati sono un carico di lavoro che deve essere abilitato per una capacità usando il portale di amministrazione. Gli amministratori della capacità possono abilitare e quindi specificare la quantità di memoria come percentuale delle risorse di memoria complessive della capacità. A differenza di altri carichi di lavoro, Premium esegue i report impaginati in uno spazio contenuto all'interno della capacità. Viene usata la memoria massima specificata per questo spazio, indipendentemente dal fatto che il carico di lavoro sia attivo o meno. Il valore predefinito è 20%. 

Per altre informazioni, vedere [Report impaginati in Power BI Premium](paginated-reports-report-builder-power-bi.md). Per altre informazioni sull'abilitazione del carico di lavoro dei report impaginati, vedere [Configurare i carichi di lavoro](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Server di report di Power BI
 
Incluso in Power BI Premium, Server di report di Power BI è un server di report *locale* con un portale Web. È possibile creare il proprio ambiente BI locale e distribuire i report dietro il firewall dell'organizzazione. Server di report offre agli utenti l'accesso a report interattivi avanzati e le funzionalità di creazione di report aziendali di SQL Server Reporting Services. Gli utenti possono esplorare visivamente i dati e individuare rapidamente modelli per prendere decisioni migliori e più rapide. Server di report offre una governance personalizzata. Quando opportuno, Server di report di Power BI semplifica la migrazione nel cloud dove l'organizzazione può usare al meglio tutte le funzionalità di Power BI Premium.

Per altre informazioni, vedere [Server di report di Power BI](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Condivisione dei contenuti illimitata

Con Premium, tutti gli utenti, all'interno o all'esterno dell'organizzazione, possono visualizzare i contenuti di Power BI, inclusi report interattivi e impaginati, senza dover acquistare licenze individuali. 

![Condivisione dei contenuti](media/service-premium-what-is/premium-sharing.png)

Premium consente anche una distribuzione generalizzata dei contenuti da parte degli utenti Pro senza richiedere licenze Pro per la visualizzazione del contenuto da parte dei destinatari. Le licenze Pro sono necessarie per gli autori dei contenuti. Gli autori si connettono alle origini dati, modellano i dati e creano report e dashboard che vengono offerti come app di aree di lavoro. 

Per altre informazioni, vedere [Licenze di Power BI](service-admin-licensing-organization.md).

## <a name="tool-connectivity-preview"></a>Connettività degli strumenti (anteprima)

In background, il **motore Vertipaq di Analysis Services** di Microsoft alimenta i set di dati di Power BI. Analysis Services offre programmabilità e supporto delle applicazioni client e degli strumenti tramite librerie client e API che supportano il protocollo XMLA standard aperto. Attualmente i set di dati di Power BI Premium supportano le operazioni di *sola lettura* da applicazioni client e strumenti Microsoft e di terze parti tramite gli **endpoint XMLA**. 

Gli strumenti Microsoft come SQL Server Management Studio e SQL Server Profiler e le app di terze parti come DAX Studio e le applicazioni di visualizzazione dei dati possono connettersi ed eseguire query su set di dati Premium tramite XMLA, DAX, MDX, DMV e TraceEvent. 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

Per altre informazioni, vedere [Connettersi ai set di dati con applicazioni client e strumenti](service-premium-connect-tools.md).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Gestione delle capacità Premium](service-premium-capacity-manage.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

||||||
