---
title: Generare automaticamente informazioni dettagliate sui dati con Power BI
description: Informazioni su come ottenere informazioni dettagliate su riquadri del dashboard e set di dati.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/25/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 3b58b0b88ed0417f88784824a67ab294dda7343e
ms.sourcegitcommit: a186679e8dae85dce23f6365bf5c36d7f407f15b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51850431"
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Generare automaticamente informazioni dettagliate sui dati con Power BI
Si ha un nuovo set di dati e non si sa da dove iniziare?  È necessario creare velocemente un dashboard?  Si desidera cercare le informazioni dettagliate perse?

Eseguire Informazioni rapide per generare visualizzazioni interattive interessanti basate sui dati. La funzionalità Informazioni rapide può essere eseguita su un intero set di dati (Informazioni rapide) o in un riquadro del dashboard specifico (Informazioni rapide con ambito). È anche possibile generare informazioni dettagliate su un'informazione dettagliata.

> [!NOTE]
> Informazioni dettagliate non funziona con DirectQuery, ma solo con i dati caricati in Power BI.
> 

La funzionalità Informazioni dettagliate si basa su un [set di algoritmi analitici avanzati](service-insight-types.md) sviluppati in collaborazione con Microsoft Research per consentire a più utenti di trovare informazioni dettagliate nei propri dati in modi nuovi e intuitivi.

## <a name="run-quick-insights-on-a-dataset"></a>Eseguire Informazioni rapide su un set di dati
Il video seguente illustra come eseguire Informazioni rapide su un set di dati, aprire un'informazione dettagliata nella modalità messa a fuoco, aggiungere un'informazione dettagliata come riquadro al dashboard e quindi ottenere informazioni dettagliate per un riquadro del dashboard.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Passare ora all'azione. Esplorare le informazioni dettagliate usando l'[esempio di analisi della qualità dei fornitori](sample-supplier-quality.md).

1. Nella scheda **Set di dati** fare clic sui puntini di sospensione (...) e scegliere **Ottieni informazioni dettagliate**.
   
    ![Scheda Set di dati](media/service-insights/power-bi-ellipses.png)
   
    ![Menu di puntini di sospensione](media/service-insights/power-bi-tab.png)
2. Power BI usa [vari algoritmi](service-insight-types.md) per cercare le tendenze nel set di dati.
   
    ![Finestra di dialogo Ricerca di informazioni dettagliate](media/service-insights/pbi_autoinsightssearching.png)
3. Entro pochi secondi, le informazioni sono pronte.  Selezionare **Visualizza informazioni dettagliate** per vedere le visualizzazioni.
   
    ![Messaggio di operazione completata](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > Alcuni set di dati non possono a generare informazioni dettagliate perché i dati non sono significativi dal punto di vista statistico.  Per altre informazioni, vedere [Ottimizzare i dati per Informazioni rapide](service-insights-optimize.md).
   > 
    
1. Le visualizzazioni appaiono in un apposito canvas di **Informazioni rapide** con un massimo di 32 schede separate di informazioni. Ogni scheda contiene un grafico o un grafico con una breve descrizione.
   
    ![Area di disegno Informazioni rapide](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interagire con le schede di informazioni dettagliate
  ![Icona Aggiungi](media/service-insights/pbi_hover.png)

1. Passare il puntatore del mouse su una scheda e selezionare l'icona a forma di puntina per aggiungere la visualizzazione a un dashboard.
2. Passare il puntatore del mouse su una scheda, selezionare i puntini di sospensione (...) e scegliere **Visualizza informazioni dettagliate**. Le informazioni dettagliate verranno aperte a schermo intero.
   
    ![Informazioni dettagliate a schermo intero](media/service-insights/power-bi-insight-focus.png)
3. In questa modalità è possibile:
   
   * Filtrare le visualizzazioni.  Per visualizzare i filtri, nell'angolo in alto a destra selezionare la freccia per espandere il riquadro Filtri.
        ![Informazioni dettagliate e menu Filtri espanso](media/service-insights/power-bi-insights-filter-new.png)
   * Per aggiungere la scheda delle informazioni dettagliate a un dashboard, selezionare l'icona di aggiunta ![Icona di aggiunta](media/service-insights/power-bi-pin-icon.png) o **Aggiungi oggetto visivo**.
   * Eseguire le informazioni dettagliate nella scheda stessa. Questa modalità d'uso è nota anche come **informazioni dettagliate con ambito**. Nell'angolo superiore destro selezionare l'icona a forma di lampadina ![Icona Ottieni informazioni dettagliate](media/service-insights/power-bi-bulb-icon.png) oppure **Ottieni informazioni dettagliate**.
     
       ![Barra dei menu con l'icona Ottieni informazioni dettagliate](media/service-insights/pbi-autoinsights-tile.png)
     
     Le informazioni dettagliate vengono visualizzate a sinistra, mentre le nuove schede, basate esclusivamente sui dati presenti in tali informazioni dettagliate specifiche, vengono visualizzate a destra.
     
       ![Informazioni dettagliate in informazioni dettagliate](media/service-insights/power-bi-insights-on-insights-new.png)
4. Per tornare all'area di disegno originale delle informazioni dettagliate, nell'angolo superiore sinistro selezionare **Esci dalla modalità messa a fuoco**.

## <a name="run-insights-on-a-dashboard-tile"></a>Eseguire informazioni dettagliate su un riquadro del dashboard
Invece di cercare informazioni dettagliate in un intero set di dati, è possibile limitare la ricerca ai dati usati per creare un singolo riquadro del dashboard. Anche questa modalità d'uso è nota come **informazioni dettagliate con ambito**.

1. Aprire un dashboard.
2. Passare il mouse su un riquadro. Selezionare i puntini di sospensione (...) e scegliere **Visualizza informazioni dettagliate**. Il riquadro verrà aperto in [modalità messa a fuoco](service-focus-mode.md) con le schede delle informazioni dettagliate visualizzate sul lato destro.    
   
    ![Modalità messa a fuoco](media/service-insights/pbi-insights-tile.png)    
4. Se un approfondimento attira l'interesse, selezionare la scheda di informazioni dettagliate per un approfondimento. Le informazioni dettagliate selezionate vengono visualizzate a sinistra, mentre le nuove schede di informazioni, basate esclusivamente sui dati presenti in tali informazioni dettagliate specifiche, vengono visualizzate a destra.    
6. Continuare a esaminare i dati e quando si osserva un'informazione dettagliata interessante, aggiungerla al dashboard selezionando **Aggiungi oggetto visivo** nell'angolo superiore destro.

## <a name="next-steps"></a>Passaggi successivi
Se è disponibile un set di dati, [ottimizzarlo per Informazioni rapide](service-insights-optimize.md).

Altre informazioni sui [tipi di informazioni rapide disponibili](service-insight-types.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

