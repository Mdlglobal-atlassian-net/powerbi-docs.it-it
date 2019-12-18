---
title: Modificare lo schema linguistico per Domande e risposte e aggiungere formulazioni in Power BI Desktop
description: Come usare Power BI Desktop per modificare lo schema linguistico utilizzato da Domande e risposte in Power BI.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 64a6294ca30901c61928eca068ab4ebbb3d39638
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958518"
---
# <a name="edit-qa-linguistic-schema-and-add-phrasings-in-power-bi-desktop"></a>Modificare lo schema linguistico per Domande e risposte e aggiungere formulazioni in Power BI Desktop 
L'uso del linguaggio naturale e di frasi comuni per porre le domande ai dati è una funzionalità molto potente. Lo è ancora di più quando i dati restituiscono una risposta. Quando si formula una domanda a Domande e risposte in Power BI, il sistema fa del suo meglio per rispondere correttamente. Tuttavia, per interazioni ancora più efficaci, è possibile migliorare le risposte. A tale scopo una soluzione è quella di modificare lo schema linguistico. 

Si parte dai dati aziendali.  Più il modello di dati è di qualità, più sarà facile per gli utenti ottenere risposte appropriate. Uno dei modi per migliorare il modello consiste nell'aggiungere uno schema linguistico che definisce e classifica la terminologia e le relazioni tra i nomi delle tabelle e delle colonne nel set di dati. In Power BI Desktop è possibile gestire gli schemi linguistici. 

Sono due gli aspetti da considerare per Domande e risposte.  Il primo aspetto riguarda la preparazione, ovvero la *modellazione*.  Il secondo aspetto riguarda la formulazione di domande e l'esplorazione dei dati, ovvero l'*utilizzo*. In alcune aziende, i dipendenti con il ruolo di *modellatore di dati* o amministratore IT possono ricevere l'incarico di assemblare i set di dati, creare i modelli di dati e pubblicare i set di dati in Power BI.  Un secondo gruppo di dipendenti può invece avere il compito di "utilizzare" i dati online.  In altre aziende questi ruoli possono essere combinati. 

Questo articolo è destinato i modellatori di dati, ovvero agli utenti impegnati a ottimizzare i set di dati per restituire i migliori risultati possibili per Domande e risposte. 

## <a name="what-is-a-linguistic-schema"></a>Che cos'è uno schema linguistico?
Uno schema linguistico descrive i termini e le frasi che Domande e risposte dovrebbe essere in grado di comprendere in merito agli oggetti contenuti in un set di dati, tra cui le parti del discorso, le formulazioni e i sinonimi correlati a tale set di dati. Quando si importa un set di dati o ci si connette a esso, Power BI crea uno schema linguistico basato sulla struttura del set. Quando si pone una domanda a Domande e risposte, parte una ricerca per recuperare corrispondenze e relazioni nei dati al fine di determinare lo scopo della domanda. Ad esempio, vengono cercati sostantivi, verbi, aggettivi, formulazioni e altri elementi. E vengono cercate anche relazioni, ad esempio, quali colonne sono oggetti di un verbo. 

Probabilmente si conosce già il significato delle parti del discorso (in caso contrario, vedere di seguito), ma il termine *formulazione* potrebbe risultare nuovo.  Una formulazione è il modo in cui si descrivono, ovvero *si formulano*, le relazioni tra più elementi. Ad esempio, per descrivere la relazione tra clienti e prodotti, si potrebbe dire "i clienti acquistano i prodotti". Oppure, per descrivere la relazione tra clienti ed età, si potrebbe dire "l'età indica quanto sono vecchi i clienti". Oppure, per descrivere la relazione tra clienti e numeri di telefono, si potrebbe dire semplicemente "i clienti hanno numeri di telefono".

