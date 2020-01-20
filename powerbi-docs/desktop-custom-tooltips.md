---
title: Personalizzazione delle descrizioni comando in Power BI Desktop
description: Creare descrizioni comando personalizzate per oggetti visivi mediante trascinamento
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 08eda4e93a3e02e357c8153c656ec16811893ea9
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761434"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Personalizzare le descrizioni comando in Power BI Desktop
Le descrizioni comando sono un modo elegante di offrire altre informazioni contestuali e dettagli ai punti dati su un oggetto visivo. L'immagine seguente mostra una descrizione comando applicata a un grafico in Power BI Desktop.

![Descrizione comando predefinita](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando viene creata una visualizzazione, la descrizione comando predefinita visualizza il valore e la categoria del punto dati. La possibilità di personalizzare le informazioni delle descrizioni comando è estremamente utile e consente di offrire più contesto e informazioni aggiuntive agli utenti che visualizzano l'oggetto visivo. Le descrizioni comando personalizzate consentono di specificare più punti dati che vengono visualizzati come parte della descrizione comando.

## <a name="how-to-customize-tooltips"></a>Come personalizzare le descrizioni comando
Per creare una descrizione comando personalizzata, nel contenitore **Campi** del riquadro **Visualizzazioni** trascinare un campo nel bucket **Descrizioni comando** come illustrato nell'immagine seguente. Nell'immagine seguente sono stati posizionati due campi nel bucket **Descrizioni comando**.

![Aggiunta di campi della descrizione comando](media/desktop-custom-tooltips/custom-tooltips-2.png)

Dopo aver aggiunto le descrizioni comando nel contenitore di campi, quando si passa il puntatore su un punto dati della visualizzazione, i valori dei campi vengono visualizzati nella descrizione comando.

![Descrizione comando personalizzata](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizzazione delle descrizioni comando tramite aggregazioni o Calcolo rapido
È possibile personalizzare ulteriormente una descrizione comando tramite una funzione di aggregazione o un *Calcolo rapido* facendo clic sulla freccia accanto al campo nel bucket **Descrizioni comando** e scegliendo tra le opzioni disponibili.

![Descrizione comando con Calcolo rapido](media/desktop-custom-tooltips/custom-tooltips-4.png)

Esistono diversi modi per personalizzare le **descrizioni comando** usando uno dei campi disponibili nel set di dati, quindi per trasmettere informazioni rapide e approfondimenti agli utenti che visualizzano dashboard o report.

