---
title: 'Esempio di analisi delle opportunità per Power BI: Presentazione'
description: 'Esempio di analisi delle opportunità per Power BI: Presentazione'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 4863bfe3d99a63fbf4ad49834e66ecb8fcaf5525
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80404137"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Esempio di analisi delle opportunità per Power BI: Presentazione

Il pacchetto di contenuto Opportunity Analysis Sample contiene un dashboard, un report e un set di dati per una società software con due canali di vendita: *diretto* e *partner*. Il responsabile delle vendite ha creato questo dashboard per tenere traccia delle opportunità e dei ricavi per regione, volume dell'offerta e canale.

Questo esempio si basa su due misure dei ricavi:

* Ricavi: stima di un venditore relativa ai ricavi previsti.
* Ricavi fattorizzati: calcolati moltiplicando i ricavi per la probabilità (%) e generalmente considerato un fattore di previsione più preciso per stimare i ricavi effettivi delle vendite. La probabilità viene determinata dalla *fase di vendita* corrente della trattativa:
  * Lead: 10%  
  * Qualify: 20%  
  * Soluzione: 40%  
  * Proposal: 60%  
  * Finalize: 80%

![Dashboard per Opportunity Analysis Sample](media/sample-opportunity-analysis/opportunity1.png)

Questo esempio fa parte di una serie che illustra come usare Power BI con dati, report e dashboard orientati al business. L'esempio è stato creato con dati reali di [obviEnce](http://www.obvience.com/), che sono stati resi anonimi. I dati sono disponibili in diversi formati: pacchetto di contenuto, file di Power BI Desktop con estensione pbix o cartella di lavoro di Excel. Vedere [Esempi per Power BI](sample-datasets.md). 

Questa esercitazione illustra il pacchetto di contenuto Opportunity Analysis Sample nel servizio Power BI. Dato che l'esperienza per i report è simile in Power BI Desktop e nel servizio, è anche possibile seguire le descrizioni usando il file con estensione pbix dell'esempio in Power BI Desktop. 

Non occorre una licenza di Power BI per esplorare gli esempi in Power BI Desktop. Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale nel servizio Power BI. 

## <a name="get-the-sample"></a>Ottenere l'esempio

Prima di poter usare l'esempio, è necessario scaricarlo come [pacchetto di contenuto](#get-the-content-pack-for-this-sample), [file con estensione pbix](#get-the-pbix-file-for-this-sample) o [cartella di lavoro di Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Scaricare il pacchetto di contenuto per questo esempio

1. Aprire il servizio Power BI (app.powerbi.com), eseguire l'accesso e aprire l'area di lavoro in cui salvare l'esempio. 

    Se non si ha una licenza Power BI Pro, è possibile salvare l'esempio nell'area di lavoro personale.

2. Nell'angolo in basso a sinistra selezionare **Recupera dati**.

    ![Selezionare Recupera dati](media/sample-datasets/power-bi-get-data.png)
3. Nella pagina **Recupera dati** che viene visualizzata selezionare **Esempi**.

