---
title: Funzionalità e proprietà degli oggetti visivi di Power BI
description: Questo articolo descrive le funzionalità e le proprietà degli oggetti visivi di Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8b14568eb3a9ebc75b8d94935aedc2ae07122ef4
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193666"
---
# <a name="capabilities-and-properties-of-power-bi-visuals"></a>Funzionalità e proprietà degli oggetti visivi di Power BI 

Le funzionalità si usano per fornire all'host informazioni sull'oggetto visivo. Tutte le proprietà nel modello capabilities sono `optional`.

Gli oggetti radice delle funzionalità di un oggetto visivo sono `dataRoles`, `dataViewMappings` e così via.

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

## <a name="define-the-data-fields-that-your-visual-expects-dataroles"></a>Definire i campi dati previsti dall'oggetto visivo: dataRoles

Per definire i campi che possono essere associati ai dati, si usa `dataRoles`. `dataRoles` usa una matrice di oggetti `DataViewRole`, che definisce tutte le proprietà obbligatorie.

### <a name="properties"></a>Proprietà

* **name**: nome interno di questo campo dati (deve essere univoco).
* **kind**: tipo di campo:
    * `Grouping`: valori discreti usati per il raggruppamento dei campi delle misure.
    * `Measure`: valori dei dati numerici.
    * `GroupingOrMeasure`: valori che possono essere usati come raggruppamento o misura.
* **displayName**: nome visualizzato dall'utente nel riquadro **Proprietà**.
* **description**: breve descrizione del campo (proprietà facoltativa).
* **requiredTypes**: tipo di dati richiesto per questo ruolo dati. I valori che non corrispondono sono impostati su null (proprietà facoltativa).
* **preferredTypes**: tipo di dati preferito per questo ruolo dati (proprietà facoltativa).

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Tipi di dati validi in requiredTypes e preferredTypes

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

I ruoli dei dati precedenti creeranno i campi visualizzati nell'immagine seguente:

![Campi dei ruoli dei dati](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped-dataviewmappings"></a>Definire il modo in cui si vuole eseguire il mapping dei dati: dataViewMappings

Una proprietà DataViewMappings descrive il modo in cui i ruoli dati sono correlati tra loro e permette di specificare i requisiti condizionali per i ruoli.

La maggior parte degli oggetti visivi fornisce un solo mapping, ma è possibile fornire più oggetti dataViewMapping. Ogni mapping valido genera una visualizzazione dati. 

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

Per altre informazioni, vedere [Mapping di viste dati in oggetti visivi di Power BI](dataview-mappings.md).

## <a name="define-property-pane-options-objects"></a>Definire le opzioni del riquadro delle proprietà: objects

Gli oggetti descrivono proprietà personalizzabili associate all'oggetto visivo. Ogni oggetto può avere più proprietà e a ogni proprietà è associato un tipo. I tipi indicano che cosa sarà la proprietà. 

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

Per altre informazioni, vedere [Oggetti e proprietà](objects-properties.md).

## <a name="handle-partial-highlighting-supportshighlight"></a>Gestire l'evidenziazione parziale: supportsHighlight

Per impostazione predefinita, questo valore è impostato su `false`, quindi i valori vengono automaticamente filtrati quando un elemento nella pagina viene selezionato. Questo filtro automatico aggiorna a sua volta l'oggetto visivo in modo da visualizzare solo il valore selezionato. Per visualizzare i dati completi, ma evidenziare solo gli elementi selezionati, è necessario impostare `supportsHighlight` su `true` nel file *capabilities.json*.

Per altre informazioni,, vedere [Evidenziare i punti dati in oggetti visivi di Power BI](highlight.md).

## <a name="handle-advanced-edit-mode-advancededitmodesupport"></a>Gestire la modalità di modifica avanzata: advancedEditModeSupport

Un oggetto visivo può dichiarare il supporto della modalità di modifica avanzata. Per impostazione predefinita, un oggetto visivo non supporta la modalità di modifica avanzata, a meno che non sia specificato diversamente nel file *capabilities.json*.

Per altre informazioni, vedere [Modalità di modifica avanzata](advanced-edit-mode.md).

## <a name="data-sorting-options-for-visual-sorting"></a>Opzioni di ordinamento dei dati per l'oggetto visivo: sorting

Un oggetto visivo può definire il proprio comportamento di ordinamento tramite le proprie funzionalità. Per impostazione predefinita, un oggetto visivo non supporta la modifica dell'ordinamento, a meno che non sia specificato diversamente nel file *capabilities.json*.

Per altre informazioni, vedere [Opzioni di ordinamento](sort-options.md).
