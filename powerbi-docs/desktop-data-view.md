---
title: Visualizzazione dati in Power BI Desktop
description: Visualizzazione dati in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 87a72ba5ac69334c04e65871c81a9006e183d88d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876361"
---
# <a name="data-view-in-power-bi-desktop"></a>Visualizzazione dati in Power BI Desktop
La **Vista dati** consente di esaminare, esplorare e interpretare i dati nel modello di **Power BI Desktop**. È diversa dalla visualizzazione di tabelle, colonne e dati nell'**Editor di query**. Con la Vista dati i dati vengono visualizzati *dopo* essere stati caricati nel modello.

Durante la modellazione dei dati talvolta si vuole vedere il contenuto effettivo di una tabella o una colonna senza creare un elemento visivo nell'area di disegno del report, spesso proprio al livello di riga. Questo risulta particolarmente utile per la creazione di misure e colonne calcolate o quando è necessario identificare un tipo di dati o una categoria di dati.

Di seguito si esaminano in dettaglio alcuni elementi della **Vista dati**.

![Visualizzazione dati in Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Icona Vista dati**: selezionare questa icona per accedere alla vista dati.

2. **Griglia dei dati**: visualizza la tabella selezionata e tutte le colonne e le righe in essa contenute. Le colonne nascoste nella **Visualizzazione report** sono visualizzate in grigio. È possibile fare clic con il pulsante destro del mouse su una colonna per visualizzare le opzioni.

3. **Barra multifunzione Creazione di modelli**: consente di gestire relazioni, creare calcoli e modificare il tipo di dati, il formato e la categoria di dati per una colonna.

4. **Barra della formula**: immettere le formule DAX per le misure e le colonne calcolate.

5. **Cerca**: consente di cercare una tabella o una colonna nel modello.

6. **Elenco dei campi**: selezionare una tabella o una colonna da visualizzare nella griglia dei dati.

## <a name="filtering-in-data-view"></a>Applicazione di filtri nella vista dati

Nella **Vista dati** è anche possibile filtrare e ordinare i dati. Ogni colonna visualizza un'icona che identifica la direzione di ordinamento (se applicata).

![Ordinamento e filtro nella Vista dati in Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

È possibile filtrare singoli valori o usare un filtro avanzato in base ai dati presenti nella colonna. 

> [!NOTE]
> Quando un modello di Power BI viene creato in impostazioni cultura diverse dall'interfaccia utente corrente (ad esempio, il modello è stato creato in Inglese (Stati Uniti) e viene visualizzato in Spagnolo), La casella di ricerca viene visualizzata nell'interfaccia utente Vista dati solo per i campi di testo.
