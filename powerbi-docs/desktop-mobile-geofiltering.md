---
title: Impostare filtri geografici in Power BI Desktop per le app per dispositivi mobili
description: "Quando si imposta un filtro geografico nel modello in Power BI Desktop, è possibile filtrare automaticamente i dati per la località specifica nelle app per dispositivi mobili di Power BI."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 07/18/2017
ms.author: maggies
ms.openlocfilehash: ac03f3e97c2e2cef7d4f083e5b835aa4c87de633
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Impostare filtri geografici in Power BI Desktop per le app per dispositivi mobili
In Power BI Desktop è possibile [classificare i dati geografici](desktop-data-categorization.md) per una colonna, in modo che Power BI Desktop sappia come gestire i valori negli oggetti visivi in un report. Un vantaggio aggiuntivo è costituito dal fatto che quando l'utente o un collega visualizza il report nell'app per dispositivi mobili di Power BI, Power BI fornisce automaticamente i filtri geografici corrispondenti alla posizione dell'utente. 

Si supponga ad esempio di essere un responsabile vendite in trasferta per incontrare clienti e si supponga di voler filtrare rapidamente il totale di vendite e ricavi per il cliente specifico che si intende incontrare. Si vogliono suddividere i dati per la località corrente, in base a stato, città o indirizzo effettivo. In seguito, se il tempo è sufficiente, si vogliono incontrare altri clienti nelle vicinanze. È possibile [filtrare il report in base alla località per trovare i clienti](mobile-apps-geographic-filtering.md).

> [!NOTE]
> È possibile filtrare in base alla località nell'app per dispositivi mobili solo se i nomi geografici del report sono in inglese, ad esempio "New York City" o "Germany".
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Identificare i dati geografici nel report
1. In Power BI Desktop passare alla visualizzazione dati ![icona Visualizzazione dati](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Selezionare una colonna con dati geografici, ad esempio una colonna City.
   
    ![colonna City](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. Nella scheda **Creazione di modelli** selezionare **Categoria di dati**, quindi scegliere la categoria corretta, ovvero in questo esempio **City**.
   
    ![casella Categoria di dati](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Continuare a impostare le categorie di dati geografiche per altri campi nel modello. 
   
   > [!NOTE]
   > È possibile impostare più colonne per ogni categoria di dati in un modello, ma in questo caso il modello non potrà applicare il filtro geografico nell'app Power BI per dispositivi mobili. Per usare il filtro geografico nelle app per dispositivi mobili, impostare solo una colonna per ogni categoria di dati, ovvero ad esempio solo una colonna **City**, una colonna **State or Province** e una colonna **Country**. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Creare oggetti visivi con i dati geografici
1. Passare alla visualizzazione report ![icona Visualizzazione report](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png)e creare oggetti visivi che usano i campi dei dati geografici. 
   
    ![Report con mappa](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    In questo esempio, il modello contiene anche una colonna calcolata che combina città e stato in un'unica colonna. Altre informazioni su come [creare colonne calcolate in Power BI Desktop](desktop-calculated-columns.md).
   
    ![campo Città + Stato](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Pubblicare il report nel servizio Power BI.

## <a name="view-the-report-in-power-bi-mobile-app"></a>Visualizzare il report nell'app Power BI per dispositivi mobili
1. Aprire il report in una qualsiasi [app Power BI per dispositivi mobili](mobile-apps-for-mobile-devices.md).
2. Se ci si trova in una località geografica con dati nel report, è ora possibile filtrarlo automaticamente in modo da visualizzare la propria località.
   
    ![Filtro geografico nell'app per dispositivi mobili](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

Altre informazioni su come [filtrare un report per località nelle app Power BI per dispositivi mobili](mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>Passaggi successivi
* [Categorizzazione dei dati in Power BI Desktop](desktop-data-categorization.md)  
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

