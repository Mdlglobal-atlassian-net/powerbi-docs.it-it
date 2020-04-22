---
title: Analisi di impatto del set di dati
description: Visualizzare e analizzare l'impatto downstream delle modifiche apportate ai set di dati.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/13/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: d6d62583d6ef6bd1fcc1630b46bdb5d97c221f16
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81525331"
---
# <a name="dataset-impact-analysis"></a>Analisi di impatto del set di dati

Quando si apportano modifiche a un set di dati o si pensa di farlo, è importante riuscire a valutare l'impatto che tali modifiche avranno sui report e sui dashboard downstream che dipendono dal set di dati. L'**analisi di impatto del set di dati** fornisce informazioni che consentono di eseguire questa valutazione.
* Mostra quante aree di lavoro, report e dashboard potrebbero essere interessati dalla modifica e consente di passare facilmente alle aree di lavoro in cui si trovano i report e i dashboard interessati, per poter eseguire un'indagine più approfondita.
* Indica il numero di visitatori univoci e il numero di visualizzazioni presenti negli elementi potenzialmente interessati. Ciò consente di determinare l'impatto complessivo della modifica per l'elemento downstream. È probabile, ad esempio, che sia più importante analizzare l'effetto di una modifica su un report con 20.000 visualizzatori univoci che analizzare l'effetto della modifica su un report con tre visualizzatori.
* Consente di notificare in modo semplice agli utenti pertinenti una modifica apportata o che si sta pensando di apportare.

L'analisi di impatto del set di dati viene avviata facilmente dalla [visualizzazione di derivazione dei dati](service-data-lineage.md).

## <a name="identifying-shared-datasets"></a>Identificazione di set di dati condivisi

È possibile eseguire l'analisi di impatto su set di dati sia condivisi che non condivisi. È tuttavia particolarmente utile per i set di dati condivisi tra aree di lavoro, in cui ottenere un quadro chiaro delle dipendenze downstream è molto più complicato che per i set di dati non condivisi, che hanno tutte le dipendenze nella stessa area di lavoro del set di dati stesso.

Nella visualizzazione di derivazione è possibile distinguere i set di dati condivisi dai set di dati non condivisi in base all'icona visualizzata nell'angolo superiore sinistro della scheda del set di dati.

![Icone di set di dati condivisi e non condivisi](media/service-dataset-impact-analysis/shared-unshared-icon.png)

## <a name="perform-dataset-impact-analysis"></a>Eseguire l'analisi di impatto del set di dati

È possibile eseguire l'analisi di impatto su qualsiasi set di dati nell'area di lavoro, indipendentemente dal fatto che sia condiviso o meno. Non è possibile eseguire l'analisi di impatto sui set di dati esterni visibili nella visualizzazione di derivazione, ma che in realtà si trovano in un'altra area di lavoro. Per eseguire l'analisi di impatto su un set di dati esterno, è necessario passare all'area di lavoro di origine.

Per eseguire l'analisi di impatto del set di dati, fare clic sul pulsante Analisi di impatto nella scheda del set di dati.

![Pulsante Analisi di impatto del set di dati](media/service-dataset-impact-analysis/open-analysis-pane-button.png)

Verrà aperto il pannello laterale Analisi di impatto.

![Pannello laterale Analisi di impatto del set di dati](media/service-dataset-impact-analysis/service-impact-analysis-pane.png)

* Il **riepilogo dell'impatto** mostra il numero di aree di lavoro, report e dashboard potenzialmente interessati, oltre al numero totale di visualizzazioni per tutti i report e i dashboard downstream connessi al set di dati.
* Il collegamento **Notifica i contatti** apre una finestra di dialogo in cui è possibile creare un messaggio sulle modifiche apportate al set di dati e inviarlo agli elenchi di contatti delle aree di lavoro interessate. 
* La **suddivisione dell'utilizzo** mostra, per ogni area di lavoro, il numero totale di visualizzazioni per i report e i dashboard contenuti potenzialmente interessati e, per ogni report e dashboard, il numero totale di visualizzatori e visualizzazioni, dove
   * Visualizzatori: numero di utenti distinti che hanno visualizzato un report o un dashboard.
   * Viste: numero di visualizzazioni per un report o un dashboard

