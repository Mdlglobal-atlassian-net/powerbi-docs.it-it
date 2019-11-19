---
title: Esempi di espressioni nel Generatore report di Power BI
description: Le espressioni sono usate di frequente nei report impaginati del Generatore report impaginati di Power BI per controllare il contenuto e l'aspetto del report.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 06847956eae4dfefc7cff75b5a360fbb8b892c39
ms.sourcegitcommit: d173e22f5a3e76717adfaa573ea391bde0338ffe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728553"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Esempi di espressioni nel Generatore report di Power BI
Le espressioni sono usate di frequente nei report impaginati del Generatore report impaginati di Power BI per controllare il contenuto e l'aspetto del report. Le espressioni vengono scritte in Microsoft Visual Basic e possono usare funzioni predefinite, codice personalizzato, variabili di report e gruppi e variabili definite dall'utente. Le espressioni iniziano con un segno di uguale (=).   

In questo argomento sono riportati esempi di espressioni che è possibile usare per le attività comuni in un report.  
  
-   [Funzioni di Visual Basic](#VisualBasicFunctions) Esempi di funzioni di data, stringa, conversione e condizionali di Visual Basic.  
  
-   [Funzioni di report](#ReportFunctions) Esempi di aggregazioni e altre funzioni di report predefinite.  
  
-   [Aspetto dei dati del report](#AppearanceofReportData) Esempi di modifica dell'aspetto di un report.  
  
-   [Proprietà](#Properties) Esempi di impostazione delle proprietà degli elementi dei report per il controllo del formato o della visibilità.  
  
-   [Parametri](#Parameters) Esempi d'uso dei parametri in un'espressione.  
  
-   [Codice personalizzato](#CustomCode) Esempi di codice personalizzato incorporato.  
  
Per altre informazioni su espressioni semplici e complesse, su dove è possibile usare le espressioni e sui tipi di riferimenti che è possibile includere in un'espressione, vedere gli argomenti contenuti in [Espressioni nel Generatore report di Power BI](report-builder-expressions.md). 
  
## <a name="functions"></a>Funzioni  
 Molte espressioni incluse in un report contengono funzioni. È possibile formattare i dati, applicare la logica e accedere ai metadati del report usando le funzioni. È possibile scrivere espressioni che usano funzioni dalla libreria di runtime di Microsoft Visual Basic e dagli spazi dei nomi `xref:System.Convert` e `xref:System.Math`. È possibile aggiungere i riferimenti alle funzioni nel codice personalizzato. È anche possibile usare le classi di Microsoft .NET Framework, tra cui `xref:System.Text.RegularExpressions`.  
  
##  <a name="VisualBasicFunctions"></a> Funzioni di Visual Basic  
 È possibile usare le funzioni di Visual Basic per manipolare i dati visualizzati nelle caselle di testo o usati per parametri, proprietà o altre aree del report. Questa sezione include esempi che illustrano alcune funzioni. Per altre informazioni, vedere [Membri della libreria di runtime di Visual Basic](https://go.microsoft.com/fwlink/?LinkId=198941) su MSDN.  
  
 .NET Framework offre numerose opzioni di formato personalizzato, ad esempio per formati di data specifici. Per altre informazioni, vedere [Formattazione di tipi](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Funzioni matematiche  
  
-   La funzione **Round** consente di arrotondare i numeri all'intero più vicino. L'espressione seguente consente di arrotondare 1,3 a 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     È anche possibile scrivere un'espressione per arrotondare un valore a un multiplo specificato, simile alla funzione **MRound** di Excel. Moltiplicare il valore per un fattore che crea un numero intero, arrotondare il numero e quindi dividere per lo stesso fattore. Ad esempio, per arrotondare 1,3 al multiplo più vicino di 0,2 (1,4), usare l'espressione seguente:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="DateFunctions"></a> Funzioni di data  
  
-   La funzione **Today** visualizza la data corrente. Questa espressione può essere usata in una casella di testo per visualizzare la data nel report o in un parametro per filtrare i dati in base alla data corrente.  
  
    ```  
    =Today()  
    ```  
  
-   Usare la funzione **DateInterval** per estrarre una parte specifica di una data. Di seguito sono elencati alcuni parametri di **DateInterval** validi:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Ad esempio, l'espressione seguente visualizzerà il numero della settimana nell'anno corrente per la data odierna:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   La funzione **DateAdd** consente di fornire un intervallo di date basato su un singolo parametro. L'espressione seguente restituisce una data sei mesi successiva alla data di un parametro denominato *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   La funzione **Year** visualizza l'anno di una data specifica. È possibile usare questa funzione per raggruppare le date oppure per visualizzare l'anno come etichetta di un set di date. L'espressione seguente restituisce l'anno di un gruppo specifico di date degli ordini di vendita. Per modificare le date è anche possibile usare la funzione **Month** e altre funzioni. Per altre informazioni, vedere la documentazione di Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   È possibile combinare le funzioni in un'espressione per personalizzare il formato. L'espressione seguente cambia il formato di una data nel formato mese-giorno-anno nel numero mese-settimana-numero settimana. Ad esempio, 12/23/2009 in Dicembre Settimana 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Questa espressione usata come campo calcolato in un set di dati può essere usata in un grafico per aggregare i valori per settimana all'interno di ogni mese.  
  
-   L'espressione seguente formatta il valore SellStartDate nel formato MMM-AA. Il campo SellStartDate è un tipo di dati datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   L'espressione seguente formatta il valore SellStartDate nel formato gg/MM/aaaa. Il campo SellStartDate è un tipo di dati datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   La funzione **CDate** converte il valore in una data. La funzione **Now** restituisce un valore di data contenente la data e l'ora corrente in base al sistema. **DateDiff** restituisce un valore Long che specifica il numero di intervalli di tempo tra due valori di data.  
  
     L'esempio seguente visualizza la data di inizio dell'anno corrente  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   L'esempio seguente visualizza la data di inizio del mese precedente in base al mese corrente.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   L'espressione seguente genera gli anni di intervallo tra SellStartDate e LastReceiptDate. Questi campi si trovano in due diversi set di dati DataSet1 e DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   La funzione **DatePart** restituisce un valore Integer contenente il componente specificato di un determinato valore di data. L'espressione seguente restituisce l'anno del primo valore di SellStartDate in DataSet1. L'ambito del set di dati è specificato poiché sono presenti più set di dati nel report.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   La funzione **DateSerial** restituisce un valore di data che rappresenta un anno, un mese e un giorno specificati, con le informazioni sull'ora impostate su mezzanotte. L'esempio seguente visualizza la data di fine del mese precedente in base al mese corrente.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Le espressioni seguenti visualizzano diverse date, in base a un valore di parametro di data selezionato dall'utente.  
  
|Descrizione esempio|Esempio|  
|-------------------------|-------------|  
|Yesterday|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Due giorni fa|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Un mese fa|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Due mesi fa|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Un anno fa|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Due anni fa|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="StringFunctions"></a> Funzioni di stringa  
  
-   Combinare più campi usando operatori di concatenazione e costanti di Visual Basic. L'espressione seguente restituisce due campi, ognuno in una riga separata nella stessa casella di testo:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Formattare date e numeri in una stringa con la funzione **Format**. L'espressione seguente visualizza i valori dei parametri *StartDate* ed *EndDate* nel formato di data estesa:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Se la casella di testo contiene solo una data o un numero, è necessario usare la proprietà Format della casella di testo per applicare la formattazione anziché la funzione **Format** all'interno della casella di testo.  
  
-   Le funzioni **Right**, **Len** e **InStr** consentono di restituire una sottostringa, ad esempio tagliando *DOMINIO*\\*nome utente* nel nome utente. L'espressione seguente restituisce la parte della stringa a destra di un carattere barra rovesciata (\\) da un parametro denominato *User*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     L'espressione seguente restituisce lo stesso valore di quella precedente, usando i membri della classe `xref:System.String` di .NET Framework anziché le funzioni di Visual Basic:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Visualizzare i valori selezionati di un parametro multivalore. L'esempio seguente usa la funzione **Join** per concatenare i valori selezionati del parametro *MySelection* in un'unica stringa che può essere impostata come espressione per il valore di una casella di testo in un elemento del report:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     L'esempio seguente esegue la stessa operazione dell'esempio precedente e visualizza una stringa di testo prima dell'elenco di valori selezionati.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   Le funzioni **Regex** di `xref:System.Text.RegularExpressions` di .NET Framework sono utili per modificare il formato di stringhe esistenti, ad esempio formattando un numero di telefono. L'espressione seguente usa la funzione **Replace** per modificare il formato di un numero telefonico di dieci cifre in un campo da "*nnn*-*nnn*-*nnnn*" in "(*nnn*) *nnn*-*nnnn*":  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Verificare che il valore di Fields!Phone.Value non contenga spazi aggiuntivi e sia di tipo `xref:System.String`.  
  
### <a name="lookup"></a>Lookup  
  
-   Specificando un campo chiave, è possibile usare la funzione **Lookup** per recuperare un valore da un set di dati per una relazione uno-a-uno, ad esempio una coppia chiave-valore. L'espressione seguente visualizza il nome del prodotto da un set di dati ("Prodotto"), a condizione che sia specificato l'identificatore del prodotto:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Specificando un campo chiave, è possibile usare la funzione **LookupSet** per recuperare un set di valori da un set di dati per una relazione uno-a-molti. Ad esempio, una persona può avere più numeri di telefono. Nell'esempio seguente si supponga che il set di dati PhoneList contenga un identificatore persona e un numero di telefono in ogni riga. **LookupSet** restituisce una matrice di valori. L'espressione seguente combina i valori restituiti in un'unica stringa e visualizza l'elenco di numeri di telefono della persona specificata da ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="ConversionFunctions"></a> Funzioni di conversione  
 È possibile usare le funzioni di Visual Basic per convertire un campo di un tipo di dati in un tipo di dati diverso. Le funzioni di conversione possono essere usate per convertire il tipo di dati predefinito di un campo nel tipo di dati necessario per i calcoli oppure per combinare testo.  
  
-   L'espressione seguente converte la costante 500 nel tipo Decimal per poterla confrontare con un tipo di dati money di Transact-SQL nel campo del valore di un'espressione di filtro.  
  
    ```  
    =CDec(500)  
    ```  
  
-   L'espressione seguente visualizza il numero di valori selezionati per il parametro multivalore *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="DecisionFunctions"></a> Funzioni di decisione  
  
-   La funzione **Iif** restituisce uno dei due valori a seconda che l'espressione sia true o meno. L'espressione seguente usa la funzione **Iif** per restituire un valore booleano **True** se il valore di `LineTotal` supera 100. In caso contrario, restituisce **False**:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Usare più funzioni **IIF** (chiamate anche "IIF annidati") per restituire uno dei tre valori a seconda del valore di `PctComplete`. L'espressione seguente può essere inserita nel colore di riempimento di una casella di testo per modificare il colore di sfondo a seconda del valore nella casella di testo.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     I valori maggiori o uguali a 10 vengono visualizzati con uno sfondo verde, i valori compresi tra 1 e 9 con uno sfondo blu e i valori minori di 1 con uno sfondo rosso.  
  
-   La stessa funzionalità può essere ottenuta usando la funzione **Switch**. La funzione **Switch** è utile in presenza di tre o più condizioni da verificare. La funzione **Switch** restituisce il valore associato alla prima espressione in una serie che restituisce true:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     I valori maggiori o uguali a 10 vengono visualizzati con uno sfondo verde, i valori compresi tra 1 e 9 con uno sfondo blu, i valori uguali a 1 con uno sfondo giallo e i valori uguali a 0 o minori con uno sfondo rosso.  
  
-   Verificare il valore del campo `ImportantDate` e restituire "Red" (Rosso) se più vecchio di una settimana e "Blue" (Blu) in caso contrario. Questa espressione può essere usata per controllare la proprietà Color di una casella di testo in un elemento del report:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Verificare il valore del campo `PhoneNumber` e restituire "No Value" (Nessun valore) se **null** (**Nothing** in Visual Basic); in caso contrario, restituire il valore del numero di telefono. Questa espressione può essere usata per controllare il valore di una casella di testo in un elemento del report.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Verificare il valore del campo `Department` e restituire il nome di un sottoreport oppure **null** (**Nothing** in Visual Basic). Questa espressione può essere usata per i sottoreport drill-through condizionali.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Verificare se il valore di un campo è Null. Questa espressione può essere usata per controllare la proprietà **Hidden** di un elemento del report immagine. Nell'esempio seguente l'immagine specificata dal campo [LargePhoto] viene visualizzata solo se il valore del campo non è Null.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   La funzione **MonthName** restituisce un valore stringa che contiene il nome del mese specificato. L'esempio seguente visualizza NA (ND) nel campo Mese quando il campo contiene il valore 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="ReportFunctions"></a> Funzioni di report  
 In un'espressione è possibile aggiungere un riferimento a funzioni di report aggiuntive che modificano i dati in un report. Questa sezione include esempi di due di queste funzioni. 
  
###  <a name="Sum"></a> Sum  
  
-   La funzione **Sum** somma i valori in un gruppo o un'area dati. Questa funzione può essere utile nell'intestazione o nel piè di pagina di un gruppo. L'espressione seguente visualizza la somma dei dati nel gruppo o nell'area dati Order (Ordine):  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   È anche possibile usare la funzione **Sum** per i calcoli di aggregazione condizionale. Ad esempio, se un set di dati include un campo denominato Stato con i valori possibili Not Started (Non avviato), Started (Avviato), Finished (Completato), l'espressione seguente, inserita in un'intestazione di gruppo, calcola la somma aggregata solo per il valore Finished (Completato):  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="RowNumber"></a> RowNumber  
  
-   La funzione **RowNumber**, usata in una casella di testo all'interno di un'area dati, visualizza il numero di riga per ogni istanza della casella di testo in cui è presente l'espressione. Questa funzione può essere utile per numerare le righe di una tabella. Può essere utile anche per attività più complesse, ad esempio l'inserimento di interruzioni di pagina in base al numero di righe. Per altre informazioni, vedere [Interruzioni di pagina](#PageBreaks) in questo argomento.  
  
     L'ambito specificato per **RowNumber** controlla l'inizio della rinumerazione. La parola chiave **Nothing** indica che il conteggio inizierà dalla prima riga dell'area dati più esterna. Per iniziare il conteggio all'interno di aree dati nidificate, usare il nome dell'area dati. Per iniziare il conteggio all'interno di un gruppo, usare il nome del gruppo.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="AppearanceofReportData"></a> Aspetto dei dati del report  
 È possibile usare le espressioni per modificare l'aspetto dei dati in un report. Ad esempio, è possibile visualizzare i valori di due campi in una singola casella di testo, visualizzare informazioni sul report o controllare il modo in cui vengono inserite le interruzioni di pagina nel report.  
  
###  <a name="PageHeadersandFooters"></a> Intestazioni e piè di pagina  
 Quando si progetta un report, è possibile che si voglia visualizzare il nome del report e il numero di pagina nel piè di pagina del report. A tale scopo, è possibile usare le espressioni seguenti:  
  
-   L'espressione seguente restituisce il nome del report e l'ora di esecuzione. Può essere inserita in una casella di testo nel piè di pagina del report o nel corpo del report. L'ora è formattata con la stringa di formattazione per la data breve di .NET Framework:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   L'espressione seguente, inserita in una casella di testo nel piè di pagina di un report, fornisce il numero di pagina e le pagine totali del report:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 Gli esempi seguenti descrivono come visualizzare il primo e l'ultimo valore di una pagina nell'intestazione di pagina, come avviene in un elenco di directory. L'esempio presuppone la presenza di un'area dati che contiene una casella di testo denominata `LastName`.  
  
-   L'espressione seguente, inserita in una casella di testo a sinistra dell'intestazione di pagina, restituisce il primo valore della casella di testo `LastName` nella pagina:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   L'espressione seguente, inserita in una casella di testo a destra dell'intestazione di pagina, restituisce l'ultimo valore della casella di testo `LastName` nella pagina:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 L'esempio seguente descrive come visualizzare un totale di pagine. L'esempio presuppone la presenza di un'area dati che contiene una casella di testo denominata `Cost`.  
  
-   L'espressione seguente, inserita nell'intestazione o nel piè di pagina, fornisce la somma dei valori nella casella di testo `Cost` per la pagina:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  È possibile fare riferimento a un solo elemento del report per ogni espressione in un'intestazione o in un piè di pagina. È anche possibile fare riferimento al nome della casella di testo, ma non all'espressione dati effettiva all'interno della casella di testo, nelle espressioni dell'intestazione e del piè di pagina.  
  
###  <a name="PageBreaks"></a> Interruzioni di pagina  
 In alcuni report è possibile che si voglia inserire un'interruzione di pagina alla fine di un numero specificato di righe in alternativa o in aggiunta alle interruzioni inserire nei gruppi o negli elementi del report. A tale scopo, creare un gruppo che contiene i gruppi o i record di dettaglio desiderati, aggiungere un'interruzione di pagina al gruppo e quindi aggiungere un'espressione di raggruppamento per raggruppare in base a un numero specificato di righe.  
  
-   L'espressione seguente, inserita nell'espressione di raggruppamento, assegna un numero a ogni set di 25 righe. Quando viene definita un'interruzione di pagina per il gruppo, questa espressione inserisce un'interruzione di pagina ogni 25 righe.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Per consentire all'utente di impostare un valore per il numero di righe per pagina, creare un parametro denominato `RowsPerPage` e basare l'espressione di raggruppamento sul parametro, come illustrato nell'espressione seguente:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="Properties"></a> Proprietà  
 Le espressioni non vengono usate soltanto per visualizzare i dati nelle caselle di testo. Possono essere usate anche per modificare il modo in cui le proprietà vengono applicate agli elementi del report. È possibile modificare le informazioni sullo stile per un elemento del report o modificarne la visibilità.  
  
###  <a name="Formatting"></a> Formattazione  
  
-   L'espressione seguente, usata nella proprietà Color di una casella di testo, modifica il colore del testo in base al valore del campo `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     È anche possibile usare la variabile oggetto di Visual Basic `Me`. Questa variabile rappresenta un altro modo per fare riferimento al valore di una casella di testo.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   L'espressione seguente, usata nella proprietà BackgroundColor di un elemento del report in un'area dati, alterna il colore di sfondo di ogni riga tra verde chiaro e bianco:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Se si usa un'espressione per un ambito specificato, potrebbe essere necessario indicare il set di dati per la funzione di aggregazione:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  I colori disponibili provengono dall'enumerazione KnownColor di .NET Framework.  
  
### <a name="chart-colors"></a>Colori del grafico  
 Per specificare i colori per un grafico forma, è possibile usare un codice personalizzato per controllare l'ordine in cui i colori vengono mappati ai valori dei punti dati. Ciò consente di usare colori coerenti per più grafici con gli stessi gruppi di categorie. 
  
###  <a name="Visibility"></a> Visibilità  
 È possibile visualizzare e nascondere gli elementi in un report usando le proprietà di visibilità per l'elemento del report. In un'area dati, ad esempio una tabella, è possibile nascondere inizialmente le righe di dettaglio in base al valore in un'espressione.  
  
-   L'espressione seguente, usata per la visibilità iniziale delle righe di dettaglio in un gruppo, visualizza le righe di dettaglio per tutte le vendite che superano il 90% nel campo `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   L'espressione seguente, impostata nella proprietà Hidden di una tabella, visualizza la tabella solo se contiene più di 12 righe:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   L'espressione seguente, impostata nella proprietà **Hidden** di una colonna, visualizza la colonna solo se il campo esiste nel set di dati del report dopo che i dati vengono recuperati dall'origine dati:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="Hyperlinks"></a> URL  
 È possibile personalizzare gli URL usando i dati del report e controllare in modo condizionale l'aggiunta degli URL come azione per una casella di testo.  
  
-   L'espressione seguente, usata come azione in una casella di testo, genera un URL personalizzato che specifica il campo del set di dati `EmployeeID` come parametro URL.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   L'espressione seguente controlla in modo condizionale se aggiungere un URL in una casella di testo. Questa espressione dipende da un parametro denominato `IncludeURLs` che consente a un utente di decidere se includere gli URL attivi in un report. Questa espressione viene impostata come azione in una casella di testo. Impostando il parametro su False e quindi visualizzando il report, è possibile esportare il report Microsoft Excel senza collegamenti ipertestuali.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="ReportData"></a> Dati del report  
 Le espressioni possono essere usate per modificare i dati usati nel report. È possibile fare riferimento a parametri e ad altre informazioni del report. È anche possibile modificare la query usata per recuperare i dati per il report.  
  
###  <a name="Parameters"></a> Parametri  
 È possibile usare le espressioni in un parametro per variare il valore predefinito per il parametro. Ad esempio, è possibile usare un parametro per filtrare i dati di un utente specifico in base all'ID utente usato per eseguire il report.  
  
-   L'espressione seguente, usata come valore predefinito per un parametro, recupera l'ID utente della persona che esegue il report:  
  
    ```  
    =User!UserID  
    ```  
  
-   Per fare riferimento a un parametro in un parametro di query, un'espressione di filtro, una casella di testo o un'altra area del report, usare la raccolta globale **Parameters**. Questo esempio presuppone che il parametro sia denominato *Department*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   I parametri possono essere creati in un report ma impostati come nascosti. Quando il report viene eseguito nel server di report, il parametro non viene visualizzato nella barra degli strumenti e il lettore del report non può modificare il valore predefinito. È possibile usare un parametro nascosto impostato su un valore predefinito come costante personalizzata. È possibile usare questo valore in qualsiasi espressione, inclusa un'espressione di campo. L'espressione seguente identifica il campo specificato dal valore del parametro predefinito per il parametro denominato *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="CustomCode"></a> Codice personalizzato  
 È possibile usare codice personalizzato incorporato in un report. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Uso di variabili di gruppo per l'aggregazione personalizzata  
 È possibile inizializzare il valore di una variabile di gruppo locale per l'ambito di un determinato gruppo e quindi includere un riferimento alla variabile nelle espressioni. Uno dei modi in cui è possibile usare una variabile di gruppo con codice personalizzato consiste nell'implementare un'aggregazione personalizzata. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Eliminazione di valori Null o zero in fase di esecuzione  
 Alcuni valori in un'espressione possono restituire valori Null o non definiti in fase di elaborazione del report. Ciò può causare errori di run-time che visualizzano **#Error** nella casella di testo anziché l'espressione valutata. La funzione **IIF** è particolarmente sensibile a questo comportamento perché, a differenza di un'istruzione If-Then-Else, viene valutata ogni parte dell'istruzione **IIF** (incluse le chiamate di funzione) prima di essere passata alla routine che verifica il valore **true** o **false**. L'istruzione `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` genera **#Error** nel report visualizzabile se `Fields!Sales.Value` è NOTHING.  
  
 Per evitare questa condizione, usare una delle strategie seguenti:  
  
-   Impostare il numeratore su 0 e il denominatore su 1 se il valore del campo B è 0 o non definito. In caso contrario, impostare il numeratore sul valore del campo A e il denominatore sul valore del campo B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Usare una funzione di codice personalizzato per restituire il valore dell'espressione. L'esempio seguente restituisce la differenza percentuale tra un valore corrente e un valore precedente. Può essere usato per calcolare la differenza tra due valori successivi e consente di gestire il caso limite del primo confronto (quando non è presente alcun valore precedente) e i casi in cui il valore precedente o il valore corrente è **null** (**Nothing** in Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     L'espressione seguente illustra come chiamare questo codice personalizzato da una casella di testo per il contenitore "ColumnGroupByYear" (gruppo o area dati).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Ciò consente di evitare le eccezioni di run-time. È ora possibile usare un'espressione come `=IIF(Me.Value < 0, "red", "black")` nella proprietà **Color** della casella di testo per controllare in modo condizionale il testo visualizzato in base ai valori maggiori o minori di 0.  
  
## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
