---
title: Utilità di interattività per gli oggetti visivi di Power BI
description: Questo articolo descrive come aggiungere selezioni negli oggetti visivi di Power BI usando l'utilità di interattività
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/24/2020
ms.openlocfilehash: 3614505cec185779bce3f63c6e7a565a5ef39443
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920885"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Utilità di interattività per gli oggetti visivi di Power BI

L'utilità di interattività (`InteractivityUtils`) è un set di funzioni e classi che consentono di semplificare l'implementazione di selezione incrociata e filtro incrociato.

> [!NOTE]
> I nuovi aggiornamenti dell'utilità di interattività supportano solo la versione più recente degli strumenti (3.x.x e versioni successive).

## <a name="installation"></a>Installazione

1. Per installare il pacchetto, eseguire il comando seguente nella directory con l'oggetto visivo di Power BI corrente.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Se si usa la versione 3.0 o successiva dello strumento, installare `powerbi-models` per risolvere le dipendenze.

    ```bash
    npm install powerbi-models --save
    ```

3. Per usare l'utilità di interattività, importare il componente necessario nel codice sorgente dell'oggetto visivo di Power BI.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Inclusione dei file CSS

Per usare il pacchetto con gli oggetti visivi di Power BI, è necessario importare il file CSS seguente nel file `.less`.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importare il file CSS come file `.less` perché lo strumento per gli oggetti visivi di Power BI esegue il wrapping delle regole CSS esterne.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>Proprietà SelectableDataPoint

I punti dati contengono in genere selezioni e valori. L'interfaccia estende l'interfaccia `SelectableDataPoint`.

`SelectableDataPoint` contiene già le proprietà descritte di seguito.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definizione di un'interfaccia per i punti dati

1. Creare un'istanza dell'utilità di interattività e salvare l'oggetto come proprietà dell'oggetto visivo

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

2. Estendere la classe del comportamento di base.

    > [!NOTE]
    > La classe `BaseBehavior` è stata introdotta nella [versione 5.6.x dell'utilità di interattività](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Se si usa una versione precedente, creare la classe di comportamento dall'esempio seguente.

3. Definire l'interfaccia per le opzioni della classe di comportamento.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Definire una classe per `visual behavior`. In alternativa, estendere la classe `BaseBehavior`.

    **Definizione di una classe per `visual behavior`**

    La classe è responsabile della gestione degli eventi del mouse `click` `contextmenu`.

    Quando un utente fa clic sugli elementi dati, l'oggetto visivo chiama il gestore di selezione per selezionare i punti dati. Se l'utente fa clic sull'elemento di sfondo dell'oggetto visivo, viene chiamato il gestore di cancellazione della selezione.

    La classe ha i metodi corrispondenti indicati di seguito:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **Estensione della classe `BaseBehavior`**

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

5. Per gestire il clic sugli elementi, chiamare il metodo `on` dell'oggetto di selezione *d3*. Questo vale anche per `elementsSelection` e `clearCatcherSelection`.

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

6. Aggiungere un gestore simile per l'evento `contextmenu` per chiamare il metodo `showContextMenu` di gestione selezione.

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

7. Per assegnare le funzioni ai gestori, l'utilità di interattività chiama il metodo `bindEvents`. Aggiungere le chiamate seguenti al metodo `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. Il metodo `renderSelection` è responsabile dell'aggiornamento dello stato di visualizzazione degli elementi nel grafico. Di seguito è riportata un'implementazione di esempio di `renderSelection`.

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

9. L'ultimo passaggio consiste nella creazione di un'istanza di `visual behavior` e nella chiamata del metodo `bind` dell'istanza dell'utilità di interattività.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` è l'oggetto di selezione *d3*, che rappresenta tutti gli elementi selezionabili dell'oggetto visivo.
    * `select(this.target)` è l'oggetto di selezione *d3*, che rappresenta gli elementi DOM principali dell'oggetto visivo.
    * `this.categories` rappresenta i punti dati con elementi, dove l'interfaccia è `VisualDataPoint` o `categories: VisualDataPoint[];`.
    * `this.behavior` è una nuova istanza di `visual behavior` creata nel costruttore dell'oggetto visivo, come illustrato di seguito.

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
## <a name="next-steps"></a>Passaggi successivi

* [Informazioni su come gestire le selezioni sul passaggio tra segnalibri](bookmarks-support.md#visuals-with-selection)

* [Informazioni su come aggiungere un menu di scelta rapida per i punti dati degli oggetti visivi](context-menu.md)

* [Informazioni su come usare la gestione selezione per aggiungere selezioni negli oggetti visivi di Power BI](selection-api.md)
