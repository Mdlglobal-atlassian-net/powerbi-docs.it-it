---
title: Supporto per la modalità a contrasto elevato
description: Aggiungere il supporto per la modalità a contrasto elevato agli oggetti visivi di Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cb77ea012fdfdbd5be62c58c6f9b94a0355db1a9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424931"
---
# <a name="high-contrast-mode-support"></a>Supporto per la modalità a contrasto elevato

L'impostazione *Contrasto elevato* di Windows migliora la visualizzazione di testo e app usando colori più nitidi.
Per altre informazioni, vedere [Supporto per il contrasto elevato in Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

Per aggiungere il supporto per il contrasto elevato a un oggetto visivo, è necessario:

1. All'inizializzazione: Determinare se Power BI è in modalità a contrasto elevato e, se sì, ottenere i colori a contrasto elevato correnti.
2. A ogni aggiornamento: Modificare il modo in cui viene eseguito il rendering dell'oggetto visivo per semplificarne la visualizzazione.

L'oggetto visivo PowerBI-visuals-sampleBarChart include l'implementazione del supporto per il contrasto elevato.

Per altre informazioni, vedere il [repository dell'oggetto visivo PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6)

## <a name="on-init"></a>All'inizializzazione

Il membro colorPalette di `options.host` include diverse proprietà per la modalità a contrasto elevato. Usare queste proprietà per determinare se la modalità a contrasto elevato è attiva e, se sì, quali colori usare.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Determinare che Power BI è in modalità a contrasto elevato

Se `host.colorPalette.isHighContrast` è `true`, la modalità a contrasto elevato è attiva e l'oggetto visivo apparirà di conseguenza.

### <a name="get-high-contrast-colors"></a>Ottenere i colori a contrasto elevato

In modalità a contrasto elevato l'oggetto visivo deve limitarsi ai colori seguenti:

* Il colore di **primo piano** viene usato per disegnare qualsiasi linea, icona, testo, contorno o riempimento delle forme.
* Il colore di **sfondo** viene usato per lo sfondo e come colore di riempimento delle forme con contorno.
* Il colore di **primo piano di una selezione** viene usato per indicare un elemento selezionato o attivo.
* Il colore dei **collegamenti ipertestuali** viene usato solo per il testo dei collegamenti ipertestuali.

> [!NOTE]
> Se è necessario un colore secondario, è possibile usare il colore di primo piano con una certa opacità. Gli oggetti visivi nativi di Power BI usano un'opacità del 40%. Usare questa opzione con cautela per mantenere facilmente visualizzabili i dettagli degli oggetti visivi.

È possibile archiviare questi valori durante l'inizializzazione:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

In alternativa, è possibile archiviare l'oggetto `host` durante l'inizializzazione e accedere alle proprietà `colorPalette` pertinenti durante l'aggiornamento.

## <a name="on-update"></a>All'aggiornamento

Le implementazioni specifiche del supporto per il contrasto elevato variano a seconda dell'oggetto visivo e dipendono dai dettagli della progettazione grafica. In genere, la modalità a contrasto elevato richiede una progettazione leggermente diversa da quella predefinita, per rendere i dettagli importanti più facilmente distinguibili con i colori limitati.

Ecco alcune linee guida seguite dagli oggetti visivi nativi di Power BI:

* Tutti i punti dati usano lo stesso colore (di primo piano).
* Tutto il testo e tutti gli assi, le frecce, le linee così via usano il colore di primo piano.
* Le forme spesse vengono disegnate come contorni, con tratti spessi (almeno due pixel) e riempimento del colore di sfondo.
* Quando necessario, i punti dati si distinguono tramite forme del marcatore diverse, mentre le righe di dati si distinguono per il tratteggio diverso.
* Quando un elemento dati è evidenziato, tutti gli altri elementi passano a un'opacità del 40%.
* Per i filtri dei dati, gli elementi del filtro attivo usano il colore selezionato in primo piano.

Nel grafico a barre di esempio tutte le barre vengono disegnate con un contorno nel colore di primo piano di due pixel e un riempimento di sfondo. Confrontare il modo in cui appare con i colori predefiniti e con un paio di temi a contrasto elevato:

![Grafico a barre di esempio che usa colori standard](./media/hc-samplebarchart-standard.png)
![Grafico a barre di esempio che usa la combinazione di colori *Scuro n. 2*](./media/hc-samplebarchart-dark2.png)
![Grafico a barre di esempio che usa la combinazione di colori *Bianco*](./media/hc-samplebarchart-white.png)

Ecco un punto nella funzione `visualTransform` che è stato modificato per supportare il contrasto elevato. Viene chiamato come parte del rendering durante `update`:

### <a name="before"></a>Prima

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Dopo

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
