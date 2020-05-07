---
title: Aggiungere un filtro a un report in Power BI
description: Aggiungere un filtro di pagina, di visualizzazione o di report a un report in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/20/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 143851013679dd0356c1ea5036c3d724b1dc436d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "73875182"
---
# <a name="add-a-filter-to-a-report-in-power-bi"></a>Aggiungere un filtro a un report in Power BI

[!INCLUDE [power-bi-service-new-look-include](includes/power-bi-service-new-look-include.md)]

Questo articolo illustra come aggiungere un filtro di pagina, di visualizzazione, di report o di drill-through a un report in Power BI. Gli esempi di questo articolo si riferiscono al servizio Power BI. I passaggi sono quasi identici in Power BI Desktop.

**Non tutti lo sanno, ma** Power BI include una nuova esperienza di filtro. Per altre informazioni, vedere [Nuova esperienza di filtro nei report di Power BI](power-bi-report-filter.md).

![Nuova esperienza di filtro](media/power-bi-report-add-filter/power-bi-filter-reading.png)

Power BI offre diversi tipi di filtri, da quello manuale a quello automatico fino ai filtri di drill-through e pass-through. Vedere le informazioni sui [diversi tipi di filtri](power-bi-report-filter-types.md).

## <a name="filters-in-editing-view-or-reading-view"></a>Filtri nella visualizzazione di modifica o nella visualizzazione di lettura
È possibile interagire con i report in due visualizzazioni diverse, ovvero di lettura e di modifica. Le funzionalità di filtro disponibili dipendono dalla visualizzazione aperta. Per i dettagli, vedere [Informazioni su filtri ed evidenziazione nei report di Power BI](power-bi-reports-filters-and-highlighting.md).

Questo articolo descrive come creare filtri nella **visualizzazione di modifica** dei report.  Per altre informazioni sui filtri nella visualizzazione di lettura, vedere [Interagire con i filtri nella visualizzazione di lettura dei report](consumer/end-user-report-filter.md).

Poiché i filtri sono *persistenti*, quando si esce dal report Power BI mantiene il filtro, il filtro dei dati e altre modifiche apportate alla visualizzazione dei dati. Quando si riapre il report è così possibile riprendere da dove ci si era interrotti. Se non si vuole mantenere le modifiche apportate ai filtri, selezionare **Ripristina impostazioni predefinite** sulla barra dei menu superiore.

![pulsante di filtri permanenti](media/power-bi-report-add-filter/power-bi-reset-to-default.png)

## <a name="levels-of-filters-in-the-filters-pane"></a>Livelli di filtri nel riquadro Filtri
Sia in Power BI Desktop che nel servizio Power BI il riquadro Filtri è visualizzato sul lato destro dell'area di disegno report. Se il riquadro Filtri non è visibile, selezionare l'icona ">" nell'angolo superiore destro per espanderlo.

È possibile impostare i filtri a tre livelli diversi per il report: filtri a livello di oggetto visivo, a livello di pagina e a livello di report. È anche possibile impostare filtri di drill-through. Questo articolo illustra i diversi livelli.

