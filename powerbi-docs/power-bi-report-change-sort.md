---
title: Modificare l'ordinamento di un grafico in un report di Power BI
description: Modificare l'ordinamento di un grafico in un report di Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6b70a9ef7774d1ba49bc5bf825a5c1cde47197f2
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modificare l'ordinamento di un grafico in un report di Power BI
In un report di Power BI è possibile ordinare alfabeticamente la maggior parte delle visualizzazioni in base ai nomi delle categorie contenute nel grafico oppure in base ai valori numerici di ciascuna categoria. Ad esempio, questo grafico viene ordinato in base al nome dell'archivio.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

È possibile modificare con facilità l'ordinamento da una categoria (nome di un negozio) a un valore (vendite per piede quadrato).

1. Selezionare i puntini di sospensione (...) e scegliere **Sort by Sales Per Sq Ft**.
2. Se necessario, selezionare l'icona di ordinamento ![](media/power-bi-report-change-sort/sorticon.png) per impostare l'**ordinamento decrescente**.

   ![](media/power-bi-report-change-sort/sortby.gif)

   **NOTA**: non è possibile ordinare tutti gli oggetti visivi.  Non è ad esempio possibile ordinare gli oggetti visivi seguenti: mappa ad albero, mappa, mappa colorata, grafico a dispersione, misuratore, scheda, scheda con più righe, grafico a cascata.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordinamento in base ad altri criteri
In alcuni casi, è necessario ordinare l'oggetto visivo usando un campo diverso o altri criteri.  Ad esempio, è possibile ordinare per mese (anziché alfabeticamente) oppure ordinare per numeri interi anziché per cifra (esempio 0, 1, 9, 20 e non 0, 1, 20, 9).  

In alcuni casi, è possibile ordinare l'oggetto visivo nel modo desiderato, ad esempio, in base al mese.  In caso contrario, potrebbe essere necessario apportare alcune modifiche al set di dati del report. Ecco varie soluzioni:

* In Power BI Desktop [usare la scheda Creazione di modelli di Strumenti dati per ordinare in base a una colonna diversa](desktop-sort-by-column.md).
* In Excel, se si è proprietari del set di dati, aggiungere una nuova colonna che concatena il nome del mese e il numero. Quindi aggiornare o importare nuovamente il set di dati per visualizzare la nuova colonna nell'area Campi.
* In Excel assicurarsi che le colonne numeriche siano contrassegnate come "numero intero" o "decimale" e non come "testo".

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle [visualizzazioni nei report di Power BI](power-bi-report-visualizations.md).

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
