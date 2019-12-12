---
title: 'DAX: Usare SELECTEDVALUE invece di VALUES'
description: Linee guida per l'uso delle funzioni SELECTEDVALUE.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700479"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: Usare SELECTEDVALUE invece di VALUES

Gli autori di modelli di dati potrebbero avere a volte l'esigenza di scrivere un'espressione DAX che verifica se una colonna è filtrata in base a un valore specifico.

Nelle versioni precedenti di DAX questa esigenza poteva essere soddisfatta in modo sicuro usando un modello che coinvolge tre funzioni DAX. Le funzioni sono [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) e [VALUES](/dax/values-function-dax). Nella definizione di misura seguente viene presentato un esempio. Calcola l'importo dell'imposta di vendita, ma solo per le vendite effettuate ai clienti australiani.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

In questo esempio la funzione HASONEVALUE restituisce TRUE solo quando un singolo valore filtra la colonna **Country-Region**. Quando è TRUE, la funzione VALUES viene confrontata con il testo letterale "Australia". Quando la funzione VALUES restituisce TRUE, la misura **Sales** viene moltiplicata per 0,10 (che rappresenta il 10%). Se la funzione HASONEVALUE restituisce FALSE, poiché più di un valore filtra la colonna, la prima funzione IF restituisce BLANK.

L'uso di HASONEVALUE è una tecnica difensiva. È necessario perché è possibile che più valori filtrino la colonna **Country-Region**. In questo caso, la funzione VALUES restituisce una tabella di più righe. Il confronto tra una tabella di più righe e un valore scalare causa un errore.

## <a name="recommendation"></a>Raccomandazione

Si consiglia di usare la funzione [SELECTEDVALUE](/dax/selectedvalue-function). Ottiene lo stesso risultato del modello descritto in questo articolo, ma in modo più efficiente ed elegante.

La definizione della misura di esempio viene ora riscritta usando la funzione SELECTEDVALUE.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> È possibile passare un valore di _risultato alternativo_ nella funzione SELECTEDVALUE. Il valore del risultato alternativo viene restituito quando alla colonna non è applicato alcun filtro o sono applicati più filtri.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Informazioni di riferimento su DAX (Data Analysis Expressions)](/dax/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
