---
title: 'Esercitazione: Usare Servizi cognitivi in Power BI (anteprima)'
description: In questa esercitazione si useranno Servizi cognitivi e flussi di dati in Power BI.
author: davidiseminger
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 4c19965def178d4260527032820c4109c4fe235f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83281577"
---
# <a name="tutorial-use-cognitive-services-in-power-bi"></a>Esercitazione: Usare Servizi cognitivi in Power BI

Power BI mette a disposizione un set di funzioni di Servizi cognitivi di Azure per arricchire i dati nella preparazione dei dati self-service per i flussi di dati. I servizi attualmente supportati sono [Analisi del sentiment](https://docs.microsoft.com/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-sentiment-analysis), [Estrazione frasi chiave](https://docs.microsoft.com/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-keyword-extraction), [Rilevamento lingua](https://docs.microsoft.com/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-language-detection) e [Assegnazione di tag alle immagini](https://docs.microsoft.com/azure/cognitive-services/computer-vision/concept-tagging-images). Le trasformazioni vengono eseguite nel servizio Power BI e non richiedono una sottoscrizione di Servizi cognitivi di Azure. Questa funzionalità richiede Power BI Premium.

Le trasformazioni di Servizi cognitivi sono supportate nella [preparazione dei dati self-service per i flussi di dati](https://powerbi.microsoft.com/blog/introducing-power-bi-data-prep-wtih-dataflows/). Per iniziare, usare gli esempi dettagliati per l'analisi del testo e l'aggiunta di tag alle immagini riportati di seguito.

In questa esercitazione verranno illustrate le procedure per:

> [!div class="checklist"]
> * Importare dati in Power BI
> * Assegnare un punteggio al sentiment ed estrarre le frasi chiave di una colonna di testo in un flusso di dati
> * Connettersi ai risultati da Power BI Desktop


## <a name="prerequisites"></a>Prerequisiti

Per completare l'esercitazione è necessario quanto segue: 

- Un account di Power BI. Se non si è ancora iscritti a Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.
- Accesso a una capacità di Power BI Premium con il carico di lavoro di Intelligenza artificiale abilitato. Questo carico di lavoro verrà disattivato per impostazione predefinita durante l'anteprima. Se si usa una capacità Premium e le informazioni dettagliate sull'intelligenza artificiale non vengono visualizzate, contattare l'amministratore della capacità Premium per abilitare il carico di lavoro di Intelligenza artificiale nel portale di amministrazione.

## <a name="text-analytics"></a>Analisi del testo

Seguire i passaggi in questa sezione per completare la parte dell'esercitazione relativa all'analisi del testo.

### <a name="step-1-apply-sentiment-scoring-in-power-bi-service"></a>Passaggio 1: Applicare il processo di assegnazione di un punteggio al sentiment nel servizio Power BI

Per iniziare, passare a un'area di lavoro di Power BI con capacità Premium e creare un nuovo flusso di dati usando il pulsante **Crea** nell'angolo superiore destro dello schermo.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_01.png)

Nella finestra di dialogo del flusso di dati, che contiene le opzioni per la creazione di un nuovo flusso di dati, selezionare **Aggiungi nuove entità**. Scegliere quindi **Testo/CSV** dal menu delle origini dati.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_02.png)

Nel campo URL incollare l'URL [https://pbiaitutorials.blob.core.windows.net/textanalytics/FabrikamComments.csv](https://pbiaitutorials.blob.core.windows.net/textanalytics/FabrikamComments.csv) e fare clic su **Avanti**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_03.png)

A questo punto i dati sono pronti per l'analisi del testo ed è possibile usare le funzioni Analisi del sentiment ed Estrazione frasi chiave nella colonna dei commenti dei clienti.

Nell'editor di Power Query selezionare **Informazioni dettagliate sull'intelligenza artificiale**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_04.png)

Espandere la cartella **Servizi cognitivi** e selezionare la funzione che si vuole usare. Questo esempio assegna un punteggio al sentiment della colonna dei commenti, ma è possibile seguire gli stessi passaggi per provare le funzioni Rilevamento lingua ed Estrazione frasi chiave.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_05.png)

Dopo aver selezionato una funzione, vengono visualizzati i campi obbligatori e facoltativi. Per assegnare un punteggio al sentiment delle recensioni di esempio, selezionare la colonna delle recensioni come input di testo. Le informazioni delle impostazioni cultura sono un input facoltativo che richiede un formato ISO. Ad esempio, se si vuole che il testo sia considerato come in lingua inglese, immettere "en". Se il campo viene lasciato vuoto, Power BI rileva la lingua del valore di input prima di assegnare un punteggio al sentiment.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_06.png)

Selezionare **Richiama** per eseguire la funzione. Viene aggiunta alla tabella una nuova colonna con il punteggio del sentiment per ogni riga. È possibile tornare a **Informazioni dettagliate sull'intelligenza artificiale** per estrarre le frasi chiave del testo delle recensioni nello stesso modo.

Completate le trasformazioni, cambiare il nome della query in "Customer comments" e selezionare **Fine**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_07.png)

