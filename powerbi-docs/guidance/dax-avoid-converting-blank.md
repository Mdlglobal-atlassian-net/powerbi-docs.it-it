---
title: 'DAX: Evitare di convertire risultati BLANK in valori'
description: Linee guida per la conversione di risultati BLANK in valori.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700387"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Evitare di convertire risultati BLANK in valori

Durante la scrittura di espressioni di misura, gli autori di modelli di dati potrebbero riscontrare casi in cui non è possibile restituire un valore significativo. In questi casi si potrebbe essere tentati di restituire un valore, ad esempio zero, in alternativa. Si consiglia di valutare con attenzione se questa decisione di progettazione è efficiente e pratica.

Si consideri la seguente definizione di misura che converte in modo esplicito i risultati BLANK in zero.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Si consideri un'altra definizione di misura che converte anch'essa i risultati BLANK in zero.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

La funzione [DIVIDE](/dax/divide-function-dax) divide la misura **Profit** per la misura **Sales**. Se il risultato è zero o BLANK, viene restituito il terzo argomento, ovvero il risultato alternativo (facoltativo). In questo esempio, poiché viene passato zero come risultato alternativo, è garantito che la misura restituisca sempre un valore.

Queste progettazioni delle misure sono inefficienti e portano a progettazioni di report di scarsa qualità.

Quando vengono aggiunte a un oggetto visivo del report, Power BI tenta di recuperare tutti i raggruppamenti all'interno del contesto di filtro. La valutazione e il recupero di risultati di query di grandi dimensioni spesso causano rallentamenti del rendering del report. Ogni misura di esempio converte di fatto un calcolo sparso in uno denso, forzando Power BI a usare più memoria del necessario.

Inoltre, troppi raggruppamenti creano spesso confusione per gli utenti del report.

Di seguito viene illustrato cosa accade quando si aggiunge la misura **Profit Margin** a un oggetto visivo tabella, raggruppando i dati in base al cliente.

![In un oggetto visivo tabella sono presenti tre colonne: Customer, Sales e Profit Margin. La tabella visualizza circa 10 righe di dati, ma la barra di scorrimento verticale indica che sono presenti molte più righe che possono essere visualizzate. La colonna Sales non visualizza alcun valore. Nella colonna Profit Margin viene visualizzato solo zero.](media/dax-avoid-converting-blank/table-visual-poor.png)

L'oggetto visivo tabella visualizza un numero eccessivo di righe. Ci sono infatti 18.484 clienti nel modello, quindi la tabella tenta di visualizzarli tutti. Si noti che per i clienti visualizzati non risultano vendite. Vengono però visualizzati perché la misura **Profit Margin** restituisce sempre un valore.

> [!NOTE]
> Quando sono presenti troppi punti dati da visualizzare in un oggetto visivo, Power BI potrebbe usare strategie di riduzione dei dati per rimuovere o riepilogare risultati di query molto estesi. Per altre informazioni, vedere [Limiti dei dati per gli oggetti visivi e strategie in base al tipo di oggetto visivo](../visuals/power-bi-data-points.md).

Di seguito viene illustrato cosa accade migliorando la definizione della misura **Profit Margin**. Ora restituisce un valore solo quando la misura **Sales** non è BLANK (o zero).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

L'oggetto visivo tabella visualizza ora solo i clienti con vendite nel contesto di filtro corrente. La misura migliorata produce un'esperienza più efficiente e pratica per gli utenti del report.

![Lo stesso oggetto visivo tabella ora visualizza quattro righe di dati. Ogni riga è riferita a un cliente con un valore di vendita e con valori Profit Margin diversi da zero.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Quando necessario, è possibile configurare un oggetto visivo per visualizzare tutti i raggruppamenti (che restituiscono valori o BLANK) nel contesto del filtro abilitando l'opzione [Mostra elementi senza dati](../desktop-show-items-no-data.md).

## <a name="recommendation"></a>Raccomandazione

È consigliabile che le misure restituiscano BLANK quando non è possibile restituire un valore significativo.

Questo approccio di progettazione è efficiente, consentendo a Power BI di eseguire il rendering dei report più velocemente. La restituzione di BLANK è consigliata anche perché per impostazione predefinita gli oggetti visivi del report eliminano i raggruppamenti quando i riepiloghi sono BLANK.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Informazioni di riferimento su DAX (Data Analysis Expressions)](/dax/)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
