---
title: Evidenziazione
description: Evidenziazioni delle selezioni dei punti dati in oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4ff2187dc99d4e790b08c11f55a37e31e85693ad
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193994"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Evidenziare i punti dati in oggetti visivi di Power BI

Per impostazione predefinita, ogni volta che un elemento viene selezionato, la matrice `values` nell'oggetto `dataView` viene filtrata in base ai soli valori selezionati. Tutti gli altri oggetti visivi nella pagina visualizzeranno solo i dati selezionati.

![Comportamento di evidenziazione predefinito di "dataView"](./media/highlight-dataview.png)

Se si imposta la proprietà `supportsHighlight` nel file `capabilities.json` su `true`, si riceve la matrice `values` completa non filtrata insieme a una matrice `highlights`. La matrice `highlights` avrà la stessa lunghezza della matrice values e tutti i valori non selezionati verranno impostati su `null`. Se questa proprietà è abilitata, è responsabilità dell'oggetto visivo evidenziare i dati appropriati confrontando la matrice `values` con la matrice `highlights`.

![Supporto dell'evidenziazione in "dataView"](./media/highlight-dataview-supports.png)

Nell'esempio si può notare che la barra 1 è selezionata. È l'unico valore nella matrice highlights. È anche importante notare che potrebbero essere presenti più selezioni e un'evidenziazione parziale. Il valore numerico corrispondente è presente nei valori e le matrici highlights saranno presenti, ma diverse.
