---
title: DirectQuery per SAP HANA in Power BI
description: Considerazioni relative all'uso di DirectQuery con SAP HANA
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: cd266118fa560b3d637a85b352f8c1f03d137ec6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="directquery-and-sap-hana"></a>DirectQuery e SAP HANA
È possibile connettersi alle origini dati di **SAP HANA** usando direttamente **DirectQuery**. Sono disponibili due opzioni per la connessione a HANA:

* **Considerare HANA come un'origine multidimensionale (impostazione predefinita):** attualmente in anteprima e nuova impostazione predefinita. In questo caso, il comportamento sarà simile a quando Power BI si connette ad altre origini multidimensionali come SAP Business Warehouse o Analysis Services. Quando ci si connette a HANA con questa impostazione, viene selezionata una singola vista analitica o di calcolo e tutti gli attributi, le misure e le gerarchie di tale vista saranno disponibili nell'elenco dei campi. Quando vengono creati oggetti visivi, i dati aggregati verranno sempre recuperati HANA. Si tratta dell'approccio consigliato normale.

* **Considerare HANA come un'origine relazionale:** in questo caso, Power BI considera HANA come un'origine relazionale. Ciò offre una maggiore flessibilità, ma è necessario prestare attenzione per assicurarsi che le misure vengono aggregate come previsto e per evitare problemi di prestazioni.

L'approccio usato per la connessione dipende da un'opzione globale, impostata selezionando **File > Opzioni e impostazioni**, quindi **Opzioni > DirectQuery** e infine selezionando l'opzione **Considera HANA come origine relazionale**, come illustrato nella figura seguente. 

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

Si noti che il **connettore SAP HANA** è attualmente in **anteprima** e deve essere abilitato per rendere visibile l'opzione menzionata in precedenza. Per abilitare la nuova esperienza di anteprima di SAP HANA, selezionarla in **Opzioni > Funzionalità di anteprima**, come illustrato nella figura seguente.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01b.png)

L'opzione per considerare HANA come origine relazionale controlla l'approccio usato per qualsiasi *nuova* connessione creata. Non ha alcun effetto sulle eventuali connessioni HANA esistenti nel report corrente, né sulle connessioni in altri report aperti. Pertanto, se l'opzione è deselezionata, quando viene aggiunta una nuova connessione a HANA mediante **Recupera dati**, tale connessione verrà stabilita considerando HANA come origine multidimensionale. Tuttavia, se viene aperto un report diverso anch'esso connesso a HANA, il comportamento di tale report sarà ancora corrispondente all'opzione impostata *al momento della creazione*. Questo significa che i report che si connettono a HANA creati prima di febbraio 2018 continueranno a considerare HANA come origine relazionale. 

I due approcci corrispondono a comportamenti molto diversi e non è possibile cambiare approccio per i report esistenti. 

Di seguito verranno esaminati entrambi gli approcci in maggiore dettaglio.

## <a name="treat-hana-as-a-multi-dimensional-source-default"></a>Considerare HANA come origine multidimensionale (impostazione predefinita)

Questo è il comportamento predefinito ed è attualmente in anteprima. Per abilitare questa funzionalità di anteprima, seguire la procedura descritta nella sezione precedente per abilitare l'opzione di anteprima. 

Dopo aver abilitato questa funzionalità di **anteprima** in **Opzioni > Funzionalità di anteprima** (vedere la sezione precedente per istruzioni su come selezionare questa impostazione), tutte le nuove connessioni a HANA useranno questo metodo di connessione per impostazione predefinita, considerando HANA come origine multidimensionale. Per considerare una connessione a HANA come origine relazionale, è necessario selezionare **File > Opzioni e impostazioni** e quindi selezionare la casella in **DirectQuery > Considera HANA come origine relazionale**. Fino a quando questa funzionalità sarà disponibile in **anteprima**, i report creati con l'approccio multidimensionale *non possono* essere pubblicati nel servizio Power BI e tale operazione genererà errori quando il report viene aperto all'interno del servizio Power BI.  

Quando ci si connette a HANA come origine multidimensionale, si applica quanto segue:

* Nello **strumento di navigazione Recupera dati** è possibile selezionare una singola visualizzazione HANA. Non è possibile selezionare singole misure o singoli attributi. Non è disponibile alcuna query definita al momento della connessione e ciò è diverso rispetto all'importazione di dati o a quando si usa DirectQuery considerando HANA come origine relazionale. Questo significa anche che non è possibile usare direttamente una query SQL HANA quando si seleziona questo metodo di connessione.

* Tutti gli attributi, le misure e le gerarchie della vista selezionata verranno visualizzati nell'elenco dei campi. 

