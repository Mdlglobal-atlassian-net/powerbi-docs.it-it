Una differenza significativa tra **DAX** e il linguaggio di formule Excel è costituita dal fatto che DAX consente di passare *intere tabelle* tra le espressioni, invece di limitare il passaggio a un singolo valore. Un vantaggio rilevante è rappresentato dal fatto che DAX consente di filtrare le tabelle nelle rispettive espressioni e quindi di usare il set di valori filtrato.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

DAX consente di creare tabelle calcolate interamente nuove e quindi di gestirle esattamente come qualsiasi altra tabella, creando anche relazioni tra queste e altre tabelle nel modello di dati.

## <a name="dax-table-functions"></a>Funzioni delle tabelle DAX
DAX offre un set avanzato di funzioni **tabella**, incluse le seguenti:

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Queste funzioni restituiscono una tabella completa, invece di un valore. In genere i risultati di una funzione **tabella** vengono usati in altre analisi come parte di un'espressione più grande, invece di usare la tabella restituita come valore finale. È importante notare che quando si usa una funzione tabella, i risultati ereditano le relazioni delle rispettive colonne.

È possibile combinare funzioni di tabella nell'espressione, purché ognuna usi una tabella e restituisca una tabella. Si consideri ad esempio l'espressione DAX seguente:

    FILTER (ALL (Table), Condition)

Questa espressione applica un filtro all'intero oggetto *Table*, ignorando il contenuto di qualsiasi filtro corrente.

La funzione DISTINCT restituisce i valori distinti di una colonna che sono visibili anche nel contesto corrente. Per usare l'esempio di espressione DAX precedente, se si usa **ALL** nell'espressione i filtri verranno ignorati, mentre se si sostituisce **ALL** con **DISTINCT** i filtri verranno rispettati.

## <a name="counting-values-with-dax"></a>Conteggio di valori con DAX
Ecco una domanda comune per cui gli autori di report di Power BI vogliono una risposta:

* Quanti valori sono disponibili per questa colonna?

Si tratta di una domanda semplice quando si ha di fronte una tabella, ma DAX la affronta in modo diverso, in particolare quando esiste una relazione tra tabelle.

Ad esempio, Power BI e DAX includono valori che non sono indicizzati correttamente tra loro. Se la relazione in ingresso viene interrotta, DAX aggiunge una nuova riga alla tabella correlata che ha celle vuote in ogni campo e la collega alla nuova riga non indicizzata per garantire l'integrità referenziale. Se la funzione contiene righe vuote, come accade spesso quando si usa **ALL**, le righe vuote verranno quindi incluse nel numero di valori per la colonna.

È anche possibile creare intere tabelle calcolate usando funzioni DAX. Le tabelle calcolate create usando DAX necessitano di una funzione **NAME** e una funzione **TABLE**. Le tabelle calcolate possono essere usate come qualsiasi altra tabella, anche per quanto riguarda la definizione di relazioni.

> Contenuto video fornito da [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

