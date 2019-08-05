---
title: Rendering di eventi
description: Gli oggetti visivi di Power BI possono indicare a Power BI che sono pronti per l'esportazione in PowerPoint/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425092"
---
# <a name="event-service"></a>Servizio eventi

La nuova API è costituita da tre metodi (Started, Finished e Failed) che devono essere chiamati durante il rendering.

All'avvio del rendering, il codice dell'oggetto visivo personalizzato chiama il metodo renderingStarted per indicare che il processo di rendering è stato avviato.

Se il rendering viene completato correttamente, il codice dell'oggetto visivo personalizzato chiama immediatamente il metodo `renderingFinished`, indicando ai listener (**soprattutto "Esporta in PDF" ed "Esporta in PowerPoint"** ) che l'immagine dell'oggetto visivo è pronta.

Si supponga un caso in cui si è verificato un problema durante il processo di rendering, impedendo il completamento dell'oggetto visivo personalizzato. Il codice dell'oggetto visivo personalizzato deve chiamare il metodo `renderingFailed` per indicare al listener che il processo di rendering non è stato completato. Questo metodo fornisce anche una stringa facoltativa per la causa dell'errore.

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
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Esempio semplice: l'oggetto visivo non include animazioni per il rendering

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

### <a name="sample-the-visual-with-animation"></a>Esempio: oggetto visivo con animazioni Oggetto visivo con animazioni

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
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Eventi di rendering per la certificazione degli oggetti visivi

Il supporto degli eventi di rendering da parte dell'oggetto visivo è uno dei requisiti della certificazione degli oggetti visivi. Per altre informazioni, vedere [Requisiti di certificazione](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
