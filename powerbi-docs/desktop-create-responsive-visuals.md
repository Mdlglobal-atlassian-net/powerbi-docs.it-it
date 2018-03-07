---
title: Ottimizzare un oggetto visivo di Power BI per qualsiasi dimensione
description: Informazioni su come ottimizzare gli oggetti visivi in Power BI Desktop e nel servizio Power BI per le app per telefoni di Power BI.
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/13/2017
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 4c80048213b20365102bcb9c6842c342d8b9052b
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Ottimizzare un oggetto visivo di Power BI per qualsiasi dimensione
È possibile configurare gli oggetti visivi nel dashboard o nel report in modo che siano *reattivi*, ovvero in modo che vengano modificati dinamicamente per visualizzare la quantità massima di dati e informazioni dettagliate, indipendentemente dalle dimensioni dello schermo.

Quando le dimensioni di un oggetto visivo subiscono modifiche, Power BI classifica in ordine di priorità la visualizzazione dei dati, ad esempio rimuovendo la spaziatura interna e spostando automaticamente la legenda sopra l'oggetto visivo, in modo che l'oggetto visivo rimanga informativo anche con dimensioni ridotte. La reattività è particolarmente utile negli oggetti visivi nelle app per dispositivi mobili di Power BI nei telefoni.

![Ridimensionamento di oggetti visivi reattivi](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

È possibile attivare la reattività per qualsiasi oggetto visivo con assi X e Y e filtri dei dati.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Attivare la reattività in Power BI Desktop
1. In Power BI Desktop nella scheda **Visualizza** assicurarsi che sia attiva l'opzione **Layout desktop**.
   
    ![Icona Layout desktop](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Selezionare un oggetto visivo e nel riquadro **Visualizzazioni** selezionare la sezione **Formato**.
3. Espandere **Generale** > impostare **Reattivo** su **On**.
   
    ![Reattivo attivato](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Quando si [crea un report ottimizzato per il telefono](desktop-create-phone-report.md) e si aggiunge l'oggetto visivo, tale oggetto verrà ora ridimensionato correttamente.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Attivare la reattività nel servizio Power BI
È possibile attivare la reattività per un oggetto visivo in un report nel servizio Power BI. È necessario potere modificare il report.

1. In un report nel servizio Power BI ([https://powerbi.com](https://powerbi.com)) selezionare **Modifica report**.
2. Selezionare un oggetto visivo e nel riquadro **Visualizzazioni** selezionare la sezione **Formato**.
3. Espandere **Generale** > impostare **Reattivo** su **On**.
   
    ![Reattivo attivato](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Quando si [crea una visualizzazione telefono di un dashboard](service-create-dashboard-mobile-phone-view.md) e si aggiunge questo oggetto visivo, tale oggetto verrà ora ridimensionato correttamente.

## <a name="next-steps"></a>Passaggi successivi
* [Creare report ottimizzati per le app per telefoni di Power BI](desktop-create-phone-report.md)
* [Creare una visualizzazione telefono di un dashboard in Power BI](service-create-dashboard-mobile-phone-view.md)
* [Visualizzare i report di Power BI ottimizzati per il proprio telefono](mobile-apps-view-phone-report.md)
* Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

