---
title: Utilità di interattività per gli oggetti visivi di Power BI
description: Questo articolo descrive come aggiungere selezioni negli oggetti visivi di Power BI usando l'utilità di interattività
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8a9218085b0da655d1ce4b3ece0b2666c4826c86
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061869"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Utilità di interattività per gli oggetti visivi di Microsoft Power BI

InteractivityUtils è un set di funzioni e classi che consentono di semplificare l'implementazione di selezione incrociata e filtro incrociato per gli oggetti visivi personalizzati di Power BI.

## <a name="installation"></a>Installazione

> [!NOTE]
> Se si continua a usare la versione precedente di powerbi-visuals-tools (numero di versione inferiore a 3.x.x), installare la nuova versione degli strumenti (3.x.x).

> [!IMPORTANT]
> I nuovi aggiornamenti dell'utilità di interattività supporteranno solo la versione più recente degli strumenti. [Altre informazioni su come aggiornare il codice degli oggetti visivi da usare con gli strumenti più recenti](migrate-to-new-tools.md)

Per installare il pacchetto, è necessario eseguire il comando seguente nella directory con l'oggetto visivo personalizzato corrente:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

A partire dalla versione 3.0 o successive, è necessario installare anche ```powerbi-models``` per risolvere le dipendenze.

```bash
npm install powerbi-models --save
```

Per usare l'utilità di interattività è necessario importare il componente necessario nel codice sorgente dell'oggetto visivo.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Inclusione di artefatti CSS nell'oggetto visivo personalizzato

Per usare il pacchetto con gli oggetti visivi personalizzati, è necessario importare il file CSS seguente nel file `your.less`:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Si otterrà quindi la struttura di file seguente:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> È necessario importare il file con estensione css come file con estensione less, perché gli strumenti per oggetti visivi di Power BI eseguono il wrapping delle regole CSS esterne.

## <a name="usage"></a>Usage

### <a name="define-interface-for-data-points"></a>Definire l'interfaccia per i punti dati

I punti dati contengono in genere selezioni e valori. L'interfaccia estende l'interfaccia `SelectableDataPoint`. `SelectableDataPoint` contiene già proprietà:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

Il primo passaggio dell'uso dell'utilità di interattività prevede la creazione di un'istanza dell'utilità di interattività e il salvataggio dell'oggetto come proprietà dell'oggetto visivo

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

Il secondo passaggio consiste nell'estendere la classe di comportamento di base:

> [!NOTE]
> La classe BaseBehavior è stata introdotta nella [versione 5.6.x dell'utilità di interattività](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Se si usa una versione precedente, creare la classe di comportamento dall'esempio seguente (la classe `BaseBehavior` è la stessa):

Definire l'interfaccia per le opzioni della classe di comportamento:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Definire la classe per `visual behaviour`. La classe è responsabile della gestione degli eventi del mouse `click`, `contextmenu`.
Quando si usano i clic agli elementi dati, l'oggetto visivo chiama il gestore di selezione per selezionare i punti dati. Se l'utente fa clic sull'elemento di sfondo dell'oggetto visivo, la selezione viene annullata. La classe ha i metodi corrispondenti: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

In alternativa, è possibile estendere la classe`BaseBehavior`:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Per gestire i clic sugli elementi, chiamare il metodo `on` dell'oggetto di selezione D3 (anche per elementsSelection e clearCatcherSelection):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Aggiungere un gestore simile per l'evento `contextmenu` per chiamare il metodo `showContextMenu` di gestione selezione:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

L'utilità di interattività chiama i metodi `bindEvents` per assegnare le funzioni ai gestori e aggiungere le chiamate di `bindClick`, `bindClearCatcher` e `bindContextMenu` nel metodo `bindEvents`:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

Il metodo `renderSelection` è responsabile dell'aggiornamento dello stato degli oggetti visivi degli elementi nel grafico.

Esempio d implementazione del metodo `renderSelection`:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

L'ultimo passaggio consiste nella creazione dell'istanza di `visual behavior` e nella chiamata del metodo `bind` dell'istanza dell'utilità di interattività:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` è l'oggetto di selezione D3, che rappresenta tutti gli elementi selezionabili nell'oggetto visivo.

* `select(this.target)` è l'oggetto di selezione D3, che rappresenta gli elementi DOM principali dell'oggetto visivo.

* Punti dati `this.categories` con elementi, dove l'interfaccia è `VisualDataPoint` (o `categories: VisualDataPoint[];`)

* `this.behavior` è una nuova istanza di `visual behavior`

  creata nel costruttore dell'oggetto visivo:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

L'oggetto visivo è ora pronto per la selezione del gestore.

## <a name="next-steps"></a>Passaggi successivi

* [Informazioni su come gestire le selezioni sul passaggio tra segnalibri](bookmarks-support.md#visuals-with-selection)

* [Informazioni su come aggiungere un menu di scelta rapida per i punti dati degli oggetti visivi](context-menu.md)

* [Informazioni su come usare la gestione selezione per aggiungere selezioni negli oggetti visivi di Power BI](selection-api.md)
