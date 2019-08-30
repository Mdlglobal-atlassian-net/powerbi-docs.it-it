---
title: 'DAX: Confronto tra funzione DIVIDE e operatore di divisione (/)'
description: Linee guida per l'uso della funzione DIVIDE DAX.
author: guyinacube
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/05/2019
ms.author: v-pemyer
ms.openlocfilehash: d22491ee314ebcebd4479c4e57dbfdf7a6a1ffdb
ms.sourcegitcommit: c2197c3ad1d747b4ad490ab75771a0d32d0ae208
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "70010438"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Confronto tra funzione DIVIDE e operatore di divisione (/)

Questo articolo è destinato agli autori di modelli di dati che definiscono espressioni DAX.

## <a name="background"></a>Sfondo

Quando si scrive un'espressione DAX per dividere un numeratore per un denominatore, è possibile scegliere di usare la funzione [DIVIDE](/dax/divide-function-dax) o l'operatore di divisione (/ - barra).

Quando si usa la funzione DIVIDE, è necessario passare le espressioni del numeratore e del denominatore. Facoltativamente, è possibile passare un valore che rappresenta un risultato alternativo.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

La funzione DIVIDE è stata progettata per gestire automaticamente i casi di divisione per zero. Se non viene passato un risultato alternativo e il denominatore è zero o BLANK, la funzione restituisce BLANK. Se viene passato un risultato alternativo, questo viene restituito al posto di BLANK.

La funzione DIVIDE è comoda perché consente di evitare di dover prima testare il valore del denominatore nell'espressione. La funzione è inoltre ottimizzata meglio per il test del valore del denominatore rispetto alla funzione [IF](/dax/if-function-dax). L'uso di DIVIDE consente anche di ottenere un'espressione più concisa ed elegante.

## <a name="example"></a>Esempio

L'espressione di misura seguente produce una divisione sicura, ma comporta l'uso di tre funzioni DAX.

```dax

=IF(ISBLANK([Sales]) || [Sales] = 0, BLANK(), [Profit] / [Sales])

```

Questa espressione di misura ottiene lo stesso risultato, ma in modo più efficiente ed elegante.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Raccomandazioni

Si consiglia di usare la funzione DIVIDE ogni volta che il denominatore è un'espressione che _potrebbe_ restituire zero o BLANK.

Se il denominatore è un valore costante, è consigliabile usare l'operatore di divisione. In questo caso, è garantita la riuscita della divisione e l'espressione offrirà prestazioni migliori, in quanto eviterà test superflui.

È necessario valutare attentamente se la funzione DIVIDE deve restituire un valore alternativo. Per le misure, la progettazione consigliata prevede la restituzione di BLANK. Questo perché gli oggetti visivi del report eliminano i raggruppamenti per impostazione predefinita quando i riepiloghi sono BLANK. Questo consente all'oggetto visivo di concentrarsi sui gruppi in cui sono presenti dati. Quando necessario, è possibile configurare l'oggetto visivo per visualizzare tutti i gruppi (che restituiscono valori o BLANK) nel contesto di filtro abilitando l'opzione "Mostra elementi senza dati".
