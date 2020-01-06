---
title: Connettersi agli esempi nel servizio Power BI
description: Informazioni su come installare ed esplorare gli esempi nel servizio Power BI.
author: maggiesMSFT
ms.reviewer: amac
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 90136f39d9f2a8e330748b56d6302bb75d2a31fe
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "73873837"
---
#  <a name="connect-to-the-samples-in-the-power-bi-service"></a>Connettersi agli esempi nel servizio Power BI

Questa esercitazione illustra come: 
- Importare un pacchetto di contenuto di esempio, aggiungerlo al servizio Power BI e aprire il contenuto. Un *pacchetto di contenuto* è un tipo di esempio in cui il set di dati è abbinato a un dashboard e a un report. 
- Aprire un file con estensione pbix di esempio in Power BI Desktop.

Se servono maggiori informazioni di base, vedere [Set di dati di esempio per Power BI](sample-datasets.md). L'articolo illustra in dettaglio tutti gli esempi, come ottenerli, dove salvarli, come usarli e alcuni degli scenari trattati. 

## <a name="prerequisites"></a>Prerequisiti
Gli esempi sono disponibili per il servizio Power BI e per Power BI Desktop. Per seguire la procedura, verrà usato l'esempio di analisi delle vendite al dettaglio.

Il pacchetto di contenuto di esempio di *analisi delle vendite al dettaglio* usato in questa esercitazione comprende un dashboard, un report e un set di dati.
Per acquisire familiarità con questo pacchetto di contenuto e il relativo scenario, vedere [Esempio di analisi delle vendite al dettaglio per Power BI: Presentazione](sample-retail-analysis.md) prima di iniziare.

## <a name="samples-in-the-power-bi-service"></a>Esempi nel servizio Power BI

1. Aprire il servizio Power BI (app.powerbi.com), eseguire l'accesso e aprire l'area di lavoro in cui salvare l'esempio. 

    Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale.

2. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento. 

   ![Selezionare Recupera dati](media/sample-datasets/power-bi-get-data.png)

   Se l'opzione **Recupera dati** non è visualizzata, espandere il riquadro di spostamento selezionando l'icona seguente nella parte superiore: ![icona hamburger](media/sample-tutorial-connect-to-the-samples/expand-nav.png).

5. Nella pagina **Recupera dati** che viene visualizzata selezionare **Esempi**.
   
