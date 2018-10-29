---
title: Relazioni molti-a-molti in Power BI Desktop (anteprima)
description: Usare le relazioni molti-a-molti in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 379f80e1e87181ffdacdaab01d87ff435f2a9501
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/20/2018
ms.locfileid: "49473775"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Relazioni molti-a-molti in Power BI Desktop (anteprima)

Con la funzionalità *Relazioni molti-a-molti* di Power BI Desktop, è possibile unire le tabelle che usano una cardinalità *Molti-a-molti*. Ciò consente di creare in modo più semplice e intuitivo modelli di dati che contengono due o più origini dati. La funzionalità *Relazioni molti-a-molti* fa parte delle capacità più ampie per i *modelli compositi* di Power BI Desktop.

![Una relazione molti-a-molti nel riquadro "Modifica relazione"](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La funzione *Relazioni molti-a-molti* di Power BI Desktop fa parte di una raccolta di tre funzionalità correlate:

* **Modelli compositi**: consente a un report di avere due o più connessioni dati, tra cui connessioni DirectQuery o importazione, in qualsiasi combinazione. Per altre informazioni, vedere [Modelli compositi in Power BI Desktop (anteprima)](desktop-composite-models.md).

* **Relazioni molti-a-molti**: con *modelli compositi* è possibile stabilire *relazioni molti-a-molti* tra le tabelle. Questo approccio consente di rimuovere i requisiti per i valori univoci nelle tabelle. Annulla anche le soluzioni alternative precedenti, ad esempio l'introduzione di nuove tabelle solo per stabilire relazioni. La funzionalità è descritta più dettagliatamente in questo articolo.

* **Modalità di archiviazione**: ora è possibile specificare gli oggetti visivi che richiedono una query per origini dati back-end. Quelli che non la richiedono vengono importati anche se basati su DirectQuery, con conseguente miglioramento delle prestazioni e riduzione del carico per il back-end. In precedenza, anche oggetti visivi semplici, come i filtri dei dati, iniziavano le query che venivano inviate alle origini di back-end. Vedere [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md) per altre informazioni.

## <a name="enable-the-many-to-many-relationships-preview-feature"></a>Abilitare la funzionalità in anteprima *Relazioni molti-a-molti*

La funzionalità *Relazioni molti-a-molti* deve essere abilitata in Power BI Desktop. Per abilitare i modelli compositi, selezionare **File** > **Opzioni e impostazioni** > **Opzioni** > **Funzionalità di anteprima** e quindi selezionare la casella di controllo **Modelli compositi**.

![Riquadro funzionalità di anteprima](media/desktop-composite-models/composite-models_02.png)

Per abilitare la funzionalità, è necessario riavviare Power BI Desktop.

![Finestra "La funzionalità richiede il riavvio"](media/desktop-composite-models/composite-models_03.png)

## <a name="what-many-to-many-relationships-solves"></a>Che cosa risolvono le *relazioni molti-a-molti*

Prima che la funzionalità *Relazioni molti-a-molti* fosse disponibile, la relazione tra due tabelle era definita in Power BI. Almeno una delle colonne della tabella interessate dalla relazione doveva contenere valori univoci. Spesso, tuttavia, nessuna colonna conteneva valori univoci. 

Ad esempio, due tabelle potevano includere la colonna *Country*, ma i valori di *Country* non erano univoci nelle tabelle. Per unire tali tabelle, era necessario escogitare una soluzione alternativa. Una possibile soluzione alternativa consisteva nell'introdurre nel modello delle tabelle aggiuntive con i valori univoci necessari. Grazie alla funzionalità *Relazioni molti-a-molti*, ora è possibile unire tali tabelle direttamente usando una relazione con cardinalità **molti a molti**.  

## <a name="use-many-to-many-relationships"></a>Usare le *relazioni molti-a-molti*

Quando si definisce una relazione tra due tabelle in Power BI, è necessario specificare la cardinalità della relazione. Ad esempio, la relazione tra *ProductSales* e *Product*&mdash;utilizzando le colonne *ProductSales [ProductCode]* e *Product [ProductCode]*&mdash;verrebbe definita come *molti-a-uno*. La relazione viene definita in questo modo perché sono presenti molti valori Sales per ogni prodotto e la colonna della tabella *Product* *(ProductCode)* è univoca. Quando si definisce una relazione con cardinalità *molti-a-uno*, *uno-a-molti* o *uno-a-uno*, Power BI la convalida per verificare che la cardinalità selezionata corrisponda effettivamente ai dati.

Ad esempio, esaminare il modello semplice nell'immagine seguente:

![Visualizzazione delle relazioni](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Ora, si supponga che la tabella *Product* contenga solo due righe, come illustrato:

![Oggetto visivo tabella Product con due righe](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Si immagini anche che la tabella *Sales* includa solo quattro righe, con una riga per un prodotto C e che, a causa di un errore di integrità referenziale, il prodotto C non esiste nella tabella *Product*.

![Oggetto visivo tabella Sales con quattro righe](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

*ProductName* e *Price*, della tabella *Product*, insieme al valore totale di *Qty* per ogni prodotto, della tabella *ProductSales*, verrebbe visualizzato come segue: 

![Oggetto visivo che visualizza il nome del prodotto, il prezzo e la quantità](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Come si vede nella figura precedente, c'è la riga *ProductName* vuota associata alle vendite per il prodotto C. Questa riga vuota corrisponde agli elementi seguenti:

* Tutte le righe della tabella *ProductSales* per le quali non esistono righe corrispondenti nella tabella *Product*. Si verifica un problema di integrità referenziale, come illustrato per il prodotto *C* in questo esempio.

* Tutte le righe della tabella *ProductSales* per cui la colonna chiave esterna è Null. 

Per questi motivi, in entrambi i casi, la riga vuota corrisponde alle vendite per cui sono sconosciuti i valori *ProductName* e *Price*.

In alcuni casi le tabelle sono unite in join da due colonne, ma nessuna delle colonne è univoca. Si considerino, ad esempio, le due tabelle seguenti:

* La tabella *Sales* contiene dati di vendita per *State*, con ogni riga che contiene l'importo delle vendite per il tipo di vendita in tale stato, inclusi gli stati CA, WA e TX. 

    ![Tabella Sales che contiene i dati di vendita per stato (State)](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La tabella *CityData* contiene i dati sulle città, inclusi popolazione e stato (inclusi gli stati CA, WA e New York).

    ![Tabella Sales che contiene i dati su città, stato e popolazione](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Nonostante sia presente una colonna *State* in entrambe le tabelle ed è ragionevole volere recuperare le vendite totali per stato insieme alla popolazione totale di ogni stato, esiste un problema: la colonna *State* non è univoca nelle tabelle. 

## <a name="the-previous-workaround"></a>La soluzione alternativa precedente

Nelle versioni di Power BI Desktop precedente alla versione di luglio 2018, gli utenti non potevano creare una relazione diretta tra queste tabelle. Una soluzione comune a questo problema consisteva nell'eseguire l'operazione seguente:

* Creare una terza tabella contenente solo gli ID di *State* univoci. La tabella potrebbe avere una o tutte le caratteristiche seguenti:
  * Una tabella calcolata, definita tramite il linguaggio DAX (Data Analysis Expressions).
  * Una tabella basata su una query definita nell'Editor di query che potrebbe visualizzare gli ID univoci prelevati da una delle tabelle.
  * Il set completo combinato.

* Correlare le due tabelle originali nella nuova tabella usando relazioni *molti-a-uno* comuni.

La tabella della soluzione alternativa può essere lasciata visibile o essere nascosta in modo che non venga visualizzata nell'elenco **Campi**. Se si nasconde la tabella, le relazioni *molti-a-uno* verrebbero normalmente impostate per filtrare in entrambe le direzioni, e si potrebbe utilizzare il campo *State* di una qualsiasi delle due tabelle. Il filtro incrociato conseguente verrebbe propagato all'altra tabella. Questo approccio è illustrato nell'immagine seguente:

![Visualizzazione delle relazioni](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un oggetto visivo che visualizza i valori *State* (dalla tabella *CityData*) insieme ai totali per *Population* e *Sales* sarebbe quindi simile al seguente:

![Oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Poiché in questa soluzione alternativa viene usata la colonna State della tabella *CityData*, vengono elencati solo gli stati in tale tabella e, di conseguenza, viene escluso lo stato TX. Inoltre, a differenza delle relazioni *molti-a-uno*, mentre la riga del totale include tutti i valori *Sales*, incluse le vendite di TX, i dettagli non includono una riga vuota a copertura delle righe non abbinate. Analogamente, non sarebbe presente alcuna riga vuota a copertura di eventuali valori *Sales* contraddistinti dal valore Null per *State*.

Se all'oggetto visivo si aggiunge anche *City* nonostante la popolazione di ogni valore *City* sia nota, i valori *Sales* mostrati per *City* si limiteranno a ripetere semplicemente i valori *Sales* dell'elemento *State* corrispondente. Ciò avviene in genere quando il raggruppamento in una colonna non è correlato a una misura di aggregazione, come illustrato nell'immagine seguente:

![Oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Se in questa soluzione alternativa si definisce la nuova tabella *Sales* come la combinazione di tutti i valori di *State* e la si rende visibile nell'elenco **Fields**, nello stesso oggetto visivo verrebbe visualizzato sia il valore *State*, nella nuova tabella, il valore totale di *Population* e il totale di *Sales*, come illustrato nell'immagine seguente:

![Oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Come si può notare, *TX*&mdash;con dati *Sales* ma dati *Population*&mdash; sconosciuti e *New York*&mdash; con dati *Population* ma nessun dato *Sales*&mdash;verrebbero inclusi. Questa soluzione alternativa non è ottimale e presenta molti problemi. Con la creazione delle relazioni molti-a-molti, questi problemi vengono risolti, come descritto nella sezione seguente.

## <a name="use-many-to-many-relationships-instead-of-the-workaround"></a>Usare le *relazioni molti-a-molti* al posto della soluzione alternativa

A partire dalla versione di luglio 2018 di Power BI Desktop, è possibile correlare direttamente le tabelle, ad esempio quelle descritte in precedenza, senza dover ricorrere a simili soluzioni alternative. Ora è possibile impostare la cardinalità della relazione su *molti-a-molti*. Questa impostazione indica che nessuna delle due tabelle contiene valori univoci. Per questo tipo di relazioni, è comunque possibile stabilire quale tabella filtri l'altra tabella o applicare un filtro bidirezionale in cui entrambe le tabelle si filtrano a vicenda.  

> [!NOTE]
> La possibilità di creare *relazioni molti-a-molti* è disponibile in anteprima. Mentre è in anteprima, non è possibile pubblicare nei modelli di servizio Power BI che utilizzano *relazioni molti-a-molti*. 

In Power BI Desktop, la cardinalità predefinita è *molti-a-molti* quando viene determinato che nessuna delle due tabelle contiene valori univoci per le colonne coinvolte nella relazione. In questi casi viene visualizzato un avviso, per verificare che l'impostazione della relazione sia il comportamento previsto, e non l'effetto indesiderato di un problema dei dati. 

Ad esempio, quando si crea una relazione diretta tra *CityData* e *Sales*&mdash;, in cui il flusso dei filtri va da *CityData* a *Sales*&mdash;Power BI Desktop visualizza la finestra **Modifica relazione** come illustrato nell'immagine seguente:

![Finestra "Modifica relazione"](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La visualizzazione **Relazioni** risultante conterrebbe la relazione molti-a-molti diretta tra le due tabelle. L'aspetto delle tabelle dell'elenco **Campi**, e il relativo comportamento quando vengono creati gli oggetti visivi, è simile a quando è stata applicata la soluzione alternativa. Nella soluzione alternativa, la tabella aggiuntiva che visualizza i distinti dati di *State* non è resa visibile. Ad esempio, come descritto nella sezione precedente, un oggetto visivo che mostri i dati di *State*, *Population* e *Sales* sarebbe visualizzato come indicato di seguito:

![Oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Le principali differenze tra le *relazioni molti-a-molti* e le più comuni relazioni *molti-a-uno* sono le seguenti:

* I valori mostrati non includono una riga vuota che tenga conto delle righe non abbinate nell'altra tabella. Né i valori tengono conto delle righe in cui la colonna usata nella relazione nell'altra tabella ha valore Null.
* Non è possibile usare la funzione `RELATED()` perché più di una riga potrebbe essere correlata.
* L'uso della funzione `ALL()` su una tabella non rimuove i filtri applicati alle altre tabelle correlate tramite una relazione molti-a-molti. Nell'esempio precedente, una misura definita come illustrato nello script seguente non rimuoverebbe i filtri sulle colonne nella tabella *CityData* correlata:

    ![Esempio di script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Un oggetto visivo che mostra i dati per *State*, *Sales* e *Sales total* avrebbe quindi l'aspetto seguente:

    ![Oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Tenendo presenti le differenze precedenti, assicurarsi che i calcoli che utilizzano `ALL(\<Table>)`, come *% del totale complessivo*, restituiscano i risultati previsti. 


## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Esistono alcune limitazioni per questa versione delle *relazioni molti-a-molti* e dei modelli compositi.

Le origini Live Connect (multidimensionali) seguenti non possono essere usate con i modelli compositi:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Set di dati Power BI
* Azure Analysis Services

Quando ci si connette a tali origini multidimensionali tramite DirectQuery, non è possibile connettersi a un'altra origine DirectQuery o attuare combinazioni con dati importati.

Le limitazioni esistenti per l'uso di DirectQuery si applicano anche quando si usano le *relazioni molti-a-molti*. Molte di queste limitazioni si riferiscono attualmente a ogni singola tabella, a seconda della modalità di archiviazione della tabella. Ad esempio, una colonna calcolata per una tabella importata può fare riferimento ad altre tabelle, ma una colonna calcolata per una tabella di DirectQuery può fare riferimento solo alle colonne nella stessa tabella. Altre limitazioni si applicano al modello nel suo complesso, se una qualsiasi delle tabelle all'interno del modello è in modalità DirectQuery. Ad esempio, le funzionalità Informazioni rapide e Domande e risposte non sono disponibili per un modello se per una delle tabelle all'interno di esso è impostata la modalità di archiviazione DirectQuery. 

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui modelli compositi e DirectQuery, vedere gli articoli seguenti:
* [Modelli compositi in Power BI Desktop (anteprima)](desktop-composite-models.md)
* [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md)
* [Usare DirectQuery in Power BI Desktop](desktop-directquery-about.md)
* [Origini dati supportate da DirectQuery in Power BI Desktop](desktop-directquery-data-sources.md)
