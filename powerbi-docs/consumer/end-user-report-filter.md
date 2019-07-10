---
title: Presentazione del riquadro Filtri del report
description: Come aggiungere un filtro a un report nel servizio Power BI per i consumer
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532944"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Presentazione del riquadro Filtri del report

Questo articolo illustra il riquadro **Filtri** del report nel servizio Power BI. Usare i filtri per individuare nuove informazioni dettagliate nei dati.

In Power BI è possibile filtrare i dati in molti modi diversi. Per altre informazioni sui filtri, vedere [Filtri ed evidenziazione nei report di Power BI](../power-bi-reports-filters-and-highlighting.md).

![Screenshot di un report nel browser con una freccia rivolta verso l'opzione Filtri.](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Uso del riquadro Filtri del report

Quando un collega condivide un report, cercare il riquadro **Filtri**. In alcuni casi è compresso lungo il bordo destro del report. Selezionarlo per espanderlo.

![Screenshot del report con il riquadro Filtri espanso.](media/end-user-report-filter/power-bi-filter-pane.png)

Il riquadro **Filtri** contiene i filtri aggiunti al report dal *designer* del report. I *consumer* possono interagire con i filtri esistenti e salvare le modifiche, ma non possono aggiungere nuovi filtri al report. Ad esempio, nello screenshot precedente il designer ha aggiunto due filtri di livello pagina: **Segment** (Segmento) e **Year** (Anno). È possibile interagire con questi filtri e modificarli, ma non è possibile aggiungere un terzo filtro a livello di pagina.

Nel servizio Power BI i report mantengono le modifiche apportate nel riquadro **Filtri**. Il servizio riporta le modifiche nella versione per dispositivi mobili del report.

Per reimpostare il riquadro **Filtri** alle impostazione predefinite del designer, selezionare ![screenshot dell'opzione Ripristina impostazioni predefinite.](media/end-user-report-filter/power-bi-reset.png) nella barra dei menu superiore.

## <a name="view-all-the-filters-for-a-report-page"></a>Visualizzare tutti i filtri per una pagina del report

Il riquadro **Filtri** visualizza tutti i filtri aggiunti al report dal designer. Il riquadro **Filtri** è anche l'area in cui è possibile visualizzare le informazioni relative ai filtri e interagire con essi. È possibile salvare le modifiche apportate o usare **Ripristina impostazioni predefinite** per ripristinare le impostazioni filtro originali.

Per salvare le proprie modifiche è anche possibile creare un segnalibro personale.  Per altre informazioni, vedere [Cosa sono i segnalibri?](end-user-bookmarks.md)

Il riquadro **Filtri** visualizza e gestisce diversi tipi di filtri del report. Questi possono essere applicati a un oggetto visivo, a una pagina del report e all'intero report.

In questo esempio è stato selezionato un oggetto visivo con due filtri. Anche la pagina del report include filtri, elencati sotto l'intestazione **Filtri in questa pagina**. L'intero report ha inoltre un filtro per **Date** (Data).

![Screenshot di un report con una visualizzazione e i relativi filtri evidenziati.](media/end-user-report-filter/power-bi-all-filters2.png)

Accanto ad alcuni filtri è presente la voce **(All)** (Tutti). **(All)** (Tutti) indica che il filtro include tutti i valori. Nello screenshot precedente **Segment (All)** (Segmento, Tutti) indica che la pagina del report include i dati relativi a tutti i segmenti di prodotto. Se si seleziona il filtro a livello di pagina **Region is West** (Area è Occidentale), la pagina del report includerà solo i dati dell'area geografica occidentale.

Tutti gli utenti che visualizzeranno il report possono interagire con i filtri.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Visualizzare solo i filtri applicati a un oggetto visivo

Per esaminare in modo più dettagliato i filtri applicati a uno specifico oggetto visivo, passare il mouse su di esso per visualizzare l'icona del filtro ![screenshot dell'icona del filtro](media/end-user-report-filter/power-bi-filter-icon.png). Selezionare l'icona del filtro per visualizzare un popup con tutti i filtri, i filtri dei dati e altri elementi che interessano l'oggetto visivo. I filtri visualizzati nel popup corrispondono a quelli visualizzati nel riquadro **Filtri**.

![Screenshot di un elenco di filtri con frecce che puntano agli stessi filtri nel riquadro Filtri.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

Ecco i tipi di filtri disponibili in questa visualizzazione:

- Filtri di base

- Filtri dei dati

- Evidenziazione incrociata

- Filtro incrociato

- Filtri avanzati

- Primi N filtri

- Filtri per data relativa

- Filtri dei dati sincronizzati

- Filtri di inclusione/esclusione

- Filtri passati tramite un URL

Nell'esempio seguente:

1. Si può vedere che all'istogramma è stato applicato un filtro incrociato.

1. **Included** (Inclusi) indica che il filtro incrociato è per **Segment** (Segmento) e che ne sono inclusi tre.

1. È stato applicato un filtro dei dati per **Quarter** (Trimestre).

1. **Region** (Area) è un filtro applicato a questa pagina del report e

1. **isVanArsdel** e **Year** (Anno) sono filtri applicati a questo oggetto visivo.

![Screenshot di un report e dei relativi filtri con l'elenco di filtri numerati in modo da coincidere con l'elenco numerato riportato sopra.](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Cercare in un filtro

Talvolta un filtro può avere un lungo elenco di valori. Usare la casella di ricerca per trovare e selezionare un valore.

![Screenshot della modalità di ricerca in un filtro.](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Visualizzare i dettagli del filtro

Per comprendere un filtro, esaminarne i valori e i conteggi disponibili.  Per visualizzare i dettagli del filtro, passare il puntatore del mouse e selezionare la freccia accanto al nome del filtro.
  
![Screenshot di un filtro con l'area occidentale selezionata.](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Modificare le selezioni del filtro

L'interazione con i filtri è un modo per cercare informazioni dettagliate sui dati. È possibile modificare le selezioni del filtro usando la freccia a discesa accanto al nome del campo.  A seconda del filtro e del tipo di dati filtrati da Power BI, le opzioni variano dalle semplici selezioni in un elenco all'identificazione di intervalli di date o numeri. Nel filtro avanzato riportato di seguito l'intervallo del filtro **Total Units YTD** nel grafico ad albero è stato modificato in modo da essere compreso tra 2.000 e 3.000. Si noti che questa modifica rimuove Prirum dal grafico ad albero.
  
![Screenshot di un report e dei relativi filtri con Fashions Direct selezionato.](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Per selezionare contemporaneamente più valori di filtro, tenere premuto CTRL. La maggior parte dei filtri supporta la selezione multipla.

### <a name="reset-filter-to-default"></a>Ripristinare le impostazioni predefinite del filtro

Per annullare tutte le modifiche apportate ai filtri, selezionare **Ripristina impostazioni predefinite** nella barra dei menu superiore.  Questa selezione ripristina lo stato originale dei filtri, come impostati dal designer del report.

![Screenshot dell'opzione Ripristina impostazioni predefinite.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Eliminare un filtro

Se si ha un solo filtro che si vuole impostare su **(All)** (Tutti), cancellarlo selezionando l'icona della gomma ![screenshot dell'icona della gomma.](media/end-user-report-filter/power-bi-eraser-icon.png) accanto al nome del filtro.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come e perché [si applicano il filtro incrociato e l'evidenziazione incrociata agli oggetti visivi in una pagina di report](end-user-interactions.md)