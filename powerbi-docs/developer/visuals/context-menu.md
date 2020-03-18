---
title: Funzionalità e proprietà degli oggetti visivi di Power BI
description: Questo articolo descrive le funzionalità e le proprietà degli oggetti visivi di Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1e2fbe3288e5dbb759a56ad1c299db2e277408b2
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380756"
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
