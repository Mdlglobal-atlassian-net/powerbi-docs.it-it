---
ms.openlocfilehash: f22c12ec0ad5bd413f3658704132143c878df1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799936"
---
L'uso delle **variabili** è una componente fondamentale di un'espressione DAX.

![](media/7-4-dax-expressions/dax-variables_1.png)

È possibile definire una variabile in un punto qualsiasi di un'espressione DAX, usando la sintassi seguente:

    VARNAME = RETURNEDVALUE

Le variabili possono essere di qualsiasi tipo di dati, incluse intere tabelle.

Tenere presente che ogni volta che si fa riferimento a una variabile nell'espressione DAX, Power BI deve ricalcolarne il valore in base alla definizione. Per questo motivo, è consigliabile evitare di ripetere variabili in una funzione.

> Contenuto video fornito da [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

