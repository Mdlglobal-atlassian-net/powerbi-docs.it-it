---
title: Introduzione all'uso delle utilità per SVG negli oggetti visivi di Power BI
description: Questo articolo descrive come usare le utilità per SVG per semplificare le modifiche del formato SVG per gli oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: aa1ac8074e842a51b369c48f57c4b5016a80140c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377973"
---
# <a name="svg-utils"></a>Utilità per SVG

SVGUtils è un set di funzioni e classi per semplificare le modifiche del formato SVG per gli oggetti visivi di Power BI

## <a name="installation"></a>Installazione

Per installare il pacchetto, è necessario eseguire il comando seguente nella directory con l'oggetto visivo corrente:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

Il modulo `CssConstants` fornisce la funzione e l'interfaccia speciali per lavorare con i selettori di classe.

Il modulo `powerbi.extensibility.utils.svg.CssConstants` fornisce la funzione e l'interfaccia seguenti:

## <a name="classandselector"></a>ClassAndSelector

Questa interfaccia descrive le proprietà comuni del selettore di classe.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Questa funzione crea un'istanza di ClassAndSelector con il nome specificato della classe.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Example:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

Il modulo `manipulation` fornisce alcune funzioni speciali per generare stringhe da usare con la proprietà Transform di SVG.

Il modulo fornisce le funzioni seguenti:

### <a name="translate"></a>translate

Questa funzione crea una stringa translate da usare con la proprietà Transform di SVG.

```typescript
function translate(x: number, y: number): string;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Questa funzione crea una stringa translateX da usare con la proprietà Transform di SVG.

```typescript
function translateXWithPixels(x: number): string;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Questa funzione crea una stringa translate da usare con la proprietà Transform di SVG.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Questa funzione crea una stringa translate-rotate da usare con la proprietà Transform di SVG.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scala

Questa funzione crea una stringa scale da usare con la proprietà Transform CSS.

```typescript
function scale(scale: number): string;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Questa funzione crea una stringa transform-origin da usare con la proprietà transform-origin CSS.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Questa funzione impone il completamento di ogni transizione di D3.

```typescript
function flushAllD3Transitions(): void;
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Questa funzione analizza la stringa transform con il valore "translate(x,y)".

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Questa funzione crea una freccia.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Example:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

Il modulo `Rect` fornisce alcune funzioni speciali per modificare i rettangoli.

Il modulo fornisce le funzioni seguenti:

### <a name="getoffset"></a>getOffset

Questa funzione restituisce un offset del rettangolo.

```typescript
function getOffset(rect: IRect): IPoint;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Questa funzione restituisce le dimensioni del rettangolo.

```typescript
function getSize(rect: IRect): ISize;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Questa funzione modifica le dimensioni del rettangolo.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Questa funzione restituisce una posizione destra del rettangolo.

```typescript
function right(rect: IRect): number;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Questa funzione restituisce una posizione inferiore del rettangolo.

```typescript
function bottom(rect: IRect): number;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Questa funzione restituisce una posizione superiore sinistra del rettangolo.

```typescript
function topLeft(rect: IRect): IPoint;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Questa funzione restituisce una posizione superiore destra del rettangolo.

```typescript
function topRight(rect: IRect): IPoint;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Questa funzione restituisce una posizione inferiore sinistra del rettangolo.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Questa funzione restituisce una posizione inferiore destra del rettangolo.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Esempio

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Questa funzione crea una copia del rettangolo.

```typescript
function clone(rect: IRect): IRect;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Questa funzione converte il rettangolo in stringa.

```typescript
function toString(rect: IRect): string;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Questa funzione applica l'offset specificato al rettangolo.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Questa funzione aggiunge il primo rettangolo al secondo rettangolo.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Questa funzione restituisce il punto più vicino al punto specificato nel rettangolo.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Questa funzione confronta i rettangoli e restituisce true se sono uguali.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Questa funzione confronta i rettangoli considerando la precisione dei valori.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Questa funzione controlla se il rettangolo è vuoto.

```typescript
function isEmpty(rect: IRect): boolean;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Questa funzione controlla se il rettangolo contiene il punto.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Questa funzione controlla se i rettangoli si intersecano.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Questa funzione restituisce un'intersezione di rettangoli.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Questa funzione combina i rettangoli.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Questa funzione restituisce un punto centrale del rettangolo.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Example:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>indicatore di misura

Il modulo `pointer` fornisce una funzione speciale per ottenere la posizione dell'indicatore di misura.

Il modulo fornisce le funzioni seguenti:

### <a name="getcoordinates"></a>getCoordinates

Questa funzione restituisce la posizione dell'indicatore di misura.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Example:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
