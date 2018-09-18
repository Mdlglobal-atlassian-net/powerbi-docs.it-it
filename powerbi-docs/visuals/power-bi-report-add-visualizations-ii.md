---
title: Parte 2, Aggiungere visualizzazioni a un report di Power BI
description: Parte 2, Aggiungere visualizzazioni a un report di Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: a15975f456bab94fd04fa7501760c9874fabf952
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44736897"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>Parte 2, Aggiungere visualizzazioni a un report di Power BI
Nella[Parte 1](power-bi-report-add-visualizations-ii.md) è stata creata una visualizzazione di base tramite la selezione delle caselle di controllo accanto ai nomi dei campi.  Nella Parte 2 verrà spiegato come usare il trascinamento della selezione e le funzionalità complete dei riquadri **Campi** e **Visualizzazioni** per creare e modificare le visualizzazioni.

### <a name="prerequisites"></a>Prerequisiti
- [Parte 1](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop: è possibile aggiungere visualizzazioni ai report usando il servizio Power BI o Power BI Desktop. Questa esercitazione usa Power BI Desktop. 
- [Esempio di analisi delle vendite al dettaglio](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>Creare una nuova visualizzazione
In questa esercitazione verrà esaminato il set di dati relativo all'analisi delle vendite al dettaglio e verranno create alcune visualizzazioni chiave.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Aprire un report e aggiungere una nuova pagina vuota.
1. Aprire il file PBIX dell'esempio di analisi delle vendite al dettaglio in Power BI Desktop. 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2.  [Aggiungere una nuova pagina](../power-bi-report-add-page.md) selezionando l'icona con il segno più (+) di colore giallo nella parte inferiore dell'area di disegno.

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Aggiungere una visualizzazione relativa al confronto tra le vendite dell'anno corrente e quelle dell'anno scorso.
1. Nella tabella **Sales** selezionare **This Year Sales** > **Value** e **Last Year Sales**. Power BI crea un istogramma.  I risultati sono interessanti ed è utile approfondire l'analisi. Come sono suddivise le vendite per mese?  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. Dalla tabella Time trascinare **FiscalMonth** nell'area **Asse**.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [Modificare la visualizzazione](power-bi-report-change-visualization-type.md) in un grafico ad aree.  Sono disponibili molti tipi di visualizzazione. Per scegliere il tipo più appropriato da usare, vedere le apposite [descrizioni, procedure consigliate ed esercitazioni](power-bi-visualization-types-for-reports-and-q-and-a.md). Dal riquadro Visualizzazioni selezionare l'icona del grafico ad aree ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png).
4. Ordinare la visualizzazione selezionando i puntini di sospensione e scegliendo **Ordina per FiscalMonth**.
5. [Ridimensionare la visualizzazione](power-bi-visualization-move-and-resize.md) selezionandola e trascinando uno dei cerchi sul contorno. Ingrandirla quanto basta per eliminare la barra di scorrimento, ma lasciando spazio sufficiente per aggiungere un'altra visualizzazione.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Salvare il report](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Aggiungere una visualizzazione della mappa in cui sono inclusi i dati sulle vendite per località
1. Nella tabella **Store** selezionare **Territory**. Power BI riconosce Territory come località e crea una visualizzazione della mappa.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. Trascinare **Total Stores** nell'area Dimensioni.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. Aggiungere una legenda.  Per visualizzare i dati in base al nome dell'archivio, trascinare **Chain** nell'area della legenda.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>Passaggi successivi
* Altre informazioni sulle [visualizzazioni nei report di Power BI](power-bi-report-visualizations.md).  
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

