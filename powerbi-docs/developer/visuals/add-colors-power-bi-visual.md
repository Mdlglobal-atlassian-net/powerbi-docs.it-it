---
title: Aggiungere colori agli oggetti visivi di Power BI
description: Questo articolo descrive come aggiungere i colori agli oggetti visivi di Power BI e come gestire i punti dati per un oggetto visivo con colori.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141157"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Aggiungere colori agli oggetti visivi di Power BI

Questo articolo descrive come aggiungere i colori agli oggetti visivi e come gestire i punti dati per un oggetto visivo a colori.

`IVisualHost` espone il colore come uno dei suoi servizi.
Il codice di esempio in questo articolo modifica l'[oggetto visivo SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Per il codice sorgente, vedere [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Per iniziare a creare oggetti visivi, vedere [Sviluppare un oggetto visivo di Power BI](custom-visual-develop-tutorial.md).

## <a name="add-color-to-data-points"></a>Aggiungere il colore ai punti dati

Ogni punto dati è rappresentato con un colore diverso.
Aggiungere il colore all'interfaccia `BarChartDataPoint`, come nell'esempio seguente:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Usare il servizio tavolozza colori

Il servizio `colorPalette` gestisce i colori usati nell'oggetto visivo.
Un'istanza del servizio è disponibile in `IVisualHost`.

Definirla nel metodo `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Assegnare il colore ai punti dati

Specificare quindi `dataPoints`.
In questo esempio ogni `dataPoints` include valore, categoria e colore.
`dataPoints` può includere anche altre proprietà.

In `SampleBarChart` il metodo `visualTransform` incapsula il calcolo di `dataPoints`.
Questo metodo fa parte dell'elemento ViewModel del grafico a barre.
Poiché il metodo esegue l'iterazione del calcolo di `dataPoints` in `visualTransform`, è il luogo ideale per assegnare i colori, come nel codice seguente:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Applicare quindi i dati da `dataPoints` nell'oggetto `barSelection` di selezione [D3](https://d3js.org/) all'interno del metodo `update`:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sugli oggetti visivi di Power BI, vedere [Funzionalità e proprietà degli oggetti visivi di Power BI](capabilities.md).

Per altre informazioni sullo sviluppo di oggetti visivi di Power BI, vedere [Come eseguire il debug degli oggetti visivi di Power BI](visuals-how-to-debug.md) e [Risoluzione dei problemi relativi agli oggetti visivi di Power BI](power-bi-custom-visuals-troubleshoot.md).
