---
title: 'DAX: Uso appropriato delle funzioni di errore'
description: Istruzioni sull'uso delle funzioni di errore DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 4730e835c511153232f79c193de5bbd56d63b963
ms.sourcegitcommit: f1f57c5bc6ea3057007ed8636ede50188ed90ce1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74410913"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Uso appropriato delle funzioni di errore

Se un'espressione DAX può generare un errore in fase di valutazione, un modeler di dati può considerare l'uso di due utili funzioni DAX.

- La funzione [ISERROR](/dax/iserror-function-dax) accetta una sola espressione e restituisce TRUE se tale espressione genera un errore.
- La funzione [IFERROR](/dax/iferror-function-dax) accetta due espressioni. Se la prima espressione genera un errore, viene restituito il valore per la seconda espressione. Si tratta in realtà di un'implementazione più ottimizzata dell'annidamento della funzione ISERROR all'interno di una funzione [IF](/dax/if-function-dax).

Sebbene queste funzioni possano essere utili e possano contribuire a scrivere espressioni facilmente comprensibili, è anche possibile che riducano significativamente le prestazioni dei calcoli. Ciò può avvenire perché tali funzioni aumentano il numero delle analisi che il motore di archiviazione deve eseguire.

La maggior parte degli errori in fase di valutazione è dovuta a valori vuoti o zero imprevisti oppure a una conversione del tipo di dati non valida.

## <a name="recommendations"></a>Raccomandazioni

È preferibile evitare di usare le funzioni ISERROR e IFERROR. In alternativa, applicare strategie difensive durante lo sviluppo del modello e la scrittura di espressioni, Possibili strategie:

- **Controllo della qualità dei dati caricati nel modello:** Usare le trasformazioni Power Query per rimuovere o sostituire valori non validi o mancanti e per impostare tipi di dati corretti. È anche possibile usare una trasformazione Power Query per filtrare le righe quando si verificano errori, ad esempio in caso di conversione di dati non valida.

    La qualità dei dati può essere controllata anche disabilitando la proprietà **Is Nullable** della colonna del modello che non aggiornerà i dati se si dovessero rilevare dati vuoti. Se si verifica questo errore, i dati caricati in seguito a un aggiornamento riuscito rimarranno nelle tabelle.
- **Uso della funzione IF:** L'espressione di un test logico della funzione IF può determinare se si verificherà un errore. Si noti che, analogamente alle funzioni ISERROR e IFERROR, questa funzione può richiedere analisi aggiuntive del motore di archiviazione, ma è probabile che le prestazioni siano migliori rispetto alle altre funzioni, in quanto non si devono generare errori.
- **Uso di funzioni a tolleranza di errore:** Alcune funzioni DAX testano e compensano le condizioni di errore. Queste funzioni consentono di immettere un risultato alternativo che verrebbe invece restituito. La funzione [DIVIDE](/dax/divide-function-dax) è uno di questi esempi. Per altre istruzioni su questa funzione, vedere l'articolo [DAX: Confronto tra funzione DIVIDE e operatore di divisione (/)](dax-divide-function-operator.md).

## <a name="example"></a>Esempio

Nell'espressione di misura seguente viene verificato se si genererà un errore. In questa istanza viene restituito un valore vuoto. Si verifica quando non si specifica la funzione IF con un'espressione value-if-false.

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

La versione successiva dell'espressione di misura è stata migliorata usando la funzione IFERROR al posto delle funzioni IF e ISERROR.

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

Questa versione finale dell'espressione di misura ottiene lo stesso risultato, ma in modo più efficiente ed elegante.

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Informazioni di riferimento su DAX (Data Analysis Expressions)](/dax/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
