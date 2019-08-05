---
title: Oggetti e proprietà
description: Proprietà personalizzabili degli oggetti visivi di Power BI
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424609"
---
# <a name="object-and-properties"></a>Oggetti e proprietà

Gli oggetti descrivono proprietà personalizzabili associate all'oggetto visivo.
Ogni oggetto può avere più proprietà e a ogni proprietà è associato un tipo.
I tipi indicano che cosa sarà la proprietà. Per altre informazioni sui tipi, vedere di seguito.

`myCustomObject` è il nome interno usato per fare riferimento all'oggetto in `dataView` e `enumerateObjectInstances`

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nome visualizzato

`displayName` è il nome che verrà mostrato nel riquadro delle proprietà.

## <a name="properties"></a>Proprietà

`properties` è una mappa delle proprietà definite dallo sviluppatore.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` è una proprietà speciale che abilita un'opzione per attivare o disattivare l'oggetto.

Esempio:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Tipi di proprietà

Esistono due tipi di proprietà: `ValueTypeDescriptor` e `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>ValueTypeDescriptor

I tipi `ValueTypeDescriptor` sono principalmente tipi primitivi e in genere vengono usati come oggetto statico.
Ecco alcuni dei tipi `ValueTypeDescriptor` più comuni

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>StructuralTypeDescriptor

I tipi `StructuralTypeDescriptor` vengono usati principalmente per oggetti associati a dati.
Il tipo `StructuralTypeDescriptor` più comune è fill

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Proprietà Gradient

La proprietà Gradient è una proprietà che non può essere impostata come proprietà standard. È invece necessario impostare una regola per la sostituzione della proprietà di selezione del colore (tipo riempimento).
Vedere l'esempio seguente:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Prestare attenzione alle proprietà `"fill"` e `"fillRule"`. La prima è il selettore dei colori, mentre la seconda è la regola di sostituzione per la sfumatura che sostituisce la proprietà "fill" `visually` quando vengono soddisfatte le condizioni della regola.

Questo collegamento tra la proprietà fill e la regola di sostituzione è impostato nella sezione `"rule"`->`"output"` della proprietà `"fillRule"`.

`"Rule"`->`"InputRole"` imposta il ruolo dati che attiva la regola (condizione). In questo esempio se il ruolo dati `"Gradient"` contiene dati, verrà applicata la regola per la proprietà `"fill"`.

Di seguito è possibile osservare un esempio del ruolo dati che attiva la regola di riempimento (`the last item`).

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="enumerateobjectinstances-method"></a>Metodo `enumerateObjectInstances`

Per usare in modo efficace gli oggetti, è necessaria una funzione nell'oggetto visivo personalizzato denominata `enumerateObjectInstances`. Questa funzione immetterà oggetti nel riquadro delle proprietà e determinerà anche la posizione in cui gli oggetti devono essere associati all'interno di dataView.  

Di seguito viene mostrato l'aspetto di una configurazione tipica:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Proprietà

Le proprietà in `enumerateObjectInstances` rifletteranno le proprietà definite nelle funzionalità. Vedere l'esempio nella parte inferiore della pagina.

### <a name="objects-selector"></a>Selettore di oggetti

Il selettore in `enumerateObjectInstances` determina la posizione in cui ogni oggetto verrà associato a dataView. Sono disponibili quattro opzioni diverse.

#### <a name="static"></a>static

Questo oggetto verrà associato a metadati `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>columns

Questo oggetto verrà associato a colonne con `QueryName` corrispondente.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Questo oggetto verrà associato all'elemento per cui è stato creato un oggetto `selectionID`. In questo esempio si presuppone che siano stati creati `selectionID` per alcuni punti dati e di eseguire un ciclo tra di essi.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>ScopeIdentity

Questo oggetto verrà associato a valori specifici all'intersezione dei gruppi. Se, ad esempio, sono presenti categorie `["Jan", "Feb", "March", ...]` e serie `["Small", "Medium", "Large"]`, può essere necessario un oggetto all'intersezione dei valori che corrispondono a `Feb` e `Large`. A questo scopo, è possibile ottenere il valore di `DataViewScopeIdentity` di entrambe le colonne, eseguirne il push alla variabile `identities` e usare questa sintassi con il selettore.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Esempio

In questo esempio viene mostrato l'aspetto di un oggetto objectEnumeration per un oggetto customColor con una proprietà `fill`. Questo oggetto deve essere associato in modo statico a `dataViews[index].metadata.objects`

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
