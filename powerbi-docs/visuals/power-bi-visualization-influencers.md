---
title: 'Esercitazione: Oggetto visivo Fattori di influenza chiave'
description: 'Esercitazione: Creare una visualizzazione di fattori di influenza chiave in Power BI'
author: mihart
manager: kvivek
ms.reviewer: juluczni
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 05/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8d2d6755d01a8ea9d5dad9813fcd7f4b4c1f8232
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051605"
---
# <a name="key-influencers-visualization"></a>Oggetto visivo Fattori di influenza chiave
I fattori di influenza chiave visual aiuta a comprendere i fattori una metrica si è interessati a tale unità. Analizza i dati, stila una classifica dei fattori importanti e li visualizza come fattori di influenza chiave. Ad esempio, si supponga di che voler scoprire quali influenze avvicendamento dei dipendenti, che è noto anche come varianza. Un fattore potrebbe essere lunghezza contratto occupazione, e un altro fattore potrebbe essere età dipendente. 
 
## <a name="when-to-use-key-influencers"></a>Quando utilizzare i fattori di influenza chiave 
L'oggetto visivo fattori di influenza chiave è un'ottima scelta se si desidera: 
- Vedere quali fattori influiscono sulla metrica che si sta analizzata.
- Confrontare l'importanza relativa di questi fattori. Ad esempio, i contratti a breve termine hanno un'influenza maggiore sull'abbandono dei dipendenti rispetto ai contratti a lungo termine? 

## <a name="key-influencer-requirements"></a>Requisiti per i fattori di influenza chiave 
La metrica è analizzare deve essere campi numerici o categorici (funzioni di aggregazione e le misure non sono ancora supportate).

## <a name="features-of-the-key-influencers-visual"></a>Funzionalità di fattori di influenza chiave visual

![Funzionalità numerate](media/power-bi-visualization-influencers/power-bi-ki-numbers-new.png)

1. **Schede**: Selezionare una scheda per passare dalla visualizzazione. **Fattori di influenza chiave** apprenderai i collaboratori principali per il valore della metrica selezionato. **Primi segmenti** Mostra i primi segmenti che contribuiscono al valore della metrica selezionato. Un *segmento* è costituito da una combinazione di valori. Un segmento, ad esempio, potrebbe essere utenti che sono stati i clienti per almeno 20 anni e in tempo reale nell'area occidentale. 

2. **Casella di riepilogo a discesa**: Il valore della metrica sotto indagine. In questo esempio, esaminare la metrica **Rating**. Il valore selezionato **bassa**.

3. **Riformulazione**: Consente di interpretare l'oggetto visivo nel riquadro sinistro.

4. **Riquadro a sinistra**: Il riquadro a sinistra contiene un oggetto visivo. In questo caso, il riquadro sinistro mostra un elenco dei fattori di influenza chiave superiore.

5. **Riformulazione**: Consente di interpretare l'oggetto visivo nel riquadro di destra.

6. **Riquadro di destra**: Il riquadro destro contiene un oggetto visivo. In questo caso, l'istogramma visualizza tutti i valori per la chiave influencer **tema** che è stata selezionata nel riquadro sinistro. Il valore specifico di **usabilità** nel riquadro a sinistra viene visualizzato in verde. Tutti gli altri valori per **tema** vengono visualizzati in nero.

7. **Linea Media**: Viene calcolata la media per tutti gli altri valori possibili per **tema** tranne **usabilità**. Pertanto il calcolo si applica a tutti i valori in nero. Indica la percentuale di altra **temi** ha fornito un livello di gravità basso. In altre parole, quando viene specificata una classificazione da un cliente, che il cliente descrive anche il motivo o del tema per la classificazione. Alcuni temi sono l'usabilità, velocità e sicurezza. 

   **Tema è usabilità** quello dell'influencer più alto seconda chiave per una valutazione bassa, in base all'oggetto visivo nel riquadro sinistro. Se si calcola la media tutti gli altri temi e il loro contributo a una classificazione compresa tra **bassa**, si ottiene il risultato visualizzato in rosso. Di tutti gli altri temi forniti, è superiore al solo % 11.35 **usabilità**.

8. **Casella di controllo**: **Mostra solo i valori che sono fattori di influenza**.

## <a name="create-a-key-influencers-visual"></a>Creare un oggetto visivo Fattori di influenza chiave 
 
Guardare questo video per imparare a creare un fattori di influenza chiave oggetto visivo. Attenersi alla seguente procedura per crearne uno. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/fDb5zZ3xmxU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Il Product Manager desidera di scoprire quali fattori ai clienti lead per lasciare recensioni negative sul servizio cloud. Per seguire la procedura, aprire il [file con estensione pbix di commenti e suggerimenti degli utenti](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.pbix) in Power BI Desktop. È anche possibile scaricare il [file di Excel di commenti e suggerimenti dei clienti per il servizio Power BI o Power BI Desktop](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.xlsx). 

