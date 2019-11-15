---
title: 'Esempio di analisi delle vendite al dettaglio per Power BI: Presentazione'
description: 'Esempio di analisi delle vendite al dettaglio per Power BI: Presentazione'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 42e3a95e344e17d1ceba11911fc8aa349ebafd0c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858559"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Esempio di analisi delle vendite al dettaglio per Power BI: Presentazione

Il pacchetto di contenuto Retail Analysis Sample contiene un dashboard, un report e un set di dati che consentono di analizzare i dati di vendita al dettaglio di articoli venduti in più negozi e più zone. Grazie alle metriche è possibile confrontare le prestazioni dell'anno in corso con quelle dell'anno precedente in termini di vendite, unità, profitto lordo e scostamento, nonché analizzare i negozi. 

![Dashboard per Retail Analysis Sample](media/sample-retail-analysis/retail1.png)

Questo esempio fa parte di una serie che illustra come usare Power BI con dati, report e dashboard orientati al business. L'esempio è stato creato con dati reali di [obviEnce](http://www.obvience.com/), che sono stati resi anonimi. I dati sono disponibili in diversi formati: pacchetto di contenuto, file di Power BI Desktop con estensione pbix o cartella di lavoro di Excel. Vedere [Esempi per Power BI](sample-datasets.md). 

Questa esercitazione esplora il pacchetto di contenuto Retail Analysis Sample nel servizio Power BI. Dato che l'esperienza per i report è simile in Power BI Desktop e nel servizio, è anche possibile seguire le descrizioni usando il file con estensione pbix dell'esempio in Power BI Desktop. 

Non occorre una licenza di Power BI per esplorare gli esempi in Power BI Desktop. Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale nel servizio Power BI. 

## <a name="get-the-sample"></a>Ottenere l'esempio

 Prima di poter usare l'esempio, è necessario scaricarlo come [pacchetto di contenuto](#get-the-content-pack-for-this-sample), [file con estensione pbix](#get-the-pbix-file-for-this-sample) o [cartella di lavoro di Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Scaricare il pacchetto di contenuto per questo esempio

1. Aprire il servizio Power BI (app.powerbi.com), eseguire l'accesso e aprire l'area di lavoro in cui salvare l'esempio. 

    Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale.

2. Nell'angolo in basso a sinistra selezionare **Recupera dati**.

    ![Selezionare Recupera dati](media/sample-datasets/power-bi-get-data.png)
3. Nella pagina **Recupera dati** che viene visualizzata selezionare **Esempi**.
   
