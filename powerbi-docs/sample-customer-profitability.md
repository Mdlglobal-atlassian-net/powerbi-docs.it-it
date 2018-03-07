---
title: "Esercitazione - Presentazione dell'esempio di analisi della redditività dei clienti per Power BI"
description: "Presentazione dell'esempio Analisi della redditività dei clienti per Power BI"
services: powerbi
documentationcenter: 
author: amandacofsky
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
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: c0aaa29a0d933da9fa61d08628766963144e0f76
ms.sourcegitcommit: c45498071d582dcca264216863906ffaae382523
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/01/2018
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Presentazione dell'esempio Analisi della redditività dei clienti per Power BI

## <a name="overview-of-the-customer-profitability-sample"></a>Panoramica dell'esempio di analisi della redditività dei clienti
Il pacchetto di contenuto "Esempio di analisi della redditività dei clienti" contiene un dashboard, un report e un set di dati per una società che produce materiali di marketing. Il dashboard è stato creato da una responsabile amministrativa per ottenere le metriche principali relative ai 5 responsabili di Business Unit, ai prodotti, ai clienti e ai margini lordi e trovare subito i fattori che influiscono negativamente sulla redditività.

![](media/sample-customer-profitability/power-bi-dash.png)

Questo esempio fa parte di una serie che illustra come usare Power BI con dati, report e dashboard orientati al business. Si tratta di dati reali messi a disposizione da obviEnce ([www.obvience.com](http://www.obvience.com/)) che sono stati resi anonimi. I dati sono disponibili in diversi formati: pacchetto di contenuto/app, cartella di lavoro di Excel o file di Power BI Desktop con estensione pbix. Vedere [Set di dati di esempio](sample-datasets.md).

## <a name="prerequisites"></a>Prerequisiti
Per iniziare, Questa esercitazione usa il servizio Power BI e il pacchetto di contenuto di esempio "Redditività clienti".  Dato che le esperienze per i report sono molto simili, è anche possibile seguire le descrizioni usando Power BI Desktop e il file PBIX di esempio. Le istruzioni per connettersi al pacchetto di contenuto e al file PBIX sono riportate di seguito.

### <a name="get-the-content-pack-for-this-sample"></a>Scaricare il pacchetto di contenuto per questo esempio

1. Aprire il servizio Power BI (app.powerbi.com) ed eseguire l'accesso.
2. Nell'angolo in basso a sinistra selezionare **Recupera dati**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Nella pagina Recupera dati che viene visualizzata selezionare l'icona **Esempi**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Selezionare l'**Esempio di analisi della redditività dei clienti**, quindi scegliere **Connetti**.  
   
   ![Recupera dati](media/sample-customer-profitability/get-supplier-sample.png)
5. Power BI importa il pacchetto di contenuto e aggiunge un nuovo dashboard, report e set di dati all'area di lavoro corrente. I nuovi contenuti sono contrassegnati con un asterisco giallo. Gli esempi sono risorse utili per provare il funzionamento di Power BI.  
   
   ![Asterisco](media/sample-customer-profitability/supplier-sample-asterisk.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Scaricare il file con estensione pbix per questo esempio

In alternativa, è possibile scaricare l'esempio come file con estensione pbix, progettato per l'uso con Power BI Desktop. [Esempio di analisi della redditività dei clienti](<http://download.microsoft.com/download/6/A/9/6A93FD6E-CBA5-40BD-B42E-4DCAE8CDD059/Customer>> Profitability Sample PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Scaricare la cartella di lavoro di Excel per questo esempio

Se si vuole esaminare più in dettaglio l'origine dati per questo esempio, è disponibile anche come [cartella di lavoro di Excel](http://go.microsoft.com/fwlink/?LinkId=529781). La cartella di lavoro contiene fogli di Power View che è possibile visualizzare e modificare. Per visualizzare i dati non elaborati, selezionare **Power Pivot > Gestisci**.


## <a name="what-is-our-dashboard-telling-us"></a>Informazioni fornite dal dashboard

In **Area di lavoro personale** trovare il dashboard per l'esempio Redditività clienti:

![Dashboard per l'esempio Redditività clienti](media/sample-customer-profitability/power-bi-dash.png)

### <a name="company-wide-dashboard-tiles"></a>Riquadri del dashboard a livello societario
1. Aprire il dashboard nel servizio Power BI. I riquadri del dashboard offrono alla responsabile amministrativa una visualizzazione delle metriche aziendali di alto livello più importanti.  Quando trova dati interessanti, può selezionare un riquadro per analizzarli in dettaglio.

2. Esaminare i riquadri sul lato sinistro del dashboard.

    ![](media/sample-customer-profitability/power-bi-manager.png)

- Il margine lordo della società è del 42,5%.
- Abbiamo 80 clienti.
- Vendiamo 5 diversi prodotti.
- La più bassa percentuale di varianza dei ricavi rispetto al budget si è avuta a febbraio, seguita dalla più alta a marzo.
- Gran parte del fatturato proviene dalle aree Est e Nord. Il margine lordo non ha mai superato il budget, richiedendo ulteriori indagini su ER-0 e MA-0.
- Il fatturato totale per l'anno in corso è vicino al budget.


### <a name="manager-specific-dashboard-tiles"></a>Riquadri del dashboard specifici del responsabile
I riquadri sul lato destro del dashboard forniscono una scorecard del team. La responsabile amministrativa deve monitorare i responsabili a lei sottoposti e questi riquadri le offrono una panoramica del profitto di alto livello, usando la percentuale di margine lordo. Se la tendenza della percentuale di margine lordo è imprevista per qualsiasi responsabile, la responsabile amministrativa potrà eseguire ulteriori indagini.

![](media/sample-customer-profitability/power-bi-manager2.png)

- Tutti i dirigenti, ad eccezione di Carlos, hanno già superato gli obiettivi di vendita. Ma le vendite effettive di Carlos sono le più alte. 
- La percentuale di margine lordo di Annelie è la più bassa, ma si osserva un aumento costante a partire da marzo.
- Valery, d'altro canto, ha visto un calo significativo della sua percentuale di margine lordo. 
- Andrew, infine, ha avuto un anno volatile. 

## <a name="explore-the-dashboards-underlying-data"></a>Esplorare i dati sottostanti del dashboard
Questo dashboard contiene riquadri collegati a un report e a una cartella di lavoro di Excel. 

### <a name="open-the-excel-online-data-source"></a>Aprire l'origine dati di Excel Online
Due riquadri in questo dashboard, "Target vs Actual" (Vendite previste ed effettive) e "Year Over Year Revenue Growth" (Crescita annuale dei ricavi) sono stati aggiunti da una cartella di lavoro di Excel. Pertanto, quando si seleziona uno di questi riquadri, Power BI apre l'origine dati, in questo caso, Excel Online.

![](media/sample-customer-profitability/power-bi-excel-online.png)

1. Selezionare uno dei riquadri aggiunti da Excel. Excel Online viene aperto all'interno del servizio Power BI.
2. Si noti che la cartella di lavoro include 3 schede di dati. Aprire "Revenue" (Ricavi).
3. Si cercherà ora di capire perché Carlos non ha ancora raggiunto gli obiettivi.  
    a. Dal dispositivo di scorrimento "Executive" (Dirigente) selezionare **Carlos Grilo**.   
    b. La prima tabella pivot indica che i ricavi di Carlos per il suo prodotto principale, Primus, sono diminuiti del 152% rispetto all'anno precedente. Il grafico di confronto degli anni indica che per la maggior parte dei mesi non raggiunge il budget.  

    ![](media/sample-customer-profitability/power-bi-pivotchart.png)

    ![](media/sample-customer-profitability/power-bi-carlos.png)

4. Continuare a esplorare e se si trova qualcosa di interessante selezionare **Aggiungi** ![](media/sample-customer-profitability/power-bi-excel-pin.png) nell'angolo in alto a destra per [aggiungerla a un dashboard](service-dashboard-pin-tile-from-excel.md).

5. Usare la freccia indietro del browser per tornare al dashboard. 

### <a name="open-the-underlying-power-bi-report"></a>Aprire il report di Power BI sottostante
La maggior parte dei riquadri nel dashboard di esempio di analisi della redditività dei clienti sono stati aggiunti dal report di esempio di analisi della redditività dei clienti sottostante. 

1. Selezionare uno di questi riquadri per aprire il report nella visualizzazione di lettura. 

2. Il report è composto da 3 pagine. Ogni scheda nella parte inferiore del report rappresenta una pagina. 

    ![](media/sample-customer-profitability/power-bi-report-tabs.png)

    * "Team Scorecard" è incentrata sulle prestazioni dei 5 responsabili e il relativo "fatturato clienti".
    * "Industry Margin Analysis" indica come analizzare la redditività rispetto all'andamento dell'intero settore.
    * "Executive Scorecard" fornisce una vista di ciascuno dei manager formattata per la visualizzazione in Cortana.

### <a name="team-scorecard-page"></a>Pagina Team Scorecard
![](media/sample-customer-profitability/customer2.png)

Verranno ora esaminati nel dettaglio due membri del team per ottenere informazioni più approfondite. Nel filtro dei dati a sinistra selezionare il nome di Andrew per filtrare la pagina del report in modo da visualizzare solo i dati su Andrew.

* Per un indicatore KPI rapido, esaminare lo stato dei ricavi di Andrew in **Revenue Status**, che è di colore verde. Andrew sta ottenendo ottimi risultati.
* Il grafico ad aree "Revenue Var % to Budget by Month" (Percentuale varianza mensile ricavi rispetto al budget) mostra che, fatta eccezione per una flessione a febbraio, nel complesso Andrew sta ottenendo risultati piuttosto buoni. La sua area dominante è l'Est, in cui gestisce 49 clienti e 5 prodotti (su 7). La sua percentuale di margine lordo non è la più elevata né la più ridotta.
* Il grafico "RevenueTY and Revenue Var % to Budget by Month" mostra un profitto costante e uniforme. Tuttavia, se si filtra il grafico facendo clic sul quadrato relativo all'area **Central** nella mappa ad albero, si scoprirà che Andrew può contare su ricavi solo a marzo e solo nello stato dell'Indiana. Si tratta di un comportamento intenzionale oppure è un fatto su cui indagare ulteriormente?

Passiamo ora a Valery. Nel filtro dei dati, selezionare il nome di Valery per filtrare la pagina del report in modo da visualizzare solo i dati sull'utente.  
![](media/sample-customer-profitability/customer3.png)

* Si noti l'indicatore KPI rosso per **RevenueTY Status**. Decisamente, è necessario indagare ulteriormente su questo elemento.
* Anche la varianza dei ricavi di Valery dipinge un quadro preoccupante: non ha raggiunto i margini di ricavo previsti.
* Valery ha solo 9 clienti, gestisce solo 2 prodotti e lavora quasi esclusivamente con i clienti nell'area nord. Questa specializzazione potrebbe spiegare le ampie fluttuazioni nelle sue metriche.
* Selezionando il quadrato **North** nella mappa ad albero si scopre che il margine lordo di Valery nell'area nord è coerente con il suo margine complessivo.
* Selezionando gli altri quadrati **Region** si apprende una storia interessante: la sua percentuale di margine lordo va dal 23% al 79% e le cifre dei ricavi, in tutte le aree tranne quella nord, sono estremamente stagionali.

Continuiamo ad andare al fondo della questione per scoprire il motivo per cui l'area di Valery non offre buoni risultati. Osservare le aree, le altre business unit e la pagina successiva del report, "Industry Margin Analysis".

### <a name="industry-margin-analysis"></a>Industry Margin Analysis
Questa pagina del report mostra una sezione diversa dei dati. Illustra il margine lordo dell'intero settore, suddiviso in base al segmento. La responsabile amministrativa usa questa pagina per confrontare le metriche della società e della business unit con le metriche del settore, per provare a capire le tendenze e la redditività. Ci si potrebbe chiedere perché il grafico ad aree "Gross Margin by Month and Executive Name" sia in questa pagina, dal momento che è specifico del team. L'inserimento in questa sede consente di filtrare la pagina in base al responsabile di business unit.  
![](media/sample-customer-profitability/customer6.png)

In che modo varia la redditività per ogni settore? In che modo sono suddivisi i prodotti e i clienti per ogni settore? Selezionare uno o più settori nella parte superiore sinistra (iniziare dal settore CPG). Per cancellare il filtro, selezionare l'icona a forma di gomma.

Nel grafico a bolle, la responsabile amministrativa cerca le bolle più grandi perché sono quelle che hanno l'impatto più significativo sui ricavi. Filtrare la pagina in base al responsabile facendo clic sui relativi nomi nel grafico ad aree facilita la visualizzazione dell'impatto di ogni responsabile in base al segmento del settore.

* L'area di influenza di Andrew attraversa molti segmenti del settore differenti, con percentuali di varianza e di margine lordo assai variabili (la maggior parte verso il lato positivo)  
* Il grafico di Annelie è simile, tranne per il fatto che lei si concentra solo su una manciata di segmenti del settore, con particolare attenzione al segmento Federal e al prodotto Gladius. 
* Carlos è chiaramente concentrato sul segmento Services, con buon profitto. Ha migliorato notevolmente la percentuale di varianza per il segmento High Tech e in un nuovo segmento, Industrial, ha prodotto risultati eccezionali rispetto al budget. 
* Tina lavora con pochi segmenti e vanta la percentuale di margine lordo più alta di tutti, ma le dimensioni in gran parte ridotte delle sue bolle mostrano che il suo impatto sul bilancio aziendale è minimo. 
* Valery, che è responsabile di un solo prodotto, lavora solo in 5 segmenti del settore. La sua influenza sul settore è stagionale, ma produce sempre una bolla di grandi dimensioni, che indica un impatto significativo sul bilancio aziendale. Il settore può spiegare i suoi risultati negativi?

### <a name="executive-scorecard"></a>Executive Scorecard
Questa pagina è formattata come una scheda di risposta per Cortana. Per altre informazioni, vedere [Creare schede di risposta per Cortana](service-cortana-answer-cards.md).

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Esaminare i dati in maniera più approfondita ponendo domande con le Domande e risposte
Per questa analisi sarebbe utile determinare quale settore genera il maggior ricavo per Valery. A tale scopo, verranno usate le Domande e risposte.

1. Aprire il report in visualizzazione di modifica selezionando **Modifica report**. La visualizzazione di modifica è disponibile solo per il proprietario del report e viene a volte definita modalità **autore**. Se si usa un report condiviso da un altro utente, invece, non sarà possibile aprirlo in visualizzazione di modifica.

2.  Dalla barra dei menu superiore selezionare **Poni una domanda** per aprire la finestra per le domande e risposte.

    ![](media/sample-customer-profitability/power-bi-ask-question.png)

3. Digitare **total revenue by industry for Valery**(ricavo totale per settore per Valery). Notare gli aggiornamenti della visualizzazione mentre si digita la domanda.
   
    ![](media/sample-customer-profitability/power-bi-qna.png)
   
   La distribuzione è la maggiore area di ricavo per Valery.

### <a name="dig-deeper-by-adding-filters"></a>Eseguire un'analisi più approfondita aggiungendo filtri
Verrà ora esaminato il settore *Distribution*.  

1. Aprire la pagina del report "Industry Margin Analysis" (Analisi del margine del settore).
2. Senza selezionare alcuna visualizzazione nella pagina del report, espandere il riquadro Filtri sulla destra, se non è già espanso. Nel riquadro Filtri dovrebbero essere visualizzati solo i filtri a livello di pagina.  
   
   ![](media/sample-customer-profitability/power-bi-filters.png)
3. Individuare il filtro per **Industry** (Settore) e selezionare la freccia per espandere l'elenco. A questo punto aggiungere un filtro di pagina per il settore Distribution (Distribuzione). Deselezionare innanzitutto tutte le opzioni selezionate, facendo clic sulla casella di controllo **Seleziona tutto**. Selezionare quindi solo **Distribution** (Distribuzione).  
   
   ![](media/sample-customer-profitability/customer7.png)
4. Il grafico ad aree "Gross margin by Month and Executive Name" indica che solo Valery e Tina hanno clienti in questo settore e che Valery ha lavorato in questo settore solo da giugno a novembre.   
5. Selezionare **Tina** e quindi **Valery** nella legenda del grafico ad aree "Gross Margin by Month and Executive". Si noti che la parte dei ricavi totali in base al prodotto di Tina (indicata in "Total Revenue by Product") è davvero minima se confrontata a quella di Valery. 
6. Per visualizzare i ricavi effettivi, usare Domande e risposte per chiedere quale è il **totale dei ricavi per dirigente e per la distribuzione in base allo scenario**.  
   
     ![](media/sample-customer-profitability/power-bi-qna2.png)

    In maniera simile, è possibile esplorare altri settori e persino aggiungere clienti agli elementi visivi per comprendere le cause delle prestazioni di Valery.

Si tratta di un ambiente sicuro in cui operare: è sempre possibile scegliere di non salvare le modifiche, ma, se le si salva, è sempre possibile scegliere **Recupera dati** per ottenere una nuova copia di questo esempio.

È anche possibile [scaricare solo il set di dati (cartella di lavoro di Excel) per questo esempio](http://go.microsoft.com/fwlink/?LinkId=529781).

## <a name="next-steps-connect-to-your-data"></a>Passaggi successivi: Connettersi ai dati
Ci auguriamo che questa presentazione abbia illustrato in che modo i dashboard di Power BI, le domande e risposte e i report forniscono informazioni dettagliate sui dati del cliente. È ora possibile connettersi ai propri dati. Con Power BI è possibile connettersi a una vasta gamma di origini dati. Per altre informazioni, vedere [Introduzione a Power BI](service-get-started.md).

[Torna a Esempi per Power BI](sample-datasets.md)  

