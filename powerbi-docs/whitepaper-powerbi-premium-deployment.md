---
title: Distribuire e gestire le capacità di Power BI Premium
description: Comprendere il potenziale di Power BI Premium e imparare a progettare, distribuire, monitorare e risolvere i problemi di soluzioni scalabili.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: fbae2a8b577c52ae597d44bd6ea9913510c4c65c
ms.sourcegitcommit: dc73e932c9982a4aa0b0ec5297fb9f94c6156bc5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2019
ms.locfileid: "66518578"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Distribuire e gestire le capacità di Power BI Premium

**Riepilogo:** Power BI Premium offre prestazioni più coerenti, supporto per volumi di dati di grandi dimensioni e la flessibilità di una piattaforma di Business Intelligence self-service ed enterprise unificata per tutti gli utenti nell'organizzazione. Questo white paper tecnico di livello 300 è stata scritta in modo specifico per gli amministratori di Power BI e gli autori di contenuti e i server di pubblicazione. L'obiettivo per aiutarli a comprendere il potenziale di Power BI Premium e per spiegare come progettare, distribuire, monitorare e risolvere i problemi di soluzioni scalabili.

**Autore:** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (Data Platform MVP ed esperto BI indipendente con soluzioni di OR bit per bit)

**Revisori tecnici:** ADAM Saxton, Akshai Mirchandani, esercente Bhavik, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, Matrat Olivier, Swati Gupta

**Si applica a:** Servizio Power BI, Power BI Premium e le capacità di Power BI Embedded di Azure

> [!NOTE]
> È possibile salvare o stampare questo white paper selezionando **Stampa** dal browser, quindi selezionando **Salva come PDF**.

## <a name="introducing-power-bi"></a>Introduzione a Power BI

Power BI è un servizio di analitica di business progettato per offrire informazioni dettagliate per consentire di prendere decisioni rapide e informate. Rilasciato nel 2015 è rapidamente diventato un servizio popolare usato per offrire soluzioni per il più basso tra le organizzazioni al più grande delle aziende.