4. Selezionare **Opportunity Analysis Sample** e quindi scegliere **Connetti**.  

   ![Connettersi all'esempio](media/sample-opportunity-analysis/opportunity-connect.png)
5. Power BI importa il pacchetto di contenuto e quindi aggiunge un nuovo dashboard, report e set di dati all'area di lavoro corrente.

   ![Voce Opportunity Analysis Sample](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Scaricare il file con estensione pbix per questo esempio

In alternativa, è possibile scaricare Opportunity Analysis Sample come [file con estensione pbix](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix), progettato per l'uso con Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Scaricare la cartella di lavoro di Excel per questo esempio

Se si vuole visualizzare l'origine dati per questo esempio, è disponibile anche come [cartella di lavoro di Excel](https://go.microsoft.com/fwlink/?LinkId=529782). La cartella di lavoro contiene fogli di Power View che è possibile visualizzare e modificare. Per vedere i dati non elaborati, abilitare i componenti aggiuntivi di Analisi dati, quindi selezionare **Power Pivot > Gestisci**. Per abilitare i componenti aggiuntivi Power View e Power Pivot, vedere [Esplorare gli esempi di Excel in Excel](sample-datasets.md#explore-excel-samples-inside-excel) per informazioni dettagliate.

## <a name="what-is-our-dashboard-telling-us"></a>Informazioni fornite dal dashboard
La responsabile delle vendite ha creato un dashboard per tenere traccia delle metriche più rilevanti. Quando vengono individuati dati interessanti, è possibile selezionare un riquadro per analizzarli in dettaglio:

- I ricavi della società ammontano a due miliardi di dollari, mentre i ricavi fattorizzati a 461 milioni.
- Il numero di opportunità e i ricavi seguono un modello a imbuto familiare, in cui i totali diminuiscono a ogni fase successiva.
- La maggior parte delle opportunità si trova nell'area orientale.
- Le opportunità di grande entità generano più ricavi rispetto a quelle di piccola o media entità.
- Le trattative di grande entità con i partner generano più ricavi: 8 milioni di dollari in media rispetto ai 6 milioni di dollari per le vendite dirette.

Dato che la quantità di lavoro richiesto per concludere una trattativa di grande, media o piccola entità è la stessa, la società dovrebbe analizzare i dati per ottenere maggiori informazioni sulle opportunità di grande entità.

1. Nell'area di lavoro in cui è stato salvato l'esempio, aprire la scheda **Dashboard**, quindi trovare il dashboard **Opportunity Analysis Sample** e selezionarlo.

2. Selezionare il riquadro **Opportunity Count by Partner Driven, Sales Stage** per aprire la prima pagina del report Opportunity Analysis Sample. 

    ![Riquadro Opportunity Count by Partner Driven, Sales Stage](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Esplorare le pagine del report

Visualizzare ogni pagina del report selezionando le schede delle pagine nella parte inferiore.

### <a name="opportunity-count-overview-page"></a>Pagina Opportunity Count Overview
![Pagina Opportunity Count](media/sample-opportunity-analysis/opportunity3.png)

Tenere presenti questi dettagli:
* L'area orientale è l'area principale in termini di numero di opportunità.  
* Nel grafico a torta **Opportunity Count by area** selezionare ogni area a turno per filtrare la pagina in base all'area. Per ogni area si noti che i partner ottengono opportunità notevolmente maggiori.   
* L'istogramma **Opportunity Count by Partner Driven and Opportunity Size** mostra che gran parte delle opportunità di grande entità sono basate sui partner, contrariamente a quelle di piccola e media entità.
* Nel grafico a barre **Opportunity Count by Sales Stage** selezionare ogni **Sales Stage** a turno per visualizzare la differenza nei numeri a livello di area. Si noti che anche se l'area orientale ha il più grande numero di opportunità, tutte le tre aree nelle fasi Solution, Proposal e Finalize mostrano numeri analoghi. Questo risultato indica una percentuale maggiore di trattative concluse nelle aree centrale e occidentale.

### <a name="revenue-analysis-page"></a>Pagina Revenue Analysis
Questa pagina offre un'analisi dei dati analoga alla precedente, ma basata sui ricavi invece che sui numeri.  

![Pagina Revenue Overview](media/sample-opportunity-analysis/opportunity4.png)

Tenere presenti questi dettagli:
* L'area orientale è l'area principale in termini di numero di opportunità, ma anche di ricavi.  
* Se si filtra il grafico **Revenue by Sales Stage and Partner Driven** selezionando **Yes** per **Partner Driven**, si vedranno ricavi di un 1,5 miliardi di dollari di ricavi e ricavi fattorizzati di 294 milioni di dollari. Confrontare questi importi con i 644 milioni di dollari e i 166 milioni di dollari per i ricavi non basati sui partner. 
* Se l'opportunità è basata sui partner, i ricavi medi per gli account di grande entità sono maggiori (8 milioni) rispetto ai 6 milioni per le opportunità non basate sui partner.  
* I ricavi medi per le opportunità di grande entità basate sui partner sono quasi il doppio rispetto a quelli per le opportunità di media entità.  
* I ricavi medi per le attività di piccola e media entità basate e non basate sui partner sono analoghi.   

Si evince che i partner hanno maggior successo nella vendita ai clienti. Pertanto, andrebbe privilegiato questo canale per la gestione delle trattative.

### <a name="opportunity-count-by-region-and-stage"></a>Opportunity Count by Region and Stage
Questa pagina del report presenta dati simili ai dati nella pagina precedente, ma suddivisi per area e fase. 

![Pagina Region Stage Counts](media/sample-opportunity-analysis/opportunity5.png)

Tenere presenti questi dettagli:
* Se si seleziona **East** nel grafico a torta **Opportunity Count by Region** per filtrare in base all'area orientale, si noterà che le opportunità in quest'area sono suddivise pressoché equamente tra quelle basate sui partner e quelle non basata sui partner.
* Le opportunità di grande entità sono più frequenti nell'area centrale, quelle di piccola entità nell'area orientale e quelle di media entità nell'area occidentale.

### <a name="upcoming-opportunities-by-month-page"></a>Pagina Upcoming Opportunities by Month
Anche in questa pagina vengono presentati fattori simili, ma con una prospettiva temporale. 
 
![Pagina Upcoming Opportunities](media/sample-opportunity-analysis/opportunity6.png)

La responsabile amministrativa usa questa pagina per gestire il carico di lavoro. Osservando le opportunità di ricavi per fase di vendita e mese, è possibile elaborare una pianificazione efficace.

Tenere presenti questi dettagli:
* I ricavi di vendita medi più alti sono quelli della fase Finalize. La chiusura di queste trattative è prioritaria.
* Se si filtra per mese (selezionando il nome del mese nel filtro dei dati **Month**), si vede che la percentuale maggiore di trattative di grande entità è concentrata nel mese di gennaio e nella fase Finalize con ricavi fattorizzati pari a 75 milioni di dollari. Il mese di febbraio ha invece il maggior numero di trattative di media entità nelle fasi Solution e Proposal.
* In generale, i numeri dei ricavi fattorizzati oscillano in base alla fase di vendita, al numero di opportunità e alle dimensioni della trattativa. Per altre informazioni approfondite, aggiungere i filtri per questi fattori usando il riquadro **Filtri** sulla destra.

## <a name="next-steps-connect-to-your-data"></a>Passaggi successivi: Connettersi ai dati
Questo ambiente è sicuro perché è possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere **Recupera dati** per ottenere una nuova copia di questo esempio.

La presentazione ha tentato di mostrare il modo in cui i dashboard, la casella Domande e risposte e i report di Power BI possono fornire analisi approfondite dei dati di esempio. È ora possibile iniziare e connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione al servizio Power BI](service-get-started.md).

