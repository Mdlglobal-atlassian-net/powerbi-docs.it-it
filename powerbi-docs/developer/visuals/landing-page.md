---
title: Pagina di destinazione
description: Come aggiungere una pagina di destinazione a oggetti visivi di Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 44cc9314b31803c97d3203d4aab846685d8f88fa
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424885"
---
# <a name="landing-page"></a>Pagina di destinazione

Con l'API 2.3.0 è possibile aggiungere una pagina di destinazione all'oggetto visivo. A questo scopo, aggiungere la proprietà `supportsLandingPage` alle funzionalità e impostarla su true. L'oggetto visivo verrà inizializzato e aggiornato ancora prima di aggiungervi dati, ovvero non mostrerà più una filigrana, in modo da poter progettare una pagina di destinazione personalizzata da visualizzare nell'oggetto visivo, purché non contenga dati.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Esempio

![Screenshot della pagina di destinazione](./media/landing-page.png)
