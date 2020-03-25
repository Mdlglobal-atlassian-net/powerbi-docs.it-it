---
title: Aggiunta di librerie esterne a oggetti visivi di Power BI
description: Questo articolo descrive come usare le librerie esterne negli oggetti visivi di Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114130"
---
# <a name="adding-external-libraries"></a>Aggiunta di librerie esterne

Questo articolo descrive come usare le librerie esterne negli oggetti visivi di Power BI. Include informazioni sull'installazione, l'importazione e la chiamata di librerie esterne dal codice dell'oggetto visivo di Power BI.

## <a name="javascript-libraries"></a>Librerie JavaScript

1. Installare una libreria JavaScript esterna usando una qualsiasi soluzione di gestione pacchetti, ad esempio *npm* o *yarn*.
2. Importare i moduli necessari nei file di origine usando la libreria esterna.

>[!NOTE]
>Se si vuole aggiungere tipi alla libreria JavaScript e ottenere protezione IntelliSense e in fase di compilazione, assicurarsi di installare il pacchetto appropriato.

### <a name="installing-the-d3-library"></a>Installazione della libreria d3

Questo è un esempio di installazione della libreria [d3](https://www.npmjs.com/package/d3) e del pacchetto [@types/d3](https://www.npmjs.com/package/@types/d3) usando [npm](https://www.npmjs.com/).

Per un esempio completo, vedere il codice [Visualizzazioni di Power BI](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Installare il pacchetto *d3* e il pacchetto *d3 types*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importare la libreria *d3* nei file che la usano, ad esempio `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>Framework CSS

1. Installare un framework CSS esterno usando una qualsiasi soluzione di gestione pacchetti, ad esempio *npm* o *yarn*.
2. Nel file `.less` dell'oggetto visivo, includere l'istruzione `import`.

### <a name="installing-bootstrap"></a>Installazione di bootstrap

Questo è un esempio di installazione di [bootstrap](https://www.npmjs.com/package/bootstrap) con [npm](https://www.npmjs.com/).

Per un esempio completo, vedere il codice [Visualizzazioni di Power BI](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Installare il pacchetto *bootstrap*.

    ```powershell
    npm install bootstrap --save
    ```

2. Includere l'istruzione `import` in `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