* Quando una misura viene usata in un oggetto visivo, HANA riceverà un query per recuperare il valore della misura al livello di aggregazione necessario per l'oggetto visivo. Quando si gestiscono misure non additive (contatori, rapporti e così via) tutte le aggregazioni vengono eseguite da HANA e non vengono eseguite ulteriori aggregazioni da Power BI. 

* Per assicurarsi che i valori di aggregazione corretti possano essere sempre ottenuti da HANA, è necessario imporre determinate restrizioni. Non è ad esempio possibile aggiungere colonne calcolate o combinare i dati da più viste HANA all'interno dello stesso report. 

Considerare HANA come origine multidimensionale non offre la maggiore flessibilità offerta dall'approccio *relazionale* alternativo, ma è più semplice e garantisce valori di aggregazione corretti quando si gestiscono misure HANA più complesse oltre a offrire in genere prestazioni migliori. 

L'**elenco dei campi** includerà tuti gli attributi, le misure e le gerarchie dalla vista HANA. Si notino i comportamenti seguenti che si applicano quando si usa questo metodo di connessione:

* Qualsiasi attributo incluso in almeno una gerarchia verrà nascosto per impostazione predefinita. Se necessario, è comunque possibile visualizzarli scegliendo **Visualizza elementi nascosti** dal menu di scelta rapida nell'elenco dei campi. È possibile renderli visibili dallo stesso menu di scelta rapida, all'occorrenza.

* In HANA, è possibile definire un attributo che usa un altro attributo come etichetta. Ad esempio, l'attributo **Product** (con valori 1, 2, 3 e così via) può usare l'attributo **ProductName** (con i valori Bike, Shirt, Gloves e così via) come etichetta. In questo caso, nell'elenco dei campi verrà visualizzato un singolo campo **Product** i cui valori saranno le etichette Bike, Shirt, Gloves e così via, ordinati in base ai valori chiave 1, 2 e 3 che ne determinano anche l'univocità. Viene creata anche una colonna nascosta **Product.Key**, che consente l'accesso ai valori di chiave sottostanti se necessario. 

Le eventuali variabili definite nel codice HANA sottostante vengono visualizzate al momento della connessione ed è possibile immettere i valori necessari. Tali valori possono essere modificati successivamente selezionando **Modifica query** sulla barra multifunzione e quindi **Modifica variabili** nel menu a discesa visualizzato. 

Le operazioni di modellazione consentite sono più restrittive rispetto al caso generale quando si usa DirectQuery, considerata la necessità di garantire che sia sempre possibile ottenere i dati aggregati corretti da HANA. È comunque ancora possibile eseguire numerose aggiunte e modifiche, tra cui definire misure, rinominare e nascondere i campi e definire formati di visualizzazione. Tutte queste modifiche verranno mantenute in caso di aggiornamento e verranno applicate le eventuali modifiche non in conflitto apportate alla vista HANA. 

### <a name="additional-modelling-restrictions"></a>Restrizioni di modellazione aggiuntive

Le principali restrizioni di modellazione aggiuntive per la connessione a SAP HANA con DirectQuery (considerata come origine multidimensionale) sono le seguenti: 

* **Nessun supporto per le colonne calcolate**: la possibilità di creare colonne calcolate è disabilitata. Ciò significa anche che il raggruppamento e il clustering, che creano le colonne calcolate, non sono disponibili.
* **Limitazioni aggiuntive per le misure**: ci sono altre limitazioni imposte alle espressioni DAX che è possibile usare nelle misure, per riflettere il livello di supporto offerto da SAP HANA.
* **Nessun supporto per la definizione di relazioni:** è possibile eseguire query su una singola vista all'interno di un report e pertanto la definizione di relazioni non è supportata.
* **Nessuna visualizzazione di dati**: la **Vista dati** in genere mostra i dati a livello di dettaglio nelle tabelle. Data la natura delle origini OLAP come SAP HANA, questa vista non è disponibile in SAP HANA.
* **I dettagli delle colonne e misure sono fissati**: l'elenco di colonne e misure visualizzate nell'elenco dei campi è fissato dall'origine sottostante e non può essere modificato. Ad esempio, non è possibile eliminare una colonna, né modificarne il tipo di dati (tuttavia, può essere rinominata).
* **Limitazioni aggiuntive in DAX**: ci sono altre limitazioni in DAX, che è possibile usare nelle definizioni di misure, in modo da riflettere le limitazioni nell'origine. Non è ad esempio possibile usare una funzione di aggregazione su una tabella.

### <a name="additional-visualization-restrictions"></a>Restrizioni di visualizzazione aggiuntive

