---
title: Eseguire e visualizzare informazioni dettagliate per i riquadri del dashboard
description: Informazioni per gli utenti finali di Power BI su come ottenere informazioni dettagliate sui riquadri del dashboard.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: fcfb16de53b4e6c67b7c46fec87ab614d07cb9b1
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "61049233"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Visualizzare informazioni dettagliate sui dati per i riquadri del dashboard con Power BI
Ogni riquadro di visualizzazione nel dashboard è una porta di accesso per l'esplorazione dei dati. Quando si seleziona un riquadro, viene aperto un report in cui è possibile filtrare e ordinare e approfondire il set di dati del report. E quando si eseguono informazioni dettagliate, Power BI esegue automaticamente l'esplorazione dei dati.

Eseguire Informazioni rapide per generare visualizzazioni interattive interessanti basate sui dati. Le informazioni rapide possono essere eseguite su un riquadro del dashboard specifico ed è anche possibile eseguire informazioni dettagliate su altre informazioni dettagliate.

La funzionalità Informazioni dettagliate si basa su un [set di algoritmi analitici avanzati](end-user-insight-types.md) sviluppati in collaborazione con Microsoft Research per consentire a più utenti di trovare informazioni dettagliate nei propri dati in modi nuovi e intuitivi.

## <a name="run-insights-on-a-dashboard-tile"></a>Eseguire informazioni dettagliate su un riquadro del dashboard
Quando si eseguono informazioni dettagliate su un riquadro del dashboard, Power BI cerca solo i dati usati per creare tale riquadro specifico. 

1. [Aprire un dashboard](end-user-dashboards.md).
2. Passare il mouse su un riquadro. Selezionare i puntini di sospensione (...) e scegliere **Visualizza informazioni dettagliate**. 

    ![Menu puntini di sospensione](./media/end-user-insights/power-bi-hover.png)


3. Il riquadro verrà aperto in [modalità messa a fuoco](end-user-focus.md) con le schede delle informazioni dettagliate visualizzate sul lato destro.    
   
    ![Modalità messa a fuoco](./media/end-user-insights/pbi-insights-tile.png)    
4. Se un approfondimento attira l'interesse, selezionare la scheda di informazioni dettagliate per un approfondimento. Le informazioni dettagliate selezionate vengono visualizzate a sinistra, mentre le nuove schede di informazioni, basate esclusivamente sui dati presenti in tali informazioni dettagliate specifiche, vengono visualizzate a destra.    

 ## <a name="interact-with-the-insight-cards"></a>Interagire con le schede di informazioni dettagliate
Dopo aver aperto le informazioni dettagliate, continuare l'esplorazione.

   * Filtrare l'oggetto visivo nell'area di disegno.  Per visualizzare i filtri, nell'angolo in alto a destra selezionare la freccia per espandere il riquadro Filtri.

     ![Informazioni dettagliate e menu Filtri espanso](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * Eseguire informazioni dettagliate sulla scheda delle informazioni dettagliate stessa. Questa modalità d'uso è nota anche come **informazioni dettagliate correlate**. Nell'angolo superiore destro selezionare l'icona a forma di lampadina ![Icona Ottieni informazioni dettagliate](./media/end-user-insights/power-bi-bulb-icon.png) oppure **Ottieni informazioni dettagliate**.
     
     ![Barra dei menu con l'icona Ottieni informazioni dettagliate](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     Le informazioni dettagliate vengono visualizzate a sinistra, mentre le nuove schede, basate esclusivamente sui dati presenti in tali informazioni dettagliate specifiche, vengono visualizzate a destra.
     
     ![Informazioni dettagliate in informazioni dettagliate](./media/end-user-insights/power-bi-insights-on-insights-new.png)

Per tornare all'area di disegno originale delle informazioni dettagliate, nell'angolo superiore sinistro selezionare **Esci dalla modalità messa a fuoco**.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
- **Visualizza informazioni dettagliate** non funziona con DirectQuery, ma solo con i dati caricati in Power BI.
- **Visualizza informazioni dettagliate** non funziona con tutti i tipi di riquadri del dashboard. Non è ad esempio disponibile per gli oggetti visivi personalizzati.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sui [tipi di informazioni rapide disponibili](end-user-insight-types.md)

