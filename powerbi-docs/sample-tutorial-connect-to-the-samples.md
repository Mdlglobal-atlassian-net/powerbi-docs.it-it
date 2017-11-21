---
title: Esercitazione sull'uso degli esempi di Power BI.
description: 'Esercitazione: Uso degli esempi di Power BI'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 03/08/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: 6d043f21635308def7b119c072a7f99c118e901d
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="the-power-bi-samples-a-tutorial"></a>Esercitazione sugli esempi di Power BI
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

È consigliabile iniziare dall'articolo [Set di dati di esempio per Power BI](sample-datasets.md). Quell'articolo illustra in dettaglio tutti gli esempi, come ottenerli, dove salvarli, come usarli e alcuni degli scenari che possono aiutare a chiarire. Una volta acquisite le nozioni di base, proseguire con questa esercitazione.   

## <a name="about-this-tutorial"></a>Informazioni su questa esercitazione
Questa esercitazione spiega come importare i pacchetti di contenuto di esempio, come aggiungerli al servizio Power BI e come aprire il contenuto. Un *pacchetto di contenuto* è un tipo di esempio in cui il set di dati è abbinato a un dashboard e a un report. I pacchetti di contenuto di esempio sono disponibili dall'interno di Power BI, mediante **Recupera dati**.

> [!NOTE]
> Questa esercitazione si applica al servizio Power BI e non a Power BI Desktop.
> 
> 

Il pacchetto di contenuto di esempio di *analisi delle vendite al dettaglio* usato in questa esercitazione comprende un dashboard, un report e un set di dati.
Per acquisire familiarità con il pacchetto di contenuto e il relativo scenario, è possibile visualizzare una [presentazione dell'esempio di analisi delle vendite al dettaglio](sample-retail-analysis.md) prima di iniziare.

## <a name="get-data-in-this-case-get-a-sample-content-pack"></a>Recuperare i dati (in questo caso un pacchetto di contenuto di esempio)
1. Aprire il servizio Power BI (app.powerbi.com) ed eseguire l'accesso.
2. Selezionare un'area di lavoro e creare un nuovo dashboard.  
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-create-dashboard2.png)
3. Assegnargli il nome **Esempio di analisi delle vendite al dettaglio**.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-name-dashboard.png)
4. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro. Se **Recupera dati** non è visibile, selezionare ![](media/sample-tutorial-connect-to-the-samples/expand-nav.png) per espandere il riquadro di spostamento.
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_getdata.png)
5. Selezionare **Esempi**.  
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_samplesdownload.png)
6. Selezionare *Esempio di analisi delle vendite al dettaglio* e scegliere **Connetti**.   
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-exactly-was-imported"></a>Che cosa viene importato esattamente?
Con i pacchetti del contenuto di esempio, quando si seleziona **Connetti** Power BI in realtà carica una copia del pacchetto di contenuto e la archivia nel cloud. Quando si fa clic su **Connetti** si ottiene ciò che l'autore del pacchetto di contenuto ha incluso, ovvero un set di dati, un report e un dashboard.

1. Power BI crea il nuovo dashboard e lo inserisce nell'elenco nella scheda **Dashboard**. L'asterisco giallo indica che si tratta di un nuovo dashboard.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dashboard.png)
2. Aprire la scheda **Report**.  È presente un nuovo report denominato *Retail Analysis Sample*.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Osservare anche la scheda **Set di dati**.  Anche lì è presente un nuovo set di dati.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Esplorare il nuovo contenuto
Ora è possibile esaminare il dashboard, il set di dati e il report autonomamente. Esistono molti modi diversi per passare al dashboard, ai report e i set di dati. Qui ne viene descritto solo uno.  

> [!TIP]
> Se si preferisce acquisire informazioni preliminari prima di iniziare,  vedere la [presentazione dell'esempio di analisi delle vendite al dettaglio](sample-retail-analysis.md) per una descrizione dettagliata di questo esempio.
> 
> 

1. Tornare alla scheda **Dashboard** e selezionare il dashboard *Retail Analysis Sample* per aprirlo.    
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards.png)
2. Il dashboard viene aperto.  Include una serie di riquadri di visualizzazione.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)
3. Selezionare uno dei riquadri per aprire il report sottostante.  In questo esempio viene selezionato il grafico ad area, evidenziato in rosa nell'immagine precedente. Nel report viene visualizzata la pagina che contiene il grafico ad area.
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Se il riquadro fosse stato creato con [Domande e risposte di Power BI](service-q-and-a.md) sarebbe comparsa la pagina Domande e risposte.
   > 
   > 
4. Nella scheda **Set di dati** sono presenti varie opzioni per esplorare il set di dati.  Non è possibile aprirlo e vedere tutte le righe e colonne, come invece si può fare in Power BI Desktop o in Excel.  Quando un utente condivide un pacchetto di contenuto con i colleghi, in genere vuole condividere le informazioni dettagliate e non consentire ai colleghi di accedere direttamente ai dati. Questo però non significa che non sia possibile esplorare il set di dati.  
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon2.png)
   
   * Un modo per esplorare il set di dati consiste nel creare visualizzazioni e report personalizzati da zero.  Selezionare l'icona del grafico ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) per aprire il set di dati in modalità di modifica report.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)
   * Un altro modo per esplorare il set di dati consiste nell'eseguire [Informazioni rapide](service-insights.md). Selezionare i puntini di sospensione (...) e scegliere **Ottieni informazioni dettagliate**. Quando le informazioni sono pronte, selezionare **Visualizza informazioni dettagliate**.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="next-steps"></a>Passaggi successivi
[Concetti di base di Power BI](service-basic-concepts.md)

[Esempi per il servizio Power BI](sample-datasets.md)

[Origini dati per Power BI](service-get-data.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

