---
title: Visualizzazione dati in Power BI Desktop
description: Visualizzazione dati in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a82465adb5b0c7fe8be0e6e724c5eda1bfcf7ec0
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538660"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Usare la vista dati in Power BI Desktop

La *visualizzazione Dati* consente di esaminare, esplorare e interpretare i dati nel modello di *Power BI Desktop*. È diversa dal modo in cui sono visualizzati i dati, le tabelle e le colonne nell'*editor di Power Query*. Nella visualizzazione Dati si possono esaminare i dati *dopo* il caricamento nel modello.

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
