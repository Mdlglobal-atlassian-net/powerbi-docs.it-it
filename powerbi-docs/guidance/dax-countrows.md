---
title: 'DAX: Usare COUNTROWS invece di COUNT'
description: Linee guida per l'uso delle funzioni COUNTROWS.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: fd3b50e9016298db8b692d6a2f3549b770f143e8
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700663"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: Usare COUNTROWS invece di COUNT

Gli autori di modelli di dati potrebbero avere l'esigenza di scrivere un'espressione DAX che conteggi le righe di una tabella. La tabella può essere una tabella del modello o un'espressione che restituisce una tabella.

Questa esigenza può essere soddisfatta in due modi. Per conteggiare i valori delle colonne, è possibile usare la funzione [COUNT](/dax/count-function-dax) oppure è possibile usare la funzione [COUNTROWS](/dax/countrows-function-dax) per conteggiare le righe della tabella. Entrambe le funzioni otterranno lo stesso risultato, a condizione che la colonna conteggiata non includa valori BLANK.

Nella definizione di misura seguente viene presentato un esempio. Calcola il numero di valori della colonna **OrderDate**.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Poiché la granularità della tabella **Sales** prevede una riga per ogni ordine di vendita e la colonna **OrderDate** non contiene valori BLANK, la misura restituirà un risultato corretto.

Tuttavia, la definizione della misura seguente è una soluzione migliore.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Esistono tre motivi per cui la seconda definizione della misura è migliore:

- Si tratta di una soluzione più efficiente, che consente quindi di ottenere prestazioni migliori.
- Non considera i valori BLANK contenuti in alcuna colonna della tabella.
- L'intenzione della formula è più chiara, al punto di essere autodescrittiva.

## <a name="recommendation"></a>Raccomandazione

Quando si intende conteggiare le righe di una tabella, è consigliabile usare sempre la funzione COUNTROWS.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Informazioni di riferimento su DAX (Data Analysis Expressions)](/dax/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
