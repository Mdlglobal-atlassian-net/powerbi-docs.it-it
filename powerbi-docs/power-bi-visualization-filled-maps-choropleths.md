---
title: Mappe colorate (Choropleth) in Power BI (esercitazione)
description: Documentazione - esercitazione sulla creazione di mappe colorate (Choropleth) in Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/19/2018
ms.author: mihart
ms.openlocfilehash: 2c15cf503a7c66a3b89e45cc338ee5174e5f24e7
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="filled-maps-choropleths-in-power-bi-tutorial"></a>Mappe colorate (choropleth) in Power BI (esercitazione)
Nelle mappe colorate vengono usate ombreggiature, tinte o motivi per visualizzare proporzionalmente le differenze relative a un valore in un'area geografica.  In questo modo è possibile visualizzare queste differenze relative con ombreggiature chiare (frequenza o valore minore) e scure (frequenza o valore maggiore).    

![](media/power-bi-visualization-filled-maps-choropleths/large_map.png)

## <a name="what-is-sent-to-bing"></a>Cosa viene inviato a Bing
Power BI si integra con Bing per fornire coordinate della mappa predefinite (un processo denominato geocodifica). Quando si crea una visualizzazione mappa nel servizio Power BI o Power BI Desktop, i dati contenuti nei bucket **Posizione**, **Latitudine** e **Longitudine** (usati per creare tale visualizzazione) vengono inviati a Bing.

L'utente, o l'amministratore, potrebbe dover aggiornare il firewall per consentire l'accesso agli URL usati da Bing per la geocodifica.  Questi URL sono:
* https://dev.virtualearth.net/REST/V1/Locations
* https://platform.bing.com/geo/spatial/v1/public/Geodata
* https://www.bing.com/api/maps/mapcontrol

Per altre informazioni sui dati inviati a Bing e per suggerimenti su come migliorare i risultati della geocodifica, vedere [Suggerimenti e consigli per le visualizzazioni mappa](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Quando usare una mappa colorata
Le mappe colorate sono ideali nelle circostanze seguenti:

* per visualizzare informazioni quantitative su una mappa
* per mostrare motivi e relazioni spaziali
* quando i dati sono standardizzati
* quando si usano dati socioeconomici
* quando le aree geografiche definite sono importanti
* per ottenere una panoramica della distribuzione nelle varie località geografiche

## <a name="create-a-basic-filled-map"></a>Creare una mappa colorata di base
Il video seguente mostra come creare una mappa di base e convertirla in una mappa colorata.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>


1. Per creare una mappa colorata personalizzata, [scaricare l'esempio di analisi delle vendite e marketing](sample-datasets.md) accedendo a Power BI e selezionando **Recupera dati \> Esempi \> Vendite e marketing \> Connetti**.
2. Quando viene visualizzato il messaggio di completamento dell'operazione, fare clic su **Visualizza set di dati**. 
   
   ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-view-dataset.png)
3. Power BI apre un'area di disegno report vuota nella [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md).
   
    ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-blank-canvas.png)
4. Nel riquadro Campi selezionare il campo **Geo** \> **State**.    
   
   ![](media/power-bi-visualization-filled-maps-choropleths/img002.png)
5. [Convertire il grafico](power-bi-report-change-visualization-type.md) in una mappa colorata. Si noti che **State** ora è presente nell'area **Location**. Bing Mappe usa il campo nell'area **Location** per creare la mappa.  La posizione può essere una qualsiasi tra quelle valide, ad esempio paesi, stati, province, CAP o altri codici postali. Bing Mappe fornisce le forme di mappa colorata per le varie posizioni a livello mondiale. Se non è presente una voce valida nell'area Località, Power BI non può creare la mappa colorata.  
   
   ![](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Filtrare la mappa in modo da visualizzare solo gli Stati Uniti continentali.
   
   a.  Nella parte inferiore del riquadro Visualizzazioni cercare l'area **Filtri** .
   
   b.  Passare il puntatore su **State** e fare clic sulla freccia di espansione.  
   ![](media/power-bi-visualization-filled-maps-choropleths/img004.png)
   
   c.  Porre un segno di spunta accanto a **All** e rimuovere quello accanto a **AK**.
   
   ![](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. Selezionare **SalesFact** \> **Sentiment** per aggiungerlo all'area **Saturazione colore**. Il campo nell'area **Saturazione colore** controlla l'ombreggiatura della mappa.  
   ![](media/power-bi-visualization-filled-maps-choropleths/power-bi-color-saturation.png)
8. L'ombreggiatura applicata alla mappa colorata delle valutazioni è di colore verde, in cui il verde chiaro rappresenta valori inferiori e il verde scuro valori superiori corrispondenti a una valutazione più positiva.  Nella figura seguente è evidenziato lo stato del Wyoming (WY) in cui il valore del sentiment è particolarmente alto (74).  
   ![](media/power-bi-visualization-filled-maps-choropleths/img007.png)
9. [Salvare il report](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Evidenziazione e filtro incrociato
Per informazioni sull'uso del riquadro Filtri, vedere [Aggiungere un filtro a un report](power-bi-report-add-filter.md).

Evidenziando una località in una mappa colorata viene applicato il filtro incrociato nelle altre visualizzazioni nella pagina del report e viceversa. 

Per seguire la procedura, copiare e incollare la mappa colorata nella pagina **Sentiment** del report *Sales and Marketing*. 

1. Selezionare uno stato nella mappa colorata.  per evidenziare le altre visualizzazioni nella pagina. Se, ad esempio, si seleziona **Texas**, è possibile notare che il valore Sentiment è 74, che il Texas si trova nel distretto centrale \#23 e che la maggior parte delle vendite viene effettuata nei settori Moderation e Convenience.   
   ![](media/power-bi-visualization-filled-maps-choropleths/img008.png)
2. Nel grafico a linee passare da **No** a **Sì** e viceversa. per filtrare la mappa colorata in modo da visualizzare il sentiment per VanArsdel e per la concorrenza di VanArsdel.  
   ![](media/power-bi-visualization-filled-maps-choropleths/img009.gif)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
I dati delle mappe possono essere ambigui.  Ad esempio, Washington può corrispondere sia a un nome di città che di stato. I dati geografici sono probabilmente archiviati in colonne distinte, una per i nomi di città e una per i nomi di stati o province, di conseguenza Bing potrebbe non essere in grado di indicare a cosa si riferisce il nome Washington. Se il set di dati contiene già i dati relativi a latitudine e longitudine, Power BI include speciali campi per ovviare alle ambiguità dei dati delle mappe. È sufficiente trascinare il campo che contiene i dati relativi alla latitudine nell'area Visualizzazioni \> Latitudine e fare  altrettanto per i dati relativi alla longitudine.  
![](media/power-bi-visualization-filled-maps-choropleths/pbi_latitude.png) 

Se si dispone delle autorizzazioni per modificare il set di dati in Power BI Desktop, guardare questo video per informazioni su come risolvere le ambiguità della mappa.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Se i dati relativi a latitudine e longitudine non sono disponibili, [seguire queste istruzioni per aggiornare il set di dati](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Per ulteriori informazioni sulle visualizzazioni mappa, vedere [Suggerimenti e consigli per le visualizzazioni mappa](power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Passaggi successivi
[Aggiungere la mappa colorata come riquadro del dashboard (aggiungendo l'oggetto visivo)](service-dashboard-tiles.md)    
 [Aggiungere una visualizzazione a un report](power-bi-report-add-visualizations-i.md)  
 [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)    
 [Modificare il tipo di visualizzazione in uso](power-bi-report-change-visualization-type.md)      
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

