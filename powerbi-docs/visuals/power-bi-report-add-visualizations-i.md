---
title: Parte 1, Aggiungere visualizzazioni a un report di Power BI
description: Parte 1, Aggiungere visualizzazioni a un report di Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d68abc7b4509595d4dfa3071dc56673e6af89e4f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871058"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Parte 1, Aggiungere visualizzazioni a un report di Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Questo articolo offre un'introduzione rapida alla creazione di una visualizzazione in un report. Le informazioni si applicano sia al servizio Power BI che a Power BI Desktop. Per contenuti più avanzati, [vedere la parte 2](power-bi-report-add-visualizations-ii.md) di questa serie. Nel video seguente Amanda illustra alcuni modi per creare, modificare e formattare gli oggetti visivi nell'area di disegno report. Sarà quindi possibile provare a usare l'[esempio di analisi di vendite e marketing](../sample-datasets.md) per creare il proprio report.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione usa il [file Sales and Marketing Sample PBIX](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu di Power BI Desktop selezionare **File** > **Apri**.
   
2. Trovare la copia del **file Sales and Marketing Sample PBIX**

1. Aprire il **file Sales and Marketing Sample PBIX** nella visualizzazione report ![Screenshot dell'icona della visualizzazione report](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleziona ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) per aggiungere una nuova pagina.

## <a name="add-visualizations-to-the-report"></a>Aggiungere visualizzazioni al report

1. Creare una visualizzazione selezionando un campo dal riquadro **Campi**.

    Iniziare con un campo numerico, ad esempio **Sales** > **TotalSales**. Power BI crea un istogramma con una sola colonna.

    ![Screenshot di un istogramma con una singola colonna.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    In alternativa, iniziare con un campo categoria, ad esempio **Name** o **Product**. Power BI crea una tabella e aggiunge tale campo nell'area **Valori**.

    ![Screenshot di una tabella con quattro categorie](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Oppure, iniziare con un campo geografia, ad esempio **Geo** > **City**. Power BI e Bing Mappe creano una visualizzazione mappa.

    ![Screenshot di una visualizzazione mappa.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Modificare il tipo di visualizzazione

 Creare una visualizzazione e quindi modificarne il tipo. 
 
 1. Selezionare **Product** > **Category** e quindi **Product** > **Count of Product** per aggiungerli entrambi all'area **Valori**.

    ![Screenshot del riquadro Campi con i valori evidenziati.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Cambiare la visualizzazione in un istogramma selezionando l'icona **Istogramma a colonne in pila**.

   ![Screenshot del riquadro Visualizzazioni con l'icona Istogramma a colonne in pila evidenziata.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Per modificare la modalità di ordinamento dell'oggetto visivo, selezionare **Altre azioni** (...).  Usare le opzioni di ordinamento per modificare la direzione di questo (crescente o decrescente) e cambiare la colonna usata per l'ordinamento (**Ordina per**).

   ![Screenshot dell'elenco a discesa Altre azioni.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Passaggi successivi

 Continuare con:

* [Parte 2: Aggiungere visualizzazioni a un report di Power BI](power-bi-report-add-visualizations-ii.md)

* [Interagire con le visualizzazioni](../consumer/end-user-reading-view.md) nel report.

