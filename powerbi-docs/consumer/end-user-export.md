---
title: Esportare dati da un oggetto visivo di Power BI
description: Esportare i dati da un oggetto visivo del report e dashboard visivo e visualizzarlo in Excel.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 4/9/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: d4384db8e05a69b138e76377e7c7b845867fa881
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61063857"
---
# <a name="export-data-from-visual"></a>Esportare i dati da visual
Se si desidera visualizzare i dati che viene usati per creare un oggetto visivo [è possibile visualizzare i dati in Power BI](end-user-show-data.md) o esportarli in Excel. L'opzione per esportare i dati richiede un determinato tipo o licenza e modificare le autorizzazioni per il contenuto. Se non è possibile esportare, rivolgersi all'amministratore di Power BI. 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Da un oggetto visivo in un dashboard di Power BI

1. Iniziare in un dashboard di Power BI. Qui usiamo i dashboard tramite il ***Marketing e vendita di esempio*** app. È possibile [scaricare questa app da AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282).

    ![](media/end-user-export/power-bi-dashboard.png)

2. Passare il mouse su un oggetto visivo per visualizzare i puntini di sospensione (...) e fare clic per visualizzare il menu azione.

    ![](media/end-user-export/power-bi-dashboard-export-visual.png)

3. Selezionare **Esporta in Excel**.

4. Ciò che accade dipende dal browser in uso. Potrebbe essere richiesto di salvare il file o maggio visualizzato un collegamento per il file esportato nella parte inferiore del browser. 

    ![](media/end-user-export/power-bi-export-browser.png)

5. Aprire il file di Excel.  

    ![](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>Da un oggetto visivo in un report
È possibile esportare dati da un oggetto visivo in un report come file con estensione xlsx (Excel) o con estensione csv formato. 

1. In un dashboard, selezionare un riquadro per aprire il report sottostante.  In questo esempio selezioniamo HyperV come lo stesso oggetto visivo precedente, *totale unità YTD Var %* . 

    ![](media/end-user-export/power-bi-export-report.png)

    Poiché questo riquadro è stato creato dal *esempio di vendite e Marketing* report, ovvero il report visualizzato. E si apre la pagina che contiene l'oggetto visivo riquadro selezionato. 

2. Selezionare il riquadro del report. Si noti che il **filtri** riquadro a destra. Questo oggetto visivo è stati applicati filtri. Per altre informazioni sui filtri, vedere [usare i filtri in un report](end-user-report-filter.md).

    ![](media/end-user-export/power-bi-export-filters.png)


3. Selezionare i puntini di sospensione nell'angolo in alto a destra della visualizzazione. Scegli **esportare i dati**.

    ![](media/end-user-export/power-bi-export-report2.png)

4. Verranno visualizzate opzioni per esportare i dati di riepilogo o di dati sottostante. Se si usa la *esempio di vendite e marketing* app **dei dati sottostanti** verrà disabilitata. Ma è possibile riscontrare i report in cui entrambe le opzioni sono abilitate. Di seguito è riportata una spiegazione della differenza.

    **I dati di riepilogo**: selezionare questa opzione se si desidera esportare i dati per ciò che viene visualizzato nell'oggetto visivo.  Questo tipo di esportazione Mostra solo i dati che è stati utilizzati per creare l'oggetto visivo. Se l'oggetto visivo è stati applicati filtri, verranno filtrati anche i dati esportati. Ad esempio, per questo oggetto visivo, l'esportazione includerà solo i dati per il 2014 e l'area centrale e solo i dati per quattro dei produttori: VanArsdel, Natura, Aliqui e Prirum.
  

    **I dati sottostanti**: selezionare questa opzione se si desidera esportare i dati per ciò che viene visualizzato nell'oggetto visivo **plus** dati aggiuntivi dal set di dati sottostante.  Questo può includere i dati contenuti nel set di dati ma non usati nell'oggetto visivo. 

    ![](media/end-user-export/power-bi-export-report3.png)

5. Ciò che accade dipende dal browser in uso. Potrebbe essere richiesto di salvare il file o maggio visualizzato un collegamento per il file esportato nella parte inferiore del browser. 

    ![](media/end-user-export/power-bi-export-edge.png)


7. Aprire il file di Excel. Confrontare la quantità di dati esportati i dati che sono esportati dall'oggetto visivo nel dashboard stesso. La differenza è che questa esportazione include **dei dati sottostanti**. 

    ![](media/end-user-export/power-bi-underlying.png)

