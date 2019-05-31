---
title: Personalizzazione delle descrizioni comando in Power BI Desktop
description: Creare descrizioni comando personalizzate per oggetti visivi mediante trascinamento
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d5259ba22287a8a2ade3107e4320c39713dcb45e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239751"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personalizzazione delle descrizioni comando in Power BI Desktop
Le descrizioni comando sono un modo elegante di offrire altre informazioni contestuali e dettagli ai punti dati su un oggetto visivo. L'immagine seguente mostra una descrizione comando applicata a un grafico in Power BI Desktop.

![Descrizione comando predefinita](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quando viene creata una visualizzazione, la descrizione comando predefinita visualizza il valore e la categoria del punto dati. Sono presenti molte istanze quando la personalizzazione delle informazioni di descrizione comando è utile e può fornire ulteriore contesto nonché informazioni per gli utenti visualizzano l'oggetto visivo. Le descrizioni comando personalizzate consentono di specificare più punti dati che vengono visualizzati come parte della descrizione comando.

## <a name="how-to-customize-tooltips"></a>Come personalizzare le descrizioni comando
Per creare una descrizione comando personalizzata, nelle **campi** del **visualizzazioni** riquadro trascinare un campo nel **descrizioni comando** bucket, illustrato nella figura seguente. Nell'immagine seguente sono stati posizionati due campi nel bucket **Descrizioni comando**.

![Aggiunta di campi della descrizione comando](media/desktop-custom-tooltips/custom-tooltips-2.png)

Dopo aver aggiunto le descrizioni comando nel contenitore di campi, quando si passa il puntatore su un punto dati della visualizzazione, i valori dei campi vengono visualizzati nella descrizione comando.

![Descrizione comando personalizzata](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personalizzazione delle descrizioni comando tramite aggregazioni o Calcolo rapido
È possibile personalizzare ulteriormente una descrizione comando tramite una funzione di aggregazione o un *Calcolo rapido* facendo clic sulla freccia accanto al campo nel bucket **Descrizioni comando** e scegliendo tra le opzioni disponibili.

![Descrizione comando con Calcolo rapido](media/desktop-custom-tooltips/custom-tooltips-4.png)

Esistono diversi modi per personalizzare **descrizioni comando**, usando dei campi disponibili nel set di dati, per trasmettere informazioni rapide e approfondimenti agli utenti che visualizzano dashboard o report.