Le metriche di utilizzo sono relative agli ultimi 30 giorni, escluso il giorno corrente. Il conteggio include l'utilizzo ricavato dalle app correlate. Le metriche consentono di comprendere l'uso dei set di dati nel tenant, nonché di valutare l'impatto di eventuali modifiche apportate al set di dati.

## <a name="notify-contacts"></a>Inviare una notifica ai contatti

Se è stata apportata una modifica a un set di dati o si sta pensando di farlo, potrebbe essere necessario contattare gli utenti interessati per informarli. Quando si invia una notifica ai contatti, viene inviato un messaggio di posta elettronica agli [elenchi di contatti](../service-create-the-new-workspaces.md#workspace-contact-list) di tutte le aree di lavoro interessate. Il nome del mittente viene visualizzato nel messaggio di posta elettronica in modo che i contatti possano trovarlo e rispondere in un nuovo thread di posta elettronica. 

1. Fare clic su **Notifica i contatti** nel riquadro laterale Analisi di impatto. Verrà visualizzata la finestra di dialogo Notifica i contatti.

   ![Finestra di dialogo Notifica i contatti](media/service-dataset-impact-analysis/notify-contacts-dialog.png)

1. Nella casella di testo specificare alcuni dettagli sulla modifica.
1. Quando il messaggio è pronto, fare clic su **Invia**.

> [!NOTE]
> Notifica contatti non è disponibile se il set di dati su cui si esegue l'analisi di impatto si trova in un'area di lavoro classica.

## <a name="privacy"></a>Privacy

Per eseguire l'analisi di impatto su un set di dati, sono necessarie le autorizzazioni di scrittura. Nel riquadro laterale Analisi di impatto vengono visualizzati solo i nomi reali per le aree di lavoro, i report e i dashboard a cui si ha accesso. Gli elementi a cui non si è autorizzati ad accedere sono elencati come **Accesso limitato** perché i nomi di alcuni elementi possono contenere informazioni personali.

Anche se non si ha accesso ad alcune aree di lavoro, verranno comunque visualizzate le metriche di utilizzo riepilogative per tali aree di lavoro e i messaggi di notifica ai contatti raggiungeranno gli elenchi di contatti di tali aree di lavoro.

## <a name="impact-analysis-from-power-bi-desktop"></a>Analisi di impatto da Power BI Desktop

Quando si apporta una modifica a un set di dati in Power BI Desktop e quindi lo si pubblica nuovamente nel servizio Power BI, un messaggio indica il numero di aree di lavoro, report e dashboard potenzialmente interessati dalla modifica e chiede di confermare la sostituzione del set di dati attualmente pubblicato con quello modificato. Il messaggio contiene anche un collegamento all'analisi di impatto completa del set di dati nel servizio Power BI, in cui è possibile visualizzare altre informazioni ed eseguire azioni per attenuare i rischi della modifica.

![Messaggio sull'analisi di impatto del set di dati in Power BI Desktop](media/service-dataset-impact-analysis/service-dataset-impact-analysis-desktop-warning.png)

> [!NOTE]
> Le informazioni visualizzate nel messaggio indicano solo un impatto potenziale, non indicano necessariamente che si è verificato un problema. Spesso le modifiche dei set di dati non hanno effetti negativi sui report e i dashboard downstream, ma questo messaggio, che illustra chiaramente l'impatto potenziale, verrà ugualmente visualizzato.
>
>Nel messaggio il numero di aree di lavoro viene visualizzato solo se più di un'area di lavoro contiene report e dashboard interessati.

## <a name="limitations"></a>Limitazioni

* Le metriche di utilizzo non sono attualmente supportate per le aree di lavoro classiche e personali.

## <a name="next-steps"></a>Passaggi successivi

* [Introduzione ai set di dati in aree di lavoro diverse (anteprima)](../service-datasets-across-workspaces.md)
* [Derivazione dei dati](service-data-lineage.md)
