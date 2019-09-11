---
title: Aggiungere una pagina di destinazione a oggetti visivi di Power BI
description: Questo articolo descrive come aggiungere una pagina di destinazione a oggetti visivi di Power BI.
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d15c52134fe3c8638625e50a1374867a4abed3c1
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236698"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Aggiungere una pagina di destinazione a oggetti visivi di Power BI

Con l'API 2.3.0 è possibile aggiungere una pagina di destinazione agli oggetti visivi di Power BI. A tale scopo, aggiungere la proprietà `supportsLandingPage` alle funzionalità e impostarla su true. Questa azione inizializza e aggiorna l'oggetto visivo prima dell'aggiunta di dati. Poiché l'oggetto visivo non mostra più una filigrana, è possibile progettare una pagina di destinazione personalizzata da visualizzare nell'oggetto visivo, purché non contenga dati.

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

Una pagina di destinazione di esempio è illustrata nell'immagine seguente:

![Screenshot della pagina di destinazione](./media/landing-page.png)
