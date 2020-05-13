---
title: 'DAX: Riferimenti a colonne e misure'
description: Indicazioni per fare riferimento alle colonne nelle misure nelle espressioni DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 42d99c7139586a78565198b59bc74716261537e0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279619"
---
# <a name="dax-column-and-measure-references"></a>DAX: Riferimenti a colonne e misure

Gli autori di modelli di dati potrebbero avere l'esigenza di scrivere espressioni DAX che facciano riferimento a colonne e misure dei modelli. Le colonne e le misure sono sempre associate alle tabelle del modello, ma queste associazioni sono diverse. Quindi, sono disponibili raccomandazioni diverse su come farvi riferimento nelle espressioni.

## <a name="columns"></a>Colonne

Una colonna è un oggetto a livello di tabella e i nomi di colonna devono essere univoci all'interno di una tabella. È quindi possibile che lo stesso nome di colonna venga usato più volte nel modello, purché appartengano a tabelle diverse. Esiste un'altra regola: un nome di colonna non può avere lo stesso nome del nome di una misura o di una gerarchia presente nella stessa tabella.

In generale, DAX non impone l'uso di un riferimento _completo_ a una colonna. Un riferimento completo significa che il nome della tabella precede il nome della colonna.

Di seguito è riportato un esempio di una definizione di colonna calcolata che usa solo riferimenti a nomi di colonna. Le colonne **Sales** e **Cost** appartengono entrambe a una tabella denominata **Orders**.

```dax
Profit = [Sales] - [Cost]
```

La stessa definizione può essere riscritta con riferimenti a colonne completi.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

In alcuni casi, tuttavia, sarà necessario usare riferimenti a colonne completi quando Power BI rileva ambiguità. Quando si immette una formula, viene generato un avviso con un messaggio di errore ondulato in rosso. Inoltre, alcune funzioni DAX come [LOOKUPVALUE](/dax/lookupvalue-function-dax) richiedono l'uso di colonne complete.

È consigliabile specificare sempre in modo completo i riferimenti alle colonne. I motivi sono riportati nella sezione [Raccomandazioni](#recommendations).

## <a name="measures"></a>Misure

Una misura è un oggetto a livello di modello. Per questo motivo, i nomi delle misure devono essere univoci all'interno del modello. Tuttavia, nel riquadro **Campi** gli autori del report vedranno ogni misura associata a una singola tabella del modello. Questa associazione è impostata per motivi estetici ed è possibile configurarla impostando la proprietà **Tabella home** per la misura. Per altre informazioni, vedere [Misure in Power BI Desktop - Organizzazione delle misure](../transform-model/desktop-measures.md#organizing-your-measures).

È possibile usare una misura completa nelle espressioni. Anche DAX IntelliSense offre il suggerimento. Tuttavia, non è necessario e non è una procedura consigliata. Se si modifica la tabella home per una misura, qualsiasi espressione che usi un riferimento di misura completo verrà interrotta. Sarà quindi necessario modificare ogni formula interrotta per rimuovere (o aggiornare) il riferimento alla misura.

Si consiglia di non specificare mai riferimenti alle misure completi. I motivi sono riportati nella sezione [Raccomandazioni](#recommendations).

## <a name="recommendations"></a>Consigli

Queste raccomandazioni sono semplici e facili da ricordare:

- Usare sempre riferimenti a colonne completi
- Non usare mai riferimenti a misure completi

Ecco perché:

- **Voce della formula**: le espressioni verranno accettate, in quanto non ci saranno riferimenti ambigui da risolvere. Inoltre, verranno soddisfatti i requisiti per quelle funzioni DAX che richiedono riferimenti a colonne completi.
- **Stabilità**: le espressioni continueranno a funzionare, anche quando si modifica una proprietà della tabella home della misura.
- **Leggibilità**: le espressioni saranno semplici e rapide da comprendere. Si determinerà rapidamente se si tratta di una colonna o di una misura, a seconda che sia completa o meno.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Riferimento a Data Analysis Expressions (DAX)](/dax/)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)

