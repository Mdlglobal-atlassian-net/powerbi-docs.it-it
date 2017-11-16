---
title: Come usare Domande e risposte di Power BI
description: Come usare Domande e risposte di Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: a6736916a4bb2e94c1f5e1e3c3c3e5339cf990ec
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-use-power-bi-qa"></a>Come usare Domande e risposte di Power BI
## <a name="ask-questions-of-your-data-using-natural-language"></a>Porre domande sui propri dati usando il linguaggio naturale
Iniziare in un dashboard. Nella casella della domanda in Domande e risposte è possibile digitare la domanda usando il linguaggio naturale. Domande e risposte riconosce le parole digitate e determina dove (in quale set di dati) trovare la risposta. Domande e risposte consente anche di formulare la domanda con il completamento automatico, la riformulazione e altri ausili testuali e visivi.

![](media/service-how-to-q-and-a/powerbi-qna.png)

La risposta alla domanda viene mostrata come visualizzazione interattiva e si aggiorna man mano che si modifica la domanda.

La funzionalità Domande e risposte è interattiva e persino divertente e non è raro che una domanda ne faccia sorgere molte altre via via che le visualizzazioni rivelano spunti interessanti. Il video seguente dimostra l'uso della funzionalità Domande e risposte per creare oggetti visivi, analizzarli e aggiungerli ai dashboard.

> [!NOTE]
> Domande e risposte è disponibile anche nell'[app Microsoft Power BI per iOS sui dispositivi iPad, iPhone e iPod Touch](mobile-apps-ios-qna.md).
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="use-natural-language-to-ask-questions-about-your-data"></a>Usare il linguaggio naturale per porre domande sui dati
1. Posizionare il cursore nella casella della domanda. Ancora prima di iniziare a digitare, Domande e risposte mostra una nuova schermata con suggerimenti utili a formulare la domanda.
   
   ![](media/service-how-to-q-and-a/powerbi-qna-cursor.png)  
   
   Questo elenco contiene:  
   a.  le domande usate per creare i [riquadri](service-dashboard-tiles.md) già aggiunti al dashboard e  
   b.  il nome delle tabelle nei [set di dati sottostanti](service-get-data.md).  
   
   Si può sempre scegliere una di queste domande come punto di partenza e quindi perfezionare la domanda per trovare la risposta specifica che si sta cercando. In alternativa, usare un nome di tabella per agevolare l'inserimento di una nuova domanda.
2. Selezionare una voce nell'elenco a discesa o iniziare a digitare una domanda.  
   
   ![](media/service-how-to-q-and-a/powerbi-qna-list.png)
3. Durante la digitazione di una domanda, Domande e risposte in Power BI seleziona la [visualizzazione](power-bi-visualization-types-for-reports-and-q-and-a.md) più adatta per la risposta. La visualizzazione cambia dinamicamente mentre si modifica la domanda. Domande e risposte consente anche di formulare una domanda con il completamento automatico, la riformulazione e altri ausili testuali e visivi.  
   ![](media/service-how-to-q-and-a/powerbi-qna-viz.png)
4. Quando si digita una query, Power BI cerca una risposta in qualsiasi set di dati per cui è presente un riquadro nel dashboard.  Se tutti i riquadri si riferiscono al *set di dati A*, la risposta proverrà dal *set di dati A*.  Se invece sono presenti riquadri del *set di dati A* e del *set di dati B*, Domande e risposte cerca la risposta migliore in questi due set di dati.
   
   > [!TIP]
   > Prestare attenzione se è presente un solo riquadro del *set di dati A* perché, se viene rimosso dal dashboard, Domande e risposte non avrà più accesso al *set di dati A*.
   > 
   > 
5. Quando il risultato è soddisfacente, [aggiungere la visualizzazione a un dashboard](service-dashboard-pin-tile-from-q-and-a.md) selezionando l'icona di aggiunta nell'angolo in alto a destra. Se il dashboard è stato condiviso con l'utente corrente o fa parte di un'app, non sarà possibile aggiungere la visualizzazione.
   
   ![](media/service-how-to-q-and-a/pbi_qna_finish-typing-question.jpg)

