---
title: Presentazione dell'esempio di analisi delle vendite al dettaglio
description: Presentazione dell'esempio di analisi delle vendite al dettaglio
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: 338f45ec7aa4564dfd17678b5c5296a08c078334
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Presentazione dell'esempio di analisi delle vendite al dettaglio
## <a name="about-the-retail-analysis-sample"></a>Informazioni sull'esempio di analisi delle vendite al dettaglio
Questo dashboard di esempio del settore, unitamente al report sottostante, consentono di analizzare i dati delle vendite al dettaglio relativi ad articoli venduti in più negozi e in più zone. Grazie alle metriche è possibile confrontare le prestazioni dell'anno corrente con quelle dell'anno precedente in diverse aree, tra cui vendite, unità, profitto lordo e scostamento, oltre ad analizzare i nuovi negozi. Si tratta di dati reali messi a disposizione da obviEnce ([www.obvience.com](http://www.obvience.com)) che sono stati resi anonimi.

È anche possibile [scaricare solo il set di dati (cartella di lavoro di Excel) per questo esempio](http://go.microsoft.com/fwlink/?LinkId=529778).

![](media/sample-retail-analysis/retail1.png)

## <a name="start-on-the-dashboard-and-open-the-report"></a>Iniziare dal dashboard e aprire il report
1. Nel dashboard, selezionare il riquadro "Total Stores":
   
   ![](media/sample-retail-analysis/retail-analysis-7.png)  
   
   Verrà visualizzata la pagina "Store Sales Overview" nel report. Come si può osservare, ci sono in totale 104 negozi, 10 dei quali nuovi. Sono presenti due catene: Fashions Direct e Lindseys. In media, i negozi Fashion Direct hanno dimensioni maggiori.
2. Nel grafico a torta selezionare **Fashions Direct**.
   
   ![](media/sample-retail-analysis/retail3.png)  
   
   Osservare il risultato nel grafico a bolle:
   
   ![](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  
   
   La zona FD-01 ha la media di vendite più elevata per piede quadrato, FD-02 ha la varianza più bassa nelle vendite rispetto all'ultimo anno, FD-03 e FD-04 hanno le peggiori prestazioni complessive.
3. Fare clic su singole bolle o altri grafici per visualizzare l'evidenziazione incrociata, che rivela l'impatto delle selezioni.
4. Per tornare al dashboard, selezionarne il nome nella barra di spostamento superiore (barre di navigazione). 
   
   ![](media/sample-retail-analysis/power-bi-breadcrumbs.png)
5. Nel dashboard, selezionare il riquadro denominato "This Year's Sales" (Vendite anno in corso).
   
   ![](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)
   
   Ciò equivale a digitare "This year sales" nella casella della domanda.
   
   Verrà visualizzata la schermata seguente:
   
   ![](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Esaminare un riquadro creato con Domande e risposte di Power BI
Entriamo nello specifico.

1. Aggiungere "this year sales **by district**" (vendite dell'anno per zona) nella casella della domanda. Osservare il risultato. La risposta viene automaticamente inserita in un grafico a barre e vengono suggerite altre frasi:
   
   ![](media/sample-retail-analysis/retail8.png)
2. Modificare ora la domanda in "this year sales **by zip and chain**" (vendite dell'anno per CAP e catena).
   
   Come si può osservare, mentre si digita la domanda, si ottiene una risposta con i grafici appropriati.
3. Provare a porre altre domande e a vedere quali risultati si ottengono.
4. Al termine, tornare al dashboard.

## <a name="dive-deeper-into-the-data"></a>Esplorare i dati in dettaglio
A questo punto verrà eseguita un'analisi più dettagliata delle prestazioni delle varie zone.

1. Nel dashboard selezionare il riquadro di confronto tra le vendite dell'anno corrente e quelle dell'anno precedente.
   
   ![](media/sample-retail-analysis/pbi_sample_retanlareacht.png)
   
   Si noti l'importante variabilità della percentuale di varianza rispetto all'anno precedente, di cui gennaio, aprile e luglio sono stati mesi particolarmente scarsi.
   
   ![](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)
   
   Vediamo se è possibile circoscrivere i possibili problemi.
2. Selezionare il grafico a bolle e scegliere **020-Mens**.
   
   ![](media/sample-retail-analysis/retail11.png)  
   
   Osservare che il fatturato totale della categoria maschile non ha subito gravi ripercussioni nel mese di aprile, ma che gennaio e luglio sono stati due mesi problematici.
3. Ora, selezionare il grafico a bolle **010-Womens**.
   
   ![](media/sample-retail-analysis/retail12.png)
   
   Osservare che la categoria femminile ha avuto complessivamente prestazioni molto peggiori, quasi ogni mese rispetto all'anno precedente.
4. Selezionare di nuovo la bolla per cancellare il filtro.

## <a name="try-out-the-slicer"></a>Provare il filtro dei dati.
Esaminiamo le prestazioni di ogni specifica zona.

1. Selezionare Allan Guinot nel filtro dei dati in alto a sinistra.
   
   ![](media/sample-retail-analysis/retail13.png)
   
   Si noti che la zona di Allan Guinot ha avuto prestazioni migliori l'anno precedente nei mesi di marzo e giugno.
2. Tenendo selezionato Allan Guinot, fare clic sulla bolla Women's.
   
   ![](media/sample-retail-analysis/power-bi-allan.png)
   
   Notare che per la categoria femminile la sua zona non ha mai realizzato il volume dell'anno precedente.
3. Esplorare i manager e le categorie dell'altra zona: quali altre importanti informazioni è possibile dedurre?
4. Al termine, tornare al dashboard.

## <a name="what-is-our-data-telling-us-about-sales-growth-this-year"></a>Cosa rivelano i dati sull'incremento delle vendite di quest'anno?
L'ultima area da esplorare è la crescita, cioè i nuovi negozi aperti quest'anno.

1. Selezionare il riquadro "Stores Opened This Year".
   
   ![](media/sample-retail-analysis/retail15.png)
   
   Come è chiaro dal riquadro, quest'anno sono stati aperti più punti vendita Fashions Direct che non Lindseys.
2. Osservare il grafico 'Sales Per Sq Ft by Name':
   
   ![](media/sample-retail-analysis/retail14.png)
   
    C'è una netta differenza nel valore Average Sales per SFW tra i nuovi negozi.
3. Fare clic sull'elemento della legenda di Fashions Direct nel grafico in alto a destra. Si noti come, anche per la stessa catena, il miglior negozio (Winchester Fashions Direct) ha prestazioni migliori rispetto al negozio con prestazioni peggiori in assoluto (Cincinnati 2 Fashions Direct), e cioè rispettivamente di $21,22 e $12,86.
   
   ![](media/sample-retail-analysis/power-bi-lindseys.png)
4. Fare clic su Winchester Fashions Direct nel filtro dei dati e osservare il grafico a linee. I primi dati sulle vendite risalgono a febbraio.
5. Fare clic su Cincinnati 2 Fashions Direct nel filtro dei dati per vedere nel grafico a linee che è stato aperto a giugno e sembra essere il negozio con le prestazioni peggiori in assoluto.
6. Come in precedenza, esplorare facendo clic sulle altre barre, linee e bolle dei grafici e vedere quali informazioni è possibile ottenere.

Si tratta di un ambiente sicuro in cui operare: è sempre possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere Recupera dati per ottenere una nuova copia di questo esempio.

## <a name="next-steps-connect-to-your-data"></a>Passaggi successivi: Connettersi ai dati
La presentazione ha tentato di mostrare il modo in cui i dashboard, la casella Domande e risposte e i report di Power BI possono fornire analisi approfondite dei dati del settore della vendita al dettaglio. È ora possibile iniziare e connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione a Power BI](service-get-started.md).

## <a name="next-steps"></a>Passaggi successivi
* [Scaricare il pacchetto di contenuto dell'esempio di analisi delle vendite al dettaglio](sample-tutorial-connect-to-the-samples.md)    
* [Scaricare la cartella di lavoro di Excel per questo esempio di Power BI](http://go.microsoft.com/fwlink/?LinkId=529778)    
* [Recuperare dati per Power BI](service-get-data.md)    
* [Power BI - Concetti di base](service-basic-concepts.md)    
* Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

