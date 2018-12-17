---
title: Aggiungere un filtro a un report
description: Come aggiungere un filtro a un report nel servizio Power BI per i consumer
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ea219071b475bf5bb9123e1aa3bbaca412507a8e
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280766"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Presentazione del riquadro Filtri del report
Questo articolo analizza il riquadro Filtri del report nel servizio Power BI.

Esistono diversi modi per filtrare i dati in Power BI, per questo è prima di tutto consigliabile leggere l'articolo [Informazioni su filtri ed evidenziazione](../power-bi-reports-filters-and-highlighting.md).

![report nel browser](media/end-user-report-filter/power-bi-browser.png)

## <a name="working-with-the-report-filters-pane"></a>Uso del riquadro Filtri del report
Quando un collega condivide un report, cercare il riquadro **Filtri**. In alcuni casi è compresso lungo il bordo destro del report. Selezionarlo per espanderlo.   

![report nel browser](media/end-user-report-filter/power-bi-expanded.png)

Il riquadro Filtri contiene filtri che sono stati aggiunti al report dal *responsabile della progettazione* del report. I *consumer* possono interagire con i filtri e salvare le modifiche, ma non aggiungere nuovi filtri al report. Ad esempio, nello screenshot precedente il designer ha aggiunto due filtri di livello pagina: Segment (Segmento) e Year (Anno). È possibile interagire e modificare questi filtri, ma non è possibile aggiungere un terzo filtro a livello di pagina.

Nel servizio Power BI i report conservano le modifiche apportate nel riquadro Filtri e tali modifiche vengono conservate anche nella versione del report per dispositivi mobili. Per ripristinare le impostazioni predefinite del responsabile della progettazione nel riquadro Filtri, selezionare **Ripristina impostazioni predefinite** nella barra dei menu superiore.     

## <a name="open-the-filters-pane"></a>Aprire il riquadro Filtri
Quando è aperto un report, il riquadro Filtri viene visualizzato lungo il lato destro dell'area di disegno report. Se il riquadro non è visibile, selezionare la freccia nell'angolo superiore destro per espanderlo.  

In questo esempio è stato scelto un oggetto visivo con 6 filtri. Anche la pagina del report dispone di filtri, elencati al titolo **Filtri a livello di pagina**. È disponibile un [Filtro di drill-through](../power-bi-report-add-filter.md) e anche l'intero report ha un filtro:  **FiscalYear** è 2013 o 2014.

![elenco di filtri](media/end-user-report-filter/power-bi-filter-list.png)

Se accanto ad alcuni filtri è presente la parola **All**, tutti i valori vengono inclusi nel filtro.  Ad esempio, **Chain(All)** nella schermata precedente indica che questa pagina del report include dati relativi a tutte le catene di negozi.  D'altra parte, il filtro a livello di report **FiscalYear è 2013 o 2014** indica che il report include solo i dati per gli anni fiscali 2013 e 2014.

Tutti gli utenti che visualizzeranno il report possono interagire con i filtri.

- Cercare nei filtri di pagina, visivi, di report e drill-through per trovare e selezionare il valore desiderato. 

    ![Cercare in un filtro](media/end-user-report-filter/power-bi-filter-search.png)

- Visualizzare i dettagli del filtro di passando il mouse e selezionando la freccia accanto al filtro.
  
   ![Visualizza Lindseys selezionato](media/end-user-report-filter/power-bi-expan-filter.png)
* Modificare il filtro, ad esempio cambiare **Lindseys** in **Fashions Direct**.
  
     ![Visualizza Fashions Direct selezionato](media/end-user-report-filter/power-bi-filter-chain.png)

* Reimpostare lo stato originale dei filtri selezionando **Ripristina impostazioni predefinite** nella barra dei menu superiore.    
    ![Ripristina impostazioni predefinite](media/end-user-report-filter/power-bi-reset-to-default.png)
    
