---
title: Usare il raggruppamento e la creazione di contenitori in Power BI Desktop
description: Informazioni su come raggruppare gli elementi e creare contenitori in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 525f7bf4c967722d8f98a9184127bc8c7907cea1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309476"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Usare il raggruppamento e la creazione di contenitori in Power BI Desktop
Quando Power BI Desktop crea oggetti visivi, aggrega i dati in blocchi (o gruppi) in base ai valori trovati nei dati sottostanti. Tuttavia, a volte si potrebbe voler perfezionare la modalità di presentazione di tali blocchi. Ad esempio, si potrebbero voler inserire tre categorie di prodotti in una categoria maggiore (un *gruppo*). In alternativa, si potrebbero voler visualizzare le cifre delle vendite in dimensioni del contenitore di 1.000.000 di euro, anziché in blocchi di 923.983 euro.

In Power BI Desktop, è possibile *raggruppare* punti dati che consentono di visualizzare, analizzare ed esplorare più chiaramente dati e tendenze negli oggetti visivi. È anche possibile definire le *dimensioni del contenitore* in modo da inserire i valori in gruppi di uguali dimensioni che consentono una migliore e più significativa visualizzazione dei dati. Questa azione è detta anche *binning*.

## <a name="using-grouping"></a>Uso del raggruppamento
Per usare il raggruppamento, selezionare due o più elementi in un oggetto visivo tenendo premuto CTRL mentre si fa clic per selezionare più elementi. Fare quindi clic con il pulsante destro del mouse su uno degli elementi della selezione multipla e scegliere **Raggruppa** dal menu di scelta rapida.

![Comando Raggruppa, grafico, raggruppamento, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_1.png)

Una volta creato, il gruppo viene aggiunto al contenitore **Legenda** per l'oggetto visivo e viene visualizzato anche nell'elenco **Campi**.

![Campi Legenda e Campi, raggruppamento, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_2.png)

Una volta creato un gruppo, è possibile modificarne facilmente i membri. Fare clic con il pulsante destro del mouse sul campo nel contenitore **Legenda** o nell'elenco **Campi**, quindi scegliere **Modifica gruppi**.

![Comando Modifica gruppi, elenchi Legenda e Campi, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_3.png)

Nella finestra di dialogo **Gruppi** è possibile creare nuovi gruppi o modificare i gruppi esistenti. È anche possibile *rinominare* qualsiasi gruppo. Basta fare doppio clic sul titolo del gruppo nella casella **Gruppi e membri** e quindi immettere un nuovo nome.

Con i gruppi è possibile eseguire ogni sorta di operazioni. È possibile aggiungere elementi dall'elenco **Valori non raggruppati** in un nuovo gruppo o in uno dei gruppi esistenti. Per creare un nuovo gruppo, selezionare due o più elementi (premendo CTRL mentre si fa clic) nella casella **Valori non raggruppati** e quindi selezionare il pulsante **Raggruppa** sotto tale casella.

È possibile aggiungere un valore non raggruppato in un gruppo esistente: è sufficiente selezionare la voce corrispondente in **Valori non raggruppati**, quindi selezionare il gruppo esistente a cui si vuole aggiungerlo e selezionare il pulsante **Raggruppa**. Per rimuovere un elemento da un gruppo, selezionarlo nella casella **Gruppi e membri** e quindi selezionare **Separa**. È anche possibile spostare categorie non raggruppate nel gruppo **Altro** o lasciarle non raggruppate.

![Finestra di dialogo Gruppi, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> È possibile creare gruppi per qualsiasi campo nell'elenco **Campi** senza dover selezionare più elementi da un oggetto visivo esistente. Fare clic con il pulsante destro del mouse sul campo e selezionare **Nuovo gruppo** dal menu visualizzato.

## <a name="using-binning"></a>Uso della creazione di contenitori
È possibile impostare le dimensioni del contenitore per i campi numerici e ora in **Power BI Desktop**. È possibile usare il binning, o creazione di contenitori, per assegnare le dimensioni appropriate ai dati visualizzati da Power BI Desktop.

Per applicare una dimensione al contenitore, fare clic con il pulsante destro del mouse su un **campo** e scegliere **Nuovo gruppo**.

![Comando Nuovo gruppo, elenco Campi, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_5.png)

Nella finestra di dialogo **Gruppi** impostare **Dimensioni contenitore** sulle dimensioni desiderate.

![Dimensioni contenitore, finestra di dialogo Gruppi, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_6.png)

Quando si seleziona **OK**, verrà visualizzato un nuovo campo nel riquadro **Campi** con **(contenitori)** accodato. È quindi possibile trascinare il campo nell'area di disegno per usare la dimensione del contenitore in un oggetto visivo.

![Trascinare il campo contenitori nell'area di disegno, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_7.png)

Per vedere in azione la *creazione di contenitori*, dare uno sguardo a questo [video](https://www.youtube.com/watch?v=BRvdZSfO0DY).

E questo è tutto per quanto riguarda l'uso del *raggruppamento* e della *creazione di contenitori* per assicurarsi che gli oggetti visivi nei report mostrino i dati nel modo desiderato.