Scegliere **Salva** per salvare il flusso di dati e assegnargli il nome Fabrikam. Selezionare il pulsante **Aggiorna adesso** visualizzato dopo il salvataggio del flusso di dati.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_08.png)

Dopo aver salvato e aggiornato il flusso di dati, è possibile usarlo in un report di Power BI.

### <a name="step-2-connect-from-power-bi-desktop"></a>Passaggio 2: Connettersi da Power BI Desktop

Aprire Power BI Desktop. Nella scheda Home della barra multifunzione selezionare **Recupera dati**.

Passare a **Flussi di dati Power BI (beta**) nella sezione Power BI e selezionare **Connetti**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_09.png)

Trattandosi di una funzionalità di anteprima, il connettore chiederà di accettare le condizioni dell'anteprima. Dopo averle accettate, accedere con l'account dell'organizzazione.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_10.png)

Selezionare il flusso di dati appena creato. Passare alla tabella dei commenti dei clienti e fare clic su **Carica**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_11.png)

Ora che i dati sono caricati è possibile iniziare a creare un report.

## <a name="image-tagging"></a>Assegnazione di tag alle immagini

Passare a un'area di lavoro di Power BI con capacità Premium. Creare un nuovo flusso di dati usando il pulsante **Crea** nell'angolo superiore destro dello schermo.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_12.png)

Selezionare **Aggiungi nuove entità**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_13.png)

Quando viene chiesto di scegliere un'origine dati, selezionare **Query vuota**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_14.png)

Copiare la query seguente nell'editor di query e fare clic su Avanti. È possibile sostituire i percorsi degli URL seguenti con altre immagini o aggiungere altre righe. La funzione *Web.Contents* importa l'URL immagine in formato binario. Se si ha un'origine dati con immagini archiviate in formato binario, è possibile usarla direttamente.


```python
let
  Source = Table.FromRows({
  { Web.Contents("https://images.pexels.com/photos/87452/flowers-background-butterflies-beautiful-87452.jpeg") },
  { Web.Contents("https://upload.wikimedia.org/wikipedia/commons/5/53/Colosseum_in_Rome%2C_Italy_-_April_2007.jpg") }}, { "Image" })
in
  Source
```

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_15.png)

Quando viene chiesto di immettere le credenziali, selezionare *Anonima*.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_16.png)

Viene visualizzata l'immagine seguente.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_17.png)

Viene chiesto di immettere le credenziali per ogni singola pagina Web.

Nell'editor di query selezionare **Informazioni dettagliate sull'intelligenza artificiale**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_18.png)

Accedere quindi con l'**account aziendale**.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_19.png)

Selezionare la funzione di assegnazione di tag alle immagini, immettere _[Binary]_ nel campo della colonna e _en_ nel campo delle informazioni delle impostazioni cultura. 

> [!NOTE]
> Attualmente non è possibile selezionare una colonna usando un elenco a discesa, ma questo aspetto verrà risolto il più presto possibile durante l'anteprima privata.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_20.png)

Nell'editor di funzioni rimuovere le virgolette attorno al nome della colonna. 

> [!NOTE]
> La rimozione delle virgolette è una soluzione alternativa temporanea, in attesa della soluzione definitiva durante l'anteprima.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_21.png)

La funzione restituisce un record con i tag sia in formato con valori separati da virgole che come record JSON. Selezionare il pulsante di espansione per aggiungere uno o entrambi i tag come colonne alla tabella.

![Creare un flusso di dati](media/service-tutorial-using-cognitive-services/tutorial-using-cognitive-services_22.png)

Selezionare **Fine** e salvare il flusso di dati. Una volta aggiornato il flusso di dati, è possibile connettersi a esso da Power BI Desktop usando i connettori di flussi di dati (vedere i passaggi a pagina 5 di questo documento).

## <a name="clean-up-resources"></a>Pulire le risorse

Quando non serve più, eliminare la query facendo clic con il pulsante destro del mouse sul relativo nome nell'editor di Power Query e scegliendo **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione sono state applicate le funzioni di assegnazione del punteggio e di assegnazione di tag alle immagini in un flusso di dati di Power BI. Per altre informazioni su Servizi cognitivi in Power BI, leggere gli articoli seguenti.

* [Servizi cognitivi in Azure](https://docs.microsoft.com/azure/cognitive-services/)
* Introduzione alla [preparazione dei dati self-service nei flussi di dati](../transform-model/service-dataflows-overview.md)
* Altre informazioni su [Power BI Premium](https://powerbi.microsoft.com/power-bi-premium/)

Potrebbero essere interessanti anche gli articoli seguenti.

* [Esercitazione: Richiamare un modello di Machine Learning Studio (versione classica) in Power BI (anteprima)](service-tutorial-invoke-machine-learning-model.md)
* [Integrazione di Azure Machine Learning in Power BI (anteprima)](../transform-model/service-machine-learning-integration.md)
* [Servizi cognitivi in Power BI (anteprima)](../transform-model/service-cognitive-services.md)