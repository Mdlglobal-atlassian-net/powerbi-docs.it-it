---
title: Visualizzazione Modello in Power BI Desktop
description: Visualizzazione Modello in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ea568c061142e66e79351de8a6c0f0603a46f775
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753227"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Usare la visualizzazione Modello in Power BI Desktop

La *visualizzazione Modello* mostra tutte le tabelle, le colonne e le relazioni presenti nel modello. Può essere particolarmente utile quando un modello contiene relazioni complesse tra molte tabelle.

Selezionare l'icona **Modello** accanto al lato della finestra per attivare una visualizzazione del modello esistente. Passare il puntatore del mouse su una linea di relazione per visualizzare le colonne usate.

![Visualizzazione Modello, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

Nella figura, la tabella *Stores* contiene una colonna *StoreKey* correlata alla tabella *Sales*, che contiene anch'essa una colonna *StoreKey*. Le due tabelle sono associate tramite una relazione *molti-a-uno* (\*:1). Una freccia al centro della linea mostra la direzione del flusso del contesto del filtro. Le doppie frecce indicano che la direzione del filtro incrociato è impostata su *Entrambi*.

È possibile fare doppio clic su una relazione per aprirla nella finestra di dialogo **Modifica relazione**. Per altre informazioni sulle relazioni, vedere [Creare e gestire le relazioni in Power BI Desktop](desktop-create-and-manage-relationships.md).
