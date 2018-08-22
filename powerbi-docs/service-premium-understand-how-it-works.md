---
title: Ottimizzazione e uso della memoria della capacità Power BI Premium
description: Informazioni sull'ottimizzazione e la gestione della memoria della capacità Power BI Premium.
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: mblythe
ms.reviewer: mblythe
author: mgblythe
manager: kfile
ms.openlocfilehash: aee7fb94f1e132783fc2b7791f7e634c903f7aa6
ms.sourcegitcommit: 1574ecba7530e6e0ee97235251a3138fb0e4789b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40256863"
---
# <a name="power-bi-premium-capacity-resource-management-and-optimization"></a>Ottimizzazione e gestione delle risorse della capacità Power BI Premium

Questo articolo descrive le modalità di gestione delle risorse nel servizio Power BI Premium e contiene suggerimenti sulla pianificazione e l'ottimizzazione della soluzione.

## <a name="premium-capacity-memory-management"></a>Gestione della memoria della capacità Premium

 La memoria della capacità Premium è usata da:

* Memoria usata dai set di dati caricati
* Memoria usata dagli aggiornamenti dei set di dati (sia pianificati che su richiesta)
* Memoria usata dalle query dei report

Quando viene eseguita una richiesta su un set di dati pubblicato nella capacità, il set di dati viene caricato in memoria dall'archivio permanente, un'operazione anche detta caricamento dell'immagine. Mantenere il set di dati caricato in memoria favorisce la risposta veloce alle future query su di esso. Alla memoria necessaria per mantenere il set di dati caricato in memoria occorre aggiungere quella usata dalle query dei report e dagli aggiornamenti del set di dati.

### <a name="dataset-memory-estimation"></a>Stima della memoria per il set di dati

Quando si tenta di caricare un set di dati in memoria, Power BI stima la quantità di memoria necessaria a quel set di dati per completare il comando richiesto. I set di dati in memoria tendono a essere di dimensioni maggiori rispetto a quando sono salvati su disco. Durante l'aggiornamento di un set di dati, la capacità di memoria richiede una quantità di memoria almeno doppia rispetto a quella necessaria quando il set di dati è inattivo.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Overcommit della capacità, rimozione e ricaricamento dei set di dati

Power BI Premium offre la possibilità di eseguire l'overcommit della capacità. Ad esempio, è possibile pubblicare più set di dati rispetto a quanto la memoria della capacità possa contenere. Se i set di dati pubblicati nella capacità richiedono una memoria superiore alle dimensioni della capacità, alcuni set di dati verranno archiviati separatamente in un archivio permanente. L'archivio permanente è parte dei 100 TB di spazio di archiviazione associati a ogni capacità.

