---
title: Aggiungere il supporto per i segnalibri per oggetti visivi di Power BI
description: Gli oggetti visivi di Power BI possono gestire il passaggio tra segnalibri
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c7fb8fa6fcf8c07f0d8f466892fff8d03a492a79
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237270"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Aggiungere il supporto per i segnalibri per oggetti visivi di Power BI

Con i segnalibri dei report di Power BI, è possibile acquisire una visualizzazione configurata di una pagina del report, lo stato di selezione e lo stato di filtro dell'oggetto visivo. Tuttavia, è necessaria un'azione aggiuntiva dal lato degli oggetti visivi personalizzati per supportare i segnalibri e rispondere correttamente alle modifiche.

Per altre informazioni sui segnalibri, vedere [Usare i segnalibri per condividere informazioni dettagliate e creare storie in Power BI](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Supporto per segnalibri del report nell'oggetto visivo

Se l'oggetto visivo interagisce con altri oggetti visivi, seleziona punti dati o filtra altri oggetti visivi, è necessario ripristinare lo stato dalle proprietà.

## <a name="add-report-bookmarks-support"></a>Aggiungere il supporto per i segnalibri del report

1. Installare (o aggiornare) l'utilità necessaria, [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) versione 3.0.0 o successiva. Contiene classi aggiuntive da modificare con lo stato selezione o filtro. È necessaria per gli oggetti visivi di filtro e per qualsiasi oggetto visivo che usa `InteractivityService`.

2. Aggiornare l'API per oggetti visivi alla versione 1.11.0 per usare `registerOnSelectCallback` in un'istanza di `SelectionManager`. È necessaria per gli oggetti visivi non di filtro che usano `SelectionManager` semplice anziché `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-report-bookmarks"></a>Interazione degli oggetti visivi personalizzati con Power BI nei segnalibri del report

Si consideri lo scenario seguente: si vogliono creare diversi segnalibri nella pagina del report, con uno stato di selezione diverso in ogni segnalibro.

In primo luogo, si seleziona un punto dati nell'oggetto visivo. L'oggetto visivo interagisce con Power BI e altri oggetti visivi passando le selezioni all'host. Si seleziona quindi **Aggiungi** nel riquadro **Segnalibro** e Power BI salva le selezioni correnti per il nuovo segnalibro.

Questo si verifica ripetutamente quando si modifica la selezione e si aggiungono nuovi segnalibri. Dopo aver creato i segnalibri, è possibile spostarsi tra di essi.

Quando si seleziona un segnalibro, Power BI ripristina lo stato di selezione o di filtro salvato e lo passa agli oggetti visivi. Gli altri oggetti visivi vengono evidenziati o filtrati in base allo stato archiviato nel segnalibro. L'host Power BI è responsabile delle azioni. L'oggetto visivo è responsabile di far riflettere correttamente il nuovo stato di selezione, ad esempio per la modifica dei colori dei punti dati di cui è stato eseguito il rendering.

Il nuovo stato di selezione viene comunicato all'oggetto visivo tramite il metodo `update`. L'argomento `options` contiene una proprietà speciale, `options.jsonFilters`. La proprietà JSONFilter può contenere `Advanced Filter` e `Tuple Filter`.

L'oggetto visivo deve ripristinare i valori di filtro per visualizzare lo stato corrispondente dell'oggetto visivo per il segnalibro selezionato. In alternativa, se l'oggetto visivo usa solo selezioni, è possibile usare la chiamata della funzione di callback speciale registrata come metodo `registerOnSelectCallback` di ISelectionManager.

### <a name="visuals-with-selection"></a>Oggetti visivi con selezione

Se l'oggetto visivo interagisce con altri oggetti visivi usando [Selection](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), è possibile aggiungere i segnalibri in uno dei due modi seguenti:

* Se l'oggetto visivo non ha già usato [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md), è possibile usare il metodo `FilterManager.restoreSelectionIds`.

* Se l'oggetto visivo usa già [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) per gestire le selezioni, è consigliabile usare il metodo `applySelectionFromFilter` nell'istanza di `InteractivityService`.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>Usare ISelectionManager.registerOnSelectCallback

Quando si seleziona un segnalibro, Power BI chiama il metodo `callback` dell'oggetto visivo con le selezioni corrispondenti. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Si supponga di avere un punto dati nell'oggetto visivo creato nel metodo [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

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

Sono ora presenti `visualDataPoints` come punti dati e la matrice `ids` passata alla funzione `callback`.

A questo punto, l'oggetto visivo deve confrontare la matrice `ISelectionId[]` con le selezioni nella matrice `visualDataPoints` e contrassegnare i punti dati corrispondenti come selezionati.

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

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>Usare InteractivityService per le selezioni dei controlli nell'oggetto visivo

Se l'oggetto visivo usa `InteractivityService`, non è necessario eseguire altre azioni per supportare i segnalibri al suo interno.

Quando si selezionano i segnalibri, l'utilità gestisce lo stato di selezione dell'oggetto visivo.

### <a name="visuals-with-a-filter"></a>Oggetti visivi con un filtro

Si supponga che l'oggetto visivo crei un filtro di dati in base all'intervallo di date. `startDate` ed `endDate` sono le date di inizio e di fine dell'intervallo.

L'oggetto visivo crea un filtro avanzato e chiama il metodo host `applyJsonFilter` per filtrare i dati in base alle condizioni pertinenti.

La destinazione è la tabella usata per il filtro.

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

Ogni volta che si seleziona un segnalibro, l'oggetto visivo riceve una chiamata `update`.

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

A questo punto, l'oggetto visivo deve modificare lo stato interno per riflettere le condizioni correnti. Lo stato interno include i punti dati e gli oggetti di visualizzazione (linee, rettangoli e così via).

> [!IMPORTANT]
> Nello scenario dei segnalibri del report, l'oggetto visivo non deve chiamare `applyJsonFilter` per filtrare gli altri oggetti visivi, che verranno già filtrati da Power BI.

L'oggetto visivo del filtro dei dati della sequenza temporale imposta il selettore di intervallo sugli intervalli di dati corrispondenti.

Per altre informazioni, vedere il [repository di Timeline Slicer](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Filtrare lo stato per salvare le proprietà dell'oggetto visivo nei segnalibri

La proprietà `filterState` crea una proprietà di una parte del filtro. L'oggetto visivo può archiviare svariati valori nei segnalibri.

Per salvare il valore della proprietà come stato del filtro, contrassegnare la proprietà dell'oggetto come `"filterState": true` nel file *capabilities.json*.

Il filtro dei dati della sequenza temporale, ad esempio, archivia i valori della proprietà `Granularity` in un filtro. Consente la modifica della granularità corrente quando si modificano i segnalibri.

Per altre informazioni, vedere il [repository di Timeline Slicer](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334).
