---
title: Evitare le pagine vuote durante la stampa di report impaginati
description: Linee guida per la progettazione di report impaginati evitando pagine vuote al momento della stampa.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 349459b95a815a52665e50687554f81f90a9c81b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920806"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Evitare le pagine vuote durante la stampa di report impaginati

Questo articolo è rivolto agli autori di report che progettano [report impaginati](../paginated-reports/paginated-reports-report-builder-power-bi.md) di Power BI. Offre raccomandazioni per evitare pagine vuote quando il report viene esportato in un formato con interruzione di pagina, ad esempio PDF o Microsoft Word, oppure quando viene stampato.

## <a name="page-setup"></a>Impostazioni di pagina

Le proprietà relative alle dimensioni della pagina di report determinano l'orientamento, le dimensioni e i margini della pagina. Per accedere a queste proprietà del report:

- Usare la **pagina delle proprietà** del report: fare clic con il pulsante destro del mouse sull'area grigio scuro all'esterno dell'area di disegno del report e quindi selezionare _Proprietà report_.
- Usare il [riquadro **Proprietà**](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): fare clic sull'area grigio scuro all'esterno dell'area di disegno del report per selezionare l'oggetto report. Assicurarsi che il riquadro **Proprietà** sia aperto.

La pagina **Imposta pagina** della **pagina delle proprietà** del report offre un'interfaccia intuitiva per visualizzare e aggiornare le proprietà di impostazione della pagina.

![L'immagine illustra la finestra Proprietà report, evidenziando la pagina Imposta pagina.](media/report-paginated-blank-page/report-page-setup-properties.png)

Verificare che tutte le proprietà relative alle dimensioni della pagina siano configurate correttamente:

|Proprietà|Recommendation|
|---------|---------|
|Unità di misura pagina|Selezionare le unità pertinenti, ovvero pollici o centimetri.|
|Orientamento|Selezionare l'opzione corretta, ovvero verticale oppure orizzontale.|
|Formato carta|Selezionare un formato carta o assegnare valori di larghezza e altezza personalizzati.|
|Margini|Impostare valori appropriati per i margini sinistro, destro, superiore e inferiore.|
|||

## <a name="report-body-width"></a>Larghezza del corpo del report

Le proprietà relative alle dimensioni della pagina determinano lo spazio disponibile per gli oggetti del report. Gli oggetti del report possono essere aree dati, visualizzazioni dati o altri elementi del report.

Una causa comune della visualizzazione di pagine vuote è la larghezza del corpo del report che _supera lo spazio della pagina disponibile_.

È possibile visualizzare e impostare la larghezza del corpo del report solo usando il riquadro **Proprietà**. Prima di tutto, fare clic su un punto qualsiasi in un'area vuota del corpo del report.

![L'immagine illustra il riquadro Proprietà, evidenziando la proprietà relativa alla larghezza del corpo del report.](media/report-paginated-blank-page/report-body-properties-width.png)

Assicurarsi che il valore della larghezza non superi la larghezza disponibile della pagina. Usare la formula seguente:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Non è possibile ridurre la larghezza del corpo del report se sono già presenti oggetti del report nello spazio che si vuole rimuovere. Prima di ridurre la larghezza è necessario riposizionarli o ridimensionarli.
>
> La larghezza del corpo del report può inoltre aumentare automaticamente quando si aggiungono nuovi oggetti oppure si ridimensionano o riposizionano quelli esistenti. Progettazione report allarga sempre il corpo per adattare la posizione e le dimensioni degli oggetti in esso contenuti.

## <a name="report-body-height"></a>Altezza del corpo del report

Un'altra causa comune della visualizzazione di una pagina vuota è la presenza di spazio in eccesso nel corpo del report dopo l'ultimo oggetto.

È consigliabile ridurre sempre l'altezza del corpo per rimuovere eventuali spazi finali.

![L'immagine illustra la progettazione di un report. Lo spazio al di sotto dell'area dati Tablix è evidenziata e contrassegnata come non necessaria.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Opzioni di interruzione pagina

Ogni area dati e visualizzazione dati ha opzioni di interruzione pagina. È possibile accedere a queste opzioni nella relativa pagina delle proprietà o nel riquadro **Proprietà**.

Assicurarsi che la proprietà **Aggiungi un'interruzione di pagina dopo** non sia inutilmente abilitata.

![L'immagine illustra una finestra Proprietà Tablix. La proprietà "Aggiungi un'interruzione di pagina dopo" è abilitata.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Utilizzare lo spazio vuoto del contenitore

Se il problema della pagina vuota persiste, si può anche provare a disabilitare la proprietà **ConsumeContainerWhitespace** del report. È possibile impostarla solo nel riquadro **Proprietà**.

![L'immagine illustra il riquadro Proprietà, evidenziando la proprietà ConsumeContainerWhitespace.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Per impostazione predefinita, è abilitata. Indica se il minimo spazio vuoto nei contenitori, ad esempio il corpo del report o un rettangolo, deve essere utilizzato. Interessa solo lo spazio vuoto a destra e al di sotto del contenuto.

## <a name="printer-paper-size"></a>Formato carta per la stampante

Infine, se il report viene stampato su carta, assicurarsi che sia stata caricata la carta corretta nella stampante. Il formato fisico della carta deve corrispondere al [formato carta del report](#page-setup).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Che cosa sono i report impaginati in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Paginazione dei report impaginati in Power BI](../paginated-reports/paginated-reports-pagination.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com)