4. Selezionare **Retail Analysis Sample** e quindi scegliere **Connetti**.  
  
   ![Connettersi all'esempio](media/sample-retail-analysis/retail16.png)
   
5. Power BI importa il pacchetto di contenuto e quindi aggiunge un nuovo dashboard, report e set di dati all'area di lavoro corrente.
   
   ![Voce Retail Analysis Sample](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Scaricare il file con estensione pbix per questo esempio

In alternativa, è possibile scaricare Retail Analysis Sample come [file con estensione pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), progettato per l'uso con Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Scaricare la cartella di lavoro di Excel per questo esempio

Se si vuole visualizzare l'origine dati per questo esempio, è disponibile anche come [cartella di lavoro di Excel](https://go.microsoft.com/fwlink/?LinkId=529778). La cartella di lavoro contiene fogli di Power View che è possibile visualizzare e modificare. Per vedere i dati non elaborati, abilitare i componenti aggiuntivi di Analisi dati, quindi selezionare **Power Pivot > Gestisci**. Per abilitare i componenti aggiuntivi Power View e Power Pivot, vedere [Esaminare gli esempi di Excel direttamente da Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) per informazioni dettagliate.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Iniziare dal dashboard e aprire il report

1. Nell'area di lavoro in cui è stato salvato l'esempio, aprire la scheda **Dashboard**, quindi trovare il dashboard **Retail Analysis Sample** e selezionarlo. 
2. Nel dashboard selezionare il riquadro **Total Stores New & Existing Stores**, che viene aperto nella pagina **Store Sales Overview** nel report Retail Analysis Sample. 

   ![Riquadro Total stores (Totale negozi)](media/sample-retail-analysis/retail-analysis-7.png)  

   In questa pagina del report si può vedere che esistono in totale 104 negozi, 10 dei quali sono nuovi. Sono presenti due catene: Fashions Direct e Lindseys. In media, i negozi Fashion Direct hanno dimensioni maggiori.
3. Nel grafico a torta **This Year Sales by Chain** selezionare **Fashions Direct**.

   ![Grafico This Year Sales by Chain](media/sample-retail-analysis/retail3.png)  

   Si noti il risultato nel grafico a bolle **Total Sales Variance %** :

   ![Grafico Total Sales Variance %](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   La zona **FD-01** ha il valore medio più elevato per**Sales per Square Foot** e la zona FD-02 ha il valore più basso per **Total Sales Variance** rispetto all'anno precedente. FD-03 e FD-04 hanno le peggiori prestazioni complessive.
4. Fare clic su singole bolle o altri grafici per visualizzare l'evidenziazione incrociata, che rivela l'impatto delle selezioni.
5. Per tornare al dashboard, selezionare **Esempio di analisi delle vendite al dettaglio** nel riquadro di spostamento superiore.

   ![Barra di spostamento](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. Nel dashboard selezionare il riquadro **This Year's Sales New & Existing Stores**, operazione che equivale a digitare *This year sales* nella casella Domande e risposte.

   ![Riquadro This Year's Sales](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Vengono visualizzati i risultati di Domande e risposte:

   ![This year's sales in Domande e risposte](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Esaminare un riquadro creato con Domande e risposte di Power BI
Entriamo nello specifico.

1. Cambiare la domanda in _this year sales **by district**_ . Osservare il risultato: la risposta viene automaticamente inserita in un grafico a barre e vengono suggerite altre frasi:

   ![This year's sales by district in Domande e risposte](media/sample-retail-analysis/retail8.png)
2. Modificare ora la domanda in _this year sales **by zip and chain**_ .

   Come si può osservare, Power BI risponde alla domanda mentre si digita e visualizza il grafico appropriato.
3. Provare a porre altre domande e a vedere quali risultati si ottengono.
4. Al termine, tornare al dashboard.

## <a name="dive-deeper-into-the-data"></a>Esplorare i dati in dettaglio
A questo punto verrà eseguita un'analisi più dettagliata delle prestazioni delle varie zone.

1. Nel dashboard selezionare il riquadro **This Year's Sales, Last Year's Sales**, che apre la pagina **District Monthly Sales** del report.

   ![Riquadro This Year's Sales, Last Year's Sales](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   Nel grafico **Total Sales Variance % by Fiscal Month** si noti la notevole varianza della percentuale di scostamento rispetto all'anno precedente, con risultati particolarmente negativi per gennaio, aprile e luglio.

   ![Grafico Total Sales Variance % by Fiscal Month](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Vediamo se è possibile circoscrivere i possibili problemi.
2. Nel grafico a bolle selezionare la bolla **020-Mens**.

   ![Selezionare 020-Mens](media/sample-retail-analysis/retail11.png)  

   Osservare che anche se il fatturato totale della categoria maschile non ha subito gravi ripercussioni nel mese di aprile, gennaio e luglio sono stati comunque mesi problematici.
1. Selezionare ora la bolla **010-Womens**.

   ![Selezionare 010-Womens](media/sample-retail-analysis/retail12.png)

   Osservare che la categoria femminile ha avuto complessivamente prestazioni molto peggiori, quasi ogni mese rispetto all'anno precedente.
1. Selezionare di nuovo la bolla per cancellare il filtro.

## <a name="try-out-the-slicer"></a>Provare il filtro dei dati
Esaminiamo le prestazioni di ogni specifica zona.

1. Selezionare **Allan Guinot** nel filtro dei dati **District Manager** in alto a sinistra.

   ![Selezionare Allan Guinot](media/sample-retail-analysis/retail13.png)

   Si noti che la zona di Allan ha avuto prestazioni migliori nei mesi di marzo e giugno rispetto all'anno precedente.
2. Con **Allan Guinot** ancora selezionato, selezionare la bolla **Womens-10** nel grafico a bolle.

   ![Selezione di Allan Guinot e Womens-10](media/sample-retail-analysis/power-bi-allan.png)

   Si noti che per la categoria Womens-10, la zona di Allan non ha raggiunto il volume dell'anno precedente.
3. Esplorare i manager e le categorie dell'altra zona: quali altre importanti informazioni è possibile dedurre?
4. Al termine, tornare al dashboard.

## <a name="what-the-data-says-about-sales-growth-this-year"></a>Cosa dicono i dati sull'incremento delle vendite dell'anno in corso
L'ultima area da esplorare è la crescita, esaminando i nuovi negozi aperti quest'anno.

1. Selezionare il riquadro **Stores Opened This Year by Open Month, Chain**, che apre la pagina **New Stores Analysis** del report.

   ![Pagina New Stores Analysis](media/sample-retail-analysis/retail15.png)

   Come è evidente dal riquadro, quest'anno sono stati aperti più punti vendita Fashions Direct che non Lindseys.
2. Osservare il grafico **Sales Per Sq Ft by Name**:

   ![Grafico Sales Per Sq Ft by Name](media/sample-retail-analysis/retail14.png)

    Si noti la differenza per vendite medie/superficie per i nuovi negozi.
3. Selezionare la voce della legenda **Fashions Direct** nel grafico in alto a destra **Open Store Count by Open Month and Chain**. Si noti come, anche per la stessa catena, il miglior negozio (Winchester Fashions Direct) ha prestazioni notevolmente migliori rispetto al negozio con prestazioni peggiori (Cincinnati 2 Fashions Direct), e cioè rispettivamente di $21,22 e $12,86.

   ![Fashions Direct selezionato](media/sample-retail-analysis/power-bi-lindseys.png)
4. Selezionare **Winchester Fashions Direct** nel filtro dei dati **Name** e osservare il grafico a linee. I primi dati sulle vendite risalgono a febbraio.
5. Selezionare **Cincinnati 2 Fashions Direct** nel filtro dei dati e osservare il grafico a linee che è stato aperto a giugno e sembra essere il negozio con le prestazioni peggiori in assoluto.
6. Esplorare i dati selezionando le altre barre, linee e bolle dei grafici e vedere quali informazioni è possibile ottenere.

## <a name="next-steps-connect-to-your-data"></a>Passaggi successivi: Connettersi ai dati
Questo ambiente è sicuro perché è possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere **Recupera dati** per ottenere una nuova copia di questo esempio.

La presentazione ha tentato di mostrare il modo in cui i dashboard, la casella Domande e risposte e i report di Power BI possono fornire analisi approfondite dei dati di esempio. È ora possibile iniziare e connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione al servizio Power BI](service-get-started.md).
