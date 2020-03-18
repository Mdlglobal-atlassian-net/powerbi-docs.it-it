---
title: Introduzione all'uso delle utilità per le descrizioni comandi negli oggetti visivi di Power BI
description: Questo articolo descrive come usare le utilità per le descrizioni comandi per semplificare la personalizzazione delle descrizioni comandi per gli oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 67470ec405806f44fdb483e857d222ad4ff05a45
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379169"
---
# <a name="tooltip-utils"></a>Utilità per le descrizioni comandi
Questo articolo spiega come installare, importare e usare le utilità per le descrizioni comandi. Questa utilità agevola la personalizzazione delle descrizioni comandi negli oggetti visivi di Power BI.

## <a name="requirements"></a>Requisiti
Per usare il pacchetto, devono essere disponibili gli elementi seguenti:
* [node.js](https://nodejs.org) (si consiglia la versione LTS più recente)
* [npm](https://www.npmjs.com/) (la versione minima supportata è 3.0.0)
* L'oggetto visivo personalizzato creato da [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installazione

Per installare il pacchetto, è necessario eseguire il comando seguente nella directory con l'oggetto visivo corrente:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Questo comando installa il pacchetto e aggiunge un pacchetto come dipendenza a ```package.json```

## <a name="usage"></a>Usage

> La guida all'utilizzo descrive un'API pubblica del pacchetto. Sono disponibili una descrizione e alcuni esempi per ogni interfaccia pubblica del pacchetto.

Il pacchetto consente di creare `TooltipServiceWrapper` e metodi che semplificano la gestione delle azioni di descrizione comando. Usa le interfacce di descrizione comando `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Include inoltre metodi specifici (gestori di eventi di tocco) correlati allo sviluppo per dispositivi mobili: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` offre il modo più semplice per modificare le descrizioni comandi.

Questo modulo include la funzione e l'interfaccia seguenti:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Interfacce](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Touch events](#touch-events)

### `createTooltipServiceWrapper`
Questa funzione crea un'istanza di ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService``` è disponibile in [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Esempio**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

È possibile esaminare il codice di esempio dell'oggetto visivo personalizzato [qui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391).

### `ITooltipServiceWrapper`
Questa interfaccia descrive i metodi pubblici di TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Questo metodo aggiunge le descrizioni comandi alla selezione corrente.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Esempio**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

È possibile esaminare il codice di esempio dell'oggetto visivo personalizzato [qui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931).

Prestare attenzione anche all'esempio di personalizzazione della descrizione comando in un oggetto visivo Gantt personalizzato [qui](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Questo metodo nasconde la descrizione comando.

```typescript
hide(): void;
```

**Esempio**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Queste interfacce vengono usate durante la creazione di TooltipServiceWrapper e il relativo utilizzo. Sono anche citate negli esempi dell'argomento precedente [qui](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Ora l'utilità per le descrizioni comandi è in grado di gestire diversi eventi di tocco utili per lo sviluppo di applicazioni per dispositivi mobili.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Questo metodo restituisce il nome dell'evento di inizio tocco.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Questo metodo restituisce il nome dell'evento di fine tocco.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Questo metodo indica se l'evento touchStart corrente è correlato o meno al puntatore.
