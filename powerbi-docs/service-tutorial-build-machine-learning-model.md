---
title: 'Esercitazione: Creare un modello di Machine Learning in Power BI (anteprima)'
description: In questa esercitazione viene creato un modello di Machine Learning in Power BI.
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
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406742"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Esercitazione: Creare un modello di Machine Learning in Power BI (anteprima)

In questo articolo dell'esercitazione viene usato il **Machine Learning automatizzato** per creare e applicare un modello di previsione per dati binari in Power BI. L'esercitazione include le istruzioni per la creazione di un flusso di dati di Power BI e l'uso delle entità definite nel flusso di dati per eseguire il training e la convalida di un modello di Machine Learning direttamente in Power BI. Il modello viene quindi usato per l'assegnazione dei punteggi per generare le previsioni.

Viene innanzitutto creato un modello di Machine Learning di previsione per dati binari per prevedere la finalità di acquisto degli acquirenti online in base a un set di attributi della sessione online. Per questo esercizio viene usato un set di dati di Machine Learning benchmark. Dopo aver eseguito il training di un modello, Power BI genera automaticamente un report di convalida che illustra i risultati del modello. È quindi possibile esaminare il report di convalida e applicare il modello ai dati per l'assegnazione dei punteggi.

Questa esercitazione prevede i passaggi seguenti:

> [!div class="checklist"]
> * Creare un flusso di dati con i dati di input
> * Creare ed eseguire il training di un modello di Machine Learning
> * Esaminare il report di convalida del modello
> * Applicare il modello a un'entità del flusso di dati
> * Uso dell'output con punteggio dal modello di un report Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Creare un flusso di dati con i dati di input

La prima parte di questa esercitazione consiste nel creare un flusso di dati con i dati di input. Questo processo richiede alcuni passaggi, come illustrato nelle sezioni seguenti, a partire dal recupero dei dati.

### <a name="get-data"></a>Recupera dati

Il primo passaggio per la creazione di un flusso di dati consiste nell'avere le origini dati pronte. In questo caso viene usato un set di dati di Machine Learning di un set di sessioni online, alcune delle quali sono terminate con un acquisto. Il set di dati contiene un set di attributi relativi a queste sessioni che verrà usato per il training del modello.

È possibile scaricare il set di dati dal sito Web UC Irvine.  Il set di dati per questa esercitazione è disponibile anche al collegamento seguente: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Creare le entità

Per creare le entità nel flusso di dati, accedere al servizio Power BI e passare a un'area di lavoro nella propria capacità dedicata in cui sia abilitata l'anteprima delle funzionalità di intelligenza artificiale.

Se non è già presente un'area di lavoro, è possibile crearne una selezionando **Aree di lavoro** nel menu di spostamento di sinistra nel servizio Power BI e selezionando **Crea area di lavoro per le app** nella parte inferiore del pannello visualizzato. Viene aperto un pannello a destra in cui immettere i dettagli dell'area di lavoro. Immettere il nome di un'area di lavoro e selezionare **Avanzate**. Verificare che l'area di lavoro usi la capacità dedicata con il pulsante di opzione e che sia assegnata a un'istanza di capacità dedicata per cui è attivata l'anteprima di intelligenza artificiale. Selezionare quindi **Salva**.

