---
title: Visualizzare il contenuto correlato da dashboard, report e set di dati
description: Navigazione semplificata, visualizzazione del contenuto correlato nel dashboard, report e set di dati
author: mihart
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 9e202d22c2ff42a29eb28a8ee154b09f18097d04
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73862269"
---
# <a name="view-related-content-in-the-power-bi-service"></a>Visualizzare il contenuto correlato nel servizio Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Il riquadro **Contenuto correlato** mostra come è interconnesso il contenuto del servizio Power BI: dashboard, report e set di dati. Il riquadro **Contenuto correlato** è anche un punto di partenza per eseguire azioni. Da qui è possibile eseguire operazioni come aprire un dashboard, aprire un report, generare informazioni dettagliate, analizzare i dati in Excel e altro ancora.  

In Power BI, i report sono basati sui set di dati, gli oggetti visivi del report vengono aggiunti ai dashboard e gli oggetti visivi del dashboard si collegano ai report. Ma come si fa a sapere quali dashboard ospitano gli oggetti visivi provenienti dal report Marketing? E come si individuano quei dashboard? Il dashboard Procurement usa oggetti visivi da più di un set di dati? In questo caso, come sono denominati e come è possibile aprirli e modificarli? Il set di dati HR è effettivamente usato in report o dashboard? Oppure può essere spostato senza causare collegamenti interrotti? Domande come queste trovano tutte una risposta nel riquadro **Contenuto correlato**.  Non solo il riquadro mostra il contenuto correlato, ma consente anche di intervenire sul contenuto e spostarsi facilmente tra il contenuto correlato.

![Contenuto correlato](./media/end-user-related/power-bi-list.png)

> [!NOTE]
> La funzionalità Contenuto correlato non funziona per i set di dati di streaming.
> 
> 

## <a name="view-related-content-for-a-dashboard-or-report"></a>Visualizzare il contenuto correlato di un dashboard o report
Questo video illustra come visualizzare il contenuto correlato di un dashboard. Seguire quindi tutte le istruzioni riportate sotto il video per provare a farlo da soli usando il set di dati di esempio Analisi dell'approvvigionamento.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M#t=3m05s" frameborder="0" allowfullscreen></iframe>

Con un dashboard o un report aperto, selezionare **Altre opzioni** (...) nella barra dei menu e scegliere **Visualizza elementi correlati** nell'elenco a discesa.

![Menu a discesa puntini di sospensione](./media/end-user-related/power-bi-dropdown.png)

Viene visualizzato il riquadro **Contenuto correlato**, Per un cruscotto digitale vengono visualizzati tutti i report con visualizzazioni aggiunte al dashboard e i set di dati associati. Per questo dashboard sono presenti visualizzazioni aggiunte da un solo report e il report è basato su un solo set di dati. 

![Riquadro Contenuto correlato](./media/end-user-related/power-bi-view-related-dashboard.png)

A questo punto, è possibile intervenire direttamente sul contenuto correlato.  Ad esempio, selezionare un nome di dashboard o report per aprirlo.  Per un report elencato, selezionare l'icona [Analizza in Excel](../service-analyze-in-excel.md) oppure [Ottieni informazioni dettagliate](end-user-insights.md). Per un set di dati, è possibile visualizzare la data e l'ora dell'ultimo aggiornamento, selezionare [Analizza in Excel](end-user-insights.md) e [Ottieni informazioni dettagliate](../service-analyze-in-excel.md).  



## <a name="view-related-content-for-a-dataset"></a>Visualizzare il contenuto correlato di un set di dati
Per aprire il riquadro *Contenuto correlato* sono necessarie almeno le autorizzazioni di **visualizzazione** per un set di dati. In questo esempio verrà usato l'esempio [Procurement Analysis Sample](../sample-procurement.md).

Nel riquadro di spostamento trovare l'intestazione **Aree di lavoro** e selezionare un'area di lavoro nell'elenco. Se è presente contenuto in un'area di lavoro, verrà visualizzato nell'area di disegno a destra. 

![aree di lavoro nel riquadro di spostamento](./media/end-user-related/power-bi-workspace.png)


In un'area di lavoro selezionare la scheda **Set di dati** e quindi trovare l'icona **Visualizza elementi correlati**![Icona Visualizza elementi correlati](./media/end-user-related/power-bi-view-related-icon-new.png).

![Scheda Set di dati](./media/end-user-related/power-bi-related-dataset.png)

Selezionare l'icona per aprire il riquadro **Contenuto correlato**.

![Il riquadro Contenuto correlato viene aperto in primo piano rispetto alla visualizzazione del contenuto di Power BI](media/end-user-related/power-bi-dataset.png)

A questo punto, è possibile intervenire direttamente sul contenuto correlato. Ad esempio, selezionare un nome di report o dashboard per aprirlo.  Per i dashboard nell'elenco, selezionare un'icona per [Condividere il dashboard con altri utenti](../service-share-dashboards.md) o per aprire la finestra **Impostazioni** per il dashboard. Per un report, selezionare l'icona [Analizza in Excel](../service-analyze-in-excel.md), [Rinomina](../service-rename.md) oppure [Ottieni informazioni dettagliate](end-user-insights.md).  

## <a name="limitations-and-troubleshooting"></a>Limitazioni e risoluzione dei problemi
* Se l'opzione "Visualizza elementi correlati" non è disponibile, cercare invece l'icona ![icona Visualizza elementi correlati](./media/end-user-related/power-bi-view-related-icon-new.png). Selezionare l'icona per aprire il riquadro **Contenuto correlato**.
* Per aprire il contenuto correlato per un report, è necessario essere in [Visualizzazione di lettura](end-user-reading-view.md).
* La funzionalità Contenuto correlato non funziona per i set di dati di streaming.

## <a name="next-steps"></a>Passaggi successivi
* [Introduzione al servizio Power BI](../service-get-started.md)
* Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