Dunque, quali set di dati restano in memoria e cosa accade agli altri? Come descritto in precedenza, quando viene eseguita una richiesta su un set di dati, questo viene caricato in memoria (caricamento dell'immagine). La richiesta può essere una query di report o un'operazione di aggiornamento.

Poiché è possibile eseguire l'overcommit della capacità, può verificarsi una situazione di utilizzo elevato della memoria. Quando la capacità rileva un utilizzo elevato della memoria (perché è necessario caricare un nuovo set di dati o perché le query eseguite su alcuni set di dati caricati aumentano i requisiti di memoria), il nodo *rimuove uno o più set di dati* che occupano la memoria della capacità. I set di dati inattivi, ovvero sui quali non sono attualmente in esecuzione operazioni di aggiornamento o query, vengono rimossi per primi e l'ordine di rimozione è secondo la modalità "utilizzati meno di recente (LRU)". Se vengono eseguiti nuovi comandi sul set di dati rimosso, il servizio tenta di ricaricarlo in memoria, potenzialmente rimuovendo altri set di dati. Questo comportamento consente un utilizzo più efficiente, permettendo alla capacità di gestire molti più set di dati rispetto a quanto la memoria possa contenere.

Il caricamento di un set di dati in memoria è un'operazione piuttosto costosa. In base alle dimensioni del set di dati, può durare da pochi secondi per i set di dati di piccole dimensioni a decine di secondi o persino minuti per quelli di circa 10 GB. La capacità Premium tenta di ridurre al minimo il numero di volte in cui sarà necessario caricare la capacità, mantenendo in memoria i set di dati usati più di recente per il maggior tempo possibile. Quando è necessaria memoria aggiuntiva, alcuni set di dati dovranno essere rimossi e il sistema tenterà di scegliere quello con l'impatto minore sull'esperienza utente. Quando è necessaria memoria aggiuntiva, alcuni set di dati dovranno essere rimossi e il sistema tenterà di scegliere quello con l'impatto minore sull'esperienza utente. Ad esempio, il sistema eviterà la rimozione dei set di dati usati attivamente negli ultimi minuti, poiché è probabile che vi vengano eseguite query a breve.

Il processo di rimozione di per sé è un'operazione rapida. Se il set di dati non è in uso attivo al momento della rimozione, l'impatto sull'utente sarà ridotto. Tuttavia, se un numero eccessivo di set di dati è in uso attivo nello stesso momento e non vi è memoria sufficiente per contenerli tutti, possono verificarsi molte rimozioni. Questo può causare una situazione di "thrashing", in cui vengono costantemente rimossi e ricaricati set di dati e gli utenti potrebbero riscontrare un calo evidente in termini di tempi di risposta e prestazioni.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Requisiti di memoria per l'aggiornamento di un set di dati in competizione con i requisiti di memoria per un set di dati attivo

I set di dati possono essere aggiornati in base a una pianificazione o su richiesta. Come descritto in precedenza, la memoria necessaria per gli aggiornamenti completi è almeno doppia rispetto alle dimensioni della memoria dei set di dati caricati e inattivi. Prima dell'avvio dell'aggiornamento, vengono stimati i requisiti di memoria per l'operazione. Se il requisito di memoria totale è superiore alla memoria disponibile nella capacità, alcuni set di dati vengono rimossi. I candidati per la rimozione vengono scelti in base alla data di ultimo utilizzo, vale a dire che il servizio tenta di mantenere in memoria il maggior numero possibile dei set di dati usati più di recente.

Se la memoria necessaria non è disponibile nonostante la rimozione, l'aggiornamento viene accodato per la ripetizione del tentativo. Il servizio riprova finché l'operazione non ha esito positivo o finché non viene avviata una nuova azione di aggiornamento.

Se viene eseguita una query interattiva su qualsiasi set di dati della capacità e non è disponibile memoria sufficiente a causa di un aggiornamento in corso, la richiesta ha esito negativo e l'utente deve eseguire un nuovo tentativo.

## <a name="cpu-resource-management-in-premium-capacity"></a>Gestione delle risorse CPU nella capacità Premium

I principali consumer di risorse CPU sono due:

- Query dei report
- Aggiornamenti (elaborazione)

### <a name="queries-from-reports"></a>Query dei report

Le query dei report usano risorse CPU della capacità. Se un report contiene query inefficienti o se si hanno molti utenti simultanei, può impegnare molte risorse CPU e la capacità esistente potrebbe non essere sufficiente per gestire il carico.

### <a name="refresh-parallelization-policy"></a>Criteri di parallelizzazione degli aggiornamenti

La memoria non è l'unica risorsa che può incidere sull'aggiornamento dei set di dati. Il numero di vCore in un server può rappresentare un ulteriore fattore. Dato che ogni operazione di aggiornamento richiede un certo numero di vCore, è previsto un limite rispetto al numero degli aggiornamenti eseguibili in parallelo. Il limite per SKU è descritto in dettaglio nella tabella seguente. Gli aggiornamenti aggiuntivi rispetto a questi limiti verranno accodati.

 | SKU  | vCore back-end  | Parallelismo di aggiornamento dei modelli   |
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

 **Invio simultaneo di venti aggiornamenti pianificati** - Power BI prova ad avviare i primi *x* aggiornamenti contemporaneamente. Il valore di *x* è determinato dai criteri di parallelizzazione degli aggiornamenti per lo SKU. Se Power BI non riesce a ottenere memoria sufficiente rimuovendo i set di dati inattivi (set di dati non utilizzati di recente), non tutti gli *x* aggiornamenti verranno avviati nello stesso momento. Gli aggiornamenti che non è possibile avviare vengono accodati fino al momento in cui diventa possibile.

 **Esecuzione simultanea di due aggiornamenti e memoria sufficiente per il completamento di uno solo di essi** - Viene avviato l'aggiornamento che è possibile completare. L'altro viene ritentato in un secondo momento.

 **Esecuzione di query su un numero elevato di set di dati durante l'aggiornamento di svariati set di dati** Se non è disponibile memoria sufficiente, Power BI prova a interrompere gli aggiornamenti attivi per dare priorità alle query interattive. Questo ridurrà le prestazioni di aggiornamento.

 **L'aggiornamento di un set di dati richiede più memoria di quella disponibile nelle dimensioni della capacità corrente** - L'aggiornamento avrà esito negativo. Non vengono eseguiti tentativi per ottenere più memoria mediante la rimozione.

 **Aggiornamento di un singolo set di dati con un notevole picco di memoria** - Se il picco è superiore alla quantità di memoria che può essere ottenuta tramite la rimozione dei set di dati inattivi, l'aggiornamento viene ritentato in un secondo momento finché non è disponibile memoria sufficiente per gestire il picco.

 **Esecuzione di query su un set di dati per cui non è possibile ottenere memoria sufficiente mediante la rimozione di tutti i set di dati inattivi e degli aggiornamenti**  - Queste query hanno esito negativo. Per questi tipi di requisiti del carico di lavoro occorre acquistare una capacità superiore.

## <a name="troubleshooting-and-testing"></a>Risoluzione dei problemi e test

Se i report sono lenti o non rispondono, iniziare testando un solo utente nel report. Iniziare quindi ad aumentare il carico di utenti simultanei per individuare il limite. In molti casi, ottimizzare le formule DAX (query di report) consente di modificare drasticamente le prestazioni dei report (e aumentare il numero di utenti simultanei supportati dalla capacità).

Usare la capacità Power BI Embedded in Azure per testare SKU diversi e determinare lo SKU Premium migliore per il carico di lavoro previsto. Lo SKU Power BI Embedded A4 SKU è uguale a P1, A5 è uguale a P2 e A6 è uguale a P3. In Azure, è possibile passare facilmente tra gli SKU aumentando o riducendo le prestazioni nel portale di Azure. Una volta individuato lo SKU più adatto per il carico di lavoro e completati i test, è possibile eliminare lo SKU.

In alcuni casi, aprire un file PBIX del modello nel computer e controllare l'utilizzo di CPU e memoria fornisce molte indicazioni sul problema. L'operazione non è di aiuto per i modelli molto grandi, ma per alcuni modelli più piccoli, provare ad aprire, aggiornare ed eseguire query sul modello dal computer. Controllare le dimensioni del modello, la memoria e la CPU usata quando si apre il modello. Provare ad aggiornare e ad eseguire query. Usare Gestione attività per controllare l'utilizzo di CPU e memoria per il file PBIX locale. A volte queste metriche nel computer stesso possono indicare che una capacità Premium inferiore, ad esempio P1/P2, potrebbe non essere idonea per la soluzione.
