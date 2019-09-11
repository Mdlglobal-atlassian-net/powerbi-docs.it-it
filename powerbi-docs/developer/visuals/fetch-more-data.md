---
title: Recuperare altri dati da Power BI
description: Questo articolo illustra come abilitare un recupero segmentato di set di dati di grandi dimensioni per gli oggetti visivi di Power BI.
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7e5ecc0e317a21d10e76e9413926822ac4d6760b
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237146"
---
# <a name="fetch-more-data-from-power-bi"></a>Recuperare altri dati da Power BI

Questo articolo illustra come caricare più dati per ignorare il rigido limite di un punto dati da 30 KB. Questo approccio fornisce i dati in blocchi. Per migliorare le prestazioni, è possibile configurare le dimensioni dei blocchi in base al caso d'uso.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Abilitare un recupero segmentato di set di dati di grandi dimensioni

Per la modalità di segmentazione `dataview`, definire le dimensioni della finestra per dataReductionAlgorithm nel file *capabilities.json* dell'oggetto visivo per l'oggetto dataViewMapping necessario. `count` determina le dimensioni della finestra, che limita il numero di nuove righe di dati che possono essere accodate a `dataview` in ogni aggiornamento.

Aggiungere il codice seguente nel file *capabilities.json*:

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

## <a name="usage-in-the-power-bi-visual"></a>Uso nell'oggetto visivo di Power BI

È possibile determinare se i dati sono presenti verificando l'esistenza di `dataView.metadata.segment`:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

È anche possibile verificare se si tratta del primo aggiornamento o di uno successivo controllando `options.operationKind`. Nel codice seguente, `VisualDataChangeOperationKind.Create` fa riferimento al primo segmento e `VisualDataChangeOperationKind.Append` fa riferimento ai segmenti successivi.

Per un'implementazione di esempio, vedere il frammento di codice seguente:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

È anche possibile richiamare il metodo `fetchMoreData` da un gestore eventi dell'interfaccia utente, come illustrato di seguito:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Come risposta alla chiamata del metodo `this.host.fetchMoreData`, Power BI chiama il metodo `update` dell'oggetto visivo con un nuovo segmento di dati.

> [!NOTE]
> Per evitare vincoli di memoria del client, Power BI attualmente limita i dati recuperati totali a 100 MB. È possibile rilevare il raggiungimento del limite quando fetchMoreData() restituisce `false`.