> [!NOTE]
> Il set di dati di commenti e suggerimenti dei clienti è basato su [Moro e così via, 2014] Moro S. P. Cortez e Rita P. "Un basate sui dati approccio per stimare la riuscita della banca Telemarketing." *Decision Trees supporta i sistemi*, Elsevier, 62:22-31, giugno 2014. 

1. Aprire il report e selezionare il **fattori di influenza chiave** icona. 

    ![Nel riquadro Visualizzazioni selezionare il modello Fattori di influenza chiave](media/power-bi-visualization-influencers/power-bi-template-new.png)

2. Spostare la metrica da analizzare nel **Analyze** campo. Il **Analyze** campo supporta solo le variabili categoriche o non continua,. Per visualizzare ciò che comporta un cliente classificazione del servizio deve essere basso, selezionare **tabella Customer** > **classificazione**. 
3. Spostare i campi che si ritiene che potrebbero influire sulla **Rating** nel **spiegano da** campo. È possibile spostare tutti i campi desiderati. In questo caso, iniziare con:
    - Country-Region 
    - Role in Org (Ruolo nell'organizzazione) 
    - Subscription Type (Tipo di sottoscrizione) 
    - Company size (Dimensione dell'azienda) 
    - Theme 
1. Per evidenziare le classificazioni negative, selezionare **bassa** nel **ciò che influenza eccellenti** casella di riepilogo a discesa.  

    ![Selezionare Low dall'elenco a discesa](media/power-bi-visualization-influencers/power-bi-key-influencers.png)

L'analisi viene eseguita a livello di tabella per il campo analizzato. In questo caso, ha il **Rating** metrica. Questa metrica è definita a livello dei clienti. Ogni cliente ha assegnato un punteggio alto o un punteggio basso. Tutti i fattori esplicativi devono essere definiti a livello di clienti per l'oggetto visivo rendere di usarle. 

Nell'esempio precedente, tutti i fattori esplicativo hanno un a uno o una relazione molti-a-uno con la metrica. In questo caso, ogni punteggio ha esattamente un tema associato. Il tema è stato il tema principale della revisione del cliente. Analogamente, i clienti provengono da un paese, avere un tipo di appartenenza ed eseguire un ruolo all'interno dell'organizzazione. I fattori esplicativi sono già gli attributi di un cliente e non sono necessari alcuna trasformazione. L'oggetto visivo può rendere utilizzo immediato di essi. 

Più avanti nell'esercitazione, esaminiamo esempi più complessi che dispongono di relazioni uno-a-molti. In questi casi, le colonne devono prima essere aggregati fino al livello cliente prima di poter eseguire l'analisi. 

Misure e utilizzati come fattori esplicativi vengono inoltre valutati a livello di tabella di funzioni di aggregazione il **Analyze** metrica. Più avanti in questo articolo vengono illustrati alcuni esempi. 

## <a name="interpret-categorical-key-influencers"></a>Interpretare i fattori di influenza chiave per categoria 
Diamo un'occhiata a fattori di influenza chiave per valutazioni basse. 

### <a name="top-single-factor-that-influences-the-likelihood-of-a-low-rating"></a>Superiore a fattore singolo che influenza le probabilità di un livello di gravità basso

L'organizzazione in questo esempio ha tre ruoli: consumer, amministratore e server di pubblicazione. Un consumer è il fattore principale che contribuisce a un livello di gravità basso. 

![Selezionare un ruolo nell'organizzazione è consumer](media/power-bi-visualization-influencers/power-bi-role-consumer.png)


Più precisamente, gli utenti sono più volte 2,57 possibilità di assegnare un punteggio negativo al servizio. I fattori di influenza chiave grafico elenchi **ruolo nell'organizzazione è consumer** prima nell'elenco a sinistra. Selezionando **ruolo nell'organizzazione è consumer**, Power BI Visualizza dettagli aggiuntivi nel riquadro di destra. Viene illustrato l'effetto di ogni ruolo comparativa sulla probabilità di un livello di gravità basso.
  
- % 14.93 del consumer di assegnare un punteggio basso. 
- Tutti gli altri ruoli in Media, assegnare un punteggio basso 5.78% del tempo.
- I consumer sono 2,57 volte più possibilità di assegnare un punteggio basso rispetto a tutti gli altri ruoli. È possibile determinare tale aspetto dividendo la barra verde per la linea tratteggiata rossa. 

### <a name="second-single-factor-that-influences-the-likelihood-of-a-low-rating"></a>Secondo fattore che influenza le probabilità di un livello di gravità basso

I fattori di influenza chiave visual Confronta e classifica i fattori da molte variabili diverse. Non ha nulla a che fare con quello dell'influencer secondo **ruoli di organigramma**. Selezionare dall'elenco, che è quello dell'influencer secondo **tema è usabilità**. 

![selezione del tema è usabilità](media/power-bi-visualization-influencers/power-bi-theme.png)

Il fattore in secondo luogo più importante è correlato al tema della revisione del cliente. I clienti che hanno aggiunto un commento sull'usabilità del prodotto sono stati 2.55 volte più possibilità di assegnare un punteggio basso rispetto ai clienti che hanno aggiunto un commento su altri temi, ad esempio l'affidabilità, progettazione o dalla velocità. 

Tra gli oggetti visivi, la media, che è illustrata dalla linea rossa tratteggiata, modificato da % 5.78 a 11.34%. La media è dinamica perché è basato sulla media di tutti gli altri valori. Per primo quello dell'influencer, la media escluso il ruolo di cliente. Per il secondo influencer, escluso è il tema dell'usabilità. 
 
Selezionare il **Mostra solo i valori che sono fattori di influenza** casella di controllo per applicare un filtro utilizzando solo i valori influenti. In questo caso, si tratta di ruoli che determinano un punteggio basso. I temi di dodici siano ridotti ai quattro che Power BI identificati come temi che drive di valutazioni basse. 

![Selezionare la casella di controllo](media/power-bi-visualization-influencers/power-bi-only-show.png)

## <a name="interact-with-other-visuals"></a>Interagire con altri oggetti visivi 
 
Ogni volta che si seleziona un filtro dei dati, il filtro o altro oggetto visivo nell'area di disegno, i fattori di influenza chiave visual consente di rieseguire l'analisi nella nuova parte di dati. Ad esempio, è possibile spostare **dimensioni dell'azienda** nel report e utilizzarlo come un filtro dei dati. Usarlo per verificare se i fattori di influenza chiave per i clienti aziendali sono diversi rispetto a popolamento generale. Dimensioni dell'azienda un enterprise sono maggiore di 50.000 dipendenti.
 
Selezionando **> 50.000** una riesecuzione dell'analisi, è possibile verificare che i fattori di influenza modificato. Per i clienti aziendali di grandi dimensioni, quello dell'influencer superiore per valutazioni basse dispone di un tema relativa alla sicurezza. Si potrebbe voler analizzare ulteriormente per vedere se sono presenti i clienti di grandi dimensioni siano scontenti sulle funzionalità di sicurezza specifiche. 

![Sezione da dimensioni dell'azienda](media/power-bi-visualization-influencers/power-bi-filter.png)

## <a name="interpret-continuous-key-influencers"></a>Interpretare continua fattori di influenza chiave 
 
Finora si è appreso come usare l'oggetto visivo per esplorare i campi categorici come i vari influenzare valutazioni basse. È anche possibile avere continuati fattori, ad esempio età, altezza e prezzo per il **spiegano da** campo. Vediamo cosa succede quando **permanenza** viene spostato dalla tabella customer in **spiegano da**. Permanenza illustra quanto tempo un cliente ha usato il servizio. 
 
Man mano che aumenta permanenza, aumenta anche la probabilità di ricevere una classificazione più basso. Questa tendenza suggerisce che i clienti a lungo termine sono più possibilità di assegnare un punteggio negativo. Queste informazioni sono interessante e uno che è possibile da completare in un secondo momento. 
 
La visualizzazione mostra che ogni volta che permanenza aumenta 13.44 mesi, in Media aumenta la probabilità di un livello di gravità basso in base all'1,23 ora. In questo caso 13,44 rappresenta la deviazione standard della permanenza. In modo che rispecchi l'informazione viene visualizzato come l'aumento di permanenza di una quantità standard, ovvero la deviazione standard della permanenza, interessa la probabilità di ricevere un livello di gravità basso. 
 
Il grafico a dispersione nel riquadro di destra viene tracciata la percentuale media di valutazioni basse per ogni valore di permanenza. Verrà evidenziato l'inclinazione con una linea di tendenza.


![Grafico a dispersione per permanenza](media/power-bi-visualization-influencers/power-bi-tenure.png)

## <a name="interpret-measures-and-aggregates-as-key-influencers"></a>Interpretare le misure e le aggregazioni come fattori di influenza chiave 
 
È possibile utilizzare le misure e le aggregazioni come fattori esplicativi all'interno di analisi. Ad esempio, voler vedere quale effetto il numero di cliente di ticket di supporto o la durata media di un ticket aperto con il punteggio di ricezione. 
 
In questo caso, si desidera vedere se il numero di ticket di supporto che dispone di un cliente influenza il punteggio che offrono. A questo punto si importano **ID Ticket di supporto** dalla tabella di ticket di supporto. Poiché un cliente può disporre di più i ticket di supporto, è aggregare l'ID per il livello dei clienti. Aggregazione è importante perché l'analisi viene eseguita a livello di clienti, in modo che tutti i driver devono essere definiti a tale livello di granularità. 
 
Verrà ora esaminato il numero di ID. Ogni riga del cliente ha un numero di ticket di supporto associato. In questo caso, come il conteggio di aumenta i ticket di supporto, la probabilità del punteggio sottoposto aumenta bassi 5.51 volte. L'oggetto visivo a destra mostra il numero medio di ticket di supporto da diverse **Rating** valori valutati a livello del cliente. 

![influenza di ID Ticket di supporto](media/power-bi-visualization-influencers/power-bi-support-ticket.png)


## <a name="interpret-the-results-top-segments"></a>Interpretare i risultati: Segmenti principali 
 
È possibile usare la **fattori di influenza chiave** pressione di tab per valutare ogni fattore singolarmente. È anche possibile usare la **primi segmenti** pressione di tab per visualizzare come una combinazione di fattori di influenza la metrica che si sta analizzando. 
 
Inizialmente, segmenti superiore mostrano una panoramica di tutti i segmenti che Power BI individuati. Nell'esempio seguente mostra che sono stati trovati sei segmenti. Questi segmenti vengono classificati in base alla percentuale di classificazioni bassa all'interno del segmento. Segmento 1, ad esempio, ha le classificazioni di raggiungendo i 74,3% dei clienti che sono basse. Più in alto è posizionata la bolla, maggiore è la proporzione di valutazioni basse. Le dimensioni della bolla rappresentano il numero di clienti si trovano all'interno del segmento. 

![Selezionare la scheda segmenti superiore](media/power-bi-visualization-influencers/power-bi-top-segments-tab.png)

Se si seleziona una bolla si esegue il drill down nei dettagli del segmento corrispondente. Se si seleziona 1 segmento, ad esempio, si noterà che si è costituito da clienti relativamente specifici. Che hai visitato i clienti per più mesi 29 e avere più di quattro i ticket di supporto. Infine, non sono server di pubblicazione, in modo che siano utenti o amministratori. 
 
In questo gruppo, raggiungendo i 74,3% dei clienti ha offerto un livello di gravità basso. Il cliente medio è stato assegnato un valore basso rating dell'11,7% del tempo, in modo da questo segmento ha una percentuale più grande di valutazioni basse. È 63 punti percentuali. Segmento 1 contiene anche circa 2.2% dei dati, in modo che rappresenta una parte indirizzabile della popolazione. 

![Seleziona primo segmento superiore](media/power-bi-visualization-influencers/power-bi-top-segments2.png)

## <a name="working-with-numerical-data"></a>Utilizzo di dati numerici

Se si sposta un campo numerico nel **Analyze** campo, è possibile scegliere come gestire tale scenario. È possibile modificare il comportamento dell'oggetto visivo, passare al **riquadro di formattazione** e il passaggio tra **tipo categorico Analysis** e **tipo di analisi continua**.

![Modificare da categoriche a continua](media/power-bi-visualization-influencers/power-bi-ki-formatting.png)

Oggetto **tipo categorico Analysis** si comporta come descritto in precedenza. Ad esempio, se si sta cercando i punteggi di sondaggio compreso tra 1 e 10, si può chiedere 'Ciò che influenza i punteggi di sondaggio sia 1'?

Oggetto **tipo di analisi continua** modifica la domanda in uno continuo. Nell'esempio precedente, la nuova domanda sarebbe 'Ciò che influenza i punteggi di sondaggio per aumentare o ridurre'?

Questa distinzione è molto utile quando si dispone di un numero elevato di valori univoci nel campo che si stanno analizzando. Nell'esempio riportato di seguito vengono esaminati i prezzi di casa. Non è molto senso porsi 'Ciò che influenza il prezzo di casa per essere 156,214'? come è molto specifici e si sono potrebbero non avere dati sufficienti per dedurre un modello.

In alternativa si può decidere di porre, 'Ciò che influisce sul prezzo di casa per aumentare'? che consente di trattare i prezzi di casa come un intervallo anziché come valori distinti.

![Domanda numerico](media/power-bi-visualization-influencers/power-bi-ki-numeric-question.png)

## <a name="interpret-the-results-key-influencers"></a>Interpretare i risultati: Fattori di influenza chiave 

In questo scenario è Esaminiamo 'Ciò che influisce sul prezzo di casa per aumentare'. Si sta esaminando una serie di fattori esplicativi che possono influire su un prezzo di casa, ad esempio **anno compilati** (anno della casa è stata creata), **KitchenQual** (qualità cucina) e **YearRemodAdd** (anno che della casa è stata modificata). 

Nell'esempio seguente illustra l'influencer superiore che è in corso di eccellente qualità di cucina. I risultati sono molto simili a quelle che abbiamo visto quando abbiamo stavamo analizza metriche categoriche con alcune importanti differenze:

- Il grafico a barre a destra viene analizzato il medie anziché le percentuali. Pertanto visualizzerà il prezzo medio di casa di casa con un'eccellente kitchen What (verde a barre) rispetto al prezzo di casa medio di una casa senza un'eccellente kitchen (linea punteggiata)
- Il numero il cerchio è ancora la differenza tra la linea rossa punteggiata e una barra verde, ma viene espresso sotto forma di numero ($158. 49K) anziché una probabilità (1.93 x). Pertanto, in Media, edifici con cucine eccellente sono quasi $160 KB più costoso di case senza cucine eccellente.

![Fattori di influenza categoriche destinazione numerica](media/power-bi-visualization-influencers/power-bi-ki-numeric-categorical.png)

Nell'esempio seguente che si esamina l'impatto dispone di un fattore di continuo (anno casa prodotto è stata rimodellata) sul prezzo di casa. Come indicato di seguito sono riportate le differenze rispetto a come si analizzano gli influencer continuati per le metriche categoriche:

-   Il grafico a dispersione nel riquadro di destra consente di tracciare il prezzo medio di casa per ogni valore distinct dell'anno rimodellato. 
-   Il valore in bolla Mostra per quanti casa Media aumenta prezzo (in questo caso $2. k 87) quando l'anno della casa è stata rimodellati aumenta per la deviazione standard (in questo caso 20 anni)

![Fattori di influenza destinazione numerico continuo](media/power-bi-visualization-influencers/power-bi-ki-numeric-continuous.png)

Infine, nel caso di misure in esame l'anno medio è stata compilata una casa. In questo caso l'analisi è il seguente:

-   Grafico a dispersione nel riquadro di destra viene tracciata il prezzo medio di casa per ogni valore distinto nella tabella
-   Il valore in bolla Mostra per quanti casa Media aumenta prezzo (in questo caso $1. 35K) quando l'anno medio aumenta la deviazione standard (in questo caso 30 anni)

![Fattori di influenza di misure di destinazione numerica](media/power-bi-visualization-influencers/power-bi-ki-numeric-measures.png)

## <a name="interpret-the-results-top-segments"></a>Interpretare i risultati: Segmenti superiore

Segmenti superiore per destinazioni numeriche visualizzati i gruppi in cui la casa i prezzi in Media sono maggiori del set di dati complessivo. Ad esempio, di seguito è possibile osservare che **1 segmento** è costituito da parti in cui **GarageCars** (numero di automobili disponibile è sufficiente l'officina) è maggiore di 2 e il **RoofStyle** è Hip. Edifici con queste caratteristiche hanno un prezzo medio di $355K rispetto alla media complessiva dei dati che è $180 KB.

![Fattori di influenza di misure di destinazione numerica](media/power-bi-visualization-influencers/power-bi-ki-numeric-segments.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi 
 
**Quali sono le limitazioni per l'anteprima?** 
 
I fattori di influenza chiave visual è attualmente in anteprima pubblica e presenta alcune limitazioni. Funzionalità non sono attualmente disponibili includono: 
- Analizzare le metriche che vengono aggregati o misure.
- Utilizza l'oggetto visivo in Power BI Embedded.
- Utilizza l'oggetto visivo nelle App per dispositivi mobili di Power BI.
- Il supporto a livello di riga.
- Supporto per DirectQuery.
- Supporto di connessione in tempo reale.

![Domanda numerico](media/power-bi-visualization-influencers/power-bi-ki-numeric-question.png)

**Viene visualizzato un errore che sono stati trovati non fattori di influenza o segmenti. Perché?** 

![Nessun fattori di influenza errore trovati](media/power-bi-visualization-influencers/power-bi-error1.png)


Questo errore si verifica quando incluso in campi **spiegano da** ma non gli influencer sono stati trovati. 
- Inclusa la metrica si erano analizzando sia in **Analyze** e **spiegano da**. La rimozione dal **spiegano da**. 
- I campi esplicativi hanno un numero eccessivo di categorie con poche osservazioni. Questa situazione rende difficile per la visualizzazione determinare quali fattori sono fattori di influenza. È difficile generalizzare base solo alcune osservazioni. Se si analizza un campo numerico è possibile passare dalla **categoriche Analysis** a **analisi continua** nel **Riquadro formattazione** sotto il  **Analisi** carta.
- I fattori esplicativi hanno sufficiente osservazioni per generalizzare, ma la visualizzazione non trova eventuali correlazioni significative al report.
 
**Viene visualizzato un errore che la metrica che si analizzano non avere dati sufficienti per eseguire l'analisi su. Perché?** 

![Errore non sono sufficienti i dati](media/power-bi-visualization-influencers/power-bi-not-enough-data.png)

La visualizzazione funziona esaminando i modelli nei dati per un gruppo rispetto ad altri gruppi. Ad esempio, cerca i clienti che ha fornito le valutazioni basse rispetto ai clienti che ha fornito valutazioni elevate fanno. Se i dati nel modello a dispone solo alcune osservazioni, i modelli sono difficili da individuare. Se la visualizzazione non ha dati sufficienti per trovare gli influencer significativi, indica che sono necessari più dati per eseguire l'analisi. 

È consigliabile che si abbiano almeno 100 osservazioni per lo stato selezionato. Lo stato è in questo caso, i clienti che hanno varianza. È anche necessario almeno 10 osservazioni per gli Stati che è utilizzare per il confronto. Lo stato di confronto è in questo caso, i clienti che non varianza.

Se si analizza un campo numerico è possibile passare dalla **categoriche Analysis** a **analisi continua** nel **Riquadro formattazione** sotto il  **Analisi** carta.

**Viene visualizzato un errore che un campo *spiegano da* in modo univoco non è correlata alla tabella che contiene la metrica si analizzano. Perché?**
 
L'analisi viene eseguita a livello di tabella per il campo analizzato. Ad esempio, se si analizza il feedback dei clienti per il servizio, si potrebbe creare una tabella che indica se un cliente ha offerto una valutazione elevata o un livello di gravità basso. In questo caso, l'analisi è in esecuzione a livello di tabella dei clienti. 

Se si dispone di una tabella correlata che viene definita a un livello più granulare rispetto alla tabella che contiene l'unità di misura, viene visualizzato questo errore. Di seguito è riportato un esempio: 
 
- Analizzare ciò che comporta ai clienti di fornire valutazioni basse del servizio.
- Si desidera vedere se il dispositivo in cui il cliente utilizza il servizio influenza le recensioni che offrono.
- Un cliente può usare il servizio in più modi diversi.
- Nell'esempio seguente, cliente 10000000 Usa sia un browser e un tablet per interagire con il servizio.

![Una tabella correlata definita a un livello più granulare rispetto alla tabella che contiene l'unità di misura](media/power-bi-visualization-influencers/power-bi-error2.png)

Se si prova a usare la colonna di dispositivo come un fattore esplicativo, viene visualizzato l'errore seguente: 

![Errore colonna non corretta](media/power-bi-visualization-influencers/power-bi-error3.png)

Questo errore viene visualizzato perché il dispositivo non è definito a livello di clienti. Un cliente può utilizzare il servizio su più dispositivi. Per la visualizzazione individuare modelli, il dispositivo deve essere un attributo del cliente. Esistono diverse soluzioni che dipendono dalla comprensione del business: 
 
- È possibile modificare il riepilogo dei dispositivi da contare. Usare count, ad esempio, se il numero di dispositivi potrebbe influire sul punteggio che offra un cliente. 
- È possibile trasformare tramite pivot la colonna di dispositivo per vedere se l'utilizzo del servizio in un dispositivo specifico influenza classificazione del cliente.
 
In questo esempio, i dati è stato trasformato tramite pivot per creare nuove colonne per browser, dispositivi mobili e tablet. È ora possibile usare questi dispositivi specifici in **spiegano da**. Tutti i dispositivi risultare come fattori di influenza, e il browser il più grande influisce sul punteggio di clienti.

Più precisamente, i clienti che non usano il browser per utilizzare il servizio sono 3,79 volte più possibilità di assegnare un punteggio basso di clienti che eseguono. Inferiore nell'elenco, per dispositivi mobili l'operazione inversa è true. I clienti che usano l'app per dispositivi mobili sono più possibilità di assegnare un punteggio basso rispetto ai clienti che non lo fanno. 

![Risolto](media/power-bi-visualization-influencers/power-bi-error3-solution.png)

**Viene visualizzato un avviso che le misure non sono stati inclusi nella mio analysis. Perché?** 

![Le misure non inclusi come errore](media/power-bi-visualization-influencers/power-bi-measures-not-included.png)


L'analisi viene eseguita a livello di tabella per il campo analizzato. Se si analizza l'abbandono dei clienti, si potrebbe creare una tabella che indica se un cliente varianza o No. In questo caso, l'analisi viene eseguita a livello di tabella dei clienti.
 
Misure e le aggregazioni sono per impostazione predefinita analizzato a livello di tabella. Se vi sono una misura per la spesa mensile Media, potrebbe essere analizzato a livello di tabella dei clienti. 

Se la tabella customer non dispone di un identificatore univoco, è Impossibile valutarne la misura e viene ignorata nell'analisi. Per evitare questa situazione, assicurarsi che la tabella contenente l'unità di misura è un identificatore univoco. In questo caso, si tratta della tabella customer e l'identificatore univoco è l'ID cliente. È anche facile aggiungere una colonna dell'indice mediante Power Query.
 
**Viene visualizzato un avviso che la metrica che si analizzano ha più di 10 valori univoci e che questa quantità potrebbe influire sulla qualità della mia analisi. Perché?** 

La visualizzazione di intelligenza artificiale consente di analizzare i campi categorici e i campi numerici. Nel caso i campi categorici, ad esempio può essere varianza è Sì o No, e la soddisfazione dei clienti è alta, Media o bassa. L'aumento del numero di categorie da analizzare, significa che sono presenti un minor numero di osservazioni per categoria. Questa situazione rende più difficile per la visualizzazione per individuare modelli nei dati. 

Durante l'analisi dei campi numerici, è possibile scegliere tra considerando i campi numerici, ad esempio testo, nel qual caso si eseguirà la stessa analisi come avviene per i dati categorici (**categoriche Analysis**). Se si dispone di un numero elevato di distinti valori è consigliabile passare l'analisi **analisi continua** come ciò significa che è possibile ottenere i modelli da quando i numeri di aumentare o diminuire anziché considerarle come distinte di valori. È possibile passare da **categoriche Analysis** a **analisi continua** nel **Riquadro formattazione** sotto il **Analysis** carta.

Per trovare gli influencer più avanzati, è consigliabile raggruppare valori analoghi in una singola unità. Ad esempio, se si dispone di una metrica per prezzo, è probabile che ottenere risultati migliori eseguendo il raggruppamento di prezzi simili in alta, Media e bassa categorie o usando i punti di singole prezzo. 

![Più di 10 fattori unici avviso](media/power-bi-visualization-influencers/power-bi-error4.png)


**Sono presenti i fattori di dati che sembrano dovrebbero essere fattori di influenza chiave, ma non sono. Perché si verifica questa situazione?**

Nell'esempio seguente, i clienti che sono consumer unità valutazioni basse, con % 14.93 delle valutazioni basse. Il ruolo di amministratore ha anche un numero elevato di valutazioni, nel percorso % 13.42, ma non è considerato un Influenzatore. 

Il motivo di questo aspetto è che la visualizzazione considera anche il numero di punti dati quando trova fattori di influenza. Nell'esempio seguente ha più di 29,000 consumer e gli amministratori di un numero minore di 10 volte, circa 2,900. 390 solo di essi ha offerto un livello di gravità basso. L'oggetto visivo non avere dati sufficienti per determinare se è stata trovata una serie con un amministratore o se è semplicemente una probabilità la ricerca. 

![Come vengono determinati gli influencer](media/power-bi-visualization-influencers/power-bi-error5.png)

**Come è possibile calcolare fattori di influenza chiave per l'analisi categoriche?**

Dietro le quinte, Usa la visualizzazione di intelligenza artificiale [a ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) per eseguire una regressione logistica per calcolare i fattori di influenza chiave. Una regressione logistica è un modello statistico che confronta diversi gruppi. 

Se si desidera vedere ciò che comporta valutazioni basse, la regressione logistica esamina le differenze tra i clienti che hanno stato assegnato un punteggio basso tra i clienti che hanno stato assegnato un punteggio alto. Se si dispone di più categorie, ad esempio neutri, alto e bassi punteggi, si esamina le differenze tra i clienti che hanno stato assegnato un livello di gravità basso tra i clienti che non ha generato un livello di gravità basso. In questo caso, i clienti che hanno stato assegnato un punteggio basso le differenze tra i clienti che ha fornito una valutazione elevata o una classificazione neutra? 
 
La regressione logistica Cerca modelli nei dati e cerca i clienti che ha fornito un livello di gravità basso potrebbero le differenze tra i clienti che ha fornito una valutazione elevata al contributo. È possibile, ad esempio, che i clienti con più i ticket di supporto forniscono una percentuale più elevata di valutazioni basse rispetto ai clienti con pochi o nessun ticket di supporto.
 
La regressione logistica prende in considerazione anche il numero di punti dati è presente. Ad esempio, se i clienti che svolgono un ruolo di amministratore assegnare punteggi in proporzione più negativi, ma esistono solo alcuni amministratori, questo fattore non è considerato influente. Questa operazione viene eseguita perché non sono sufficienti punti dati disponibili per dedurre un modello. Un test statistico, noto come un test Wald, viene usato per determinare se un fattore viene considerato un Influenzatore. L'oggetto visivo usa un valore p pari a 0,05 per determinare la soglia. 

**Come è possibile calcolare fattori di influenza chiave per l'analisi numerica?**

Dietro le quinte, Usa la visualizzazione di intelligenza artificiale [a ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) per eseguire una regressione lineare per calcolare i fattori di influenza chiave. Una regressione lineare è un modello statistico che esamina come il risultato del campo che si analizzano cambia in base i fattori esplicativi.

Ad esempio, se analizzati prezzi, una regressione lineare avrà un aspetto nell'impatto con che un'eccellente kitchen avranno sul prezzo di casa. Edifici con cucine eccellente hanno in genere i prezzi di casa inferiori o superiori rispetto a fornitori senza cucine eccellente?

La regressione lineare prende in considerazione anche il numero di punti dati. Ad esempio, se edifici con autorità giudiziarie tennis hanno prezzi più elevati ma non contiene un numero molto ridotto che hanno un campo da tennis è disponibile, questo fattore non è considerato influente. Questa operazione viene eseguita perché non sono sufficienti punti dati disponibili per dedurre un modello. Un test statistico, noto come un test Wald, viene usato per determinare se un fattore viene considerato un Influenzatore. L'oggetto visivo usa un valore p pari a 0,05 per determinare la soglia. 

**Come vengono calcolati i segmenti?**

Dietro le quinte, Usa la visualizzazione di intelligenza artificiale [a ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) per l'esecuzione di un albero delle decisioni per trovare i sottogruppi interessanti. L'obiettivo di albero delle decisioni è finire con un sottogruppo di punti dati che è relativamente alto nella metrica che si è interessati. Potrebbe trattarsi di clienti con un livello basso o case con prezzi elevati.

L'albero delle decisioni accetta ogni fattore esplicativo e tenta di motivo quale factor offre il meglio *dividere*. Ad esempio, se si filtra i dati in modo da includere solo i clienti aziendali di grandi dimensioni, che separa i clienti che ha fornito una valutazione elevata al contributo e un livello di gravità basso? O forse è preferibile per filtrare i dati in modo da includere solo i clienti che hanno aggiunto un commento sulla sicurezza? 

Dopo che l'albero delle decisioni esegue una divisione, viene preso il sottogruppo di dati e determina la suddivisione migliore successiva per tali dati. In questo caso, il sottogruppo è i clienti che hanno aggiunto un commento sulla sicurezza. Dopo ogni divisione, considera anche se dispone di sufficienti punti dati per questo gruppo rappresentativa abbastanza per dedurre un modello da o se si tratta di un'anomalia nei dati di e non un segmento reale. Un altro test statistico viene applicato per verificare la presenza della rilevanza statistica della condizione di divisione con p-pari a 0,05. 

Al termine dell'esecuzione dell'albero delle decisioni, accetta tutte le divisioni, ad esempio i commenti di sicurezza e aziendali di grandi dimensioni e crea i filtri di Power BI. Questa combinazione di filtri viene integrata in un segmento dell'oggetto visivo. 
 
**Il motivo per cui in alcuni casi diventano i fattori di influenza o non venga più fattori di influenza come si spostano più campi nel *spiegano da* campo?**

La visualizzazione valuta tutti i fattori esplicativi insieme. Un fattore potrebbe essere un Influenzatore da solo, ma quando viene considerato con altri fattori potrebbe non. Si supponga di che voler analizzare ciò che comporta un prezzo di casa sia elevata, con camere da letto e le dimensioni di casa come fattori esplicativi:

- Di per sé camere da letto più potrebbe essere un driver per i prezzi di casa sia elevato.
- Dimensioni di casa incluse nell'analisi indica che osservi ora cosa accade per camere da letto mentre house rimarranno invariate.
- Se le dimensioni di casa sono fissata a piedi quadrati 1.500, è improbabile che un continuo aumento del numero di camere da letto aumenta notevolmente il prezzo di casa. 
- Camere da letto non può essere importante di un fattore com'era prima erano considerata le dimensioni di casa. 




## <a name="next-steps"></a>Passaggi successivi
- [Grafici combinati in Power BI](power-bi-visualization-combo-chart.md)
- [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
