---
title: API dei filtri degli oggetti visivi negli oggetti visivi di Power BI
description: Questo articolo illustra il modo in cui gli oggetti visivi di Power BI possono filtrare altri oggetti visivi.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 95e661e81e7753d0a28806cca5d652f8e92666a8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114107"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>API dei filtri degli oggetti visivi negli oggetti visivi di Power BI

L'API dei filtri visivi consente di filtrare i dati negli oggetti visivi di Power BI. La differenza principale rispetto alle altre selezioni consiste nel fatto che gli altri oggetti visivi verranno filtrati in qualsiasi modo, indipendentemente dal supporto dell'evidenziazione in tali oggetti visivi.

Per abilitare il filtro per l'oggetto visivo, questo deve contenere l'oggetto `filter` nella sezione `general` del codice di *capabilities.json*.

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

Le interfacce API per i filtri degli oggetti visivi sono disponibili nel pacchetto [powerbi-models](https://www.npmjs.com/package/powerbi-models). Il pacchetto contiene anche classi per la creazione di istanze di filtro.

```cmd
npm install powerbi-models --save
```

Se si usa una versione meno recente degli strumenti (precedente a 3.x.x), è necessario includere `powerbi-models` nel pacchetto degli oggetti visivi. Per altre informazioni, vedere la guida [Aggiungere l'API del filtro avanzato all'oggetto visivo personalizzato](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md).

Tutti i filtri estendono l'interfaccia `IFilter`, come illustrato nel codice seguente:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Dove:
* `target` è la colonna della tabella nell'origine dati.

## <a name="the-basic-filter-api"></a>API del filtro di base

L'interfaccia del filtro di base è illustrata nel codice seguente:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Dove:
* `operator` è un'enumerazione con i valori *In*, *NotIn* e *All*.
* `values` sono i valori per la condizione.

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

Il filtro indica di fornire tutte le righe in cui `col1` è uguale al valore 1, 2 o 3.

L'equivalente SQL è il seguente:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Per creare un filtro, è possibile usare la classe BasicFilter in `powerbi-models`.

Se si usa una versione precedente dello strumento, è necessario ottenere un'istanza dei modelli nell'oggetto finestra usando `window['powerbi-models']`, come illustrato nel codice seguente:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

L'oggetto visivo richiama il filtro usando il metodo applyJsonFilter() nell'interfaccia host, IVisualHost, che viene fornita all'oggetto visivo nel costruttore.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>API del filtro avanzato

L'[API del filtro avanzato](https://github.com/Microsoft/powerbi-models) permette query complesse di selezione e filtro di punti dati tra oggetti visivi in base a più criteri, tra cui *LessThan*, *Contains*, *Is*, *IsBlank* e così via.

Il filtro è stato introdotto nell'API degli oggetti visivi 1.7.0.

Anche l'API del filtro avanzato richiede `target` con i nomi `table` e `column`. Tuttavia, gli operatori dell'API del filtro avanzato sono *And* e *Or*. 

Inoltre, il filtro usa condizioni invece di valori con l'interfaccia:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Gli operatori di condizione per il parametro `operator` sono *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* e "IsNotBlank"`

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

L'equivalente SQL è il seguente:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Per il codice di esempio completo per l'uso dell'API del filtro avanzato, vedere il [repository dell'oggetto visivo Sampleslicer](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="the-tuple-filter-api-multi-column-filter"></a>API del filtro di tuple (filtro multicolonna)

L'API del filtro di tuple è stata introdotta nell'API degli oggetti visivi 2.3.0. È simile all'API del filtro di base, ma permette di definire condizioni per diverse colonne e tabelle.

L'interfaccia del filtro è illustrata nel codice seguente: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Dove:
* `target` è una matrice di colonne con nomi di tabella:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  Il filtro può riguardare colonne di varie tabelle.

* `$schema` è https://powerbi.com/product/schema#tuple.

* `filterType` è *FilterType.Tuple*.

* `operator` consente l'uso solo nell'operatore *In*.

* `values` è una matrice di tuple di valori e ogni tupla rappresenta una combinazione consentita dei valori della colonna di destinazione. 

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
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "https://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> L'ordine dei nomi di colonna e dei valori della condizione è importante.

L'equivalente SQL è il seguente:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Ripristinare il filtro JSON dalla vista dati

A partire dall'API versione 2.2, è possibile ripristinare il filtro JSON da *VisualUpdateOptions*, come illustrato nel codice seguente:

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

Quando si passa da un segnalibro all'altro, Power BI chiama il metodo `update` dell'oggetto visivo e l'oggetto visivo ottiene l'oggetto `filter` corrispondente. Per altre informazioni, vedere [Aggiungere il supporto dei segnalibri per gli oggetti visivi di Power BI](bookmarks-support.md).

### <a name="sample-json-filter"></a>Filtro JSON di esempio

Nell'immagine seguente è illustrato il codice del filtro JSON di esempio:

![Codice del filtro JSON](media/filter-api/json-filter.png)

### <a name="clear-the-json-filter"></a>Cancellare il filtro JSON

L'API del filtro accetta il valore `null` del filtro come *reimpostazione* o *cancellazione*.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
