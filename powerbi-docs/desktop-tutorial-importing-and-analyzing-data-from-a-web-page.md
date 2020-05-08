---
title: 'Esercitazione: Importare e analizzare i dati da una pagina Web'
description: 'Esercitazione: Importare e analizzare i dati da una pagina Web con Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 5497c56f358470d0d24f69f0d67865dbbd7839a3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "77026739"
---
# <a name="tutorial-analyze-webpage-data-by-using-power-bi-desktop"></a>Esercitazione: Analizzare i dati di una pagina Web con Power BI Desktop

Si supponga di voler creare un report sui vincitori delle diverse edizioni della Coppa UEFA. Con Power BI Desktop, è possibile importare questi dati da una pagina Web in un report e creare le relative visualizzazioni. In questa esercitazione viene illustrato come usare Power BI Desktop per:

- Connettersi a un'origine dati Web e spostarsi tra le tabelle disponibili.
- Definire una nuova forma dei dati e trasformare i dati nell'editor di Power Query.
- Assegnare un nome a una query e importarla in un report di Power BI Desktop.
- Creare e personalizzare una mappa e una visualizzazione grafico a torta.

## <a name="connect-to-a-web-data-source"></a>Connettersi a un'origine dati Web

I dati sui vincitori della Coppa UEFA sono disponibili nella tabella dei risultati nella pagina di Wikipedia sulla Coppa UEFA all'indirizzo https://en.wikipedia.org/wiki/UEFA_European_Football_Championship. 