![Crea un'area di lavoro](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Dopo aver creato l'area di lavoro, è possibile selezionare **Ignora** nella parte inferiore destra della schermata iniziale, come illustrato nell'immagine seguente.

![Ignorare se è presente un'area di lavoro](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selezionare la scheda **Flussi di dati (anteprima)** . Selezionare il pulsante **Crea** nella parte superiore destra dell'area di lavoro e quindi selezionare **Flusso di dati**.

![Creare il flusso di dati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selezionare **Aggiungi nuove entità**. Viene avviato un editor di **Power Query** nel browser.

![Aggiungi nuove entità](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selezionare **File di testo/File CSV** come origine dati, come illustrato nell'immagine seguente.

![File di testo/File CSF selezionato](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

In **Connessione a un'origine dati** copiare il link seguente a *online_shoppers_intention.csv* nella casella **Percorso file o URL** e quindi selezionare **Avanti**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Percorso file](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

L'editor di Power Query visualizza un'anteprima dei dati del file CSV. Selezionare **Trasforma tabella** nella barra multifunzione dei comandi e quindi selezionare **Usa la prima riga come intestazione** dal menu visualizzato. Viene aggiunto il passaggio di query _Intestazioni alzate di livello_ nella sezione **Passaggi applicati** nella parte destra della schermata. È possibile rinominare la query con un nome più descrittivo modificando il valore nella casella **Nome** disponibile nel riquadro di destra. Ad esempio, è possibile modificare il nome della query in _Online Visitor_.

![Passare a un nome descrittivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Alcuni tipi di dati degli attributi in questo set di dati sono _numerici_ o _booleani_, sebbene possano essere interpretati come stringhe da **Power Query**. Selezionare l'icona del tipo di attributo nella parte superiore di ogni intestazione di colonna per modificare le colonne elencate di seguito nei tipi seguenti:

* **Numero decimale:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Vero/Falso:** Weekend; Revenue

![Modificare il tipo di dati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Il modello **Previsione per dati binari** di cui viene eseguito il training richiede un campo booleano come etichetta che identifica i risultati delle osservazioni precedenti. In questo set di dati l'attributo _Revenue_ indica l'acquisto ed è già disponibile come valore booleano. Non è quindi necessario aggiungere una colonna calcolata per l'etichetta. In altri set di dati potrebbe essere necessario trasformare gli attributi delle etichette esistenti in una colonna booleana.

Selezionare il pulsante **Fine** per chiudere l'editor di Power Query. Viene visualizzato l'elenco delle entità con i dati _Online Visitors_ aggiunti. Selezionare **Salva** nell'angolo superiore destro, specificare un nome per il flusso di dati e quindi selezionare **Salva** nella finestra di dialogo, come illustrato nell'immagine seguente.

![Salvare il flusso di dati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Aggiornare il flusso di dati

Se si salva il flusso di dati, viene visualizzata una notifica che indica che il flusso di dati è stato salvato. Selezionare **Aggiorna adesso** per inserire i dati dell'origine nel flusso di dati.

![Aggiorna adesso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selezionare **Chiudi** nell'angolo in alto a destra e attendere il completamento dell'aggiornamento del flusso di dati.

È possibile aggiornare il flusso di dati anche con i comandi **Azioni**. Il flusso di dati mostra il timestamp al completamento dell'aggiornamento.

![Timestamp dell'aggiornamento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Creare ed eseguire il training di un modello di Machine Learning

Al termine dell'aggiornamento, selezionare il flusso di dati. Per aggiungere un modello di Machine Learning, selezionare il pulsante **Applica modello di ML** nell'elenco **Azioni** dell'entità di base che contiene i dati di training e le informazioni sull'etichetta e quindi selezionare **Aggiungi un modello di Machine Learning**.

![Aggiungi un modello di Machine Learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

Il primo passaggio per la creazione del modello di Machine Learning consiste nell'identificare i dati cronologici, incluso il campo etichetta di cui eseguire la previsione. Il modello verrà creato in base a questi dati.

Nel caso del set di dati in uso, si tratta del campo **Revenue** (Ricavi). Selezionare **Revenue** (Ricavi) come valore 'Campo del risultato cronologico' e quindi selezionare **Avanti**.

![Selezionare i dati cronologici](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Successivamente è necessario selezionare il tipo di modello di Machine Learning da creare. Power BI analizza i valori nel campo dei risultati cronologici identificato e suggerisce i tipi di modelli di Machine Learning che è possibile creare per prevedere il campo.

In questo caso poiché viene eseguita la previsione di un risultato binario che indica se un utente effettuerà un acquisto o meno, selezionare **Previsione per dati binari** come tipo di modello e quindi fare clic su Avanti.

![Previsione per dati binari selezionata](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Power BI esegue quindi un'analisi preliminare dei dati e suggerisce gli input che possono essere usati dal modello. È possibile personalizzare i campi di input usati per il modello. Nel set di dati curato selezionare la casella di controllo accanto al nome dell'entità per selezionare tutti i campi. Selezionare **Avanti** per accettare gli input.

![Seleziona la casella di controllo Avanti](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Nel passaggio finale è necessario specificare un nome per il modello nonché le etichette descrittive per i risultati da usare nel report generato automaticamente che riepiloga i risultati della convalida del modello. È necessario quindi denominare il modello _Purchase Intent Prediction_ (Previsione finalità di acquisto) e le etichette Vero e Falso come _Purchase_ (Acquisto) e _No-Purchase_ (Nessun acquisto). Selezionare quindi **Salva**.

![Salvare il modello](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Il modello di Machine Learning è ora pronto per il training. Selezionare **Aggiorna adesso** per avviare il training del modello.

![Aggiorna adesso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Il processo di training inizierà con il campionamento e la normalizzazione dei dati cronologici e la suddivisione del set di dati in due nuove entità *Purchase Intent Prediction Training Data* (Dati training previsione finalità di acquisto) e *Purchase Intent Prediction Testing Data* (Dati test previsione finalità di acquisto).

A seconda delle dimensioni del set di dati, il processo di training può richiedere da pochi minuti a un paio di ore. A questo punto è possibile visualizzare il modello nella scheda **Modelli di Machine Learning** del flusso di dati. Lo stato _Pronto_ indica che il modello è stato accodato per il training o è in fase di training.

![Pronto per il training](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Durante il training del modello non sarà possibile visualizzare o modificare il flusso di dati. È possibile verificare che il modello sia in fase di training e convalidato controllando lo stato del flusso di dati. Viene visualizzato un aggiornamento dei dati in corso nella scheda **Flussi di dati** dell'area di lavoro.

![In corso](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Una volta completato il training del modello, il flusso di dati visualizza una nuova ora di aggiornamento. È possibile verificare che il modello sia in fase di training, passando alla scheda **Modelli di Machine Learning** nel flusso di dati. Il modello creato dovrebbe visualizzare lo stato **Con training** e l'ora **Ultimo training** dovrebbe essere aggiornata.

![Ultimo training](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Esaminare il report di convalida del modello

Per esaminare il report di convalida del modello, in **Modelli di Machine Learning** selezionare il pulsante **Visualizza il report prestazioni e applica il modello** nella colonna **Azioni** per il modello. Questo report descrive le prestazioni probabili del modello di Machine Learning.

Nella pagina **Prestazioni del modello** del report selezionare **Fattori di influenza chiave** per visualizzare i fattori di previsione principali del modello. È possibile selezionare uno dei fattori di previsione per visualizzare la distribuzione dei risultati associata al fattore di previsione.

![Prestazioni del modello](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

È possibile usare il filtro dei dati **Soglia probabilità** nella pagina Prestazioni del modello per esaminarne l'influenza sulla precisione e il richiamo del modello.

![Probability threshold](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Le altre pagine del report descrivono le metriche delle prestazioni statistiche per il modello.

Il report include anche una pagina Dettagli del training che descrive le diverse iterazioni eseguite, il modo in cui le funzionalità sono state estratte dagli input e gli iperparametri usati per il modello finale.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Applicare il modello a un'entità del flusso di dati

Selezionare il pulsante **Applica modello** nella parte superiore del report per richiamare il modello quando viene aggiornato il flusso di dati. Nella finestra di dialogo **Applica** è possibile specificare l'entità di destinazione con i dati di origine a cui applicare il modello.

![Applica il modello](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quando richiesto, scegliere **Aggiorna** per aggiornare il flusso di dati per visualizzare in anteprima i risultati del modello.

Se si applica il modello, viene creata una nuova entità con il suffisso **enriched <nome_modello>** aggiunto all'entità a cui è stato applicato il modello. In questo caso l'applicazione del modello all'entità **OnlineShoppers** crea l'entità **OnlineShoppers enriched Purchase Intent Prediction** che include l'output previsto del modello.

L'applicazione di un modello Previsione per dati binari aggiunge tre colonne con il risultato previsto, il punteggio di probabilità e i principali fattori di influenza specifici del record per la previsione, ognuno con il nome di colonna specificato.

![Tre colonne di risultati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

A causa di un problema noto, le colonne di output con punteggio nell'entità arricchita sono accessibili solo da Power BI Desktop. Per visualizzare le anteprime nel servizio, è necessario usare un'entità di anteprima speciale.

Una volta completato l'aggiornamento del flusso di dati, è possibile selezionare l'entità **OnlineShoppers enriched Purchase Intent Prediction Preview** per visualizzare i risultati.

![Visualizzare i risultati](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Uso dell'output con punteggio dal modello di un report Power BI

Per usare l'output con punteggio del modello di Machine Learning, è possibile connettersi al flusso di dati da Power BI Desktop usando il connettore Flussi di dati. L'entità **OnlineShoppers enriched Purchase Intent Prediction** può ora essere usata per incorporare le previsioni del modello nei report di Power BI.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato creato e applicato un modello di previsione per dati binari in Power BI eseguendo i passaggi seguenti:

* Creare un flusso di dati con i dati di input
* Creare ed eseguire il training di un modello di Machine Learning
* Esaminare il report di convalida del modello
* Applicare il modello a un'entità del flusso di dati
* Uso dell'output con punteggio dal modello di un report Power BI

Per altre informazioni sull'automazione di Machine Learning in Power BI, vedere [Machine Learning automatizzato in Power BI (anteprima)](service-machine-learning-automated.md).
