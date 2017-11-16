---
title: 'Creare un nuovo report da un set di dati '
description: Informazioni su come creare un nuovo report di Power BI da un set di dati.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: f4afb1eaa1b3012fdbdb0eff35e9eff695cc32e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-new-power-bi-report-by-importing-a-dataset"></a>Creare un nuovo report di Power BI importando un set di dati
Dopo aver letto [Report in Power BI](service-reports.md) si supponga di voler creare un report personalizzato. È possibile creare un report in molti modi, ma in questo articolo verrà spiegato come crearne uno molto semplice da un set di dati di Excel. Una volta apprese le nozioni di base relative alla creazione di un report, è possibile consultare gli argomenti più avanzati elencati nella sezione **Passaggi successivi** alla fine di questo articolo.  

> **SUGGERIMENTO**: per creare un report copiandone uno esistente, vedere [Copiare un report](power-bi-report-copy.md).
> 
> 

## <a name="import-the-dataset"></a>Importare il set di dati
In questo metodo di creazione del report si inizia con un set di dati e un'area di disegno report vuota. Per seguire la procedura, [scaricare il set di dati di Excel dell'esempio di analisi delle vendite al dettaglio](http://go.microsoft.com/fwlink/?LinkId=529778) e salvarlo in OneDrive for Business (scelta consigliata) o in locale.

1. Dal momento che il report verrà creato in un'area di lavoro del servizio Power BI, selezionare un'area di lavoro esistente o crearne una nuova.
   
   ![](media/service-report-create-new/power-bi-workspaces2.png)
2. Nella parte inferiore del riquadro di spostamento sinistro selezionare **Recupera dati**.
   
   ![](media/service-report-create-new/power-bi-get-data3.png)
3. Selezionare **File** e passare al percorso in cui è stato salvato l'esempio di analisi delle vendite al dettaglio.
   
    ![](media/service-report-create-new/power-bi-select-files.png)
4. Per questo esercizio, selezionare **Importa**.
   
   ![](media/service-report-create-new/power-bi-import.png)
5. Dopo l'importazione del set di dati, selezionare **Visualizza set di dati**.
   
   ![](media/service-report-create-new/power-bi-view-dataset.png)
6. Quando si visualizza un set di dati, verrà aperto l'editor di report.  Verranno visualizzati un'area di disegno vuota e gli strumenti di modifica del report.
   
   ![](media/service-report-create-new/power-bi-blank-report.png)

> **SUGGERIMENTO**: se non si conosce l'area di disegno per la modifica dei report o non se ne ricorda l'uso, prima di continuare è possibile eseguire la [presentazione dell'editor di report](service-the-report-editor-take-a-tour.md).
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Aggiungere un misuratore radiale al report
Dopo aver importato il set di dati, è possibile iniziare a rispondere ad alcune domande.  Il responsabile marketing vuole sapere se gli obiettivi di vendita annuali verranno soddisfatti. Un misuratore costituisce una [valida opzione di visualizzazione](power-bi-report-visualizations.md) per visualizzare questo tipo di informazioni.

1. Nel riquadro Campi selezionare **Sales** > **This Year Sales** > **Value**.
   
    ![](media/service-report-create-new/power-bi-report-step1.png)
2. Convertire l'oggetto visivo in un misuratore selezionando il modello del misuratore ![](media/service-report-create-new/powerbi-gauge-icon.png) nel riquadro **Visualizzazioni**.
   
    ![](media/service-report-create-new/power-bi-report-step2.png)
3. Trascinare anche **Sales** > **This Year Sales** > **Obiettivo** in **Valore di destinazione**. La procedura è quasi finita.
   
    ![](media/service-report-create-new/power-bi-report-step3.png)
4. A questo punto è opportuno [salvare il report](service-report-save.md).
   
   ![](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Aggiungere un grafico ad area e un filtro dei dati al report
Il responsabile marketing ha altre domande a cui è necessario dare una risposta. Vuole conoscere l'andamento delle vendite di quest'anno rispetto all'anno precedente e vuole che i risultati siano visualizzati in base alla zona.

1. È innanzitutto necessario fare spazio nell'area di disegno. Selezionare il misuratore e spostarlo nell'angolo in alto a destra. A questo punto trascinarne e rilasciarne uno degli angoli per ridurlo.
2. Deselezionare il misuratore. Nel riquadro Campi selezionare **Sales** > **This Year Sales** > **Value** e quindi selezionare **Sales** > **Last Year Sales**.
   
    ![](media/service-report-create-new/power-bi-report-step4.png)
3. Convertire l'oggetto visivo in un grafico ad area selezionando il modello del grafico ad area ![](media/service-report-create-new/power-bi-areachart-icon.png) nel riquadro **Visualizzazioni**.
4. Selezionare **Tempo** > **Periodo** per aggiungerlo all'area **Asse**.
   
    ![](media/service-report-create-new/power-bi-report-step5.png)
5. Per ordinare la visualizzazione, selezionare i puntini di sospensione e scegliere **Ordina per periodo**.
6. A questo punto verrà aggiunto il filtro dei dati. Selezionare un'area vuota nell'area di disegno e scegliere il modello Filtro dei dati ![](media/service-report-create-new/power-bi-slicer-icon.png). All'area di disegno verrà aggiunto un filtro dei dati vuoto.
   
    ![](media/service-report-create-new/power-bi-report-step6.png)    
7. Selezionare **District** > **District** nel riquadro Campi. Spostare e ridimensionare il filtro dei dati.
   
    ![](media/service-report-create-new/power-bi-report-step7.png)  
8. Usare il filtro dei dati per individuare modelli e informazioni dettagliate per zona.
   
   ![](media/service-report-create-new/power-bi-slicer-video2.gif)  
9. Facoltativamente, continuare ad aggiungere visualizzazioni.

## <a name="next-steps"></a>Passaggi successivi
* [Creare una copia di un report](power-bi-report-copy.md)
* [Salvare il report](service-report-save.md)    
* [Aggiungere una nuova pagina al report](power-bi-report-add-page.md)  
* Informazioni su come [aggiungere visualizzazioni a un dashboard](service-dashboard-pin-tile-from-report.md)    
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

