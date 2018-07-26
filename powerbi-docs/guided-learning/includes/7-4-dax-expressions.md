L'uso delle **variabili** è una componente fondamentale di un'espressione DAX.

![](media/7-4-dax-expressions/dax-variables_1.png)

È possibile definire una variabile in un punto qualsiasi di un'espressione DAX, usando la sintassi seguente:

    VARNAME = RETURNEDVALUE

Le variabili possono essere di qualsiasi tipo di dati, incluse intere tabelle.

Tenere presente che ogni volta che si fa riferimento a una variabile nell'espressione DAX, Power BI deve ricalcolarne il valore in base alla definizione. Per questo motivo, è consigliabile evitare di ripetere variabili in una funzione.

> Contenuto video fornito da [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

