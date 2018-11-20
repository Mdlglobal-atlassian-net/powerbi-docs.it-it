---
title: 'Creare un nuovo report da un set di dati '
description: Informazioni su come creare un nuovo report di Power BI da un set di dati.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/24/2018
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 96b46e595ffd2373a2d59776cb8c2b4314727d89
ms.sourcegitcommit: 1e4fee6d1f4b7803ea285eb879c8d5a4f7ea8b85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51718046"
---
# <a name="create-a-new-report-in-power-bi-service-by-importing-a-dataset"></a>Creare un nuovo report del servizio Power BI importando un set di dati
Dopo aver letto [Report in Power BI](consumer/end-user-reports.md) si supponga di voler creare un report personalizzato. È possibile creare un report in molti modi, ma in questo articolo verrà spiegato come crearne uno molto semplice da un set di dati di Excel tramite il servizio Power BI. Una volta apprese le nozioni di base relative alla creazione di un report, è possibile consultare gli argomenti più avanzati elencati nella sezione **Passaggi successivi** alla fine di questo articolo.  

> **SUGGERIMENTO**: per creare un report copiandone uno esistente, vedere [Copiare un report](power-bi-report-copy.md).
> 
> ### <a name="prerequisites"></a>Prerequisiti
> - Servizio Power BI (per la creazione di report con Power BI Desktop, vedere [Visualizzazione Report in Power BI Desktop](desktop-report-view.md))  
> - Set di dati dell'esempio di analisi delle vendite al dettaglio

## <a name="import-the-dataset"></a>Importare il set di dati
In questo metodo di creazione del report si inizia con un set di dati e un'area di disegno report vuota. Per seguire la procedura, [scaricare il set di dati di Excel dell'esempio di analisi delle vendite al dettaglio](http://go.microsoft.com/fwlink/?LinkId=529778) e salvarlo in OneDrive for Business (scelta consigliata) o in locale.

1. Dal momento che il report verrà creato in un'area di lavoro del servizio Power BI, selezionare un'area di lavoro esistente o crearne una nuova.
   
   ![Elenco di aree di lavoro per le app](media/service-report-create-new/power-bi-workspaces2.png)
2. Nella parte inferiore del riquadro di spostamento sinistro selezionare **Recupera dati**.
   
   ![Recupera dati](media/service-report-create-new/power-bi-get-data3.png)
3. Selezionare **File** e passare al percorso in cui è stato salvato l'esempio di analisi delle vendite al dettaglio.
   
    ![Selezionare File](media/service-report-create-new/power-bi-select-files.png)
4. Per questo esercizio, selezionare **Importa**.
   
   ![Selezionare Importa](media/service-report-create-new/power-bi-import.png)
5. Dopo l'importazione del set di dati, selezionare **Visualizza set di dati**.
   
   ![Selezionare Visualizza set di dati](media/service-report-create-new/power-bi-view-dataset.png)
6. Quando si visualizza un set di dati, verrà aperto l'editor di report.  Verranno visualizzati un'area di disegno vuota e gli strumenti di modifica del report.
   
   ![Editor di report](media/service-report-create-new/power-bi-blank-report.png)

> **SUGGERIMENTO**: se non si conosce l'area di disegno per la modifica dei report o non se ne ricorda l'uso, prima di continuare è possibile eseguire la [presentazione dell'editor di report](service-the-report-editor-take-a-tour.md).
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Aggiungere un misuratore radiale al report
Dopo aver importato il set di dati, è possibile iniziare a rispondere ad alcune domande.  Il responsabile marketing vuole sapere se gli obiettivi di vendita annuali verranno soddisfatti. Un misuratore costituisce una [valida opzione di visualizzazione](visuals/power-bi-report-visualizations.md) per visualizzare questo tipo di informazioni.

1. Nel riquadro Campi selezionare **Sales** > **This Year Sales** > **Value**.
   
    ![Grafico a barre nell'editor di report](media/service-report-create-new/power-bi-report-step1.png)
2. Convertire l'oggetto visivo in un misuratore selezionando il modello del misuratore ![Icona del misuratore](media/service-report-create-new/powerbi-gauge-icon.png) nel riquadro **Visualizzazioni**.
   
    ![Oggetto visivo misuratore nell'editor di report](media/service-report-create-new/power-bi-report-step2.png)
3. Trascinare anche **Sales** > **This Year Sales** > **Obiettivo** in **Valore di destinazione**. La procedura è quasi finita.
   
    ![Oggetto visivo misuratore con Obiettivo come valore di destinazione](media/service-report-create-new/power-bi-report-step3.png)
4. A questo punto è opportuno [salvare il report](service-report-save.md).
   
   ![Menu File](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Aggiungere un grafico ad area e un filtro dei dati al report
Il responsabile marketing ha altre domande a cui è necessario dare una risposta. Vuole conoscere l'andamento delle vendite di quest'anno rispetto all'anno precedente e vuole che i risultati siano visualizzati in base alla zona.

1. È innanzitutto necessario fare spazio nell'area di disegno. Selezionare il misuratore e spostarlo nell'angolo in alto a destra. A questo punto trascinarne e rilasciarne uno degli angoli per ridurlo.
2. Deselezionare il misuratore. Nel riquadro Campi selezionare **Sales** > **This Year Sales** > **Value** e quindi selezionare **Sales** > **Last Year Sales**.
   
    ![Editor di report con misuratore e grafico a barre](media/service-report-create-new/power-bi-report-step4.png)
3. Convertire l'oggetto visivo in un grafico ad area selezionando il modello del grafico ad area ![Icona del grafico](media/service-report-create-new/power-bi-areachart-icon.png) nel riquadro **Visualizzazioni**.
4. Selezionare **Tempo** > **Periodo** per aggiungerlo all'area **Asse**.
   
    ![Editor di report con il grafico ad area attivo](media/service-report-create-new/power-bi-report-step5.png)
5. Per ordinare la visualizzazione in base a un periodo di tempo, selezionare i puntini di sospensione e scegliere **Ordina per periodo**.
6. A questo punto verrà aggiunto il filtro dei dati. Selezionare un'area vuota nell'area di disegno e scegliere il modello Filtro dei dati ![Icona Filtro dei dati](media/service-report-create-new/power-bi-slicer-icon.png)    . All'area di disegno verrà aggiunto un filtro dei dati vuoto.
   
    ![Area di disegno report](media/service-report-create-new/power-bi-report-step6.png)    
7. Selezionare **District** > **District** nel riquadro Campi. Spostare e ridimensionare il filtro dei dati.
   
    ![Editor di report, aggiungere il distretto](media/service-report-create-new/power-bi-report-step7.png)  
8. Usare il filtro dei dati per individuare modelli e informazioni dettagliate per zona.
   
   ![Video dell'uso del filtro dei dati](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continuare con l'esplorazione dei dati e con l'aggiunta di visualizzazioni. Quando si trovano informazioni approfondite particolarmente interessanti, [aggiungerle a un dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Passaggi successivi
* [Aggiungere una nuova pagina al report](power-bi-report-add-page.md)  
* Informazioni su come [aggiungere visualizzazioni a un dashboard](service-dashboard-pin-tile-from-report.md)   
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

