---
title: API dei filtri degli oggetti visivi
description: Informazioni sul modo in cui gli oggetti visivi di Power BI possono filtrare altri oggetti visivi
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425046"
---
# <a name="power-bi-visual-filters-api"></a>API dei filtri degli oggetti visivi di Power BI

Il filtro degli oggetti visivi permette di filtrare i dati. La differenza principale rispetto alle selezioni consiste nel fatto che gli altri oggetti visivi verranno filtrati in qualsiasi modo, indipendentemente dal supporto dell'evidenziazione in tali oggetti visivi.

Per abilitare il filtro per l'oggetto visivo, questo deve contenere l'oggetto `filter` nella sezione `general`del contenuto di capabilities.json.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Le interfacce API per i filtri sono disponibili nel pacchetto [`powerbi-models`](https://www.npmjs.com/package/powerbi-models). Il pacchetto contiene anche classi per la creazione di istanze di filtro.

```cmd
npm install powerbi-models --save
```

Se si usano gli strumenti delle versioni precedenti (versione precedente a 3.x.x), è necessario includere `powerbi-models` nel pacchetto degli oggetti visivi. [Breve guida su come includere il pacchetto](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Tutti i filtri estendono l'interfaccia `IFilter`.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target`: colonna della tabella nell'origine dati.

## <a name="basic-filter-api"></a>API del filtro di base

L'interfaccia del filtro di base è la seguente

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator`: enumerazione con valori "In", "NotIn", "All"

`values`: valori per la condizione

Esempio di filtro di base:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Il filtro indica di fornire tutte le righe in cui `col1` è uguale a un valore tra 1, 2 o 3.

L'equivalente SQL è il seguente

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Per creare un filtro, è possibile usare la classe BasicFilter in `powerbi-models`.

Se si usa la versione precedente dello strumento, è necessario ottenere un'istanza dei modelli nell'oggetto finestra tramite `window['powerbi-models']`:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

L'oggetto visivo richiama il filtro usando il metodo applyJsonFilter() nell'interfaccia host IVisualHost fornita all'oggetto visivo nel costruttore.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>API del filtro avanzato

L'[API del filtro avanzato](https://github.com/Microsoft/powerbi-models) permette query complesse di selezione/filtro di punti dati tra oggetti visivi in base a più criteri, tra cui "LessThan", "Contains", "Is", "IsBlank" e così via.

Il filtro è stato introdotto nell'API degli oggetti visivi 1.7.0.

L'API del filtro avanzato richiede anche `target` con i nomi `table` e `column`. Tuttavia, gli operatori dell'API del filtro avanzato sono `"And" | "Or"`. 

Inoltre, il filtro usa condizioni invece di valori con l'interfaccia:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Gli operatori di condizione per il parametro `operator` sono `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

L'equivalente SQL è il seguente

```sql
SELECT * FROM table WHERE col1 < 0;
```

Il codice di esempio completo per usare l'API del filtro avanzato è disponibile nel [`Sampleslicer visual`repository](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>API del filtro di tuple (filtro multicolonna)

L'API del filtro di tuple è stata introdotta nell'API degli oggetti visivi 2.3.0.

Questa API è simile al filtro di base, ma permette di definire condizioni per diverse colonne e tabelle.

Un filtro ha questa interfaccia: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` è una matrice di colonne con nomi di tabella:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  Il filtro può riguardare colonne di tabelle diverse.

`$schema` è "http://powerbi.com/product/schema#tuple"

`filterType` è `FilterType.Tuple`

`operator` permette di usare solo l'operatore `"In"`

`values` è una matrice di tuple di valori, dove ogni tupla rappresenta una combinazione consentita dei valori della colonna di destinazione 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Esempio completo:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**L'ordine dei nomi di colonna e dei valori della condizione è importante.**

L'equivalente SQL è il seguente

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Ripristino del filtro JSON da DataView

A partire dall'API 2.2, i **filtri JSON** possono essere ripristinati da **VisualUpdateOptions**

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Power BI chiama il metodo `update` dell'oggetto visivo quando si usa il passaggio tra segnalibri e l'oggetto visivo ottiene l'oggetto `filter` corrispondente.
[Altre informazioni sul supporto dei segnalibri](bookmarks-support.md)

### <a name="sample-json-filter"></a>Filtro JSON di esempio

![Screenshot del filtro JSON](./media/json-filter.png)

### <a name="clear-json-filter"></a>Cancellare il filtro JSON

L'API del filtro accetta il valore `null` del filtro come reimpostazione o cancellazione.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
