---
title: Creare un report impaginato con un set di dati condiviso di Power BI - Power BI Report Builder
description: Creare un report impaginato in Power BI Report Builder basato su un set di dati condiviso di Power BI.
ms.date: 01/03/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 335b93720718bb72027c29c6093aad952cc4cdb2
ms.sourcegitcommit: b09de56e971b8844a3771413d1f56d49b31baaaf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691477"
---
# <a name="create-a-paginated-report-based-on-a-power-bi-shared-dataset"></a>Creare un report impaginato basato su un set di dati condiviso di Power BI

È possibile usare un set di dati creato in Power BI Desktop come origine dati per i report impaginati di Generatore report di Power BI. Si immagini questo scenario: è stato creato un report di Power BI in Power BI Desktop. È stato dedicato molto tempo alla progettazione del modello di dati e quindi è stato creato un bellissimo report di Power BI con molti oggetti visivi interessanti. Il report include una matrice con molte righe, quindi è necessario scorrere per visualizzarle tutte. I lettori del report vogliono un report da poter stampare, in cui siano visibili tutte le righe della matrice. A tale scopo, è possibile usare un report impaginato di Power BI: stampare una tabella o una matrice che occupa più pagine, con intestazioni e piè di pagina e un layout di pagina perfetto progettato dall'utente. Questo report corrisponderà al report di Power BI Desktop. Si vuole che siano basati sugli stessi dati, senza discrepanze, quindi si usa lo stesso set di dati.

![Dal report di Power BI Desktop al report impaginato di Generatore Report](media/report-builder-shared-datasets/power-bi-desktop-report-builder-arrow-26-pgs.png)

Non è necessario che il set di dati si trovi in un'area di lavoro con capacità Premium né che l'utente sia membro di tale area di lavoro. È sufficiente avere l'[autorizzazione di creazione](service-datasets-build-permissions.md) per il set di dati. Per pubblicare il report impaginato, è necessaria una licenza di Power BI Pro. È anche necessario almeno un ruolo Collaboratore per un'area di lavoro con capacità Premium.

## <a name="what-you-need"></a>Elementi necessari

Ecco un elenco degli elementi necessari e non necessari per usare un set di dati condiviso in Generatore report di Power BI.

