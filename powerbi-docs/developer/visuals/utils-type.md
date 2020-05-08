---
title: Introduzione all'uso delle utilità per i tipi negli oggetti visivi di Power BI
description: Questo articolo descrive come usare le utilità per SVG per estendere i tipi di base per gli oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 5a3cfb7ea9c9f398193b45652aa43c6b83c8f70b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377996"
---
# <a name="type-utils"></a>Utilità per i tipi

TypeUtils è un set di funzioni e classi per estendere i tipi di base per gli oggetti visivi di Power BI.

## <a name="installation"></a>Installazione

Per installare il pacchetto, è necessario eseguire il comando seguente nella directory con l'oggetto visivo personalizzato corrente:

npm install powerbi-visuals-utils-typeutils --save Questo comando installa il pacchetto e aggiunge un pacchetto come dipendenza al file package.json

## <a name="double"></a>Double

Il modulo `Double` fornisce funzionalità per modificare la precisione dei numeri.

Il modulo fornisce le funzioni seguenti:

### <a name="pow10"></a>pow10

Questa funzione restituisce la potenza di 10.

```typescript
function pow10(exp: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Questa funzione restituisce un logaritmo in base 10 del numero.

```typescript
function log10(val: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Questa funzione restituisce una potenza di 10 che rappresenta la precisione del numero.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Questa funzione controlla se un delta tra due numeri è inferiore alla precisione specificata.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Questa funzione controlla se il primo valore è minore del secondo.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Questa funzione controlla se il primo valore è minore o uguale al secondo.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Questa funzione controlla se il primo valore è maggiore del secondo.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Questa funzione controlla se il primo valore è maggiore o uguale al secondo.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Questa funzione arrotonda per difetto il numero con la precisione specificata.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Questa funzione `ceils` il numero con la precisione specificata.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Questa funzione arrotonda per difetto il numero alla precisione specificata.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Questa funzione `ceils` il numero alla precisione specificata.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Questa funzione arrotonda il numero alla precisione specificata.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Questa funzione restituisce un numero compreso tra il valore minimo e il valore massimo.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Questa funzione arrotonda il numero.

```typescript
function round(x: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Questa funzione rimuove i decimali non significativi.

```typescript
function removeDecimalNoise(value: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Questa funzione controlla se il numero è intero.

```typescript
function isInteger(value: number): boolean;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Questa funzione incrementa il numero in base al numero specificato e restituisce il numero arrotondato.

```typescript
function toIncrement(value: number, increment: number): number;
```

Example:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototipo

Il modulo `Prototype` fornisce funzionalità per ereditare oggetti.

Il modulo fornisce le funzioni seguenti:

## <a name="inherit"></a>inherit

Questa funzione restituisce un nuovo oggetto con l'oggetto specificato come prototipo.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Example:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Questa funzione restituisce un nuovo oggetto con l'oggetto specificato come prototipo se e solo se il prototipo non è stato impostato.

```typescript
function inheritSingle<T>(obj: T): T;
```

Example:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

Il modulo `PixelConverter` consente di convertire i pixel in punti e i punti in pixel.

Il modulo fornisce le funzioni seguenti:

## <a name="tostring"></a>toString

Questa funzione converte il valore in pixel in una stringa.

```typescript
function toString(px: number): string;
```

Example:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Questa funzione converte il valore in punti specificato nel valore in pixel e restituisce l'interpretazione della stringa.

```typescript
function fromPoint(pt: number): string;
```

Example:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Questa funzione converte il valore in punti specificato nel valore in pixel.

```typescript
function fromPointToPixel(pt: number): number;
```

Example:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Questa funzione converte il valore in pixel specificato nel valore in punti.

```typescript
function toPoint(px: number): number;
```

Example:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
