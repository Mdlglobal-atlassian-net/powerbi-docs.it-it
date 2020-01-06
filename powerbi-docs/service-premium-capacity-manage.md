---
title: Gestire le capacità di Microsoft Power BI Premium
description: Descrive le attività di gestione per le capacità di Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 2e32a61891cee2fb5e2a80167d5283962dc164bb
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "74697475"
---
# <a name="managing-premium-capacities"></a>Gestire le capacità Premium

La gestione di Power BI Premium comporta la creazione, la gestione e il monitoraggio delle capacità Premium. Questo articolo offre una panoramica delle capacità; per istruzioni dettagliate, vedere [Configurare e gestire le capacità](service-admin-premium-manage.md).

## <a name="creating-and-managing-capacities"></a>Creazione e gestione delle capacità

La pagina **Impostazioni di capacità** del portale di amministrazione di Power BI visualizza il numero di vCore acquistate e le capacità Premium disponibili. La pagina consente agli amministratori globali di Office 365 o agli amministratori del servizio Power BI di creare capacità Premium da vCore disponibili o modificare le capacità Premium esistenti.

Quando si crea una capacità Premium, è necessario che gli amministratori definiscano quanto segue:

- Nome della capacità (univoco all'interno del tenant).
- Amministratori della capacità.
- Dimensioni della capacità.
- Area per la residenza dei dati.

È necessario assegnare almeno un amministratore della capacità. Gli utenti assegnati come amministratori della capacità possono:

- Assegnare le aree di lavoro alla capacità.
- Gestire le autorizzazioni utente per aggiungere amministratori della capacità o utenti aggiuntivi con autorizzazioni di assegnazione (per consentire loro di assegnare le aree di lavoro alla capacità).
- Gestire i carichi di lavoro per configurare l'utilizzo massimo della memoria per i carichi di lavoro di report impaginati e flussi di dati.
- Riavviare la capacità per reimpostare tutte le operazioni in seguito a un overload del sistema.

Gli amministratori della capacità non possono accedere al contenuto dell'area di lavoro, a meno che non vengano assegnati esplicitamente nelle autorizzazioni dell'area di lavoro. Gli amministratori della capacità non hanno accesso a tutte le aree di amministrazione di Power BI (se non assegnati esplicitamente) come ad esempio le metriche di utilizzo, i log di controllo o le impostazioni del tenant. In particolare gli amministratori della capacità non hanno le autorizzazioni per creare nuove capacità o ridimensionare le capacità esistenti. Gli amministratori vengono assegnati in base alla capacità, garantendo in questo modo che possano solo visualizzare e gestire le capacità a cui sono assegnati.

Le dimensioni della capacità vengono selezionate da un elenco disponibile di opzioni SKU che è limitato dal numero di vCore disponibili nel pool. È possibile creare più capacità dal pool, che possono essere originate da uno o più SKU acquistati. Ad esempio, è possibile usare uno SKU P3 (32 vCore) per creare tre capacità: una P2 (16 vCore) e due P1 (2 x 8 vCore). Per ottenere prestazioni e scalabilità migliori, è possibile creare capacità di dimensioni minori, come descritto nell'articolo [Ottimizzazione delle capacità Premium](service-premium-capacity-optimize.md). L'immagine seguente illustra una configurazione di esempio per l'organizzazione fittizia Contoso costituita da cinque capacità Premium (3 x P1 e 2 x P3), ognuna contenente aree di lavoro e diverse aree di lavoro in capacità condivisa.

![Configurazione di esempio per l'organizzazione fittizia Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Una capacità Premium può essere assegnata a un'area diversa dall'area principale del tenant Power BI, chiamata Multi-Geo. La funzionalità Multi-Geo offre un controllo amministrativo sui data center all'interno di aree geografiche definite in cui risiede il contenuto di Power BI. La logica di una distribuzione Multi-Geo è in genere finalizzata alla conformità aziendale o di enti pubblici anziché alle prestazioni e alla scalabilità. Il caricamento di report e dashboard comporta comunque richieste all'area iniziale per i metadati. Per altre informazioni, vedere [Supporto Multi-Geo per Power BI Premium](service-admin-premium-multi-geo.md).

Gli amministratori del servizio Power BI e gli amministratori globali di Office 365 possono modificare le capacità Premium. In particolare, gli amministratori possono:

- Modificare le dimensioni della capacità per aumentare o ridurre le risorse.
- Aggiungere o rimuovere gli amministratori della capacità.
- Aggiungere o rimuovere utenti che dispongono di autorizzazioni di assegnazione.
- Aggiungere o rimuovere carichi di lavoro aggiuntivi.
- Cambiare le aree.

Per assegnare un'area di lavoro a una capacità Premium specifica sono necessarie le autorizzazioni di assegnazione. Le autorizzazioni possono essere concesse all'intera organizzazione, a utenti specifici o a gruppi.

Per impostazione predefinita, le capacità Premium supportano solo i carichi di lavoro associati all'esecuzione di query di Power BI. Le capacità Premium supportano anche carichi di lavoro aggiuntivi: **Intelligenza artificiale (Servizi cognitivi)** , **Report impaginati** e **Flussi di dati**. Per ogni carico di lavoro è necessario configurare la memoria massima (come percentuale della memoria totale disponibile) che può essere usata dal carico di lavoro. È importante tenere presente che l'aumento delle allocazioni di memoria massime può influire sul numero di modelli attivi che possono essere ospitati e sulla velocità effettiva degli aggiornamenti. 

La memoria viene allocata in modo dinamico ai flussi di dati e in modo statico ai report impaginati. Il motivo per l'allocazione statica della memoria massima consiste nel fatto che i report impaginati vengono eseguiti in uno spazio indipendente protetto della capacità. È necessario prestare attenzione quando si imposta la memoria dei report impaginati in quanto riduce la memoria disponibile per il caricamento di modelli. Per altre informazioni, vedere [Impostazioni predefinite della memoria](service-admin-premium-workloads.md#default-memory-settings).

L'eliminazione di una capacità Premium è possibile e non comporta l'eliminazione delle aree di lavoro e del contenuto. Al contrario, le aree di lavoro assegnate vengono spostate nella capacità condivisa. Se la capacità Premium è stata creata in un'area diversa, l'area di lavoro viene spostata nella capacità condivisa dell'area principale.

### <a name="assigning-workspaces-to-capacities"></a>Assegnazione delle aree di lavoro alle capacità

Le aree di lavoro possono essere assegnate a una capacità Premium nel portale di amministrazione di Power BI o, per un'area di lavoro, nel riquadro **Area di lavoro**.

Gli amministratori della capacità, nonché gli amministratori globali di Office 365 o gli amministratori del servizio Power BI, possono assegnare in blocco le aree di lavoro nel portale di amministrazione di Power BI. L'assegnazione in blocco può essere applicata ad:

- **Aree di lavoro in base agli utenti**: tutte le aree di lavoro di proprietà degli utenti, incluse le aree di lavoro personali, vengono assegnate alla capacità Premium. Ciò include la riassegnazione delle aree di lavoro già assegnate a una capacità Premium diversa. Inoltre, agli utenti sono assegnate anche le autorizzazioni di assegnazione dell'area di lavoro.

- **Aree di lavoro specifiche**
- **Aree di lavoro dell'intera organizzazione**: tutte le aree di lavoro, incluse le aree di lavoro personali, vengono assegnate alla capacità Premium. A tutti gli utenti attuali e futuri vengono assegnate le autorizzazioni di assegnazione dell'area di lavoro. Questo approccio non è consigliato. È preferibile un approccio più mirato.

È possibile aggiungere un'area di lavoro a una capacità Premium usando il riquadro **Area di lavoro**, a condizione che l'utente sia un amministratore dell'area di lavoro e abbia le autorizzazioni di assegnazione.

![Uso del riquadro Area di lavoro per assegnare un'area di lavoro a una capacità Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Gli amministratori dell'area di lavoro possono rimuovere un'area di lavoro da una capacità (alla capacità condivisa) senza richiedere l'autorizzazione di assegnazione. La rimozione di aree di lavoro da capacità dedicate consente di rilocare l'area di lavoro nella capacità condivisa. Si noti che la rimozione di un'area di lavoro da una capacità Premium può avere conseguenze negative. È possibile ad esempio che il contenuto condiviso non sia disponibile per gli utenti con licenza gratuita di Power BI o che l'aggiornamento pianificato venga sospeso quando vengono superati i limiti supportati dalle capacità condivise.

Nel servizio Power BI un'area di lavoro assegnata a una capacità Premium è facilmente identificabile dall'icona a rombo nel nome dell'area di lavoro.

![Identificazione di un'area di lavoro assegnata a una capacità Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Capacità di monitoraggio

Il monitoraggio delle capacità Premium consente agli amministratori di verificare le prestazioni delle capacità. È possibile monitorare le capacità usando il portale di amministrazione di Power BI o l'app **Power BI Premium Capacity Metrics**.

### <a name="power-bi-admin-portal"></a>Portale di amministrazione di Power BI

Nel portale di amministrazione la scheda **Integrità** di ogni capacità visualizza le metriche di riepilogo per la capacità e ogni carico di lavoro abilitato. Le metriche mostrano una media degli ultimi sette giorni.  

A livello di capacità, le metriche sono cumulative di tutti i carichi di lavoro abilitati. Sono disponibili le metriche seguenti:

- **UTILIZZO CPU**: visualizza l'utilizzo medio della CPU come percentuale della CPU totale disponibile per la capacità.  
- **UTILIZZO MEMORIA**: visualizza l'utilizzo medio della memoria (in GB) come totale della memoria disponibile per la capacità. 

Per ogni carico di lavoro abilitato, vengono visualizzati l'utilizzo della CPU e l'utilizzo della memoria, oltre a una serie di metriche specifiche del carico di lavoro. Ad esempio, per il carico di lavoro Flusso di dati, **Conteggio totale** visualizza il totale degli aggiornamenti per ogni flusso di dati e **Durata media** visualizza la durata media dell'aggiornamento per il flusso di dati.

![Scheda Integrità della capacità nel portale](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Per altre informazioni su tutte le metriche disponibili per ogni carico di lavoro, vedere [Monitorare le capacità nel portale di amministrazione](service-admin-premium-monitor-portal.md).

Le funzionalità di monitoraggio nel portale di amministrazione di Power BI sono progettate per offrire un breve riepilogo delle metriche chiave della capacità. Per un monitoraggio più dettagliato, è consigliabile usare l'app **Power BI Premium Capacity Metrics**.

### <a name="power-bi-premium-capacity-metrics-app"></a>App Power BI Premium Capacity Metrics

L'app [Power BI Premium Capacity Metrics app](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) è un'app di Power BI disponibile per gli amministratori della capacità e viene installata come tutte le app di Power BI. Contiene un dashboard e un report.

![App Power BI Premium Capacity Metrics](media/service-premium-capacity-manage/capacity-metrics-app.png)

All'apertura dell'app, il dashboard viene caricato nei numerosi riquadri presenti offrendo una visualizzazione aggregazioni per tutte le capacità di cui l'utente è amministratore. Il layout del dashboard include cinque sezioni principali:

- **Overview** (Panoramica): versione dell'app, numero di capacità e aree di lavoro
- **System Summary** (Risorse di sistema): metriche di memoria e CPU
- **Dataset Summary** (Riepilogo set di dati): numero di set di dati, DQ/LC, aggiornamento e metriche delle query
- **Dataflow Summary** (Riepilogo flusso di dati): numero di flussi di dati e metriche del set di dati
- **Paginated Report Summary** (Riepilogo report impaginato): metriche di aggiornamento e visualizzazione

Per accedere al report sottostante da cui sono stati aggiunti i riquadri del dashboard, è possibile fare clic su qualsiasi riquadro del dashboard. Viene visualizzata una prospettiva più dettagliata di ogni sezione del dashboard e sono supportati i filtri interattivi. 

È possibile applicare filtri impostando filtri dei dati per intervallo di date, capacità, area di lavoro e carico di lavoro (report, set di dati, flusso di dati) e selezionando elementi negli oggetti visivi del report per applicare un filtro incrociato alla pagina del report. Il filtro incrociato è una tecnica efficace per limitare i periodi di tempo, le capacità, le aree di lavoro, i set di dati e così via. Può essere molto utile quando si esegue l'analisi della causa radice.

Per informazioni dettagliate sulle metriche del dashboard e del report nell'app, vedere [Monitorare le capacità Premium con l'app](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretazione delle metriche

È necessario monitorare le metriche per acquisire una conoscenza di base dell'utilizzo delle risorse e dell'attività del carico di lavoro. Se la capacità diventa lenta, è importante individuare le metriche da monitorare e le conclusioni che se ne possono trarre.

Per offrire esperienze reattive agli utenti del report e una velocità effettiva delle query più elevata, il completamento delle query dovrebbe richiedere meno di un secondo. Una maggior durata dei processi in background, inclusi gli aggiornamenti, in genere non rappresenta un problema.

In generale, i report lenti possono indicare una capacità con surriscaldamento. Il mancato caricamento dei report può indicare una capacità surriscaldata. In entrambe le situazioni, la causa radice potrebbe essere attribuibile a molti fattori, inclusi i seguenti:

- Le **query non riuscite** indicano sicuramente una pressione della memoria e l'impossibilità di caricare un modello in memoria. Il servizio Power BI tenta di caricare un modello per 30 secondi.

- **Tempi di attesa delle query eccessivi** possono essere dovuti a diverse ragioni:
  - La necessità del servizio Power BI di rimuovere prima i modelli e quindi di caricare il modello su cui eseguire la query (tenere presente che frequenze di rimozione dei set di dati più elevate non sono un'indicazione di stress della capacità, a meno che non siano accompagnati da tempi di attesa delle query lunghi che indicano un thrashing di memoria).
  - Tempi di caricamento del modello (in particolare l'attesa di caricare un modello di grandi dimensioni in memoria).
  - Query a esecuzione prolungata.
  - Numero di connessioni LC\DQ eccessivo (superamento dei limiti della capacità).
  - Saturazione della CPU.
  - Progettazione di report complessi con un numero eccessivo di oggetti visivi in una pagina (tenere presente che ogni oggetto visivo è una query).

- Le **durate delle query prolungate** possono indicare che le progettazioni dei modelli non sono ottimizzate, in particolare quando sono attivi più set di dati in una capacità e un solo set di dati produce durate delle query prolungate. Questo suggerisce che la capacità ha risorse sufficienti e che il set di dati in questione non è ottimale o è semplicemente lento. Le query con esecuzione prolungata possono rappresentare un problema poiché possono bloccare l'accesso alle risorse richieste da altri processi.
- **Tempi di attesa dell'aggiornamento prolungati** indicano una quantità di memoria insufficiente a causa dei numerosi modelli attivi che usano la memoria o che un aggiornamento problematico blocca altri aggiornamenti (superando i limiti di aggiornamento parallelo).

Per una descrizione più dettagliata dell'uso delle metriche, vedere l'articolo [Ottimizzazione delle capacità Premium](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Riconoscimenti

Questo articolo è stato scritto da Peter Myers, Data Platform MVP ed esperto indipendente di business intelligence con [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Ottimizzazione delle capacità Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurare i carichi di lavoro in una capacità Premium](service-admin-premium-workloads.md)   

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

