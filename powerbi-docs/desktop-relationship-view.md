---
title: Visualizzazione delle relazioni in Power BI Desktop
description: Visualizzazione delle relazioni in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cd9671b8c38cb2aa1502c3aa00a871d125f819b1
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760481"
---
# <a name="work-with-relationship-view-in-power-bi-desktop"></a>Utilizzo di Visualizzazione relazioni in Power BI Desktop
La **Visualizzazione relazioni** mostra tutte le tabelle, le colonne e le relazioni presenti nel modello. Ciò può essere particolarmente utile quando un modello contiene relazioni complesse tra molte tabelle.

Descrizione dettagliata

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Icona della Visualizzazione relazioni: fare clic per visualizzare il modello nella Visualizzazione relazioni

**B.** Relazione: è possibile passare il puntatore del mouse su una relazione per visualizzare le colonne usate. Fare doppio clic su una relazione per aprirla nella finestra di dialogo **Modifica relazione**. 

Nella figura sopra si può vedere che la tabella *Stores* contiene una colonna *StoreKey* correlata alla tabella *Sales*, anch'essa contenente una colonna *StoreKey*. Questa è una relazione *Molti-a-uno* (\*:1) e l'icona al centro della linea mostra la direzione del filtro incrociato impostata su *Entrambi*. La freccia sull'icona mostra la direzione del flusso di contesto di filtro.

Per altre informazioni sulle relazioni, vedere [Creare e gestire le relazioni in Power BI Desktop](desktop-create-and-manage-relationships.md).

