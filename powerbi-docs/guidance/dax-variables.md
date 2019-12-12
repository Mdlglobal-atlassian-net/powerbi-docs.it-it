---
title: 'DAX: Usare le variabili per migliorare le formule'
description: Linee guida sull'uso di variabili nelle espressioni DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700709"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Usare le variabili per migliorare le formule

Per gli autori di modelli di dati, la scrittura e il debug di alcuni calcoli DAX possono risultare difficoltosi. È normale che i requisiti di calcolo complessi includano spesso la scrittura di espressioni composte o complesse. Le espressioni composte possono comportare l'uso di molte funzioni annidate ed eventualmente il riutilizzo della logica dell'espressione.

L'uso di variabili nelle formule DAX consente di scrivere calcoli complessi ed efficienti. Le variabili possono:

- [Migliorare le prestazioni](#improve-performance)
- [Migliorare la leggibilità](#improve-readability)
- [Semplificare il debug](#simplify-debugging)
- [Ridurre la complessità](#reduce-complexity)

In questo articolo verranno illustrati i primi tre vantaggi usando una misura di esempio per l'incremento delle vendite rispetto all'anno precedente (YoY, Year-over-Year). La formula per calcolare l'incremento delle vendite rispetto all'anno precedente è: vendite del periodo _vendite inferiori dello stesso periodo dell'ultimo anno, _diviso per_ le vendite dello stesso periodo dell'ultimo anno.

Si inizierà con la definizione della misura seguente.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

La misura produce il risultato corretto, ma è possibile migliorarlo, come si vedrà ora.

## <a name="improve-performance"></a>Migliorare le prestazioni

Si noti che la formula ripete l'espressione che calcola "lo stesso periodo dell'ultimo anno". Questa formula non è efficiente perché Power BI deve valutare la stessa espressione due volte. La definizione della misura può essere resa più efficiente usando una variabile.

La definizione della misura seguente rappresenta un miglioramento. Usa un'espressione per assegnare il risultato dello "stesso periodo dell'ultimo anno" a una variabile denominata **SalesPriorYear**. La variabile viene quindi usata due volte nell'espressione RETURN.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

La misura continua a produrre il risultato corretto in circa metà del tempo della query.

## <a name="improve-readability"></a>Migliorare la leggibilità

Nella definizione della misura precedente è possibile notare come la scelta del nome della variabile renda più facilmente comprensibile l'espressione RETURN. L'espressione è breve e auto-descrittiva.

## <a name="simplify-debugging"></a>Semplificare il debug

Le variabili consentono anche di eseguire il debug di una formula. Per testare un'espressione assegnata a una variabile, si riscrive temporaneamente l'espressione RETURN in modo che restituisca la variabile.

La definizione della misura seguente restituisce solo la variabile **SalesPriorYear**. Si noti come imposta come commento l'espressione RETURN prevista. Questa tecnica consente di ripristinarla facilmente al termine del debug.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Ridurre la complessità

Nelle versioni precedenti di DAX le variabili non erano ancora supportate. Erano necessarie espressioni complesse, che introducevano nuovi contesti di filtro, per usare le funzioni DAX [EARLIER](/dax/earlier-function-dax) o [EARLIEST](/dax/earliest-function-dax) per poter fare riferimento a contesti di filtro esterni. Queste funzioni erano purtroppo difficili da comprendere e da usare per gli autori di modelli di dati.

Le variabili vengono sempre valutate al di fuori dei filtri applicati dall'espressione RETURN. Per questo motivo, quando si usa una variabile in un contesto di filtro modificato, si ottiene lo stesso risultato ottenuto con la funzione EARLIEST. È quindi possibile evitare l'uso delle funzioni EARLIER o EARLIEST. Ciò significa che è ora possibile scrivere formule meno complesse e più facili da comprendere.

Si consideri la definizione di colonna calcolata seguente aggiunta alla tabella **Subcategory**. Valuta una classificazione per ogni sottocategoria di prodotto in base ai valori della colonna **Subcategory Sales**.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

La funzione EARLIER viene usata per fare riferimento al valore della colonna **Subcategory Sales** _nel contesto della riga corrente_.

Per migliorare la definizione della colonna calcolata, è possibile usare una variabile invece della funzione EARLIER. La variabile **CurrentSubcategorySales** archivia il valore della colonna **Subcategory Sales** _nel contesto della riga corrente_ e l'espressione RETURN lo usa in un contesto di filtro modificato.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- Articolo di DAX su [VAR](/dax/var-dax)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
