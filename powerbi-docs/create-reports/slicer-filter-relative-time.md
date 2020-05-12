---
title: Usare un filtro dei dati o un filtro per intervalli temporali relativi in Power BI
description: Informazioni su come usare un filtro dei dati o un filtro per limitare intervalli temporali relativi in Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 4f0bfdbf3eb3856f872c872fbe0880ad39839e07
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867600"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Usare un filtro dei dati e un filtro per intervalli temporali relativi in Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Con la sempre maggiore diffusione di scenari che richiedono l'aggiornamento rapido, può risultare molto utile poter filtrare i dati in base a un intervallo temporale più ridotto. Con il filtro dei dati o il filtro per intervalli temporali relativi è possibile applicare filtri basati sul tempo a qualsiasi colonna di data/ora nel modello di dati. È ad esempio possibile usare il filtro dei dati per intervalli temporali per visualizzare solo le visualizzazioni video nell'ultimo minuto o nell'ultima ora. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Esempio di intervallo temporale relativo":::

Non è necessario usare questa funzionalità insieme alla funzionalità di [aggiornamento automatico della pagina](../desktop-automatic-page-refresh.md). Tuttavia, molti scenari correlati agli intervalli temporali relativi si abbinano perfettamente alla funzionalità di aggiornamento automatico della pagina.  

> [!NOTE]
> Quando si applica un filtro o un filtro dei dati per intervalli temporali relativi a livello di pagina o di report, tutti gli oggetti visivi presenti nella pagina o nel report vengono filtrati in base allo stesso intervallo temporale esatto, usando un *orario di riferimento* condiviso. Poiché gli oggetti visivi potrebbero avere orari di esecuzione leggermente diversi, questo orario di riferimento condiviso garantisce la sincronizzazione degli oggetti visivi nella pagina o nel report. In questo articolo sono disponibili altre informazioni sull'[orario di riferimento](#understanding-anchor-time).

## <a name="turn-on-relative-time-preview"></a>Attivare la funzionalità di anteprima degli intervalli temporali relativi

Il filtro per gli intervalli temporali relativi è in anteprima, quindi è necessario attivare l'opzione della funzionalità. Passare a **File** > **Opzioni e impostazioni** > **Opzioni**. In **Impostazioni globali** > **Funzionalità di anteprima** assicurarsi che **Filtro temporale relativo** sia selezionato.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="Impostare l'opzione di anteprima per il filtro temporale relativo":::

## <a name="create-a-relative-time-slicer-or-filter"></a>Creare un filtro dei dati o un filtro per intervalli temporali relativi

Dopo aver abilitato la funzionalità, è possibile trascinare e rilasciare il campo di data o ora nell'area dei campi di un filtro dei dati o nell'area di rilascio nel riquadro Filtri. 

### <a name="create-a-slicer"></a>Creare un filtro dei dati

1. Trascinare un campo di data o ora nel canvas.

2. Selezionare il tipo di visualizzazione **Filtro dei dati**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Creare un filtro dei dati temporali":::

### <a name="create-a-filter"></a>Creare un filtro
 
- Trascinare un campo di data o ora nel riquadro Filtri per **questo oggetto visivo**, **questa pagina** o **tutte le pagine**.

### <a name="set-relative-time"></a>Impostare l'intervallo di tempo relativo 

Impostare quindi il tipo di filtro su **Ora relativa**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Impostazione del filtro Ora relativa":::
 
Ecco come appare in un filtro dei dati:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Intervallo temporale relativo in un filtro dei dati":::

Ecco come appare in una scheda di filtro: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Intervallo temporale relativo in un filtro":::
 
Con questo nuovo tipo di filtro è possibile usare le opzioni **Ultimo**, **Successivo** o **Questo** per specificare il periodo di tempo per il filtro: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Scegliere Ultimo, Successivo o Questo per il periodo di tempo":::
 
È possibile specificare l'intervallo temporale usando un numero intero e un'unità di tempo: **Minuti** o **Ore**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Scegliere minuti o ore":::

Se è necessario risparmiare spazio nel canvas, è anche possibile creare il filtro per intervalli temporali relativi come scheda filtro nel riquadro Filtri.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Impostare l'intervallo temporale relativo in un filtro":::
 
## <a name="understanding-anchor-time"></a>Informazioni sull'orario di riferimento

Quando si applica un filtro a livello di pagina o di report, tutti gli oggetti visivi della pagina o del report vengono sincronizzati in base allo stesso intervallo temporale esatto. Queste query vengono tutte eseguite in relazione a un orario denominato *orario di riferimento*. L'orario di riferimento viene aggiornato automaticamente nei casi seguenti:

- Caricamento iniziale della pagina.
- Aggiornamento manuale.
- Aggiornamento della pagina automatico o aggiornamento della pagina per il rilevamento di modifiche.
- Modifica al modello.

### <a name="anchor-time-exceptions"></a>Eccezioni per l'orario di riferimento

- L'applicazione di filtri temporali relativi usando l'oggetto visivo Domande e risposte non avviene in relazione a questo orario di riferimento fino a quando non si converte l'oggetto visivo Domande e risposte in un oggetto visivo standard. Tuttavia, gli altri oggetti visivi di intelligenza artificiale, ad esempio i fattori di influenza chiave e l'albero di scomposizione, vengono sincronizzati rispetto all'orario di riferimento. 
- Inoltre, i filtri dei dati o i filtri per intervalli di data relativi non sono relativi all'orario di riferimento, se non in presenza di filtri per intervalli temporali relativi. Se la stessa pagina include sia un filtro per intervalli di data relativi che per intervalli temporali relativi, il filtro per intervalli di data relativi rispetta l'orario di riferimento.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Al filtro dei dati e al filtro per intervalli temporali relativi si applicano attualmente le limitazioni e le considerazioni seguenti.

- **Considerazioni sul fuso orario**: i modelli di dati in Power BI non includono informazioni sul fuso orario. Questi modelli possono archiviare informazioni sugli orari, ma non includono alcuna indicazione sul fuso orario specifico. Il filtro dei dati e il filtro si basano sempre sull'ora UTC. Se l'utente imposta un filtro in un report e lo invia a un collega in un altro fuso orario, l'utente e il collega visualizzano entrambi gli stessi dati. Se non si trovano nel fuso orario UTC, l'utente e il collega devono entrambi tenere conto della differenza di orario. Usare l'editor di query per convertire i dati acquisiti in un fuso orario locale nell'ora UTC.
- Questo nuovo tipo di filtro è supportato in Power BI Desktop, nel servizio Power BI, in Power BI Embedded e nelle app Power BI per dispositivi mobili. Tuttavia, esistono alcune limitazioni note per il supporto:

    - Non è supportato tramite l'API di incorporamento.
    - Non è supportato per la pubblicazione sul Web.

- **Memorizzazione di query nella cache**: viene usata la cache del client. Si supponga quindi di specificare come intervallo l'ultimo minuto, poi gli ultimi 5 minuti e infine di tornare all'ultimo minuto. A questo punto, vengono visualizzati gli stessi risultati della prima esecuzione, a meno che non si aggiorni la pagina o la pagina non venga aggiornata automaticamente.

## <a name="next-steps"></a>Passaggi successivi

- [Usare un filtro dei dati e un filtro per la data relativa in Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Filtri dei dati in Power BI](../visuals/power-bi-visualization-slicers.md)

