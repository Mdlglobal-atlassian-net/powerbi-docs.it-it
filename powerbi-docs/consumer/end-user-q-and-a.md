---
title: Domande e risposte per i consumer di Power BI
description: Panoramica della documentazione per le query in linguaggio naturale Domande e risposte di Power BI.
author: mihart
ms.reviewer: mohammad ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: cc20d981e1e774eed109c614e146415ec3813601
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709789"
---
# <a name="qa-for-power-bi-consumers"></a>Domande e risposte per i consumer di Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-qa"></a>Che cosa sono le domande e risposte?
A volte il modo più rapido per ottenere una risposta dai dati consiste nel porre una domanda usando il linguaggio naturale. ad esempio "a quanto ammontano le vendite totali dello scorso anno".

Domande e risposte consente di esplorare i dati tramite funzionalità intuitive basate sul linguaggio naturale e di ricevere le risposte sotto forma di grafici. Domande e risposte è diverso da un motore di ricerca in quanto consente di ottenere risultati relativi solo ai dati in Power BI.

## <a name="which-visualization-does-qa-use"></a>Quali visualizzazioni usa Domande e risposte?
Domande e risposte sceglie la visualizzazione ottimale in base ai dati da visualizzare. Talvolta per i dati nel set di dati sottostante sono specificati il tipo o la categoria e questo aiuta Domande e risposte a decidere come visualizzarli. Se ad esempio i dati sono definiti come tipo data, è più probabile che vengano visualizzati come grafico a linee. Per i dati classificati come città è invece più probabile che venga usata la visualizzazione mappa.

È anche possibile specificare quale oggetto visivo si vuole usare aggiungendolo alla domanda. Tenere comunque presente che non sempre Domande e risposte è in grado di visualizzare i dati usando il tipo di oggetto visivo richiesto. Domande e risposte fornisce un elenco di tipi di oggetti visivi utilizzabili.

## <a name="where-can-i-use-qa"></a>Dove è possibile usare Domande e risposte?
Domande e risposte è disponibile nei dashboard del servizio Power BI e nella parte inferiore del dashboard in Power BI per dispositivi mobili. Se il designer non concede all'utente le autorizzazioni di modifica, è possibile usare Domande e risposte per esplorare i dati, ma non sarà possibile salvare le visualizzazioni create con Domande e risposte.

![Casella delle domande](media/end-user-q-and-a/powerbi-qna.png)

È anche possibile trovare Domande e risposte nei report, se il *designer* del report ha aggiunto un [oggetto visivo Domande e risposte](../visuals/power-bi-visualization-q-and-a.md).   

![Oggetto visivo Domande e risposte](media/end-user-q-and-a/power-bi-q-and-a-default.png)

## <a name="qa-on-dashboards"></a>Domande e risposte nei dashboard

**Domande e risposte di Power BI** è disponibile con una licenza Pro o Premium.  Gli argomenti relativi a [Domande e risposte nelle app Power BI per dispositivi mobili](mobile/mobile-apps-ios-qna.md) e [Domande e risposte con Power BI Embedded](../developer/qanda.md) vengono illustrati in articoli separati. Attualmente, **Domande e risposte di Power BI** supporta solo le risposte alle query in linguaggio naturale espresse in inglese, anche se è disponibile un'anteprima per lo spagnolo che può essere abilitata dall'amministratore di Power BI.


![Mappa ad albero creata con Domande e risposte](media/end-user-q-and-a/power-bi-treemap.png)

Porre la domanda è solo l'inizio.  È possibile spostarsi tra i dati perfezionando o espandendo la domanda, scoprendo nuove informazioni preziose e usando le caratteristiche di zoom avanti o indietro per visualizzare rispettivamente i dettagli o una vista più ampia. Le informazioni approfondite che si possono individuare sono di qualità eccezionale.

L'esperienza è completamente interattiva... e veloce. Basata su un sistema di archiviazione in memoria, la risposta è quasi istantanea.


## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>Usare Domande e risposte in un dashboard nel servizio Power BI
Nel servizio Power BI (app.powerbi.com) un dashboard contiene riquadri aggiunti da uno o più set di dati ed è quindi possibile porre domande su tutti i dati inclusi in questi set di dati. Per visualizzare i report e i set di dati usati per creare il dashboard, selezionare **Visualizza elementi correlati** dall'elenco a discesa **Altre azioni**.

![Visualizza elementi correlati dalla barra dei menu](media/end-user-q-and-a/power-bi-q-and-a-view-related.png)

## <a name="how-do-i-start"></a>Come iniziare?
Prima di tutto è importante acquisire familiarità con il contenuto. Esaminare gli oggetti visivi nel dashboard e nel report. Farsi un'idea del tipo e della gamma di dati disponibili per l'utente. 

ad esempio:

* Se le etichette dell'asse e i valori di un oggetto visivo includono "vendite", "account", "mese" e "opportunità", è possibile porre tranquillamente domande come questa: "Quale *account* ha la massima *opportunità*" oppure "Mostra le *vendite* per mese come grafico a barre".

* Se si hanno dati relativi alle prestazioni del sito Web in Google Analytics, è possibile chiedere a Domande e risposte di indicare il tempo trascorso su una pagina Web, il numero di visite singole in una pagina e i tassi di coinvolgimento degli utenti. Se invece si cercano dati demografici, è possibile porre domande sull'età e sul reddito familiare per luogo.

Una volta acquisita familiarità con i dati, tornare al dashboard e posizionare il cursore nella casella delle domande. Viene aperta la schermata Domande e risposte.

![Schermata Domande e risposte](media/end-user-q-and-a/power-bi-suggested.png) 

Ancora prima di iniziare a digitare, Domande e risposte mostra una nuova schermata con suggerimenti utili a formulare la domanda. Verranno visualizzate frasi e domande contenenti i nomi delle tabelle nei set di dati sottostanti e, in alcuni casi, domande *in primo piano* create dal proprietario del set di dati.

È possibile selezionarne una qualsiasi per aggiungerla alla casella delle domande e perfezionarla per trovare una risposta specifica. 

![Schermata Domande e risposte](media/end-user-q-and-a/power-bi-result.png) 

Power BI aiuta a porre le domande anche tramite funzionalità come le richieste di conferma, il completamento automatico e i suggerimenti visivi. Fornisce questo aiuto per Domande e risposte nei dashboard e nei report e con l'oggetto visivo Domande e risposte. Queste funzionalità sono illustrate in dettaglio più avanti, nella sezione [Creare un oggetto visivo Domande e risposte digitando una query in linguaggio naturale](#create-a-qa-visual-by-typing-a-natural-language-query)

<!-- ![video](../visuals/media/end-user-q-and-a/qna4.gif) -->


## <a name="the-qa-visual-in-power-bi-reports"></a>Oggetto visivo Domande e risposte nei report di Power BI

L'oggetto visivo Domande e risposte consente di porre domande in linguaggio naturale e ottenere risposte sotto forma di oggetti visivi. Dal momento che si comporta come qualsiasi altro oggetto visivo in un report, all'oggetto visivo Domande e risposte può essere applicato il filtro incrociato o l'evidenziazione incrociata, oltre a essere supportati anche i segnalibri e i commenti. 

Un oggetto visivo Domande e risposte è identificabile in base alla casella delle domande visualizzata nella parte superiore, in cui è possibile immettere domande usando il linguaggio naturale. L'oggetto visivo Domande e risposte può essere usato più volte per porre domande sui dati. Quando si esce dal report, viene reimpostato l'oggetto visivo Domande e risposte predefinito. 