Viene reso disponibile in due modi: Soluzione di reporting denominato come un servizio cloud e locale **Server di Report di Power BI**. \[[1](#endnote-01)\]

Power BI come un servizio cloud è Software-as-a-Service (SaaS) \[ [2](#endnote-02)\]. Rappresenta un set di servizi e applicazioni che consentono alle organizzazioni di sviluppare, distribuire, gestire, la condivisione delle soluzioni per il monitoraggio delle loro attività aziendali.

Non è l'intenzione di questo white paper di fornire una descrizione completa del servizio Power BI. In alternativa, è incentrato su argomenti rilevanti per l'oggetto di Power BI Premium. Per informazioni generali su Power BI, vedere il completi [documentazione di Power BI](service-admin-premium-multi-geo.md). Per una spiegazione più dettagliata del servizio Power BI con l'obiettivo di offrire buone prestazioni le distribuzioni aziendali, consultare il completi [pianificazione di una distribuzione di Power BI Enterprise](https://aka.ms/pbienterprisedeploy) white paper.

All'interno del contesto dell'oggetto di questo white paper, in questa sezione presenta e descrive le capacità, Power BI i tipi di contenuto, le modalità di archiviazione del modello e gestione delle licenze. La comprensione di questi argomenti è essenziale per la distribuzione e la gestione di Power BI Premium correttamente.

### <a name="capacities"></a>Capacities

**Le capacità** sono contenuto un concetto di Power BI core che rappresenta un set di risorse (memoria, processore e memoria) usate per ospitare e distribuire Power BI. Le capacità condivisi o dedicate. Oggetto **capacità condivisa** è condiviso con altri clienti Microsoft, mentre un **capacità dedicata di** si impegnerà a un singolo cliente. In cui sono state introdotte le capacità dedicate di [capacità Premium](#premium-capacities) argomento.

In capacità condivisa, i carichi di lavoro eseguiti su risorse di calcolo condivise con altri clienti. La capacità deve condividere risorse, vengono imposte limitazioni per assicurarsi che "fair play", ad esempio le dimensioni massime del modello (1 GB) e massima frequenza di aggiornamento giornaliera (otto volte al giorno).

### <a name="workspaces"></a>Aree di lavoro

Le aree di lavoro di Power BI si trovano all'interno di capacità e che rappresentano i contenitori di protezione, collaborazione e la distribuzione. Ogni utente di Power BI dispone di un'area di lavoro persona detta **area di lavoro personale**. È possibile creare nuove aree di lavoro per abilitare la collaborazione e la distribuzione e si parla **aree di lavoro App**. Per impostazione predefinita, le aree di lavoro - tra cui le aree di lavoro personale, vengono creati nella capacità condivisa.

### <a name="power-bi-content-types"></a>Tipi di contenuto BI Power

Per introdurre gli argomenti di Power BI Premium, è importante iniziare con una discussione approfondita dell'architettura di Power BI inclusi i tipi di contenuto fondamentali.

Tutto il contenuto di Power BI verrà archiviato e gestito all'interno di aree di lavoro che sono contenitori per il contenuto di Power BI. Ogni utente di Power BI ha i propri area di lavoro personale, ma la procedura consigliata generale consiste nel creare le aree di lavoro di app. Le aree di lavoro di App consentono comproprietà di contenuto e la possibilità di collaborare sul contenuto. Offrono anche la possibilità di gestire in modo temporaneo e distribuire contenuti a destinatari wide come le app.

Il seguente contenuto di Power BI verrà archiviato nelle aree di lavoro:

- Dataflows
- Set di dati
- Cartelle di lavoro
- Report
- Dashboard

#### <a name="dataflows"></a>Dataflows

Flussi di dati di Power BI consentono alle organizzazioni per unificare i dati provenienti da origini diverse. Si può essere considerate come dati preparati e gestione temporanea per l'uso nei modelli, ma non può essere usati direttamente come origine per la creazione di report. Le estensioni si avvalgono l'ampia raccolta di connettori di dati di Microsoft, consentendo l'inserimento di dati da origini dati basate su cloud e locali.

Flussi di dati può solo essere creati e gestiti in aree di lavoro di app e vengono archiviati come entità in Common Data modello (CDM) in Azure Data Lake Storage Gen2. In genere, i processi sono pianificati per aggiornare in modo ricorrente per archiviare i dati aggiornati.

Per altre informazioni, vedere la [di preparazione dei dati self-servizi in Power BI (anteprima)](service-dataflows-overview.md) documento.

#### <a name="datasets"></a>Set di dati

I set di dati di Power BI rappresentano un'origine dati pronti per la visualizzazione e creazione di report. Esistono molti tipi di set di dati creato da:

- La connessione a un modello di dati esistente che non è ospitato in una capacità di Power BI
- Caricamento di un file di Power BI Desktop che contiene un modello
- Caricamento di una cartella di lavoro di Excel (contenente una o più tabelle di Excel e/o un modello di dati della cartella di lavoro) o il caricamento di un file CSV (comma Comma-Separated Value)
- Uso del servizio Power BI per creare un push, il flusso o ibrida set di dati di streaming

Ad eccezione di set di dati di streaming \[ [3](#endnote-03)\], il set di dati rappresenta un modello di dati che sfrutta le tecnologie di modellazione avanzata di Analysis Services.

Si noti che nella documentazione, a volte i termini set di dati e i modelli sono intercambiabili. In genere, dal punto di vista del servizio Power BI, viene indicato come un **set di dati** e da un punto di vista dello sviluppo, è indicato come una **modello**. Nel contesto di questo white paper sono molto lo stesso significato.

##### <a name="externally-hosted-models"></a>Modelli ospitato esternamente

La connessione a un modello ospitato esternamente prevede l'installazione di [On-Premises Data Gateway](service-gateway-onprem.md) per connettersi a SQL Server Analysis Services, se si tratta in locale o macchina virtuale ospitata Infrastructure-as-a-Service (IaaS). Azure Analysis Services non richiede un gateway. Questo scenario spesso risulta più utile quando sono presenti gli investimenti esistenti del modello, in genere che fanno parte di Enterprise Data Warehouse (EDW). Consente a Power BI eseguire una **connessione dinamica** (LC) per Analysis Services e rispetta applicando le autorizzazioni di dati usando l'identità dell'utente del report di Power BI. Per SQL Server Analysis Services, sono supportati sia i modelli multidimensionali (cubi) e i modelli tabulari. Come illustrato nell'immagine seguente, un set di dati di connessione dinamica passa le query ai modelli ospitati esternamente.

![Un set di dati di connessione dinamica passa le query ai modelli ospitati esternamente](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>Power BI Desktop-sviluppato modelli

Power BI Desktop - un'applicazione client destinata allo sviluppo di Power BI - utilizzabile per sviluppare un modello che è in realtà un modello tabulare di Analysis Services. I modelli possono essere sviluppati tramite l'importazione di dati da flussi di dati, che può quindi essere integrata con altre origini dati. Sebbene le specifiche su come è possibile ottenere la modellazione è di fuori dell'ambito di questo white paper, è importante capire che esistono tre diversi tipi - o modalità - dei modelli che possono essere sviluppati usando Power BI Desktop. Queste modalità determinano se i dati vengono importati nel modello o se rimane nell'origine dati. Sono tre modalità: Import, DirectQuery e composito. Verrà considerata una descrizione completa di ogni modalità per la [modalità di archiviazione del modello](#model-storage-modes) argomento.

Modelli ma ospitato e i modelli sviluppati in Power BI desktop possono applicare la sicurezza a livello di riga (RLS) per limitare i dati che possono essere recuperati per un determinato utente. Ad esempio, gli utenti assegnati al gruppo di sicurezza personale di vendita possono solo visualizzare i dati del report per le aree di vendita a cui sono assegnate. Ruoli a livello di riga possono essere dinamico o statico. **I ruoli dinamici** Filtra per l'utente del report, mentre **ruoli statici** applicherà gli stessi filtri per tutti gli utenti assegnati al ruolo.

##### <a name="excel-workbook-models"></a>Modelli di cartella di lavoro di Excel

Creazione di set di dati basati su cartelle di lavoro di Excel o CSV file comporterà la creazione automatica di un modello. Verranno importati dati in formato CSV e tabelle di Excel per creare le tabelle del modello, mentre un modello di dati della cartella di lavoro di Excel verrà essere invertito per creare un modello di Power BI. In tutti i casi, i dati dei file viene importati in un modello.

Differenze, quindi, possono essere effettuate sui set di dati di Power BI che rappresentano modelli:

- Essi siano ospitati nel servizio Power BI o esternamente sono ospitati da Analysis Services
- È possibile archiviare i dati importati o pass-through poter emettere richieste di query per origini dati sottostanti o una combinazione di entrambi

Ecco un riepilogo delle informazioni importanti sui set di dati di Power BI che rappresentano modelli:

- Modelli di SQL Server Analysis Services ospitata richiedono un gateway per eseguire query di LC
- Power BI ospitati i modelli di importano dei dati
  - Deve essere completamente caricate nella memoria in modo che è possibile eseguire query
  - Richiedono l'aggiornamento per mantenere i dati correnti e deve coinvolgere i gateway quando i dati di origine non sono accessibili direttamente tramite Internet
- Power BI ospitati i modelli che utilizzano la modalità di archiviazione DirectQuery (DQ) richiedono la connettività ai dati di origine. Quando il modello viene eseguita una query, Power BI esegue query all'origine dati per recuperare i dati correnti. Questa modalità deve coinvolgere i gateway quando i dati di origine non sono accessibili direttamente tramite Internet.
- I modelli possono applicare le regole a livello di riga, l'applicazione di filtri per limitare l'accesso ai dati per determinati utenti

Per distribuire e gestire Power BI Premium, è importante comprendere dove sono ospitati i modelli, la relativa modalità di archiviazione, tutte le dipendenze in un gateway, le dimensioni dei dati importati e tipo e la frequenza di aggiornamento. Questi tutti possono avere un impatto significativo per le risorse di Power BI Premium. Inoltre, la progettazione del modello stesso tra cui la query di preparazione dei dati e calcoli è possibile aggiungere alla combinazione di considerazioni.

È inoltre importante comprendere che ospitate da Power BI Importa i modelli possono aggiornare in base alla pianificazione o essere attivate su richiesta da un utente nel servizio Power BI.

Progettazione di modelli ottimizzati è descritto più avanti in questo documento tecnico nel [ottimizzazione modelli](#optimizing-models) argomento.

#### <a name="workbooks"></a>Cartelle di lavoro

Le cartelle di lavoro di Power BI sono un tipo di contenuto di Power BI \[ [4](#endnote-04)\]. Si tratta di cartelle di lavoro di Excel che sono stati caricati nel servizio Power BI e non vanno confuse con le cartelle di lavoro Excel caricati che creano set di dati (modelli). Il tipo di contenuto della cartella di lavoro rappresenta una connessione a una cartella di lavoro, che è stato possibile caricare sia il servizio Power BI o rimane nell'archiviazione cloud in OneDrive o SharePoint Online.

È importante comprendere che questo tipo di contenuto non è disponibile come origine dati per le visualizzazioni di dati di Power BI. Al contrario, può essere aperto come cartella di lavoro nel servizio Power BI con Excel Online. Lo scopo principale di questo tipo di contenuto consiste nel consentire legacy rapporti di cartella di lavoro di Excel deve essere accessibile da all'interno del servizio Power BI e per consentire le visualizzazioni di dati essere aggiunti ai dashboard di Power BI.

Per altre informazioni, vedere la [ottenere dati dai file di cartella di lavoro di Excel](service-excel-workbook-files.md) documento.

#### <a name="reports"></a>Report

Esistono due tipi di report: Report di Power BI e report impaginati.

**Report di Power BI** offrono un'esperienza che si connette a un singolo set di dati di una visualizzazione dati interattiva. I report sono spesso progettati per incoraggiare la partecipazione degli utenti consentendo loro di interagire con una matrice straordinaria gamma di funzionalità, incluso il filtro, il sezionamento, tra il filtraggio e l'evidenziazione, drill-up, drill-down, drill-through, una naturale domande e risposte messo in dubbio la lingua, messa a fuoco, navigazione tra le pagine, evidenziazione, visualizzazione segnalibri e altro ancora.

Nel contesto di questo white paper, è importante comprendere impatto dell'architettura di Power BI, le interazioni utente e Progettazione report di Power BI possono tutte su delle risorse del servizio Power BI:

- Per caricare e interagire con i report basati sui modelli di importazione, il modello deve essere completamente caricato nella memoria (se ospitati nel servizio Power BI o esternamente)
- Ogni oggetto visivo del report esegue una query per recuperare i dati esaminando il modello
- In genere, le interazioni di filtro e filtro dei dati comportano l'esecuzione di query il modello. Ad esempio, la modifica di una selezione di filtro dei dati - per impostazione predefinita - richiederà il ricaricamento di singoli oggetti visivi nella pagina \[ [5](#endnote-05)\]
- Report di Power BI non garantiscono la visualizzazione dei dati correnti e possono richiedere all'utente di aggiornare il report per ricaricare la pagina del report e i rispettivi oggetti visivi
- Gli utenti possono interagire con domande e risposte lo consente una funzionalità del linguaggio naturale per porre domande, fornire la progettazione di report di Power BI e il set di dati rappresenta un modello di importazione di dati basato su Power BI o un set di dati di LC configurato per l'attivazione di domande e risposte

**Report impaginati** che consente la pubblicazione e il rendering dei report di SQL Server Reporting Services (SSRS) (\*formato con estensione rdl). Come suggerisce il nome, i report impaginati vengono comunemente usati quando i requisiti prevedono una necessità per la stampa su una dimensione di pagina fisse, o quando sono presenti elenchi di variabili di dati che devono essere completamente espanso. Ad esempio, una fattura progettata per il rendering a più pagine (anziché lo scorrimento all'interno di un oggetto visivo) e stampa.

Scelta di fornire i due tipi di report supportate per gli autori di report, consentendo loro di selezionare il tipo in base ai requisiti e uso previsto. In generale, report di Power BI sono ideali per esperienze interattive, consentendo all'utente di esplorare e individuare informazioni dettagliate dai dati, mentre i report impaginati sono più adatti ai layout di pagina basata sul parametro.

Indipendentemente dal tipo di report, ottenere gli aggiornamenti di carico e i dati di report reattivi (quando vengono modificati i filtri o parametri) è fondamentale per garantire un'esperienza utente affidabili e con ottime prestazioni.

#### <a name="dashboards"></a>Dashboard

Dashboard di Power BI consentono di offrire esperienze di monitoraggio e sono concettualmente molto diversi dai report di Power BI. I dashboard sono progettati per la visualizzazione in un'unica console per esprimere i valori e visualizzazioni di dati nei riquadri. In generale, i dashboard offrono esperienze interazione un numero minore rispetto ai report di Power BI, con alcune progettazioni di dashboard è previsto alcuna interazione. Ad esempio, un dashboard automatico presentato in una schermata non a sfioramento in una stanza del server. Un'altra differenza significativa è che i dashboard possono essere presenti i riquadri che possono essere basati solo su un singolo set di dati del report origini dati provenienti da più set di dati, mentre un Power BI.

È importante comprendere che un dashboard è progettato per caricare rapidamente e per esprimere i dati più recenti (noti nel servizio Power BI) in qualsiasi momento. A tale scopo, la memorizzazione nella cache i risultati della query di riquadro e esegue questa operazione per ogni dashboard. In effetti, è necessario eseguire questa operazione per ogni utente che ha accesso a un dashboard basato su modelli che impongono dinamica a livello di riga.

Il servizio Power BI Aggiorna automaticamente le cache di query dashboard immediatamente dopo l'aggiornamento di modelli basati su Power BI Importa. Nel caso di modelli di LC e DQ, il proprietario del set di dati ha un livello di controllo sulla frequenza nel servizio Power BI Aggiorna la cache, che può essere configurata come spesso come ogni 15 minuti o di frequenza minima di una volta alla settimana. Si noti che gli aggiornamenti della cache di query di LC eseguirà innanzitutto una query per determinare se un aggiornamento dei modelli è stata eseguita dopo l'ultimo aggiornamento della cache e non procederà per aggiornare la cache quando un aggiornamento non si è verificato poiché i metadati del modello. Questo controllo non è possibile che i modelli DQ e pertanto gli aggiornamenti della cache verranno eseguito se i dati di origine sono stata modificata o non.

Cache delle query dashboard Aggiorna DQ base e i modelli di LC possono influire significativamente sulle risorse del servizio Power BI sia le origini dati esterne. Prendere in considerazione un dashboard con 20 riquadri, tutti basati su un modello di Azure Analysis Services che consente di applicare a livello di riga dinamica che vengono aggiornati ogni ora e che è stato condiviso questo dashboard di 100 utenti. Se il set di dati è configurato per l'aggiornamento ogni ora, ciò comporterebbe almeno 2000 (20 x 100) query LC. Questo potrebbe imporre un carico elevato nel servizio Power BI e origini dati esterne e inoltre può superare i limiti imposti per le risorse disponibili. Limiti e alle risorse di capacità sono descritti nel [i nodi della capacità](#capacity-nodes) argomento.

Gli utenti possono interagire con un dashboard in vari modi, che richiedono le risorse del servizio Power BI. In particolare, gli utenti possono:

- Attivare un aggiornamento dei riquadri dei dashboard, che può comportare un aggiornamento su richiesta di tutti i dati basato su Power BI Importa modelli correlati
- Interagire con le domande e risposte una funzionalità del linguaggio naturale per porre domande (purché lo consente la progettazione dei dashboard e i set di dati è un modello di importazione di dati basato su Power BI o un set di dati di LC configurato per l'attivazione di domande e risposte)
- Usare la funzionalità informazioni rapide di Power BI individuare informazioni approfondite da un set di dati sottostante e rispondere con oggetti visivi che visualizzano e descriverli (purché che il riquadro si basa su un set di dati è il modello di importazione dati basato su Power BI)
- Configurare gli avvisi sui riquadri del dashboard, che richiede il servizio Power BI per confrontare le soglie per affiancare i valori - possibilmente con una frequenza oraria - e per notificare agli utenti quando vengono superate le soglie (specificando che il riquadro Visualizza un singolo valore numerico e si basa su un set di dati che è il modello di importazione dati basato su Power BI)

### <a name="model-storage-modes"></a>Modalità di archiviazione del modello

È importante ricordare che Power BI Desktop consente di sviluppare un modello in una delle tre modalità. È importante comprendere i motivi per ogni modalità di archiviazione del modello di dati e i possibili impatti sulle risorse del servizio Power BI. Questa sezione vengono presentate tutte le tre modalità. Verranno discusse in modo dettagliato più avanti in questo white paper nell'argomento ottimizzare i modelli.

#### <a name="import-mode"></a>Modalità di importazione

Modalità di importazione è la modalità più comune usata per sviluppare i modelli a causa di prestazioni molto elevate associata con l'esecuzione di query, la flessibilità di progettazione disponibile per i creatori di modelli, in memoria e il supporto per specifiche funzionalità del servizio Power BI (domande e risposte, Quick Insights e così via.). È la modalità predefinita quando si crea una nuova soluzione di Power BI Desktop.

È importante comprendere che i dati importati viene sempre archiviati per disco e devono essere completamente caricate nella memoria per eseguire una query o aggiornamento. Una volta in memoria, importazione modelli ottenere i risultati della query estremamente veloce. È inoltre importante comprendere che non vi sia alcun concetto di un modello di importazione parzialmente caricato in memoria.

All'aggiornamento, i dati vengono compressi e ottimizzati e quindi archiviati su disco dal motore di archiviazione VertiPaq. Quando viene caricato dal disco in memoria, è possibile vedere una compressione 10x, e quindi, è ragionevole aspettarsi che è possibile comprimere 10 GB di dati di origine a circa 1 GB di dimensioni. Dimensioni di archiviazione su disco è possono ottenere una riduzione di 20% in primo piano questo. \[[6](#endnote-06)\]

Flessibilità di progettazione può essere ottenuta in tre modi. I creatori di modelli di dati è possibile:

- Integrare i dati per la memorizzazione nella cache i dati da più origini dati, indipendentemente dal tipo di origine dati e del formato
- Sfruttare l'intero set di funzioni di Power Query Formula Language (in modo informale M) durante la creazione di query di preparazione dei dati
- Sfruttare l'intero set di funzioni di Data Analysis Expressions (DAX), migliorare il modello con la logica di business, ottenuta con tabelle calcolate, misure e colonne calcolate

Come illustrato nell'immagine seguente, un modello di importazione possa integrare dati da un numero qualsiasi di tipi di origini dati supportate.

![Un modello di importazione è possibile integrare i dati da un numero qualsiasi di tipi di origini dati supportate](media/whitepaper-premium-deployment/import-model.png)

Tuttavia, anche se esistono vantaggi sostanziali associati ai modelli di importazione, esistono gli svantaggi troppo:

- L'intero modello deve essere caricato in memoria prima di eseguire una query al modello, che è possibile inserire un utilizzo elevato per le risorse disponibili man mano che aumentano il numero e dimensioni dei modelli di Power BI
- I dati del modello sono solo a quelle dell'aggiornamento più recente e pertanto devono essere aggiornati, preferibilmente in base a una pianificazione importazione modelli
- Un aggiornamento completo verrà rimossi tutti i dati da tutte le tabelle e ricaricarlo dall'origine dati. Ciò può risultare dispendioso in termini di tempo e risorse per il servizio Power BI e le origini dati. Power BI hanno il supporto per l'aggiornamento incrementale che è possibile evitare di troncamento e il ricaricamento di intere tabelle, e questo aspetto è illustrato nel [Optimizing Power BI-Hosted modelli](#optimizing-power-bi-hosted-models) argomento.

Da una prospettiva della risorsa del servizio Power BI, i modelli di importazione richiedono:

- Quantità di memoria sufficiente per caricare il modello quando viene eseguita una query o aggiornamento
- Risorse di elaborazione e risorse di memoria aggiuntiva per aggiornare i dati

#### <a name="directquery-mode"></a>Modalità DirectQuery

Modelli sviluppati in modalità DirectQuery (DQ) non importano i dati. In alternativa, è costituito solo da metadati che, se sottoposti a query le query native di problemi all'origine dati sottostante.

![Un modello DirectQuery esegue query nativa dell'origine dati sottostante](media/whitepaper-premium-deployment/direct-query-model.png)

Esistono due motivi principali per prendere in considerazione lo sviluppo di un modello DQ. Il primo motivo è quando i volumi di dati sono troppo grandi - anche quando vengono applicati i metodi di riduzione dei dati - caricare in un modello o aggiornare in pratica. Il secondo motivo è quando necessario "quasi in tempo reale" dati, oltre a quelle ottenute entro i limiti di aggiornamento pianificato (48 volte al giorno per una capacità dedicata) di recapitare report e dashboard.

Esistono diversi vantaggi associati ai modelli DQ:

- Non si applicano i limiti di dimensioni di importazione modello
- I modelli non richiedono l'aggiornamento
- Gli utenti del report verranno visualizzati i dati più recenti quando si interagisce con i filtri dei report e i filtri dei dati e può aggiornarne l'intero report per recuperare i dati correnti
- I riquadri del dashboard, quando basate su modelli DQ, è possono aggiornare automaticamente la stessa frequenza ogni 15 minuti

Esistono tuttavia numerosi svantaggi e le limitazioni associate ai modelli DQ:

- Il modello deve essere basato su un'origine dati supportata singolo e pertanto è necessario già realizzato qualsiasi integrazione dei dati nell'origine dati. Origini dati supportate sono i sistemi relazionali e di analisi, con supporto per molti archivi dati diffusi \[ [7](#endnote-07)\].
- Le prestazioni possono risultare lenta, non hanno conseguenze potenzialmente negative sul servizio Power BI (query può essere elevato della CPU) e sull'origine dati (che potrebbe non essere ottimizzata per le query analitiche)
- Le query di Power Query non possono essere eccessivamente complesse e sono limitate a funzioni che possono essere invertite per le query native riconosciute dall'origine dati e le espressioni M
- Le funzioni DAX sono limitate a quelle che possono essere invertiti per le query native riconosciute dall'origine dati e non è supportata per le tabelle calcolate o funzionalità di Intelligence ora incorporate
- Per impostazione predefinita, le query del modello che richiedono il recupero di più di un milione di righe avrà esito negativo
- Dashboard con più oggetti visivi e report può visualizzare i risultati non coerenti, soprattutto quando l'origine dati è volatile
- Domande e risposte e informazioni rapide non sono supportate

Da una prospettiva della risorsa del servizio Power BI, i modelli DQ richiedono:

- Memoria minima per caricare il modello (solo metadati) quando vengono eseguite query
- Risorse del processore talvolta significativa per generare ed elaborare le query inviate all'origine dati

Per altre informazioni, vedere la [uso di DirectQuery in Power BI Desktop](desktop-use-directquery.md) documento.

#### <a name="composite-mode"></a>Modalità composita

Modelli sviluppati in modalità Composite consentono di configurare la modalità di archiviazione per le tabelle del modello singoli. Di conseguenza supporta una combinazione di importazione e tabelle DQ. Supporta anche le tabelle calcolate (definite con DAX) e più origini dati DQ.

Modalità di archiviazione di tabella può essere configurata come Import, DirectQuery o Dual. Una tabella configurata come modalità di archiviazione doppia è Import e DirectQuery e consente al servizio Power BI determinare la modalità più efficiente da usare in base a una query dalla query.

![Un modello composito è una combinazione di modalità di archiviazione di importazione e DQ, configurata a livello di tabella](media/whitepaper-premium-deployment/composite-model.png)

Modelli compositi impegnano a offrire il meglio delle modalità di importazione e DirectQuery. Quando è configurato in modo appropriato è possibile combinare le prestazioni delle query elevate dei modelli in memoria con la possibilità di recuperare quasi in tempo reale dei dati da origini dati.

I creatori di modelli di dati che sviluppano modelli compositi è probabile che configurare le tabelle dimensione-tipo di importazione o doppia modalità e tipo di fact tabelle di archiviazione in modalità DirectQuery. Si consideri ad esempio un modello con una tabella di tipo di dimensione Product in modalità doppia e una tabella di tipo di fact Sales nella modalità DirectQuery. La tabella Product è stato possibile eseguire query in modo rapido e in modo efficiente dalla memoria per il rendering di un filtro dei dati di report. Nella tabella Sales potrebbe quindi possibile eseguire query in modalità DirectQuery, unita alla tabella di prodotti correlata. La query di quest'ultima è stato possibile abilitare la generazione di una singola query nativa efficace per unire tabelle Product e vendite e il filtro per i valori di filtro dei dati.

In generale, i vantaggi e svantaggi, associati alla modalità in ogni modello possono essere considerati da applicare alla modalità di archiviazione di tabella nei modelli compositi.

Per altre informazioni, vedere la [usare i modelli compositi in Power BI Desktop](desktop-composite-models.md) documento.

### <a name="licensing"></a>Gestione delle licenze

Power BI dispone di tre licenze:

- Power BI gratuito
- Power BI Pro
- Power BI Premium

Il **Power BI gratuito** licenza consente a un utente di accedere al servizio Power BI e di lavoro all'interno di propria area di lavoro mediante la pubblicazione di report e modelli. È importante comprendere che non è possibile condividere il contenuto di Power BI con questa licenza. Questa licenza, come suggerisce il nome, è gratuita.

Il **Power BI Pro** licenza consentono di creare e collaborare all'interno di aree di lavoro di app e condividere e distribuire Power BI una persona del contenuto. Possono anche configurare l'aggiornamento per i set di dati mantenere automaticamente i dati correnti, e da origini dati locali. Inoltre, possono controllare e regolare la modalità di accesso e uso dei dati. Questa licenza è necessaria per ricevere il contenuto condiviso dagli altri, a meno che l'utente è associato a una capacità dedicata di Power BI Premium.

Il **Power BI Premium** licenza è una licenza a livello di tenant e è descritti nella [Introduzione a Power BI Premium](#introducing-power-bi-premium) sezione.

Per ulteriori informazioni sulle licenze di Power BI, vedere la [prezzi di Power BI](https://powerbi.microsoft.com/pricing/) pagina.

## <a name="introducing-power-bi-premium"></a>Introduzione a Power BI Premium

Power BI Premium offre una piattaforma unificata per BI self-service ed enterprise con costi prevedibili, scalabilità e prestazioni affidabili. Principalmente raggiunge questo fornendo risorse dedicate per eseguire il servizio Power BI per l'organizzazione.

Power BI Premium offre anche molte funzionalità aziendali:

- Distribuzione di contenuti economica, consentendo la condivisione del contenuto di Power BI agli utenti di Power BI gratuito illimitati, tra cui gli utenti esterni
- Supporto per set di dati di dimensioni maggiori \[ [8](#endnote-08)\]
- Maggiori frequenze di aggiornamento di flussi di dati e set di dati (fino a 48 volte al giorno)
- Aggiornamento incrementale di flussi di dati e set di dati
- Le entità del flusso di dati collegato e l'esecuzione parallela delle trasformazioni
- Report impaginati
- Server Report di Power BI, per reporting on-premise
- Possibilità di incorporare il contenuto nelle App per conto di utenti dell'app (PaaS)

Molte di queste funzionalità possono essere sfruttate per offrire soluzioni aziendali efficienti e scalabili e vengono analizzate le [ottimizzazione della capacità Premium](#optimizing-premium-capacities) sezione.

### <a name="subscriptions-and-licensing"></a>Sottoscrizioni e licenze

Power BI Premium è disponibile in due famiglie di SKU (SKU Unit) un abbonamento a Office 365 a livello di tenant:

- **EM** SKU (EM1-EM3) per l'incorporamento, che richiedono un impegno annuo, con fatturazione mensile
- **P** SKU (P1-P3) per le funzionalità di incorporamento ed enterprise, che richiedono un impegno mensile o annuo, con fatturazione mensile e include una licenza per installare il Server di Report di Power BI in locale

Un approccio alternativo consiste nell'acquistare una sottoscrizione di Azure Power BI Embedded con una singola famiglia di SKU: **Oggetto** SKU (A1-A6) per l'incorporamento e la capacità solo a scopo di test.

Tutti gli SKU di memorie centrali virtuali per creare le capacità di offrire \[ [9](#endnote-09)\], ma gli SKU EM sono limitati per l'incorporamento di scalabilità più piccoli. Anche se l'obiettivo di questo white paper è sugli SKU P, gran parte degli argomenti illustrati è importante anche gli SKU.

A differenza di sottoscrizione Premium SKU, SKU di Azure non richiedono alcun impegno temporale e vengono fatturati su base oraria. Sono offrire elasticità completa l'abilitazione di scalabilità di, ridurre, sospendere, riprendere e delete.

Azure Power BI Embedded è in gran parte esulano dall'ambito di questo white paper, ma si è descritto nell'argomento test approcci come un'opzione economica e pratica per testare e valutare i carichi di lavoro.

Per altre informazioni sugli SKU di Azure, vedere la [documentazione di Azure Power BI Embedded](/azure/power-bi-embedded/).

Le sottoscrizioni di Power BI Premium vengono acquistate dagli amministratori nel centro di amministrazione di Microsoft 365. In particolare, solo gli amministratori globali di Office 365 o gli amministratori fatturazione possono acquistare SKU.

Dopo aver acquistato, il tenant riceve un numero corrispondente di memorie centrali virtuali da assegnare alla capacità - questo è noto come **limitazione delle richieste di v-core**. Ad esempio, l'acquisto di uno SKU P3 fornisce al tenant 32 memorie centrali.

Per altre informazioni, vedere la [come acquistare Power BI Premium](service-admin-premium-purchase.md) documento.

### <a name="premium-capacities"></a>Capacità Premium

A differenza di una capacità condivisa in cui i carichi di lavoro eseguiti nelle risorse di calcolo condivise con altri clienti, una **capacità dedicata** sia per l'utilizzo esclusivo da un'organizzazione. È isolata con risorse di calcolo dedicate che offrono prestazioni coerenti e affidabili per il contenuto ospitato.

È l'obiettivo di questo white paper **capacità Premium** , vale a dire è associato a una delle SKU P o EM.

#### <a name="capacity-nodes"></a>Nodi della capacità

Come descritto in sottoscrizioni e licenze argomento, sono disponibili due famiglie di SKU di Power BI Premium: EM e P. Tutti gli SKU Premium di Power BI sono disponibili come capacità nodi, ognuno dei quali rappresenta una quantità di set di risorse costituito da processore, memoria e archiviazione. Oltre alle risorse, ogni SKU ha i limiti operativi per il numero di connessioni DirectQuery DQ () e connessione in tempo reale (LC) al secondo e il numero di modello parallelo viene aggiornato.

L'elaborazione avviene tramite un determinato numero di memorie centrali, suddiviso equamente tra back-end e front-end.

**V-core di back-end** sono responsabili della funzionalità di Power BI core, inclusa elaborazione di query, gestione della cache, che esegue R services, aggiornamento dei modelli, elaborazione in linguaggio naturale (domande e risposte) e il rendering lato server di report e immagini. V-core di back-end vengono assegnate una quantità fissa di memoria che è usato per modelli di host che sono anche denominati per i set di dati attivo primaria.

**V-core di front-end** sono responsabili per il web service, dashboard e report gestione dei documenti, gestione dei diritti di accesso, pianificazione, API, carica e scarica e a livello generale per tutti gli elementi relativi all'utente esperienze.

Archiviazione è impostata su 100 TB per ogni nodo di capacità.

Le risorse e i limiti di ogni SKU Premium (e allo stesso modo dimensioni SKU A) sono descritte nella tabella seguente.

| Nodi della capacità | Totale vCore | vCore back-end | RAM (GB) | vCore front-end | DQ/LC (/ sec) | Parallelismo di aggiornamento del modello |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>Capacità dei carichi di lavoro

Capacità dei carichi di lavoro sono servizi resi disponibili agli utenti. Per impostazione predefinita, le capacità Premium e Azure supportano solo un set di dati del carico di lavoro associato all'esecuzione di query di Power BI che non può essere disabilitata.

Altri carichi di lavoro può essere abilitate per i report impaginati, flussi di dati e intelligenza artificiale. Ogni carico di lavoro aggiuntivo richiede la configurazione della memoria massima (come percentuale del totale di memoria disponibile) che può essere utilizzata dal carico di lavoro.

#### <a name="how-capacities-function"></a>Funzionamento di capacità

In qualsiasi momento, il servizio Power BI mira a ottimizzare l'uso delle risorse di capacità, mentre non superamento dei limiti imposti per la capacità.

Operazioni di capacità sono classificate come interattivo o in background. Le operazioni interattive includono il rendering delle richieste e risposta alle interazioni dell'utente (applicazione di filtri, domande e risposte per query e così via). In generale, l'esecuzione di query di importazione modello la memoria è a elevato utilizzo di risorse, mentre eseguire query sui modelli di LC/DQ è a elevato utilizzo di CPU. Operazioni in background includono flussi di dati e importano gli aggiornamenti del modello e la memorizzazione nella cache di query dashboard.

È importante comprendere che le operazioni interattive abbiano sempre la priorità su operazioni in background per garantire un'esperienza utente ottimizzata. Se sono presenti risorse insufficienti, operazioni in background vengono aggiunti a una coda per l'elaborazione quando libero risorse. Operazioni in background, come gli aggiornamenti di set di dati e le funzioni di intelligenza artificiale, possono essere arrestato durante l'elaborazione dal servizio Power BI e aggiunto a una coda.

I modelli di importazione devono essere completamente caricati nella memoria in modo che possano essere sottoposti a query o aggiornamento. Il servizio Power BI gestisce la memoria utilizzo usando sofisticati algoritmi per garantire il massimo utilizzo di memoria disponibile e può raggiungere l'overcommit della capacità: Sebbene sia possibile per una capacità di archiviare importazione molti dei modelli (fino a 100 TB per ogni capacità Premium), quando relativo spazio di archiviazione combinato disco supera la memoria supportata (e memoria aggiuntiva è necessaria per l'esecuzione di query e aggiornamento), quindi non possono tutti essere caricati in memoria in corrispondenza di contemporaneamente.

I modelli di importazione vengono quindi caricati - e rimossi dal - memoria in base all'utilizzo. Importa un modello viene caricato quando è sottoposto a query (operazione interattiva) e non è ancora in memoria o quando è necessario aggiornare (operazione in background).

La rimozione di un modello dalla memoria è detta **rimozione** , ed è un'operazione che Power BI è possibile eseguire rapidamente a seconda delle dimensioni dei modelli. Se la capacità non riscontra qualsiasi utilizzo della memoria, i modelli vengono semplicemente caricati in memoria e rimangono nella coda. \[[10](#endnote-10) \] , tuttavia, quando memoria disponibile è insufficiente per caricare un modello, il servizio Power BI prima di tutto necessario liberare memoria. Consente di liberare memoria grazie al rilevamento di modelli che sono diventate inattivi effettuando la ricerca di modelli che non sono stati utilizzati negli ultimi tre minuti \[ [11](#endnote-11)\]e quindi nella neutralizzazione di essi. Se non sono presenti modelli inattivi per la rimozione, il servizio Power BI si cerca di rimozione dei modelli caricati per operazioni in background. Ad esempio la rimozione dei carichi di lavoro in background, ad esempio il carico di lavoro di intelligenza artificiale. Ultima risorsa, dopo 30 secondi di tentativi non riusciti \[ [11](#endnote-11)\], consiste nell'eseguire l'operazione interattiva. In questo caso, l'utente del report è normalmente una notifica di errore con un suggerimento per riprovare più tardi.

È importante sottolineare che l'eliminazione di set di dati è un comportamento normale e previsto. E mira a ottimizzare l'utilizzo di memoria per il caricamento e scaricamento di modelli cui dimensioni combinate possono superare la memoria disponibile. Si tratta da progettazione e completamente trasparente agli utenti dei report. Percentuali di rimozione elevata non indicano necessariamente che la capacità è rilevavano risorse assegnata. Un problema, tuttavia, diventano possibile, se la velocità di risposta query o aggiornamento carente a causa di percentuali di rimozione elevata.

Gli aggiornamenti dei modelli di importazione sono sempre a uso intensivo della memoria come modelli devono essere caricati in memoria e memoria aggiuntiva è necessaria per l'elaborazione. Un aggiornamento completo può usare circa il doppio della quantità di memoria necessaria per il modello. In questo modo si garantisce che il modello può essere sottoposto a anche quando in fase di elaborazione (le query vengono inviate al modello esistente, fino a quando non ha completato l'aggiornamento e i nuovi dati del modello sono disponibili). Si noti che l'aggiornamento incrementale richiederà meno memoria è stato possibile completare più rapidamente e pertanto consente di ridurre sostanzialmente un utilizzo elevato delle risorse di capacità. Gli aggiornamenti possono anche essere intensivo della CPU per i modelli, specialmente quelli con trasformazioni complesse di Power Query o tabelle/colonne calcolate che sono complesse o sono basati su tabelle di grandi dimensioni.

Aggiornamenti - come tutte le query, è necessario che il modello di essere caricate in memoria. Se la memoria è insufficiente, nel servizio Power BI proverà a rimuovere modelli inattivi, e se questo non è possibile (per tutti i modelli sono attivi), il processo di aggiornamento è in coda. Gli aggiornamenti vengono in genere elevato della CPU, non più importanti rispetto alle query. Per questo motivo, sono previsti limiti di capacità sul numero di aggiornamenti simultanei, impostata su 1,5 volte il numero di v-core di back-end, arrotondato per eccesso. Se sono presenti troppi gli aggiornamenti simultanei, un aggiornamento pianificato verrà accodato. Quando si verificano queste situazioni, richiede più tempo per il completamento dell'aggiornamento. Si noti che gli aggiornamenti su richiesta (attivati da una richiesta dell'utente o una chiamata API) riproverà a tre volte \[ [11](#endnote-11)\]e quindi esito negativo se non sono ancora sufficienti risorse.

## <a name="managing-power-bi-premium"></a>La gestione di Power BI Premium

La gestione di Power BI Premium comporta l'acquisto di sottoscrizioni e creare, gestire e monitorare le capacità Premium.

### <a name="creating-and-managing-capacities"></a>Creazione e la gestione delle capacità

Il **le impostazioni di capacità** pagina della **amministratore di Power BI** portale Visualizza il numero di memorie centrali virtuali acquistate e disponibili (ad esempio ancora deve essere assegnato a una capacità) ed elenca le capacità Premium. La pagina consente agli amministratori globali di Office 365 o Power BI gli amministratori del servizio per creare le capacità Premium da v-core disponibili o per modificare le capacità Premium esistente.

Quando si crea una capacità Premium, l'amministratore deve definire:

- Nome della capacità (univoco all'interno del tenant)
- Amministratori della capacità
- Dimensioni della capacità
- Area per la residenza dei dati \[ [12](#endnote-12)\]

Deve essere assegnato almeno un amministratore della capacità. Gli utenti assegnati come amministratori della capacità possono:

- Assegnare le aree di lavoro alla capacità
- Gestire le autorizzazioni utente, per aggiungere altri amministratori della capacità o gli utenti con autorizzazioni di assegnazione (per consentire loro di assegnare le aree di lavoro alla capacità)
- Gestire i carichi di lavoro, per configurare l'utilizzo di memoria massima per i report impaginati e i carichi di lavoro di flussi di dati
- Riavviare la capacità, per reimpostare tutte le operazioni in caso di sovraccarico del sistema \[ [13](#endnote-13)\]

Gli amministratori della capacità non possono accedere il contenuto dell'area di lavoro (a meno che non assegnato in modo esplicito le autorizzazioni dell'area di lavoro) e non hanno accesso a tutte le aree di amministrazione di Power BI (a meno che non assegnato in modo esplicito), ad esempio le metriche di utilizzo, i log di controllo o le impostazioni del tenant. Inoltre, gli amministratori della capacità autorizzazioni insufficienti per creare nuove capacità o aumentare le capacità esistenti. Inoltre, vengono assegnati in una base capacità-, garantendo che possano solo visualizzare e gestire le capacità a cui sono assegnate.

Dimensioni della capacità è necessario selezionare da un elenco di opzioni di SKU disponibili che è vincolato dal numero di v-core disponibili nel pool. È possibile creare più le capacità del pool di cui è stato originato da uno o più acquistati SKU. Ad esempio, uno SKU P3 (32 memorie centrali) può essere utilizzati per creare tre capacità: uno P2 (16 v-core) e P1 due (2 x 8 v-core). Miglioramento delle prestazioni e scalabilità può essere ottenuti mediante la creazione di dimensioni minori dimensioni capacità, e in questo argomento viene discusso nel [ottimizzazione della capacità Premium](#optimizing-premium-capacities) sezione. L'immagine seguente mostra un'impostazione di esempio per l'organizzazione Contoso costituito da cinque le capacità Premium (3x P1 e 2 x P3) con ogni lavoro per le app che lo contiene e varie aree di lavoro nella capacità condivisa.

![Un'impostazione di esempio per l'organizzazione Contoso](media/whitepaper-premium-deployment/contoso-organization-example.png)

Una capacità Premium può essere assegnata a una regione diversa da quella iniziale del tenant di Power BI, che fornisce controllo amministrativo su quale Data Center (all'interno di determinate aree geografiche) si trova il contenuto di Power BI. \[[12](#endnote-12)\]

Gli amministratori del servizio Power BI e gli amministratori globali di Office 365 possono modificare le capacità Premium. In particolare, gli utenti possono:

- Modificare le dimensioni della capacità per aumentare o ridurre le risorse. Non è tuttavia possibile effettuare il downgrade di uno SKU P per uno SKU EM, o eseguire l'aggiornamento e viceversa.
- Aggiungere o rimuovere gli amministratori della capacità
- Aggiungere o rimuovere utenti che dispongono delle autorizzazioni di assegnazione
- Aggiungere o rimuovere altri carichi di lavoro
- Modificare le aree geografiche

Sono necessarie autorizzazioni di assegnazione per assegnare un'area di lavoro a una specifica capacità Premium. Le autorizzazioni possono essere concesse per l'intera organizzazione, utenti o gruppi specifici.

Per impostazione predefinita, le capacità Premium supportano i carichi di lavoro associati all'esecuzione di query di Power BI. Supporta inoltre tre altri carichi di lavoro: **Report impaginati**, **Dataflows**, e **intelligenza artificiale**. Ogni carico di lavoro richiede la configurazione della memoria massima (come percentuale del totale di memoria disponibile) che può essere utilizzata dal carico di lavoro. È importante comprendere che un aumento delle allocazioni di memoria massima può influire sul numero di modelli attivi che può essere ospitato e la velocità effettiva degli aggiornamenti.

La memoria viene allocata in modo dinamico ai flussi di dati e in modo statico ai report impaginati. Il motivo per l'allocazione in modo statico la memoria massima è che i report impaginati eseguiti all'interno di uno spazio protetto indipendente della capacità. Dovrebbe prestare attenzione durante l'impostazione impaginazione report memoria in quanto riduce la memoria disponibile per il caricamento dei modelli.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Report impaginati | N/D | 20% predefinita; 10% minima | 20% predefinita; 5% minima | 20% predefinita; 2,5% minima |
| Flussi di dati | 20% predefinita; 8% minima  | 20% predefinita; 4% minima  | 20% predefinita; 2% minima | 20% predefinita; 1% minima  |
| AI | N/D | impostazione predefinita il 20%. 20% minimo  | 20% predefinita; 10% minima | 20% predefinita; 5% minima  |
| | | | | |

L'eliminazione di una capacità Premium, è possibile e non comporterà l'eliminazione delle relative aree di lavoro e il contenuto. Al contrario, si passerà le aree di lavoro assegnati alla capacità condivisa. Quando la capacità Premium è stata creata in un'area diversa, verrà spostato l'area di lavoro alla capacità condivisa dell'area home.

### <a name="assigning-workspaces-to-capacities"></a>Assegnazione di aree di lavoro alla capacità

Le aree di lavoro può essere assegnati a una capacità Premium nel **amministratore di Power BI** **portale** o - per un'area di lavoro - in di **area di lavoro** riquadro.

Gli amministratori della capacità, così come gli amministratori globali di Office 365 o amministratori del servizio Power BI, possono blocco assegnare aree di lavoro di **amministratore di Power BI** **portale**. BULK assegnato è possibile applicare a:

- **Le aree di lavoro da parte degli utenti** : Tutte le aree di lavoro appartenenti a tali utenti, inclusi le aree di lavoro personale, vengono assegnate alla capacità Premium. Ciò include la riassegnazione delle aree di lavoro quando sono già assegnati a una capacità Premium diversa. Inoltre, gli utenti sono assegnati anche le autorizzazioni di assegnazione dell'area di lavoro.

- **Aree di lavoro specifiche**
- **Le aree di lavoro dell'intera organizzazione** : Tutte le aree di lavoro, incluse le aree di lavoro personale, vengono assegnate alla capacità Premium. Inoltre, tutti gli utenti attuali e futuri vengono assegnati le autorizzazioni di assegnazione dell'area di lavoro. \[[14](#endnote-14)\]

Un'area di lavoro può essere aggiunti a una capacità Premium tramite il **dell'area di lavoro** riquadro fornendo all'utente sia un amministratore dell'area di lavoro e disponga delle autorizzazioni di assegnazione.

![Utilizzo del riquadro area di lavoro per assegnare un'area di lavoro a una capacità Premium](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Gli amministratori dell'area di lavoro possono rimuovere un'area di lavoro da una capacità (per la capacità condivisa) senza richiedere l'autorizzazione di assegnazione. Rimozione di aree di lavoro dalla capacità dedicata in modo efficace consente di spostare l'area di lavoro alla capacità condivisa. Si noti che la rimozione di un'area di lavoro da una capacità Premium possono avere conseguenze negative causando, ad esempio, il contenuto condiviso diventi non disponibile per Power BI gratuito concesso in licenza agli utenti o la sospensione dell'aggiornamento pianificato quando superano i limiti supportati da capacità condivisa.

Nel servizio Power BI, un'area di lavoro assegnato a una capacità Premium più facilmente identificabile dall'icona a forma di rombo che decora il nome dell'area di lavoro.

![Che identifica un'area di lavoro assegnato a una capacità Premium](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Le capacità di monitoraggio

Monitoraggio le capacità Premium offre agli amministratori una conoscenza del modo in cui eseguono le capacità. Le capacità possono essere monitorate tramite il [app le metriche della capacità di Power BI Premium](service-admin-premium-monitor-capacity.md) o il [portale di amministrazione di Power BI](service-admin-premium-monitor-portal.md).

#### <a name="interpreting-metrics"></a>L'interpretazione delle metriche

Le metriche devono essere monitorate per stabilire una conoscenza di base delle attività della risorsa di informazioni sull'utilizzo e carico di lavoro. Se la capacità non è più lenta, è importante comprendere le metriche da monitorare e le conclusioni è possibile apportare.

In teoria, le query deve essere completata entro un secondo per offrire esperienze a risposta agli utenti dei report e consentono una velocità effettiva di query. È in genere di preoccupazione minore quando i processi in background - tra cui aggiornamenti - richiedono tempi più lunghi per il completamento.

In generale, report lenta può essere un'indicazione di una capacità in eccesso di riscaldamento. Quando i report non riesce a caricare, questa è un'indicazione di una capacità eccessiva riscaldata. In entrambi i casi, la causa radice potrebbe essere imputabile a numerosi fattori, tra cui:

- **Query non riuscite** certamente indicano un utilizzo elevato della memoria e un modello potrebbe non essere caricati in memoria. Il servizio Power BI verrà effettuato un tentativo di caricare un modello per 30 secondi prima che si verifichi.

- **Tempi di attesa eccessivi query** può essere dovuto a diversi motivi:
  - La necessità per il servizio Power BI prima di tutto rimuovere dei modelli e quindi caricare il modello con query (tenere presente che superiore percentuali di rimozione set di dati da solo non sono un'indicazione di stress di capacità, a meno che non accompagnato da query tempi di attesa lunghi che indicano thrashing di memoria)
  - Caricamento del modello orari (in particolare l'attesa per caricare un modello di grandi dimensioni in memoria)
  - Query con esecuzione prolungata
  - Numero eccessivo di connessioni LC\DQ (superamento dei limiti di capacità)
  - Saturazione della CPU
  - Strutture di report complessi con un numero eccessivo di oggetti visivi in una pagina (tenere presente che ogni oggetto visivo è una query)
- **Durata query lunghe durate** può indicare che le progettazioni di modello non sono ottimizzate, soprattutto quando sono attivi in una capacità di più set di dati e un solo set di dati produce lunga durate delle query. Ciò suggerisce che la capacità è sufficientemente risorse assegnata e che il set di dati nella domanda è solo lento o non ottimali. Query a esecuzione prolungata può essere problematica perché in grado di bloccare l'accesso alle risorse richieste da altri processi.
- **Aggiornamento lungo tempi di attesa o tempi di attesa di chiamate per intelligenza artificiale** indica memoria insufficiente a causa di molti modelli attive che utilizzano memoria, o che sta bloccando un aggiornamento problematico altra viene aggiornata (superamento dei limiti di aggiornamento parallelo).

Una spiegazione più dettagliata di come usare le metriche viene descritta successivamente nel [ottimizzazione della capacità Premium](#optimizing-premium-capacities) sezione.

## <a name="optimizing-premium-capacities"></a>Ottimizzazione della capacità Premium

Quando si verificano problemi di prestazioni della capacità Premium, un primo approccio comune è ottimizzare o ottimizzare le soluzioni già distribuite per ripristinare i tempi di risposta accettabili. La logica esegue l'override è per evitare di acquistare altra capacità di Premium, a meno che non può essere giustificata.

Quando è necessaria ulteriore capacità Premium, sono disponibili due opzioni che verranno descritta più avanti in questa sezione:

- Aumentare la capacità Premium
- Aggiungere una nuova capacità Premium

Infine, il test di approcci e ridimensionamento delle capacità Premium si concluderà in questa sezione.

### <a name="general-best-practices"></a>Procedure consigliate generali

Quando l'impegno per ottenere migliori prestazioni presenti e utilizzo sono alcune procedure consigliate che possono essere eseguite a bordo come indicazioni generali. Tra queste sono incluse:

- Utilizzando le aree di lavoro di app anziché le aree di lavoro personale
- Separazione di BI self-service (SSBI) e aziendali critici in capacità differenti

  ![La separazione aziendali critici e BI self-service in capacità differenti](media/whitepaper-premium-deployment/separate-capacities.png)

- Se la condivisione del contenuto solo con gli utenti di Power BI Pro, potrebbe essere necessario archiviare il contenuto in una capacità dedicata
- Usare le capacità dedicate durante la ricerca per ottenere un tempo di aggiornamento specifico oppure quando le funzionalità specifiche sono necessarie, ad esempio grandi set di dati o impaginato di reporting

### <a name="addressing-common-questions"></a>Indirizzamento delle domande più comuni

Ottimizzazione delle distribuzioni di Power BI Premium è un argomento complesso che interessa la comprensione dei requisiti del carico di lavoro, le risorse disponibili e l'uso effettivo.

Questo argomento illustra sette domande comuni sul supporto, che descrive i possibili problemi e spiegazioni e informazioni su come identificare e risolvere i problemi.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Perché è la capacità lenta e che cosa può fare?

Esistono molti motivi che possono contribuire a una lenta capacità Premium. Questa domanda richiede ulteriore informazioni utili per comprendere cosa si intende per lento. Sono lente caricare i report? O non vengono caricati per? Sono oggetti visivi del report lente caricare o aggiornare quando gli utenti interagiscono con il report? Gli aggiornamenti richiedono più tempo per il completamento previsto o si è verificato in precedenza?

Avendo compreso del motivo, è possibile iniziare a esaminare. Le risposte alle domande seguenti sei consente di risolvere più problemi specifici.

#### <a name="what-content-is-using-up-my-capacity"></a>Il tipo di contenuto Usa la capacità?

È possibile usare la **le metriche della capacità di Power BI Premium** Filtra per capacità ed esaminare le metriche delle prestazioni per il contenuto dell'area di lavoro dell'app. È possibile esaminare l'uso di risorse e le metriche delle prestazioni per ora negli ultimi sette giorni per tutto il contenuto archiviato all'interno di una capacità Premium. Ciò è spesso il primo passaggio da eseguire quando la risoluzione dei problemi di interesse generale sulle prestazioni della capacità Premium.

Le metriche chiave per il monitoraggio includono:

- Utilizzo medio della CPU e il conteggio di utilizzo elevato
- Calcolare la media di memoria e il conteggio di utilizzo elevato e utilizzo della memoria per i set di dati specifico, flussi di dati e i report impaginati
- Attiva set di dati caricati in memoria
- Durate delle query medi e massimi
- Tempi di attesa media della query
- Flusso di dati e set di dati medio aggiornamento volte
- Intelligenza artificiale medio chiamare volte e tempi di attesa

Inoltre, nell'App Power BI Premium capacità metriche memoria attive Mostra la quantità totale di memoria allocata a un report che non può essere rimosso perché è in uso negli ultimi tre minuti. Un picco nel tempo di attesa di aggiornamento elevato potrebbe essere correlato con un set di dati di grandi dimensioni e/o attivo.

Il grafico "Parte superiore di 5 per la durata media" evidenzia i primi cinque set di dati, i report impaginati, flussi di dati e le chiamate di intelligenza artificiale per un utilizzo della capacità di risorse. Contenuto negli elenchi di cinque principali sono candidati per l'ottimizzazione di indagine e la possibile.

#### <a name="why-are-reports-slow"></a>Perché i report di rallentamento?

Le tabelle seguenti illustrano i possibili problemi e sui modi per identificare e gestirli.

##### <a name="insufficient-capacity-resources"></a>Risorse di capacità insufficiente

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Memoria attive totali elevata (modello non può essere rimosso perché è in uso negli ultimi tre minuti)<br><br> Più elevati picchi di tempi di attesa query<br><br> Più elevati picchi di tempi di attesa di aggiornamento | Monitorare le metriche della memoria \[ [18](#endnote-18)\]e i conteggi di rimozione \[ [19](#endnote-19)\] | Diminuire le dimensioni del modello, o convertire alla modalità DirectQuery, vedere la [ottimizzazione modelli](#optimizing-models) argomento in questa sezione<br><br> Aumentare la capacità<br><br> Assegnare il contenuto a una capacità diversa |

##### <a name="inefficient-report-designs"></a>Progettazioni di report inefficiente

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Le pagine del report contengono numerosi oggetti visivi (applicazione di filtri interattiva può attivare almeno una query per ogni oggetto visivo)<br><br> Gli oggetti visivi recuperano più dati rispetto al necessario | Esaminare le progettazioni di report<br><br> Intervista agli utenti di report di comprendere come interagiscono con i report<br><br> Monitorare le metriche di query di set di dati \[ [20](#endnote-20)\] | Report di riprogettazione con oggetti visivi di un numero inferiore per ogni pagina |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>Set di dati lenta (specialmente quando i report già stato eseguito correttamente)

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Sempre più grandi volumi di dati di importazione<br><br> Logica di calcolo complesso o inefficiente, inclusi i ruoli a livello di riga<br><br> Modello non completamente ottimizzato<br><br> (DQ/LC) Latenza di gateway<br><br> Tempi di risposta query DQ origine lenta | Esaminare le progettazioni di modello<br><br> Monitorare i contatori delle prestazioni del gateway | Vedere le [ottimizzazione modelli](#optimizing-models) argomento in questa sezione |

##### <a name="high-concurrent-report-usage"></a>Utilizzo elevato rapporto simultanee

| Possibili spiegazioni | Come identificare | Come risolvere |
| --- | --- | --- |
| Tempi di attesa di query elevati<br><br> Saturazione della CPU<br><br> Limiti di connessione DQ/LC superati | Monitorare l'utilizzo della CPU \[ [21](#endnote-21)\], tempi di attesa di query e l'utilizzo di DQ/LC \[ [22](#endnote-22) \] metriche + durate delle Query, se possibile ripristinarne indicare i problemi di concorrenza | Aumentare la capacità oppure assegnare il contenuto a una capacità diversa<br><br> Report di riprogettazione con oggetti visivi di un numero inferiore per ogni pagina |

#### <a name="why-are-reports-not-loading"></a>Perché i report non stia caricando?

Quando i report non è possibile caricarlo è uno scenario peggiore e un chiaro indizio che la capacità di memoria insufficiente ed è eccessiva riscaldata. Ciò può verificarsi quando tutti i modelli caricati vengono sottoposte a attivamente e pertanto non è possibile eliminarle e qualsiasi operazione di aggiornamento sono stato messo in pausa o posticipate. Il servizio Power BI proverà a caricare il set di dati per 30 secondi e l'utente normalmente viene avvisato dell'errore con un suggerimento per riprovare più tardi.

Non è attualmente disponibile alcuna metrica da monitorare per il report errori di caricamento. Monitoraggio memoria del sistema, specificamente più alto utilizzo e tempo di utilizzo più elevato, è possibile identificare il potenziale per risolvere questo problema. Eliminazioni di set di dati elevata e lungo tempo di attesa medio aggiornamento set di dati è stato possibile suggerire che questo problema è in corso.

Se ciò si verifica molto raramente, questo potrebbe non essere considerato un problema di priorità. Gli utenti del report vengono informati che il servizio è occupato e che è opportuno ritentare dopo un breve periodo di tempo. In questo caso troppa frequenza, il problema può essere risolto aumentando la capacità Premium oppure tramite l'assegnazione del contenuto a una capacità diversa.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **errori di Query** metrica per determinare in questo caso. È anche possibile riavviare la capacità, la reimpostazione di tutte le operazioni in caso di sovraccarico del sistema.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>Il motivo per cui gli aggiornamenti non vengono avviato su pianificazione?

Ore di inizio aggiornamento pianificato non è garantite. È importante ricordare che il servizio Power BI avrà sempre la priorità operazioni interattive su operazioni in background. L'aggiornamento è un'operazione in background che può verificarsi quando due condizioni sono soddisfatte:

- È disponibile memoria sufficiente
- Non viene superato il numero di aggiornamenti simultanei supportati per la capacità Premium

Quando non vengono soddisfatte le condizioni, l'aggiornamento viene accodata fino a quando le condizioni sono soddisfacenti.

Per un aggiornamento completo, è importante ricordare che sono necessaria almeno raddoppierà le dimensioni di memoria corrente del set di dati. Se non è disponibile memoria sufficiente, non è possibile iniziare l'aggiornamento fino a quando non la rimozione del modello consente di liberare memoria: questo significa che ritarda fino a quando uno o più set di dati diventa inattiva e può essere eliminata.

È importante ricordare che il numero di aggiornamenti simultanei massimi supportato è impostato su 1,5 volte i back-end memorie centrali, arrotondati per eccesso.

Un aggiornamento pianificato non riuscirà quando che non può cominciare prima della scadenza di inizio dell'aggiornamento pianificato successivo. Un aggiornamento su richiesta attivato manualmente dall'interfaccia utente tenterà di eseguire fino a tre volte prima che si verifichi.

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **medio aggiornamento tempo di attesa (minuti)** metrica per determinare il ritardo medio tra l'orario pianificato e l'inizio dell'operazione.

Anche se non viene in genere una priorità di amministrazione per influenzare i dati in fase di aggiornamento, assicurarsi che sia disponibile memoria sufficiente. Questa operazione potrebbe comportare l'isolamento del set di dati per le capacità con sufficienti risorse note. È anche possibile che gli amministratori è stato possibile coordinare con i proprietari dei set di dati per scaglionare o ridurre i tempi di aggiornamento dati pianificato per ridurre al minimo i conflitti. Si noti che non è possibile che un amministratore di visualizzare la coda di aggiornamento o per recuperare le pianificazioni di set di dati.

#### <a name="why-are-refreshes-slow"></a>Il motivo per cui vengono aggiornati lenta?

Gli aggiornamenti possono essere lento - o percepita lenta (come gli indirizzi di domanda comune precedente).

Quando in realtà, l'aggiornamento è lenta, può essere dovuto a diversi motivi:

- CPU insufficiente (l'aggiornamento può essere elevato della CPU)
- Memoria insufficiente, causando la sospensione di aggiornamento (che richiede l'aggiornamento ricominciare da capo quando le condizioni sono favorevoli per riprendere)
- Non-capacità motivi, tra cui reattività del sistema di origine dati, la latenza di rete, autorizzazioni non valide o velocità effettiva del gateway
- Volume di dati - un buon motivo per configurare incrementale aggiorna, come descritto di seguito

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **durata media di aggiornamento (minuti)** metrica per determinare un benchmark per il confronto nel corso del tempo e il **medio aggiornamento tempo di attesa (minuti)** metriche per determinare il ritardo medio tra medio di ritardo tra l'orario pianificato e l'inizio dell'operazione.

L'aggiornamento incrementale può ridurre notevolmente durata di aggiornamento dati, in particolare per tabelle di modelli di grandi dimensioni. Esistono quattro vantaggi associati con l'aggiornamento incrementale:

- **Gli aggiornamenti sono più veloci** : Solo un subset di una tabella richiede il caricamento, riducendo l'utilizzo della CPU e memoria e il parallelismo può essere superiore quando l'aggiornamento di più partizioni
- **Gli aggiornamenti si verificano solo quando necessario** : I criteri di aggiornamento incrementale possono essere configurati per caricare solo quando vengono modificati dati
- **Gli aggiornamenti sono più affidabili** : Le connessioni in esecuzione più brevi per i sistemi di origine dati volatili sono meno soggette a disconnessione
- **I modelli rimangono trim** : I criteri di aggiornamento incrementale possono essere configurati per Rimuovi automaticamente cronologia oltre a una finestra temporale scorrevole di tempo

Per altre informazioni, vedere la [Incremental aggiornamento in Power BI Premium](service-premium-incremental-refresh.md) documento.

#### <a name="why-are-data-refreshes-not-completing"></a>Perché i dati viene aggiornato non è stato completato?

Quando l'aggiornamento dei dati verrà avviata ma non viene completato, può essere dovuto a diversi motivi:

- Memoria insufficiente, anche se è presente un solo modello la capacità Premium, ad esempio la dimensione del modello è molto grande
- Non-capacità motivi, inclusi i dati di origine disconnessione del sistema, le autorizzazioni non è valide o errore di gateway

Gli amministratori della capacità (e gli amministratori del servizio Power BI) possono monitorare il **Aggiorna gli errori dovuti a memoria insufficiente** metrica.

#### <a name="why-are-ai-calls-failing"></a>Il motivo per cui vengono chiamate per intelligenza artificiale non superati?

Le chiamate di intelligenza artificiale possono non riuscire per diversi motivi. La memoria minima necessaria per avviare l'intelligenza artificiale per il carico di lavoro è 5 GB, ma ciò potrebbe non essere sufficiente per alcuni set di dati di input. Ad esempio, training del modello di apprendimento automatico richiede almeno due volte e talvolta più volte la dimensione di set di dati input. Inoltre, una chiamata di intelligenza artificiale viene terminata se sono necessari più di due ore. Per la macchina automatizzato chiamate di training del modello che non completata dopo due ore, il modello migliore disponibile in queste due ore di formazione viene restituito.  Le chiamate di intelligenza artificiale possono essere interrotta da richieste interattive, che hanno la precedenza.

Gli amministratori devono monitorare i tempi di attesa per intelligenza artificiale segni di altre richieste che hanno la precedenza. Gli amministratori possono anche assicurarsi che sia disponibile per il carico di lavoro di intelligenza artificiale rispetto all'input di dati di dimensioni memoria sufficiente. Ciò può implicare isolare i carichi di lavoro di intelligenza artificiale per le capacità note per avere risorse sufficienti. È anche possibile che gli amministratori è stato possibile coordinare con i proprietari del flusso di dati per scaglionare o ridurre i tempi di aggiornamento del flusso di dati per ridurre al minimo i conflitti. Si noti che non è possibile che un amministratore di visualizzare la coda di chiamata per intelligenza artificiale.

### <a name="optimizing-models"></a>Ottimizzare i modelli

Progettazione modello ottimale è fondamentale nell'offrire una soluzione efficiente e scalabile. Tuttavia, è oltre l'ambito di questo white paper per fornire una descrizione completa. Al contrario, questa sezione fornisce le aree principali da tenere in considerazione quando ottimizzare i modelli.

#### <a name="optimizing-power-bi-hosted-models"></a>Ottimizzare i modelli di Power BI ospitati

Ottimizzare i modelli ospitati in una capacità Premium possono essere ottenuti a livello di dati origini e modello.

Prendere in considerazione la possibilità di ottimizzazione per un modello di importazione:

![Possibilità di ottimizzazione per un modello di importazione](media/whitepaper-premium-deployment/import-model-optimizations.png)

A livello di origine dati:

- Origini dati relazionali possono essere ottimizzate per garantire l'aggiornamento più rapido possibile da pre-l'integrazione di dati, applicare indici appropriati, la definizione di partizioni della tabella che si allineano ai periodi di aggiornamento incrementale e materializzare i calcoli (invece di calcolato tabelle e colonne del modello) o l'aggiunta di logica di calcolo per le visualizzazioni
- Origini dati relazionali possono essere pre-integrate con archivi relazionali
- Assicurarsi che i gateway avere risorse sufficienti, preferibilmente prevede computer dedicati con sufficiente larghezza di banda di rete e in stretta vicinanza alle origini dati

A livello del modello:

- Progettazioni query di Power Query possono ridurre al minimo o rimuovere trasformazioni complesse e in particolare quelli che uniscono diverse origini dati (data warehouse ottenere questo risultato durante la fase di Extract-Transform-Load). Assicurando che i livelli di privacy di origine dei dati appropriati siano impostati, questo può evitare anche che richiedono Power BI caricare tutti i risultati per produrre un risultato combinato per tutte le query.
- La struttura del modello determina i dati da caricare e ha un impatto diretto sulle dimensioni del modello. Si può essere progettato per evitare il caricamento di dati non necessari, rimuovendo le colonne, la rimozione di righe (in particolare i dati cronologici) oppure caricando i dati di riepilogo (a scapito di caricamento di dati dettagliati). Tramite la rimozione di colonne con cardinalità elevata (in particolare sulle colonne di testo) che non archiviare né comprimere in modo molto efficiente, è possibile riduzione delle dimensioni notevoli.
- Le prestazioni delle query del modello possono essere migliorate tramite la configurazione di relazioni per direzione singola a meno che non è presente un motivo valido per consentire il filtro bidirezionale. È consigliabile usare anche la funzione CROSSFILTER anziché filtro bidirezionale.
- Tabelle di aggregazione possono ottenere query più veloci le risposte caricando pre-riepilogo dati, tuttavia, ciò aumenta la dimensione del modello e risultato in tempi più lunghi di aggiornamento. In genere, le tabelle di aggregazione devono essere riservate per i modelli di dimensioni molto grandi o progetti di modelli composto.
- Tabelle e colonne calcolate aumentano le dimensioni del modello e comportare tempi di aggiornamento. In generale, una dimensioni di archiviazione inferiori e tempi di aggiornamento può essere ottenute quando i dati viene materializzati o calcolati nell'origine dati. In caso contrario, utilizzano colonne personalizzate di Power Query può offrire la compressione di archiviazione migliorata.
- Potrebbero esserci opportunità per ottimizzare le espressioni DAX per misure e le regole a livello di riga, ad esempio la riscrittura per la logica per evitare costose formule
- L'aggiornamento incrementale può notevolmente ridurre i tempi di aggiornamento e conservare la memoria e CPU. L'aggiornamento incrementale può essere configurato anche per rimuovere i dati cronologici mantenendo le dimensioni dei modelli trim.
- Un modello può essere riprogettato come due modelli quando sono presenti modelli di query diversi e in conflitto. Ad esempio, alcuni report le aggregazioni di alto livello presente sulle tutti cronologia e può tollerare la latenza di 24 ore. Altri report sono in questione con i dati di oggi e richiedono l'accesso granulare a singole transazioni. Invece di progettazione un solo modello per soddisfare tutti i report, creare due modelli ottimizzati per ogni requisito.

Prendere in considerazione la possibilità di ottimizzazione per un modello DirectQuery. Come il modello di inoltrare le richieste di query all'origine dati sottostante, è essenziale alla fornitura di query del modello reattivo di ottimizzazione di origine dati.

 ![Possibilità di ottimizzazione per un modello DirectQuery](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

A livello di origine dati:

- L'origine dati può essere ottimizzato per garantire il più rapido possibile l'esecuzione di query da pre-integrazione di dati (che non sono possibili a livello del modello), applicare indici appropriati, la definizione di partizioni della tabella, la materializzazione riepilogo dati (con le viste indicizzate), e riducendo al minimo la quantità di calcolo. Un'esperienza ottimale si ottiene quando le query pass-through è necessario filtrare solo ed eseguire degli inner join tra tabelle indicizzate o le viste.
- Assicurarsi che i gateway avere risorse sufficienti, preferibilmente prevede computer dedicati con sufficiente larghezza di banda di rete e in stretta vicinanza all'origine dati

A livello del modello:

- Query di Power Query progettazioni preferibilmente non applicare alcuna trasformazione - tentare in altro modo mantenere le trasformazioni di inattività minimo
- Le prestazioni delle query del modello possono essere migliorate tramite la configurazione di relazioni per direzione singola a meno che non è presente un motivo valido per consentire il filtro bidirezionale. Inoltre, modellare relazioni devono essere configurate per presupporre viene applicata l'integrità referenziale (in questo caso) e comporterà la query dell'origine dati usando gli inner join più efficiente (invece di outer join).
- Evitare di creare colonne personalizzate di query di Power Query o una colonna calcolata del modello: questi criteri nell'origine dati, quando possibile materializzare
- Potrebbero esserci opportunità per ottimizzare le espressioni DAX per misure e le regole a livello di riga, ad esempio la riscrittura per la logica per evitare costose formule

Prendere in considerazione la possibilità di ottimizzazione per un modello composito. È importante ricordare che un modello composito consente una combinazione di importazione e DirectQuery tabelle.

![Possibilità di ottimizzazione per un modello composito](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- In genere, gli argomenti di ottimizzazione per i modelli di Import che di DirectQuery si applicano per le tabelle del modello composito che usano queste modalità di archiviazione.
- In genere, possono ottenere una progettazione bilanciata configurando tabelle tipo di dimensione, che rappresentano le entità aziendali, come Dual-tipo di fact e modalità di tabelle di archiviazione (spesso tabelle di grandi dimensioni che rappresentano informazioni operative) come modalità di archiviazione DirectQuery. Modalità di archiviazione duale significa entrambi importazione e DirectQuery le modalità di archiviazione e ciò consente al servizio Power BI determinare la modalità di archiviazione più efficiente da usare durante la generazione di una query nativa per pass-through.
- Assicurarsi che i gateway avere risorse sufficienti, preferibilmente prevede computer dedicati con sufficiente larghezza di banda di rete e in stretta vicinanza alle origini dati
- Le tabelle con aggregazioni configurate come modalità di archiviazione di importazione è in grado di offrire miglioramenti delle prestazioni di query significativo quando utilizzato per riepilogare le tabelle dei fatti-type con modalità archiviazione DirectQuery. In questo caso, le tabelle di aggregazione aumenterà le dimensioni del modello e aumentare la durata dell'aggiornamento, e spesso si tratta di un compromesso accettabile per le query più veloci.

#### <a name="optimizing-externally-hosted-models"></a>Ottimizzare i modelli di ospitato esternamente

Molte possibilità di ottimizzazione illustrati nel [Optimizing Power BI-Hosted modelli](#optimizing-power-bi-hosted-models) argomento si applicano anche ai modelli sviluppati con Azure Analysis Services e SQL Server Analysis Services. Le eccezioni non crittografate sono determinate funzionalità che non sono attualmente supportate, inclusi i modelli compositi e tabelle di aggregazione.

Un'altra considerazione per i set di dati ma ospitato è il database di hosting in relazione al servizio Power BI. Per Azure Analysis Services, ciò significa creare la risorsa di Azure nella stessa area come tenant di Power BI (area iniziale). Per SQL Server Analysis Services, per IaaS, ciò significa che ospita la VM nella stessa area e in locale, significa assicurare un programma di installazione di gateway efficiente.

Per inciso, potrebbe essere interessante notare che i database di Azure Analysis Services e i database tabulari di SQL Server Analysis Services richiedono che i propri modelli caricare completamente in memoria e che rimangano presenti in qualsiasi momento per supportare l'esecuzione di query. Analogamente al servizio Power BI, dovrà essere memoria sufficiente per l'aggiornamento se il modello deve rimanere online durante l'aggiornamento. A differenza del servizio Power BI, non è previsto che i modelli sono obsoleti automaticamente da e verso memoria in base all'utilizzo. Power BI Premium, di conseguenza, offre un approccio più efficiente per massimizzare l'esecuzione di query del modello con l'utilizzo di memoria inferiore.

### <a name="capacity-planning"></a>Pianificazione della capacità

La dimensione di una capacità Premium determina la memoria disponibile e le risorse del processore e limiti imposti per la capacità. Anche il numero di capacità Premium è un fattore importante, come la creazione di Premium più capacità può consentire di isolare i carichi di lavoro tra loro. Si noti che l'archiviazione è di 100 TB per ogni nodo di capacità e questa condizione potrebbe essere più che sufficiente per qualsiasi carico di lavoro.

Determinazione della dimensione e il numero di capacità Premium può essere difficile, soprattutto per le capacità iniziale, che si crea. Il primo passaggio quando il ridimensionamento delle capacità consiste nel comprendere la media del carico di lavoro che rappresentano previsto l'utilizzo quotidiano. È importante comprendere che non tutti i carichi di lavoro sono uguali. Ad esempio, a un estremo di una gamma - 100 utenti simultanei, l'accesso a una singola pagina che contiene un singolo oggetto visivo è facile ottenere. Ancora - a altra estremità dello spettro - 100 utenti simultanei che accedono ai 100 report diversi, ognuno con 100 oggetti visivi nella pagina del report, sta per effettuare richieste molto diverse delle risorse di capacità.

Gli amministratori della capacità, pertanto è necessario prendere in considerazione molti fattori specifici per l'ambiente, contenuto e l'utilizzo previsto. L'obiettivo di override è ottimizzare l'utilizzo della capacità e offrire tempi di query coerenti, tempi di attesa accettabile e percentuali di rimozione. Fattori da prendere in considerazione possono includere:

- **Le caratteristiche di dimensioni e i dati del modello** : I modelli di importazione devono essere completamente caricati nella memoria per consentire l'esecuzione di query o l'aggiornamento. I set di dati di LC/DQ può richiedere tempi significativi del processore e memoria probabilmente significativa a valutare misure complesse o le regole a livello di riga. Velocità effettiva delle query LC/DQ, memoria e processore dimensione sono vincolate dalle dimensioni della capacità.
- **Modelli attivi simultanei** : L'esecuzione di query simultanee di importazione diversi modelli distribuirà migliore della velocità di risposta e le prestazioni quando rimangono in memoria. Deve essere presente memoria sufficiente per ospitare tutti i modelli sottoposti frequentemente a query, con ulteriore memoria per consentire loro l'aggiornamento.
- **Aggiornamento dei modelli importazione** : Il tipo di aggiornamento (completa o incrementale), durata e la complessità delle query di Power Query e tabella/colonna calcolata per la logica può influire sulla memoria e in particolare l'utilizzo del processore. Gli aggiornamenti simultanei sono limitati dalle dimensioni della capacità (1,5 x backend v-core, arrotondati per eccesso).
- **Query simultanee** : Può causare molte query simultanee in risponde segnala quando processore o LC/DQ connessioni supera il limite di capacità. Questo avviene soprattutto per le pagine del report che includono numerosi oggetti visivi.
- **Flussi di dati, impaginati, report e le funzioni di intelligenza artificiale** : La capacità può essere configurata per supportare flussi di dati, i report impaginati e funzioni di intelligenza artificiale, con ognuno dei quali richiede una configurabile percentuale massima di memoria di capacità. Memoria viene allocata dinamicamente per flussi di dati, ma viene allocato in modo statico per i report impaginati e il carico di lavoro di intelligenza artificiale.

Oltre a questi fattori, gli amministratori della capacità possono provare a creare più capacità. Le capacità più consentono l'isolamento dei carichi di lavoro e possono essere configurate per verificare che i carichi di lavoro con priorità hanno garantito di risorse. Ad esempio, le capacità di due possono essere create per separare i carichi di lavoro cruciali da carichi di lavoro di BI (SSBI) self-service. La capacità di business-critical è utilizzabile per isolare i modelli di grandi dimensioni aziendali fornendo loro con risorse garantite, con accesso consentita solo ai reparti IT di creazione. La capacità SSBI utilizzabile per ospitare un numero crescente di modelli più piccoli, con accesso concesso ai business analyst. La capacità SSBI potrebbe verificarsi in momenti attese query o aggiornamento sono tollerabile.

Nel corso del tempo, gli amministratori della capacità possono bilanciare le aree di lavoro tra le capacità per lo spostamento del contenuto tra le aree di lavoro o le aree di lavoro tra le capacità e aumentando le capacità verso l'alto o verso il basso. Per ospitare più grande in genere, i modelli scalabilità verticale e per una concorrenza più elevata è scalare orizzontalmente.

È importante ricordare che l'acquisto di una licenza fornisce al tenant memorie centrali virtuali. L'acquisto di una **P3** sottoscrizione può essere utilizzata per crearne uno, o fino a quattro le capacità Premium, vale a dire 1 x P3 o 2x P2 o 4 x P1. Inoltre, prima upsizing una capacità di P2 a una capacità di P3, possa essere presi in considerazione la suddivisione di memorie centrali virtuali per creare due le capacità di P1.

### <a name="testing-approaches"></a>Test di approcci

Una volta che viene stabilita una dimensioni della capacità, il test può essere eseguito mediante la creazione di un ambiente controllato. Un'opzione economica e pratica consiste nel creare una capacità di Azure (SKU), notare che una capacità di P1 è la stessa dimensione una capacità A4, con P2 e P3 capacità le stesse dimensioni di capacità di A5 e A6, rispettivamente. Funzionalità di Azure è possibile creare rapidamente e vengono fatturati su base oraria. Pertanto, una volta completato il test, possano essere facilmente eliminate per arrestare l'addebito dei costi.

Il contenuto di prova può essere aggiunto a aree di lavoro create la capacità di Azure e come un singolo utente può quindi eseguire i report per generare un carico di lavoro realistico e rappresentativo di query. Se sono presenti modelli di importazione, un aggiornamento per ogni modello deve essere eseguito anche. Strumenti di monitoraggio sono quindi utilizzabile per esaminare tutte le metriche per comprendere l'utilizzo delle risorse.

È importante che i test siano ripetibili: Test da eseguire più volte e deve recapitare approssimativamente lo stesso risultato ogni volta. Una media di questi risultati è utilizzabile per estrapolare e stimare il carico di lavoro in condizioni di produzione reale.

Per generare un test di stress, si consiglia di sviluppare un'applicazione per simulare un carico di lavoro realistico di test di carico. Le specifiche di come ottenere questo risultato non rientrano nell'ambito di questo white paper. Per altre informazioni con un esempio di codice, vedere la [Load Testing Power BI applicazioni con Visual Studio Load Test](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinar.

## <a name="exploring-real-world-scenarios"></a>Esplorazione di scenari reali

In questa sezione, verranno introdotte diverse scenari reali per descrivere i problemi comuni o problematiche, come di identificarli e come per la risoluzione:

- [Mantenere aggiornati i set di dati](#keeping-datasets-up-to-date)
- [Che identifica i set di dati risponde lente](#identifying-slow-responding-datasets)
- [Identificazione delle cause per sporadicamente rallentare rispondono i set di dati](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinazione se vi è memoria sufficiente](#determining-whether-there-is-enough-memory)
- [Determinare se vi sia sufficiente CPU](#determining-whether-there-is-enough-cpu)

I passaggi, insieme a esempi di grafico e tabella sono dal **App di metriche di capacità di Power BI Premium** (app) che un amministratore di Power BI avranno accesso a.

### <a name="keeping-datasets-up-to-date"></a>Mantenimento dei set di dati fino alla data

In questo scenario, è stata attivata un'indagine quando gli utenti espresso lamentele che i dati del report in alcuni casi sembravano essere obsolete o "obsolete".

Nell'app, l'amministratore interagisce con il **consente di aggiornare** visivo, l'ordinamento di set di dati il **il tempo di attesa massimo** statistiche in ordine decrescente. Ciò consente di visualizzare i set di dati che hanno tempi più lunghi di attesa volte, raggruppati per nome dell'area di lavoro.

![Aggiornamenti di set di dati ordinati in ordine decrescente di tempo di attesa massimo, raggruppato per area di lavoro](media/whitepaper-premium-deployment/dataset-refreshes.png)

Inoltre, nelle **oraria Aggiorna attesa tempi medi** visual, egli nota che i tempi di attesa di aggiornamento in modo coerente picchi 16:00 circa ogni giorno.

![L'aggiornamento è in attesa picco periodicamente alle 16.00](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Sono disponibili numerosi possibili spiegazioni per questi risultati:

- Troppi tentativi di aggiornamento potrebbero essere eseguita allo stesso tempo, che superano i limiti imposti dal nodo di capacità (sei aggiornamenti simultanei in un P1 con allocazione di memoria predefinita)

- I set di dati da aggiornare possono risultare troppo grandi per rientrare nella memoria disponibile (che richiede almeno 2 volte la memoria necessaria per l'aggiornamento completo)
- Inefficiente per la logica di Power Query può essere causando un picco di utilizzo della memoria durante l'aggiornamento di set di dati. In una capacità occupata questo occasionalmente può raggiungere il limite fisico, l'esecuzione dell'aggiornamento e potenzialmente influire sulle altre operazioni di visualizzazione di report sulla capacità.
- Frequentemente a query i set di dati che devono rimanere in memoria può influire sulle capacità di altri set di dati di aggiornamento, a causa di memoria disponibile è limitata

Che consente di esaminare questo, l'amministratore di Power BI può cercare:

- Scarsa disponibilità di memoria al momento dell'aggiornamento dei dati, quando la memoria disponibile è inferiore a 2 volte la dimensione del set di dati da aggiornare
- Set di dati che sono non stati in fase di aggiornamento e non in memoria prima dell'aggiornamento, ma che viene avviato per mostrare il traffico interattivo durante i periodi di aggiornamento pesanti. Per visualizzare i set di dati sono stati caricati in memoria in qualsiasi momento di Power BI amministratore può esaminare i set di dati relativa alla **set di dati** della scheda del filtro incrociato e l'app a un determinato momento facendo clic su una delle barre nel **oraria Conteggi di set di dati caricato**. Un picco locale (illustrato nell'immagine seguente) indica un'ora quando più set di dati sono stati caricati in memoria, che possa ritardare l'avvio degli aggiornamenti pianificati
- Eliminazioni di set di dati maggiore richiede Inserisci durante gli aggiornamenti dei dati sono pianificati per avviarsi, che indica durante l'utilizzo della memoria elevato causata, è necessario gestire un numero eccessivo diversi report interattivi antecedente al momento dell'aggiornamento. Il **eliminazioni di set di dati orarie e il consumo di memoria** visual possono indicare chiaramente i picchi di eliminazioni.

L'immagine seguente mostra un picco locale nei set di dati caricato, che suggerisce l'esecuzione di query interattivo posticipato iniziale degli aggiornamenti. La selezione di un periodo di tempo nel **oraria conta set di dati caricati** visivo attraverserà filtro il **set di dati di dimensioni** visual.

![Un picco locale nei set di dati caricato suggerisce interattiva avvio ritardato l'esecuzione di query degli aggiornamenti](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

L'amministratore di Power BI è possibile tentare di risolvere il problema eseguendo i passaggi per assicurarsi che sia disponibile per gli aggiornamenti dei dati per l'avvio tramite memoria sufficiente:

- Connessione al set di dati e ai proprietari chiedendogli di scaglionare e lo spazio dati pianificazioni dell'aggiornamento
- La riduzione di set di dati carico della query rimuovendo i dashboard non necessari o dashboard di riquadri, specialmente quelle che applicare la sicurezza a livello di riga
- Velocizzare gli aggiornamenti dei dati, ottimizzando al tempo per la logica di Power Query, modello di colonne calcolate o aggiornare tabelle, riducendo le dimensioni di set di dati o la configurazione più grandi set di dati per eseguire dati incrementali

### <a name="identifying-slow-responding-datasets"></a>Che identifica i set di dati risponde lente

In questo scenario, è stata attivata un'indagine quando gli utenti espresso lamentele che determinati rapporti impiega molto tempo per aprire e in alcuni casi si blocca.

Nell'app, l'amministratore di Power BI può usare la **durate delle Query** visual per determinare i set di dati prestazioni peggiori ordinando i set di dati da decrescente **durata media**. Questo oggetto visivo Mostra anche set di dati i conteggi di query, pertanto è possibile vedere con quale frequenza vengono eseguite su set di dati.

![Rivelare i set di dati prestazioni peggiori](media/whitepaper-premium-deployment/worst-performing-datasets.png)

L'amministratore di Power BI può fare riferimento al **distribuzione della durata Query** visivo che mostra una distribuzione complessiva delle prestazioni delle query suddivisi in bucket: (< = 30 ms, 0 a 100 ms, e così via) per il periodo di tempo filtrato. In genere, le query che accettano un secondo o meno vengono considerati reattiva dalla maggior parte degli utenti; le query che richiedono più tempo tendono a creare una percezione del peggioramento delle prestazioni.

Il **oraria distribuzione della durata Query** visual consente all'amministratore di Power BI identificare i periodi di un'ora quando le prestazioni della capacità potrebbero essere stata percepita come insufficienti. Maggiore la barra di segmenti di query rappresentano le durate oltre a un secondo, il più grande il rischio che gli utenti percepiranno una riduzione delle prestazioni.

L'oggetto visivo è interattiva e quando viene selezionato un segmento della barra, il corrispondente **durate delle Query** visivo nella pagina del report tabella è a filtro incrociato per visualizzare il set di dati rappresenta. Questo filtro incrociato consente all'amministratore di Power BI identificare facilmente quale set di dati risponde lentamente.

L'immagine seguente mostra un oggetto visivo filtrato in base **oraria distribuzioni di durata Query**, messa a fuoco sui set di dati prestazioni peggiori in bucket di un'ora. 

![Filtrato oraria Query durata distribuzioni visual Mostra peggio eseguendo i set di dati](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

Una volta identificato il set di dati dalle prestazioni scarse in un intervallo di tempo specifico di 1 ora, l'amministratore di Power BI può esaminare se una riduzione delle prestazioni è causata da una capacità in overload o a causa di un modo non corretto progettato set di dati o report. A tale scopo, è possibile fare riferimento al **tempi di attesa delle Query** visivo e i set di dati di ordinamento ordine decrescente di tempo di attesa media della query. Se è in attesa un'alta percentuale delle query, una richiesta elevata per il set di dati è probabilmente la causa delle numerose attese di query. Se la query Media di tempo di attesa è sostanziale (> 100 ms), potrebbe essere opportuno valutare il set di dati e report per vedere se è possibile ottimizzare. Ad esempio, forse meno oggetti visivi nella data pagine del report o un'ottimizzazione di espressione DAX.

![L'oggetto visivo tempi di attesa delle Query consente di visualizzare i set di dati con prestazioni ridotte](media/whitepaper-premium-deployment/query-wait-times.png)

Esistono diversi motivi possibili per la compilazione in fase di attesa query backup nel set di dati:

- Una progettazione ottimale del modello, le espressioni di misura o persino progettazione dei report - tutte le circostanze che possono contribuire a query che utilizzano livelli elevati di CPU a esecuzione prolungata. In tal modo le nuove query in attesa finché i thread CPU diventino disponibili ed è possibile creare un effetto di serie di istruzioni (blocco del traffico può essere considerata), presenta comunemente durante l'orario di ufficio di picco. Il **attese Query** pagina sarà la risorsa principale per determinare se i set di dati hanno tempi di attesa elevato Media della query.
- Un numero elevato di utenti simultanei capacità (centinaia di migliaia) utilizzano il report o set di dati stesso. I set di dati anche ben progettata può eseguire in modo errato oltre una soglia di concorrenza. Ciò in genere viene indicato con un singolo set di dati che mostra un valore notevolmente superiore per il conteggio di query rispetto a Mostra altri set di dati (ad esempio 300 KB esegue una query per un set di dati rispetto a < 30 KB query per tutti gli altri set di dati). A un certo punto la query è in attesa per questo set di dati verrà avviata in modo da scaglionare e questo verrà visualizzato nei **durate delle Query** visual.
- Molti diversi set di dati sottoposti a query contemporaneamente, provocando thrashing come frequente del ciclo di set di dati da e verso memoria. Di conseguenza gli utenti riscontra prestazioni rallentate quando il set di dati vengono caricati in memoria. Per risolvere il problema, l'amministratore di Power BI può fare riferimento al **eliminazioni di set di dati orarie e il consumo di memoria** visual, che potrebbe indicare che un numero elevato di set di dati caricati in memoria sono in corso rimosso ripetutamente.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificazione delle cause per sporadicamente rallentare rispondono i set di dati

In questo scenario, è stata attivata un'indagine quando gli utenti descritto report oggetti visivi in alcuni casi hanno avvertiti lente nel rispondere o potrebbe non rispondere, ma in altri momenti erano siano accettabili reattive.

All'interno dell'app, il **durate delle Query** sezione è stata usata per trovare il set di dati causa del problema nel modo seguente:

- Nel **durate delle Query** visual l'amministratore filtrato set di dati dal set di dati (a partire i primi set di dati sottoposti a query) ed esaminare le barre filtrate cross-i **oraria Query distribuzioni** visual.
- Quando una singola barra un'ora ha illustrato le modifiche significative del rapporto tra tutti i gruppi di durata delle query e altre barre di un'ora per set di dati (ad esempio i rapporti tra i colori cambia drasticamente), significa che questo set di dati illustrato una modifica sporadica in Prestazione.
- Le barre di un'ora che mostra una parte irregolare delle query con prestazioni ridotte, indicato un intervallo di tempo in cui tale set di dati sia stato influenzato da un effetto di noisy neighbor, provocato da attività degli altri set di dati.

L'immagine seguente mostra un'ora il 30 gennaio, in cui si è verificato un ostacolo significativo delle prestazioni di un set di dati, indicato dalla dimensione della finestra di "(3,10s]"durata bucket di esecuzione. Facendo clic sulla barra di un'ora, vengono visualizzati tutti i set di dati caricati in memoria durante tale periodo, pertanto esponendo il candidato colpevole i set di dati che causa l'effetto influiscono negativamente sulle prestazioni.

![Indicatore da una parte significativa delle prestazioni peggiori](media/whitepaper-premium-deployment/worst-performing-queries.png)

Una volta identificato un oggetto timespan problematico (ad esempio durante il 30 gennaio nell'immagine precedente) all'amministratore di Power BI può rimuovere tutti i filtri di set di dati, quindi filtra solo per tale intervallo di tempo per determinare quali set di dati in modo attivo sono state eseguite query durante questo periodo. Set di dati per l'effetto di noisy neighbor causa del problema è in genere il set di dati sottoposti a query top o quella con la durata più lunga Media della query.

Una soluzione a questo problema potrebbe essere la causa del problema sono supportati i set di dati in diverse aree di lavoro in capacità Premium differenti o in capacità condivisa se le dimensioni del set di dati, i requisiti di consumo e l'aggiornamento dati modelli di distribuzione.

Potrebbe essere true anche il contrario. L'amministratore di Power BI è stato possibile identificare volte quando migliora drasticamente le prestazioni delle query un set di dati e quindi cercare ciò che non viene più visualizzata. Se non sono presente in tale punto determinate informazioni, che può essere utile in modo che punti al problema che provocano.

### <a name="determining-whether-there-is-enough-memory"></a>Determinazione se vi è memoria sufficiente

Per determinare se è disponibile memoria sufficiente per la capacità di completare i carichi di lavoro, l'amministratore di Power BI può fare riferimento al **percentuali di memoria utilizzata** visivo nel **i set di dati** scheda dell'app. **Tutti i** memoria (totale) rappresenta la memoria utilizzata dal set di dati caricati in memoria, indipendentemente dal fatto che vengono attivamente sottoposti a query o elaborazione. **Attiva** memoria rappresenta la memoria utilizzata dal set di dati che vengono attivamente elaborati.

In una capacità integro avrà un aspetto dell'oggetto visivo come questa, che mostra un gap tra tutti i (totale) e memoria attiva:

![Una capacità integro mostrerà un gap tra tutti i (totale) e di memoria attive](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

In una capacità riscontrando un utilizzo elevato della memoria, l'oggetto visivo stesso mostrerà chiaramente memoria attiva e la memoria totale convergenti, vale a dire che è Impossibile caricare set di dati aggiuntivi in memoria a quel punto nel tempo. In questo caso, l'amministratore di Power BI può scegliere **capacità riavviare** (nella **opzioni avanzate** dell'area di impostazioni di capacità del portale di amministrazione). Riavviare i risultati di capacità in tutti i set di dati viene scaricata dalla memoria e consentendo loro di ricaricare in memoria come richiesto (dalla query o aggiornamento dati).

![* * Attiva * * memoria convergente con * * memoria All * *](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Determinazione se vi è sufficientemente CPU

In generale, l'utilizzo medio della CPU di una capacità deve rimanere sotto dell'80%. Che superano questo valore indica che la capacità sta per raggiungere la saturazione della CPU.

Effetti della saturazione della CPU sono espresse dalle operazioni richiede più tempo del previsto a causa della capacità di esecuzione di numerosi cambi di contesto della CPU quando tenta di elaborare tutte le operazioni. In una capacità Premium con un numero elevato di query simultanee indicato dalle query elevati tempi di attesa. Una conseguenza di tempi di attesa di query elevati è più lento della velocità di risposta superiori al consueto. L'amministratore di Power BI è possibile identificare facilmente quando la CPU è satura visualizzando il **oraria distribuzioni di tempo di attesa Query** visual. I picchi periodici di query di attesa conteggi indicano potenziali saturazione della CPU.

![I picchi periodici di query di attesa conteggi indicano potenziali saturazione della CPU](media/whitepaper-premium-deployment/peak-query-wait-times.png)

Un modello simile in alcuni casi può essere rilevato in operazioni in background se cui contribuiscono alla saturazione della CPU. Un amministratore di Power BI può cercare un picco periodico nei tempi di aggiornamento per un set di dati specifico, che può indicare la saturazione della CPU al momento (probabilmente a causa di un altro set di dati in corso aggiornamenti e/o query interattive). In questa istanza, che fa riferimento per la **sistema** visualizzazione dell'app potrebbe non necessariamente rivela che la CPU è al 100%. Il **sistema** consente di visualizzare le medie oraria, ma la CPU può diventare saturo per diversi minuti di pesanti operazioni, che viene visualizzato come picchi in tempi di attesa.

Sono disponibili ulteriori dettagli per visualizzare l'effetto della saturazione della CPU. Mentre il numero di query in attesa è importante, il tempo di attesa di query verrà sempre eseguito in una certa misura senza causare una riduzione delle prestazioni percepibile. Alcuni set di dati (con più lunga medio fase di query, che indica la complessità o dimensioni) sono più soggette agli effetti della saturazione della CPU rispetto ad altri. Per identificare facilmente tali set di dati, l'amministratore di Power BI può cercare le modifiche nella composizione colore delle barre nel **oraria distribuzione tempo di attesa** visual. Dopo l'individuazione di una barra degli outlier, possono cercare i set di dati con query attese durante tale periodo e anche esaminare confrontato per query con durata media per il tempo di attesa media della query. Quando queste due metriche sono di grandezza e il carico di lavoro di query del set di dati è non semplice, è probabile che il set di dati è stata interessata da CPU insufficiente.

Questo effetto può essere particolarmente evidente quando un set di dati vengono utilizzati in brevi picchi di query ad alta frequenza da più utenti (ad esempio in una sessione di formazione), causando la saturazione della CPU durante ogni burst. In questo caso, i tempi di attesa query significativi in questo set di dati possono essere provati, nonché conseguenze su altri set di dati della capacità (effetto influiscono negativamente sulle prestazioni).

In alcuni casi, gli amministratori di Power BI possono richiedere che i proprietari del set di dati crei un minore carico di lavoro di query volatili tramite la creazione di un dashboard (Aggiorna le query che periodicamente con qualsiasi set di dati per i riquadri memorizzato nella cache) invece di un report. Si possono aiutare a evitare i picchi quando viene caricato il dashboard. Questa soluzione potrebbe non essere sempre possibile per determinati requisiti di business, tuttavia può essere un metodo efficace per evitare la saturazione della CPU, senza apportare la modifica al set di dati.

## <a name="conclusion"></a>Conclusioni

Power BI Premium offre prestazioni più coerenti, supporto per volumi di dati di grandi dimensioni e la flessibilità di una piattaforma di Business Intelligence self-service ed enterprise unificata per tutti gli utenti nell'organizzazione. Questo white paper tecnico di livello 300 è stata scritta in modo specifico per gli amministratori di Power BI e gli autori di contenuti e i server di pubblicazione. L'obiettivo per aiutarli a comprendere il potenziale di Power BI Premium e per spiegare come progettare, distribuire, monitorare e risolvere i problemi di soluzioni scalabili.

Per distribuire e gestire le capacità di Power BI Premium, gli amministratori e sviluppatori di modelli richiede una buona conoscenza di come funzione di capacità, come possono essere gestiti e monitorati e come i modelli di ottimizzare, per rispondere in modo appropriato alla problemi di prestazioni e i colli di bottiglia che dovessero verificarsi.

## <a name="end-notes"></a>Note di fine

<a name="endnote-01"></a>\[1\] questa tecnica si occupa di Power BI Premium è supportato solo dal servizio cloud Power BI e in modo che il Server di Report di Power BI non è nell'ambito, ad eccezione di stato che la licenza necessarie per installare il Server di Report di Power BI viene fornito con alcuni Power BI Premium SKU.

<a name="endnote-02"></a>\[2\] power BI come un servizio cloud quando viene usato per incorporare il contenuto per conto degli utenti dell'applicazione è Platform-as-a-Service (PaaS). Questo tipo di incorporamento, può essere ottenuto con due prodotti diversi, uno dei quali è Power BI Premium.

<a name="endnote-03"></a>\[3\] push, streaming e set di dati ibridi non sono archiviate nella capacità Premium e non vengono presi in considerazione durante la distribuzione, la gestione e monitoraggio le capacità Premium.

<a name="endnote-04"></a>\[4\] cartelle di lavoro di Excel come un tipo di contenuto di Power BI non vengono archiviati nella capacità Premium e non vengono presi in considerazione quando si distribuisce, la gestione o monitoraggio le capacità Premium.

<a name="endnote-05"></a>\[5\] gli oggetti visivi possono essere configurati per ignorare le interazioni di filtro dei dati. Per altre informazioni, vedere la [interazioni tra le visualizzazioni in un report di Power BI](service-reports-visual-interactions.md) documento.

<a name="endnote-06"></a>\[6\] differenza nella dimensione può essere determinata confrontando la dimensione del file di Power BI Desktop con la memoria di Gestione attività usando per il file.

<a name="endnote-07"></a>\[7\] supporto per origini dati di Microsoft includono SQL Server, Azure Databricks, Azure HDInsight Spark (Beta), Database SQL di Azure e Azure SQL Data Warehouse. Per informazioni sulle origini aggiuntive, vedere la [origini dati supportate da DirectQuery in Power BI](desktop-directquery-data-sources.md) documento.

<a name="endnote-08"></a>\[8\] power BI Premium supporta il caricamento di un file di Power BI Desktop (pbix) con un massimo di 10 GB di dimensioni. Una volta caricato, un set di dati possono aumentare fino a 12 GB di dimensioni come risultato di aggiornamento. Dimensioni massime di caricamento varia a seconda dello SKU. Per altre informazioni, vedere la [supporto di Power BI Premium per grandi set di dati](service-premium-large-datasets.md) documento.

<a name="endnote-09"></a>\[9\] SKU con meno di quattro memorie centrali virtuali non vengono eseguiti in un'infrastruttura dedicata. Ciò include EM1, EM2, A1 e A2 SKU.

<a name="endnote-10"></a>\[10\] Sebbene accada raramente, i modelli possono essere scaricati dalla memoria a causa di operazioni del servizio.

<a name="endnote-11"></a>\[11\] questi intervalli di tempo sono soggetti a modifiche in qualsiasi momento.

<a name="endnote-12"></a>\[12\] questa è definita più aree geografiche, attualmente in anteprima. Viene usata in genere la base logica per una distribuzione multi-geo Capabilities aziendali o conformità per enti pubblici, piuttosto che le prestazioni e scalabilità. Il caricamento del dashboard e report comporta comunque richieste per l'area iniziale per i metadati. Per altre informazioni, vedere la [supporto tecnico di Multi-Geo Capabilities per Power BI Premium (anteprima)](service-admin-premium-multi-geo.md) documento.

<a name="endnote-13"></a>\[13\] è possibile che gli utenti possono causare problemi di prestazioni per l'overload del servizio Power BI con i processi, la scrittura di query troppo complessa, la creazione di riferimenti circolari e così via.

<a name="endnote-14"></a>\[14\] non è consigliabile l'opzione per assegnare le aree di lavoro dell'intera organizzazione, ed è preferito un approccio più mirato. In genere, non è consigliabile usare le aree di lavoro personale per il contenuto di produzione.

<a name="endnote-15"></a>\[15\] è possibile monitorare SKU nell'app o nel portale di Azure, ma non nel portale di amministrazione di Power BI. Per monitorare lo SKU, aggiornamento del report non riuscirà se l'app non è stato aggiunto al ruolo di lettore della risorsa. Per altre informazioni, vedere la [le capacità di monitoraggio di Power BI Premium e Power BI Embedded](service-admin-premium-monitor-capacity.md) documento.

<a name="endnote-16"></a>\[16\] possono attendere gli aggiornamenti quando non è sufficiente CPU o memoria per iniziare.

<a name="endnote-17"></a>\[17\] la dimensione del set di dati in memoria può essere maggiore della dimensione su disco fino al 20%.

<a name="endnote-18"></a>\[18\] medio di utilizzo della memoria (GB) e il consumo di memoria massima (GB)

<a name="endnote-19"></a>\[19\] eliminazioni di set di dati

<a name="endnote-20"></a>\[20\] attesa di query di set di dati, durata Query di set di dati Media (ms), set di dati di conteggio e tempo medio di set di dati di attesa (ms)

<a name="endnote-21"></a>\[21\] conteggio di utilizzo elevato della CPU e il tempo di CPU di massimo utilizzo (ultimi sette giorni)

<a name="endnote-22"></a>\[22\] DQ/LC conteggio di utilizzo elevato e l'ora DQ/LC di massimo utilizzo (ultimi sette giorni)