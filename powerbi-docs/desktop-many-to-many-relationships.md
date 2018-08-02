---
title: Relazioni molti-a-molti in Power BI Desktop (anteprima)
description: Usare le relazioni molti-a-molti in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/23/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 1105de002f6461589d61c6f0077cceeedaada471
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39211340"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Relazioni molti-a-molti in Power BI Desktop (anteprima)

Con la funzionalità **relazione molti-a-molti** in **Power BI Desktop** è possibile unire in join le tabelle con una cardinalità **molti-a-molti** e creare modelli di dati che contengono più origini dati in modo più semplice e più intuitivo. La funzionalità **relazione molti-a-molti** fa parte delle capacità più ampie per i **modelli compositi** in **Power BI Desktop**.

![molti-a-molti nella finestra di dialogo Modifica relazione](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La capacità **relazioni molti-a-molti** in **Power BI Desktop** fa parte di una raccolta di tre funzionalità correlate:

* **Modelli compositi** - Consente a un report di avere più connessioni dati, tra cui connessioni DirectQuery o importazione, in qualsiasi combinazione.
* **Relazioni molti-a-molti** - Con i **modelli compositi** è possibile stabilire **relazioni molti-a-molti** tra tabelle, rimuovendo i requisiti per i valori univoci nelle tabelle ed evitando soluzioni alternative precedenti, come l'introduzione di nuove tabelle solo per stabilire relazioni. 
* **Modalità di archiviazione** - È ora possibile specificare gli oggetti visivi che richiedono una query per origini dati back-end e quelli che non la richiedono vengono importati anche se basati su DirectQuery, con conseguente miglioramento delle prestazioni e riduzione del carico per il back-end. In precedenza, anche oggetti visivi semplici, come i filtri dei dati, attivavano l'invio di query alle origini di back-end. 

Questa raccolta delle tre funzionalità correlate per i **modelli compositi** è descritta in articoli separati:

* I **modelli compositi** sono descritti in dettaglio nell'articolo [Modelli compositi in Power BI Desktop (anteprima)](desktop-composite-models.md).
* Le **relazioni molti-a-molti** sono descritti in questo articolo.
* La **modalità di archiviazione** è descritta in un articolo apposito [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md).

## <a name="enabling-the-many-to-many-relationships-preview-feature"></a>Abilitazione della funzionalità in anteprima relazioni molti-a-molti

La funzionalità **relazioni molti-a-molti**, disponibile in anteprima, fa parte delle capacità **modelli compositi** e deve essere abilitata in **Power BI Desktop**. Per abilitare i **modelli compositi**, selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità di anteprima** e quindi selezionare la casella di controllo **Modelli compositi**.

![abilitazione delle funzionalità in anteprima](media/desktop-composite-models/composite-models_02.png)

È necessario riavviare **Power BI Desktop** per rendere effettiva la modifica.

![riavvio richiesto per rendere effettive le modifiche](media/desktop-composite-models/composite-models_03.png)


## <a name="what-many-to-many-relationships-solves"></a>Quali relazioni molti-a-molti vengono risolte

Prima della disponibilità delle **relazioni molti-a-molti**, quando si definiva una relazione tra due tabelle in Power BI, almeno una delle colonne coinvolte nella relazione doveva contenere valori univoci. In molte circostanze, tuttavia, nessuna colonna nella tabella conteneva valori univoci. 

Ad esempio, due tabelle potrebbero includere una colonna con i valori *Country*, ma i valori di *Country* non sono univoci nelle tabelle. Per creare un join tra tali tabelle, era necessario creare una soluzione alternativa, ad esempio introdurre altre tabelle nel modello contenenti i valori univoci necessari. La funzionalità **relazioni molti-a-molti** offre un approccio alternativo, che consente di unire in join direttamente queste tabelle tramite una relazione con cardinalità **molti-a-molti**.  

## <a name="using-many-to-many-relationships"></a>Uso delle relazioni molti-a-molti

Quando si definisce una relazione tra due tabelle in Power BI, è necessario definire la cardinalità della relazione. Ad esempio, la relazione tra *ProductSales* e *Product* (usando le colonne *ProductSales[ProductCode]* e *Product[ProductCode]*) verrebbe definita come **molti-a-uno**, perché esistono molte vendite per ogni prodotto e la colonna nella tabella *Product* *(ProductCode)* è univoca. Quando si definisce la cardinalità di una relazione come **molti-a-uno**, **uno-a-molti** o **uno-a-uno**, Power BI esegue la convalida per verificare che la cardinalità selezionata corrisponda ai dati effettivi.

Ad esempio, esaminare il modello semplice nell'immagine seguente.

![visualizzazione delle relazioni](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Si immagini quindi che la tabella *Product* contenga solo due righe.

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Si immagini anche che la tabella *Sales* includa solo quattro righe, incluse le *vendite* per un prodotto **C** che non esiste nella tabella *Product* (a causa di un errore di integrità referenziale).

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Un oggetto visivo per la visualizzazione di *ProductName* e *Price* (dalla tabella *Product*), insieme al valore totale di *Qty* per ogni prodotto (dalla tabella *ProductSales*) verrebbe visualizzato come nell'immagine seguente: 

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Come si può vedere nell'immagine precedente, nell'oggetto visivo è presente una riga con *ProductName* vuoto, associata alle vendite per il prodotto *C*. Questa riga vuota corrisponde a quanto segue:

* Tutte le righe nella tabella *ProductSales* in cui non è presente alcuna riga corrispondente nella tabella *Product*. Si tratta di un problema di integrità referenziale, come per il prodotto *C* in questo esempio.

* Tutte le righe nella tabella *ProductSales* per cui la colonna chiave esterna è Null. 

Per questi motivi, in entrambi i casi la riga vuota corrisponde alle vendite per cui sono sconosciuti i valori *ProductName* e *Price*.

Tuttavia, in alcuni casi le tabelle sono unite in join da due colonne, ma nessuna delle colonne è univoca. Si considerino, ad esempio, le due tabelle seguenti:

* La tabella *Sales* contiene dati di vendita in base a *State*, con ogni riga che contiene l'importo delle vendite per il tipo di vendita in tale stato (inclusi gli stati CA, WA e TX) 

    ![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La tabella *CityData* contiene i dati sulle città, inclusi popolazione e stato (inclusi gli stati CA, WA e New York)

    ![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Anche se è presente una colonna *State* in entrambe le tabelle ed è ragionevole volere recuperare le *vendite* totali per *stato*, insieme alla popolazione totale di ogni stato, esiste un problema: la colonna *State* non è univoca nelle tabelle. 

## <a name="the-prior-workaround"></a>La soluzione alternativa precedente

Nelle versioni di **Power BI Desktop** precedenti alla versione di luglio 2018, non era possibile creare una relazione diretta tra queste tabelle. Una soluzione comune a questo problema consisteva nell'eseguire le operazioni seguenti:

* Creare una terza tabella contenente solo gli ID di *State* univoci. Può trattarsi di una tabella calcolata (definita tramite DAX) o di una tabella definita tramite una query definita in **Editor di query** che può contenere gli ID univoci ricavati da una delle tabelle o il set completo unito.

* Correlare le due tabelle originali nella nuova tabella, usando relazioni *molti-a-uno* comuni.

La tabella per la soluzione può essere lasciata visibile o nascosta in modo che non venga visualizzata nell'elenco dei campi. In quest'ultimo caso, la relazione **molti-a-uno** verrebbe comunemente impostata per filtrare in entrambe le direzioni, in modo da poter usare il campo *Stato* da una delle tabelle con la conseguente propagazione del filtro incrociato all'altra tabella. Questo approccio è illustrato nell'immagine seguente della **visualizzazione Relazioni**.

![visualizzazione delle relazioni](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un oggetto visivo che mostra i valori *State* (dalla tabella *CityData*) insieme ai totali per *Population* e *Sales* sarebbe quindi simile al seguente.

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

Si noti che dato l'uso dello stato dalla tabella *CityData* in questa soluzione alternativa, vengono elencati solo i valori di *State* in tale tabella e, di conseguenza, viene escluso lo stato TX. Inoltre, a differenza delle relazioni **molti-a-uno**, mentre la riga del totale include tutti i valori *Sales* (incluse le vendite di TX), i dettagli non includono una riga vuota a copertura delle righe non corrispondenti. Analogamente, non sarebbe presente alcuna riga vuota a copertura di eventuali valori *Sales* per cui è presente un valore Null per *State*.

Se si aggiungesse anche *City* a tale oggetto visivo, mentre la popolazione per ogni *City* è nota, il valore di *Sales* visualizzato per *City* sarebbe semplicemente una ripetizione di *Sales* per il valore di *State* corrispondente (come avviene in genere quando si esegue il raggruppamento su una colonna non correlata a una misura di aggregazione), come illustrato nell'immagine seguente.

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Se la nuova tabella *Sales* venisse definita come l'unione di tutti i valori *States* in questa soluzione alternativa e venisse resa visibile nell'elenco dei campi, lo stesso oggetto visivo che mostra i valori per *State* (nella nuova tabella) insieme ai valori totali per *Population* e *Sales* sarebbe come indicato di seguito.

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

In questo caso, come mostrato nell'oggetto visivo, verrebbero inclusi *TX* (con *Sales* ma con popolazione sconosciuta), e *New York* (con popolazione nota ma senza *Sales*). 

Come si può notare, questa soluzione alternativa non è ottimale e presenta molti problemi. Con la creazione della **relazione molti-a-molti**, questi problemi vengono risolti, come descritto nella sezione seguente.

## <a name="using-many-to-many-relationships-instead-of-the-workaround"></a>Uso di relazioni molti-a-molti al posto della soluzione alternativa

Nelle versioni di **Power BI Desktop** a partire da luglio 2018, è possibile correlare direttamente le tabelle con le caratteristiche descritte nella sezione precedente senza dover ricorrere alle soluzioni alternative illustrate. È ora possibile impostare la cardinalità di una relazione **molti-a-molti**, a indicare che nessuna delle due tabelle contiene valori univoci. Per questo tipo di relazioni, è comunque possibile stabilire quale tabella filtri l'altra tabella o usare un filtro bidirezionale in cui entrambe le tabelle si filtrano a vicenda.  

> [!NOTE]
> La possibilità di creare relazioni **molti-a-molti** è disponibile in anteprima e durante questa fase non è possibile pubblicare modelli usando relazioni **molti-a-molti** nel servizio Power BI. 

In **Power BI Desktop**, la cardinalità predefinita è **molti-a-molti** quando viene determinato che nessuna delle due tabelle contiene valori univoci per le colonne coinvolte nella relazione. In questi casi viene visualizzato un avviso, per verificare che l'impostazione della relazione sia il comportamento previsto, anziché l'effetto indesiderato di un problema dei dati. 

Ad esempio, quando si crea una relazione direttamente tra *CityData* e *Sales*, in cui il flusso dei filtri va da *CityData* a *Sales*, la finestra di dialogo della relazione sarà simile a quella illustrata nell'immagine seguente.

![Finestra di dialogo Modifica relazione](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La **visualizzazione Relazioni** risultante conterrebbe la relazione **molti-a-molti** diretta tra le due tabelle. L'aspetto nell'elenco **Campi** e il comportamento conseguente quando vengono creati oggetti visivi, sono quindi identici a quelli ottenuti con la soluzione alternativa descritta nella sezione precedente, in cui la tabella aggiuntiva (con i valori distinti per *State*) non viene resa visibile. Ad esempio, come nella sezione precedente che descrive la soluzione alternativa, un oggetto visivo che mostra i valori di *State* insieme a totale delle vendite e della popolazione avrebbe l'aspetto seguente.

![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Pertanto, le principali differenze tra le relazioni **molti-a-molti** e le più comuni relazioni **molti-a-uno** sono le seguenti.

* I valori mostrati non includono una riga vuota per le eventuali righe non corrispondenti nell'altra tabella, né per le righe in cui la colonna usata nella relazione nell'altra tabella è Null.
* Non è possibile usare la funzione *RELATED()* (perché più di una riga potrebbe essere correlata)
* L'uso della funzione *ALL()* su una tabella non rimuoverà i filtri applicati alle altre tabelle correlate tramite una relazione **molti-a-molti**. Ad esempio, una misura definita come illustrato di seguito nell'esempio precedente non rimuoverebbe i filtri sulle colonne nella tabella *CityData* correlata:

    ![esempio di script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Un oggetto visivo che mostra i valori per *State*, *Sales* e *Sales total* avrebbe quindi l'aspetto seguente:

    ![oggetto visivo tabella](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Per questo motivo, occorre prestare attenzione per assicurarsi che i calcoli che usano *ALL(\<Table>)*, come *% del totale complessivo*, restituiscano i risultati desiderati. 


## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Esistono alcune limitazioni per questa versione delle **relazioni molti-a-molti** e dei **modelli compositi**.

Le origini multidimensionali seguenti non possono essere usate con i **modelli compositi**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Set di dati Power BI

Quando ci si connette a tali origini multidimensionali tramite DirectQuery, non è neanche possibile connettersi a un'altra origine DirectQuery o attuare combinazioni con dati importati.

Le limitazioni esistenti per l'uso di DirectQuery si applicano anche quando si usano le **relazioni molti-a-molti**. Molte di queste limitazioni si riferiscono attualmente a ogni singola tabella, a seconda della **modalità di archiviazione** della tabella. Ad esempio, una colonna calcolata per una tabella importata può fare riferimento ad altre tabelle, ma una colonna calcolata per una tabella di DirectQuery è ancora limitata e può fare riferimento solo alle colonne nella stessa tabella. Altre limitazioni si applicano al modello nel suo complesso, se una qualsiasi delle tabelle all'interno del modello è in modalità DirectQuery. Ad esempio, le funzionalità **Informazioni rapide** e **Domande e risposte** non sono disponibili per un modello se per una delle tabelle all'interno di esso è impostata la **modalità di archiviazione** DirectQuery. 

## <a name="next-steps"></a>Passaggi successivi

Gli articoli seguenti includono ulteriori informazioni sui modelli compositi e descrivono anche la modalità DirectQuery in modo dettagliato.

* [Modelli compositi in Power BI Desktop (anteprima)](desktop-composite-models.md)
* [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md)

Articoli su DirectQuery:

* [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
* [Origini dati supportate da DirectQuery in Power BI](desktop-directquery-data-sources.md)

