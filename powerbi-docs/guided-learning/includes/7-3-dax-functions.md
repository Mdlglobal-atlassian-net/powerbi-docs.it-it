Con DAX sono disponibili numerose funzioni per modellare, creare o analizzare i dati. Queste funzioni possono essere raggruppate nelle categorie seguenti:

* Funzioni di **aggregazione**
* Funzioni di **conteggio**
* Funzioni **logiche**
* Funzioni **informative**
* Funzioni di **testo**
* Funzioni di **data**

Analogamente a Excel, quando si inizia a digitare una formula nella **barra della formula** di Power BI Desktop, viene visualizzato un elenco di funzioni disponibili per determinare la funzione disponibile da selezionare. Usando i tasti di direzione **su** e **giù** della tastiera è possibile evidenziare le funzioni disponibili e visualizzare una breve descrizione.

Power BI visualizza le funzioni che corrispondono alle lettere digitate, quindi se si digita *S* nell'elenco vengono visualizzate solo le funzioni che iniziano con la lettera *S*. Se si digita *Su*, nell'elenco vengono visualizzate solo le funzioni che *contengono* la sequenza di lettere *Su* nel nome (i nomi di funzione non devono iniziare necessariamente con *Su*, ma contenere tale sequenza di lettere).

![](media/7-3-dax-functions/dax-functions_1.png)

In questo modo è facile sperimentare con DAX e trovare tutte le varie funzioni DAX disponibili in Power BI. È sufficiente iniziare a digitare una formula e Power BI farà il resto.

Dopo aver illustrato come avviare una formula DAX, verranno esaminate ora le diverse categorie di funzioni.

## <a name="aggregation-functions"></a>Funzioni di aggregazione
DAX include diverse funzioni di **aggregazione**, tra cui le seguenti funzioni usate comunemente:

* SUM
* AVERAGE
* MIN
* MAX
* SUMX (e altre funzioni *X*)

Queste funzioni supportano solo le colonne numeriche e in genere possono aggregare una sola colonna per volta.

Tuttavia, le funzioni di aggregazione speciali che terminano con **X** come **SUMX** possono essere usate in più colonne. Queste funzioni scorrono la tabella e valutano l'espressione per ogni riga.

## <a name="counting-functions"></a>Funzioni di conteggio
Le funzioni di **conteggio** usate frequentemente in DAX includono:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Queste funzioni conteggiano diversi elementi, come valori distinti, valori non vuoti e righe di tabella.

## <a name="logical-functions"></a>Funzioni logiche
La raccolta di funzioni **logiche** in DAX include:

* AND
* OR
* NOT
* IF
* IFERROR

Queste funzioni speciali possono essere espresse anche con gli *operatori*. Ad esempio, nella formula DAX per **AND** è possibile usare **&&**.

Quando sono necessarie più di due condizioni nella formula è possibile usare gli operatori (ad esempio **&&**), altrimenti ai fini della leggibilità del codice DAX è consigliabile usare il nome della funzione stessa (ad esempio **AND**).

## <a name="information-functions"></a>Funzioni informative
Le funzioni **informative** in DAX includono:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Nonostante queste funzioni possano essere utili a seconda della situazione, la capacità di identificare in anticipo il tipo di dati delle colonne può essere di sicuro un vantaggio.

DAX usa le funzioni **MAX** e **MIN** sia per *aggregare* valori sia per *confrontarli*.

## <a name="text-functions"></a>Funzioni di testo
Le funzioni di **testo** in DAX includono:

* CONCATENATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Queste funzioni di **testo** hanno un comportamento molto simile a quelle con lo stesso nome in Excel, quindi se si ha familiarità con la gestione delle funzioni di testo in Excel si è già un passo avanti. In caso contrario, è sempre possibile sperimentare queste funzioni in Power BI e ottenere altre informazioni sul relativo comportamento.

## <a name="date-functions"></a>Funzioni di data
DAX include le funzioni di **data** seguenti:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Anche se queste funzioni sono utili per calcolare ed estrarre informazioni dai valori di *data*, non si applicano alla funzionalità di Business Intelligence per le gerarchie temporali, che usa una tabella data.

> Contenuto video fornito da [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

