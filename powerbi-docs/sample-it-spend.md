---
title: 'Esempio di analisi della spesa IT per Power BI: Presentazione'
description: 'Esempio di analisi della spesa IT per Power BI: Presentazione'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 00effa1838327a9463671cf9be2f5764be71deb4
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404693"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Esempio di analisi della spesa IT per Power BI: Presentazione

Il pacchetto di contenuto dell'esempio di analisi della spesa IT contiene un dashboard, un report e un set di dati e consente di confrontare i costi pianificati ed effettivi di un reparto IT. Il confronto consente di valutare l'accuratezza delle pianificazioni per l'anno in corso e verificare le aree che evidenziano importanti deviazioni dalla pianificazione. La società di questo esempio prevede un ciclo di pianificazione annuale e genera una nuova ultima stima ogni trimestre per valutare le variazioni nella spesa IT nel corso dell'esercizio fiscale.

![Dashboard per l'esempio di analisi della spesa IT](media/sample-it-spend/it1.png)

Questo esempio fa parte di una serie che illustra come usare Power BI con dati, report e dashboard orientati al business. L'esempio è stato creato con dati reali di [obviEnce](http://www.obvience.com/), che sono stati resi anonimi. I dati sono disponibili in diversi formati: pacchetto di contenuto, file di Power BI Desktop con estensione pbix o cartella di lavoro di Excel. Vedere [Esempi per Power BI](sample-datasets.md). 

Questa esercitazione esplora il pacchetto di contenuto IT Spend Analysis Sample nel servizio Power BI. Dato che l'esperienza per i report è simile in Power BI Desktop e nel servizio, è anche possibile seguire le descrizioni usando il file con estensione pbix dell'esempio in Power BI Desktop. 

Non occorre una licenza di Power BI per esplorare gli esempi in Power BI Desktop. Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale nel servizio Power BI. 

## <a name="get-the-sample"></a>Ottenere l'esempio

 Prima di poter usare l'esempio, è necessario scaricarlo come [pacchetto di contenuto](#get-the-content-pack-for-this-sample), [file con estensione pbix](#get-the-pbix-file-for-this-sample) o [cartella di lavoro di Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Scaricare il pacchetto di contenuto per questo esempio

1. Aprire il servizio Power BI (app.powerbi.com), eseguire l'accesso e aprire l'area di lavoro in cui salvare l'esempio.

   Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale.

2. Nell'angolo in basso a sinistra selezionare **Recupera dati**.
   
   ![Selezionare Recupera dati](media/sample-datasets/power-bi-get-data.png)
3. Nella pagina **Recupera dati** che viene visualizzata selezionare **Esempi**.
   
4. Selezionare **Esempio di analisi della spesa IT** e quindi scegliere **Connetti**.  
  
   ![Connettersi all'esempio](media/sample-it-spend/it-connect.png)
   
5. Power BI importa il pacchetto di contenuto e quindi aggiunge un nuovo dashboard, report e set di dati all'area di lavoro corrente.
   
   ![Voce Esempio di analisi della spesa IT](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Scaricare il file con estensione pbix per questo esempio

In alternativa, è possibile scaricare l'esempio di analisi della spesa IT come [file con estensione pbix](https://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix), progettato per l'uso con Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Scaricare la cartella di lavoro di Excel per questo esempio

Se si vuole visualizzare l'origine dati per questo esempio, è disponibile anche come [cartella di lavoro di Excel](https://go.microsoft.com/fwlink/?LinkId=529783). La cartella di lavoro contiene fogli di Power View che è possibile visualizzare e modificare. Per vedere i dati non elaborati, abilitare i componenti aggiuntivi di Analisi dati, quindi selezionare **Power Pivot > Gestisci**. Per abilitare i componenti aggiuntivi Power View e Power Pivot, vedere [Esplorare gli esempi di Excel in Excel](sample-datasets.md#explore-excel-samples-inside-excel) per informazioni dettagliate.

## <a name="it-spend-analysis-sample-dashboard"></a>Dashboard di Esempio di analisi della spesa IT
I due riquadri numerici nella parte sinistra del dashboard, **Var Plan %** (% piano di varianza) e **Variance Latest Estimate % Quarter 3** (% varianza ultima stima - 3° trimestre), offrono una panoramica dell'andamento rispetto ai piani e alla stima dell'ultimo trimestre (LE3 = Latest Estimate Quarter 3). In generale, la varianza rispetto al piano è di circa il 6%. È ora necessario analizzare la causa di questa varianza e individuare quando, dove e in quale categoria si verifica.

## <a name="ytd-it-spend-trend-analysis-page"></a>Pagina YTD IT Spend Trend Analysis (Analisi della spesa IT da inizio anno)
Quando si seleziona il riquadro del dashboard **Var Plan % by Sales Region** (% piano di varianza per regione di vendita), viene visualizzata la pagina **YTD IT Spend Trend Analysis** (Analisi della spesa IT da inizio anno) del report di Esempio di analisi della spesa IT. È subito possibile osservare che esiste una varianza positiva negli Stati Uniti e in Europa e una varianza negativa in Canada, America Latina e Australia. Per gli Stati Uniti la varianza è del 6% +LE, mentre per l'Australia è del 7% -LE.

![% piano di varianza per regione di vendita](media/sample-it-spend/it2.png)

Tuttavia, osservare semplicemente il grafico e trarne delle conclusioni può essere fuorviante. È necessario esaminare gli importi in valuta effettivi per ridimensionare il tutto.

1. Selezionare **Aus and NZ** (Aus e NZ) nel grafico **Var Plan % by Sales Region** (% piano di varianza per regione di vendita) e osservare il grafico **Var Plan by IT Area** (Piano di varianza per area IT).

   ![Pagina YTD IT Spend Trend Analysis (Analisi della spesa IT da inizio anno)](media/sample-it-spend/it3.png)
2. A questo punto, selezionare **USA**. Si noti che Australia e Nuova Zelanda contribuiscono in minima parte alla spesa complessiva se confrontate con gli Stati Uniti.

    A questo punto, occorre esplorare quale categoria negli Stati Uniti è causa della varianza.

## <a name="ask-questions-of-the-data"></a>Ottenere le risposte dai dati
1. Selezionare **Esempio di analisi della spesa IT** nel riquadro di spostamento superiore per tornare al dashboard di esempio.
2. Selezionare **Porre una domanda sui dati**.
3. Dall'elenco **Domande per iniziare** a sinistra selezionare **what is the plan by IT area** (qual è il piano per area IT).

   ![Grafico Plan by IT Area (Piano per area IT)](media/sample-it-spend/it-area-chart.png)

4. Nella casella Domande e risposte eliminare la voce precedente e immettere *show IT areas, var plan % and var le3 % bar chart* (mostra grafico a barre aree IT, % piano di varianza e % var LE3).

   ![Grafico Var Plan % and Var LE3 % by IT Area (% piano di varianza e % var LE3 per area IT)](media/sample-it-spend/it4.png)

   Nella prima area IT, **Infrastructure** (Infrastruttura), si noti che la percentuale è cambiata drasticamente tra il piano di varianza iniziale e la stima più recente del piano di varianza.

## <a name="ytd-spend-by-cost-elements-page"></a>Pagina YTD Spend by Cost Elements (Spesa per elementi di costo da inizio anno)

1. Tornare al dashboard ed esaminare il riquadro **Variance Plan %, Variance Latest Estimate % - Quarter 3** (% piano di varianza, % varianza ultima stima - 3° trimestre).

   ![Riquadro Var Plan %, Var LE3 (% piano di varianza, var LE3)](media/sample-it-spend/it5.png)

   Si noti che l'area Infrastructure (Infrastruttura) risalta per la notevole varianza positiva rispetto al piano.

1. Selezionare questo riquadro per aprire il report e visualizzare la pagina **YTD Spend by Cost Elements** (Spesa per elementi di costo da inizio anno).
2. Selezionare la barra **Infrastructure** (Infrastruttura) nel grafico **Var Plan % and Var LE3 % by IT Area** (% piano di varianza e % var LE3 per area IT) in basso a destra e osservare i valori della varianza rispetto al piano nel grafico **Var Plan % by Sales Region** (% piano di varianza per regione di vendita) in basso a sinistra.

    ![Pagina YTD Spend by Cost Elements (Spesa per elementi di costo da inizio anno)](media/sample-it-spend/it6.png)
3. Selezionare un nome dopo l'altro nel filtro dei dati **Cost Element Group** (Gruppo elementi di costo) per trovare l'elemento di costo con la varianza maggiore.
4. Tenendo **Other** (Altro) selezionato, selezionare **Infrastructure** (Infrastruttura) nel filtro dei dati **IT Area** (Area IT) e selezionare le aree secondarie del filtro dei dati **IT Sub Area** (Area secondaria IT) per trovare l'area secondaria con la varianza maggiore.  

   Si noti la varianza notevole per **Networking** (Rete). Apparentemente l'azienda ha deciso di regalare ai propri dipendenti dei servizi telefonici come benefit, anche se questa iniziativa non era stata pianificata.

## <a name="plan-variance-analysis-page"></a>Pagina Plan Variance Analysis (Analisi varianza del piano)

1. Selezionare la scheda **Plan Variance Analysis** (Analisi varianza del piano) nella parte inferiore della pagina.

2. Nel grafico **Var Plan and Var Plan % by Business Area** (Piano di varianza e % piano di varianza per area commerciale) a sinistra selezionare la colonna **Infrastructure** (Infrastruttura) per evidenziare i valori dell'area commerciale dell'infrastruttura nel resto della pagina.

    ![Pagina Plan Variance Analysis (Analisi varianza del piano)](media/sample-it-spend/it7.png)

   Si noti nel grafico **Var plan % by Month and Business Area** (% piano di varianza per mese e area commerciale) che l'area commerciale dell'infrastruttura ha iniziato ad avere una varianza positiva nel mese di febbraio. Si noti anche come il valore della varianza rispetto al piano per quell'area commerciale vari in base al paese rispetto a tutte le altre aree commerciali. 

3. Usare i filtri dei dati **IT Area** (Area IT) e **IT Sub Area** (Area secondaria IT) a destra per filtrare i valori nel resto della pagina ed esplorare i dati. 

## <a name="edit-the-report"></a>Modificare il report
Selezionare **Modifica report** nell'angolo in alto a sinistra per esplorarlo in Visualizzazione di modifica:

* Osservare la conformazione delle pagine, con i campi in ogni grafico e i filtri nelle pagine.
* Aggiungere pagine e grafici basati sugli stessi dati.
* Modificare il tipo di visualizzazione per ogni grafico.
* Aggiungere i grafici di interesse al dashboard.

## <a name="next-steps-connect-to-your-data"></a>Passaggi successivi: Connettersi ai dati
Questo ambiente è sicuro perché è possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere **Recupera dati** per ottenere una nuova copia di questo esempio.

La presentazione ha tentato di mostrare il modo in cui i dashboard, la casella Domande e risposte e i report di Power BI possono fornire analisi approfondite dei dati di esempio. È ora possibile iniziare e connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione al servizio Power BI](service-get-started.md).
