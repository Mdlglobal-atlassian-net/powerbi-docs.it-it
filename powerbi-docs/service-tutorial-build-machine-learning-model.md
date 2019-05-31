---
title: 'Esercitazione: Creare un modello di Machine Learning in Power BI (anteprima)'
description: In questa esercitazione si compila un modello di Machine Learning in Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406742"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Esercitazione: Creare un modello di Machine Learning in Power BI (anteprima)

In questo articolo dell'esercitazione, userà **automatizzati di Machine Learning** per creare e applicare un modello di stima binaria in Power BI. L'esercitazione include materiale sussidiario per la creazione di un flusso di dati di Power BI e con le entità definite nel flusso di dati per il training e di convalidare un modello di machine learning direttamente in Power BI. È quindi utilizzare il modello per il punteggio per generare stime.

In primo luogo, si creerà un binario stima modello di machine learning, per stimare l'intenzione di acquisto di acquirenti online basato su un set di attributi relativi sessione online. Un set di dati di benchmark machine learning viene usato per questo esercizio. Una volta che viene eseguito il training di un modello, Power BI genera automaticamente un report di convalida che spiega i risultati del modello. È quindi possibile esaminare il rapporto di convalida e applicare il modello ai dati per l'assegnazione dei punteggi.

Questa esercitazione prevede i passaggi seguenti:

> [!div class="checklist"]
> * Creare un flusso di dati con i dati di input
> * Creare ed eseguire il training di un modello di machine learning
> * Esaminare il rapporto di convalida del modello
> * Applicare il modello a un'entità del flusso di dati
> * Usando l'output con punteggio provenienti dal modello in un report di Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Creare un flusso di dati con i dati di input

La prima parte di questa esercitazione consiste nel creare un flusso di dati con dati di input. Questo processo richiede pochi passaggi, come illustrato nelle sezioni seguenti, che iniziano con il recupero di dati.

### <a name="get-data"></a>Recupera dati

Il primo passaggio nella creazione di un flusso di dati deve avere le origini dati pronte. In questo caso, usiamo un set di dati di apprendimento automatico da un insieme di sessioni online, alcuni dei quali culminato nell'acquisto di elaborazione. Il set di dati contiene un set di attributi relative alle sessioni, che verrà usata per il nostro modello di training.

È possibile scaricare il set di dati dal sito Web UC Irvine.  Inoltre è disponibile, ai fini di questa esercitazione, dal collegamento seguente: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Creare le entità

Per creare le entità nel flusso di dati, accedere al servizio Power BI e passare a un'area di lavoro nella propria capacità dedicata in cui sia abilitata l'anteprima delle funzionalità di intelligenza artificiale.

Se si ha già un'area di lavoro, è possibile crearne uno selezionando **aree di lavoro** nel menu di spostamento a sinistra nel servizio Power BI e selezionare **Crea area di lavoro di app** nella parte inferiore del pannello che viene visualizzata. Verrà aperto un pannello a destra immettere i dettagli dell'area di lavoro. Immettere un nome dell'area di lavoro e selezionare **avanzate**. Verificare che l'area di lavoro utilizza capacità dedicata tramite il pulsante di opzione, che viene assegnato a un'istanza di capacità dedicata che ha attivato l'anteprima di intelligenza artificiale. Selezionare quindi **Salva**.

