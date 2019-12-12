---
title: Migrazione a powerbi-visuals-tools 3.x
description: Introduzione alla nuova versione di powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 245475feeb43ee544117aaa54969f2de1e207cd5
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696283"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Eseguire la migrazione alla nuova versione di powerbi-visuals-tools 3.x.x

A partire dalla versione 3, gli strumenti per oggetti visivi di Power BI usano Webpack per creare oggetti visivi personalizzati.
La nuova versione offre agli sviluppatori molte nuove opportunità per la creazione di oggetti visivi:

* TypeScript v3.x.x per impostazione predefinita. A partire da TypeScript 1.5 la nomenclatura è stata modificata. [Altre informazioni sui moduli TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

* I moduli ES6 sono supportati. Non è più necessario usare [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries). Usare invece le importazioni ES6.

* Le nuove versioni di [D3v5](https://d3js.org/) e altre librerie basate su moduli ES6 sono supportate.

* Dimensioni del pacchetto ridotte. Webpack usa il [tree shaking](https://webpack.js.org/guides/tree-shaking/) per rimuovere il codice inutilizzato. Il codice di JS viene ridotto e, di conseguenza, si ottiene un miglioramento delle prestazioni nel caricamento degli oggetti visivi.

* Prestazioni API migliorate.

* La libreria Globalize.js [è integrata](migrate-to-new-tools.md#remove-globalizejs-library) in formatting-utils.

* Gli strumenti usano [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) per visualizzare la codebase dell'oggetto visivo.

Di seguito sono descritti tutti i passaggi di migrazione per la nuova versione degli strumenti per oggetti visivi di Power BI.

## <a name="backward-compatibility"></a>Compatibilità con le versioni precedenti

I nuovi strumenti mantengono la compatibilità con le versioni precedenti per la codebase degli oggetti visivi precedenti, ma possono essere necessarie alcune modifiche aggiuntive per caricare le librerie esterne.

Le librerie, che supportano i sistemi di moduli, verranno importate come moduli Webpack. Verrà eseguito il wrapping di tutte le altre librerie e del codice sorgente dell'oggetto visivo in un unico modulo.

Le variabili globali come JQuery e Lodash usate negli strumenti pbiviz precedenti sono ora obsolete. Ciò significa che se il codice di un oggetto visivo precedente viene inoltrato su variabili globali, l'oggetto visivo può risultare danneggiato.

Nella versione precedente degli strumenti per oggetti visivi di Power BI era necessario definire una classe Visual nel modulo `powerbi.extensibility.visual`.

## <a name="how-to-install-powerbi-visuals-tools"></a>Come installare powerbi-visuals-tools

È possibile installare il nuovo set di strumenti eseguendo il comando

```cmd
npm install -g powerbi-visuals-tools
```

Esempio di oggetto visivo sampleBarChart e [modifiche](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) corrispondenti in `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Come installare l'API degli oggetti visivi personalizzati di Power BI

La nuova versione di powerbi-visual-tools non include al suo interno tutte le versioni dell'API. Lo sviluppatore deve invece installare una versione specifica del pacchetto [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api). La versione del pacchetto corrisponde alla versione API degli oggetti visivi personalizzati di Power BI e include tutte le definizioni dei tipi per l'API degli oggetti visivi personalizzati di Power BI.

Aggiungere `powerbi-visuals-api` nelle dipendenze di un progetto eseguendo il comando `npm install --save-dev powerbi-visuals-api`.
Rimuovere anche il collegamento alle definizioni dei tipi dell'API precedente. I tipi di `powerbi-visuals-api` vengono inclusi automaticamente da Webpack. Le modifiche corrispondenti sono in [questa](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) riga di `package.json`.

## <a name="update-tsconfigjson"></a>Aggiornare `tsconfig.json`

Per usare moduli esterni, è necessario cambiare l'opzione `out` in `outDir`.
`"outDir": "./.tmp/build/",` invece di `"out": "./.tmp/build/visual.js",`.

È necessario poiché i file TypeScript verranno compilati in file JavaScript in modo indipendente. Ecco perché non è più necessario specificare il file visual.js come output.

È anche possibile cambiare l'opzione `target` in `ES6` se si vuole usare codice JavaScript moderno come output. [È facoltativo](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Aggiornare le utilità degli oggetti visivi personalizzati

Se si usa una delle utilità powerbi-visuals-utils (https://www.npmjs.com/search?q=powerbi-visuals-utils)), è necessario aggiornare anche questa alla versione più recente.

Eseguire il comando `npm install powerbi-visuals-utils-<UTILNAME> --save`. Ad esempio, `npm install powerbi-visuals-utils-dataviewutils --save` per ottenere la nuova versione con i moduli esterni di TypeScript.

Un esempio è disponibile nel [repository](https://github.com/Microsoft/powerbi-visuals-mekkochart) Mekko Chart.
Questo oggetto visivo usa tutte le utilità.

## <a name="remove-globalizejs-library"></a>Rimuovere la libreria Globalize.js

La nuova versione di [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) include già globalize.js.
Non è necessario includere manualmente questa libreria nel progetto.
Tutte le localizzazioni necessarie verranno aggiunte automaticamente al pacchetto finale.

## <a name="fix-loading-external-libraries"></a>Correggere il caricamento di librerie esterne

Includere invece il nuovo file JS dopo le librerie nella matrice `externalJS` di `pbiviz.json`. Esempio:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importare le librerie nell'origine. Esempio per `lodash-es`:

```JS
import * as _ from "lodash-es";
```

dove `_` è la variabile globale per la libreria `lodash`.

## <a name="changes-in-the-visuals-sources"></a>Modifiche nelle origini degli oggetti visivi

La modifica principale consiste nella conversione dei moduli interni in moduli esterni poiché non è possibile usare moduli esterni all'interno di moduli interni.

Di seguito vengono descritte le modifiche che sono state applicate al grafico a barre di esempio

Le descrizioni dettagliate delle modifiche sono riportate di seguito:

1. Rimuovere tutte le definizioni dei moduli da ogni file del [codice sorgente](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importare le definizioni dell'API degli oggetti visivi personalizzati di Power BI](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importare](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) le interfacce o le classi necessarie dal modulo interno `powerbi`.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importare](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) la libreria D3.js

    ```typescript
    import * as d3 from "d3";
    ```

    Oppure importare solo i moduli della libreria D3 necessari

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importare](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) nel file di origine principale le utilità, le classi, le interfacce definite nel progetto dell'oggetto visivo

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importare gli stili CSS

La nuova versione degli strumenti consente agli sviluppatori di importare lo stile CSS o LESS direttamente nel codice TypeScript.

La [sezione degli stili](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) usata in precedenza viene pertanto ignorata dal compilatore.

Per usare il foglio di stile, aprire il file TS principale e aggiungere la riga seguente:  

```typescript
import "./../style/visual.less";
```  

Gli stili CSS e LESS verranno compilati automaticamente.  

### <a name="externaljs-section-in-pbivizjson"></a>Sezione externalJS in pbiviz.json

Gli strumenti [non richiedono](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) il caricamento di un elenco di `externalJS` nel bundle dell'oggetto visivo. Webpack include infatti tutte le librerie importate.

**La sezione externalJS in pbivi.json deve essere vuota.**

Chiamare i tipici comandi `npm run package` per creare il pacchetto dell'oggetto visivo oppure `npm run start` per avviare il server di sviluppo.

## <a name="updating-d3js-library-to-version-5"></a>Aggiornamento della libreria D3.js alla versione 5

Con i nuovi strumenti, è possibile iniziare a usare la nuova versione della libreria D3.js.

Chiamare i comandi per aggiornare D3 nel progetto dell'oggetto visivo

`npm install --save d3@5` per installare la nuova D3.js.

`npm install --save-dev @types/d3@5` per installare le nuove definizioni dei tipi per D3.js.

Sono state apportate modifiche importanti ed è necessario modificare il codice in modo che usi la nuova D3.js.

1. L'interfaccia `d3.Selection<T>` [è stata modificata](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) in `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. Non è possibile applicare diversi attributi tramite una singola chiamata al metodo `attr`. È [necessario passare](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) ogni attributo in una chiamata diversa al metodo `attr`. Il funzionamento è [simile](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) anche per il metodo `style`.

3. In D3.js v4 viene introdotto il nuovo metodo merge. Questo metodo viene comunemente usato per unire le selezioni di immissione e aggiornamento dopo un join di dati. [Chiamare il metodo merge](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) per usare correttamente D3.

[Altre informazioni](https://github.com/d3/d3/blob/master/CHANGES.md) sulle modifiche nella libreria D3.js.

## <a name="babel"></a>Babel

A partire dalla versione 3.1, gli strumenti usano Babel per compilare il nuovo codice JS moderno nel vecchio ES5 al fine di supportare un'ampia gamma di browser.

Questa opzione è abilitata per impostazione predefinita, ma è necessario importare manualmente il pacchetto [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill).

Eseguire il comando per installare il pacchetto

`npm install --save @babel/polyfill`

e importare il pacchetto nel punto iniziale del codice dell'oggetto visivo, in genere il file "src/visual.ts":

`import "@babel/polyfill";`

Per altre informazioni su Babel, vedere la [documentazione](https://babeljs.io/docs/en/).

Eseguire infine [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) per visualizzare la codebase dell'oggetto visivo.  

![Statistiche del codice dell'oggetto visivo](./media/webpack-stats.png)
