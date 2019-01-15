---
title: Usare la visualizzazione di modellazione in Power BI Desktop (anteprima)
description: Usare la visualizzazione di modellazione per vedere set di dati complessi in formato visivo in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 84e2bc663a4e3912608279c7315bc494b3c9844a
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296525"
---
# <a name="modeling-view-in-power-bi-desktop-preview"></a>Visualizzazione di modellazione in Power BI Desktop (anteprima)

Con la **visualizzazione di modellazione** in **Power BI Desktop**, è possibile visualizzare e usare set di dati complessi contenenti molte tabelle. Con la visualizzazione di modellazione, è possibile eseguire le operazioni seguenti:


## <a name="enabling-the-modeling-view-preview-feature"></a>Abilitazione della funzionalità in anteprima visualizzazione di modellazione

La funzionalità visualizzazione di modellazione è disponibile in anteprima e deve essere abilitata in **Power BI Desktop**. Per abilitare la visualizzazione di modellazione, selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità in anteprima**, quindi selezionare la casella di controllo **Visualizzazione di modellazione** come illustrato nell'immagine seguente.

![Abilitare la funzionalità in anteprima visualizzazione di modellazione in Power BI Desktop](media/desktop-modeling-view/modeling-view_01.png)

Verrà indicato che è necessario riavviare **Power BI Desktop** per rendere effettiva la funzionalità in anteprima. 

![Riavviare Power BI Desktop per abilitare le funzionalità in anteprima](media/desktop-modeling-view/modeling-view_01b.png)

## <a name="using-modeling-view"></a>Uso della visualizzazione di modellazione

Per accedere alla visualizzazione di modellazione, selezionare l'icona Visualizzazione di modellazione sul lato sinistro di **Power BI Desktop**, come illustrato nell'immagine seguente.

![Icona Visualizzazione di modellazione in Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Creazione di diagrammi separati

Con la visualizzazione di modellazione, è possibile creare diagrammi del modello contenenti solo un subset delle tabelle nel modello. Ciò consente di ottenere una visualizzazione più chiara delle tabelle che si vuole usare e di semplificare l'uso dei set di dati complessi. Per creare un nuovo diagramma solo con un subset delle tabelle, fare clic sul segno **+** accanto alla scheda **Tutte le tabelle** nella parte inferiore della finestra di Power BI Desktop.

![Creare un nuovo diagramma facendo clic sul segno + nella sezione delle schede](media/desktop-modeling-view/modeling-view_03.png)

È quindi possibile trascinare una tabella dall'elenco **Campi** alla superficie del diagramma. Fare clic con il pulsante destro del mouse sulla tabella e quindi scegliere **Aggiungi tabelle correlate** dal menu visualizzato.

![Fare clic con il pulsante destro del mouse su una tabella e scegliere Aggiungi tabelle correlate](media/desktop-modeling-view/modeling-view_04.png)

Quando si esegue questa operazione, le tabelle correlate alla tabella originale vengono visualizzate nel nuovo diagramma. L'immagine seguente illustra come vengono visualizzate le tabelle correlate dopo aver selezionato l'opzione di menu **Aggiungi tabelle correlate**.

![Visualizzazione delle tabelle correlate](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Impostazione delle proprietà comuni

In visualizzazione di modellazione è possibile selezionare più oggetti contemporaneamente tenendo premuto il tasto **CTRL** e facendo clic su più tabelle. Tutte le tabelle selezionate vengono evidenziate nella visualizzazione di modellazione. Quando sono evidenziate più tabelle, le modifiche applicate nel riquadro **Proprietà** vengono applicate a tutte le tabelle selezionate.

È ad esempio possibile modificare la [modalità di archiviazione](desktop-storage-mode.md) per più tabelle nella Visualizzazione diagramma tenendo premuto il tasto **CTRL**, selezionando le tabelle, quindi modificando l'impostazione della modalità di archiviazione nel riquadro **Proprietà**.

![Selezionare più tabelle tenendo premuto CTRL, quindi impostare le proprietà comuni per tutte le tabelle selezionate](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Passaggi successivi

Gli articoli seguenti includono altre informazioni sui modelli di dati e descrivono anche la modalità DirectQuery in modo dettagliato.

* [Aggregazioni in Power BI Desktop (anteprima)](desktop-aggregations.md)
* [Modelli compositi in Power BI Desktop (anteprima)](desktop-composite-models.md)
* [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md)
* [Relazioni molti-a-molti in Power BI Desktop (anteprima)](desktop-many-to-many-relationships.md)


Articoli su DirectQuery:

* [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
* [Origini dati supportate da DirectQuery in Power BI](desktop-directquery-data-sources.md)
