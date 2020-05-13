---
title: Linee guida per i modelli compositi in Power BI Desktop
description: Linee guida per lo sviluppo di modelli compositi.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 528fc40427a1cb242d9154028d1a7c6617c8a14e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279686"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Linee guida per i modelli compositi in Power BI Desktop

Questo articolo è destinato agli sviluppatori di modelli compositi per Power BI. Vengono descritti i casi d'uso dei modelli compositi e vengono offerte linee guida di progettazione. In particolare, le linee guida consentono di determinare se un modello composito è appropriato per la soluzione. In tal caso, l'articolo si rivelerà utile anche per ottimizzare la progettazione del modello.

> [!NOTE]
> Questo articolo non include un'introduzione ai modelli compositi. Se non si ha familiarità con i modelli compositi, è consigliabile leggere prima l'articolo [Usare modelli compositi in Power BI Desktop](../transform-model/desktop-composite-models.md).
>
> Poiché i modelli compositi sono costituiti da almeno un'origine DirectQuery, è anche importante avere una conoscenza approfondita delle [relazioni dei modelli](../transform-model/desktop-relationships-understand.md), dei [modelli DirectQuery](../connect-data/desktop-directquery-about.md) e delle [linee guida per la progettazione di modelli DirectQuery](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Casi d'uso di modelli compositi

Quando possibile, è preferibile sviluppare un modello in modalità di importazione. Questa modalità offre una flessibilità di progettazione elevata e prestazioni ottimizzate.

Tuttavia, i modelli in modalità di importazione non consentono di risolvere i problemi correlati a volumi di dati di grandi dimensioni o di creare report sui dati quasi in tempo reale. In questi casi è possibile prendere in considerazione un modello DirectQuery, a condizione che i dati siano archiviati in una singola origine dati [supportata dalla modalità DirectQuery](../connect-data/power-bi-data-sources.md).

Anche nelle situazioni seguenti è possibile prendere in considerazione lo sviluppo di un modello composito.

- Il modello potrebbe essere un modello DirectQuery, ma con prestazioni ottimizzate. In un modello composito è possibile migliorare le prestazioni configurando l'archiviazione appropriata per ogni tabella. È anche possibile aggiungere [aggregazioni](../transform-model/desktop-aggregations.md). Queste opzioni di ottimizzazione sono entrambe descritte più avanti in questo articolo.
- Si vuole combinare un modello DirectQuery con dati aggiuntivi, che devono essere importati nel modello. I dati importati possono essere caricati da un'origine dati diversa o da tabelle calcolate.
- Si vogliono combinare due o più origini dati DirectQuery in un unico modello.

