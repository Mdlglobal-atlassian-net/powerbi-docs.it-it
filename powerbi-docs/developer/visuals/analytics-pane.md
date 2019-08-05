---
title: Riquadro di analisi
description: Come creare linee di riferimento dinamiche negli oggetti visivi di Power BI
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425529"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Riquadro di analisi negli oggetti visivi di Power BI

Il **riquadro di analisi** è stato [introdotto per gli oggetti visivi nativi ](https://docs.microsoft.com/power-bi/desktop-analytics-pane) a novembre 2018.
Gli oggetti visivi personalizzati con l'API v2.5.0 possono presentare e gestire le proprie proprietà nel **riquadro di analisi**.

![Riquadro di analisi](./media/visualization-pane-analytics-tab.png)

Viene gestito in modo analogo alla [gestione delle proprietà nel riquadro Formato](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), definendo un oggetto nel file capabilities.json dell'oggetto visivo. 

Le differenze sono le seguenti:

1. Nella definizione di `object` aggiungere un campo `objectCategory` con valore 2.

    > [!NOTE]
    > Il campo `objectCategory` è un campo facoltativo introdotto nell'API 2.5.0. Definisce l'aspetto dell'oggetto visivo controllato dall'oggetto (1 = Formatting, 2 = Analytics). La categoria "Formatting" viene usata per aspetto, colori, assi, etichette e così via. La categoria "Analytics" viene usata per previsioni, linee di tendenza, linee di riferimento, forme e così via.
    >
    > Se omesso, il valore predefinito di `objectCategory` è "Formatting".

2. L'oggetto deve avere le due proprietà seguenti:
    1. `show` di tipo booleano con valore predefinito false.
    2. `displayName` di tipo testo. Il valore predefinito scelto diventerà il nome visualizzato iniziale dell'istanza.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Tutte le altre proprietà devono essere definite in modo analogo a quanto avviene per gli oggetti di formattazione. L'enumerazione degli oggetti viene eseguita esattamente come nel **riquadro Formato**.

***Limitazioni e problemi noti***

  1. Non sono ancora supportate più istanze. Gli oggetti non possono avere un [selettore](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) diverso da uno statico, ovvero "selector" = null, e gli oggetti visivi personalizzati non possono avere più istanze di una scheda definite dall'utente.
  2. Le proprietà di tipo `integer` non vengono visualizzate correttamente. Come soluzione alternativa, usare invece il tipo `numeric`.

> [!NOTE]
> Usare il riquadro di analisi solo per gli oggetti che aggiungono nuove informazioni o fanno luce sulle informazioni presentate. Ad esempio, le linee di riferimento dinamiche che illustrano tendenze importanti.
> Tutte le opzioni che controllano l'aspetto dell'oggetto visivo, ovvero la formattazione, devono essere mantenute nel riquadro di formattazione.