6. Selezionare **Retail Analysis Sample** e quindi scegliere **Connetti**.   
   
   ![Pulsante Connetti](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-was-imported"></a>Cosa è stato importato?
Con i pacchetti di contenuto di esempio, quando si seleziona **Connetti** Power BI ottiene una copia del pacchetto di contenuto e la archivia nel cloud. Quando si seleziona **Connetti** si ottiene ciò che l'autore del pacchetto di contenuto ha incluso, ovvero un set di dati, un report e un dashboard. 

1. Quando si seleziona **Connetti**, Power BI crea il nuovo dashboard e lo aggiunge nella scheda **Dashboard**. 
   
   ![Voce Retail Analysis Sample](media/sample-retail-analysis/retail-entry.png)
2. Aprire la scheda **Report**. Sarà presente un nuovo report denominato *Esempio di analisi delle vendite al dettaglio*.
   
   ![Voce relativa al report dell'esempio di analisi delle vendite al dettaglio](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Esaminare la scheda **Set di dati** e osservare la presenza anche di un nuovo set di dati.
   
   ![Voce relativa al set di dati dell'esempio di analisi delle vendite al dettaglio](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Esplorare il nuovo contenuto
Ora è possibile esaminare il dashboard, il set di dati e il report autonomamente. Ci sono molti modi diversi per passare ai dashboard, ai report e ai set di dati. Uno di questi modi è descritto nella procedura seguente.  

1. Tornare alla scheda **Dashboard** e selezionare il dashboard **Esempio di analisi delle vendite al dettaglio** per aprirlo.       

   Il dashboard viene aperto e include una serie di riquadri di visualizzazione.   
 
1. Selezionare uno dei riquadri nel dashboard per aprire il report sottostante. In questo esempio verrà selezionato il grafico ad area **This Year's Sales, Last Year's Sales by Fiscal Month**.  

   ![Dashboard dell'esempio di analisi delle vendite al dettaglio con l'oggetto visivo evidenziato](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)

   Il report si apre alla pagina che contiene il grafico ad area selezionato, in questo caso, la pagina **District Monthly Sales** del report.
   
   ![Pagina del report District Monthly Sales](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Se il riquadro fosse stato creato con [Domande e risposte di Power BI](power-bi-tutorial-q-and-a.md) verrebbe visualizzata invece la pagina Domande e risposte. Se il riquadro fosse stato [aggiunto da Excel](service-dashboard-pin-tile-from-excel.md), verrebbe aperto Excel Online all'interno di Power BI.
   > 
   > 
1. Quando un utente condivide un pacchetto di contenuto con i colleghi, in genere vuole condividere solo informazioni dettagliate specifiche e non consentire ai colleghi di accedere direttamente ai dati. Nella scheda **Set di dati** sono disponibili varie opzioni per esplorare il set di dati. Non è tuttavia possibile vedere le righe e le colonne di dati, come invece si può fare in Power BI Desktop o in Excel. 
   
   ![Voce relativa al set di dati dell'esempio di analisi delle vendite al dettaglio](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)
   
1. Un modo per esplorare il set di dati consiste nel creare visualizzazioni e report personalizzati da zero. Selezionare l'icona del grafico ![Icona del grafico](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) per aprire il set di dati in modalità di modifica report.
     
   ![Nuovo report](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)

1. Un altro modo per esplorare il set di dati consiste nell'eseguire [Informazioni rapide](consumer/end-user-insights.md). Selezionare **Altre opzioni** (...) e quindi scegliere **Ottieni informazioni rapide**. Quando le informazioni sono pronte, selezionare **Visualizza informazioni dettagliate**.
     
    ![Report con informazioni dettagliate](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="samples-in-power-bi-desktop"></a>Esempi in Power BI Desktop 
Quando si apre il file con estensione pbix di esempio per la prima volta in Power BI Desktop, viene applicata la visualizzazione report, che consente di esplorare, creare e modificare qualsiasi numero di pagine del report con visualizzazioni. La visualizzazione report offre un'esperienza di progettazione analoga a quella della visualizzazione di modifica di un report nel servizio Power BI, consentendo di spostare le visualizzazioni, nonché di copiare e incollare, unire e così via. 

A differenza di quanto avviene quando si modifica un report nel servizio Power BI, in Power BI Desktop è anche possibile lavorare con le query e modellare i dati per ottenere informazioni dettagliate di migliore qualità nei report. Il file di Power BI Desktop può quindi essere salvato in qualsiasi posizione, nell'unità locale o nel cloud.

1. Scaricare il [file con estensione pbix dell'esempio di analisi delle vendite al dettaglio](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) e aprirlo in Power BI Desktop. 

    ![Esempio in visualizzazione report di Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. Il file verrà aperto nella visualizzazione Report. Osservare le quattro schede nella parte inferiore dell'editor di report, che rappresentano le quattro pagine del report. Per questo esempio è selezionata la pagina **New Stores**. 

    ![Scheda New Stores evidenziata](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

1. Per un approfondimento sull'editor di report, vedere [Presentazione dell'editor di report](service-the-report-editor-take-a-tour.md).

## <a name="whats-in-your-report"></a>Quali elementi sono presenti nel report?
Quando si scarica un file con estensione pbix di esempio, oltre al report viene scaricato anche il *set di dati sottostante*. Quando si apre il file, Power BI Desktop carica i dati con le query e le relazioni associate. È possibile visualizzare i dati e le relazioni sottostanti, ma non è possibile visualizzare le query sottostanti nell'editor di query.


1. Passare alla [visualizzazione dati](desktop-data-view.md) selezionando l'icona di tabella ![icona di tabella](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png).
 
    ![Vista dati di Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    Nella visualizzazione dati è possibile esaminare, esplorare e comprendere i dati nel modello di Power BI Desktop. Questa visualizzazione è diversa da quella di tabelle, colonne e dati nell'editor di query. I dati nella visualizzazione dati sono già caricati nel modello.

    Durante la modellazione dei dati talvolta si vuole vedere il contenuto effettivo delle righe e delle colonne di una tabella senza creare un oggetto visivo nell'area di disegno report. Questo vale in particolare per la creazione di misure e colonne calcolate o quando è necessario identificare un tipo di dati o una categoria di dati.

1. Passare alla [visualizzazione relazioni](desktop-relationship-view.md) selezionando l'icona seguente: ![Icona della visualizzazione relazioni](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png).
 
    ![Visualizzazione delle relazioni in Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    La visualizzazione Relazioni mostra tutte le tabelle, le colonne e le relazioni presenti nel modello. Da qui è possibile visualizzare, modificare e creare relazioni.

## <a name="next-steps"></a>Passaggi successivi
Questo ambiente è sicuro perché è possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere **Recupera dati** per ottenere una nuova copia di questo esempio.

La presentazione ha illustrato in che modo dashboard, set di dati, relazioni e report di Power BI possono fornire informazioni dettagliate sui dati di esempio. È ora possibile iniziare e connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione al servizio Power BI](service-get-started.md) e [Introduzione a Power BI Desktop](desktop-getting-started.md).  

Per altre informazioni, vedere:  
- [Concetti di base del servizio Power BI](service-basic-concepts.md)
- [Esempi per il servizio Power BI](sample-datasets.md)
- [Origini dati per Power BI](service-get-data.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
