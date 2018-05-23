---
title: Usare il raggruppamento e la creazione di contenitori in Power BI Desktop
description: Informazioni su come raggruppare gli elementi e creare contenitori in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 17d6b2cf2e70843cd2abf3ceb7b6cef76f6acb47
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Usare il raggruppamento e la creazione di contenitori in Power BI Desktop
Quando **Power BI Desktop** crea oggetti visivi, aggrega i dati in blocchi (o gruppi) in base ai valori rilevati nei dati sottostanti. Tuttavia, a volte si potrebbe voler perfezionare la modalità di presentazione di tali blocchi. Ad esempio, si potrebbero voler inserire tre categorie di prodotti in una categoria maggiore (un *gruppo*). In alternativa, si potrebbero voler visualizzare le cifre delle vendite in dimensioni del contenitore di 1.000.000 euro, anziché 923.983 euro divisi uniformemente.

In Power BI Desktop è possibile **raggruppare** punti dati che consentono di visualizzare, analizzare ed esplorare più chiaramente dati e tendenze negli oggetti visivi. È anche possibile definire le **dimensioni del contenitore** in modo da inserire i valori in gruppi di uguali dimensioni che consentono una migliore visualizzazione dei dati *.*

### <a name="using-grouping"></a>Uso del raggruppamento
Per usare il raggruppamento, selezionare due o più elementi in un oggetto visivo tenendo premuto CTRL mentre si fa clic per selezionare più elementi. Fare quindi clic con il pulsante destro del mouse su uno degli elementi della selezione multipla e selezionare **Gruppo** dal menu visualizzato.

![](media/desktop-grouping-and-binning/grouping-binning_1.png)

Una volta creato, il gruppo viene aggiunto al bucket **Legenda** per l'oggetto visivo e viene visualizzato anche nell'elenco **Campi**.

![](media/desktop-grouping-and-binning/grouping-binning_2.png)

Dopo aver creato un gruppo, è possibile modificare facilmente i relativi membri facendo clic con il pulsante destro del mouse sul campo dal bucket **Legenda** o dall'elenco **Campi** e selezionando **Modifica gruppi**.

![](media/desktop-grouping-and-binning/grouping-binning_3.png)

Nella finestra **Gruppi** visualizzata è possibile creare nuovi gruppi o modificare i gruppi esistenti. È anche possibile *rinominare* qualsiasi gruppo facendo doppio clic sul titolo del gruppo nella casella **Gruppi e membri** e digitando un nuovo nome.

Con i gruppi è possibile eseguire diverse operazioni. È possibile aggiungere elementi dall'elenco **Valori non raggruppati** in un nuovo gruppo o in uno dei gruppi esistenti. Per creare un nuovo gruppo, selezionare due o più elementi (premendo CTRL mentre si fa clic) dalla casella **Valori non raggruppati** e quindi fare clic sul pulsante **Gruppo** sotto tale casella.

È possibile aggiungere un valore non raggruppato in un gruppo esistente: è sufficiente selezionare il valore non raggruppato, quindi selezionare il gruppo esistente a cui si vuole aggiungerlo e fare clic sul pulsante **Gruppo**. Per rimuovere un elemento da un gruppo, selezionarlo dalla casella **Gruppi e membri** e quindi fare clic su **Separa**. È anche possibile selezionare se le categorie separate devono essere inserite nel gruppo **Altro** o se devono rimanere non raggruppate.

![](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> È possibile creare gruppi per qualsiasi campo nell'area **Campi** senza la necessità di eseguire la selezione multipla da un oggetto visivo esistente. Fare clic con il pulsante destro del mouse sul campo e selezionare **Nuovo gruppo** dal menu visualizzato.
> 
> 

### <a name="using-binning"></a>Uso della creazione di contenitori
È possibile impostare le dimensioni del contenitore per i campi numerici e ora in **Power BI Desktop**. È possibile usare la creazione di contenitori per assegnare le dimensioni appropriate ai dati visualizzati da **Power BI Desktop**.

Per applicare una dimensione al contenitore, fare clic con il pulsante destro del mouse su un **campo** e selezionare **Nuovo gruppo**.

![](media/desktop-grouping-and-binning/grouping-binning_5.png)

Nella finestra **Gruppi** impostare le **Dimensioni contenitore** sulle dimensioni desiderate.

![](media/desktop-grouping-and-binning/grouping-binning_6.png)

Quando si seleziona **OK**, verrà visualizzato un nuovo campo nel riquadro **Campi** con *(contenitori)* accodato. È quindi possibile trascinare il campo nell'area di disegno per usare la dimensione del contenitore in un oggetto visivo.

![](media/desktop-grouping-and-binning/grouping-binning_7.png)

Per vedere in azione la **creazione di contenitori**, dare uno sguardo a questo [video](https://www.youtube.com/watch?v=BRvdZSfO0DY).

E questo è tutto per quanto riguarda l'uso del **raggruppamento** e della **creazione di contenitori** per assicurarsi che gli oggetti visivi nei report mostrino i dati nel modo desiderato.