![Screenshot dell'oggetto visivo Domande e risposte predefinito](media/end-user-q-and-a/power-bi-q-and-a-default.png)


## <a name="use-qa"></a>Usare Domande e risposte 
Per usare Domande e risposte in un dashboard o per usare l'oggetto visivo Domande e risposte in un report, selezionare una delle domande suggerite o digitare una propria domanda in linguaggio naturale. 

### <a name="create-a-qa-visual-by-using-a-suggested-question"></a>Creare un oggetto visivo Domande e risposte usando una domanda suggerita

In questo esempio è stato selezionato **top geo states by total units**. Power BI seleziona automaticamente il tipo di oggetto visivo migliore da usare. In questo caso viene selezionata una mappa.

![Mappa dell'oggetto visivo Domande e risposte](media/end-user-q-and-a/power-bi-q-and-a-suggested.png)

È anche possibile indicare a Power BI il tipo di oggetto visivo da usare aggiungendolo alla query in linguaggio naturale. Tenere presente che non tutti i tipi di oggetti visivi funzioneranno o avranno senso con i dati in uso. Questi dati, ad esempio, non producono un grafico a dispersione particolarmente utile, ma risultano più significativi sotto forma di mappa colorata.

![Oggetto visivo Domande e risposte come mappa colorata](media/end-user-q-and-a/power-bi-filled-map.png)

### <a name="create-a-qa-visual-by-typing-a-natural-language-query"></a>Creare un oggetto visivo Domande e risposte digitando una query in linguaggio naturale


Se non si è certi del tipo di domande da porre o della terminologia da usare, espandere **Mostra tutti i suggerimenti** o esaminare gli altri oggetti visivi nel report. In questo modo si acquisirà familiarità con i termini e il contenuto del set di dati.

1. Digitare la domanda nel campo di Domande e risposte usando il linguaggio naturale. Quando si digita una domanda, Power BI offre funzionalità di completamento automatico, segnali visivi e feedback.

    **Completamento automatico**: mentre si digita la domanda, Domande e risposte di Power BI mostra i suggerimenti pertinenti e contestuali che consentono di diventare rapidamente produttivi con il linguaggio naturale. Durante la digitazione si ottengono feedback e risultati immediati. L'esperienza è simile alla digitazione in un motore di ricerca.

    In questo esempio, il suggerimento che ci interessa è l'ultimo. 

    ![Domande e risposte con una parola sottolineata blu](media/end-user-q-and-a/power-bi-autocomplete.png)

    **Sottolineature rosse e blu**: Domande e risposte di Power BI mostra le parole con sottolineature per facilitare l'individuazione delle parole che Power BI non ha riconosciuto. Una sottolineatura continua di colore blu indica che Power BI ha riconosciuto la parola. L'esempio seguente mostra che Domande e risposte ha riconosciuto la parola **store**.

    ![Domande e risposte con un elenco a discesa di suggerimenti per completare la domanda](media/end-user-q-and-a/power-bi-blue.png)

    Selezionare una parola sottolineata blu per visualizzare un elenco a discesa di domande suggerite. 

    ![Elenco a discesa con suggerimenti "È anche possibile provare"](media/end-user-q-and-a/power-bi-try.png)


    Spesso quando si digita una parola in Domande e risposte, questa viene contrassegnata con una sottolineatura rossa per indicare uno di due possibili problemi. Il primo tipo di problema è classificato come scarsa attendibilità. Se si digita una parola vaga o ambigua, il campo viene sottolineato in rosso. Un esempio può essere proprio la parola "Location". Poiché più campi possono contenere la parola "Location", il sistema usa una sottolineatura rossa per chiedere di specificare di quale campo si tratta. In questo esempio Power BI chiede di selezionare il campo che si vuole usare per "VanArsdel".
    
    ![Termine sottolineato in rosso nella casella delle domande in Domande e risposte](media/end-user-q-and-a/power-bi-q-and-a-red.png)
    
    Un altro esempio di scarsa attendibilità può riguardare il caso in cui si digita la parola "area", ma la colonna corrispondente è in realtà identificata dalla parola "district". Domande e risposte di Power BI riconosce le parole che hanno lo stesso significato grazie all'integrazione con Bing e Office. In questo caso, la parola viene sottolineata in rosso per indicare all'utente che non si tratta di una corrispondenza diretta.

    ![Domande e risposte riformula la domanda usando un sinonimo](media/end-user-q-and-a/power-bi-red.png)

    Il secondo tipo di problema si verifica quando Domande e risposte non è in grado di riconoscere la parola. Un esempio è dato dall'uso della parola "geography" anche se questa non è presente nei dati. La parola è inclusa nel dizionario, ma Domande e risposte contrassegna questo termine con una sottolineatura rossa. Domande e risposte di Power BI non può creare una visualizzazione e suggerisce di chiedere al progettista del report di aggiungere il termine.

    ![Domande e risposte con il suggerimento di chiedere al progettista di aggiungere la parola geography](media/end-user-q-and-a/power-bi-geography.png)

    **Suggerimenti**: mentre si va avanti a digitare, Power BI informa che non è in grado di comprendere la domanda e tenta di aiutare l'utente. Nell'esempio riportato di seguito Power BI chiede "Si intendeva..." e suggerisce un modo diverso per formulare una domanda usando la terminologia del set di dati. 

    ![Correzioni suggerite per l'oggetto visivo Domande e risposte](media/end-user-q-and-a/power-bi-q-and-a-did-you-mean.png)

    Dopo la selezione della correzione di Power BI, i risultati vengono visualizzati come grafico a linee. 

    ![Risultati dell'oggetto visivo Domande e risposte come grafico a linee](media/end-user-q-and-a/power-bi-q-and-a-line.png)


    È tuttavia possibile modificare il grafico a linee in un altro tipo di oggetto visivo.  

    ![Oggetto visivo Domande e risposte con "come istogramma" aggiunto alla domanda](media/end-user-q-and-a/power-bi-q-and-a-specify-type.png)



## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

**Domanda**: Domande e risposte non viene visualizzato nel dashboard corrente.    
**Risposta 1**: se non viene visualizzata una casella della domanda, prima di tutto verificare le impostazioni. Per fare ciò selezionare l'icona della ruota dentata in alto a destra nella barra degli strumenti di Power BI.   
![icona della ruota dentata](media/end-user-q-and-a/power-bi-settings.png)

Quindi scegliere **Impostazioni** > **Dashboard**. Verificare che sia presente un segno di spunta accanto a **Visualizza la casella di ricerca di Domande e risposte in questo dashboard**.    
![Impostazioni di domande e risposte per il dashboard](media/end-user-q-and-a/power-bi-turn-on.png)  


**Risposta 2**: in alcuni casi non è possibile accedere alle impostazioni. Se l'amministratore o il *designer* del dashboard ha disattivato Domande e risposte, contattarli per vedere se è possibile riattivare questa funzionalità.   

**Domanda**: quando si digita una domanda, non si ottengono i risultati desiderati.    
**Risposta**: selezionare l'opzione per contattare il proprietario del report o del dashboard. È possibile eseguire questa operazione direttamente dalla pagina del dashboard di Domande e risposte o dall'oggetto visivo Domande e risposte. In alternativa, è possibile cercare il proprietario dall'intestazione di Power BI.  Il designer può adottare varie misure per migliorare i risultati di Domande e risposte. Ad esempio, il designer può rinominare le colonne del set di dati usando termini di facile comprensione (`CustomerFirstName` invece di `CustFN`). Poiché conosce particolarmente bene il set di dati, il designer può anche ideare domande utili e aggiungerle alle domande suggerite di Domande e risposte.

![Visualizzare le informazioni di contatto](media/end-user-q-and-a/power-bi-q-and-a-contact.png)

## <a name="privacy"></a>Privacy

Microsoft può usare le domande dei clienti per migliorare Power BI. Per altre informazioni, vedere l'[Informativa sulla privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="next-steps"></a>Passaggi successivi
Per informazioni sul modo in cui un oggetto visivo Domande e risposte viene creato e gestito da un *designer* di report, vedere [Tipo di oggetto visivo Domande e risposte](../visuals/power-bi-visualization-q-and-a.md).
