---
title: 'Esempio di analisi della qualità dei fornitori per Power BI: Presentazione'
description: 'Esempio di analisi della qualità dei fornitori per Power BI: Presentazione'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 76e053d34dcd7f1f199f4cbf9f02196e8efc6232
ms.sourcegitcommit: ba95d4979f1869f49a7d266c591f95e2810fdb29
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69621326"
---
# <a name="supplier-quality-analysis-sample-for-power-bi-take-a-tour"></a>Esempio di analisi della qualità dei fornitori per Power BI: Presentazione

Questo dashboard di esempio specifico del settore, unitamente al report sottostante, consente di analizzare una delle problematiche tipiche della supply chain: l'analisi della qualità dei fornitori. Questa analisi si basa su due metriche principali: numero totale di difetti e tempo totale di inattività causato da tali difetti. 

Questo esempio ha due obiettivi principali:

* Individuare i migliori e i peggiori fornitori in termini di qualità.
* Identificare gli stabilimenti che presentano le prestazioni migliori e il minor tempo di inattività nelle operazioni di individuazione e scarto di prodotti difettosi.

![Dashboard per l'esempio di analisi della qualità dei fornitori](media/sample-supplier-quality/supplier1.png)

Questo esempio fa parte di una serie che illustra come usare Power BI con dati, report e dashboard orientati al business. L'esempio è stato creato con dati reali di [obviEnce](http://www.obvience.com/), che sono stati resi anonimi. I dati sono disponibili in diversi formati: pacchetto di contenuto, file di Power BI Desktop con estensione pbix o cartella di lavoro di Excel. Vedere [Esempi per Power BI](sample-datasets.md). 

Questa esercitazione illustra il pacchetto di contenuto relativo all'esempio di analisi della qualità dei fornitori nel servizio Power BI. Dato che l'esperienza per i report è simile in Power BI Desktop e nel servizio, è anche possibile seguire le descrizioni usando il file con estensione pbix dell'esempio in Power BI Desktop. 

Non occorre una licenza di Power BI per esplorare gli esempi in Power BI Desktop. Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale nel servizio Power BI. 

## <a name="get-the-sample"></a>Ottenere l'esempio

Prima di poter usare l'esempio, è necessario scaricarlo come [pacchetto di contenuto](#get-the-content-pack-for-this-sample), [file con estensione pbix](#get-the-pbix-file-for-this-sample) o [cartella di lavoro di Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Scaricare il pacchetto di contenuto per questo esempio

1. Aprire il servizio Power BI (app.powerbi.com), eseguire l'accesso e aprire l'area di lavoro in cui salvare l'esempio.

   Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale.

2. Nell'angolo in basso a sinistra selezionare **Recupera dati**.
   
   ![Selezionare Recupera dati](media/sample-datasets/power-bi-get-data.png)
3. Nella pagina **Recupera dati** che viene visualizzata selezionare **Esempi**.
   
4. Selezionare **Esempio di analisi della qualità dei fornitori** e quindi scegliere **Connetti**.  
   
   ![Connettersi all'esempio](media/sample-supplier-quality/supplier16.png)

5. Power BI importa il pacchetto di contenuto e quindi aggiunge un nuovo dashboard, report e set di dati all'area di lavoro corrente.
   
   ![Voce relativa all'esempio di analisi della qualità dei fornitori](media/sample-supplier-quality/supplier17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Scaricare il file con estensione pbix per questo esempio

In alternativa, è possibile scaricare l'esempio di analisi della qualità dei fornitori come [file con estensione pbix](http://download.microsoft.com/download/8/C/6/8C661638-C102-4C04-992E-9EA56A5D319B/Supplier-Quality-Analysis-Sample-PBIX.pbix), progettato per l'uso con Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Scaricare la cartella di lavoro di Excel per questo esempio

Se si vuole visualizzare l'origine dati per questo esempio, è disponibile anche come [cartella di lavoro di Excel](http://go.microsoft.com/fwlink/?LinkId=529779). La cartella di lavoro contiene fogli di Power View che è possibile visualizzare e modificare. Per vedere i dati non elaborati, abilitare i componenti aggiuntivi di Analisi dati, quindi selezionare **Power Pivot > Gestisci**. Per abilitare i componenti aggiuntivi Power View e Power Pivot, vedere [Esaminare gli esempi di Excel direttamente da Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) per informazioni dettagliate.

## <a name="downtime-caused-by-defective-materials"></a>Tempo di inattività causato da materiali difettosi
In questa sezione viene analizzato il tempo di inattività causato da materiali difettosi e vengono individuati i fornitori responsabili.  

1. Nel dashboard selezionare il riquadro **Total Defect Quantity** o **Total Downtime Minutes**.

   ![Selezionare il riquadro per aprire il report](media/sample-supplier-quality/supplier2.png)  

   Il report per l'esempio di analisi della qualità dei fornitori si apre alla pagina **Downtime Analysis**.

   Si noti che sono presenti 33 milioni di pezzi difettosi, che causano un tempo di inattività totale di 77.000 minuti. Anche se alcuni materiali presentano un numero minore di pezzi difettosi, possono causare ritardi e, di conseguenza, un maggior tempo di inattività. Nella pagina del report è possibile analizzarli in dettaglio.  
2. Se si osserva la riga **Total Downtime Minutes** nel grafico combinato **Defects and Downtime (min) by Material Type**, è possibile notare che la maggior parte del tempo di inattività dipende dai materiali corrugati.  
3. Selezionare la colonna **Corrugate** per vedere quali stabilimenti subiscono l'impatto maggiore a causa di questo difetto e qual è il fornitore responsabile.  

   ![Selezionare la colonna Corrugate](media/sample-supplier-quality/supplier3.png)  
4. Nella mappa **Downtime (min) by Plant** selezionare i singoli stabilimenti a turno per vedere il fornitore o il materiale responsabile del tempo di inattività nello stabilimento.

### <a name="which-are-the-worst-suppliers"></a>Quali sono i fornitori peggiori?
 Si vuole trovare gli otto fornitori peggiori e determinare la percentuale di tempo di inattività di cui essi sono responsabili. A tale scopo, è possibile modificare il grafico ad area **Downtime (min) by Vendor** in grafico ad albero.  

1. Nella pagina **Downtime Analysis** del report selezionare **Modifica report** nell'angolo in alto a sinistra.  
2. Selezionare il grafico ad area **Downtime (min) by Vendor** e nel riquadro **Visualizzazioni** selezionare l'icona **Mappa ad albero**.  

   ![Selezionare l'icona del grafico ad albero](media/sample-supplier-quality/supplier4.png)  

    Il grafico ad albero imposta automaticamente il campo **Vendor** come **Group**.  

    ![Grafico ad albero Downtime (min) by Vendor](media/sample-supplier-quality/supplier5.png)  

   Da questo grafico ad albero si vede che gli otto fornitori principali corrispondono agli otto blocchi a sinistra del grafico. Si osserva anche che sono responsabili di circa il 50% del tempo di inattività complessivo.  
3. Selezionare **Esempio di analisi della qualità dei fornitori** nella barra di spostamento superiore per tornare al dashboard.

### <a name="comparing-plants"></a>Confronto tra stabilimenti
In questa sezione viene identificato lo stabilimento che offre le prestazioni migliori in termini di gestione dei materiali difettosi e che, di conseguenza, presenta un minor tempo di inattività.  

1. Nel dashboard selezionare il riquadro della mappa **Total Defect Reports by Plant, Defect Type**.      

   ![Riquadro Total Defect Reports by Plant, Defect Type](media/sample-supplier-quality/supplier6.png)  

   Verrà aperta la pagina **Supplier Quality Analysis** del report.  

2. Nella legenda di **Total Defect Reports by Plant and Defect Type** selezionare il cerchio **Impact**.  

    ![Selezionare Impact](media/sample-supplier-quality/supplier7.png)  

    Si noti nel grafico a bolle che **Logistics** è la categoria che presenta più problemi. Questa categoria presenta i valori maggiori in termini di quantità di difetti totali, segnalazioni di difetti e tempo di inattività in minuti. Di seguito vengono illustrati i dettagli della categoria.  
3. Selezionare la bolla **Logistics** nel grafico a bolle e osservare gli stabilimenti di Springfield e Naperville, IL. Naperville sembra ottenere risultati migliori nella gestione dei materiali difettosi perché ha un alto numero di scarti, ma un impatto ridotto rispetto a Springfield.  

   ![Selezionare Logistics](media/sample-supplier-quality/supplier8.png)  
4. Selezionare **Esempio di analisi della qualità dei fornitori** nella barra di spostamento superiore per tornare al dashboard.

## <a name="which-material-type-is-best-managed"></a>Quale tipo di materiale viene gestito meglio?
Il tipo di materiale che consente una gestione migliore è quello con il tempo di inattività minore o privo di impatti, indipendentemente dalla quantità di difetti.

1. Osservare il riquadro **Total Defect Quantity by Material Type, Defect Type** nel dashboard.

   ![Riquadro Total Defect Quantity by Material Type, Defect Type](media/sample-supplier-quality/supplier9.png)

   Si noti che sebbene il tipo di materiale **Raw Materials** presenti un elevato numero di difetti totali, la maggior parte di essi è stata rifiutata o non ha alcun impatto.

   Osservare che questo tipo di materiale non causa molto tempo di inattività, nonostante la presenza di notevoli quantità di difetti.

2. Osservare il riquadro **Total Defect Qty, Total Downtime Minutes by Material Type** nel dashboard.

   ![Riquadro Total Defect Qty, Total Downtime Minutes by Material Type](media/sample-supplier-quality/supplier10.png)

   Le materie prime in apparenza sono gestite in modo efficace: hanno più difetti, ma comportano un minor tempo di inattività in minuti.

### <a name="compare-defects-to-downtime-by-year"></a>Confrontare i difetti e il tempo di inattività per anno
1. Selezionare il riquadro della mappa **Total Defect Reports by Plant, Defect Type** per aprire la pagina **Supplier Quality Analysis** del report.
2. Nel grafico **Total Defect Qty by Month and Year** osservare che la quantità di difetti è maggiore nel 2014 rispetto al 2013.  

    ![Grafico Total Defect Qty by Month and Year](media/sample-supplier-quality/supplier11.png)  
3. La presenza di più difetti si traduce in un tempo di inattività maggiore? Porre domande nella casella Domande e risposte per ottenere le informazioni desiderate.  
4. Selezionare **Esempio di analisi della qualità dei fornitori** nella barra di spostamento superiore per tornare al dashboard.  
5. Poiché si sa che le materie prime hanno il numero di difetti più alto, digitare *show material types, year and total defect qty* nella casella della domanda.  

    I difetti delle materie prime erano molto più numerosi nel 2014 rispetto al 2013.  

    ![Domanda di Domande e risposte: show material types, year, and total defect qty](media/sample-supplier-quality/supplier12.png)  
6. Cambiare quindi la domanda in: _show material types, year, and total **downtime minutes**_ .  

   ![Domanda di Domande e risposte: show material types, year, and total downtime minutes](media/sample-supplier-quality/supplier13.png)

   Si noti che il tempo di inattività per le materie prime era più o meno equivalente nel 2013 e nel 2014, anche se nel 2014 erano presenti molti più difetti. Per l'anno 2014 il maggior numero di difetti delle materie prime non ha comportato un aumento del tempo di inattività.

### <a name="compare-defects-to-downtime-month-to-month"></a>Confrontare i difetti e il tempo di inattività mese per mese
Ora viene analizzato un altro riquadro del dashboard relativo alla quantità difettosa totale.  

1. Selezionare **Chiudi Domande e risposte** nell'angolo in alto a sinistra per tornare al dashboard.  

    Esaminare in modo più accurato il riquadro **Total Defect Quantity by Month, Year**. Si può notare che nella prima metà del 2014 il numero di difetti era simile al 2013, mentre ha subito un notevole incremento nella seconda metà del 2014.  

    ![Riquadro Total Defect Quantity by Month, Year](media/sample-supplier-quality/supplier14.png)  

    L'aumento della quantità di difetti porta a un incremento equivalente del tempo di inattività?  
2. Nella casella della domanda digitare *total downtime minutes by month and year as a line chart*.  

   ![Domanda di Domande e risposte: total downtime minutes by month and year as a line chart](media/sample-supplier-quality/supplier15.png)

   A parte l'aumento del tempo di inattività durante i mesi di giugno e ottobre, il numero di difetti non ha causato tempo di inattività significativamente maggiore. Il risultato indica che i difetti vengono gestiti in modo efficace.  
3. Per aggiungere il grafico al dashboard, selezionare l'icona della puntina ![Icona Aggiungi](media/sample-supplier-quality/pin.png) sopra la casella della domanda.  
4. Per esaminare i mesi con valori outlier, analizzare il tempo di inattività in minuti durante il mese di ottobre per tipo di materiale, località dello stabilimento, categoria e così via ponendo domande come *total downtime minutes in October by plant*. 
5. Selezionare **Chiudi Domande e risposte** nell'angolo in alto a sinistra per tornare al dashboard.

## <a name="next-steps-connect-to-your-data"></a>Passaggi successivi: Connettersi ai dati
Questo ambiente è sicuro perché è possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere **Recupera dati** per ottenere una nuova copia di questo esempio.

La presentazione ha tentato di mostrare il modo in cui i dashboard, la casella Domande e risposte e i report di Power BI possono fornire analisi approfondite dei dati di esempio. È ora possibile iniziare e connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione al servizio Power BI](service-get-started.md).
