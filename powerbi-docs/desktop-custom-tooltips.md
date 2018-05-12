---
title: Personalizzazione delle descrizioni comando in Power BI Desktop
description: Creare descrizioni comando personalizzate per oggetti visivi mediante trascinamento
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6783987bb0afaea4131012425d91aacb2decb5cf
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizzazione delle descrizioni comando in Power BI Desktop
Le descrizioni comando sono un modo elegante di offrire altre informazioni contestuali e dettagli ai punti dati su un oggetto visivo. L'immagine seguente mostra una descrizione comando applicata a un grafico in Power BI Desktop.

![](media/desktop-custom-tooltips/custom-tooltips_1.png)

Quando viene creata una visualizzazione, la descrizione comando predefinita visualizza il valore e la categoria del punto dati. La possibilità di personalizzare le informazioni di descrizione comando è estremamente utile e consente di offrire più contesto e informazioni aggiuntive agli utenti che visualizzano l'oggetto visivo. Le descrizioni comando personalizzate consentono di specificare più punti dati che vengono visualizzati come parte della descrizione comando.

## <a name="how-to-customize-tooltips"></a>Come personalizzare le descrizioni comando
Per creare una descrizione comando personalizzata, nel contenitore **Campi** del riquadro **Visualizzazioni** basta trascinare un campo nel bucket **Descrizioni comando** come illustrato nell'immagine seguente. Nell'immagine seguente, sono stati posizionati quattro campi nel bucket **Descrizioni comando**.

![](media/desktop-custom-tooltips/custom-tooltips_2.png)

Dopo aver aggiunto le descrizioni comando nel contenitore di campi, passando il puntatore su un punto dati nella visualizzazione è possibile visualizzare i valori per i campi nella descrizione comando.

![](media/desktop-custom-tooltips/custom-tooltips_3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizzazione delle descrizioni comando tramite aggregazioni o Calcolo rapido
È possibile personalizzare ulteriormente una descrizione comando tramite una funzione di aggregazione o un *Calcolo rapido* facendo clic sulla freccia accanto al campo nel bucket **Descrizioni comando** e scegliendo tra le opzioni disponibili.

![](media/desktop-custom-tooltips/custom-tooltips_4.png)

Esistono diversi modi per personalizzare le **Descrizioni comando** tramite uno dei campi disponibili nel set di dati, quindi per trasmettere informazioni rapide e approfondimenti agli utenti che visualizzano dashboard o report.

