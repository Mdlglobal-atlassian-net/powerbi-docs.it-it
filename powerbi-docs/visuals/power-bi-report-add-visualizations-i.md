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
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299291"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Parte 1, Aggiungere visualizzazioni a un report di Power BI

Questo articolo offre un'introduzione rapida alla creazione di una visualizzazione in un report. Le informazioni si applicano sia al servizio Power BI che a Power BI Desktop. Per contenuti più avanzati, [vedere la parte 2](power-bi-report-add-visualizations-ii.md) di questa serie. Nel video seguente Amanda illustra alcuni modi per creare, modificare e formattare gli oggetti visivi nell'area di disegno report. Sarà quindi possibile provare a usare l'[esempio di analisi di vendite e marketing](../sample-datasets.md) per creare il proprio report.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Aprire un report e aggiungere una nuova pagina

1. Aprire un [report in Visualizzazione di modifica](../service-interact-with-a-report-in-editing-view.md).

    Questa esercitazione usa l'[esempio di analisi di vendite e marketing](../sample-datasets.md).

1. Se il riquadro **Campi** non è visibile, selezionare l'icona a forma di freccia per aprirlo.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Aggiungere una pagina vuota al report.

## <a name="add-visualizations-to-the-report"></a>Aggiungere visualizzazioni al report

1. Creare una visualizzazione selezionando un campo dal riquadro **Campi**.

    Iniziare con un campo numerico, ad esempio **SalesFact** > **Sales $** . Power BI crea un istogramma con una sola colonna.

    ![Screenshot di un istogramma con una singola colonna.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    In alternativa, iniziare con un campo categoria, ad esempio **Name** o **Product**. Power BI crea una tabella e aggiunge tale campo nell'area **Valori**.

    ![GIF di un utente che selezione Product e poi la categoria per creare una tabella.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Oppure, iniziare con un campo geografia, ad esempio **Geo** > **City**. Power BI e Bing Mappe creano una visualizzazione mappa.

    ![Screenshot di una visualizzazione mappa.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Creare una visualizzazione e quindi modificarne il tipo. Selezionare **Product** > **Category** e quindi **Product** > **Count of Product** per aggiungerli entrambi all'area **Valori**.

   ![Screenshot del riquadro Campi con i valori evidenziati.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Cambiare la visualizzazione in un istogramma selezionando l'icona **Istogramma a colonne in pila**.

   ![Screenshot del riquadro Visualizzazioni con l'icona Istogramma a colonne in pila evidenziata.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Quando si creano visualizzazioni nel report, è possibile [aggiungerle al dashboard](../service-dashboard-pin-tile-from-report.md). Per aggiungere la visualizzazione, selezionare l'icona Aggiungi ![Screenshot dell'icona Aggiungi](media/power-bi-report-add-visualizations-i/pinnooutline.png).

   ![Screenshot di una visualizzazione Istogramma con l'icona Aggiungi evidenziata.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Passaggi successivi

 Continuare con:

* [Parte 2: Aggiungere visualizzazioni a un report di Power BI](power-bi-report-add-visualizations-ii.md)

* [Interagire con le visualizzazioni](../consumer/end-user-reading-view.md) nel report.

* [Eseguire altre operazioni con le visualizzazioni](power-bi-report-visualizations.md).

* [Salvare il report](../service-report-save.md).
