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
ms.openlocfilehash: 7eea15d4389afaac2ac69e2f26eaa38fe84e337b
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75304180"
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

Valutare attentamente se la funzione DIVIDE deve restituire un valore alternativo. Per le misure, la progettazione consigliata prevede in genere la restituzione di BLANK. La restituzione di BLANK è consigliata perché per impostazione predefinita gli oggetti visivi del report eliminano i raggruppamenti quando i riepiloghi sono BLANK. Questo consente all'oggetto visivo di concentrare l'attenzione sui gruppi in cui sono presenti dati. Quando necessario, è possibile configurare l'oggetto visivo per visualizzare tutti i gruppi (che restituiscono valori o BLANK) nel contesto di filtro abilitando l'opzione [Mostra elementi senza dati](../desktop-show-items-no-data.md).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Informazioni di riferimento su DAX (Data Analysis Expressions)](/dax/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
