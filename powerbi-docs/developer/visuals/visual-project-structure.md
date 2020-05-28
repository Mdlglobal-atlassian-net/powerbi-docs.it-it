---
title: Struttura del progetto per un oggetto visivo di Power BI
description: Questo articolo descrive la struttura dei file e delle cartelle del progetto per un oggetto visivo di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: ce0f22c17ed718d3e2ad4e4fa9d9514edd315583
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407421"
---
# <a name="power-bi-visual-project-structure"></a>Struttura del progetto per un oggetto visivo di Power BI

Il modo migliore per iniziare a creare un nuovo oggetto visivo di Power BI è tramite lo strumento per oggetti visivi di Power BI, [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools).

Per creare un nuovo oggetto visivo di Power BI, passare alla directory in cui si vuole crearlo ed eseguire il comando seguente:

`pbiviz new <visual project name>`

Questo comando crea una cartella di Power BI contenente i file seguenti:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Descrizione dei file e delle cartelle

Questa sezione offre informazioni per ogni cartella e ogni file all'interno della directory creata dallo strumento **pbiviz** per oggetti visivi di Power BI.  

### <a name="vscode"></a>.vscode

Questa cartella contiene le impostazioni per il progetto VS Code.

Per configurare l'area di lavoro, modificare il file `.vscode/settings.json`.

Per altre informazioni, vedere [Impostazioni per l'utente e l'area di lavoro](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>asset

Questa cartella contiene il file `icon.png`.

Lo strumento per oggetti visivi di Power BI usa questo file come nuova icona visiva di Power BI nel riquadro di visualizzazione di Power BI.

### <a name="src"></a>src

Questa cartella contiene il codice sorgente dell'oggetto visivo.

In questa cartella lo strumento per oggetti visivi di Power BI crea i file seguenti:
* `visual.ts`: codice sorgente principale dell'oggetto visivo.
* `settings.ts`: codice delle impostazioni dell'oggetto visivo. Le classi nel file rappresentano un'interfaccia per la definizione di [proprietà dell'oggetto visivo](./objects-properties.md#properties) personalizzate.

### <a name="style"></a>style

Questa cartella contiene il file `visual.less`, al cui interno si trovano gli stili dell'oggetto visivo.

### <a name="capabilitiesjson"></a>capabilities.json

Questo file contiene le proprietà e le impostazioni principali (o [funzionalità](./capabilities.md)) dell'oggetto visivo. Consente all'oggetto visivo di dichiarare le funzionalità, gli oggetti, le proprietà e il [mapping della vista dati](./dataview-mappings.md) supportati.

### <a name="package-lockjson"></a>package-lock.json

Questo file viene generato automaticamente per tutte le operazioni in cui *npm* modifica l'albero `node_modules` o il file `package.json`.

Per altre informazioni su questo file, vedere la documentazione di [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) ufficiale.

### <a name="packagejson"></a>package.json

Questo file descrive il pacchetto del progetto. Contiene informazioni sul progetto, ad esempio autori, descrizione e dipendenze del progetto.

Per altre informazioni su questo file, vedere la documentazione di [npm-package.json](https://docs.npmjs.com/files/package.json.html) ufficiale.

### <a name="pbivizjson"></a>pbiviz.json

Questo file contiene i metadati dell'oggetto visivo.

Per visualizzare un file `pbiviz.json` di esempio con commenti che descrivono le voci dei metadati, vedere la sezione sulle [voci dei metadati](#metadata-entries).

### <a name="tsconfigjson"></a>tsconfig.json

File di configurazione di [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

Questo file deve contenere il percorso del file **\*.ts** in cui si trova la classe principale dell'oggetto visivo, come specificato nella proprietà `visualClassName` nel file `pbiviz.json`.

### <a name="tslintjson"></a>tslint.json

Questo file contiene la [ configurazione di TSLint](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Voci di metadati

I commenti nelle didascalie del codice seguente del file `pbiviz.json` descrivono le voci dei metadati.

> [!NOTE]
> * Dalla versione 3.x.x dello strumento **pbiviz**, `externalJS` non è supportato.
> * Per il supporto della localizzazione, [aggiungere le impostazioni locali di Power BI all'oggetto visivo](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Passaggi successivi

* Per comprendere le interazioni tra un oggetto visivo, un utente e Power BI, vedere [Concetto di oggetto visivo in Power BI](./power-bi-visuals-concept.md).

* Seguire la [guida dettagliata](./custom-visual-develop-tutorial.md) per iniziare a sviluppare oggetti visivi di Power BI personalizzati da zero.
