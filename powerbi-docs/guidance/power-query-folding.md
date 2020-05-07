---
title: Linee guida per la riduzione della query in Power BI Desktop
description: Linee guida per ottenere la riduzione della query di Power Query in Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "75622149"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Linee guida per la riduzione della query in Power BI Desktop

Questo articolo è destinato agli autori di modelli di dati in Power BI Desktop. Fornisce indicazioni sulle procedure consigliate per quando e come è possibile ottenere la riduzione della query di Power Query.

La _riduzione della query_ è la possibilità per una query di Power Query di generare una singola istruzione di query che recuperi e trasformi i dati di origine. Per altre informazioni, vedere [Riduzione della query di Power Query](/power-query/power-query-folding).

## <a name="guidance"></a>Materiale sussidiario

Le linee guida per la riduzione della query variano in base alla modalità del modello.

Per una tabella **DirectQuery** o con modalità di archiviazione **Doppia**, la query di Power Query deve ottenere la riduzione della query.

Per una tabella di **importazione**, potrebbe essere possibile ottenere la riduzione della query. Quando la query è basata su un'origine relazionale e se è possibile costruire una singola istruzione SELECT, si ottengono le _migliori prestazioni di aggiornamento dei dati_ assicurandosi che venga eseguita la riduzione della query. Se il motore mashup di Power Query è ancora necessario per elaborare le trasformazioni, è necessario cercare di ridurre al minimo il lavoro necessario, soprattutto per i set di dati di grandi dimensioni.

L'elenco puntato seguente fornisce indicazioni specifiche sulle procedure consigliate.

- **Delegare quanto più possibile l'elaborazione all'origine dati**: quando non è possibile ridurre tutti i passaggi di una query di Power Query, individuare il passaggio che impedisce la riduzione della query. Quando possibile, spostare i passaggi successivi in una posizione precedente nella sequenza in modo che sia possibile eseguirne il factoring nella riduzione della query. Si noti che il motore mashup di Power Query può essere sufficientemente intelligente da riordinare i passaggi della query quando genera la query di origine.

    Per un'origine dati relazionale, se il passaggio che impedisce la riduzione della query può essere eseguito in una singola istruzione SELECT o all'interno della logica procedurale di una stored procedure, valutare la possibilità di usare una query SQL nativa, come descritto di seguito.

- **Usare una query SQL nativa**: quando una query di Power Query recupera dati da un'origine relazionale, è possibile per le stesse origini usare una query SQL nativa. La query può essere in effetti qualsiasi istruzione valida, inclusa l'esecuzione di una stored procedure. Se l'istruzione produce più set di risultati, verrà restituito solo il primo. I parametri possono essere dichiarati nell'istruzione ed è consigliabile usare la funzione M [Value.NativeQuery](/powerquery-m/value-nativequery). Questa funzione è stata progettata per passare i valori dei parametri in modo sicuro e comodo. È importante comprendere che il motore mashup di Power Query non è in grado di ridurre i passaggi della query successivi e quindi si dovrebbe includere tutta la logica di trasformazione (o la maggior parte possibile) nell'istruzione della query nativa.

    Quando si usano query SQL native, è necessario tenere presenti due considerazioni importanti:

    - Per una tabella del modello DirectQuery, la query deve essere un'istruzione SELECT e non può usare espressioni di tabella comune (CTE) o una stored procedure.
    - L'aggiornamento incrementale non può usare una query SQL nativa. Quindi, forza il motore mashup di Power Query a recuperare tutte le righe di origine e quindi ad applicare filtri per determinare le modifiche incrementali.

    > [!IMPORTANT]
    > Una query SQL nativa può eseguire potenzialmente molte altre operazioni oltre al recupero dei dati. È possibile eseguire qualsiasi istruzione valida (ed eventualmente più volte), inclusa una che modifica o elimina i dati. È importante applicare il principio dei privilegi minimi per assicurarsi che l'account usato per accedere al database disponga solo dell'autorizzazione di lettura per i dati richiesti.

- **Preparare e trasformare i dati nell'origine**: quando si rileva che alcuni passaggi della query di Power Query non possono essere ridotti, potrebbe essere possibile applicare le trasformazioni nell'origine dati. Per ottenere le trasformazioni, è possibile scrivere una vista di database che trasforma logicamente i dati di origine. In alternativa, si possono preparare e materializzare fisicamente i dati prima che Power BI esegua query su di essi. Un data warehouse relazionale è un ottimo esempio di dati preparati, in genere costituito da origini pre-integrate di dati dell'organizzazione.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- Articolo concettuale sulla [riduzione della query](/power-query/power-query-folding) di Power Query
- [Aggiornamento incrementale in Power BI Premium](../service-premium-incremental-refresh.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