![Tabella dei risultati di Wikipedia](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

Le connessioni Web vengono stabilite solo tramite l'autenticazione di base. I siti Web che richiedono l'autenticazione potrebbero non funzionare correttamente con il connettore Web.

Per importare i dati:

1. Nella scheda **Home** della barra multifunzione di Power BI Desktop fare clic sul menu a discesa **Dati** e quindi selezionare **Web**.

   ![Dati - Barra multifunzione](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 

   >[!NOTE]
   >È anche possibile selezionare direttamente la voce **Dati** oppure selezionare **Recupera dati** nella finestra di dialogo delle attività iniziali di Power BI Desktop, quindi selezionare **Web** nella sezione **Tutto** o **Altro** della finestra di dialogo **Recupera dati** e poi selezionare **Connetti**.

1. Nella finestra di dialogo **Da Web** incollare l'URL `https://en.wikipedia.org/wiki/UEFA_European_Football_Championship` nella casella di testo **URL** e quindi scegliere **OK**.

    ![Finestra di dialogo Recupera dati](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)

   Dopo la connessione alla pagina web di Wikipedia, la finestra di dialogo **Strumento di navigazione** visualizza un elenco delle tabelle disponibili nella pagina. È possibile selezionare uno qualsiasi dei nomi di tabella per visualizzare l'anteprima dei dati. La tabella **Results[edit]** contiene i dati richiesti, anche se non sono esattamente nella forma desiderata. Ora si procederà a definire una nuova forma per i dati e a pulirli prima di caricarli nel report.

   ![Finestra di dialogo Strumento di navigazione](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

   >[!NOTE]
   >Il riquadro **Anteprima** visualizza la tabella più recente selezionata, ma tutte le tabelle selezionate vengono caricate nell'editor di Power Query quando si sceglie **Trasforma dati** o **Carica**.

1. Selezionare la tabella **Results[edit]** nell'elenco **Strumento di navigazione** e quindi scegliere **Trasforma dati**.

   Nell'**editor di Power Query** viene aperta un'anteprima della tabella, in cui è possibile applicare trasformazioni per pulire i dati.

   ![Editor di Power Query](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="shape-data-in-power-query-editor"></a>Definire una forma per i dati nell'Editor di Power Query

È possibile rendere i dati più semplici da analizzare visualizzando solo gli anni e i paesi che hanno vinto. È possibile usare l'editor di Power Query per eseguire questi passaggi per la modifica della forma dei dati e la relativa pulizia.

Per prima cosa rimuovere dalla tabella tutte le colonne meno due. Rinominare queste colonne come *Year* e *Country* in una fase successiva del processo.

1. Nella griglia dell'**editor di Power Query** selezionare le colonne. Per selezionare più elementi tenere premuto CTRL.

1. Fare clic con il pulsante destro del mouse e selezionare **Rimuovi altre colonne** oppure selezionare **Rimuovi colonne** > **Rimuovi altre colonne** nel gruppo **Gestisci colonne** nella scheda **Home** della barra multifunzione per rimuovere tutte le altre colonne dalla tabella.

   ![Menu a discesa Rimuovi altre colonne](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png)

   o

   ![Rimuovi altre colonne - Barra multifunzione](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

Quindi rimuovere la parola superflua *Details* dalle celle della prima colonna.

1. Selezionare la prima colonna.

1. Fare clic con il pulsante destro del mouse e selezionare **Sostituisci valori** oppure selezionare **Sostituisci valori** dal gruppo **Trasforma** nella scheda **Home** della barra multifunzione. Questa opzione è disponibile anche nel gruppo **Qualsiasi colonna** nella scheda **Trasforma**.

   ![Menu a discesa Sostituisci valori](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) 

   o

   ![Sostituisci valori - Barra multifunzione](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)

1. Nella finestra di dialogo **Sostituisci valori** digitare **Details** nella casella di testo **Valore da trovare**, lasciare vuota la casella di testo **Sostituisci con** e quindi scegliere **OK** per eliminare la parola *Details* da questa colonna.

   ![Rimuovere una parola dalla colonna](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

Alcune celle contengono solo la parola "Year" anziché i valori relativi agli anni. È possibile filtrare la colonna in modo da visualizzare solo le righe che non contengono la parola "Year".

1. Selezionare la freccia a discesa del filtro nella colonna.

1. Nel menu a discesa scorrere verso il basso e deselezionare la casella di controllo accanto all'opzione **Year**, quindi selezionare **OK**.

   ![Filtrare i dati](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

Dal momento che si stanno esaminando solo i vincitori finali, è possibile rinominare la seconda colonna come **Country**. Per rinominare la colonna:

1. Fare doppio clic o toccare e tenere premuta l'intestazione della seconda colonna oppure
   - Fare clic con il pulsante destro del mouse sull'intestazione di colonna e selezionare **Rinomina** oppure
   - Selezionare la colonna e selezionare **Rinomina** nel gruppo **Qualsiasi colonna** nella scheda **Trasforma** della barra multifunzione.

   ![Menu a discesa Rinomina](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) 
  
   o

   ![Rinomina - Barra multifunzione](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)

1. Digitare **Country** nell'intestazione e premere **INVIO** per rinominare la colonna.

È anche necessario escludere tramite filtro le righe come "2020" che contengono valori Null nella colonna **Country**. È possibile usare il menu Filtro come è stato fatto con i valori **Year** oppure è possibile:

1. Fare clic con il pulsante destro del mouse sulla cella **Country** nella riga **2020**, che contiene un valore *Null*.

1. Scegliere **Filtri per testo** > **Diverso da** dal menu di scelta rapida per rimuovere tutte le righe contenenti tale valore nella cella.

   ![Filtro del testo](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)

## <a name="import-the-query-into-report-view"></a>Importare la query in visualizzazione Report

Dopo la conversione dei dati nella forma richiesta, è il momento di assegnare il nome "Euro Cup Winners" alla query e importarla nel report.

1. Nella casella di testo **Nome** del riquadro **Impostazioni query** immettere **Euro Cup Winners**.

   ![Assegnare un nome alla query](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

1. Selezionare **Chiudi e applica** > **Chiudi e applica** nella scheda **Home** della barra multifunzione.

   ![Chiudi e applica](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

La query viene caricata nella visualizzazione *Report* di Power BI Desktop, dove è possibile visualizzarla nel riquadro **Campi**.

   ![Riquadro Campi](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

>[!TIP]
>È sempre possibile tornare all'editor di Power Query per modificare e perfezionare la query come indicato di seguito:
>- Selezionare i puntini di sospensione **Altre opzioni** ( **...** ) accanto a **Euro Cup Winners** nel riquadro **Campi** e selezionare **Modifica query** oppure
>- Selezionare **Modifica query** > **Modifica query** nel gruppo **Dati esterni** della scheda **Home** della barra multifunzione in visualizzazione Report. 

## <a name="create-a-visualization"></a>Creare una visualizzazione

Per creare una visualizzazione in base ai dati:

1. Selezionare il campo **Country** nel riquadro **Campi** oppure trascinarlo nell'area di disegno del report. Power BI Desktop riconosce i dati come nomi di paesi e crea automaticamente una visualizzazione **Mappa**.

   ![Visualizzazione mappa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)

1. Aumentare le dimensioni della mappa trascinando i punti di controllo negli angoli in modo che tutti i nomi dei paesi vincitori siano visibili.  

   ![Aumentare le dimensioni della mappa](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)

1. La mappa mostra punti dati identici per ogni paese che ha vinto un torneo nell'ambito della Coppa UEFA. Per fare in modo che le dimensioni di ogni punto dati rispecchi il numero di volte in cui quel paese ha vinto, trascinare il campo **Year** in **Trascinare qui i campi di dati** in **Dimensioni** nella parte inferiore del riquadro **Visualizzazioni**. Il campo viene automaticamente modificato in una misura **Count of Year** (Numero di anni) e la visualizzazione mappa mostra ora punti dati di dimensioni maggiori per i paesi che hanno vinto più tornei.

   ![Trascinare Count of Year in Size](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

## <a name="customize-the-visualization"></a>Personalizzare la visualizzazione

Come si può notare, è molto facile creare visualizzazioni basate sui dati. È anche molto semplice personalizzare queste visualizzazioni per presentare meglio i dati nel modo desiderato.

### <a name="format-the-map"></a>Formattare la mappa

È possibile modificare l'aspetto di una visualizzazione selezionandola e quindi selezionando l'icona **Formato** (rullo) nel riquadro **Visualizzazioni**. Ad esempio i punti dati relativi alla Germania riportati nella visualizzazione potrebbero essere fuorvianti, dal momento che la Germania Ovest ha vinto due coppe mentre la Germania ne ha vinta una e la mappa sovrappone i due punti anziché separarli o aggiungerli insieme. È possibile colorare questi due punti in modo diverso per evidenziare questo aspetto. È anche possibile assegnare alla mappa un titolo più descrittivo e interessante.

1. Con la visualizzazione selezionata, selezionare l'icona **Formato** e quindi selezionare **Colori dati** per espandere le opzioni di colore dei dati.

   ![Formattare i colori dei dati](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)

1. Impostare **Mostra tutto** su **Attivato** e quindi selezionare l'elenco a discesa accanto a **West Germany** e scegliere un colore giallo.

   ![Modificare il colore](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)

1. Selezionare **Titolo** per espandere le opzioni del titolo e nel campo **Testo titolo** digitare **Euro Cup Winners** al posto del titolo corrente.

1. Impostare **Colore carattere** su rosso, **Dimensioni testo** su **12** e **Famiglia di caratteri** su **Segoe (grassetto)** .

   ![Formattare i colori dei dati](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)

A questo punto la visualizzazione mappa è simile alla seguente:

![Visualizzazione mappa formattata](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)

### <a name="change-the-visualization-type"></a>Modificare il tipo di visualizzazione

È possibile modificare il tipo di visualizzazione selezionandola e quindi selezionando un'icona diversa nella parte superiore del riquadro **Visualizzazioni**. Ad esempio, nella visualizzazione mappa non sono disponibili i dati per l'Unione Sovietica e la Cecoslovacchia, perché questi paesi non esistono più sul planisfero. Un altro tipo di visualizzazione, ad esempio una mappa ad albero o un grafico a torta, potrebbe essere più accurato dal momento che mostra tutti i valori.

Per convertire la mappa in un grafico a torta, selezionare la mappa e quindi selezionare l'icona **Grafico a torta** nel riquadro **Visualizzazioni**.

![Modificare la visualizzazione in un grafico a torta](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- È possibile usare le opzioni di formattazione di **Colori dati** per assegnare lo stesso colore alla Germania e alla Germania Ovest. 
>- Per raggruppare i paesi che hanno ottenuto il maggior numero di vittorie nel grafico a torta, selezionare i puntini di sospensione ( **...** ) nella parte superiore destra della visualizzazione e quindi selezionare **Ordina per Count of Year** (Ordina per numero di anni) dall'elenco a discesa.

Power BI Desktop offre un'esperienza end-to-end molto semplice, dal recupero di dati da una vasta gamma di origini dati, al data shaping per soddisfare le esigenze di analisi, fino alla visualizzazione dei dati in modi accattivanti e interattivi. Quando il report è pronto, è possibile [caricarlo in Power BI](desktop-upload-desktop-files.md) e creare dashboard basati sul report che potranno essere condivisi con altri utenti di Power BI.

## <a name="see-also"></a>Vedere anche

* [Altre esercitazioni su Power BI Desktop](/power-bi/guided-learning/)
* [Video su Power BI Desktop](desktop-videos.md)
* [Forum di Power BI](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Blog su Power BI](https://go.microsoft.com/fwlink/?LinkID=519327)

