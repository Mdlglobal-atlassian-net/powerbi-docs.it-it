---
title: Usare le linee della griglia e il blocco alla griglia nei report di Power BI Desktop
description: Usare le linee della griglia, il blocco alla griglia, l'ordine Z, l'allineamento e la distribuzione nei report di Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 4/19/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7477fc19dda5aeb7729fbbde319faa0d930db179
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34289833"
---
# <a name="use-gridlines-and-snap-to-grid-in-power-bi-desktop-reports"></a>Usare le linee della griglia e il blocco alla griglia nei report di Power BI Desktop
L'area di disegno dei report **Power BI Desktop** offre linee della griglia che consentono di allineare accuratamente gli oggetti visivi in una pagina del report e di usare funzionalità per bloccare alla griglia tali oggetti del report per un aspetto pulito, allineato e distribuito in modo uniforme.

In **Power BI Desktop** è anche possibile modificare l'ordine Z (portare avanti o indietro) degli oggetti in un report e allineare o distribuire uniformemente gli oggetti visivi selezionati nell'area di disegno.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_0.png)

### <a name="enabling-gridlines-and-snap-to-grid"></a>Abilitazione delle linee guida della griglia e del blocco alla griglia
Per abilitare le linee della griglia, selezionare la barra multifunzione **Visualizzazione**, quindi selezionare le caselle di controllo **Mostra griglia** e **Blocca sulla griglia**. È possibile selezionare una o entrambe le opzioni perché funzionano in modo indipendente.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_1.png)

> [!NOTE]
> Se le opzioni **Mostra griglia** e **Blocca sulla griglia** sono disabilitate, connettersi a qualsiasi origine dati per attivarle.
> 
> 

### <a name="using-gridlines"></a>Uso delle linee delle griglie
Le linee della griglia sono guide visibili che consentono di allineare gli oggetti visivi. Per stabilire se due o più oggetti visivi sono allineati orizzontalmente o verticalmente, usare le linee della griglia per determinare se i bordi sono allineati.

Usare CTRL + clic per selezionare più di un oggetto visivo contemporaneamente e visualizzare i bordi di tutti gli oggetti visivi selezionati e vedere se gli elementi visivi sono allineati correttamente.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_2.png)

#### <a name="using-gridlines-inside-visuals"></a>Uso delle linee della griglia negli oggetti visivi
In Power BI sono anche disponibili linee della griglia negli oggetti visivi, per una guida visibile, utile nel confronto di valori e punti dati. A partire dalla versione di settembre 2017 di **Power BI Desktop**, è possibile gestire le linee della griglia negli oggetti visivi usando la scheda **Asse X** o **Asse Y** (in base al tipo di oggetto visivo) nella sezione **Formato** del riquadro **Visualizzazioni**. È possibile gestire gli elementi seguenti delle linee della griglia in un oggetto visivo:

* Attivare o disattivare le linee della griglia
* Modificare il colore delle linee della griglia
* Modificare la larghezza delle linee della griglia
* Selezionare lo stile delle linee della griglia nell'oggetto visivo, ad esempio continuo, tratteggiato o punteggiato

Modificare alcuni elementi delle linee della griglia può risultare particolarmente utile nei report in cui vengono usati sfondi scuri per gli oggetti visivi. L'immagine seguente mostra la sezione **Linee della griglia** nella scheda **Asse Y**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_9.png)

### <a name="using-snap-to-grid"></a>Uso di Blocca sulla griglia
Quando si abilita **Blocca sulla griglia**, tutti gli oggetti visivi nell'area di disegno di **Power BI Desktop** spostati o ridimensionati vengono automaticamente allineati all'asse della griglia più vicino, rendendo molto l'allineamento di due o più oggetti visivi alle dimensioni o alla stessa posizione orizzontale o verticale.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_3.png)

Non è necessaria nessuna altra azione per usare la **griglia** e il **blocco alla griglia** ai fini dell'allineamento corretto degli oggetti visivi nei report.

### <a name="using-z-order-align-and-distribute"></a>Uso di ordine Z, allineamento e distribuzione
È possibile gestire l'ordine dalla parte anteriore a quella posteriore degli oggetti visivi in un report, noto anche come *ordine Z* degli elementi. Questa funzionalità consente di sovrapporre gli oggetti visivi in qualsiasi modo desiderato, quindi modificare l'ordine dalla parte anteriore a quella posteriore di ognuno. Per impostare l'ordine degli oggetti visivi, si usano i pulsanti **Porta avanti** e **Porta indietro**, disponibili nella sezione **Disponi** della barra multifunzione **Formato**. La barra multifunzione **Formato** viene visualizzata non appena si seleziona uno o più oggetti visivi nella pagina.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_4.png)

La barra multifunzione **Formato** consente di allineare gli oggetti visivi in più modi, assicurando che vengano visualizzati nella pagina nel modo più funzionale.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_5.png)

Il pulsante **Allinea** consente di allineare un oggetto visivo selezionato al bordo (o al centro) dell'area di disegno del report, come illustrato nella figura seguente.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_6.png)

Quando si selezionano due o più oggetti visivi, questi vengono allineati tra loro usando il limite dell'allineamento esistente. Ad esempio, se si selezionano due oggetti visivi e si sceglie l'opzione **Allinea a sinistra**, gli oggetti visivi vengono allineati al limite più a sinistra di tutti gli oggetti visivi selezionati.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_7.png)

È anche possibile distribuire gli oggetti visivi in modo uniforme tra l'area di disegno del report, in orizzontale o verticale. Usare semplicemente il pulsante **Distribuisci** della barra multifunzione **Formato**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_8.png)

Selezionando alcuni di questi strumenti di linee griglia, allineamento e distribuzione, i report avranno esattamente l'aspetto desiderato.

