---
title: Aggiungere un filtro di visualizzazione, di pagina, di drill-through o di report a un report
description: Aggiungere un filtro di pagina, di visualizzazione o di report a un report in Power BI
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
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: bd358b8e986313ba665326de0ff2722e0113554d
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="add-a-filter-to-a-power-bi-report-in-editing-view"></a>Aggiungere un filtro a un report di Power BI (in Visualizzazione di modifica)
> [!TIP]
> È consigliabile leggere prima l'articolo [Informazioni su filtri ed evidenziazione nei report di Power BI](power-bi-reports-filters-and-highlighting.md).
> 
> 

## <a name="what-is-the-difference-between-report-filters-in-editing-view-versus-reading-view"></a>Differenza tra i filtri dei report nella Visualizzazione di lettura e nella Visualizzazione di modifica
Per interagire con i report è possibile usare una di queste modalità: [Visualizzazione di lettura](service-reading-view-and-editing-view.md) e [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md).  Le funzionalità di filtro disponibili dipendono dalla modalità usata.

* Nella Visualizzazione di modifica è possibile aggiungere filtri a livello di report, pagina e oggetto visivo. I filtri vengono salvati insieme al report. Le persone che esaminano il report nella Visualizzazione di lettura possono interagire con i filtri aggiunti, ma non possono salvare le modifiche apportate.
* Nella Visualizzazione di lettura è possibile interagire con qualsiasi filtro visivo, di report e di pagina già presente nel report, ma non è consentito salvare le modifiche apportate al filtro.

> [!NOTE]
> Questo articolo descrive come creare i filtri nel report **Visualizzazione di modifica**.  Per altre informazioni sui filtri nella Visualizzazione di lettura, vedere [Interagire con un report nella Visualizzazione di lettura in Power BI](service-reading-view-and-editing-view.md).
> 
> 

## <a name="visual-filters-page-filters-drillthrough-filters-and-report-filters"></a>Filtri visivi, filtri della pagina, filtri di drill-through e filtri report
Un **filtro della pagina** si applica a tutti gli oggetti visivi nella pagina del report. Un **filtro visivo** si applica a un singolo oggetto visivo in una pagina del report. Un **filtro report** si applica a tutte le pagine del report.

