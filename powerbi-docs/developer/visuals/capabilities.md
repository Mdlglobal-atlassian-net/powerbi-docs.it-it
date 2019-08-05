---
title: Funzionalità
description: Funzionalità e proprietà degli oggetti visivi di Power BI
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425460"
---
# <a name="power-bi-visual-capabilities"></a>Funzionalità degli oggetti visivi di Power BI

Le funzionalità forniscono all'host informazioni sull'oggetto visivo. Tutte le proprietà nel modello Capabilities sono `optional`

Gli oggetti radice delle funzionalità degli oggetti visivi sono `dataRoles`, `dataViewMappings` e così via.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>Definire i campi dati previsti dall'oggetto visivo - `dataRoles`

Per definire i campi che possono essere associati ai dati, viene usato `dataRoles`, che accetta una matrice di oggetti `DataViewRole` che definisce tutte le proprietà necessarie.

### <a name="properties"></a>Proprietà

* **name**: nome interno di questo campo dati (deve essere univoco)
* **kind**: tipo di campo:
    * `Grouping`: valori discreti usati per il raggruppamento dei campi di misura
    * `Measure`: valori dei dati numerici
    * `GroupingOrMeasure`: può essere usato come raggruppamento o misura
* **displayName**: nome visualizzato all'utente nel riquadro delle proprietà
* **description**: breve descrizione del campo (proprietà facoltativa)
* **requiredTypes**: tipo di dati richiesto per questo ruolo dati. Qualsiasi valore che non corrisponde verrà impostato su null (proprietà facoltativa)
* **preferredTypes**: tipo di dati preferito per questo ruolo dati (proprietà facoltativa)

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Tipi di dati validi in "requiredTypes" e "preferredTypes"

* **bool**: valore booleano
* **integer**: valore intero (numero intero)
* **numeric**: valore numerico
* **text**: valore di testo
* **geography**: dati geografici

### <a name="example"></a>Esempio

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

I ruoli dati precedenti creano i campi seguenti

![Visualizzazione del ruolo dati](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>Definire il modo in cui si vuole eseguire il mapping dei dati - `dataViewMappings`

Un oggetto DataViewMapping descrive il modo in cui i ruoli dati sono correlati tra loro e permette di specificare i requisiti condizionali per i ruoli.

La maggior parte degli oggetti visivi fornisce un solo mapping, ma è possibile fornire più oggetti dataViewMapping. Ogni mapping valido produrrà un oggetto DataView. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[Altre informazioni su DataViewMappings](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>Definire le opzioni del riquadro delle proprietà - `objects`

Gli oggetti descrivono proprietà personalizzabili associate all'oggetto visivo.
Ogni oggetto può avere più proprietà e a ogni proprietà è associato un tipo.
I tipi indicano che cosa sarà la proprietà. Per altre informazioni sui tipi, vedere di seguito.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[Altre informazioni sugli oggetti](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>Gestire l'evidenziazione parziale - `supportsHighlight`

Per impostazione predefinita, questo valore è impostato su false, che significa che i "valori" verranno filtrati automaticamente quando viene selezionato un elemento nella pagina e questa operazione a sua volta aggiorna l'oggetto visivo in modo da visualizzare solo il valore selezionato. Se si vuole visualizzare i dati completi, ma evidenziare solo gli elementi selezionati, è necessario impostare `supportsHighlight` su true in capabilities.json.

[Altre informazioni sull'evidenziazione](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>Gestire la modalità di modifica avanzata - `advancedEditModeSupport`

Un oggetto visivo può dichiarare il supporto della modalità di modifica avanzata.
Per impostazione predefinita, un oggetto visivo non supporta la modalità di modifica avanzata, a meno che non sia specificato diversamente nel file capabilities.json.

[Altre informazioni su advancedEditModeSupport](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>Opzioni di ordinamento dei dati per l'oggetto visivo - `sorting`

Un oggetto visivo può definire il proprio comportamento di ordinamento tramite le proprie funzionalità.
Per impostazione predefinita, un oggetto visivo non supporta la modifica dell'ordinamento, a meno che non sia specificato diversamente nel file capabilities.json.

[Altre informazioni sull'ordinamento](sort-options.md)