Esistono alcune restrizioni per gli oggetti visivi durante la connessione a SAP HANA con DirectQuery (considerata come origine multidimensionale): 
* **Nessuna aggregazione di colonne**: non è possibile modificare l'aggregazione per una colonna in un oggetto visivo ed è sempre *Non riepilogare*.

## <a name="treat-hana-as-a-relational-source"></a>Considerare HANA come origine relazionale 

Se si sceglie di connettersi a HANA come origine relazionale, diventa disponibile una maggiore flessibilità. Ad esempio, è possibile creare colonne calcolate, includere dati da più viste HANA e creare relazioni tra le tabelle risultanti. Tuttavia, quando si usa SAP HANA in questo modo, è importante comprendere alcuni aspetti del modo in cui vengono considerate le connessioni, per assicurarsi che: 

* I risultati siano quelli previsti, quando la vista di SAP HANA contiene misure non additive, ad esempio conteggi distinti, o medie, anziché semplici somme.
* Le query risultanti siano efficienti

È utile iniziare chiarendo il comportamento di un'origine relazionale, ad esempio SQL Server, quando la query definita in **Recupera dati** o **Editor query** esegue un'aggregazione. Nell'esempio seguente una query definita in **Editor query** restituisce il prezzo medio di *ProductID*.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Se i dati vengono importati in Power BI, invece di DirectQuery, il risultato sarebbe il seguente:

* I dati vengono importati a livello di aggregazione definita dalla query creata in **Editor query**. Ad esempio, prezzo medio per prodotto. Di conseguenza viene creata una tabella con due colonne *ProductID* e *AveragePrice* che può essere usato negli oggetti visivi.
* In un oggetto visivo sui dati importati viene eseguita un'aggregazione successiva, ad esempio *Somma*, *Media*, *Min* e altre. Ad esempio, se si include *AveragePrice* in un oggetto visivo verrà usata l'aggregazione *Somma* per impostazione predefinita che restituirà la somma di *AveragePrice* per ogni *ProductID*; in questo caso di esempio sarebbe 13,67. Lo stesso vale per qualsiasi funzione di aggregazione alternativa,ad esempio *Min*, *Media*e così via, usata nell'oggetto visivo. Ad esempio, la *Media* di *AveragePrice* restituisce la media di 6,66, 4 e 3, che equivale a 4,56, ma non la media di *Price* nei sei record della tabella sottostante, ovvero 5,17.
  
Se si usa **DirectQuery** (sulla stessa origine relazionale) invece di Import, si applica la stessa semantica e i risultati saranno esattamente gli stessi:  

* Data la stessa query, in modo logico vengono presentati esattamente gli stessi dati a livello di report, anche se i dati non vengono effettivamente importati.

* In un oggetto visivo sulla tabella logica della query viene eseguita di nuovo un'aggregazione successiva, ad esempio *Somma*, *Media*, *Min* e altre. E di nuovo, un oggetto visivo contenente la *Media* di *AveragePrice* restituisce ugualmente 4,56.
  
Si consideri ora SAP HANA quando la connessione viene considerata come origine relazionale. Power BI può usare sia le *Viste analitiche* che le *Viste di calcolo* in SAP HANA; entrambe possono contenere misure. Ancora oggi l'approccio a SAP HANA segue gli stessi principi descritti in precedenza in questa sezione: la query definita in **Recupera dati** o **Editor query** determinerà i dati disponibili e quindi qualsiasi aggregazione successiva in un oggetto visivo su quei dati; lo stesso vale per Import e DirectQuery.  
Tuttavia, la caratteristica principale di HANA è che la query definita nella finestra di dialogo iniziale **Recupera dati** o **Editor query** è sempre una query di aggregazione e in genere includerà le misure in cui l'aggregazione effettiva che verrà usata è definita dalla vista HANA.

L'equivalente dell'esempio di SQL Server illustrato in precedenza consiste in una vista di HANA contenente *ID*, *ProductID*, *DepotID* e le misure che includono *AveragePrice*, definito nella vista come *Prezzo medio*.  
    
Se nell'esperienza **Recupera dati** sono state effettuate selezioni per le misure **ProductID** e **AveragePrice**, questo consente di definire una query sulla vista e richiedere i dati di aggregazione. Nell'esempio precedente, per motivi di semplicità viene usato pseudo-SQL che non corrisponde alla sintassi esatta di HANA SQL. Pertanto qualsiasi altra aggregazione definita in un oggetto visivo contribuisce a continuare l'aggregazione dei risultati di tale query. Di nuovo, come descritto in precedenza per SQL Server, questo vale sia per il caso di Import che di DirectQuery. Si noti che nel caso di DirectQuery la query di **Recupera dati** o **Editor query** verrà usata in una selezione all'interno di una singola query inviata ad HANA e pertanto in questo caso i dati non verranno letti tutti, prima di un'aggregazione aggiuntiva.  