![](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

## <a name="add-a-filter-to-a-specific-visualization-aka-visual-filter"></a>Aggiungere un filtro a una visualizzazione specifica (noto anche come filtro visivo)
È possibile eseguire questa operazione in due modi diversi: 

* filtrando un campo già usato dalla visualizzazione
* identificando un campo non ancora usato dalla visualizzazione e aggiungendolo direttamente al bucket **Filtri a livello di oggetto visivo**.

### <a name="by-filtering-the-fields-already-in-the-visualization"></a>Applicazione del filtro ai campi già presenti nella visualizzazione
1. Aprire il [report in Visualizzazione di modifica](service-reading-view-and-editing-view.md).
   
   ![](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. Aprire il riquadro Visualizzazioni e Filtri e il riquadro Campi (se non sono già aperti).
   
   ![](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. Selezionare un oggetto visivo per attivarlo. Tutti i campi usati dall'oggetto visivo vengono identificati ed elencati nel riquadro **Campi** ed elencati anche nel riquadro **Filtri** sotto l'intestazione **Filtri a livello di oggetto visivo**.
   
   ![](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. A questo punto verrà aggiunto un filtro a un campo già usato dalla visualizzazione. 
   
   * Scorrere verso il basso fino all'area **Filtri a livello di oggetto visivo** e scegliere la freccia per espandere il campo da filtrare. In questo esempio il filtro verrà applicato al campo **StoreNumberName**.
     
      ![](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
   * Impostare i controlli **Filtro di base** o **Filtro avanzato** o **Top N** (vedere [Come usare i filtri dei report](power-bi-how-to-report-filter.md)). In questo esempio verrà selezionato il filtro di base e verranno aggiunti segni di spunta accanto ai numeri 10, 11, 15 e 18.
     
      ![](media/power-bi-report-add-filter/power-bi-basic-filters.png) 
   * L'oggetto visivo cambia per riflettere il nuovo filtro. Se si salva il report insieme al filtro, i lettori del report possono interagire con il filtro nella Visualizzazione di lettura, selezionando o deselezionando i valori.
     
      ![](media/power-bi-report-add-filter/power-bi-filter-effect.png)
5. Alla visualizzazione verrà ora aggiunto un campo completamente nuovo come filtro a livello di oggetto visivo.
   
   * Nel riquadro Campi selezionare il campo da aggiungere come nuovo filtro a livello di oggetto visivo e trascinarlo nell'area **Filtri a livello di oggetto visivo**.  In questo esempio il campo **District Manager** verrà trascinato nel bucket **Filtri a livello di oggetto visivo** e verrà selezionato solo Andrew Ma. 
     
      ![](media/power-bi-report-add-filter/power-bi-andrew.png)
   * Si noti che **District Manager** *non* è stato aggiunto alla visualizzazione. La visualizzazione è ancora costituita dall'asse **StoreNumberName** e dal valore **This Year Sales**.  
     
      ![](media/power-bi-report-add-filter/power-bi-visualization.png)
   * La visualizzazione è inoltre filtrata in modo da visualizzare solo le vendite di Andrew per quest'anno relative ai negozi specificati.
     
     ![](media/power-bi-report-add-filter/power-bi-filtered-andrew.png)

## <a name="add-a-filter-to-an-entire-page-aka-page-view-filter"></a>Aggiungere un filtro a un'intera pagina (anche noto come filtro di visualizzazione pagina)
1. Aprire il [report in Visualizzazione di modifica](service-reading-view-and-editing-view.md).
2. Aprire il riquadro Visualizzazioni e Filtri e il riquadro Campi (se non sono già aperti).
3. Nel riquadro Campi selezionare il campo da aggiungere come nuovo filtro a livello di pagina e trascinarlo nell'area **Filtri a livello di pagina**.  
4. Selezionare i valori da filtrare e impostare i controlli **Filtro di base** o **Filtro avanzato** (vedere [Come usare i filtri dei report](power-bi-how-to-report-filter.md)).
   
   L'intera visualizzazione nella pagina interessata da questo filtro cambia in modo da rispecchiare la modifica. 
   
   ![](media/power-bi-report-add-filter/filterpage.gif)

Se si salva il report insieme al filtro, i lettori del report possono interagire con il filtro nella Visualizzazione di lettura, selezionando o deselezionando i valori.

## <a name="add-a-drillthrough-filter"></a>Aggiungere un filtro di drill-through
Con il drill-through nel servizio Power BI e in Power BI Desktop è possibile creare una pagina di report di *destinazione* incentrata su una specifica entità, ad esempio un fornitore, un cliente o un produttore. Dalle altre pagine del report gli utenti possono ora fare clic con il pulsante destro del mouse su un punto dati per tale entità ed eseguire il drill-through fino alla pagina con stato attivo.

### <a name="create-a-drillthrough-filter"></a>Creare un filtro di drill-through
Per eseguire la procedura, aprire l'esempio Redditività clienti nella visualizzazione di modifica. Si supponga di volere una pagina incentrata sulle aree commerciali Executive.   

1. Aggiungere una nuova pagina al report e denominarla **Team Executive**. Questa sarà la pagina di *destinazione* del drill-through.
2. Aggiungere visualizzazioni che tengono traccia delle metriche essenziali per le aree commerciali del team Executive.    
3. Aggiungere **Executive > Executive Name** all'area dei filtri di drill-through.    
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    Si noti che Power BI aggiunge una freccia indietro alla pagina del report.  La selezione della freccia indietro riporta gli utenti alla pagina di *origine* del report, ovvero la pagina attiva quando è stato scelto il drill-through. La freccia indietro funziona solo nella visualizzazione di lettura.
   
     ![](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>Usare il filtro di drill-through
Di seguito viene illustrato il funzionamento del filtro di drill-through.

1. Aprire la pagina **Team Scorecard** del report.    
2. Si supponga di essere Andrew Ma e di volere visualizzare la pagina del report Team Executive con un filtro che mostra solo i propri dati.  Dal grafico ad area in alto a sinistra fare clic con il pulsante destro del mouse su qualsiasi punto dati verde per aprire l'opzione di menu Drill-through.
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. Selezionare **Drill-through > Team Executive** per eseguire il drill-through fino alla pagina del report denominata **Team Executive**. La pagina viene filtrata in modo da visualizzare informazioni sul punto dati su cui è stato fatto clic con il pulsante destro del mouse, in questo caso Andrew Ma. Solo il campo nell'area Filtri di drill-through viene passato alla pagina del report di drill-through.  
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-filter-to-an-entire-report-aka-report-filter"></a>Aggiungere un filtro a un intero report (anche noto come filtro del report)
1. Aprire il [report in Visualizzazione di modifica](service-reading-view-and-editing-view.md).
2. Aprire il riquadro Visualizzazioni e Filtri e il riquadro Campi (se non sono già aperti).
3. Nel riquadro Campi selezionare il campo da aggiungere come nuovo filtro a livello di report e trascinarlo nell'area **Filtri a livello di report**.  
4. Selezionare i valori da filtrare con i controlli (vedere [Come usare i filtri dei report](power-bi-how-to-report-filter.md).

Gli oggetti visivi nella pagina attiva e in tutte le pagine del report cambiano in modo da rispecchiare il nuovo filtro. Se si salva il report insieme al filtro, i lettori del report possono interagire con il filtro nella Visualizzazione di lettura, selezionando o deselezionando i valori.

1. Selezionare la freccia indietro per tornare alla pagina precedente del report.

## <a name="troubleshooting"></a>Risoluzione dei problemi
### <a name="why-your-visual-level-filter-and-page-level-filter-may-return-different-results"></a>Motivo per cui il filtro a livello di oggetto visivo e il filtro a livello di pagina possono restituire risultati diversi
Quando si aggiunge un filtro a livello di oggetto visivo, Power BI filtra i risultati aggregati.  L'aggregazione predefinita è Sum, ma è possibile [modificare il tipo di aggregazione](service-aggregates.md).  

Quando si aggiunge un filtro di livello pagina, Power BI filtra senza l'aggregazione.  Ciò avviene perché una pagina può contenere numerosi oggetti visivi che possono utilizzare tipi diversi di aggregazione.  Pertanto, il filtro viene applicato su ogni riga di dati.

Se il riquadro Filtri non è visualizzato, verificare che sia attiva la [Visualizzazione di modifica](service-interact-with-a-report-in-editing-view.md) del report.

## <a name="next-steps"></a>Passaggi successivi
 [Come usare i filtri dei report](power-bi-how-to-report-filter.md)

  [Filtri ed evidenziazione nei report](power-bi-reports-filters-and-highlighting.md)

[Interagire con i filtri e l'evidenziazione nella Visualizzazione di lettura del report](service-reading-view-and-editing-view.md)

[Modificare il filtro incrociato e l'evidenziazione incrociata tra gli oggetti visivi nel report](service-reports-visual-interactions.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