![Crea un'area di lavoro](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Dopo aver creato l'area di lavoro, è possibile selezionare **Skip** in basso a destra della schermata iniziale, come illustrato nell'immagine seguente.

![Ignorare se si dispone di un'area di lavoro](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selezionare il **flussi di dati (anteprima)** scheda. Selezionare il **Create** nella parte superiore destra dell'area di lavoro e quindi selezionare **flusso di dati**.

![Creare flussi di dati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selezionare **Aggiungi nuove entità**. Verrà avviata una **Power Query** editor nel browser.

![Aggiungi nuove entità](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selezionare **File di testo/CSV** come origine dati, illustrato nella figura seguente.

![File di testo/CSF selezionato](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Nel **connettersi a un'origine dati** che viene visualizzata accanto, incollare il collegamento seguente per il *online_shoppers_intention.csv* nel **URL o percorso File** casella e quindi selezionare **Avanti**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Percorso del file](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Editor di Power Query viene visualizzata un'anteprima dei dati dal file CSV. Selezionare **tabella trasformare** nella barra multifunzione di comando e quindi selezionare **utilizza la prima riga come intestazioni** dal menu visualizzato. Verrà aggiunta la _alzate di livello le intestazioni_ passaggio della query nel **i passaggi applicati** sezione sulla destra della schermata. È possibile rinominare la query per un nome più descrittivo, modificando il valore nel **nome** casella trovata nel riquadro di destra. Ad esempio, è possibile modificare il nome della Query per _visitatore Online_.

![Sostituire con un nome descrittivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Alcuni dei tipi di dati di attributi di questo set di dati sono _numerico_ oppure _booleano_, anche se questi possono essere interpretati come stringhe in base al **Power Query**. Selezionare l'icona del tipo di attributo nella parte superiore di ciascuna intestazione di colonna per modificare le colonne elencate di seguito per i tipi seguenti:

* **Numero decimale:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True o False:** Fine settimana; Ricavi

![Modificare il tipo di dati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Il **stima binaria** si eseguirà il training di modelli richiede un campo booleano come un'etichetta che identifica i risultati dalle ultime osservazioni. In questo set di dati, il _ricavi_ attributo indica l'acquisto e questo attributo è già disponibile come un valore booleano. Pertanto, non dobbiamo aggiungere una colonna calcolata per l'etichetta. In altri set di dati, potrebbe essere necessario trasformare gli attributi di etichetta esistenti in una colonna booleana.

Selezionare **Fine** per chiudere l'Editor di Power Query. Viene visualizzato l'elenco di entità con la _visitatori Online_ dati è stata aggiunta. Selezionare **salvare** nell'angolo superiore destro, specificare un nome per il flusso di dati e quindi selezionare **salvare** nella finestra di dialogo, come illustrato nell'immagine seguente.

![Salvare il flusso di dati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Aggiornare il flusso di dati

Il salvataggio dei risultati del flusso di dati in viene visualizzata una notifica che informa che è stato salvato il flusso di dati. Selezionare **Aggiorna ora** acquisire i dati dall'origine nel flusso di dati.

![Aggiorna adesso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selezionare **Chiudi** nell'angolo in alto a destra e attendere il completamento dell'aggiornamento del flusso di dati.

È anche possibile aggiornare il flusso di dati usando il **azioni** comandi. Il flusso di dati mostra il timestamp di quando l'aggiornamento è stata completata.

![Timestamp dell'aggiornamento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Creare ed eseguire il training di un modello di machine learning

Selezionare il flusso di dati dopo aver completato l'aggiornamento. Per aggiungere un modello di machine learning, selezionare il **modello di Machine Learning applicate** pulsante il **azioni** elencati per l'entità di base che contiene le informazioni sull'etichetta e i dati di training e quindi selezionare **Aggiungi un modello di Machine learning**.

![Aggiungi un modello di Machine Learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

Il primo passaggio per creare il modello di machine learning consiste nell'identificare i dati cronologici, tra cui il campo dell'etichetta che si desidera stimare. Verrà creato il modello di informazioni da questi dati.

Nel caso di set di dati viene usato, questo è il **ricavi** campo. Selezionare **Revenue** come il valore 'campo risultato cronologici' e quindi selezionare **successivo**.

![Selezionare i dati cronologici](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Successivamente, è necessario selezionare il tipo di modello per creare di machine learning. Power BI analizza i valori nel campo risultato cronologici che è stato identificato e suggerisce i tipi di modelli di machine learning che possono essere creati per prevedere quel campo.

In questo caso, poiché si sta stimare un risultato binario del fatto che un utente effettuerà un acquisto o non, selezionare **stima binaria** per il tipo di modello e quindi selezionare il pulsante Avanti.

![Stima binaria selezionato](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Successivamente, Power BI esegue un'analisi preliminare dei dati e suggerisce gli input che è stato possibile usare il modello. È possibile personalizzare i campi di input utilizzati per il modello. Nel nostro set di dati curato per selezionare tutti i campi, selezionare la casella di controllo accanto al nome dell'entità. Selezionare **successivo** per accettare l'input.

![Selezionare la casella di controllo successivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Nel passaggio finale, è necessario fornire un nome per il modello, nonché le etichette descrittive per i risultati da utilizzare nel report generato automaticamente che riepilogano i risultati della convalida del modello. Successivamente è necessario assegnare un nome modello _acquisto con finalità di stima_e le etichette true e false come _acquisto_ e _Purchase No_. Selezionare quindi **Salva**.

![Salvare il modello](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Il modello di machine learning è ora pronto per il training. Selezionare **le opzioni Aggiorna ora** avviare training del modello.

![Aggiorna adesso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Campionamento e normalizzazione dei dati cronologici e dividere il set di dati in due nuove entità viene avviato il processo di training *dati di Training di acquisto con finalità di stima* e *stima di acquisto con finalità di test Dati*.

A seconda delle dimensioni del set di dati, il processo di training può richiedere da pochi minuti a un paio d'ore. A questo punto, è possibile visualizzare il modello nel **di Machine learning i modelli** scheda del flusso di dati. Il _pronti_ lo stato indica che il modello è stato accodato per il training o si trova sotto la formazione.

![Pronto per il training](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Mentre il modello di training, sarà possibile visualizzare o modificare il flusso di dati. È possibile verificare che il modello è in corso il training e convalidato tramite lo stato del flusso di dati. Questa opzione corrisponde a un aggiornamento di dati in corso nel **Dataflows** scheda dell'area di lavoro.

![Nel processo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Una volta completato il training del modello, il flusso di dati viene visualizzato un tempo di aggiornamento aggiornato. È possibile verificare che il training del modello, passando per la **di Machine learning i modelli** scheda nel flusso di dati. Il modello creato deve mostrare lo stato **Trained** e il **ultima training** ora risulterà aggiornata.

![Ultimo sottoposto a training su](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Esaminare il rapporto di convalida del modello

Per esaminare il report di convalida del modello, nel **modelli di Machine learning, s** sceglie il **Visualizza report di prestazioni e applicare il modello** pulsante il **azioni** colonna per il modello . Questo report descrive come è probabile che le prestazioni del modello di machine learning.

Nel **le prestazioni del modello** pagina del report, selezionare **fattori di influenza chiave** per visualizzare i predittori superiore per il modello. È possibile selezionare uno dei predittori per vedere come la distribuzione di risultato associato tale predittore.

![Prestazioni del modello](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

È possibile usare la **soglia di probabilità** filtro dei dati nella pagina delle prestazioni dei modelli per esaminare la relativa influenza sulla precisione e richiamo per il modello.

![Probability threshold](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Le altre pagine del report descrivono le metriche delle prestazioni statistica per il modello.

Il report include anche una pagina di dettagli di Training che descrive le diverse iterazioni che sono stati eseguiti, come le funzionalità sono stati estratti dagli input e gli iperparametri per il modello finale utilizzato.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Applicare il modello a un'entità del flusso di dati

Selezionare il **Applica modello** nella parte superiore del report per richiamare questo modello quando viene aggiornato il flusso di dati. Nel **applica** finestra di dialogo è possibile specificare l'entità di destinazione che contiene i dati di origine a cui deve essere applicato il modello.

![Applica il modello](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quando richiesto, è necessario **Aggiorna** il flusso di dati per visualizzare in anteprima i risultati del modello.

L'applicazione del modello creerà una nuova entità, con il suffisso **arricchiti < model_name >** aggiunto all'entità a cui è applicato il modello. In questo caso, l'applicazione del modello per il **OnlineShoppers** entità creerà **OnlineShoppers arricchiti acquisto con finalità di stima**, che include l'output stimato dal modello.

Applicare un modello di stima binaria aggiunte tre colonne con risultato stimato, punteggio di probabilità e i principali fattori di influenza di record specifici per la stima, ognuna con prefisso con il nome di colonna specificato.

![Tre colonne del risultato](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

A causa di un problema noto, le colonne di output con punteggio nell'entità arricchiti sono accessibili solo da Power BI Desktop. Per visualizzare un'anteprima nel servizio, è necessario usare un'entità di anteprima speciale.

Una volta completato l'aggiornamento del flusso di dati, è possibile selezionare i **OnlineShoppers arricchiti acquisto con finalità di stima anteprima** entità per visualizzare i risultati.

![Visualizzare i risultati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Usando l'output con punteggio provenienti dal modello in un report di Power BI

Per usare l'output con punteggio del modello di machine learning, è possibile connettersi al flusso di dati da Power BI desktop, usando il connettore di flussi di dati. Il **OnlineShoppers arricchiti acquisto con finalità di stima** entità può ora essere usato per incorporare le stime dal modello di report di Power BI.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è creato e applicato a un modello di stima binaria in Power BI attenendosi alla procedura seguente:

* Creare un flusso di dati con i dati di input
* Creare ed eseguire il training di un modello di machine learning
* Esaminare il rapporto di convalida del modello
* Applicare il modello a un'entità del flusso di dati
* Usando l'output con punteggio provenienti dal modello in un report di Power BI

Per altre informazioni su automazione di Machine Learning in Power BI, vedere [automatizzati di Machine Learning in Power BI (anteprima)](service-machine-learning-automated.md).
