---
title: Visualizzazione delle relazioni in Power BI Desktop
description: Visualizzazione delle relazioni in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 178f3cd9015af503ff12875548822ba1ab5365c3
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54272767"
---
# <a name="relationship-view-in-power-bi-desktop"></a>Visualizzazione delle relazioni in Power BI Desktop
La **Visualizzazione relazioni** mostra tutte le tabelle, le colonne e le relazioni presenti nel modello. Ciò può essere particolarmente utile quando un modello contiene relazioni complesse tra molte tabelle.

Descrizione dettagliata

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Icona della Visualizzazione relazioni: fare clic per visualizzare il modello nella Visualizzazione relazioni

**B.** Relazione: è possibile passare il puntatore del mouse su una relazione per visualizzare le colonne usate. Fare doppio clic su una relazione per aprirla nella finestra di dialogo **Modifica relazione**. 

Nella figura sopra si può vedere che la tabella *Stores* contiene una colonna *StoreKey* correlata alla tabella *Sales*, anch'essa contenente una colonna *StoreKey*. Questa è una relazione *Molti-a-uno* (\*:1) e l'icona al centro della linea mostra la direzione del filtro incrociato impostata su *Entrambi*. La freccia sull'icona mostra la direzione del flusso di contesto di filtro.

Per altre informazioni sulle relazioni, vedere [Creare e gestire le relazioni in Power BI Desktop](desktop-create-and-manage-relationships.md).

