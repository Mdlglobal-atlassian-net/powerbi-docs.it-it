---
title: Modificare l'ordinamento di un grafico in un report
description: Modificare l'ordinamento di un grafico in un report di Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: Conceptual
ms.date: 05/12/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 67246168b5387f49e7bda22e470f5a908a4bff9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608258"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modificare l'ordinamento di un grafico in un report di Power BI
In un report di Power BI è possibile ordinare alfabeticamente la maggior parte delle visualizzazioni in base ai nomi delle categorie contenute nel grafico oppure in base ai valori numerici di ciascuna categoria. Ad esempio, questo grafico viene ordinato in base alla categoria **store name**.

![grafico a barre ordinato alfabeticamente in base all'asse X](media/end-user-change-sort/pbi_chartsortcategory.png)

È possibile modificare con facilità l'ordinamento da una categoria (nome di un negozio) a un valore (vendite per piede quadrato).

1. Selezionare i puntini di sospensione (...) e scegliere **Ordina per > Sales Per Sq Ft**.
2. Se necessario, selezionare di nuovo i puntini di sospensione e scegliere **Ordinamento decrescente**.

   ![video che illustra come selezionare Ordina per e poi Ordinamento crescente o Ordinamento decrescente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> non è possibile ordinare tutti gli oggetti visivi. Ad esempio, gli oggetti visivi seguenti non possono essere ordinati: Mappa ad albero, Mappa, Mappa colorata, Grafico a dispersione, Misuratore, Scheda, Scheda con più righe, Grafico a cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Salvataggio delle modifiche all'ordinamento
I report di Power BI mantengono i filtri, i filtri dei dati, l'ordinamento e altre modifiche alla visualizzazione dei dati. Pertanto, se si esce da un report e lo si visualizza di nuovo, le modifiche sono salvate.  Per annullare le modifiche e ripristinare le impostazioni del designer del report, selezionare **Ripristina impostazioni predefinite** dalla barra dei menu superiore. 

![ordinamento permanente](media/end-user-change-sort/power-bi-reset-to-default.png)

Se tuttavia il pulsante **Ripristina impostazioni predefinite** appare disattivato, significa che il designer del report ha disabilitato la possibilità di salvare le modifiche.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordinamento in base ad altri criteri
In alcuni casi, è necessario ordinare l'oggetto visivo usando un campo diverso o altri criteri.  Ad esempio, è possibile ordinare per mese (anziché alfabeticamente) oppure ordinare per numeri interi anziché per cifra (esempio 0, 1, 9, 20 e non 0, 1, 20, 9).  

In alcuni casi, è possibile ordinare l'oggetto visivo nel modo desiderato, ad esempio, in base al mese.  In caso contrario, potrebbe essere necessario apportare alcune modifiche al set di dati del report. Chiedere al designer del report di aggiornare il set di dati.

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle [visualizzazioni nei report di Power BI](end-user-visualizations.md).

[Power BI - Concetti di base](end-user-basic-concepts.md)
