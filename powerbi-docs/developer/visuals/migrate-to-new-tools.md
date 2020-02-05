---
title: Eseguire la migrazione a powerbi-visuals-tools versione 3.x
description: Introduzione alla nuova versione di powerbi-visuals-tools
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818825"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Eseguire la migrazione al nuovo powerbi-visuals-tools versione 3.*x*

A partire dalla versione 3, gli strumenti per oggetti visivi di Power BI (powerbi-visuals-tools o `pbiviz`) usano webpack per creare oggetti visivi personalizzati.
La nuova versione offre agli sviluppatori molti miglioramenti per la creazione di oggetti visivi:

- Per impostazione predefinita, viene usato TypeScript versione 3.*x*. A partire da TypeScript 1.5, la nomenclatura è stata modificata. [Altre informazioni sui moduli TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

- Sono supportati i moduli ECMAScript 6 (ES6). Usare ora le importazioni ES6 invece di [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Sono supportate le nuove versioni di Data-Driven Documents ([D3v5](https://d3js.org/)) e altre librerie basate su moduli ES6.

- Dimensioni del pacchetto ridotte. Webpack usa il [tree shaking](https://webpack.js.org/guides/tree-shaking/) per rimuovere il codice inutilizzato, riducendo il codice JavaScript e offrendo prestazioni migliori per il caricamento degli oggetti visivi.

- Prestazioni API migliorate.

- La libreria Globalize.js [è integrata](migrate-to-new-tools.md#remove-the- globalizejs-library) in FormattingUtils.

- Gli strumenti per oggetti visivi di Power BI usano [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) per visualizzare la codebase dell'oggetto visivo.

Questo articolo descrive tutti i passaggi di migrazione per la nuova versione degli strumenti per oggetti visivi di Power BI.

## <a name="backward-compatibility"></a>Compatibilità con le versioni precedenti

I nuovi strumenti mantengono la compatibilità con le versioni precedenti per la codebase degli oggetti visivi precedenti, ma possono essere necessarie alcune modifiche aggiuntive per caricare le librerie esterne.

Le librerie che supportano i sistemi di moduli vengono importate come moduli webpack. Per tutte le altre librerie e per il codice sorgente dell'oggetto visivo, viene eseguito il wrapping in un unico modulo.

Variabili globali come JQuery e Lodash, usate negli strumenti per oggetti visivi di Power BI precedenti, sono ora obsolete. Se il codice precedente per l'oggetto visivo è basato su variabili globali, probabilmente l'oggetto visivo non funzionerà con i nuovi strumenti.

Nella versione precedente degli strumenti per oggetti visivi di Power BI è necessario definire una classe Visual nel modulo `powerbi.extensibility.visual`. Con la nuova versione degli strumenti, è invece necessario definire una classe Visual nel file TypeScript (con estensione ts) principale. In genere, il file è `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Installare powerbi-visuals-tools

Eseguire questo comando per installare i nuovi strumenti:

```cmd
npm install -g powerbi-visuals-tools
```

Il codice seguente proviene dal file `package.json` nel [repository dell'oggetto visivo sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), dopo l'aggiornamento del progetto dell'oggetto visivo per supportare i nuovi strumenti:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Installare l'API degli oggetti visivi personalizzati di Power BI

La nuova versione di powerbi-visual-tools non include tutte le versioni API. È invece necessario installare una versione specifica del pacchetto [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api). Scegliere la versione del pacchetto che corrisponde alla versione API degli oggetti visivi personalizzati di Power BI. Il pacchetto fornisce tutte le definizioni di tipo per l'API degli oggetti visivi personalizzati di Power BI.

Aggiungere `powerbi-visuals-api` alle dipendenze del progetto eseguendo questo comando:

```cmd
npm install --save-dev powerbi-visuals-api
```

Rimuovere inoltre tutti i collegamenti alle precedenti definizioni di tipo dell'API, in quanto webpack include automaticamente i tipi da `powerbi-visuals-api`. Le modifiche corrispondenti si trovano in [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) e [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Aggiornare tsconfig.json

Per usare moduli esterni, modificare l'opzione `out` in `outDir`. Usare, ad esempio, `"outDir": "./.tmp/build/",` invece di `"out": "./.tmp/build/visual.js",`.

Questa modifica è necessaria perché i file TypeScript verranno compilati in file JavaScript in modo indipendente. Ecco perché non è più necessario specificare il file visual.js come output.

È anche possibile modificare l'opzione `target` in `ES6` se si vuole usare codice JavaScript moderno come output. Questa modifica è [facoltativa](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Aggiornare le utilità degli oggetti visivi personalizzati

Se si usa uno dei pacchetti [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), aggiornare anche questi alla versione più recente. A questo scopo, eseguire il comando seguente:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Ad esempio, per ottenere la nuova versione con moduli esterni di TypeScript, eseguire: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Per un esempio di un oggetto visivo che usa tutti i pacchetti `powerbi-visuals-utils`, vedere il [repository di MekkoChart](https://github.com/Microsoft/powerbi-visuals-mekkochart).

## <a name="remove-the-globalizejs-library"></a>Rimuovere la libreria Globalize.js

La nuova versione di [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) include già Globalize.js. Di conseguenza, non è necessario includere manualmente questa libreria nel progetto. Tutte le localizzazioni necessarie verranno aggiunte automaticamente al pacchetto finale.

## <a name="configure-loading-of-external-libraries"></a>Configurare il caricamento di librerie esterne

Includere nuovi file JavaScript dopo le librerie nella matrice `externalJS` di `pbiviz.json`. ad esempio:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importare le librerie nel codice sorgente. Per `lodash-es`, ad esempio, usare questa istruzione:

```JS
import * as _ from "lodash-es";
```

Nell'esempio precedente `_` è la variabile globale per la libreria `lodash`.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Apportare modifiche nelle origini degli oggetti visivi

La modifica principale che è necessario apportare è la conversione di moduli interni in moduli esterni. Non è possibile usare moduli esterni all'interno di moduli interni.

Ecco una descrizione dettagliata delle modifiche da apportare. Le modifiche vengono descritte nel contesto del codice di esempio dell'oggetto visivo personalizzato Grafico a barre:

1. Rimuovere tutte le definizioni di modulo da ogni file del [codice sorgente](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importare le definizioni dell'API degli oggetti visivi personalizzati di Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importare le interfacce o le classi necessarie](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) dal modulo interno `powerbi`.

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

4. [Importare la libreria D3.js](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    In alternativa, importare i moduli della libreria D3 necessari:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importare le utilità, le classi e le interfacce definite nel progetto dell'oggetto visivo](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) nel file di origine principale:

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

La nuova versione degli strumenti permette di importare gli stili `CSS` e `Less` direttamente nel codice TypeScript. La [sezione degli stili](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) usata in precedenza viene ora ignorata dal compilatore.

Per usare il foglio di stile, aprire il file TypeScript (con estensione ts) principale e aggiungere questa riga:  

```typescript
import "./../style/visual.less";
```  

Gli stili `CSS` e `Less` verranno compilati automaticamente.

### <a name="externaljs-section-in-pbivizjson"></a>Sezione externalJS in pbiviz.json

Gli strumenti [non richiedono un elenco di librerie `externalJS`](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) da caricare nel bundle dell'oggetto visivo, in quanto webpack include tutte le librerie importate.

> [!NOTE]
> In `pbiviz.json` lasciare vuota la sezione `externalJS`.

Usare il tipico comando `npm run package` per creare il pacchetto dell'oggetto visivo oppure `npm run start` per avviare il server di sviluppo.

## <a name="update-the-d3js-library-to-version-5"></a>Aggiornare la libreria D3.js alla versione 5

Con i nuovi strumenti per oggetti visivi, è possibile iniziare a usare la nuova versione della libreria D3.js. Eseguire questi comandi per aggiornare la libreria D3 nel progetto dell'oggetto visivo:

- `npm install --save d3@5` per installare la nuova D3.js.

- `npm install --save-dev @types/d3@5` per installare le nuove definizioni dei tipi per D3.js.

> [!IMPORTANT]
> La versione 5 della libreria D3 introduce diverse modifiche di rilievo.

Modificare il codice perché funzioni con la nuova libreria D3.js:

- L'interfaccia `d3.Selection<T>` [è stata modificata](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) in `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Non è possibile applicare diversi attributi tramite un'unica chiamata al metodo `attr`. È invece necessario [passare ogni attributo in una chiamata separata](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) a `attr`. Effettuare anche [chiamate separate al metodo `style`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- Con la libreria D3.js versione 4 è stato introdotto il nuovo metodo `merge`. Questo metodo viene comunemente usato per unire le selezioni di `enter` e `update` dopo l'operazione di join dei dati. Per usare correttamente la libreria D3, [chiamare il metodo `merge`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Altre informazioni](https://github.com/d3/d3/blob/master/CHANGES.md) sulle modifiche nella libreria D3.js.

## <a name="install-babel-and-core-js"></a>Installare Babel e core-js

A partire dalla versione 3.1, gli strumenti per oggetti visivi usano Babel per compilare codice JS moderno nei moduli ECMAScript 5 (ES5) precedenti, in modo da supportare un'ampia gamma di browser.

Questa opzione è abilitata per impostazione predefinita, ma è necessario importare manualmente il pacchetto [`core-js`](https://www.npmjs.com/package/core-js). Eseguire questo comando per installare il pacchetto:

```cmd
npm install --save core-js
```

Importare quindi il pacchetto nel punto iniziale del codice dell'oggetto visivo. In genere, si tratta del file "src/visual.ts".

```JS
import "core-js/stable";
```

Per altre informazioni su Babel, vedere la [documentazione](https://babeljs.io/docs/en/).
