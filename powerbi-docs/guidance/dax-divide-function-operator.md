---
title: 'DAX: Confronto tra funzione DIVIDE e operatore di divisione (/)'
description: Linee guida per l'uso della funzione DIVIDE DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695198"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Confronto tra funzione DIVIDE e operatore di divisione (/)

Quando si scrive un'espressione DAX per dividere un numeratore per un denominatore, un modeler di dati può scegliere di usare la funzione [DIVIDE](/dax/divide-function-dax) o l'operatore di divisione (/ - barra).

Quando si usa la funzione DIVIDE, è necessario passare le espressioni del numeratore e del denominatore. Facoltativamente, è possibile passare un valore che rappresenta un _risultato alternativo_.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

La funzione DIVIDE è stata progettata per gestire automaticamente i casi di divisione per zero. Se non viene passato un risultato alternativo e il denominatore è zero o BLANK, la funzione restituisce BLANK. Quando viene passato un risultato alternativo, questo viene restituito al posto di BLANK.

La funzione DIVIDE è comoda perché consente di evitare di dover prima testare il valore del denominatore nell'espressione. La funzione è inoltre ottimizzata meglio per il test del valore del denominatore rispetto alla funzione [IF](/dax/if-function-dax). Il miglioramento delle prestazioni è significativo perché il controllo della divisione per zero è dispendioso. L'uso di DIVIDE consente anche di ottenere un'espressione più concisa ed elegante.

## <a name="example"></a>Esempio

L'espressione di misura seguente genera una divisione sicura, ma comporta l'uso di quattro funzioni DAX.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Questa espressione di misura ottiene lo stesso risultato, ma in modo più efficiente ed elegante.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Raccomandazioni

Si consiglia di usare la funzione DIVIDE ogni volta che il denominatore è un'espressione che _potrebbe_ restituire zero o BLANK.

Se il denominatore è un valore costante, è consigliabile usare l'operatore di divisione. In questo caso, è garantita la riuscita della divisione e l'espressione offrirà prestazioni migliori, in quanto eviterà test superflui.

Valutare attentamente se la funzione DIVIDE deve restituire un valore alternativo. È preferibile progettare le misure in modo che restituiscano BLANK quando non è possibile valutare un risultato significativo. Per altre informazioni, vedere [Evitare di convertire risultati BLANK in valori](dax-avoid-converting-blank.md).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Informazioni di riferimento su DAX (Data Analysis Expressions)](/dax/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
