---
title: Funzionalità e proprietà degli oggetti visivi di Power BI
description: Questo articolo descrive le funzionalità e le proprietà degli oggetti visivi di Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819193"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Aggiungere un menu di scelta rapida all'oggetto visivo di Power BI

Per fare in modo che Power BI visualizzi un menu di scelta rapida per l'oggetto visivo è possibile usare `selectionManager.showContextMenu()` con parametri `selectionId` e una posizione (come un oggetto `{x:, y:}`).

> [!IMPORTANT]
> `selectionManager.showContextMenu()` è stato introdotto nell'API degli oggetti visivi 2.2.0.

In genere viene aggiunto come un evento di clic con il pulsante destro del mouse o di pressione prolungata per i dispositivi di tocco. Il menu di scelta rapida è stato aggiunto al grafico a barre di esempio per riferimento:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
