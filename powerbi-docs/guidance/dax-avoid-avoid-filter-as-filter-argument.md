---
title: "DAX: Evitare l'uso di FILTER come argomento di filtro"
description: Informazioni sull'uso della funzione FILTER come argomento di filtro.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 6abcb77e3eb534e8b5d20c1d5567c117cbb97ffe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161433"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Evitare l'uso di FILTER come argomento di filtro

Chi si occupa della modellazione dei dati si trova spesso a scrivere espressioni DAX che devono essere valutate in un contesto di filtro modificato. È ad esempio possibile scrivere una definizione di misura per calcolare le vendite per i prodotti con margine elevato. Questo calcolo verrà descritto più avanti nell'articolo.

> [!NOTE]
> Questo articolo riguarda in particolare i calcoli dei modelli che applicano filtri alle tabelle di importazione.

Le funzioni DAX [CALCULATE](/dax/calculate-function-dax) e [CALCULATETABLE](/dax/calculatetable-function-dax) sono importanti e utili. Consentono di scrivere calcoli per la rimozione o l'aggiunta di filtri o per la modifica dei percorsi delle relazioni. A tale scopo, vengono passati argomenti di filtro che sono espressioni booleane, espressioni di tabella o funzioni di filtro speciali. In questo articolo verranno illustrate solo le espressioni booleane e di tabella.

Si consideri la definizione di misura seguente, che consente di calcolare le vendite dei prodotti rossi usando un'espressione di tabella. L'istruzione sostituisce i filtri applicati alla tabella **Product**.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

La funzione CALCULATE accetta un'espressione di tabella restituita dalla funzione DAX [FILTER](/dax/filter-function-dax) che valuta l'espressione filtro per ogni riga della tabella **Product**. Ottiene il risultato corretto, ovvero le vendite per i prodotti rossi. È tuttavia possibile ottenere lo stesso risultato in modo molto più efficiente usando un'espressione booleana.

Ecco una definizione di misura migliorata che usa un'espressione booleana invece dell'espressione di tabella. La funzione DAX [KEEPFILTERS](/dax/keepfilters-function-dax) garantisce che tutti i filtri esistenti applicati alla colonna **Color** vengano mantenuti, non sovrascritti.

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

È consigliabile passare gli argomenti di filtro come espressioni booleane, quando possibile. Ciò perché le tabelle dei modelli di importazione sono archivi di colonne in memoria. Sono ottimizzate in modo esplicito per filtrare efficacemente le colonne in questo modo.

Alle espressioni booleane usate come argomenti di filtro si applicano tuttavia alcune restrizioni, ovvero:

- Non possono confrontare colonne con altre colonne
- Non possono fare riferimento a una misura
- Non possono usare funzioni CALCULATE annidate
- Non possono usare funzioni che analizzano o restituiscono una tabella

Ciò significa che per i requisiti di filtro più complessi è necessario usare le espressioni di tabella.

Si consideri ora una definizione di misura diversa.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Un _prodotto con margine elevato_ (High Margin Product) è un prodotto il cui prezzo di listino è superiore al doppio del costo standard. In questo esempio è necessario usare la funzione FILTER. L'espressione filtro è infatti troppo complessa per un'espressione booleana.

Ecco un altro esempio. In questo caso si vuole calcolare le vendite, ma solo per i mesi che hanno ottenuto un profitto.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

Anche in questo esempio è necessario usare la funzione FILTER. Ciò perché è necessario valutare la misura **Profit** per eliminare i mesi in cui non è stato ottenuto un profitto. Non è possibile usare una misura in un'espressione booleana quando viene usata come argomento di filtro.

## <a name="recommendations"></a>Consigli

Per ottenere prestazioni ottimali, è consigliabile usare espressioni booleane come argomenti di filtro, quando possibile.

La funzione FILTER deve quindi essere usata solo quando è necessario. È possibile usarla per eseguire confronti tra colonne con filtro complesso. Questi confronti tra colonne possono includere:

- Misure
- Altre colonne
- Uso della funzione DAX [OR](/dax/or-function-dax) o dell'operatore logico OR (||)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Riferimento a Data Analysis Expressions (DAX)](/dax/)
- [Funzioni di filtro (DAX)](/dax/filter-function-dax)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
