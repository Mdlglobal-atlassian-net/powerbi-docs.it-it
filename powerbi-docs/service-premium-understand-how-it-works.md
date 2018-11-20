---
title: Ottimizzazione e uso della memoria della capacità Power BI Premium
description: Informazioni sull'ottimizzazione e la gestione della memoria della capacità Power BI Premium.
ms.date: 10/18/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: mblythe
ms.reviewer: mblythe
author: mgblythe
manager: kfile
ms.openlocfilehash: 534c06c66d561a04dbffc04412095d6924c92781
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51266071"
---
# <a name="microsoft-power-bi-premium-capacity-resource-management-and-optimization"></a>Ottimizzazione e gestione delle risorse della capacità Microsoft Power BI Premium

Questo articolo descrive le modalità di gestione delle risorse in Power BI Premium e offre esempi e suggerimenti per la risoluzione dei problemi. Per una panoramica, vedere [Che cos'è Power BI Premium?](service-premium.md).

## <a name="premium-capacity-memory-management"></a>Gestione della memoria della capacità Premium

 La memoria della capacità Premium è usata da:

* I set di dati caricati in memoria
* Gli aggiornamenti dei set di dati (pianificati e su richiesta)
* I carichi di lavoro supportati dalla capacità
* Le query dei report

Quando viene eseguita una richiesta su un set di dati pubblicato nella capacità, il set di dati viene caricato in memoria dall'archivio permanente, un'operazione anche detta caricamento dell'immagine. Mantenere il set di dati caricato in memoria favorisce la risposta veloce alle future query su di esso. Alla memoria necessaria per mantenere il set di dati caricato in memoria occorre aggiungere quella usata dalle query dei report e dagli aggiornamenti del set di dati.

### <a name="dataset-memory-estimation"></a>Stima della memoria per il set di dati

Quando si tenta di caricare un set di dati in memoria, Power BI stima la quantità di memoria necessaria al set di dati per completare il comando richiesto. I set di dati in memoria tendono a essere di dimensioni maggiori rispetto a quando sono salvati su disco. Durante l'aggiornamento di un set di dati, Power BI richiede una quantità di memoria almeno doppia rispetto a quella necessaria quando il set di dati è inattivo.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Overcommit della capacità, rimozione e ricaricamento dei set di dati

Power BI Premium offre la possibilità di eseguire l'*overcommit* della capacità. Ad esempio, è possibile pubblicare più set di dati di quanti la capacità possa contenerne. Se i set di dati pubblicati richiedono una quantità di memoria superiore a quella disponibile nella capacità, alcuni set di dati vengono archiviati separatamente nell'archivio permanente. L'archivio permanente è parte dei 100 TB di spazio di archiviazione associato a ogni capacità.

Dunque, quali set di dati restano in memoria e cosa accade agli altri? Come descritto in precedenza, quando viene eseguita una richiesta su un set di dati, questo viene caricato in memoria (caricamento dell'immagine). La richiesta può essere una query di report o un'operazione di aggiornamento. Ma poiché è possibile eseguire l'overcommit della capacità, può verificarsi una situazione di utilizzo elevato di memoria. In questi casi, il nodo *rimuove* uno o più set di dati dalla memoria. I set di dati inattivi (senza operazioni di query/aggiornamento in esecuzione) vengono rimossi per primi. Poi l'ordine di rimozione si basa sul principio LRU ("utilizzati meno di recente"). Se vengono eseguiti nuovi comandi sul set di dati rimosso, il servizio tenta di ricaricarlo in memoria, potenzialmente rimuovendo altri set di dati. Questo comportamento consente un utilizzo più efficiente, permettendo alla capacità di gestire molti più set di dati rispetto a quanto la memoria possa contenere.

Il caricamento di un set di dati in memoria è un'operazione piuttosto costosa. In base alle dimensioni del set di dati, può durare da pochi secondi per i set di dati di piccole dimensioni a decine di secondi o persino minuti per quelli di circa 10 GB. La capacità Premium tenta di ridurre al minimo il numero di volte in cui sarà necessario caricare la capacità, mantenendo in memoria i set di dati usati più di recente per il maggior tempo possibile. Quando è necessaria memoria aggiuntiva, alcuni set di dati dovranno essere rimossi e il sistema tenterà di scegliere quello con l'impatto minore sull'esperienza utente. Quando è necessaria memoria aggiuntiva, alcuni set di dati dovranno essere rimossi e il sistema tenterà di scegliere quello con l'impatto minore sull'esperienza utente. Ad esempio, il sistema eviterà di rimuovere set di dati usati attivamente negli ultimi minuti. È probabile che presto verranno di nuovo eseguite query su questi set di dati.

Il processo di rimozione di per sé è un'operazione rapida. Se il set di dati non è in uso attivo al momento della rimozione, l'impatto sull'utente sarà ridotto. Tuttavia, se un numero eccessivo di set di dati è in uso attivo nello stesso momento e non vi è memoria sufficiente per contenerli tutti, possono verificarsi molte rimozioni. Troppi set di dati attivi possono determinare una situazione di "thrashing" in cui set di dati vengono costantemente rimossi e ricaricati e gli utenti potrebbero riscontrare un calo evidente in termini di tempi di risposta e prestazioni.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Requisiti di memoria per l'aggiornamento di un set di dati in competizione con i requisiti di memoria per un set di dati attivo

I set di dati possono essere aggiornati in base a una pianificazione o su richiesta. Come descritto in precedenza, la memoria necessaria per gli aggiornamenti completi è almeno doppia rispetto alle dimensioni della memoria dei set di dati caricati e inattivi. Prima dell'avvio dell'aggiornamento, vengono stimati i requisiti di memoria per l'operazione. Se il requisito di memoria totale è superiore alla memoria disponibile nella capacità, alcuni set di dati vengono rimossi. Anche in questo caso, la rimozione si basa sul principio LRU.

Se la memoria necessaria non è disponibile nonostante la rimozione, l'aggiornamento viene accodato per la ripetizione del tentativo. Il servizio riprova finché l'operazione non ha esito positivo o finché non viene avviata una nuova azione di aggiornamento.

Se viene eseguita una query interattiva su qualsiasi set di dati della capacità e non è disponibile memoria sufficiente a causa di un aggiornamento in corso, la richiesta ha esito negativo e l'utente deve eseguire un nuovo tentativo.

### <a name="workloads"></a>Carichi di lavoro

Per impostazione predefinita, le capacità per **Power BI Premium** e **Power BI Embedded** supportano solo il carico di lavoro associato all'esecuzione di query di Power BI nel cloud. È ora disponibile il supporto in anteprima per due carichi di lavoro aggiuntivi: **Report impaginati** e **Flussi di dati**. Se abilitati, questi carichi di lavoro possono influire sull'utilizzo della memoria nella capacità. Per altre informazioni, vedere [Configurare i carichi di lavoro](service-admin-premium-manage.md#configure-workloads).

## <a name="cpu-resource-management-in-premium-capacity"></a>Gestione delle risorse CPU nella capacità Premium

I principali consumer di risorse CPU sono due:

* Query dei report
* Aggiornamenti (elaborazione)

### <a name="queries-from-reports"></a>Query dei report

Le query dei report consumano le risorse della CPU nella capacità. Report con query inefficienti o molti utenti simultanei possono consumare molte risorse della CPU. La capacità esistente potrebbe non essere sufficiente per gestire il carico.

### <a name="refresh-parallelization-policy"></a>Criteri di parallelizzazione degli aggiornamenti

La memoria non è l'unica risorsa che può incidere sull'aggiornamento dei set di dati. Il numero di vCore in un server può rappresentare un ulteriore fattore. Poiché ogni operazione di aggiornamento richiede un certo numero di vCore, è previsto un limite rispetto al numero di aggiornamenti eseguibili in parallelo. Il limite per SKU è descritto in dettaglio nella tabella seguente. Gli aggiornamenti aggiuntivi rispetto a questi limiti vengono accodati.

 | SKU | vCore back-end | Parallelismo di aggiornamento dei modelli |
 | --- | --- | --- |
 | A1  | 0,5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0,5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Se gli aggiornamenti subiscono ritardi, controllare il numero di aggiornamenti paralleli supportati dalla capacità.

## <a name="example-scenarios"></a>Scenari di esempio

Di seguito sono descritti alcuni scenari comuni e le azioni eseguite dal servizio:

**Invio simultaneo di venti aggiornamenti pianificati**. Power BI prova ad avviare i primi *x* aggiornamenti contemporaneamente. Il valore di *x* è determinato dai criteri di parallelizzazione degli aggiornamenti per lo SKU. Se Power BI non riesce a ottenere memoria sufficiente rimuovendo i set di dati inattivi (set di dati non utilizzati di recente), non tutti gli *x* aggiornamenti verranno avviati nello stesso momento. Gli aggiornamenti che non è possibile avviare vengono accodati fino al momento in cui diventa possibile.

**Esecuzione simultanea di due aggiornamenti e memoria sufficiente per il completamento di uno solo di essi**. Viene avviato l'aggiornamento che è possibile completare. L'altro viene ritentato in un secondo momento.

**Esecuzione di query su un numero elevato di set di dati durante l'aggiornamento di diversi set di dati**. Se non è disponibile memoria sufficiente, Power BI prova a interrompere gli aggiornamenti attivi per dare priorità alle query interattive. Questo riduce le prestazioni di aggiornamento.

**L'aggiornamento di un set di dati richiede più memoria di quella disponibile nella capacità corrente**. L'aggiornamento ha esito negativo. Non vengono eseguiti tentativi per ottenere più memoria mediante la rimozione.

**Aggiornamento di un singolo set di dati con un notevole picco di memoria**. Se il picco è superiore alla quantità di memoria che può essere ottenuta tramite la rimozione dei set di dati inattivi, l'aggiornamento viene ritentato in un secondo momento finché non è disponibile memoria sufficiente per gestire il picco.

**Esecuzione di query su un set di dati per cui non è possibile ottenere memoria sufficiente mediante la rimozione di tutti i set di dati inattivi e degli aggiornamenti** . Queste query hanno esito negativo. Per questi tipi di requisiti del carico di lavoro occorre acquistare una capacità superiore.

## <a name="troubleshooting-and-testing"></a>Risoluzione dei problemi e test

Se i report sono lenti o non rispondono, iniziare testando un solo utente nel report. Iniziare quindi ad aumentare il carico di utenti simultanei per individuare il limite. In molti casi, l'ottimizzazione delle query DAX può cambiare in modo significativo le prestazioni dei report. L'ottimizzazione delle query aumenta anche il numero di utenti simultanei supportato dalla capacità. [Monitorare la capacità](service-admin-premium-monitor-capacity.md) per identificare potenziali problemi di prestazioni.

Usare la capacità Power BI Embedded in Azure per testare SKU diversi e determinare lo SKU Premium migliore per il carico di lavoro previsto. Lo SKU A4 di Power BI Embedded equivale a P1, A5 equivale a P2 e A6 equivale a P3. In Azure, è possibile passare facilmente tra gli SKU aumentando o riducendo le prestazioni nel portale di Azure. Una volta individuato lo SKU più adatto per il carico di lavoro e completati i test, è possibile eliminare lo SKU.

In alcuni casi, l'apertura di un file Power BI Desktop (con estensione pbix) del modello disponibile nel computer e la verifica del consumo di memoria e CPU offrono molte indicazioni sul problema. L'operazione non è di aiuto per i modelli molto grandi, ma per alcuni modelli più piccoli, provare ad aprire, aggiornare ed eseguire query sul modello dal computer. Controllare le dimensioni del modello, la memoria e la CPU usata quando si apre il modello. Provare ad aggiornare e ad eseguire query. Usare Gestione attività per verificare il consumo di CPU e memoria per il file locale. A volte queste metriche nel computer stesso possono indicare che una capacità Premium inferiore, ad esempio P1/P2, potrebbe non essere idonea per la soluzione.

## <a name="next-steps"></a>Passaggi successivi

[Gestire capacità all'interno di Power BI Premium e Power BI Embedded](service-admin-premium-manage.md)