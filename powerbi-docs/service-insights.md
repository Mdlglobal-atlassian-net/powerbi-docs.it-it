---
title: Ottenere Informazioni rapide in Power BI
description: Documentazione relativa all'esecuzione e all'uso di Informazioni rapide con il servizio Power BI.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: et_MLSL2sA8
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/01/2017
ms.author: mihart
ms.openlocfilehash: 8b069f29737992817d20396007864cc8c005ca99
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="quick-insights-with-power-bi"></a>Informazioni rapide con Power BI
Si ha un nuovo set di dati e non si sa da dove iniziare?  È necessario creare velocemente un dashboard?  Si vuole cercare rapidamente gli approfondimenti persi?

Eseguire Informazioni rapide per generare visualizzazioni interattive interessanti basate sui dati. Informazioni rapide può essere eseguito in un intero set di dati (Informazioni rapide) o in un riquadro del dashboard specifico (Informazioni rapide con ambito). È anche possibile eseguire Informazioni rapide per un'informazione dettagliata.

> **NOTA**: Informazioni rapide non funziona con DirectQuery, ma solo con i dati caricati in Power BI.
> 
> 

La funzionalità Quick Insights si basa su un [set di algoritmi analitici avanzati](service-insight-types.md) sviluppati in collaborazione con Microsoft Research per consentire a più utenti di trovare informazioni dettagliate nei loro dati in modi nuovi e intuitivi.

## <a name="run-quick-insights-on-a-dataset"></a>Eseguire Informazioni rapide in un set di dati
Il video seguente illustra come eseguire Informazioni rapide su un set di dati, aprire un'informazione in modalità messa a fuoco, aggiungere una di queste informazioni rapide come riquadro nel dashboard e ottenere informazioni rapide per un oggetto visivo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Passare ora all'azione. Esplorare Informazioni rapide usando l'[esempio di analisi della qualità dei fornitori](sample-supplier-quality.md).

1. Nella scheda **Set di dati** fare clic sui puntini di sospensione (...) e scegliere **Ottieni informazioni dettagliate**.
   
    ![](media/service-insights/power-bi-ellipses.png)
   
    ![](media/service-insights/power-bi-tab.png)
2. Power BI usa [vari algoritmi](service-insight-types.md) per cercare le tendenze nel set di dati.
   
    ![](media/service-insights/pbi_autoinsightssearching.png)
3. Entro pochi secondi, le informazioni sono pronte.  Selezionare **Visualizza approfondimenti** per visualizzare le visualizzazioni.
   
    ![](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **NOTA**: alcuni set di dati non possono generare informazioni rapide perché i dati non sono statisticamente significativi.  Per altre informazioni, vedere [Ottimizzare i dati per Informazioni rapide](service-insights-optimize.md).
   > 
   > 
4. Le visualizzazioni appaiono in un apposito canvas di **Informazioni rapide** con un massimo di 32 schede separate di informazioni. Ogni scheda contiene un grafico o un grafico con una breve descrizione.
   
    ![](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-quick-insight-cards"></a>Interagire con le schede di Informazioni rapide
  ![](media/service-insights/pbi_hover.png)

1. Passare il puntatore del mouse su una scheda e selezionare l'icona a forma di puntina per aggiungere la visualizzazione a un dashboard.
2. Passare il mouse su una scheda e selezionare l'icona della modalità messa a fuoco per visualizzare la scheda a schermo intero.
   
    ![](media/service-insights/power-bi-insight-focus.png)
3. In questa modalità è possibile:
   
   * [Filtrare](service-interact-with-a-report-in-reading-view.md) le visualizzazioni.  Per visualizzare i filtri, nell'angolo in alto a destra selezionare la freccia per espandere il riquadro Filtri.
     
        ![](media/service-insights/power-bi-insights-filter-new.png)
   * Per aggiungere la scheda delle informazioni dettagliate a un dashboard, selezionare l'icona di aggiunta ![](media/service-insights/power-bi-pin-icon.png) o **Aggiungi oggetto visivo**.
   * Eseguire Informazioni rapide nella scheda stessa. Questa modalità d'uso è nota anche come **Informazioni rapide con ambito**. Nell'angolo superiore destro selezionare l'icona a forma di lampadina ![](media/service-insights/power-bi-bulb-icon.png) oppure **Ottieni informazioni dettagliate**.
     
       ![](media/service-insights/pbi-autoinsights-tile.png)
     
     L'informazione rapida viene visualizzata a sinistra, mentre le nuove schede, basate esclusivamente sui dati presenti in quell'informazione, vengono visualizzate a destra.
     
       ![](media/service-insights/power-bi-insights-on-insights-new.png)
4. Per tornare all'area di disegno originale di Informazioni rapide, nell'angolo superiore sinistro selezionare **Esci dalla modalità messa a fuoco**.

## <a name="run-quick-insights-on-a-dashboard-tile"></a>Eseguire Informazioni rapide in un riquadro del dashboard
Invece di cercare informazioni dettagliate in un intero set di dati, è possibile limitare la ricerca ai dati usati per creare un singolo riquadro del dashboard. Questa modalità d'uso è nota anche come **Informazioni rapide con ambito**.

1. Aprire un dashboard.
2. Selezionare un riquadro e [aprire il riquadro nella modalità messa a fuoco](service-focus-mode.md).
3. Nell'angolo in alto a destra selezionare **Ottieni informazioni dettagliate**.
   
    ![](media/service-insights/pbi-autoinsights-tile.png)
4. Power BI visualizza le schede di informazioni dettagliate sul lato destro del riquadro.
   
    ![](media/service-insights/pbi-insights-tile.png)
5. Se un approfondimento attira l'interesse, selezionare la scheda di informazioni dettagliate per un approfondimento. L'informazione rapida selezionata viene visualizzata a sinistra, mentre le nuove schede di informazioni, basate esclusivamente sui dati presenti in quell'informazione rapida, vengono visualizzate a destra.
6. Continuare l'approfondimento dei dati e quando si trova un'informazione rapida interessante, aggiungere il relativo oggetto visivo al dashboard selezionando **Aggiungi oggetto visivo** nell'angolo superiore destro. È anche possibile inviare un commento per informare il proprietario del set di dati se una particolare informazione rapida è stata utile o meno.
   
    ![](media/service-insights/useful.png)

## <a name="next-steps"></a>Passaggi successivi
Se è disponibile un set di dati, [ottimizzarlo per Informazioni rapide](service-insights-optimize.md).

Altre informazioni sui [tipi di informazioni rapide disponibili](service-insight-types.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