> [!NOTE]
> I modelli compositi non possono combinare origini di connessione dinamica o origini di database analitici DirectQuery. Le origini di connessione dinamica includono [modelli di dati con hosting esterno](../connect-data/service-datasets-understand.md#external-hosted-models) e set di dati di Power BI. Le origini di database analitici DirectQuery includono SAP Business Warehouse e SAP HANA.

## <a name="optimize-model-design"></a>Ottimizzare la progettazione del modello

Un modello composito può essere ottimizzato configurando le [modalità di archiviazione](../transform-model/desktop-storage-mode.md) delle tabelle e aggiungendo [aggregazioni](../transform-model/desktop-aggregations.md).

### <a name="table-storage-mode"></a>Modalità archiviazione tabella

In un modello composito è possibile configurare la modalità di archiviazione per ogni tabella, ad eccezione delle tabelle calcolate:

- **DirectQuery**: è consigliabile impostare questa modalità per le tabelle che rappresentano volumi di dati di grandi dimensioni o che devono offrire risultati quasi in tempo reale. I dati non verranno mai importati nelle tabelle. In genere, queste tabelle saranno tabelle di tipo fact, ovvero tabelle usate per il riepilogo.
- **Import**: è consigliabile impostare questa modalità per le tabelle di tipo dimensione, ovvero le tabelle usate per filtri e raggruppamento. Infatti, è l'unica opzione per le tabelle basate sulle origini non supportate dalla modalità DirectQuery. Le tabelle calcolate sono sempre di tipo importazione.
- **Doppia**: si consiglia di impostare questa modalità per le tabelle di tipo dimensione, quando esiste la possibilità che queste tabelle vengano sottoposte a query insieme con le tabelle di tipo fact DirectQuery dalla stessa origine.

Esistono diversi scenari in cui Power BI esegue una query su un modello composito:

- **Le query vengono eseguite solo su tabelle di importazione o doppie**: tutti i dati vengono recuperati dalla cache del modello, ottimizzando la velocità delle prestazioni. Questo scenario è comune per le tabelle di tipo dimensione sottoposte a query da filtri o oggetti visivi di tipo filtro dei dati.
- **Le query vengono eseguite su tabelle doppie o tabelle DirectQuery dalla stessa origine**: tutti i dati vengono recuperati inviando una o più query native all'origine DirectQuery. Consente di ottenere le prestazioni più rapide, specialmente quando sono presenti indici appropriati nelle tabelle di origine. Questo scenario è comune per le query correlate alle tabelle di tipo dimensione doppie e alle tabelle di tipo fact DirectQuery. Queste query vengono eseguite _all'interno dell'isola_, quindi tutte le relazioni uno-a-uno o uno-a-molti vengono valutate come [relazioni forti](../transform-model/desktop-relationships-understand.md#strong-relationships).
- **Tutte le altre query**: queste query coinvolgono relazioni tra isole. Questo perché una tabella di importazione è correlata a una tabella DirectQuery o una tabella doppia è correlata a una tabella DirectQuery da un'origine diversa, nel qual caso si comporta come una tabella di importazione. Tutte le relazioni vengono valutate come [relazioni deboli](../transform-model/desktop-relationships-understand.md#weak-relationships). Ciò significa anche che i raggruppamenti applicati alle tabelle non DirectQuery devono essere inviati all'origine DirectQuery come una tabella virtuale. In questo caso la query nativa può risultare inefficiente, soprattutto per set di raggruppamenti di grandi dimensioni. Ed è anche possibile che dati sensibili vengano esposti nella query nativa.

Riepilogando, è consigliabile:

- valutare con attenzione se un modello composito sia la soluzione ideale. Sebbene consenta l'integrazione a livello di modello di origini dati diverse, introduce anche complessità di progettazione con possibili conseguenze
- Impostare la modalità di archiviazione su **DirectQuery** quando una tabella è una tabella di tipo fact che archivia volumi di dati di grandi dimensioni o deve produrre risultati quasi in tempo reale
- Impostare la modalità di archiviazione su **Doppia** quando una tabella è una tabella di tipo dimensione e verrà sottoposta a query con tabelle di tipo fact **DirectQuery** basate sulla stessa origine
- Configurare frequenze di aggiornamento appropriate affinché la cache dei modelli delle tabelle doppie (e di eventuali tabelle calcolate dipendenti) resti sincronizzata con i database di origine
- Cercare di garantire l'integrità dei dati tra le origini dati, inclusa la cache del modello: le relazioni deboli eliminano le righe quando i valori delle colonne correlate non corrispondono
- Ottimizzare le origini dati DirectQuery con gli indici appropriati per join, filtri e raggruppamento efficienti
- Non caricare dati sensibili in tabelle di importazione o doppie se è presente il rischio che una query nativa venga intercettata. Per altre informazioni, vedere [Usare modelli compositi in Power BI Desktop (Implicazioni per la sicurezza)](../transform-model/desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Aggregations

È possibile aggiungere aggregazioni alle tabelle DirectQuery nel modello composito. Le aggregazioni vengono memorizzate nella cache del modello e pertanto si comportano come tabelle di importazione, sebbene non possano essere usate come una tabella del modello. Il loro scopo è quello di migliorare le prestazioni per le query a "granularità più elevata". Per altre informazioni, vedere [Aggregazioni in Power BI Desktop](../transform-model/desktop-aggregations.md).

È consigliabile che una tabella di aggregazioni segua una regola di base: il numero di righe deve essere minore di almeno 10 volte rispetto alla tabella sottostante. Se, ad esempio, la tabella sottostante archivia 1 miliardo di righe, la tabella di aggregazioni non deve superare i 100 milioni di righe. Questa regola garantisce un miglioramento delle prestazioni adeguato rispetto al costo della creazione e della gestione della tabella di aggregazioni.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Usare modelli compositi in Power BI Desktop](../transform-model/desktop-composite-models.md)
- [Relazioni nei modelli in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [Modelli DirectQuery in Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [Usare DirectQuery in Power BI Desktop](../connect-data/desktop-use-directquery.md)
- [Risoluzione dei problemi del modello DirectQuery in Power BI Desktop](../connect-data/desktop-directquery-troubleshoot.md)
- [Origini dati di Power BI](../connect-data/power-bi-data-sources.md)
- [Modalità di archiviazione in Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Aggregazioni in Power BI Desktop](../transform-model/desktop-aggregations.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com)
