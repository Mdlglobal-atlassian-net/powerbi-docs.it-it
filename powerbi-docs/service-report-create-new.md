---
title: Creare un report da un set di dati
description: Creare un report di Power BI da un set di dati.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c3f30206a01dce9cf9fd3ce0600b46b401df2b1f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871759"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>Creare un report nel servizio Power BI importando un set di dati
Dopo aver letto [Report in Power BI](consumer/end-user-reports.md) si supponga di voler creare un report personalizzato. Ci sono diversi modi per creare un report. In questo articolo si inizia creando un report di base nel servizio Power BI da un set di dati di Excel. Una volta apprese le nozioni di base relative alla creazione di un report, vedere gli argomenti più avanzati elencati in [Passaggi successivi](#next-steps) alla fine di questo articolo.  

## <a name="prerequisites"></a>Prerequisiti
- [Iscriversi al servizio Power BI](service-self-service-signup-for-power-bi.md). Per creare report con Power BI Desktop, vedere [Visualizzazione report in Power BI Desktop](desktop-report-view.md). 
- [Scaricare il set di dati di Excel dell'esempio di analisi delle vendite al dettaglio](https://go.microsoft.com/fwlink/?LinkId=529778) e salvarlo in OneDrive for Business o in locale.

## <a name="import-the-dataset"></a>Importare il set di dati
In questo metodo di creazione del report si inizia con un set di dati e un'area di disegno report vuota. È possibile seguire la procedura con il set di dati di Excel dell'esempio di analisi delle vendite al dettaglio.

1. Poiché il report verrà creato in un'area di lavoro del servizio Power BI, selezionare un'area di lavoro esistente o crearne una.
   
   ![Elenco di aree di lavoro](media/service-report-create-new/power-bi-workspaces2.png)
2. Nella parte inferiore del riquadro di spostamento selezionare **Recupera dati**.
   
   ![Recupera dati](media/service-report-create-new/power-bi-get-data3.png)
3. Selezionare **File** e passare al percorso in cui è stato salvato l'esempio di analisi delle vendite al dettaglio.
   
    ![Selezionare File](media/service-report-create-new/power-bi-select-files.png)
4. Per questo esercizio, selezionare **Importa**.
   
   ![Selezionare Importa](media/service-report-create-new/power-bi-import.png)
5. Dopo l'importazione del set di dati, selezionare **Visualizza set di dati**.
   
   ![Selezionare Visualizza set di dati](media/service-report-create-new/power-bi-view-dataset.png)
6. Quando si visualizza un set di dati, verrà aperto l'editor di report.  Verranno visualizzati un'area di disegno vuota e gli strumenti di modifica del report.
   
   ![Editor di report](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Se non si ha familiarità con l'area di disegno per la modifica dei report o non se ne ricorda l'uso, vedere [Presentazione dell'editor di report in Power BI](service-the-report-editor-take-a-tour.md) prima di continuare. 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Aggiungere un misuratore radiale al report
Dopo aver importato il set di dati, è possibile iniziare a rispondere ad alcune domande.  Il responsabile marketing vuole sapere se gli obiettivi di vendita annuali verranno soddisfatti. Un misuratore costituisce una [valida opzione di visualizzazione](visuals/power-bi-report-visualizations.md) per visualizzare questo tipo di informazioni.

1. Nel riquadro Campi selezionare **Sales** > **This Year Sales** > **Value**.
   
    ![Grafico a barre nell'editor di report](media/service-report-create-new/power-bi-report-step1.png)
2. Convertire l'oggetto visivo in un misuratore selezionando il modello Misuratore ![Icona Misuratore](media/service-report-create-new/powerbi-gauge-icon.png) nel riquadro **Visualizzazioni**.
   
    ![Oggetto visivo misuratore nell'editor di report](media/service-report-create-new/power-bi-report-step2.png)
3. Trascinare anche **Sales** > **This Year Sales** > **Obiettivo** in **Valore di destinazione**. La procedura è quasi finita.
   
    ![Oggetto visivo misuratore con Obiettivo come valore di destinazione](media/service-report-create-new/power-bi-report-step3.png)
4. A questo punto è opportuno salvare il report.
   
   ![Menu File](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Aggiungere un grafico ad area e un filtro dei dati al report
Il responsabile marketing ha altre domande a cui è necessario dare una risposta. Vuole conoscere l'andamento delle vendite di quest'anno rispetto all'anno precedente. Vuole inoltre visualizzare i risultati in base alla zona.

1. È innanzitutto necessario fare spazio nell'area di disegno. Selezionare il misuratore e spostarlo nell'angolo in alto a destra. A questo punto trascinarne e rilasciarne uno degli angoli per ridurlo.
2. Deselezionare il misuratore. Nel riquadro Campi selezionare **Sales** > **This Year Sales** > **Value** e quindi selezionare **Sales** > **Last Year Sales**.
   
    ![Editor di report con misuratore e grafico a barre](media/service-report-create-new/power-bi-report-step4.png)
3. Convertire l'oggetto visivo in un grafico ad aree selezionando il modello Grafico ad aree ![Icona Grafico](media/service-report-create-new/power-bi-areachart-icon.png) nel riquadro **Visualizzazioni**.
4. Selezionare **Tempo** > **Periodo** per aggiungerlo all'area **Asse**.
   
    ![Editor di report con il grafico ad area attivo](media/service-report-create-new/power-bi-report-step5.png)
5. Per ordinare la visualizzazione in base a un periodo di tempo, selezionare i puntini di sospensione e scegliere **Ordina per periodo**.
6. A questo punto verrà aggiunto il filtro dei dati. Selezionare un'area vuota nell'area di disegno e scegliere il modello Filtro dei dati ![Icona Filtro dei dati](media/service-report-create-new/power-bi-slicer-icon.png) . Nell'area di disegno è ora presente un filtro dei dati vuoto.
   
    ![Area di disegno report](media/service-report-create-new/power-bi-report-step6.png)    
7. Selezionare **District** > **District** nel riquadro Campi. Spostare e ridimensionare il filtro dei dati.
   
    ![Editor di report, aggiungere il distretto](media/service-report-create-new/power-bi-report-step7.png)  
8. Usare il filtro dei dati per individuare modelli e informazioni dettagliate per zona.
   
   ![Video dell'uso del filtro dei dati](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continuare con l'esplorazione dei dati e con l'aggiunta di visualizzazioni. Quando si trovano informazioni approfondite particolarmente interessanti, [aggiungerle a un dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Passaggi successivi

* Informazioni su come [aggiungere visualizzazioni a un dashboard](service-dashboard-pin-tile-from-report.md)   
* Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

