---
title: Modificare l'ordinamento di un grafico in un report
description: Modificare l'ordinamento di un grafico in un report di Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/01/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fdd43320fec2b96aa708cb5bb1a21e269a117d2a
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830671"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modificare l'ordinamento di un grafico in un report di Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]


> [!IMPORTANT]
> **Questo articolo è destinato agli utenti di Power BI senza autorizzazioni di modifica per il report o il set di dati. Per istruzioni più dettagliate sull'ordinamento, vedere [Ordinare per colonna in Power BI Desktop](../desktop-sort-by-column.md)**.

Nel servizio Power BI è possibile modificare l'aspetto di un oggetto visivo ordinandolo in base a campi dati diversi. La modifica dell'ordinamento di un oggetto visivo consente di dare risalto alle informazioni da comunicare.

Gli oggetti visivi in un dashboard non possono essere ordinati, ma in un report di Power BI è possibile ordinare la maggior parte delle visualizzazioni 

Sia che si usino dati numerici (come cifre di vendita) o dati di tipo testo (come nomi di stati), è possibile ordinare le visualizzazioni in qualsiasi modo. In Power BI sono disponibili funzionalità estremamente flessibili per l'ordinamento, nonché menu rapidi. 

## <a name="get-started"></a>Inizia

Per iniziare, selezionare un oggetto visivo e scegliere **Altre azioni** (...).  Per l'ordinamento sono disponibili tre opzioni: **Ordinamento decrescente**, **Ordinamento crescente** e **Ordina per**. 
    

![grafico a barre ordinato alfabeticamente in base all'asse X](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Ordinare alfabeticamente o numericamente

Gli oggetti visivi possono essere ordinati alfabeticamente in base ai nomi delle categorie contenute nell'oggetto visivo oppure in base ai valori numerici di ogni categoria. Ad esempio, questo grafico viene ordinato alfabeticamente in base alla categoria **Name** dell'asse X, indicante il negozio.

![grafico a barre ordinato alfabeticamente in base all'asse X](media/end-user-change-sort/powerbi-sort-category.png)

È possibile modificare con facilità l'ordinamento da una categoria (nome di un negozio) a un valore (vendite per piede quadrato). Selezionare **Altre azioni** (...) e scegliere **Ordina per**. Selezionare un valore numerico usato nell'oggetto visivo.  In questo esempio è stato selezionato **Sales Per Sq Ft**.

![Screenshot che mostra la selezione dell'opzione Ordina per e quindi di un valore](media/end-user-change-sort/power-bi-sort-value.png)

Se necessario, passare dall'ordinamento crescente a quello decrescente.  Selezionare di nuovo **Altre opzioni** (...) e scegliere **Ordinamento decrescente** o **Ordinamento crescente**. Il campo usato per l'ordinamento è in grassetto e ha una barra gialla.

   ![video che illustra come selezionare Ordina per e poi Ordinamento crescente o Ordinamento decrescente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> non è possibile ordinare tutti gli oggetti visivi. Non è ad esempio possibile ordinare gli oggetti visivi seguenti: mappa ad albero, mappa, mappa colorata, grafico a dispersione, misuratore, scheda, grafico a cascata.

## <a name="saving-changes-you-make-to-sort-order"></a>Salvataggio delle modifiche all'ordinamento
I report di Power BI mantengono i filtri, i filtri dei dati, l'ordinamento e altre modifiche alla visualizzazione dei dati. Se quindi si esce da un report e lo si visualizza di nuovo, le modifiche apportate all'ordinamento risultano salvate.  Per annullare le modifiche e ripristinare le impostazioni del progettista del report, selezionare **Ripristina impostazioni predefinite** dalla barra dei menu superiore. 

![ordinamento permanente](media/end-user-change-sort/power-bi-reset.png)

Se tuttavia il pulsante **Ripristina impostazioni predefinite** appare disattivato, significa che il *progettista* del report ha disabilitato la possibilità di salvare le modifiche.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

### <a name="sorting-using-other-criteria"></a>Ordinamento in base ad altri criteri
In alcuni casi, è necessario ordinare l'oggetto visivo usando un campo diverso, che non è incluso nell'oggetto visivo, o altri criteri.  È ad esempio possibile ordinare per mese in modo sequenziale (e non alfabeticamente) oppure ordinare per numeri interi invece che per cifra (esempio 0, 1, 9, 20 e non 0, 1, 20, 9).  Solo la persona che ha progettato il report può apportare queste modifiche. Per trovare le informazioni sul contatto del *progettista*, selezionare il nome del report nella barra dell'intestazione.

![Elenco a discesa che mostra le informazioni di contatto](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sulle [visualizzazioni nei report di Power BI](end-user-visualizations.md).

[Power BI - Concetti di base](end-user-basic-concepts.md)
