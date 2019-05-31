---
title: Gestire le capacità di Microsoft Power BI Premium
description: Descrive le attività di gestione per le capacità di Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565237"
---
# <a name="managing-premium-capacities"></a>La gestione delle capacità Premium

La gestione di Power BI Premium comporta la creazione, gestione e monitoraggio le capacità Premium.

## <a name="creating-and-managing-capacities"></a>Creazione e la gestione delle capacità

Il **delle impostazioni di capacità** pagina del portale di amministrazione di Power BI Visualizza il numero di memorie centrali virtuali acquistate e le capacità Premium disponibile. La pagina consente agli amministratori globali di Office 365 o amministratori del servizio Power BI per creare le capacità Premium da v-core disponibili o per modificare le capacità Premium esistente.

Quando si crea una capacità Premium, gli amministratori devono definire:

- Nome della capacità (univoco all'interno del tenant).
- Amministratori della capacità.
- Dimensioni della capacità.
- Area di residenza dei dati.

Deve essere assegnato almeno un amministratore della capacità. Gli utenti assegnati come amministratori della capacità possono:

- Assegnare le aree di lavoro alla capacità.
- Gestire le autorizzazioni utente, per aggiungere altri amministratori della capacità o gli utenti con autorizzazioni di assegnazione (per consentire loro di assegnare le aree di lavoro alla capacità).
- Gestire i carichi di lavoro, per configurare l'utilizzo di memoria massima per i report impaginati e i carichi di lavoro di flussi di dati.
- Riavviare la capacità, per reimpostare tutte le operazioni a causa di un sovraccarico del sistema.

Gli amministratori della capacità non possono accedere il contenuto dell'area di lavoro a meno che non assegnato in modo esplicito nelle autorizzazioni dell'area di lavoro. Sono inoltre autorizzati ad accedere a tutte le aree di amministrazione di Power BI (a meno che non assegnato in modo esplicito), ad esempio le metriche di utilizzo, i log di controllo o le impostazioni del tenant. Inoltre, gli amministratori della capacità autorizzazioni insufficienti per creare nuove capacità o aumentare le capacità esistenti. Gli amministratori vengono assegnati in base a una per ogni capacità, assicurando che possono solo visualizzare e gestire le capacità a cui sono assegnate.

Dimensioni della capacità viene selezionata da un elenco di opzioni dello SKU, disponibili che è vincolato dal numero di v-core disponibili nel pool. È possibile creare più capacità disponibili nel pool e che può essere originato da uno o più acquistati SKU. Ad esempio, uno SKU P3 (32 memorie centrali) può essere utilizzati per creare tre capacità: uno P2 (16 v-core) e P1 due (2 x 8 v-core). Miglioramento delle prestazioni e scalabilità possono essere ottenuti tramite la creazione di capacità di dimensioni più piccole, come descritto nel [ottimizzazione della capacità Premium](service-premium-capacity-optimize.md) articolo. L'immagine seguente mostra un'impostazione di esempio per l'organizzazione Contoso costituito da cinque le capacità Premium (3x P1 e 2 x P3) con ogni lavoro per le app che lo contiene e varie aree di lavoro nella capacità condivisa.

![Un'impostazione di esempio per l'organizzazione Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Una capacità Premium può essere assegnata a una regione diversa da quella iniziale del tenant di Power BI, noto come multi-geo Capabilities. Multi-geo Capabilities fornisce controllo amministrativo su quale Data Center in determinate aree geografiche si trova il contenuto di Power BI. Viene usata in genere la base logica per una distribuzione multi-geo Capabilities aziendali o conformità per enti pubblici, piuttosto che le prestazioni e scalabilità. Il caricamento del dashboard e report comporta comunque richieste per l'area iniziale per i metadati. Per altre informazioni, vedere [supporto tecnico di Multi-Geo Capabilities per Power BI Premium](service-admin-premium-multi-geo.md).

Gli amministratori del servizio Power BI e gli amministratori globali di Office 365 possono modificare le capacità Premium. In particolare, gli utenti possono:

- Modificare le dimensioni di capacità per aumentare o ridurre le risorse.
- Aggiungere o rimuovere gli amministratori della capacità.
- Aggiungere o rimuovere utenti che dispongono delle autorizzazioni di assegnazione.
- Aggiungere o rimuovere altri carichi di lavoro.
- Modificare le aree.

Sono necessarie autorizzazioni di assegnazione per assegnare un'area di lavoro a una specifica capacità Premium. Le autorizzazioni possono essere concesse per l'intera organizzazione, utenti specifici o gruppi.

Per impostazione predefinita, le capacità Premium supportano i carichi di lavoro associati all'esecuzione di query di Power BI. Capacità Premium supportano anche altri carichi di lavoro: **Intelligenza artificiale (servizi cognitivi)** , **report impaginati**, e **Dataflows**. Ogni carico di lavoro richiede la configurazione della memoria massima (come percentuale del totale di memoria disponibile) che può essere utilizzata dal carico di lavoro. È importante comprendere che un aumento delle allocazioni di memoria massima comprometta il numero di modelli attivi che può essere ospitato e la velocità effettiva degli aggiornamenti. 

Memoria viene allocata dinamicamente per flussi di dati, ma viene allocata in modo statico per i report impaginati. Il motivo per l'allocazione in modo statico la memoria massima è che i report impaginati eseguiti all'interno di uno spazio protetto indipendente della capacità. Dovrebbe prestare attenzione durante l'impostazione impaginazione report memoria in quanto riduce la memoria disponibile per il caricamento dei modelli. Per altre informazioni, vedere la [impostazioni di memoria predefinite](service-admin-premium-workloads.md#default-memory-settings).

L'eliminazione di una capacità Premium, è possibile e non comportare l'eliminazione delle relative aree di lavoro e il contenuto. Al contrario, lo stato le aree di lavoro assegnati in capacità condivisa. Quando la capacità Premium è stata creata in un'area diversa, l'area di lavoro viene spostato a capacità condivisa dell'area home.

### <a name="assigning-workspaces-to-capacities"></a>Assegnazione di aree di lavoro alla capacità

Le aree di lavoro può essere assegnati a una capacità Premium nel portale di amministrazione di Power BI oppure, per un'area di lavoro, nelle **dell'area di lavoro** riquadro.

Gli amministratori della capacità, così come gli amministratori globali di Office 365 o amministratori del servizio Power BI, possono eseguire bulk assegnare le aree di lavoro nel portale di amministrazione di Power BI. BULK assegnato è possibile applicare a:

- **Le aree di lavoro da parte degli utenti** -tutte le aree di lavoro appartenenti a tali utenti, inclusi le aree di lavoro personale, vengono assegnati alla capacità Premium. Ciò include la riassegnazione delle aree di lavoro quando sono già assegnati a una capacità Premium diversa. Inoltre, gli utenti sono assegnati anche le autorizzazioni di assegnazione dell'area di lavoro.

- **Aree di lavoro specifiche**
- **Le aree di lavoro dell'intera organizzazione** -tutte le aree di lavoro, incluse le aree di lavoro personale, vengono assegnati alla capacità Premium. Tutti gli utenti attuali e futuri vengono assegnati le autorizzazioni di assegnazione dell'area di lavoro. Questo approccio non è consigliato. È preferibile un approccio più mirato.

Un'area di lavoro può essere aggiunti a una capacità Premium tramite il **dell'area di lavoro** riquadro fornendo all'utente sia un amministratore dell'area di lavoro e disponga delle autorizzazioni di assegnazione.

![Utilizzo del riquadro area di lavoro per assegnare un'area di lavoro a una capacità Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Gli amministratori dell'area di lavoro possono rimuovere un'area di lavoro da una capacità (per la capacità condivisa) senza richiedere l'autorizzazione di assegnazione. Rimozione di aree di lavoro dalla capacità dedicata in modo efficace consente di spostare l'area di lavoro alla capacità condivisa. Si noti che la rimozione di un'area di lavoro da una capacità Premium possono avere conseguenze negative causando, ad esempio, il contenuto condiviso diventi non disponibile per Power BI gratuito concesso in licenza agli utenti o la sospensione dell'aggiornamento pianificato quando superano i limiti supportati da capacità condivisa.

Nel servizio Power BI, un'area di lavoro assegnato a una capacità Premium più facilmente identificabile dall'icona a forma di rombo che decora il nome dell'area di lavoro.

![Che identifica un'area di lavoro assegnato a una capacità Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Le capacità di monitoraggio

Monitoraggio le capacità Premium offre agli amministratori una conoscenza del modo in cui eseguono le capacità. Le capacità possono essere monitorate tramite il portale di amministrazione di Power BI o il **le metriche della capacità di Power BI Premium** app (Power BI).

### <a name="power-bi-admin-portal"></a>Portale di amministrazione di Power BI

Nel portale di amministrazione, per ogni capacità, il **integrità** scheda fornisce metriche di riepilogo per ogni carico di lavoro abilitato e la capacità. Le metriche indicano una media negli ultimi sette giorni.  

A livello di capacità, le metriche sono cumulative di tutti i carichi di lavoro abilitati. vengono fornite le metriche seguenti:

- **UTILIZZO della CPU** -fornisce un utilizzo medio della CPU come percentuale della disponibilità totale della CPU per la capacità.  
- **UTILIZZO della memoria** -restituisce la media su un totale di memoria disponibile per la capacità di utilizzo della memoria (in GB). 

Per ogni carico di lavoro abilitato, utilizzo della CPU e utilizzo della memoria viene fornite una serie di metriche di carico di lavoro specifico. Ad esempio, per il carico di lavoro del flusso di dati **totale conteggio** Visualizza il totale viene aggiornata per ogni flusso di dati, e **durata media** Mostra la durata media di aggiornamento per il flusso di dati.

![Capacità di integrità, scheda nel portale](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Per altre informazioni su tutte le metriche disponibili per ogni carico di lavoro, vedere [monitorare le capacità nel portale di amministrazione](service-admin-premium-monitor-portal.md).

Le funzionalità di monitoraggio nel portale di amministrazione di Power BI sono progettate per fornire un breve riepilogo delle metriche di capacità principali. Per informazioni dettagliate di monitoraggio, è consigliabile usare la **le metriche della capacità di Power BI Premium** app.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium app metriche della capacità

Il [le metriche della capacità di Power BI Premium app](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) è disponibile per gli amministratori della capacità di un'app Power BI e viene installato come qualsiasi altra app di Power BI. Contiene un dashboard e report.

![Power BI Premium app metriche della capacità](media/service-premium-capacity-manage/capacity-metrics-app.png)

Quando si apre l'app, viene caricato il dashboard per presentare numerose sezioni esprimere una visualizzazione aggregata in tutte le capacità di cui l'utente è un amministratore della capacità. Il layout del dashboard include cinque aree principali:

- **Panoramica** -versione dell'App, il numero di aree di lavoro e delle capacità
- **Riepilogo sistema** -metriche memoria e CPU
- **Set di dati di riepilogo** : numero di set di dati, DQ/LC, aggiornamento e le metriche di query
- **Riepilogo del flusso di dati** : numero di flussi di dati e le metriche di set di dati
- **Riepilogo Report impaginato** : aggiornare e visualizzare le metriche

Il report sottostante, da cui sono stati aggiunti i riquadri del dashboard, sono accessibili facendo clic su qualsiasi riquadro del dashboard. Fornisce un punto di vista più dettagliata di ognuna delle sezioni del dashboard e supporta l'applicazione di filtri interattiva. 

Il filtro può essere ottenuto impostando i filtri dei dati dall'intervallo di date, capacità, dell'area di lavoro e del carico di lavoro (report, set di dati, flussi di dati), e selezionando gli elementi all'interno di report gli oggetti visivi per filtrare la pagina del report. Filtro incrociato è una tecnica potente per restringere l'elenco a periodi di tempo specifico, le capacità, le aree di lavoro, i set di dati e così via e può essere molto utile quando si esegue l'analisi della causa radice.

Per informazioni dettagliate sulle metriche del dashboard e report nell'app, vedere [le capacità di monitoraggio Premium con l'app](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>L'interpretazione delle metriche

Le metriche devono essere monitorate per stabilire una conoscenza di base delle attività della risorsa di informazioni sull'utilizzo e carico di lavoro. Se la capacità non è più lenta, è importante comprendere le metriche da monitorare e le conclusioni è possibile apportare.

In teoria, le query deve essere completata entro un secondo per offrire esperienze a risposta agli utenti dei report e consentono una velocità effettiva di query. È in genere di preoccupazione minore quando i processi in background - tra cui aggiornamenti - richiedono tempi più lunghi per il completamento.

In generale, report lenta può essere un'indicazione di una capacità in eccesso di riscaldamento. Quando i report non riesce a caricare, questa è un'indicazione di una capacità eccessiva riscaldata. In entrambi i casi, la causa radice potrebbe essere imputabile a numerosi fattori, tra cui:

- **Query non riuscite** certamente indicano un utilizzo elevato della memoria e un modello potrebbe non essere caricati in memoria. Il servizio Power BI verrà effettuato un tentativo di caricare un modello per 30 secondi prima che si verifichi.

- **Tempi di attesa eccessivi query** può essere dovuto a diversi motivi:
  - La necessità per il servizio Power BI prima di tutto rimuovere dei modelli e quindi caricare il modello con query (tenere presente che superiore percentuali di rimozione set di dati da solo non sono un'indicazione di stress di capacità, a meno che non accompagnato da query tempi di attesa lunghi che indicano thrashing di memoria).
  - Modello i tempi di caricamento (in particolare l'attesa per caricare un modello di grandi dimensioni in memoria).
  - Query con esecuzione prolungata.
  - Numero eccessivo di connessioni LC\DQ (superamento dei limiti di capacità).
  - Saturazione della CPU.
  - Report complessi costituiti da progettazioni con un numero eccessivo di oggetti visivi in una pagina (tenere presente che ogni oggetto visivo è una query).

- **Durata query lunghe durate** può indicare che le progettazioni di modello non sono ottimizzate, soprattutto quando sono attivi in una capacità di più set di dati e un solo set di dati produce lunga durate delle query. Ciò suggerisce che la capacità è sufficientemente risorse assegnata e che il set di dati nella domanda è solo lento o non ottimali. Query a esecuzione prolungata può essere problematica perché in grado di bloccare l'accesso alle risorse richieste da altri processi.
- **Aggiornare Long tempi di attesa** indica memoria insufficiente a causa di molti modelli attive che utilizzano memoria, o che sta bloccando un aggiornamento problematico altra viene aggiornata (superamento dei limiti di aggiornamento parallelo).

Viene descritta una spiegazione più dettagliata di come usare le metriche nel [capacità Premium ottimizzazione](service-premium-capacity-optimize.md) articolo.

## <a name="acknowledgements"></a>Riconoscimenti

Questo articolo è stato scritto da Peter Myers, MVP di piattaforma dei dati e indipendenti esperti di Business Intelligence con [bit per bit soluzioni](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Ottimizzazione della capacità Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurare i carichi di lavoro in una capacità Premium](service-admin-premium-workloads.md)   

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

||||||
