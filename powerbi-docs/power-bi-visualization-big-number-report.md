---
title: Creare un riquadro per numeri elevati da un report di Power BI
description: Creare un riquadro per numeri elevati da un report di Power BI
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 9f748ed1d3a34c6c6aceb14337bbb780598a15f9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-big-number-tile-from-a-power-bi-report"></a>Creare un riquadro per numeri elevati da un report di Power BI
A volte è di vitale importanza individuare uno specifico numero nel dashboard di Power BI, ad esempio le vendite totali, la quota di mercato anno per anno o le opportunità totali. È possibile creare un riquadro per numeri elevati [inserendo una domanda nella casella Domande e risposte](power-bi-visualization-big-number.md) o in un report di Power BI. Questo articolo spiega come crearne uno in un report.

1. Creare un [dashboard](service-dashboards.md) e [recuperare i dati](service-get-data.md).
   
   [Scaricare l'esempio di analisi delle vendite al dettaglio](sample-retail-analysis.md) per avere dei dati su cui fare pratica. 
2. Aprire il report in [visualizzazione di modifica](service-reading-view-and-editing-view.md).
3. Nel report trovare una pagina con dello spazio vuoto oppure [aggiungere una nuova pagina al report](power-bi-report-add-page.md).
4. Nell'elenco dei campi selezionare il campo numerico da visualizzare.
   
   In questo esempio **Open Store count** nella tabella **Store** . Power BI crea un istogramma con un numero.
   
   ![](media/power-bi-visualization-big-number-report/pbi_rptnumbertilechart.png)
5. Nel riquadro Visualizzazioni selezionare l'icona Scheda.
   
   ![](media/power-bi-visualization-big-number-report/pbi_changechartcard.png)
6. Passare il puntatore del mouse sulla scheda e selezionare l'icona a forma di puntina ![](media/power-bi-visualization-big-number-report/pbi_pintile.png) per aggiungere il riquadro al dashboard. 
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-icon.png)
7. Aggiungere il riquadro a un dashboard esistente o a un nuovo dashboard. 
   
   * Dashboard esistente: selezionare il nome del dashboard nell'elenco a discesa.
   * Nuovo dashboard: digitare il nome del nuovo dashboard.
8. Selezionare **Aggiungi**.
   
   Un messaggio di operazione completata (nell'angolo superiore destro) informa l'utente che è stata aggiunta la visualizzazione, come riquadro, al dashboard.
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-success-message.png)
9. Selezionare **Vai al dashboard**. In quel punto è possibile [modificare e spostare](service-dashboard-edit-tile.md) la visualizzazione aggiunta.

## <a name="next-steps"></a>Passaggi successivi
[Riquadri del dashboard in Power BI](service-dashboard-tiles.md)

[Dashboard in Power BI](service-dashboards.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

