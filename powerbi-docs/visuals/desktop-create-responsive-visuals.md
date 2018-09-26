---
title: Ottimizzare un oggetto visivo di Power BI per qualsiasi dimensione
description: Informazioni su come ottimizzare gli oggetti visivi nei report esistenti in Power BI Desktop e nel servizio Power BI per le app per telefono di Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 1260f2c69a4ab913f7451671ab7821ee250998c0
ms.sourcegitcommit: fb1885da7cf11367660edbf7b7346dc039ee9b5d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47187238"
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Ottimizzare un oggetto visivo di Power BI per qualsiasi dimensione
Per impostazione predefinita, quando si crea un nuovo report, gli oggetti visivi sono *reattivi*, ovvero cambiano dinamicamente in modo da visualizzare la quantità massima di dati e informazioni dettagliate, indipendentemente dalle dimensioni dello schermo. Anche per i report meno recenti è possibile impostare gli oggetti visivi in modo che vengano ridimensionati in modo dinamico.

Quando le dimensioni di un oggetto visivo subiscono modifiche, Power BI classifica in ordine di priorità la visualizzazione dei dati, ad esempio rimuovendo la spaziatura interna e spostando automaticamente la legenda sopra l'oggetto visivo, in modo che l'oggetto visivo rimanga informativo anche con dimensioni ridotte. La reattività è particolarmente utile negli oggetti visivi nelle app per dispositivi mobili di Power BI nei telefoni.

![Ridimensionamento di oggetti visivi reattivi](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Qualsiasi oggetto visivo con assi X e Y e filtri dei dati può essere ridimensionato in modo reattivo.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Attivare la reattività in Power BI Desktop
1. In Power BI Desktop, in un report meno recente, verificare che nella scheda **Visualizza** sia attiva l'opzione **Layout desktop**.
   
    ![Icona Layout desktop](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Selezionare un oggetto visivo e nel riquadro **Visualizzazioni** selezionare la sezione **Formato**.
3. Espandere **Generale** > impostare **Reattivo** su **On**.
   
    ![Reattivo attivato](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Quando si [crea un report ottimizzato per il telefono](../desktop-create-phone-report.md) e si aggiunge l'oggetto visivo, tale oggetto verrà ora ridimensionato correttamente.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Attivare la reattività nel servizio Power BI
È possibile attivare la reattività per un oggetto visivo in un report meno recente nel servizio Power BI. È necessario potere modificare il report.

1. In un report nel servizio Power BI ([https://powerbi.com](https://powerbi.com)) selezionare **Modifica report**.
2. Selezionare un oggetto visivo e nel riquadro **Visualizzazioni** selezionare la sezione **Formato**.
3. Espandere **Generale** > impostare **Reattivo** su **On**.
   
    ![Reattivo attivato](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Quando si [crea una visualizzazione telefono del report](../desktop-create-phone-report.md) e si aggiunge questo oggetto visivo, l'oggetto verrà ora ridimensionato correttamente.

## <a name="next-steps"></a>Passaggi successivi
* [Creare report ottimizzati per le app per telefoni di Power BI](../desktop-create-phone-report.md)
* [Visualizzare i report di Power BI ottimizzati per il proprio telefono](../consumer/mobile/mobile-apps-view-phone-report.md)
* Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

