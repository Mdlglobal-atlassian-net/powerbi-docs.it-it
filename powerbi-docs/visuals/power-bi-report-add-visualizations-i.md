---
title: Parte 1, Aggiungere visualizzazioni a un report di Power BI
description: Parte 1, Aggiungere visualizzazioni a un report di Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 52c0211aea0462e0bf79d7a48808f1f826c09fb6
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296088"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>Parte 1, Aggiungere visualizzazioni a un report di Power BI
Questo articolo offre una breve introduzione alla creazione di una visualizzazione in un report tramite il servizio Power BI o Power BI Desktop.  Per i contenuti più avanzati, [vedere la Parte II](power-bi-report-add-visualizations-ii.md). Nel video seguente Amanda illustra alcuni modi per creare, modificare e formattare gli oggetti visivi nell'area di disegno report. Sarà quindi possibile provare a usare l'[esempio di analisi di vendite e marketing](../sample-datasets.md) per creare il proprio report.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Aprire un report e aggiungere una nuova pagina
1. Aprire un [report in Visualizzazione di modifica](../consumer/end-user-reading-view.md). Questa esercitazione usa l'[esempio di analisi di vendite e marketing](../sample-datasets.md).
2. Se il riquadro Campi non è visibile, selezionare l'icona a forma di freccia per aprirlo. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. Aggiungere una pagina vuota al report.

## <a name="add-visualizations-to-the-report"></a>Aggiungere visualizzazioni al report
1. Creare una visualizzazione selezionando un campo dal riquadro **Campi**.  
   
   **Iniziare con un campo numerico**, ad esempio SalesFact > Sales $. Power BI crea un istogramma con una sola colonna.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **In alternativa, iniziare con un campo categoria**, ad esempio Name o Product: Power BI crea una tabella e aggiunge tale campo nell'area **Valori**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **Oppure, iniziare con un campo geografia**, ad esempio Geo > City. Power BI e Bing Mappe creano una visualizzazione mappa.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Creare una visualizzazione e quindi modificarne il tipo. Selezionare **Product > Category** e quindi **Product > Count of Product** per aggiungerli entrambi all'area **Valori**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Cambiare la visualizzazione in un istogramma selezionando l'icona istogramma.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. Quando si creano visualizzazioni nel report, è possibile [aggiungerle al dashboard](../service-dashboard-pin-tile-from-report.md). Per aggiungere la visualizzazione, selezionare l'icona Aggiungi ![](media/power-bi-report-add-visualizations-i/pinnooutline.png).
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>Passaggi successivi
 Continuare con la [Parte 2: Aggiungere visualizzazioni a un report di Power BI](power-bi-report-add-visualizations-ii.md)
   
   [Interagire con le visualizzazioni](../consumer/end-user-reading-view.md) nel report.
   
   [Eseguire altre operazioni con le visualizzazioni](power-bi-report-visualizations.md).
   
   [Salvare il report](../service-report-save.md).
