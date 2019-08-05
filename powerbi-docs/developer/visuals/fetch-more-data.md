---
title: Recuperare altri dati
description: Abilitare il recupero segmentato di set di dati di grandi dimensioni per gli oggetti visivi di Power BI
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425069"
---
# <a name="fetch-more-data-from-power-bi"></a>Recuperare altri dati da Power BI

L'API per il caricamento di altri dati permette di superare il rigido limite di 30.000 punti dati. L'API restituisce i dati in blocchi. Le dimensioni dei blocchi sono configurabili per migliorare le prestazioni in base al caso d'uso.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Abilitare il recupero segmentato di set di dati di grandi dimensioni

Per la modalità di segmentazione `dataview`, definire una "finestra" dataReductionAlgorithm nel file `capabilities.json` dell'oggetto visivo per l'oggetto dataViewMapping necessario.
`count` determina le dimensioni della finestra, che limita il numero di nuove righe di dati accodate a `dataview` in ogni aggiornamento.

Da aggiungere nel file capabilities.json

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

I nuovi segmenti vengono accodati all'oggetto `dataview` esistente e forniti all'oggetto visivo come chiamata `update`.

## <a name="usage-in-the-custom-visual"></a>Utilizzo nell'oggetto visivo personalizzato

I dati di indicazione sono presenti o non possono essere determinati controllando l'esistenza di `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

È anche possibile verificare se si tratta del primo aggiornamento o di uno successivo controllando `options.operationKind`.

`VisualDataChangeOperationKind.Create` indica il primo segmento, `VisualDataChangeOperationKind.Append` indica i segmenti successivi.

Per un'implementazione di esempio, vedere il frammento di codice seguente:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Il metodo `fetchMoreData` può anche essere richiamato da un gestore eventi dell'interfaccia utente

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI chiamerà il metodo `this.host.fetchMoreData` dell'oggetto visivo con un nuovo segmento di dati come risposta alla chiamata del metodo `update`.

> [!NOTE]
> Power BI attualmente limita i dati recuperati totali a **100 MB** per evitare vincoli di memoria del client. È possibile rilevare il raggiungimento di questo limite quando fetchMoreData () restituisce "false".*
