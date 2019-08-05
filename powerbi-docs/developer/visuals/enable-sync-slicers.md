---
title: Abilitare la funzionalità Sincronizza filtri dei dati
description: Come aggiungere la funzionalità Sincronizza filtri dei dati per gli oggetti visivi di Power BI
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425023"
---
# <a name="sync-slicers"></a>Sincronizza filtri dei dati

Per supportare la funzionalità [Sincronizza filtri dei dati](https://docs.microsoft.com/power-bi/desktop-slicers), l'oggetto visivo filtro dei dati personalizzato deve usare l'API 1.13 o versione successiva.

Il secondo aspetto necessario è che l'opzione sia abilitata in `capabilities.json` (vedere un esempio di seguito).

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Una volta apportate le modifiche in `capabilities.json`, è possibile visualizzare il pannello delle opzioni Sincronizza filtri dei dati quando si fa clic sull'oggetto visivo filtro dei dati personalizzato.

> [!NOTE]
> Se il filtro dei dati contiene più di un campo (categoria o misura), la funzionalità verrà disabilitata perché non supporta la presenza di più campi.

![Riquadro Sincronizza filtri dei dati](./media/sync-slicers-panel.png)

Nel pannello è possibile osservare che la visibilità del filtro dei dati e l'applicazione del filtro possono essere applicate per diverse pagine del report.