![riquadro Filtri nella visualizzazione di lettura](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

## <a name="add-a-filter-to-a-visual"></a>Aggiungere un filtro a un oggetto visivo
È possibile aggiungere un filtro a livello di oggetto visivo a un oggetto visivo specifico in due modi diversi. 

* Filtrare un campo già usato dalla visualizzazione.
* Identificare un campo non ancora usato dalla visualizzazione e aggiungerlo direttamente al bucket **Filtri a livello di oggetto visivo**.


Questa procedura usa l'esempio di analisi delle vendite al dettaglio, che è possibile scaricare per seguire i passaggi. Scaricare il pacchetto di contenuto dell'[esempio di analisi delle vendite al dettaglio](sample-retail-analysis.md#get-the-content-pack-for-this-sample).

### <a name="filter-the-fields-in-the-visual"></a>Filtrare i campi nell'oggetto visivo

1. Selezionare **Altre opzioni (...)**  > **Modifica report** per aprire il report nella visualizzazione di modifica.
   
   ![Pulsante Modifica report](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Aprire il riquadro Visualizzazioni e Filtri e il riquadro Campi (se non sono già aperti).
   
   ![Riquadri Visualizzazioni, Filtri e Campi](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. Selezionare un oggetto visivo per attivarlo. Tutti i campi usati dall'oggetto visivo sono elencati nel riquadro **Campi** e anche nel riquadro **Filtri** sotto l'intestazione **Filtri a livello di oggetto visivo**.
   
   ![Selezionare filtri a livello di oggetto visivo](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. A questo punto, verrà aggiunto un filtro a un campo già usato dalla visualizzazione. 
   
    Scorrere verso il basso fino all'area **Filtri a livello di oggetto visivo** e scegliere la freccia per espandere il campo da filtrare. In questo esempio il filtro verrà applicato a **StoreNumberName**.
     
    ![La freccia consente di espandere il filtro](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
    
    Impostare i controlli **Filtro di base**, **Filtro avanzato** o **Primi N**. In questo esempio viene eseguita una ricerca di **cha** nel filtro di base e vengono selezionati i cinque negozi trovati.
     
    ![Ricerca nel filtro di base](media/power-bi-report-add-filter/power-bi-search-filter.png) 
   
    L'oggetto visivo cambia per riflettere il nuovo filtro. Se si salva il report insieme al filtro, i lettori del report vedranno inizialmente l'oggetto visivo filtrato e potranno interagire con il filtro nella visualizzazione di lettura selezionando o deselezionando i valori.
     
    ![Oggetto visivo filtrato](media/power-bi-report-add-filter/power-bi-search-visual-filter-results.png)
    
    Quando si usa il filtro in un campo usato nell'oggetto visivo in cui il campo è aggregato (ad esempio una somma, una media o un conteggio), si filtra in base al valore *aggregato* in ogni punto dati. Se quindi si applica un filtro all'oggetto visivo in cui **This Year Sales > 500000**, nel risultato sarà presente solo il punto dati **13 - Charleston Fashion Direct**. I filtri in base alle [misure del modello](desktop-measures.md) si applicano sempre al valore aggregato del punto dati.

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>Filtrare con un campo non presente nell'oggetto visivo

Aggiungere ora un nuovo campo alla visualizzazione come filtro a livello di oggetto visivo.
   
1. Nel riquadro Campi selezionare il campo da aggiungere come nuovo filtro a livello di oggetto visivo e trascinarlo nell'area **Filtri a livello di oggetto visivo**.  In questo esempio il campo **District Manager** viene trascinato nel bucket **Filtri a livello di oggetto visivo**, viene eseguita la ricerca di **an** e vengono selezionati i tre manager trovati.
     
    ![Aggiungere un campo al riquadro Filtri](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    Si noti che **District Manager***non* è stato aggiunto alla visualizzazione. La visualizzazione è ancora costituita dall'asse **StoreNumberName** e dal valore **This Year Sales**.  
     
    ![Il campo non è nell'oggetto visivo](media/power-bi-report-add-filter/power-bi-visualization.png)

    La visualizzazione è ora filtrata in modo da mostrare solo le vendite di tali manager per l'anno in corso per i negozi specificati.
     
    ![Oggetto visivo filtrato](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    Se si salva il report insieme al filtro, i lettori del report potranno interagire con il filtro **District Manager** nella visualizzazione di lettura, selezionando o deselezionando i valori.
    
    Se si trascina una *colonna numerica* nel riquadro di filtro per creare un filtro a livello di oggetto visivo, il filtro viene applicato alle *righe di dati sottostanti*. Se, ad esempio, si aggiunge un filtro nel campo **UnitCost** e si imposta **UnitCost** > 20, verranno visualizzati solo i dati per le righe dei prodotti in cui il costo unitario è maggiore di 20, indipendentemente dal costo unitario totale per i punti dati presenti nell'oggetto visivo.

## <a name="add-a-filter-to-an-entire-page"></a>Aggiungere un filtro a un'intera pagina

È anche possibile aggiungere un filtro a livello di pagina a un'intera pagina.

1. Nel servizio Power BI aprire il report di analisi delle vendite al dettaglio e quindi passare alla pagina **District Monthly Sales**. 

2. Selezionare **...**  > **Modifica report** per aprire il report nella visualizzazione di modifica.
   
   ![Pulsante Modifica report](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. Aprire il riquadro Visualizzazioni e Filtri e il riquadro Campi (se non sono già aperti).
3. Nel riquadro Campi selezionare il campo da aggiungere come nuovo filtro a livello di pagina e trascinarlo nell'area **Filtri a livello di pagina**.  
4. Selezionare i valori da filtrare e impostare il controllo **Filtro di base** o **Filtro avanzato**.
   
   Tutte le visualizzazioni nella pagina vengono ridisegnate in modo da rispecchiare la modifica.
   
   ![Aggiungere un filtro e selezionare i valori](media/power-bi-report-add-filter/filterpage.gif)

    Se si salva il report insieme al filtro, i lettori del report potranno interagire con il filtro nella visualizzazione di lettura, selezionando o deselezionando i valori.

## <a name="add-a-drillthrough-filter"></a>Aggiungere un filtro di drill-through
Con il drill-through nel servizio Power BI e in Power BI Desktop è possibile creare una pagina di report di *destinazione* incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Dalle altre pagine del report gli utenti possono ora fare clic con il pulsante destro del mouse su un punto dati per tale entità ed eseguire il drill-through fino alla pagina con stato attivo.

### <a name="create-a-drillthrough-filter"></a>Creare un filtro di drill-through
Per seguire la procedura, scaricare l'[esempio di analisi della redditività dei clienti](sample-customer-profitability.md#get-the-content-pack-for-this-sample). Si supponga di volere una pagina incentrata sulle aree commerciali Executive.

1. Nel servizio Power BI aprire il report di analisi delle vendite al dettaglio e quindi passare alla pagina **District Monthly Sales**.

2. Selezionare **Altre opzioni (...)**  > **Modifica report** per aprire il report nella visualizzazione di modifica.
   
   ![Pulsante Modifica report](media/power-bi-report-add-filter/power-bi-edit-view.png)

1. Aggiungere una nuova pagina al report e denominarla **Team Executive**. Questa pagina sarà la *destinazione* del drill-through.
2. Aggiungere visualizzazioni che tengono traccia delle metriche essenziali per le aree commerciali del team Executive.    
3. Dalla tabella **Executives** trascinare **Executive** all'area Filtri di drill-through.    
   
    ![Aggiungere un valore ai filtri di drill-through](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    Si noti che Power BI aggiunge una freccia indietro alla pagina del report.  La selezione della freccia indietro riporta gli utenti alla pagina di *origine* del report, ovvero la pagina attiva quando è stato scelto il drill-through. Nella visualizzazione di modifica tenere premuto il tasto CTRL per selezionare la freccia indietro
   
     ![Freccia indietro](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>Usare il filtro di drill-through
Di seguito viene illustrato il funzionamento del filtro di drill-through.

1. Aprire la pagina **Team Scorecard** del report.    
2. Si supponga di essere Andrew Ma e di volere visualizzare la pagina del report Team Executive con un filtro che mostra solo i propri dati.  Dal grafico ad area in alto a sinistra fare clic con il pulsante destro del mouse su qualsiasi punto dati verde per aprire l'opzione di menu Drill-through.
   
    ![Avviare l'azione di drill-through](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. Selezionare **Drill-through > Team Executive** per eseguire il drill-through fino alla pagina del report denominata **Team Executive**. La pagina viene filtrata in modo da visualizzare informazioni sul punto dati su cui è stato fatto clic con il pulsante destro del mouse, in questo caso Andrew Ma. I filtri presenti nella pagina di origine vengono applicati alla pagina del report drill-through.  
   
    ![Selezionare l'azione di drill-through](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-report-level-filter-to-filter-an-entire-report"></a>Aggiungere un filtro a livello di report per filtrare un intero report

1. Selezionare **Modifica report** per aprire il report in visualizzazione di modifica.
   
   ![Pulsante Modifica report](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Aprire i riquadri Visualizzazioni e Filtri e Campi, se non sono già aperti.
3. Nel riquadro Campi selezionare il campo da aggiungere come nuovo filtro a livello di report e trascinarlo nell'area **Filtri a livello di report**.  
4. Selezionare i valori da filtrare.

    Gli oggetti visivi nella pagina attiva e in tutte le pagine del report cambiano in modo da rispecchiare il nuovo filtro. Se si salva il report insieme al filtro, i lettori del report potranno interagire con il filtro nella visualizzazione di lettura, selezionando o deselezionando i valori.

1. Selezionare la freccia indietro per tornare alla pagina precedente del report.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

- Se il riquadro Filtri non è visualizzato, verificare che sia attiva la [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md) del report.    
- Se sono state apportate numerose modifiche ai filtri e si vuole ripristinare le impostazioni predefinite dell'autore del report, selezionare **Ripristina impostazioni predefinite** dalla barra dei menu superiore.

## <a name="next-steps"></a>Passaggi successivi
[Presentazione del riquadro Filtri del report](consumer/end-user-report-filter.md)

[Filtri ed evidenziazione nei report](power-bi-reports-filters-and-highlighting.md)

[Tipi diversi di filtri in Power BI](power-bi-report-filter-types.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