* Eliminare il filtro selezionando **x** accanto al nome del filtro.
  
    ![x evidenziata](media/end-user-report-filter/power-bi-delete-filter.png)

  L'eliminazione di un filtro ne comporta la rimozione dall'elenco, ma non elimina i dati dal report.  Se ad esempio si elimina il filtro **FiscalYear è 2013 o 2014**, i dati dell'anno fiscale rimarranno nel report ma non verranno più filtrati per visualizzare solo 2013 e 2014; verranno invece visualizzati tutti gli anni fiscali presenti nei dati.  Tuttavia, dopo aver eliminato il filtro, non sarà possibile modificarlo nuovamente perché viene rimosso dall'elenco. Un'opzione migliore consiste nel cancellare il filtro selezionando l'icona della gomma ![icona della gomma](media/end-user-report-filter/power-bi-eraser-icon.png).
  
  



## <a name="clear-a-filter"></a>Eliminare un filtro
 Nella modalità di filtro avanzato o di base selezionare l'icona della gomma  ![icona della gomma](media/end-user-report-filter/pbi_erasericon.jpg) per cancellare il filtro. 


## <a name="types-of-filters-text-field-filters"></a>Tipi di filtro: filtri dei campi di testo
### <a name="list-mode"></a>Modalità elenco
Se si seleziona una casella di controllo, il valore corrispondente viene selezionato o deselezionato. Si può usare la casella di controllo **Tutto** per selezionare o deselezionare tutte le caselle di controllo. Le caselle di controllo rappresentano tutti i valori disponibili per il campo.  Man mano che si regola il filtro, la riformulazione si aggiorna in base alle scelte effettuate. 

![filtro della modalità elenco](media/end-user-report-filter/power-bi-restatement-new.png)

Si noti che a questo punto la riformulazione indica "is Mar, Apr or May" (è Mar, Apr o Mag).

### <a name="advanced-mode"></a>Modalità avanzata
Selezionare **Filtro avanzato** per passare alla modalità avanzata. Usare i controlli a discesa e le caselle di testo per identificare i campi da includere. Specificando **And** o **Or**, è possibile creare complesse espressioni di filtro. Dopo avere impostato tutti i valori desiderati, selezionare il pulsante **Applica filtro** .  

![modalità avanzata](media/end-user-report-filter/power-bi-advanced.png)

## <a name="types-of-filters-numeric-field-filters"></a>Tipi di filtro: filtri dei campi numerici
### <a name="list-mode"></a>Modalità elenco
Se i valori sono finiti, quando si seleziona il nome del campo viene visualizzato un elenco.  Per informazioni sull'uso delle caselle di controllo, vedere la sezione **Filtri dei campi di testo**&gt;**Modalità elenco riportata sopra.**   

### <a name="advanced-mode"></a>Modalità avanzata
Se i valori sono finiti o rappresentano un intervallo, quando si seleziona il nome del campo viene attivata la modalità di filtro avanzato. Usare gli elenchi a discesa e le caselle di testo per specificare un intervallo di valori da visualizzare. 

![filtro avanzato](media/end-user-report-filter/power-bi-dropdown-and-text.png)

Specificando **And** o **Or**, è possibile creare complesse espressioni di filtro. Dopo avere impostato tutti i valori desiderati, selezionare il pulsante **Applica filtro** .

## <a name="types-of-filters-date-and-time"></a>Tipi di filtro: data e ora
### <a name="list-mode"></a>Modalità elenco
Se i valori sono finiti, quando si seleziona il nome del campo viene visualizzato un elenco.  Per informazioni sull'uso delle caselle di controllo, vedere la sezione **Filtri dei campi di testo**&gt;**Modalità elenco riportata sopra.**   

### <a name="advanced-mode"></a>Modalità avanzata
Se i valori dei campi rappresentano una data o un'ora, si può specificare un'ora di inizio/fine quando si usano i filtri Data/Ora.  

![filtro data/ora](media/end-user-report-filter/pbi_date-time-filters.png)


## <a name="next-steps"></a>Passaggi successivi
[Informazioni su come e perché si applicano il filtro incrociato e l'evidenziazione incrociata agli oggetti visivi in una pagina di report](end-user-interactions.md)