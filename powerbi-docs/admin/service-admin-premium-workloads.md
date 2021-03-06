---
title: Come configurare i carichi di lavoro in Power BI Premium
description: Informazioni su come configurare i carichi di lavoro in una capacità Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: f76763eba578c05102eda60077f110ba752949bc
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274513"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurare i carichi di lavoro in una capacità Premium

Questo articolo descrive l'abilitazione e la configurazione di carichi di lavoro per le capacità Power BI Premium. Per impostazione predefinita le capacità supportano solo il carico di lavoro associato all'esecuzione delle query di Power BI. È anche possibile abilitare e configurare carichi di lavoro aggiuntivi per **[intelligenza artificiale (Servizi cognitivi)](../transform-model/service-cognitive-services.md)** , **[flussi di dati](../transform-model/service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[report impaginati](../paginated-reports/paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Impostazioni predefinite della memoria

I carichi di lavoro delle query sono ottimizzati e limitati alle risorse determinate dallo SKU di capacità Premium. Le capacità Premium supportano anche carichi di lavoro aggiuntivi che possono usare le risorse della capacità. I valori di memoria predefiniti per questi carichi di lavoro si basano sui nodi di capacità disponibili per lo SKU. Le impostazioni della memoria massima non sono cumulative. La memoria massima specificata viene allocata in modo dinamico per l'intelligenza artificiale e i flussi di dati, ma staticamente viene allocata per i report impaginati.

|                   | EM1 / A1                  | EM2 / A2                  | EM3 / A3                  | P1 / A4                  | P2 / A5                  | P3 / A6                   |
|-------------------|---------------------------|---------------------------|---------------------------|--------------------------|--------------------------|---------------------------|
| AI                | Non supportato               | 40% predefinita; 40% minima  | 20% predefinita; 20% minima  | 20% predefinita; 8% minima  | 20% predefinita; 4% minima  | 20% predefinita; 2% minima   |
| Set di dati          | 100% predefinita; 67% minima | 100% predefinita; 40% minima | 100% predefinita; 20% minima | 100% predefinita; 8% minima | 100% predefinita; 4% minima | 100% predefinita; 2% minima  |
| Flussi di dati         | 40% predefinita; 40% minima  | 24% predefinita; 24% minima  | 20% predefinita; 12% minima  | 20% predefinita; 5% minima  | 20% predefinita; 3% minima  | 20% predefinita; 2% minima   |
| Report impaginati | Non supportato               | Non supportato               | Non supportato               | 20% predefinita; 10% minima | 20% predefinita; 5% minima  | 20% predefinita; 2,5% minima |
|                   |                           |                           |                           |                          |                          |                           |

## <a name="workload-settings"></a>Impostazioni del carico di lavoro

### <a name="ai-preview"></a>Intelligenza artificiale (anteprima)

Il carico di lavoro Intelligenza artificiale consente di usare servizi cognitivi e Machine Learning automatizzato in Power BI. Usare le impostazioni seguenti per controllare il comportamento del carico di lavoro.

| Nome dell'impostazione | Descrizione |
|---------------------------------|----------------------------------------|
| **Memoria massima (%)** | Percentuale massima di memoria disponibile che i processi di intelligenza artificiale possono usare in una capacità. |
| **Consente l'utilizzo da Power BI Desktop** | Questa impostazione è riservata per un uso futuro e non è presente in tutti i tenant. |
| **Consente la creazione di modelli di Machine Learning** | Specifica se gli analisti aziendali possono eseguire il training, nonché convalidare e richiamare i modelli di Machine Learning direttamente in Power BI. Per altre informazioni, vedere [Machine Learning automatizzato in Power BI (anteprima](../transform-model/service-machine-learning-automated.md)). |
| **Abilita parallelismo per le richieste di intelligenza artificiale** | Specifica se le richieste di intelligenza artificiale possono essere eseguite in parallelo. |
|  |  |

### <a name="datasets"></a>Set di dati

Il carico di lavoro Set di dati è abilitato per impostazione predefinita e non può essere disabilitato. Usare le impostazioni seguenti per controllare il comportamento del carico di lavoro. Sotto la tabella sono disponibili altre informazioni sull'utilizzo per alcune impostazioni.

| Nome dell'impostazione | Descrizione |
|---------------------------------|----------------------------------------|
| **Memoria massima (%)** | Percentuale massima di memoria disponibile che i set di dati possono usare in una capacità. |
| **Endpoint XMLA** | Specifica che le connessioni dalle applicazioni client rispettano l'appartenenza al gruppo di sicurezza impostata a livello di area di lavoro e di app. Per altre informazioni, vedere [Connettersi ai set di dati con applicazioni client e strumenti](service-premium-connect-tools.md). |
| **Max Intermediate Row Set Count** (Numero massimo di set di righe intermedie) | Numero massimo di righe intermedie restituite da DirectQuery. Il valore predefinito è 1 milione e l'intervallo consentito è compreso tra 100000 e 2147483647. |
| **Dimensioni massime del set di dati offline (GB)** | Dimensioni massime del set di dati offline in memoria. Si tratta delle dimensioni compresse su disco. Il valore predefinito è 0, che corrisponde al limite massimo definito dallo SKU. L'intervallo consentito è compreso tra 0 e il limite di dimensione della capacità. |
| **Max Result Row Set Count** (Numero massimo di set di righe di risultati) | Numero massimo di righe restituite in una query DAX. Il valore predefinito è -1 (nessun limite) e l'intervallo consentito è compreso tra 100000 e 2147483647. |
| **Limite di memoria query (%)** | Percentuale massima di memoria disponibile nel carico di lavoro che può essere usata per l'esecuzione di una query MDX o DAX. Il valore predefinito è 0, che comporta l'applicazione di un limite di memoria query automatico specifico dello SKU. |
| **Timeout query (secondi)** | Quantità massima di tempo prima del timeout di una query. Il valore predefinito è 3600 secondi (1 ora). Il valore 0 specifica che non è previsto un timeout per le query. |
| **Aggiornamento pagina automatico (anteprima)** | Abilitare/disabilitare l'opzione per consentire alle aree di lavoro Premium di avere report con aggiornamento automatico delle pagine. |
| **Intervallo di aggiornamento minimo** | Se l'aggiornamento automatico delle pagine è abilitato, è l'intervallo minimo consentito per l'intervallo di aggiornamento della pagina. Il valore predefinito è 5 minuti, il minimo consentito è 1 secondo. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Max Intermediate Row Set Count (Numero massimo di set di righe intermedie)

Usare questa impostazione per controllare l'effetto dei report a elevato utilizzo di risorse o progettati in modo non corretto. Quando una query a un set di dati DirectQuery genera un risultato di dimensioni molto grandi dal database di origine, può causare un picco nell'utilizzo della memoria e nell'overhead di elaborazione. Questa situazione può causare un esaurimento quasi completo delle risorse di altri utenti e report. Questa impostazione consente all'amministratore della capacità di regolare il numero di righe che una singola query può recuperare dall'origine dati.

In alternativa, se la capacità può supportare più di un milione di righe per impostazione predefinita e si ha un set di dati di grandi dimensioni, aumentare questa impostazione per recuperare più righe.

Si noti che questa impostazione ha effetto solo sulle query DirectQuery, mentre [Max Result Row Set Count](#max-result-row-set-count) (Numero massimo di set di righe di risultati) ha effetto sulle query DAX.

#### <a name="max-offline-dataset-size"></a>Dimensioni massime del set di dati offline

Usare questa impostazione per impedire agli autori di report di pubblicare un set di dati di grandi dimensioni che potrebbe influire negativamente sulla capacità. Si noti che Power BI non riesce a determinare le dimensioni effettive in memoria finché il set di dati non viene caricato in memoria. È possibile che un set di dati con una dimensione offline inferiore abbia un footprint della memoria maggiore rispetto a un set di dati con una dimensione offline maggiore.

Se un set di dati esistente ha dimensioni superiori a quelle specificate per questa impostazione, il set di dati non viene caricato quando un utente prova ad accedervi. Il caricamento del set di dati può anche non riuscire se è più grande della memoria massima configurata per il carico di lavoro dei set di dati.

Per salvaguardare le prestazioni del sistema, viene applicato un limite fisso aggiuntivo specifico dello SKU per le dimensioni massime del set di dati offline, indipendentemente dal valore configurato. Questo limite fisso non si applica ai set di dati di Power BI ottimizzati per dati di grandi dimensioni. Per altre informazioni, vedere [Modelli di grandi dimensioni in Power BI Premium](service-premium-large-models.md).

|                                           | EM1 / A1 | EM2 / A2 | EM3 / A3 | P1 / A4 | P2 / A5 | P3 / A6 |   
|-------------------------------------------|----------|----------|----------|---------|---------|---------|
| Limite fisso per le dimensioni massime del set di dati offline | 3 GB     | 5 GB     | 6 GB     | 10 GB   | 10 GB   | 10 GB   |
|                                           |          |          |          |         |         |         |

#### <a name="max-result-row-set-count"></a>Max Result Row Set Count (Numero massimo di set di righe di risultati)

Usare questa impostazione per controllare l'effetto dei report a elevato utilizzo di risorse o progettati in modo non corretto. Se questo limite viene raggiunto in una query DAX, un utente del report visualizza l'errore seguente. Dovrà copiare i dettagli dell'errore e contattare un amministratore.

![Non è stato possibile caricare i dati per questo elemento visivo](media/service-admin-premium-workloads/could-not-load-data.png)

Si noti che questa impostazione ha effetto solo sulle query DAX, mentre [Max Intermediate Row Set Count](#max-intermediate-row-set-count) (Numero massimo di set di righe intermedie) ha effetto sulle query DirectQuery.

#### <a name="query-memory-limit"></a>Limite di memoria query

Usare questa impostazione per controllare l'effetto dei report a elevato utilizzo di risorse o progettati in modo non corretto. Alcune query e calcoli possono produrre risultati intermedi che usano una grande quantità di memoria nella capacità. Questa situazione può rallentare molto l'esecuzione di altre query, causare l'eliminazione di altri set di dati dalla capacità e generare errori di memoria insufficiente per altri utenti della capacità.

Questa impostazione si applica a tutte le query DAX e MDX eseguite da report Power BI, da report Analizza in Excel e da altri strumenti che possono connettersi tramite l'endpoint XMLA.

Si noti che le operazioni di aggiornamento dei dati possono eseguire anche query DAX nell'ambito dell'aggiornamento dei riquadri del dashboard e delle cache visive dopo l'aggiornamento dei dati nel set di dati. È anche possibile che a causa di questa impostazione tali query abbiano esito negativo e che di conseguenza l'operazione di aggiornamento dei dati venga visualizzata con uno stato di errore, anche se i dati nel set di dati sono stati aggiornati correttamente.

Il valore predefinito è 0, che comporta l'applicazione del limite di memoria query automatico specifico dello SKU indicato di seguito.

|                              | EM1 / A1 | EM2 / A2 | EM3 / A3 | P1 / A4 | P2 / A5 | P3 / A6 |   
|------------------------------|----------|----------|----------|---------|---------|---------|
| Limite di memoria query automatico | 1 GB     | 2 GB     | 2 GB     | 6 GB    | 6 GB    | 10 GB   |
|                              |          |          |          |         |         |         |

Per salvaguardare le prestazioni del sistema, viene applicato un limite fisso di 10 GB per tutte le query eseguite dai report di Power BI, indipendentemente dal limite di memoria delle query configurato dall'utente. Questo limite fisso non si applica alle query eseguite da strumenti che usano il protocollo Analysis Services (noto anche come XMLA). È opportuno che gli utenti considerino la possibilità di semplificare la query o i calcoli se la query richiede un elevato utilizzo di memoria.

#### <a name="query-timeout"></a>Timeout query

Usare questa impostazione per mantenere un controllo migliore sulle query con esecuzione prolungata, che possono rallentare il caricamento dei report per gli utenti.

Questa impostazione si applica a tutte le query DAX e MDX eseguite da report Power BI, da report Analizza in Excel e da altri strumenti che possono connettersi tramite l'endpoint XMLA.

Si noti che le operazioni di aggiornamento dei dati possono eseguire anche query DAX nell'ambito dell'aggiornamento dei riquadri del dashboard e delle cache visive dopo l'aggiornamento dei dati nel set di dati. È anche possibile che a causa di questa impostazione tali query abbiano esito negativo e che di conseguenza l'operazione di aggiornamento dei dati venga visualizzata con uno stato di errore, anche se i dati nel set di dati sono stati aggiornati correttamente.

Questa impostazione si applica a una singola query e non al tempo necessario per l'esecuzione di tutte le query associate all'aggiornamento di un set di dati o di un report. Si consideri l'esempio seguente:

- L'impostazione **Timeout query** è pari a 1200 (20 minuti).
- Devono essere eseguite cinque query, ognuna delle quali richiede 15 minuti.

Il tempo totale per tutte le query è di 75 minuti, ma il limite dell'impostazione non viene raggiunto perché ogni singola query viene eseguita per meno di 20 minuti.

Si noti che i report di Power BI eseguono l'override di questa impostazione predefinita con un timeout molto più ridotto per ogni query alla capacità. Il timeout per ogni query è in genere di circa tre minuti.

#### <a name="automatic-page-refresh-preview"></a>Aggiornamento pagina automatico (anteprima)

Se l'opzione è abilitata, l'aggiornamento automatico delle pagine consente agli utenti con capacità Premium di aggiornare le pagine del report in base a un intervallo definito per le origini DirectQuery. L'amministratore della capacità può eseguire le operazioni seguenti:

- Abilitare e disabilitare l'aggiornamento automatico delle pagine
- Definire un intervallo di aggiornamento minimo

La figura seguente illustra il punto in cui viene impostato l'intervallo di aggiornamento automatico:

![impostazione dell'amministratore per l'intervallo di aggiornamento automatico](media/service-admin-premium-workloads/automatic-refresh-interval.png)

Le query create dall'aggiornamento automatico delle pagine vengono indirizzate direttamente all'origine dati. È quindi importante considerare l'affidabilità e il carico in tali origini quando si consente l'aggiornamento automatico delle pagine all'interno dell'organizzazione. 

### <a name="dataflows"></a>Flussi di dati

Il carico di lavoro Flussi di dati consente di usare la preparazione dei dati self-service con flussi di dati per inserire, trasformare, integrare e arricchire i dati. Usare le impostazioni seguenti per controllare il comportamento del carico di lavoro.

| Nome dell'impostazione | Descrizione |
|---------------------------------|----------------------------------------|
| **Memoria massima (%)** | Percentuale massima di memoria disponibile che i flussi di dati possono usare in una capacità. |
| **Motore di calcolo dei flussi di dati avanzato (anteprima)** | Abilitare questa opzione per ottenere calcoli fino a 20 volte più veloci per le entità calcolate quando si utilizzano volumi di dati su larga scala. **Per attivare il nuovo motore, è necessario riavviare la capacità.** Per altre informazioni, vedere [Motore di calcolo dei flussi di dati avanzato](#enhanced-dataflows-compute-engine). |
| **Dimensioni del contenitore** | Dimensioni massime del contenitore usate dai flussi di dati per ogni entità nel flusso di dati. Il valore predefinito è 700 MB. Per altre informazioni, vedere [Dimensioni del contenitore](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Motore di calcolo dei flussi di dati avanzato

Per trarre vantaggio dal nuovo motore di calcolo, suddividere l'inserimento di dati in flussi di dati distinti e inserire la logica di trasformazione in entità calcolate in flussi di dati diversi. Questo approccio è consigliato perché il motore di calcolo opera sui flussi di dati che fanno riferimento a un flusso di dati esistente. Non funziona sui flussi di dati di inserimento. Seguendo queste linee guida si garantisce che il nuovo motore di calcolo gestisca le fasi di trasformazione, ad esempio join e unioni, per ottenere prestazioni ottimali.

#### <a name="container-size"></a>Dimensioni del contenitore

Quando si aggiorna un flusso di dati, il carico di lavoro Flussi di dati genera un contenitore per ogni entità nel flusso di dati. Ogni contenitore può arrivare a usare una quantità di memoria pari al volume specificato nell'impostazione Dimensioni del contenitore. L'impostazione predefinita per tutti gli SKU è 700 MB. Potrebbe essere necessario modificare questa impostazione se:

- L'aggiornamento dei flussi di dati richiede troppo tempo oppure l'aggiornamento dei flussi di dati non riesce a causa di un timeout.
- Le entità dei flussi di flussi includono passaggi di calcolo, ad esempio un join.  

È consigliabile usare l'app [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) per analizzare le prestazioni del carico di lavoro Flussi di dati.

In alcuni casi, l'aumento delle dimensioni del contenitore potrebbe non migliorare le prestazioni. Se ad esempio il flusso di dati recupera i dati solo da un'origine senza eseguire calcoli significativi, la modifica delle dimensioni del contenitore potrebbe non essere utile. L'aumento delle dimensioni del contenitore può essere utile se consente al carico di lavoro Flussi di dati di allocare ulteriore memoria per le operazioni di aggiornamento delle entità. Con più memoria allocata, è possibile ridurre il tempo necessario per aggiornare le entità a elevato utilizzo di calcoli.

Il valore di Dimensioni contenitore non può superare la quantità massima di memoria per il carico di lavoro Flussi di dati. Una capacità P1, ad esempio, ha 25 GB di memoria. Se la quantità massima di memoria (%) del carico di lavoro Flussi di dati è impostata sul 20%, il valore di Dimensioni del contenitore (MB) non può essere superiore a 5000. In tutti i casi, le dimensioni del contenitore non possono superare la quantità di memoria massima, anche se si imposta un valore superiore.

### <a name="paginated-reports"></a>Report impaginati

Il carico di lavoro Report impaginati consente di eseguire report impaginati, in base al formato di SQL Server Reporting Services standard, nel servizio Power BI. Usare l'impostazione seguente per controllare il comportamento del carico di lavoro.

| Nome dell'impostazione | Descrizione |
|---------------------------------|----------------------------------------|
| **Memoria massima (%)** | Percentuale massima di memoria disponibile che i report impaginati possono usare in una capacità. |
|  |  |

I report impaginati offrono le stesse funzionalità dei report SQL Server Reporting Services (SSRS) attualmente disponibili, inclusa la possibilità per gli autori di report di aggiungere codice personalizzato.  Questo consente agli autori di modificare dinamicamente i report, ad esempio i colori del testo in base alle espressioni di codice.  Per assicurare un isolamento appropriato, i report impaginati vengono eseguiti in una sandbox protetta per capacità. I report eseguiti con la stessa capacità possono causare effetti collaterali reciproci. Per i report impaginati è consigliabile seguire una procedura simile a quella adottata per gli autori che possono pubblicare contenuto in un'istanza di SSRS. Assicurarsi che gli autori che pubblicano contenuto in una capacità siano considerati attendibili dall'organizzazione. È possibile proteggere ulteriormente l'ambiente eseguendo il provisioning di più capacità e assegnando autori diversi a ciascuna di esse. 

In alcuni casi, il carico di lavoro Report impaginati può diventare non disponibile. In questo caso, per il carico di lavoro viene visualizzato uno stato di errore nel portale di amministrazione e gli utenti vedono il timeout per il rendering del report. Per attenuare questo problema, disabilitare il carico di lavoro e quindi riabilitarlo.

## <a name="configure-workloads"></a>Configurare i carichi di lavoro

È possibile ottimizzare le risorse disponibili della capacità abilitando i carichi di lavoro solo se verranno effettivamente usati. Cambiare le impostazioni della memoria e le altre impostazioni solo dopo aver stabilito che le impostazioni predefinite non soddisfano i requisiti relativi alle risorse della capacità.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Per configurare i carichi di lavoro nel portale di amministrazione di Power BI

1. In **Impostazioni di capacità** > **Capacità Premium** selezionare una capacità.

1. In **ALTRE OPZIONI** espandere **Carichi di lavoro**.

1. Abilitare uno o più carichi di lavoro e impostare un valore per **Memoria massima** e le altre impostazioni.

1. Selezionare **Applica**.

### <a name="rest-api"></a>API REST

I carichi di lavoro possono essere abilitati e assegnati a una capacità usando le API REST [Capacità](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitoraggio dei carichi di lavoro

L'[app Metrica per la capacità Power BI Premium](service-admin-premium-monitor-capacity.md) fornisce metriche per set di dati, flussi di dati e report impaginati per monitorare i carichi di lavoro abilitati per le capacità. 


> [!IMPORTANT]
> Se per la capacità Power BI Premium si riscontra un utilizzo elevato delle risorse, con conseguenti problemi di prestazioni o affidabilità, è possibile ricevere messaggi di posta elettronica di notifica per identificare e risolvere il problema. Questo può essere un modo semplificato per risolvere i problemi relativi al sovraccarico di capacità. Per altre informazioni, vedere [Notifiche per capacità e affidabilità](service-interruption-notifications.md#capacity-and-reliability-notifications).


## <a name="next-steps"></a>Passaggi successivi

[Ottimizzazione delle capacità Power BI Premium](service-premium-capacity-optimize.md)[
Preparazione dei dati self-service in Power BI con flusso di dati](../transform-model/service-dataflows-overview.md)
[Che cosa sono i report impaginati in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
[Aggiornamento automatico della pagina in Power BI Desktop (anteprima)](../create-reports/desktop-automatic-page-refresh.md)

Altre domande? [Inviare una domanda alla community di Power BI](https://community.powerbi.com/)
