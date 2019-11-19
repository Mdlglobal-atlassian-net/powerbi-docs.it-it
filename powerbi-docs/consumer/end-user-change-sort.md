---
title: Modificare l'ordinamento di un grafico in un report
description: Modificare l'ordinamento di un grafico in un report di Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852378"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modificare l'ordinamento di un grafico in un report di Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Nel servizio Power BI è possibile modificare l'aspetto di un oggetto visivo ordinandolo in base a campi dati diversi. La modifica dell'ordinamento di un oggetto visivo consente di dare risalto alle informazioni da comunicare e di garantire che l'oggetto visivo evidenzi la tendenza prevista.

Sia che si usino dati numerici (come cifre di vendita) o dati di tipo testo (come nomi di stati), è possibile ordinare le visualizzazioni in qualsiasi modo per ottenere l'aspetto desiderato. In Power BI sono disponibili funzionalità estremamente flessibili per l'ordinamento, nonché menu rapidi. In qualsiasi oggetto visivo selezionare **Altre opzioni** (...) e quindi selezionare il campo in base al quale si vuole eseguire l'ordinamento.

![grafico a barre ordinato alfabeticamente in base all'asse X](media/end-user-change-sort/power-bi-more-actions.png)

Gli oggetti visivi in un dashboard non possono essere ordinati, ma in un report di Power BI è possibile ordinare alfabeticamente la maggior parte delle visualizzazioni in base ai nomi delle categorie contenute nel grafico oppure in base ai valori numerici di ciascuna categoria. Ad esempio, questo grafico viene ordinato alfabeticamente in base alla categoria **store name**.

![grafico a barre ordinato alfabeticamente in base all'asse X](media/end-user-change-sort/pbi-chartsortcategory.png)

È possibile modificare con facilità l'ordinamento da una categoria (nome di un negozio) a un valore (vendite per piede quadrato).

1. Selezionare **Altre opzioni** (...) e scegliere **Ordina per > Sales Per Sq Ft**.
2. Se necessario, selezionare di nuovo **Altre opzioni** (...) e scegliere **Ordinamento decrescente**. Il campo usato per l'ordinamento è in grassetto e ha una barra gialla.

   ![video che illustra come selezionare Ordina per e poi Ordinamento crescente o Ordinamento decrescente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> non è possibile ordinare tutti gli oggetti visivi. Non è ad esempio possibile ordinare gli oggetti visivi seguenti: mappa ad albero, mappa, mappa colorata, grafico a dispersione, misuratore, scheda, grafico a cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Salvataggio delle modifiche all'ordinamento
I report di Power BI mantengono i filtri, i filtri dei dati, l'ordinamento e altre modifiche alla visualizzazione dei dati. Pertanto, se si esce da un report e lo si visualizza di nuovo, le modifiche sono salvate.  Per annullare le modifiche e ripristinare le impostazioni del progettista del report, selezionare **Ripristina impostazioni predefinite** dalla barra dei menu superiore. 

![ordinamento permanente](media/end-user-change-sort/power-bi-reset.png)

Tuttavia, se il pulsante **Ripristina impostazioni predefinite** appare disattivato, significa che il progettista del report ha disabilitato la possibilità di salvare le modifiche.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Ordinamento in base ad altri criteri
In alcuni casi, è necessario ordinare l'oggetto visivo usando un campo diverso, che non è incluso nell'oggetto visivo, o altri criteri.  Ad esempio, è possibile ordinare per mese (anziché alfabeticamente) oppure ordinare per numeri interi anziché per cifra (esempio 0, 1, 9, 20 e non 0, 1, 20, 9).  Il progettista del report sarà in grado di aggiornare il set di dati per abilitare questo tipo di ordinamento. È possibile trovare le informazioni di contatto per il progettista del report selezionando il nome del report nella barra di intestazione.

![Elenco a discesa che mostra le informazioni di contatto](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle [visualizzazioni nei report di Power BI](end-user-visualizations.md).

[Power BI - Concetti di base](end-user-basic-concepts.md)
