---
title: Scenari di capacità di Microsoft Power BI Premium
description: Vengono descritti scenari comuni di capacità Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565336"
---
# <a name="premium-capacity-scenarios"></a>Scenari di capacità Premium

Questo articolo descrive gli scenari reali in cui sono state implementate le capacità di Power BI premium. Problemi comuni e le sfide, sono descritti anche come identificare i problemi e consentono di risolverli:

- [Mantenere aggiornati i set di dati](#keeping-datasets-up-to-date)
- [Che identifica i set di dati risponde lente](#identifying-slow-responding-datasets)
- [Identificazione delle cause per sporadicamente rallentare rispondono i set di dati](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinazione se vi è memoria sufficiente](#determining-whether-there-is-enough-memory)
- [Determinare se vi sia sufficiente CPU](#determining-whether-there-is-enough-cpu)

I passaggi, insieme a esempi di grafico e tabella sono dal **le metriche della capacità di Power BI Premium app** che un amministratore di Power BI avranno accesso a.

## <a name="keeping-datasets-up-to-date"></a>Mantenere aggiornati i set di dati

In questo scenario, è stata attivata un'indagine quando gli utenti espresso lamentele che i dati del report in alcuni casi sembravano essere obsolete o "obsolete".

Nell'app, l'amministratore interagisce con il **consente di aggiornare** visivo, l'ordinamento di set di dati il **il tempo di attesa massimo** statistiche in ordine decrescente. Questo oggetto visivo consente di visualizzare i set di dati con i tempi di attesa più lunghi, raggruppati per nome dell'area di lavoro.

![Aggiornamenti di set di dati ordinati in ordine decrescente di tempo di attesa massimo, raggruppato per area di lavoro](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Nel **oraria Aggiorna attesa tempi medi** visual, egli nota che i tempi di attesa di aggiornamento in modo coerente picchi 16:00 circa ogni giorno.

![L'aggiornamento è in attesa picco periodicamente alle 16.00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Sono disponibili numerosi possibili spiegazioni per questi risultati:

- Troppi tentativi di aggiornamento possono verificarsi allo stesso tempo, che supera i limiti definiti dal nodo di capacità. In questo caso, sei gli aggiornamenti simultanei in un P1 con allocazione di memoria predefinita.

- I set di dati da aggiornare possono risultare troppo grandi per rientrare nella memoria disponibile (che richiede almeno 2 volte la memoria necessaria per l'aggiornamento completo).
- Inefficiente per la logica di Power Query può essere causando un picco di utilizzo della memoria durante l'aggiornamento di set di dati. In una capacità di occupato, questo picco occasionalmente può raggiungere il limite fisico, l'esecuzione dell'aggiornamento e potenzialmente influire sulle altre operazioni di visualizzazione di report sulla capacità.
- Frequentemente a query i set di dati che devono rimanere in memoria può influire sulle capacità di altri set di dati di aggiornamento a causa di memoria disponibile è limitata.

Che consente di esaminare, l'amministratore di Power BI può cercare:

- Scarsa disponibilità di memoria al momento della data viene aggiornata quando la memoria disponibile è inferiore a 2 volte la dimensione del set di dati da aggiornare.
- Set di dati non aggiornati e non in memoria prima dell'aggiornamento, ancora iniziato a mostrare il traffico interattivo durante i periodi di aggiornamento pesanti. Per visualizzare i set di dati vengono caricati in memoria in qualsiasi momento, un amministratore di Power BI può esaminare i set di dati relativa alla **set di dati** scheda nell'app. L'amministratore può quindi attraversare filtro a un determinato momento facendo clic su una delle barre nel **oraria conta set di dati caricato**. Un picco locale, illustrato nell'immagine seguente, indica un'ora quando più set di dati sono stati caricati in memoria, che è stato possibile ritardare l'avvio degli aggiornamenti pianificati.
- Eliminazioni di set di dati maggiore richiede Inserisci durante gli aggiornamenti dei dati sono pianificati per avviarsi. Eliminazioni possono indicare vi è stato causato richieste di memoria elevata, è necessario gestire un numero eccessivo diversi report interattivi antecedente al momento dell'aggiornamento. Il **eliminazioni di set di dati orarie e il consumo di memoria** visual possono indicare chiaramente i picchi di eliminazioni.

L'immagine seguente mostra un picco locale nei set di dati caricato, che suggerisce l'esecuzione di query interattivo posticipato iniziale degli aggiornamenti. La selezione di un periodo di tempo nel **oraria conta set di dati caricati** visivo attraverserà filtro il **set di dati di dimensioni** visual.

![Un picco locale nei set di dati caricato suggerisce interattiva avvio ritardato l'esecuzione di query degli aggiornamenti](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

L'amministratore di Power BI è possibile tentare di risolvere il problema eseguendo i passaggi per assicurarsi che sia disponibile per gli aggiornamenti dei dati per l'avvio tramite memoria sufficiente:

- Connessione al set di dati e ai proprietari chiedendogli di scaglionare e lo spazio dati pianificazioni dell'aggiornamento.
- La riduzione di set di dati carico della query rimuovendo i dashboard non necessari o dashboard di riquadri, specialmente quelle che applicare la sicurezza a livello di riga.
- Velocizzare gli aggiornamenti dei dati, ottimizzando al tempo per la logica di Power Query. Migliorare le colonne calcolate o tabelle di modellazione. Ridurre le dimensioni dei set di dati o configurare i set di dati più grande per eseguire l'aggiornamento incrementale dei dati.

## <a name="identifying-slow-responding-datasets"></a>Che identifica i set di dati risponde lente

In questo scenario, ha iniziato un'indagine quando gli utenti espresso lamentele che determinati rapporti ha impiegato troppo tempo per aprire e in alcuni casi si blocca.

Nell'app, l'amministratore di Power BI può usare la **durate delle Query** visual per determinare i set di dati prestazioni peggiori ordinando i set di dati da decrescente **durata media**. Questo oggetto visivo Mostra anche set di dati i conteggi di query, pertanto è possibile vedere con quale frequenza vengono eseguite su set di dati.

![Set di dati prestazioni peggiori](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

L'amministratore può fare riferimento al **distribuzione della durata Query** visivo che mostra una distribuzione complessiva delle prestazioni delle query suddivisi in bucket: (< = 30 ms, 0 a 100 ms) per il periodo di tempo filtrato. In genere, le query che accettano un secondo o meno vengono considerati reattiva dalla maggior parte degli utenti; le query che richiedono più tempo tendono a creare una percezione del peggioramento delle prestazioni.

Il **oraria distribuzione della durata Query** visual consente all'amministratore di Power BI identificare i periodi di un'ora quando le prestazioni della capacità potrebbero essere stata percepita come insufficienti. Maggiore la barra di segmenti di query rappresentano le durate oltre a un secondo, il più grande il rischio che gli utenti percepiranno una riduzione delle prestazioni.

L'oggetto visivo è interattiva e quando viene selezionato un segmento della barra, il corrispondente **durate delle Query** visivo nella pagina del report tabella è a filtro incrociato per visualizzare il set di dati rappresenta. Questo filtro incrociato consente all'amministratore di Power BI identificare facilmente quale set di dati risponde lentamente.

L'immagine seguente mostra un oggetto visivo filtrato in base **oraria distribuzioni di durata Query**, messa a fuoco sui set di dati prestazioni peggiori in bucket di un'ora. 

![Filtrato oraria Query durata distribuzioni visual Mostra peggio eseguendo i set di dati](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Una volta identificato il set di dati dalle prestazioni scarse in un intervallo di tempo specifico di un'ora, l'amministratore di Power BI può esaminare se una riduzione delle prestazioni è causata da una capacità in overload o a causa di un modo non corretto progettato set di dati o report. Cui possono fare riferimento al **tempi di attesa delle Query** visivo e i set di dati di ordinamento ordine decrescente di tempo di attesa media della query. Se è in attesa un'alta percentuale delle query, una richiesta elevata per il set di dati è probabilmente la causa di troppi attese di query. Se la query Media di tempo di attesa è sostanziale (> 100 ms), potrebbe essere opportuno valutare il set di dati e report per vedere se è possibile ottimizzare. Ad esempio, meno gli oggetti visivi nella data pagine del report o un'ottimizzazione di espressione DAX.

![L'oggetto visivo tempi di attesa delle Query consente di visualizzare i set di dati con prestazioni ridotte](media/service-premium-capacity-scenarios/query-wait-times.png)

Esistono diversi motivi possibili per l'accumulo di tempo di attesa di query nei set di dati:

- Una progettazione di modelli non ottimali, le espressioni di misura o persino progettazione dei report - tutte le circostanze che possono contribuire a query che utilizzano livelli elevati di CPU a esecuzione prolungata. In tal modo le nuove query in attesa finché i thread CPU diventino disponibili ed è possibile creare un effetto di serie di istruzioni (blocco del traffico può essere considerata), presenta comunemente durante l'orario di ufficio di picco. Il **attese Query** pagina sarà la risorsa principale per determinare se i set di dati hanno tempi di attesa elevato Media della query.
- Un numero elevato di utenti simultanei capacità (centinaia di migliaia) utilizzano il report o set di dati stesso. I set di dati anche ben progettata può eseguire in modo errato oltre una soglia di concorrenza. Ciò in genere viene indicato con un singolo set di dati che mostra un valore notevolmente superiore per il conteggio di query rispetto a Mostra altri set di dati (ad esempio, 300 KB esegue una query per un set di dati rispetto a < 30 KB query per tutti gli altri set di dati). A un certo punto le attese di query per questo set di dati verrà avviata in modo da scaglionare, che può essere visualizzata nel **durate delle Query** visual.
- Molti diversi set di dati sottoposti a query contemporaneamente, provocando thrashing come frequente del ciclo di set di dati da e verso memoria. Di conseguenza gli utenti riscontra prestazioni rallentate quando il set di dati vengono caricati in memoria. Per confermare, l'amministratore di Power BI può fare riferimento al **eliminazioni di set di dati orarie e il consumo di memoria** visual, che potrebbe indicare che un numero elevato di set di dati caricati in memoria sono in corso rimosso ripetutamente.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificazione delle cause per sporadicamente rallentare rispondono i set di dati

In questo scenario, un'indagine, ha iniziato a quando gli utenti descritto che oggetti visivi del report in alcuni casi sono lenti a rispondere o potrebbe non rispondere, ma in altri momenti fossero siano accettabili reattive.

All'interno dell'app, il **durate delle Query** sezione è stata usata per trovare il set di dati causa del problema nel modo seguente:

- Nel **durate delle Query** visual l'amministratore filtrato set di dati dal set di dati (a partire i primi set di dati sottoposti a query) ed esaminare le barre filtrate cross-i **oraria Query distribuzioni** visual.
- Quando una singola barra un'ora ha illustrato le modifiche significative del rapporto tra tutti i gruppi di durata delle query e altre barre di un'ora per set di dati (ad esempio, i rapporti tra i colori modifica drasticamente), significa che questo set di dati illustrato una modifica sporadica in Prestazione.
- Le barre di un'ora che mostra una parte irregolare delle query con prestazioni ridotte, indicato un intervallo di tempo in cui tale set di dati sia stato influenzato da un effetto di noisy neighbor, provocato da attività degli altri set di dati.

L'immagine seguente mostra un'ora il 30 gennaio, in cui si è verificato un ostacolo significativo delle prestazioni di un set di dati, indicato dalla dimensione della finestra di "(3,10s]"durata bucket di esecuzione. Facendo clic sulla barra di un'ora, vengono visualizzati tutti i set di dati caricati in memoria durante tale periodo, esponendo i set di dati possibili che causa l'effetto influiscono negativamente sulle prestazioni.

![Indicatore da una parte significativa delle prestazioni peggiori](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Una volta identificato un oggetto timespan problematico (ad esempio, durante il 30 gennaio nell'immagine precedente) all'amministratore di Power BI può rimuovere tutti i filtri di set di dati quindi filtra solo per tale intervallo di tempo per determinare quali set di dati in modo attivo sono state eseguite query durante l'operazione. Set di dati per l'effetto di noisy neighbor causa del problema è in genere il set di dati sottoposti a query top o quella con la durata più lunga Media della query.

Una soluzione a questo problema potrebbe essere la causa del problema sono supportati i set di dati in diverse aree di lavoro in capacità Premium differenti o in capacità condivisa se le dimensioni del set di dati, i requisiti di consumo e l'aggiornamento dati modelli di distribuzione.

Potrebbe essere true anche il contrario. L'amministratore di Power BI è stato possibile identificare volte quando migliora drasticamente le prestazioni delle query un set di dati e quindi cercare ciò che non viene più visualizzata. Se non sono presente in tale punto determinate informazioni, che può essere utile in modo che punti al problema che provocano.

## <a name="determining-whether-there-is-enough-memory"></a>Determinazione se vi è memoria sufficiente

Per determinare se è disponibile memoria sufficiente per la capacità di completare i carichi di lavoro, l'amministratore di Power BI può fare riferimento al **percentuali di memoria utilizzata** visivo nel **i set di dati** scheda dell'app. **Tutti i** memoria (totale) rappresenta la memoria utilizzata dal set di dati caricati in memoria, indipendentemente dal fatto che vengono attivamente sottoposti a query o elaborazione. **Attiva** memoria rappresenta la memoria utilizzata dal set di dati che vengono attivamente elaborati.

In una capacità integro avrà un aspetto dell'oggetto visivo come questa, che mostra un gap tra tutti i (totale) e memoria attiva:

![Una capacità integro mostrerà un gap tra tutti i (totale) e di memoria attive](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

In una capacità riscontrando un utilizzo elevato della memoria, l'oggetto visivo stesso mostrerà chiaramente memoria attiva e la memoria totale convergenti, vale a dire che è Impossibile caricare set di dati aggiuntivi in memoria, quindi. In questo caso, l'amministratore di Power BI può scegliere **capacità riavviare** (nella **opzioni avanzate** dell'area di impostazioni di capacità del portale di amministrazione). Riavviare i risultati di capacità in tutti i set di dati viene scaricata dalla memoria e consentendo loro di ricaricare in memoria come richiesto (dalla query o aggiornamento dati).

![* * Attiva * * memoria convergente con * * memoria All * *](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determinare se vi sia sufficiente CPU

In generale, l'utilizzo medio della CPU di una capacità deve rimanere sotto dell'80%. Che superano questo valore indica che la capacità sta per raggiungere la saturazione della CPU.

Effetti della saturazione della CPU sono espresse dalle operazioni richiede più tempo del previsto, a causa della capacità di esecuzione di numerosi cambi di contesti di CPU a causa dei tentativi per l'elaborazione di tutte le operazioni. In una capacità Premium con un numero elevato di query simultanee, questo è indicato da tempi di attesa di query elevati. Una conseguenza di tempi di attesa di query elevati è più lento della velocità di risposta superiori al consueto. L'amministratore di Power BI è possibile identificare facilmente quando la CPU è satura visualizzando il **oraria distribuzioni di tempo di attesa Query** visual. I picchi periodici di query di attesa conteggi indicano potenziali saturazione della CPU.

![I picchi periodici di query di attesa conteggi indicano potenziali saturazione della CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Un modello simile in alcuni casi può essere rilevato in operazioni in background se cui contribuiscono alla saturazione della CPU. Un amministratore di Power BI può cercare un picco periodico nei tempi di aggiornamento per un set di dati specifico, che può indicare la saturazione della CPU al momento (probabilmente a causa di altri set di dati in corso aggiornamenti e/o query interattive). In questa istanza, che fa riferimento per la **sistema** visualizzazione dell'app potrebbe non necessariamente rivela che la CPU è al 100%. Il **sistema** consente di visualizzare le medie oraria, ma la CPU può diventare saturo per diversi minuti di pesanti operazioni, che viene visualizzato come picchi in tempi di attesa.

Sono disponibili ulteriori dettagli per visualizzare l'effetto della saturazione della CPU. Mentre il numero di query in attesa è importante, il tempo di attesa di query verrà sempre eseguito in una certa misura senza causare una riduzione delle prestazioni percepibile. Alcuni set di dati (con più lunga medio fase di query, che indica la complessità o dimensioni) sono più soggette agli effetti della saturazione della CPU rispetto ad altri. Per identificare facilmente tali set di dati, l'amministratore di Power BI può cercare le modifiche nella composizione colore delle barre nel **oraria distribuzione tempo di attesa** visual. Dopo l'individuazione di una barra degli outlier, possono cercare i set di dati con query attese durante tale periodo e anche esaminare confrontato per query con durata media per il tempo di attesa media della query. Quando queste due metriche sono di grandezza e il carico di lavoro di query del set di dati è non semplice, è probabile che il set di dati è stata interessata da CPU insufficiente.

Questo effetto può essere particolarmente evidente quando un set di dati vengono utilizzati in brevi picchi di query ad alta frequenza da più utenti (ad esempio, in una sessione di formazione), causando la saturazione della CPU durante ogni burst. In questo caso, i tempi di attesa query significativi in questo set di dati possono essere provati, nonché conseguenze su altri set di dati della capacità (effetto influiscono negativamente sulle prestazioni).

In alcuni casi, gli amministratori di Power BI possono richiedere che i proprietari del set di dati crei un minore carico di lavoro di query volatili tramite la creazione di un dashboard (Aggiorna le query che periodicamente con qualsiasi set di dati per i riquadri memorizzato nella cache) invece di un report. Si possono aiutare a evitare i picchi quando viene caricato il dashboard. Questa soluzione potrebbe non essere sempre possibile per determinati requisiti di business, tuttavia può essere un metodo efficace per evitare la saturazione della CPU, senza apportare la modifica al set di dati.

## <a name="acknowledgements"></a>Riconoscimenti

Questo articolo è stato scritto da Peter Myers, MVP di piattaforma dei dati e indipendenti esperti di Business Intelligence con [bit per bit soluzioni](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Monitorare le capacità Premium con l'app](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Capacità di monitoraggio nel portale di amministrazione](service-admin-premium-monitor-portal.md)   

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

||||||