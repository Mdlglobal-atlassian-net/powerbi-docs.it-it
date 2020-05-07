---
title: Usare i parametri a cascata nei report impaginati
description: Linee guida per la progettazione di report impaginati usando i parametri a cascata.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 90f501b257313c48cbef13517747ff83cd9ea9d1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920775"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Usare i parametri a cascata nei report impaginati

Questo articolo è rivolto agli autori di report che progettano [report impaginati](../paginated-reports/paginated-reports-report-builder-power-bi.md) di Power BI. Offre scenari per la progettazione di parametri a cascata. I parametri a cascata sono parametri di report con dipendenze. Quando l'utente di un report seleziona il valore (o i valori) di un parametro, esso viene usato per impostare i valori disponibili per un altro parametro.

> [!NOTE]
> Questo articolo non include un'introduzione ai parametri a cascata e alla relativa configurazione. Se non si ha familiarità con i parametri a cascata, è consigliabile leggere prima di tutto [Aggiungere parametri a cascata a un report (Generatore report e SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Scenari di progettazione

Esistono due scenari di progettazione per l'uso dei parametri a cascata. Possono essere usati in modo efficace per:

- Filtrare _set di elementi di grandi dimensioni_
- Presentare elementi _pertinenti_

### <a name="example-database"></a>Esempio di database

Gli esempi presentati in questo articolo si basano su un database SQL di Azure. Il database registra le operazioni di vendita e contiene varie tabelle in cui vengono archiviati rivenditori, prodotti e ordini cliente.

Una tabella denominata **Reseller**, contenente molte migliaia di record, archivia un record per ogni rivenditore. La tabella **Reseller** contiene queste colonne:

- ResellerCode (Integer)
- ResellerName
- Country-Region
- State-Province
- city
- PostalCode

È presente anche una tabella denominata **Sales**. La tabella archivia i record degli ordini cliente e ha una relazione di chiave esterna con la tabella **Reseller** nella colonna **ResellerCode**.

### <a name="example-requirement"></a>Esempio di richiesta

Viene richiesto di sviluppare un report Profilo del rivenditore. Il report deve essere progettato in modo da visualizzare le informazioni relative a un singolo rivenditore. Non è appropriato richiedere all'utente del report di immettere i codici dei rivenditori poiché è raro che questi vengano memorizzati.

## <a name="filter-large-sets-of-items"></a>Filtrare set di elementi di grandi dimensioni

Verranno ora esaminati tre esempi che consentono di limitare i set di elementi disponibili di grandi dimensioni, come i rivenditori, ovvero:

- [Filtrare in base alle colonne correlate](#filter-by-related-columns)
- [Filtrare in base a una colonna di raggruppamento](#filter-by-a-grouping-column)
- [Filtrare in base ai criteri di ricerca](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrare in base alle colonne correlate

In questo esempio l'utente del report interagisce con cinque parametri del report. Deve selezionare il paese, la provincia, la città e quindi il codice postale. Un parametro finale elenca quindi i rivenditori presenti in quella posizione geografica.

![L'immagine illustra cinque parametri del report: paese, provincia, città, codice postale e rivenditore. Vengono impostati i valori dei primi quattro e l'elenco dei rivenditori viene filtrato in modo da visualizzare solo quattro elementi.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Di seguito viene illustrato come sviluppare i parametri a cascata:

1. Creare i cinque parametri del report, ordinati nella sequenza corretta.
2. Creare il set di dati **CountryRegion** che recupera i singoli valori dei paesi usando l'istruzione di query seguente:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Creare il set di dati **StateProvince** che recupera i singoli valori delle province per il paese selezionato usando l'istruzione di query seguente:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Creare il set di dati **City** che recupera i singoli valori delle città per il paese e la provincia selezionati usando l'istruzione di query seguente:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Continuare in questo modo per creare il set di dati **PostalCode**.
6. Creare il set di dati **Reseller** per recuperare tutti i rivenditori per i valori geografici selezionati usando l'istruzione di query seguente:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Per ogni set di dati, ad eccezione del primo, eseguire il mapping dei parametri di query ai parametri del report corrispondenti.

> [!NOTE]
> Tutti i parametri di query (preceduti dal simbolo @) indicati in questi esempi possono essere incorporati all'interno di istruzioni SELECT o passati alle stored procedure.
>
> Le stored procedure costituiscono in genere un approccio migliore alla progettazione. I piani di query sono infatti memorizzati nella cache per garantire un'esecuzione più rapida. Esse consentono inoltre di sviluppare una logica più sofisticata, se necessario. Attualmente non sono tuttavia supportate per le origini dati relazionali del gateway, ovvero SQL Server, Oracle e Teradata.
>
> Infine, è consigliabile assicurarsi sempre della presenza di indici adeguati per supportare un recupero dati efficiente. In caso contrario, il popolamento dei parametri del report potrebbe risultare lento e sovraccaricare il database. Per altre informazioni sull'indicizzazione di SQL Server, vedere [Architettura e guida per la progettazione degli indici di SQL Server](/sql/relational-databases/sql-server-index-design-guide?view=sql-server-2017).

### <a name="filter-by-a-grouping-column"></a>Filtrare in base a una colonna di raggruppamento

In questo esempio l'utente del report interagisce con un parametro del report per selezionare la prima lettera del rivenditore. Un secondo parametro elenca quindi i rivenditori quando il nome inizia con la lettera selezionata.

![L'immagine illustra due parametri del report: gruppo e rivenditore. Il valore del primo parametro è impostato sulla lettera A e l'elenco dei rivenditori viene filtrato in modo da visualizzare molti elementi che iniziano con questa lettera.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Di seguito viene illustrato come sviluppare i parametri a cascata:

1. Creare i parametri del report **ReportGroup** e **Reseller**, ordinati nella sequenza corretta.
2. Creare il set di dati **ReportGroup** per recuperare le prime lettere usate da tutti i rivenditori usando l'istruzione di query seguente:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Creare il set di dati **Reseller** per recuperare tutti i rivenditori il cui nome inizia con la lettera selezionata usando l'istruzione di query seguente:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Eseguire il mapping del parametro di query del set di dati **Reseller** al parametro del report corrispondente.

Un modo più efficiente consiste nell'aggiungere la colonna di raggruppamento alla tabella **Reseller**. Se è salvata in modo permanente e indicizzata, restituisce il risultato migliore. Per altre informazioni, vedere [Specificare le colonne calcolate in una tabella](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Questa tecnica può offrire un potenziale ancora maggiore. Si osservi lo script seguente che aggiunge una nuova colonna di raggruppamento per filtrare i rivenditori in base a _gruppi di lettere predefiniti_. Crea anche un indice per recuperare in modo efficiente i dati richiesti dai parametri del report.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrare in base ai criteri di ricerca

In questo esempio l'utente del report interagisce con un parametro del report per immettere un criterio di ricerca. Un secondo parametro elenca quindi i rivenditori quando il nome contiene il criterio.

![L'immagine illustra due parametri del report: ricerca e rivenditore. Il valore del primo parametro è impostato sul testo "red" e l'elenco dei rivenditori viene filtrato in modo da visualizzare diversi elementi che contengono il testo.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Di seguito viene illustrato come sviluppare i parametri a cascata:

1. Creare i parametri del report **Search** e **Reseller**, ordinati nella sequenza corretta.
2. Creare il set di dati **Reseller** per recuperare tutti i rivenditori il cui nome contiene il testo di ricerca usando l'istruzione di query seguente:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Eseguire il mapping del parametro di query del set di dati **Reseller** al parametro del report corrispondente.

> [!TIP]
> È possibile migliorare ulteriormente questa progettazione per offrire maggiore controllo agli utenti del report. Si può infatti consentire agli utenti di definire un valore dei criteri di ricerca. Ad esempio, il valore di ricerca "red%" filtrerà l'elenco in modo da visualizzare i rivenditori i cui nomi _iniziano_ con i caratteri "red".
>
> Per altre informazioni, vedere [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql?view=sql-server-ver15#using-the--wildcard-character).

Di seguito è illustrato come è possibile consentire agli utenti del report di definire i propri criteri.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Molti professionisti che non si occupano di database, tuttavia, non conoscono il carattere jolly percentuale (%). Hanno invece familiarità con il carattere asterisco (*). Modificando la clausola WHERE, è possibile consentire l'uso di questo carattere.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Presentare elementi pertinenti

In questo scenario è possibile usare i dati della tabella dei fatti per limitare i valori disponibili. Agli utenti del report verranno presentati gli elementi in cui è stata registrata attività.

In questo esempio l'utente del report interagisce con tre parametri del report. I primi due impostano un intervallo di date relativo alle date degli ordini cliente. Il terzo parametro elenca quindi i rivenditori presso i quali sono stati creati ordini durante questo periodo di tempo.

![L'immagine illustra tre parametri del report: data di inizio ordine, data di fine ordine e rivenditore. I due parametri di data sono impostati per il mese di gennaio 2020 e l'elenco dei rivenditori viene filtrato in modo da visualizzare molti elementi che rappresentano i rivenditori che hanno effettuato ordini durante il mese.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Di seguito viene illustrato come sviluppare i parametri a cascata:

1. Creare i parametri del report **OrderDateStart**, **OrderDateEnd** e **Reseller**, ordinati nella sequenza corretta.
2. Creare il set di dati **Reseller** per recuperare tutti i rivenditori che hanno creato ordini nell'intervallo di date, usando l'istruzione di query seguente:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Consigli

È consigliabile progettare i report con parametri a cascata, ove possibile. Essi infatti:

- Offrono esperienze utili e intuitive agli utenti dei report
- Sono efficienti, poiché recuperano set più piccoli dei valori disponibili

Per assicurarsi di ottimizzare le origini dati:

- Usare le stored procedure, ove possibile
- Aggiungere indici appropriati per un recupero dati efficiente
- Materializzare i valori delle colonne e persino le righe per evitare costose valutazioni in fase di query

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Parametri dei report in Power BI Report Builder](../paginated-reports/report-builder-parameters.md)
- [Aggiungere parametri a cascata a un report (Generatore report e SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com)
