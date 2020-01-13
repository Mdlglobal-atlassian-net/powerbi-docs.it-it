---
title: Struttura del progetto per un oggetto visivo di Power BI
description: Questo articolo descrive una struttura di progetti con oggetti visivi
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542094"
---
# <a name="power-bi-visual-project-structure"></a>Struttura del progetto per un oggetto visivo di Power BI

Dopo aver eseguito il nuovo `<visual project name>` di pbiviz, lo strumento crea la struttura di base di file e cartelle nella cartella `<visual project name>`.

## <a name="visual-project-structure"></a>Struttura di progetto con oggetti visivi

![Struttura di progetto con oggetti visivi](./media/visual-project-structure.png)

* `.vscode` contiene le impostazioni del progetto per VS Code. Per configurare l'area di lavoro modificare il file `.vscode/settings.json`. Leggere altre informazioni sulle [impostazioni di VS Code nella documentazione](https://code.visualstudio.com/docs/getstarted/settings)

* La cartella `assets` contiene solo il file `icon.png`. Lo strumento usa questo file come icona dell'oggetto visivo nel riquadro Visualizzazione di Power BI.

    ![Riquadro Visualizzazione](./media/visualization-pane-analytics-tab.png)

* La cartella `node_modules` contiene tutti i pacchetti [installati da Gestione pacchetti del nodo](https://docs.npmjs.com/files/folders.html).

* La cartella `src` contiene il codice sorgente dell'oggetto visivo. Per impostazione predefinita, lo strumento crea due file:

  * `visual.ts`: codice sorgente principale dell'oggetto visivo.

  * `settings.ts`: codice delle impostazioni dell'oggetto visivo. Le classi del file semplificano l'[utilizzo delle proprietà dell'oggetto visivo](./objects-properties.md#properties).

* La cartella `style` contiene il file `visual.less` con gli stili dell'oggetto visivo.

* Il file `capabilities.json` contiene le proprietà e le impostazioni principali dell'oggetto visivo. Consente all'oggetto visivo di dichiarare le funzionalità, gli oggetti, le proprietà e il mapping della vista dati supportati.

    Leggere altre informazioni sulle [funzionalità nella documentazione](./capabilities.md).

* `package-lock.json` viene generato automaticamente per tutte le operazioni in cui npm modifica l'albero di `node_modules` o `package.json`.

    Leggere altre informazioni su [`package-lock.json` nella documentazione ufficiale di NPM](https://docs.npmjs.com/files/package-lock.json).

* `package.json` descrive il pacchetto del progetto. In genere contiene informazioni sul progetto e sui relativi autori, oltre alla descrizione e alle dipendenze del progetto.

    Leggere altre informazioni su [`package.json` nella documentazione ufficiale di NPM](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` contiene i metadati dell'oggetto visivo. Specificare i metadati dell'oggetto visivo in questo file.

    Contenuto tipico del file:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    dove

  * `name`: nome interno dell'oggetto visivo.

  * `displayName`: nome dell'oggetto visivo nell'interfaccia utente di Power BI.

  * `guid`: ID univoco dell'oggetto visivo.

  * `visualClassName`: nome della classe principale dell'oggetto visivo. Power BI crea l'istanza di questa classe per iniziare a usare l'oggetto visivo nel report di Power BI.

  * `version`: numero di versione dell'oggetto visivo.

  * `author`: contiene il nome dell'autore e l'indirizzo di posta elettronica di contatto.

  * `icon` in `assets`: percorso del file di icona dell'oggetto visivo.

  * `externalJS` contiene i percorsi delle librerie JS usate nell'oggetto visivo.

    > [!IMPORTANT]
    > La versione più recente dello strumento, ossia 3.x.x o successiva, non usa più `externalJS`.

  * `style` è il percorso dei file di stile.

  * `capabilities` è il percorso del file `capabilities.json`.

  * `dependencies` è il percorso del file `dependencies.json`. `dependencies.json` contiene informazioni sui pacchetti R usati negli oggetti visivi basati su R.

  * `stringResources` è una matrice di percorsi di file con localizzazioni.

  Leggere altre informazioni sulla [localizzazione negli oggetti visivi nella documentazione](./localization.md)

* `tsconfig.json` è il file di configurazione di TypeScript.

    Leggere altre informazioni sulla [configurazione di TypeScript nella documentazione ufficiale](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    Il file `tsconfig.json` nella sezione `files` deve contenere il percorso del file *.ts in cui si trova la classe principale dell'oggetto visivo specificata nella proprietà `visualClassName` del file `pbiviz.json`.

* Il file `tslint.json` contiene la configurazione di TSLint.

    Leggere altre informazioni sulla [configurazione di TSLint nella documentazione ufficiale](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Passaggi successivi

* Leggere altre informazioni sul [concetto di oggetto visivo](./power-bi-visuals-concept.md) per comprendere meglio il modo in cui oggetti visivi, utenti e Power BI interagiscono tra loro.

* Seguire la [guida dettagliata](./custom-visual-develop-tutorial.md) per iniziare a sviluppare oggetti visivi di Power BI da zero.
