---
title: Segnalibri
description: Gli oggetti visivi di Power BI possono gestire il passaggio tra segnalibri
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425506"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Aggiungere il supporto per i segnalibri per oggetti visivi di Power BI

I segnalibri dei report di Power BI permettono l'acquisizione della visualizzazione configurata di una pagina del report, uno stato di selezione e uno stato di filtro dell'oggetto visivo. Tuttavia, è necessaria un'azione aggiuntiva dal lato degli oggetti visivi personalizzati per supportare i segnalibri e rispondere correttamente alle modifiche.

Altre informazioni sui segnalibri sono disponibili nella [documentazione](https://docs.microsoft.com/power-bi/desktop-bookmarks)

## <a name="report-bookmarks-support-in-your-visual"></a>Supporto per segnalibri del report nell'oggetto visivo

Se l'oggetto visivo interagisce con altri oggetti visivi, seleziona punti dati o filtra altri oggetti visivi, è necessario ripristinare lo stato dalle proprietà.

## <a name="how-to-add-report-bookmarks-support"></a>Come aggiungere il supporto per i segnalibri del report

1. Installare (o aggiornare) l'utilità necessaria: `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) versione 3.0.0 o successiva. Contiene classi aggiuntive da modificare con lo stato selezione o filtro. È necessaria per gli oggetti visivi di filtro e per qualsiasi oggetto visivo che usa `InteractivityService`.

2. Aggiornare l'API dell'oggetto visivo alla versione 1.11.0 per l'uso di `registerOnSelectCallback` nell'istanza di `SelectionManager`. È necessaria per gli oggetti visivi non di filtro che usano `SelectionManager` semplice anziché `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Interazione degli oggetti visivi personalizzati con Power BI nello scenario dei segnalibri del report

Si consideri l'esempio seguente: Un utente crea diversi segnalibri nella pagina del report, con uno stato di selezione diverso in ogni segnalibro.

In primo luogo, l'utente seleziona un punto dati nell'oggetto visivo. L'oggetto visivo interagisce con Power BI e altri oggetti visivi passando le selezioni all'host. L'utente seleziona quindi "Aggiungi" in `Bookmark panel` e Power BI salva le selezioni correnti per il nuovo segnalibro.

Questo si verifica ripetutamente quando l'utente modifica la selezione e aggiunge nuovi segnalibri.
Una volta creato il segnalibro, l'utente può passare tra un segnalibro e l'altro.

Quando gli utenti selezionano un segnalibro, Power BI ripristina lo stato di selezione o di filtro salvato e passa agli oggetti visivi. Gli altri oggetti visivi verranno evidenziati o filtrati in base allo stato archiviato nel segnalibro. L'host Power BI è responsabile delle azioni. L'oggetto visivo è responsabile di far riflettere correttamente il nuovo stato di selezione, ad esempio la modifica del colore dei punti dati di cui è stato eseguito il rendering.

Il nuovo stato di selezione viene comunicato all'oggetto visivo tramite il metodo `update`. L'argomento `options` conterrà una proprietà speciale: `options.jsonFilters`. Si tratta di JSONFilter e la proprietà può contenere `Advanced Filter` e `Tuple Filter`.

L'oggetto visivo deve ripristinare i valori di filtro per visualizzare lo stato corrispondente dell'oggetto visivo per il segnalibro selezionato.

In alternativa, usare la chiamata della funzione di callback speciale registrata nel metodo `registerOnSelectCallback` di ISelectionManager, se l'oggetto visivo usa solo selezioni.

### <a name="visuals-with-selections"></a>Oggetti visivi con selezioni

Se gli oggetti visivi interagiscono con altri oggetti visivi tramite [selezioni](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), è possibile aggiungere segnalibri in due modi diversi.

* È possibile usare il metodo `FilterManager.restoreSelectionIds` se **non è stato usato [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** in precedenza nell'oggetto visivo.

* Se l'oggetto visivo usa già **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** per gestire le selezioni, è necessario usare il metodo `applySelectionFromFilter` nell'istanza di `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Uso di `ISelectionManager.registerOnSelectCallback`

Quando un utente fa clic sui segnalibri, Power BI chiama il metodo `callback` dell'oggetto visivo con le selezioni corrispondenti. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Si supponga che nell'oggetto visivo sia presente un punto dati creato nel metodo [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

`datapoints` ha un aspetto simile al seguente:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Di conseguenza, sono presenti `visualDataPoints` come punti dati e la matrice `ids` passata alla funzione `callback`.

A questo punto, l'oggetto visivo deve confrontare la matrice di `ISelectionId[]` con le selezioni nella matrice `visualDataPoints` e contrassegnare i punti dati corrispondenti come selezionati.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Una volta aggiornati, i punti dati riflettono lo stato di selezione corrente archiviato nell'oggetto `filter`. Quando viene eseguito il rendering dei punti dati, lo stato di selezione dell'oggetto visivo personalizzato corrisponderà allo stato del segnalibro.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Uso di `InteractivityService` per le selezioni dei controlli nell'oggetto visivo

Se l'oggetto visivo usa `InteractivityService`, non è necessario eseguire altre azioni per supportare i segnalibri al suo interno.

L'utilità gestirà lo stato di selezione dell'oggetto visivo quando l'utente seleziona i segnalibri.

### <a name="visuals-with-filter"></a>Oggetti visivi con filtro

Si supponga che l'oggetto visivo crei un filtro di dati in base all'intervallo di date. `startDate` e `endDate` corrispondono all'inizio e alla fine dell'intervallo.
L'oggetto visivo crea un filtro avanzato e chiama il metodo host `applyJsonFilter` per filtrare i dati in base alle condizioni pertinenti.
`target` è la tabella per il filtro.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Ogni volta che un utente fa clic su un segnalibro, l'oggetto visivo riceve una chiamata `update`.

L'oggetto visivo personalizzato deve controllare il filtro nell'oggetto:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Se l'oggetto `filter` non è null, l'oggetto visivo deve ripristinare le condizioni di filtro dall'oggetto:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

L'oggetto visivo deve quindi modificare il proprio stato interno, ovvero i punti dati e gli oggetti di visualizzazione (linee, rettangoli e così via), in modo da riflettere le condizioni correnti.

> [!IMPORTANT]
> Nello scenario dei segnalibri del report, l'oggetto visivo non deve chiamare `applyJsonFilter` per filtrare altri oggetti visivi, che verranno già filtrati da Power BI.

L'oggetto visivo del filtro dati della sequenza temporale modifica il selettore di intervallo in modo che corrisponda agli intervalli di dati.

Per altre informazioni, vedere il [repository di Timeline Slicer](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Filtrare lo stato per salvare le proprietà dell'oggetto visivo nei segnalibri

La proprietà `filterState` crea una proprietà di una parte del filtro. L'oggetto visivo può archiviare valori diversi nei segnalibri.

Per salvare il valore della proprietà come stato di filtro, la proprietà dell'oggetto deve essere contrassegnata come `"filterState": true` in `capabilities.json`.

Esempio: `Timeline Slicer` archivia i valori della proprietà `Granularity` nel filtro. Permette quindi di modificare la granularità corrente alla modifica dei segnalibri da parte dell'utente.

Per altre informazioni, vedere il [repository di Timeline Slicer](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
