---
title: Eseguire il rendering degli eventi negli oggetti visivi di Power BI
description: Gli oggetti visivi di Power BI possono indicare a Power BI che sono pronti per l'esportazione in PowerPoint o PDF.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 873968a89a230171d8fecba81a7d528767ee7077
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819147"
---
# <a name="render-events-in-power-bi-visuals"></a>Eseguire il rendering degli eventi negli oggetti visivi di Power BI

La nuova API è costituita da tre metodi (`started`, `finished` o `failed`) che devono essere chiamati durante il rendering.

All'avvio del rendering, il codice dell'oggetto visivo di Power BI chiama il metodo `renderingStarted` per indicare che il processo di rendering è stato avviato.

Se il rendering viene completato correttamente, il codice dell'oggetto visivo di Power BI chiama immediatamente il metodo `renderingFinished`, indicando ai listener (principalmente *Esporta in PDF* ed *Esporta in PowerPoint*) che l'immagine dell'oggetto visivo è pronta.

Se si verifica un problema durante il processo, il rendering dell'oggetto visivo Power BI non può essere eseguito correttamente. Per segnalare ai listener che il processo di rendering non è stato completato, il codice dell'oggetto visivo di Power BI deve chiamare il metodo `renderingFailed`. Questo metodo include anche una stringa facoltativa per indicare la causa dell'errore.

## <a name="usage"></a>Usage

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Esempio: l'oggetto visivo non visualizza animazioni

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Esempio: l'oggetto visivo visualizza le animazioni

Se l'oggetto visivo include animazioni o funzioni asincrone per il rendering, il metodo `renderingFinished` deve essere chiamato dopo l'animazione o all'interno della funzione asincrona.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Eventi di rendering per la certificazione degli oggetti visivi

Il supporto degli eventi di rendering da parte dell'oggetto visivo è uno dei requisiti per la certificazione degli oggetti visivi. Per altre informazioni, vedere [Requisiti di certificazione](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements).