Quando si usa DirectQuery su HANA, è importante tenere presente quanto segue per tutti questi comportamenti e queste considerazioni:  

* È necessario prestare attenzione alle altre aggregazioni eseguite negli oggetti visivi, ogni volta che la misura in HANA non è correttiva,ad esempio non è una semplice *Somma*, *Min* o *Max*.

* In **Recupera dati** o **Editor query** solo le colonne obbligatorie devono essere incluse per recuperare i dati necessari. Questo riflette il fatto che il risultato sarà una query ragionevole che può essere inviata ad HANA. Ad esempio, se sono state selezionate decine di colonne, pensando che potrebbero essere necessarie negli oggetti visivi successivi, anche per DirectQuery un semplice oggetto visivo implica che la query di aggregazione usata nella selezione conterrà tali colonne, che in genere avranno prestazioni basse.
  
Esaminiamo un esempio. Nell'esempio seguente la selezione di cinque colonne (**CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**) nella finestra di dialogo **Recupera dati**, oltre alla misura *OrderQuantity*, implica che in un secondo momento la creazione di un semplice oggetto visivo che contiene Min OrderQuantity comporterà la seguente query SQL per HANA. La parte in grigio è la selezione secondaria, contenente la query da **Recupera dati** / **Editor query**. Se questa selezione secondaria offre un risultato di cardinalità molto elevato, le prestazioni risultanti di HANA saranno probabilmente ridotte.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
A causa di questo comportamento, è consigliabile che gli elementi selezionati in **Recupera dati** o **Editor query** siano limitati agli elementi necessari, sebbene generino comunque una query ragionevole per HANA.  

## <a name="best-practices"></a>Procedure consigliate 

Per entrambi gli approcci per la connessione a SAP HANA, le raccomandazioni per l'uso di DirectQuery si applicano anche a HANA, in particolare quelle correlate a garantire prestazioni ottimali. Queste raccomandazioni sono descritte in dettaglio nell'articolo [Uso di DirectQuery in Power BI](desktop-directquery-about.md).
   
## <a name="limitations"></a>Limitazioni

L'elenco seguente descrive tutte le funzionalità di SAP HANA che non sono completamente supportate o hanno un comportamento diverso quando si usa Power BI. 

* **Gerarchie padre-figlio**: le gerarchie padre-figlio non saranno visibili in Power BI,
perché Power BI accede a HANA tramite l'interfaccia SQL e le gerarchie padre-figlio non sono completamente accessibili tramite SQL.
* **Altri metadati di gerarchia**: la struttura di base delle gerarchie viene visualizzata in Power BI, tuttavia alcuni metadati di gerarchia (ad esempio, il controllo del comportamento delle gerarchie incomplete) non avranno alcun effetto.
Anche in questo caso, la causa sono le limitazioni imposte dall'interfaccia SQL.
* **Connessione mediante SSL**: non è possibile connettersi alle istanze di SAP HANA configurate per l'uso di SSL.
Supporto per le viste di attributi: Power BI può connettersi a viste analitiche e di calcolo, ma non consente la connessione diretta alle viste di attributi.
* **Supporto per gli oggetti del catalogo**: Power BI non può connettersi a oggetti del catalogo.
* **Modifiche alle variabili dopo la pubblicazione**: non è possibile modificare i valori per tutte le variabili HANA direttamente nel servizio Power BI, dopo la pubblicazione del report. 
 
## <a name="known-issues"></a>Problemi noti 
L'elenco seguente descrive tutti i problemi noti per la connessione a SAP HANA (DirectQuery) tramite Power BI. 

* **Problema HANA quando si eseguono query per contatori e altre misure**: HANA restituisce dati non corretti in caso di connessione a una vista analitica e se nello stesso oggetto visivo vengono incluse una misura contatore e altre misure di rapporto. Questo problema è descritto nella nota SAP 2128928 (Risultati imprevisti per l'esecuzione di query su una colonna calcolata e un contatore). La misura di rapporto non sarà corretta in questo caso. 

* **Più colonne di Power BI da una singola colonna HANA**: per alcune viste di calcolo, in cui una colonna HANA viene usata in più di una gerarchia, HANA espone questa condizione come due attributi separati. Ciò comporta la creazione di due colonne in Power BI.  Queste colonne sono tuttavia nascoste per impostazione predefinita e tutte le query riguardanti le gerarchie, o le colonne direttamente, si comportano in modo corretto. 
 
## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su DirectQuery, vedere le risorse seguenti:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Origini dati supportate da DirectQuery)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [Gateway dati locale](service-gateway-onprem.md)