### <a name="tell-qa-which-visualization-to-use"></a>Indicare a Domande e risposte quale visualizzazione usare.
Con Domande e risposte non solo è possibile chiedere che i dati parlino da soli, ma è anche possibile specificare in che modo visualizzarli. È sufficiente aggiungere "come <visualization type>" alla fine della domanda.  ad esempio "mostra volume inventario per stabilimento come mappa" e "mostra inventario totale come scheda".  Provare in prima persona.

## <a name="how-does-qa-know-how-to-answer-questions"></a>Come fa Domande e rispondere alle domande?
### <a name="which-datasets-does-qa-use"></a>Quali set di dati usa?
Per poter rispondere a domande specifiche sui dati, Domande e risposte si basa sui nomi delle tabelle, delle colonne e dei campi calcolati presenti nel set di dati sottostante. I nomi usati dall'utente o dal proprietario del set di dati sono quindi fondamentali. 

Si supponga ad esempio di avere una tabella di Excel denominata “Vendite”, con le colonne “Prodotto”, “Mese”, “Unità vendute”, “Vendite lorde” e “Profitto”. Si possono porre domande su ognuna di queste entità.  Si può chiedere "mostra *vendite*", "totale *profitto* per *mese*", "ordina *prodotti* per *unità vendute*" e così via.

Domande e risposte è in grado di rispondere alle domande basate sull'organizzazione del set di dati. Come funzionerebbe per i dati in Salesforce? Quando ci si connette al proprio account salesforce.com, Power BI genera automaticamente un dashboard.  Prima di iniziare a porre domande con Domande e risposte, osservare i dati presenti nelle visualizzazioni del dashboard e anche quelli presenti nell'elenco a discesa di Domande e risposte.

* Se i valori e le etichette dell'asse delle visualizzazioni includono "vendite", "account", "mese" e "opportunità", è possibile porre domande come: "Quale *account* ha la massima *opportunità* oppure mostra *vendite* per mese come grafico a barre.
* Se l'elenco a discesa include "venditore", "stato" e "anno", è possibile porre domande come: "quale *venditore* ha realizzato meno *vendite* in *Florida* nel *2013*".

Se si hanno dati relativi alle prestazioni del sito Web in Google Analytics, è possibile chiedere a Domande e risposte di indicare il tempo trascorso su una pagina Web, il numero di visite singole in una pagina e i tassi di coinvolgimento degli utenti. Se invece si cercano dati demografici, è possibile porre domande sull'età e sul reddito familiare per luogo.

### <a name="which-visualization-does-qa-use"></a>Quali visualizzazioni usa Domande e risposte?
Domande e risposte sceglie la visualizzazione ottimale in base ai dati da visualizzare. Talvolta per i dati nei set di dati sottostanti sono specificati il tipo o la categoria e questo aiuta Domande e risposte a decidere come visualizzarli. Se ad esempio i dati sono definiti come tipo data, è più probabile che vengano visualizzati come grafico a linee. Per i dati classificati come città è invece più probabile che venga usata la visualizzazione mappa.

È anche possibile specificare quale visualizzazione si vuole usare aggiungendola alla domanda. Tenere comunque presente che non sempre Domande e risposte è in grado di visualizzare i dati usando il tipo di visualizzazione richiesto.

Per informazioni sulle parole chiave riconosciute da Domande e risposte, vedere [Suggerimenti per porre domande](service-q-and-a-tips.md).

## <a name="next-steps"></a>Passaggi successivi
Tornare a [Domande e risposte in Power BI](service-q-and-a.md)  
[Esercitazione: Usare Domande e risposte con l'esempio sulle vendite al dettaglio](power-bi-visualization-introduction-to-q-and-a.md)  
[Suggerimenti per porre domande in Domande e risposte](service-q-and-a-tips.md)  
[Preparare una cartella di lavoro per Domande e risposte](service-prepare-data-for-q-and-a.md)  
[Aggiungere un riquadro a un dashboard da Domande e risposte](service-dashboard-pin-tile-from-q-and-a.md)  

