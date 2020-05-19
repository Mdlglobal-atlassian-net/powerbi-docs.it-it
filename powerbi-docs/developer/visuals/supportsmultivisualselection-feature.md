---
title: Funzionalità supportsMultiVisualSelection
description: Questo articolo descrive come usare la funzionalità supportsMultiVisualSelection negli oggetti visivi di Power BI e illustra i requisiti necessari.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272696"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Usare la funzionalità supportsMultiVisualSelection

La funzionalità `supportsMultiVisualSelection` consente di usare la selezione in più oggetti visivi in un report.

## <a name="example"></a>Esempio

In un report con più oggetti visivi selezionare due valori per applicarli ad altri oggetti visivi. In [Retail Analysis Sample](../../create-reports/sample-retail-analysis.md), ad esempio, selezionare **Fashions Direct** in un unico oggetto visivo. Premere CTRL e selezionare **Jan** in un altro oggetto visivo. Nel report le selezioni vengono applicate agli altri oggetti visivi che supportano l'utilizzo di questa funzionalità. Gli altri oggetti visivi ora hanno come ambito **Fashions Direct** e **Jan**.

## <a name="requirements"></a>Requisiti

Questa funzionalità richiede l'API v3.2.0 o versione successiva.

Non è possibile applicare questa funzionalità agli oggetti visivi immagine. Non è possibile applicarla ad alcuni oggetti visivi avanzati, ad esempio driver chiave, alberi di scomposizione, oggetti visivi Domande e risposte, caselle di testo e grafici a misuratore.

## <a name="usage"></a>Usage

Per usare la funzionalità `supportsMultiVisualSelection`, aggiungere il codice seguente al file `capabilities.json` dell'oggetto visivo.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sui concetti di Power BI, vedere [Oggetti visivi in Power BI](power-bi-visuals-concept.md).

Per provare lo sviluppo in Power BI, vedere [Sviluppo di un oggetto visivo di Power BI](custom-visual-develop-tutorial.md).
