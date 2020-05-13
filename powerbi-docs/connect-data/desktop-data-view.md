---
title: Visualizzazione dati in Power BI Desktop
description: Visualizzazione dati in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9311facac78a21568206843c026c8330960c9d33
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347517"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Usare la vista dati in Power BI Desktop

La *visualizzazione Dati* consente di esaminare, esplorare e interpretare i dati nel modello di *Power BI Desktop*. È diversa dal modo in cui sono visualizzati i dati, le tabelle e le colonne nell'*editor di Power Query*. Nella visualizzazione Dati si possono esaminare i dati *dopo* il caricamento nel modello.

> [!NOTE]
> Poiché la visualizzazione Dati mostra i dati dopo il caricamento nel modello, l'icona Visualizzazione Dati non è visibile se tutte le origini dati sono basate su DirectQuery. 

Durante la modellazione dei dati, talvolta è opportuno verificare il contenuto effettivo di una tabella o una colonna, senza creare un elemento visivo nell'area di disegno del report, fino a raggiungere il livello di riga. Questo livello di visualizzazione risulta particolarmente utile per la creazione di misure e colonne calcolate o quando è necessario identificare un tipo di dati o una categoria di dati.

Di seguito si esamineranno in dettaglio alcuni elementi della visualizzazione Dati.

![Visualizzazione dati in Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Icona della visualizzazione Dati**. Selezionare questa icona per accedere alla visualizzazione Dati.

2. **Griglia dati**. Questa area mostra la tabella selezionata e tutte le colonne e le righe incluse. Le colonne nascoste nella visualizzazione *Report* sono riportate in grigio. È possibile fare clic con il pulsante destro del mouse su una colonna per visualizzare le opzioni.

3. **Barra multifunzione Creazione di modelli**. Consente di gestire relazioni, creare calcoli e modificare il tipo di dati, il formato e la categoria di dati per una colonna.

4. **Barra della formula**. Immettere le formule DAX (Data Analysis Expression) per le misure e le colonne calcolate.

5. **Casella di ricerca**. Consente di cercare una tabella o una colonna nel modello.

6. **Elenco di campi**. Consente di selezionare una tabella o una colonna da visualizzare nella griglia dati.

## <a name="filtering-in-data-view"></a>Applicazione di filtri nella visualizzazione Dati

Nella visualizzazione Dati è anche possibile filtrare e ordinare i dati. In ogni colonna è presente un'icona che identifica la direzione di ordinamento, se applicata.

![Ordinamento e filtro nella Vista dati in Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

È possibile filtrare singoli valori o usare un filtro avanzato in base ai dati presenti nella colonna.

> [!NOTE]
> Quando un modello di Power BI viene creato con impostazioni cultura diverse da quelle dell'interfaccia utente corrente, la casella di ricerca viene visualizzata nell'interfaccia utente della visualizzazione Dati solo per i campi di testo. Questo è il caso, ad esempio, di un modello creato in inglese (Stati Uniti) e visualizzato in spagnolo.


## <a name="next-steps"></a>Passaggi successivi

Power BI Desktop offre infinite possibilità. Per altre informazioni sulle capacità disponibili, vedere le risorse seguenti:

* [Che cos'è Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Panoramica delle query con Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipi di dati in Power BI Desktop](desktop-data-types.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Attività di query comuni in Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