- Generatore report di Power BI. [Scaricare e installare Generatore report di Power BI](https://go.microsoft.com/fwlink/?linkid=2086513).
- Per accedere a un set di dati di Power BI, è necessaria l'autorizzazione di creazione per il set di dati. Leggere le informazioni sull'[autorizzazione di creazione](service-datasets-build-permissions.md).
- Non è necessaria una licenza di Power BI Pro per creare un report impaginato in Generatore report. 
- È necessaria una licenza di Power BI Pro per pubblicare il report impaginato. È anche necessario almeno un ruolo Collaboratore per un'area di lavoro con capacità Premium. 
- Facoltativo: per seguire questo articolo, è possibile scaricare il [file con estensione pbix dell'esempio di analisi delle vendite al dettaglio](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) di Power BI Desktop, aprirlo in Power BI Desktop e aggiungere una tabella con numerose colonne. Nel riquadro **Formato** disattivare **Totali**. Pubblicare quindi il report in un'area di lavoro nel servizio Power BI.

    ![Totali disattivati](media/report-builder-shared-datasets/power-bi-desktop-totals-off.png)

## <a name="connect-to-the-power-bi-dataset"></a>Connettersi al set di dati di Power BI

1. Aprire Generatore report di Power BI.
1. Selezionare **Accedi** nell'angolo superiore destro di Generatore report per accedere al proprio account di Power BI.
1. Nel riquadro Dati report selezionare **Nuovo** > **Connessione al set di dati di Power BI**.

    ![Nuovo set di dati nel riquadro Dati report](media/report-builder-shared-datasets/power-bi-report-builder-new-dataset.png)

    > [!NOTE]
    > Non è possibile creare l'origine dati o il set di dati per un set di dati di Power BI usando le procedure guidate di creazione di una tabella, una matrice o un grafico di Generatore report. Dopo la creazione, è possibile usare le procedure guidate per creare tabelle, matrici o grafici basati su di essi.

1. Cercare il set di dati o l'area di lavoro in cui si trova > **Seleziona**.
    Generatore report inserisce il nome del set di dati.

    ![Selezionare il set di dati](media/report-builder-shared-datasets/power-bi-report-builder-select-dataset.png)
    
1. Il set di dati è elencato in Origini dati nel riquadro Dati report.

    ![Set di dati in Origini dati nel riquadro Dati report](media/report-builder-shared-datasets/power-bi-report-builder-data-source.png)

    Tenere presente che è possibile connettersi a più set di dati di Power BI e ad altre origini dati nello stesso report impaginato.


## <a name="get-the-query-for-the-dataset"></a>Ottenere la query per il set di dati

Quando si vuole che i dati nel report di Power BI e nel report di Generatore report corrispondano, non è sufficiente connettersi al set di dati. È necessaria anche la query basata su tale set di dati.

1. Aprire il report di Power BI (con estensione pbix) in Power BI Desktop.
1. Assicurarsi che nel report sia presente una tabella contenente tutti i dati che devono essere presenti nel report impaginato.

1. Nella scheda **Visualizza** della barra multifunzione selezionare **Analizzatore prestazioni**.

    ![Aprire l'analizzatore prestazioni](media/report-builder-shared-datasets/power-bi-performance-analyzer.png)

1. Nel riquadro **Analizzatore prestazioni** selezionare **Avvia registrazione** e quindi **Aggiorna gli oggetti visivi**.

    ![Aggiorna gli oggetti visivi](media/report-builder-shared-datasets/power-bi-performance-analyzer-refresh-visuals.png)

1. Espandere il segno più ( **+** ) accanto al nome della tabella e selezionare **Copia la query**. La query è la formula DAX necessaria per il set di dati in Generatore report di Power BI.

    ![Copiare la query](media/report-builder-shared-datasets/power-bi-performance-analyzer-copy-query.png)

## <a name="create-the-dataset-with-the-query"></a>Creare il set di dati con la query

1. Tornare a Generatore report di Power BI.
1. Fare clic con il pulsante destro del mouse sul set di dati in **Origini dati** e scegliere **Aggiungi set di dati**.

    ![Aggiungi set di dati](media/report-builder-shared-datasets/power-bi-report-builder-add-dataset.png)

1. Nella finestra Proprietà set di dati specificare un nome e selezionare **Progettazione query**.

4. Verificare che sia selezionata l'opzione **DAX** e deselezionare l'icona **Modalità progettazione**.

    ![Progettazione query di Generatore report](media/report-builder-shared-datasets/power-bi-report-builder-query-designer.png)

1. Nella casella superiore incollare la query copiata da Power BI Desktop.

1. Selezionare **Esegui query** (il punto esclamativo rosso, !) per assicurarsi che la query funzioni. 

    ![Eseguire la query](media/report-builder-shared-datasets/power-bi-report-builder-run-query.png)

    I risultati della query verranno visualizzati nella casella inferiore.

    ![Risultati query](media/report-builder-shared-datasets/power-bi-report-builder-query-results.png)

1. Seleziona **OK**.

    La query verrà visualizzata nella sezione **Query** della finestra di dialogo **Proprietà set di dati**.

    ![Finestra di dialogo Proprietà set di dati](media/report-builder-shared-datasets/power-bi-report-builder-dataset-properties.png)

1. Seleziona **OK**.

    A questo punto è possibile visualizzare il nuovo set di dati con un elenco dei relativi campi nel riquadro Dati report.

    ![Set di dati nel riquadro Dati report](media/report-builder-shared-datasets/power-bi-report-builder-dataset.png)

## <a name="create-a-table-in-the-report"></a>Creare una tabella nel report

Un modo rapido per creare una tabella consiste nell'usare la Creazione guidata tabella.

1. Nella scheda **Inserisci** della barra multifunzione selezionare **Tabella** > **Creazione guidata tabella**.

    ![Avviare la Creazione guidata tabella](media/report-builder-shared-datasets/power-bi-report-builder-table-wizard.png)

1. Scegliere il set di dati creato con la query DAX > **Avanti**.

    ![Scegliere un set di dati](media/report-builder-shared-datasets/power-bi-report-builder-choose-dataset.png)

1. Per creare una tabella flat, selezionare i campi desiderati in **Campi disponibili**. È possibile selezionare più campi contemporaneamente selezionando il primo campo desiderato, tenendo premuto MAIUSC e selezionando l'ultimo.

    ![Selezionare più campi](media/report-builder-shared-datasets/power-bi-report-builder-select-fields.png)

1. Trascinare i campi nella casella **Valori** > **Avanti**.

    ![Creazione guidata tabella](media/report-builder-shared-datasets/power-bi-report-builder-value-fields.png)

1. Scegliere le opzioni di layout desiderate > **Avanti**.

1. Fare clic su **Fine**.
    La tabella verrà aperta in visualizzazione Progettazione.

    ![Visualizzazione Progettazione report](media/report-builder-shared-datasets/power-bi-report-builder-design-view.png)

1. Selezionare **Fare clic per aggiungere il titolo** e aggiungere un titolo.

1. Selezionare **Esegui** per visualizzare in anteprima il report.

    ![Anteprima report](media/report-builder-shared-datasets/power-bi-report-builder-preview.png)

1. Selezionare **Layout di stampa** per vedere l'aspetto del report quando verrà stampato. 

    Il layout del report richiede alcune modifiche. Ha 54 pagine, perché le colonne e i margini fanno sì che la tabella occupi la larghezza di due pagine.

    ![Layout di stampa del report](media/report-builder-shared-datasets/power-bi-report-builder-print-layout-2-p1-p2.png)

## <a name="format-the-report"></a>Formattare il report

Sono disponibili diverse opzioni di formattazione per fare in modo che la tabella occupi una sola pagina. 

1. È possibile ridurre i margini di pagina nel riquadro Proprietà. Se il riquadro Proprietà non è visualizzato, fare clic sulla scheda **Visualizza** della barra multifunzione e selezionare la casella **Proprietà**.

1. Selezionare il report, non la tabella o il titolo.
1. Nel riquadro **Proprietà report**, in **Pagina** espandere **Margini** e modificare ogni margine impostandolo su **2 cm**.

    ![Impostare i margini di pagina](media/report-builder-shared-datasets/power-bi-report-builder-page-margins.png)

1. È anche possibile impostare una larghezza inferiore per le colonne. Selezionare il bordo della colonna e trascinare il lato destro verso sinistra.

    ![Impostare la larghezza delle colonne](media/report-builder-shared-datasets/power-bi-report-builder-column-width.png)

1. Un'altra opzione consiste nel verificare che i valori numerici siano formattati correttamente. Selezionare una cella con un valore numerico. 
    > [!TIP]
    > È possibile formattare più celle contemporaneamente tenendo premuto MAIUSC mentre si selezionano le altre celle.

    ![Selezionare più celle](media/report-builder-shared-datasets/power-bi-report-builder-select-cells.png)

1. Nella scheda **Home** della barra multifunzione, nella sezione **Numero** modificare il formato **Predefinito** in un formato numerico, ad esempio **Valuta**.

    ![Impostare il formato dei numeri](media/report-builder-shared-datasets/power-bi-report-builder-number-format.png)

1. Modificare lo stile di **Segnaposto** in **Valori di esempio** per poter vedere la formattazione nella cella. 

    ![Visualizzare i valori di esempio](media/report-builder-shared-datasets/power-bi-report-builder-sample-values.png)

1. Se appropriato, nella sezione **Numero** diminuire i numeri decimali per risparmiare spazio.

### <a name="getting-rid-of-blank-pages"></a>Eliminazione delle pagine vuote

Anche dopo aver impostato una larghezza inferiore per i margini e le colonne della tabella, è possibile che una pagina ogni due sia vuota. Questo problema dipende da una questione matematica. 

I margini di pagina impostati sommati alla larghezza del *corpo* del report devono dare un risultato inferiore alla larghezza del formato del report.

Si immagini, ad esempio, che il formato del report sia 21 x 28 cm e che siano stati impostati margini laterali di 2 cm. La somma dei due margini fa 4 cm, quindi il corpo deve avere una larghezza inferiore a 17 cm.

1. Selezionare il bordo destro dell'area di progettazione del report e trascinarlo in modo che sia inferiore al valore desiderato sul righello. 

    > [!TIP]
    > È possibile impostare il valore in modo più accurato nelle proprietà di **Corpo**. In **Dimensioni** impostare la proprietà **Larghezza**.

    ![Impostare le dimensioni del corpo](media/report-builder-shared-datasets/power-bi-report-builder-body-size.png)

1. Selezionare **Esegui** per visualizzare l'anteprima del report e assicurarsi di avere eliminato le pagine vuote. Il report ora ha solo 26 pagine invece delle 54 originali. Operazione riuscita.

    ![Evitare di stampare le pagine vuote](media/report-builder-shared-datasets/power-bi-report-builder-print-26-pgs.png)

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni 

- Per i set di dati che usano una connessione dinamica ad Analysis Services, è possibile connettersi direttamente usando la connessione di Analysis Services sottostante invece di un set di dati condiviso.
- I set di dati con l'indicazione Innalzato o Certificato vengono visualizzati nell'elenco di set di dati disponibili, ma non contrassegnati come tali. 

## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)