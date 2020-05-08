---
title: Personalizzazione delle descrizioni comando in Power BI Desktop
description: Creare descrizioni comando personalizzate per oggetti visivi mediante trascinamento
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 93177ac56bc2d8ecfe4b85f4ab66daef6bf0f0f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161018"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Personalizzare le descrizioni comando in Power BI Desktop

Le descrizioni comando sono un modo elegante di offrire altre informazioni contestuali e dettagli ai punti dati su un oggetto visivo. L'immagine seguente mostra una descrizione comando applicata a un grafico in Power BI Desktop.

![Descrizione comando predefinita](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando viene creata una visualizzazione, la descrizione comando predefinita visualizza il valore e la categoria del punto dati. Quando si personalizzano le informazioni sulla descrizione comando sono disponibili molte istanze. La personalizzazione delle descrizioni comando offre ulteriore contesto e informazioni aggiuntive per gli utenti che visualizzano l'oggetto visivo. Le descrizioni comando personalizzate consentono di specificare più punti dati che vengono visualizzati come parte della descrizione comando.

## <a name="how-to-customize-tooltips"></a>Come personalizzare le descrizioni comando

Per creare una descrizione comando personalizzata, nel contenitore **Campi** del riquadro **Visualizzazioni** trascinare un campo nel bucket **Descrizioni comando** come illustrato nell'immagine seguente. Nell'immagine seguente sono stati posizionati tre campi nel bucket **Descrizioni comando**.

![Aggiunta di campi della descrizione comando](media/desktop-custom-tooltips/custom-tooltips-2.png)

Dopo aver aggiunto le descrizioni comando a **Descrizioni comando**, quando si passa il mouse su un punto dati della visualizzazione, vengono visualizzati i valori di quei campi.

![Descrizione comando personalizzata](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>Personalizzazione delle descrizioni comando con aggregazioni o misure rapide

È possibile personalizzare ulteriormente una descrizione comando selezionando una funzione di aggregazione o una *misura rapida*. Selezionare la freccia accanto al campo nel bucket **Descrizioni comando**. Quindi, selezionare una delle opzioni disponibili.

![Descrizione comando con misura rapida](media/desktop-custom-tooltips/custom-tooltips-4.png)

Esistono diversi modi per personalizzare le descrizioni comando, usando uno dei campi disponibili nel set di dati, e trasmettere informazioni rapide e approfondimenti agli utenti che visualizzano dashboard o report.