Questi formulazioni esistono in una varietà di forme e dimensioni. Alcune corrispondono direttamente alle relazioni presenti nel modello di dati. Alcune fanno riferimento alle colonne e alle tabelle che le contengono. Altre fanno riferimento a più tabelle e colonne in relazioni complesse. In tutti i casi, però, descrivono con termini semplici in che modo gli elementi sono correlati tra loro.

Gli schemi linguistici vengono salvati in formato YAML. Questo formato è correlato a un formato diffuso, JSON, ma offre una sintassi più flessibile e più facile da leggere. Gli schemi linguistici possono essere modificati, esportati e importati in Power BI Desktop.

## <a name="prerequisites"></a>Prerequisiti

- Se non si è già letto l'articolo su come [migliorare il modello di dati per Domande e risposte](q-and-a-best-practices.md), è consigliabile leggere innanzitutto tale articolo. Include numerosi suggerimenti per progettare e migliorare il modello di dati e una sezione importante sull'aggiunta dei sinonimi.  
- Scaricare gli esempi di [file con estensione yaml e pbix](https://go.microsoft.com/fwlink/?linkid=871858).   
- Installare un editor per i file YAML. È consigliabile usare [Visual Studio Code](https://code.visualstudio.com/).

### <a name="set-up-an-editor-for-yaml-files"></a>Configurare un editor per i file YAML
Per modificare i file YAML degli schemi linguistici è consigliabile usare Visual Studio Code. Visual Studio Code include un supporto predefinito per i file YAML, che può essere esteso per convalidare specificamente il formato di schema linguistico usato in Power BI.
1. Installare [Visual Studio Code](https://code.visualstudio.com/).    

2. Selezionare lo schema linguistico di esempio salvato in precedenza: [file con estensione yaml](https://go.microsoft.com/fwlink/?linkid=871858) (SummerOlympics.lsdl.yaml).    
4. Selezionare **Visual Studio Code** e **Always use this app to open .yaml files** (Usa sempre questa app per aprire i file yaml).

    ![Come aprire il file](media/q-and-a-tooling-advanced/power-bi-visual-code.png)

4. In Visual Studio Code installare l'estensione YAML Support by Red Hat.    
    a. Selezionare la scheda **Extensions** (ultima a sinistra) o premere CTRL+MAIUSC+X.    
    ![icona estensioni](media/q-and-a-tooling-advanced/power-bi-extensions.png)    
    b. Cercare "yaml" e selezionare **YAML Support by Red Hat** nell'elenco.    
    c. Selezionare **Install > Reload**.


## <a name="working-with-linguistic-schemas"></a>Utilizzo degli schemi linguistici

Gli schemi linguistici possono essere utilizzati in due modi. Il primo consiste nel modificare, importare ed esportare il file YAML dalla barra multifunzione in Power BI Desktop. Questo metodo è illustrato nell'articolo sull'[esperienza d'uso degli strumenti di Domande e risposte](q-and-a-tooling-intro.md) in Power BI. In questo caso, non è necessario aprire il file YAML per migliorare Domande e risposte. 

L'altro modo per modificare uno schema linguistico consiste nell'esportare e modificare direttamente il file YAML.  Quando si modifica il file YAML di uno schema linguistico, si contrassegnano le colonne nella tabella come elementi grammaticali diversi e si definiscono le parole che potrebbero essere usate per formulare una domanda. Ad esempio, si definiscono le colonne che sono il soggetto e l'oggetto del verbo e si aggiungono parole alternative che i colleghi potrebbero usare per fare riferimento a tabelle, colonne e misure nel modello. 

![Esempio di file YAML di uno schema linguistico](media/q-and-a-tooling-advanced/power-bi-linguistic-schema.png)

Per poter modificare uno schema linguistico, è necessario prima aprirlo, vale a dire esportarlo da Power BI Desktop. Quando si salva nuovamente il file YAML nello stesso percorso, l'operazione viene considerata un'importazione.  È tuttavia possibile importare anche altri file YAML.  Se, ad esempio, si ha un set di dati simile in cui si è lavorato molto per aggiungere parti del discorso, identificare relazioni e creare formulazioni e sinonimi, è possibile usare il file YAML corrispondente in un file di Power BI Desktop diverso. 

Domande e risposte userà tutte queste informazioni combinandole con gli eventuali miglioramenti che consentono di fornire una migliore risposta, arricchire il completamento automatico e il riepilogo delle domande.

## <a name="edit-a-linguistic-schema"></a>Modifica di uno schema linguistico
Quando si esporta uno schema linguistico da Power BI Desktop per la prima volta, la maggior parte o l'intero contenuto del file viene generato automaticamente dal motore di Domande e risposte. Queste entità generate, parole (sinonimi), relazioni e frasi vengono designate con un tag **State: Generated**. Sono incluse nel file principalmente a scopo informativo, ma possono essere un punto di partenza utile per apportare altre modifiche. 

> [!NOTE]
> Il file YAML di esempio incluso in questa esercitazione non contiene i tag **State:Generated** e **State:Deleted** perché è stato appositamente preparato per l'esercitazione. Per visualizzare questi tag, aprire un file con estensione pbix non modificato nella visualizzazione relazioni ed esportare lo schema linguistico.

![File YAML con State: Generated](media/q-and-a-tooling-advanced/power-bi-generated-state.png)

Quando si importa il file di schema linguistico in Power BI Desktop, tutti gli elementi contrassegnati come **State: Generated** vengono ignorati e successivamente rigenerati. Se pertanto si vuole modificare il contenuto generato, rimuovere il tag **State: Generated** corrispondente. Analogamente, se si vuole rimuovere il contenuto generato, sostituire il tag **State: Generated** con **State: Deleted** in modo che non venga rigenerato quando si importa il file dello schema linguistico.

### <a name="export-then-import-a-yaml-file"></a>Esportare e quindi importare un file YAML

1. Aprire il set di dati in Visualizzazione modello di Power BI Desktop. 
2. Nella scheda **Modellazione** selezionare **Schema linguistico** > **Esporta lo schema linguistico**.
3. Salvare il file. Il nome del file termina con .lsdl.yaml.
4. Aprire il file in Visual Code o in un altro editor.
4. In Visualizzazione modello di Power BI Desktop, nella scheda **Modellazione**, selezionare **Schema linguistico** > **Importa lo schema linguistico**. 
6. Passare al percorso in cui è stato salvato il file YAML modificato e selezionare il file. Verrà visualizzato un messaggio di conferma per informare l'utente che il file YAML dello schema linguistico è stato importato.

    ![Messaggio di operazione completata](media/q-and-a-tooling-advanced/power-bi-success.png)

## <a name="phrasings-in-the-linguistic-schema"></a>Formulazioni nello schema linguistico
Si è detto che una formulazione è il modo in cui si descrivono, ovvero si formulano, le relazioni tra più elementi. Ad esempio, per descrivere la relazione tra clienti e prodotti, si potrebbe dire "i clienti acquistano i prodotti".

## <a name="where-do-phrasings-come-from"></a>Da dove provengono le formulazioni?
Power BI aggiunge automaticamente molte formulazioni semplici allo schema linguistico, in funzione della struttura del modello e di alcune supposizioni basate sui nomi delle colonne. ad esempio:
- La maggior parte delle colonne è correlata alla tabella che le contiene con una semplice formulazione come "i prodotti hanno descrizioni".
- Le relazioni del modello generano formulazioni predefinite per entrambe le direzioni della relazione, come "gli ordini hanno prodotti" e "i prodotti hanno ordini".
- In base ai nomi delle colonne, alcune relazioni del modello possono ricavare formulazioni predefinite più complesse come "gli ordini sono spediti a città".

Per parlare di determinati aspetti gli utenti usano tuttavia innumerevoli modi che Domande e risposte non può immaginare. È quindi opportuno aggiungere manualmente delle formulazioni personalizzate.

## <a name="why-add-phrasings"></a>Perché aggiungere formulazioni?
Il primo motivo per cui è utile aggiungere una formulazione è per definire un nuovo termine. Ad esempio, se si desidera poter chiedere "elenca i clienti più vecchi", è necessario innanzitutto insegnare a Domande e risposte cosa si intende per "vecchi". In questo caso si potrebbe aggiungere la formulazione "l'età indica quanto sono vecchi i clienti".

Il secondo motivo per cui è utile aggiungere una formulazione è per risolvere un'ambiguità. La ricerca di parole chiave semplici non dà risultati ottimali quando le parole hanno più di un significato. Ad esempio, "Voli per Chicago" non ha lo stesso significato di "Voli da Chicago". Domande e risposte non riconoscerà l'intenzione dell'utente, a meno che non si aggiungano le formulazioni "voli da città di partenza" e "voli per città di arrivo". Analogamente, Domande e risposte capirà la distinzione tra "automobili che John ha venduto a Mary" e "automobili che John ha acquistato da Mary" solo dopo che sono state aggiunte le formulazioni "i clienti acquistano le automobili dai dipendenti" e "i dipendenti vendono le automobili ai clienti".

L'ultimo motivo per cui è utile aggiungere formulazioni è migliorare le riformulazioni. Per evitare che Domande e risposte rimandi l'affermazione "Mostra i clienti e i loro prodotti", sarebbe più chiaro dire "Mostra i clienti e i prodotti che hanno acquistato" oppure "Mostra i clienti e i prodotti che hanno guardato", a seconda del modo in cui la domanda è stata intesa. L'aggiunta di formulazioni personalizzate consente alle riformulazioni di essere più esplicite e meno ambigue.


## <a name="kinds-of-phrasings"></a>Tipi di formulazioni
Per comprendere i diversi tipi di formulazioni, è prima necessario ripassare un paio di termini di grammatica basilari:
- Un *sostantivo* è una persona, un luogo o un'operazione. 
    Esempi: auto, ragazzo, Mario, flusso
- Un *verbo* è un'azione o un modo di essere. 
    Esempi: covare, scoppiare, divorare, espellere
- Un *aggettivo* è un nome che descrive un sostantivo. 
    Esempi: potente, magico, dorato, due
- Una *preposizione* è una parola usata prima di un sostantivo per collegarlo a un sostantivo, verbo o aggettivo precedente. Esempi: di, per, con, da
-  Un *attributo* è una qualità o una funzione di un oggetto.
-  Un *nome* è una parola o un gruppo di parole con cui ci si riferisce a una persona, a un animale, a un luogo o a una cosa.   


### <a name="attribute-phrasings"></a>Formulazioni con attributi
Le formulazioni con attributi sono la spina dorsale di Domande e risposte e vengono utilizzate quando un elemento agisce come un attributo di un altro elemento. Sono semplici, dirette e svolgono la maggior parte del carico di lavoro quando non è stata definita una formulazione più precisa o dettagliata. Le formulazioni con attributi sono descritte con il verbo di base "avere", ad esempio "i prodotti hanno categorie" e "i paesi ospiti hanno città ospiti". Consentono automaticamente anche la formulazione di domande con le preposizioni "di" e "per" ("categorie di prodotti", "ordini per prodotti") e con la forma di possesso ("ordini di John"). Le formulazioni con attributi vengono impiegate nei tipi di domanda seguenti:

- Quali clienti hanno ordini?
- Elenca le città per stato crescente
- Mostra gli ordini contenenti tè
- Elenca i clienti con ordini
- Qual è la categoria di ogni prodotto?
- Conta gli ordini di Robert King    

Power BI genera la stragrande maggioranza delle formulazioni con attributi necessari nel modello, tenendo conto del contenimento di tabella/colonna e delle relazioni del modello. In genere, non è necessario crearle manualmente.
Di seguito viene riportato un esempio dell'aspetto che ha una formulazione con attributi all'interno dello schema linguistico:

```json
product_has_category:
  Binding: {Table: Products}
  Phrasings:
  - Attribute: {Subject: product, Object: product.category}
```
 
### <a name="name-phrasings"></a>Formulazioni nominali
Le formulazioni nominali sono utili se il modello di dati prevede una tabella che contiene oggetti identificati da un nome, come i nomi di atleti o di clienti. Ad esempio, la formulazione "nomi dei prodotti è come sono chiamati i prodotti" è essenziale per poter usare nomi dei prodotti nelle domande. Le formulazioni nominali consentono anche di usare "denominato" come verbo, ad esempio "Elenco di clienti denominati John Smith". Le formulazioni nominali sono comunque molto importanti quando sono usate in combinazione con altre formulazioni per consentire l'uso di un valore nome per fare riferimento a una particolare riga di tabella. Ad esempio, per "I clienti che hanno acquistato tè", Domande e risposte può indicare che il valore "tè" fa riferimento all'intera riga della tabella di prodotti anziché semplicemente a un valore nella colonna del nome del prodotto. Le formulazioni nominali vengono impiegate nei tipi di domanda seguenti:    
- Quali dipendenti si chiamano Robert King
- Chi si chiama Ernst Handel
- Sport di Fernand De Montigny
- Numero di atlete chiamate Mary
- Che cosa ha acquistato Robert King?

Supponendo di avere usato una convenzione di denominazione sensata per le colonne di nome nel modello (ad esempio, "Nome" o "NomeProdotto" anziché "NmPrd"), la maggior parte delle formulazioni nominali necessarie per il modello verrà generata automaticamente da Power BI, pertanto, in genere, non è necessario crearle manualmente.

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione nominale all'interno dello schema linguistico:

```json
employee_has_name:
  Binding: {Table: Employees}
  Phrasings:
  - Name:
      Subject: employee
      Name: employee.name
```

 
### <a name="adjective-phrasings"></a>Formulazioni aggettivali
Le formulazioni aggettivali definiscono nuovi aggettivi utilizzati per descrivere elementi presenti nel modello. Ad esempio, la formulazione "i clienti soddisfatti sono clienti con valutazione > 6" è necessaria per porre domande quali "Elenca i clienti soddisfatti a Chicago". Esistono diversi tipi di formulazioni aggettivali utilizzabili in situazioni diverse.

Le *formulazioni aggettivali semplici* definiscono un nuovo aggettivo in base a una condizione, ad esempio "i prodotti sospesi sono prodotti con stato = S". Le formulazioni aggettivali vengono impiegate nei tipi di domanda seguenti:
- Quali prodotti sono sospesi?
- Elenca i prodotti sospesi
- Elenca gli atleti vittoriosi
- Prodotti che sono esauriti

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione aggettivale semplice all'interno dello schema linguistico:

product_is_discontinued:

```json
Binding: {Table: Products}
  Conditions:
  - Target: product.discontinued
    Operator: Equals
    Value: true
  Phrasings:
  - Adjective:
      Subject: product
      Adjectives: [discontinued]
```

Le *formulazioni aggettivali di quantità* definiscono un nuovo aggettivo basato su un valore numerico che indica l'estensione a cui si riferisce l'aggettivo, ad esempio "le lunghezze indicano quanto sono lunghi i fiumi" e "le regioni piccole hanno superfici poco estese". Le formulazioni aggettivali di quantità vengono impiegate nei tipi di domanda seguenti:
- Elenca i fiumi lunghi
- Quali fiumi sono i più lunghi?
- Elenca le regioni più piccole che hanno vinto il campionato di basket
- Quanto è lungo il Rio Grande?

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione aggettivale di quantità all'interno dello schema linguistico:

river_has_length:

 ```json
Binding: {Table: Rivers}
  Phrasings:
  - Adjective:
      Subject: river
      Adjectives: [long]
      Antonyms: [short]
      Measurement: river.length
```

Le *formulazioni aggettivali dinamiche* definiscono un set di nuovi aggettivi basati su valori di una colonna del modello, ad esempio "i colori descrivono i prodotti". Le formulazioni aggettivali dinamiche vengono impiegate nei tipi di domanda seguenti:
- Elenca i prodotti rossi
- Quali prodotti sono verdi?
- Mostra eventi di pattinaggio femminili
- Conta i problemi attivi

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione aggettivale dinamica all'interno dello schema linguistico:

product_has_color:
```json
Binding: {Table: Products}
  Phrasings:
  - DynamicAdjective:
      Subject: product
      Adjective: product.color
```

 
### <a name="noun-phrasings"></a>Formulazioni sostantivali
Le formulazioni sostantivali definiscono nuovi nomi che descrivono sottogruppi di elementi nel modello. Spesso includono un qualche tipo di misura o condizione specifica al modello. Ad esempio, per il modello Olympics potrebbe essere opportuno aggiungere formulazioni che distinguono i campioni dai vincitori di medaglie, gli sport con palla dagli sport acquatici, i giochi di squadra dai giochi individuali, le categorie di età degli atleti (adolescenti, adulti, senior) e così via. Per un database di film si potrebbero voler aggiungere formulazioni sostantivali come "i fiaschi sono film con profitto netto < 0", in modo da poter formulare domande come "conta i fiaschi per anno". Esistono due formi di formulazioni sostantivali utilizzabili in situazioni diverse.

Le *formulazioni sostantivali semplici* definiscono un nuovo sostantivo basato su una condizione, ad esempio "il consulente è un dipendente per cui tempo pieno = false" e "il campione è un atleta con un numero di medaglie > 5". Le formulazioni sostantivali semplici vengono impiegate nei tipi di domanda seguenti:

- Quali dipendenti sono consulenti?
- Conta i consulenti a Portland
- Quanti campioni nel 2016

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione sostantivale semplice all'interno dello schema linguistico:

employee_is_contractor:

```json
Binding: {Table: Employees}
  Conditions:
  - Target: employee.full_time
    Operator: Equals
    Value: false
  Phrasings:
  - Noun:
      Subject: employee
      Nouns: [contractor]
```

Le *formulazioni sostantivali dinamiche* definiscono un gruppo di nuovi nomi basati su valori di una colonna del modello, ad esempio "i lavori definiscono sottogruppi di dipendenti". Le formulazioni sostantivali dinamiche vengono impiegate nei tipi di domanda seguenti:

- Elenca i cassieri di Chicago
- Quali dipendenti sono baristi?
- Elenca gli arbitri nel 1992

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione sostantivale dinamica all'interno dello schema linguistico: employee_has_job:

 ```json
Binding: {Table: Employees}
  Phrasings:
  - DynamicNoun:
      Subject: employee
      Noun: employee.job
```

### <a name="preposition-phrasings"></a>Formulazioni con preposizioni
Le formulazioni con preposizioni consentono di descrivere come sono collegati tra loro gli elementi del modello tramite le preposizioni. Ad esempio, la formulazione "le città sono negli stati" migliora la comprensione della domande "conta le città in Francia". Alcune formulazioni con preposizioni sono create automaticamente quando una colonna viene riconosciuta come entità geografica. Le formulazioni con preposizioni vengono impiegate nei tipi di domanda seguenti:

- Conta i clienti a New York
- Elenca i libri di linguistica
- In quale città vive Robert King?
- Quanti libri sono per Stephen Pinker?
 
Di seguito viene riportato un esempio dell'aspetto che ha una formulazione con preposizioni all'interno dello schema linguistico: customers_are_in_cities:

 ```json
Binding: {Table: Customers}
  Phrasings:
  - Preposition:
      Subject: customer
      Prepositions: [in]
      Object: customer.city
```

 
### <a name="verb-phrasings"></a>Formulazioni verbali
Le formulazioni verbali consentono di descrivere come sono collegati tra loro gli elementi del modello tramite i verbi. Ad esempio, la formulazione "i clienti acquistano i prodotti" migliora la comprensione delle domande del tipo "chi ha comprato formaggio?" e "che cosa ha acquistato John?" Le formulazioni verbali sono le formulazioni più flessibili, spesso mettono in relazione più di due elementi tra loro, ad esempio "i dipendenti vendono i prodotti ai clienti". Le formulazioni verbali vengono impiegate nei tipi di domanda seguenti:

- Chi ha venduto cosa a chi?
- Quale dipendente ha venduto tè a John?
- A quanti clienti è stato venduto il tè da Mary?
- Elenca i prodotti che Mary ha venduti a John.
- Quali prodotti sospesi sono stati venduti ai clienti di Chicago dai dipendenti di Boston?

Le formulazioni verbali possono inoltre contenere formulazioni con preposizioni diventando, di conseguenza, ancora più flessibili, ad esempio "gli atleti vincono medaglie ai concorsi" o "i clienti ricevono rimborsi per i prodotti". Le formulazioni verbali con formulazioni con preposizioni vengono impiegate nei tipi di domanda seguenti:

- Quanti atleti hanno vinto la medaglia d'oro ai campionati Visa?
- Quali clienti hanno ottenuto un rimborso per il formaggio?
- In quale gara Danell Leyva ha vinto la medaglia di bronzo?

Alcune formulazioni verbali sono create automaticamente quando il sistema riconosce che una colonna contiene sia un verbo che una preposizione.

Di seguito viene riportato un esempio dell'aspetto che ha una formulazione verbale all'interno dello schema linguistico: customers_buy_products_from_salespeople:

```json
Binding: {Table: Orders}
  Phrasings:
  - Verb:
      Subject: customer
      Verbs: [buy, purchase]
      Object: product
      PrepositionalPhrases:
      - Prepositions: [from]
        Object: salesperson
```

### <a name="relationships-with-multiple-phrasings"></a>Relazioni con più formulazioni
Spesso, una stessa relazione può essere descritta in più modi. In questo caso, una singola relazione può essere definita da più formulazioni. È comune che la relazione tra un'entità di tabella e un'entità di colonna contenga sia una formulazione con attributi sia un altro tipo di formulazione. Ad esempio, nella relazione tra cliente e nome cliente è opportuno che sia presente sia una formulazione con attributi (ad esempio, "i clienti hanno nomi") che una formulazione nominale (ad esempio, "i nomi cliente sono i nomi dei clienti") affinché sia possibile porre entrambi i tipi di domanda.

Di seguito viene riportato un esempio dell'aspetto che ha una relazione con due formulazioni all'interno dello schema linguistico: customer_has_name:

  ```json
Binding: {Table: Customers}
  Phrasings:
    - Attribute: {Subject: customer, Object: customer.name}
    - Name:
        Subject: customer
        Object: customer.name
```

Un altro esempio sarebbe aggiungere la formulazione alternativa "i dipendenti vendono i prodotti ai clienti" alla relazione "i clienti acquistano i prodotti dai dipendenti". Si noti che non è necessario aggiungere le variazioni del tipo "i dipendenti vendono i prodotti *ai clienti*" o "i prodotti sono venduti ai clienti *dai dipendenti*", poiché le variazioni del soggetto e dell'oggetto indiretto introdotte dalle preposizione "ai" e "dai" vengono dedotte automaticamente da Domande e risposte.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
Se si apporta una modifica a un file con estensione lsdl.yaml che non è conforme al formato dello schema linguistico, i problemi vengono sottolineati con una riga ondulata simile alla seguente: 

![File yaml con errori](media/q-and-a-tooling-advanced/power-bi-yaml-errors.png)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
