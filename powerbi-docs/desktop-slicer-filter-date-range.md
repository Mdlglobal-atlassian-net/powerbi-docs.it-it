---
title: Usare un filtro dei dati o un filtro per la data relativa in Power BI Desktop
description: Informazioni su come usare un filtro dei dati o un filtro per limitare intervalli di date relative in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1d074cbd61373bf53e22ecc60c0c1389c0b94881
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi-desktop"></a>Usare un filtro dei dati e un filtro per la data relativa in Power BI Desktop
Con il **filtro dei dati per la data relativa** o il **filtro per la data relativa** è possibile applicare filtri basati sulla data a qualsiasi colonna di date nel modello di dati. È ad esempio possibile usare il **filtro dei dati per la data relativa** per visualizzare solo i dati relativi a vendite effettuate negli ultimi trenta giorni (nell'ultimo mese o negli ultimi mesi di calendario e così via). Quando si aggiornano i dati, il periodo di tempo relativo applica automaticamente il vincolo appropriato per la data relativa.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_01.png)

## <a name="using-the-relative-date-range-slicer"></a>Uso del filtro dei dati per la data relativa
È possibile usare il filtro dei dati per la data relativa come qualsiasi altro filtro dei dati. È sufficiente creare un oggetto visivo **filtro dei dati** per il report e quindi selezionare un valore di data per il valore **Campo**. Nell'immagine seguente è selezionato il campo *OrderDate*.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_02.png)

Selezionare la freccia in giù nell'angolo in alto a destra del **filtro dei dati per la data relativa** per visualizzare un menu.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_03.png)

Per il filtro dei dati per la data relativa selezionare *Relativa*.

È quindi possibile selezionare le impostazioni. Per il primo elenco a discesa nel *filtro dei dati per la data relativa* sono disponibili le opzioni seguenti:

* Ultima
* Argomento successivo
* Questa

Queste selezioni sono mostrate nell'immagine seguente.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_04.png)

L'impostazione successiva (in mezzo) nel *filtro dei dati per la data relativa* consente di immettere un numero per definire l'intervallo di date relative.

La terza impostazione consente di selezionare l'unità di misura relativa alla data. Sono disponibili le opzioni seguenti:

* Giorni
* Settimane
* Settimane (calendario)
* Mesi
* Mesi (calendario)
* Anni
* Anni (calendario)

Queste selezioni sono mostrate nell'immagine seguente.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_05.png)

Se nell'elenco si seleziona *Mesi* e si immette 2 nell'impostazione in mezzo, si ottiene il risultato seguente: se oggi è il 20 luglio, i dati inclusi negli oggetti visivi vincolati dal filtro dei dati mostrano i dati per i due mesi precedenti, a partire dal 20 maggio e fino al 20 luglio (data odierna).

Se invece si seleziona *Mesi (calendario)*, gli oggetti visivi vincolati mostrano i dati a partire dall'1 maggio fino al 30 giugno, ovvero gli ultimi due mesi di calendario completi.

## <a name="using-the-relative-date-range-filter"></a>Uso del filtro intervalli per la data relativa
È anche possibile creare un filtro intervalli per la data relativa per la pagina del report o per l'intero report. A tale scopo, è sufficiente trascinare un campo relativo alla data nell'area **Filtri a livello di pagina** o nell'area **Filtri a livello di report** del riquadro **Campo**, come mostrato nell'immagine seguente.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_06.png)

È quindi possibile modificare l'intervallo di date relative in modo simile a come si personalizza il **filtro dei dati per la data relativa**. Selezionare **Filtro per data relativa** dall'elenco a discesa **Tipo di filtro**.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_07.png)

Dopo la selezione di **Filtro per data relativa**, vengono visualizzate tre sezioni da modificare, inclusa una casella numerica intermedia, in modo analogo al filtro dei dati.

![](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter_08.png)

Queste sono tutte le operazioni necessarie per usare i vincoli per la data relativa nei report.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Le limitazioni e le considerazioni seguenti sono attualmente applicabili al **filtro intervalli per la data relativa** e al filtro.

* I modelli di dati in **Power BI** non includono informazioni sul fuso orario. Questi modelli possono archiviare informazioni sugli orari, ma non includono alcuna indicazione sul fuso orario specifico.
* Il filtro dei dati e il filtro sono sempre basati sull'ora UTC, quindi se si configura un filtro in un report e lo si invia a un collega in un fuso orario diverso verranno visualizzati per entrambi gli stessi dati. Se tuttavia l'utente non si trova nel fuso orario UTC, è possibile che vengano visualizzati dati relativi a una differenza di orario diversa dal previsto.
* I dati acquisiti in un fuso orario locale possono essere convertiti in UTC tramite l'**Editor di query**.

