---
title: Usare misure rapide per calcoli comuni e avanzati
description: Le misure rapide forniscono formule DAX già pronte che accelerano l'esecuzione di calcoli comuni.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/22/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4e5ea5e5fcbffb5c61434ecc26a90d80d1cd1736
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "74415363"
---
# <a name="use-quick-measures-for-common-calculations"></a>Usare misure rapide per calcoli comuni
È possibile usare *misure rapide* per eseguire facilmente e velocemente calcoli comuni e avanzati. Una misura rapida esegue un set di comandi DAX (Data Analysis Expressions) dietro le quinte e quindi presenta i risultati da usare nel report. Non è necessario scrivere i comandi DAX. Questa operazione viene eseguita automaticamente in base all'input specificato in una finestra di dialogo. Sono disponibili diverse categorie di calcoli e metodi per modificare ogni calcolo secondo le proprie esigenze. L'aspetto forse più importante è che è possibile visualizzare le espressioni DAX che vengono eseguite dalla misura rapida e iniziare subito o espandere la propria conoscenza di DAX.

## <a name="create-a-quick-measure"></a>Creare una misura rapida

Per creare una misura rapida in Power BI Desktop, fare clic con il pulsante destro del mouse o selezionare i tre puntini **...** accanto a un elemento nel riquadro **Campi** e selezionare **Nuova misura rapida** dal menu visualizzato. 

![Selezionare Nuova misura rapida](media/desktop-quick-measures/quick-measures_01.png)

È anche possibile fare clic con il pulsante destro del mouse o selezionare la freccia dell'elenco a discesa accanto a un valore nell'area **Valori** per un oggetto visivo esistente e selezionare **Nuova misura rapida** dal menu. 

Quando si seleziona **Nuova misura rapida**, viene visualizzata la finestra **Misure rapide**, che consente di selezionare il calcolo da eseguire e i campi sui quali eseguirlo. 

Selezionare il campo **Selezionare un calcolo** per visualizzare un lungo elenco di misure rapide disponibili. 

![Calcoli con misure rapide disponibili](media/desktop-quick-measures/quick-measures_04.png)

I cinque tipi di calcolo con misure rapide, con i relativi calcoli, sono:

* **Aggregazione per categoria**
  * Media per categoria
  * Varianza per categoria
  * Massimo per categoria
  * Minimo per categoria
  * Media ponderata per categoria
* **Filtri**
  * Valore filtrato
  * Differenza dal valore filtrato
  * Differenza percentuale dal valore filtrato
  * Vendite di nuovi clienti
* **Business Intelligence**
  * Totale da inizio anno
  * Totale da inizio trimestre
  * Totale da inizio mese
  * Variazione rispetto all'anno precedente
  * Variazione rispetto al trimestre precedente
  * Variazione rispetto al mese precedente
  * Media mobile
* **Totali**
  * Totale parziale
  * Totale per categoria (filtri applicati)
  * Totale per categoria (filtri non applicati)
* **Operazioni matematiche**
  * Addizione
  * Sottrazione
  * Moltiplicazione
  * Divisione
  * Differenza percentuale
  * Coefficiente di correlazione
* **Testo**
  * Classificazione a stelle
  * Elenco concatenato di valori

Per inviare le proprie idee su nuove misure rapide da usare o sulle formule DAX sottostanti o idee di altro tipo sulle misure rapide, vedere la fine di questo articolo.

> [!NOTE]
> Quando si usano connessioni in tempo reale di SQL Server Analysis Services (SSAS), sono disponibili alcune misure rapide. Power BI Desktop visualizza solo le misure rapide supportate per la versione di SSAS a cui ci si connette. Se durante la connessione a un'origine dati dinamica alcune misure rapide non sono disponibili nell'elenco, è perché la versione di SSAS a cui si è effettuata la connessione non supporta i comandi DAX usati per implementare le misure rapide in questione.

Dopo aver selezionato i calcoli e i campi per la misura rapida, selezionare **OK**. La nuova misura rapida verrà visualizzata nel riquadro **Campi** e la formula DAX sottostante verrà visualizzata nella barra della formula. 

## <a name="quick-measure-example"></a>Esempio di misura rapida
Verrà ora esaminata una misura rapida in azione.

L'oggetto visivo matrice seguente visualizza una tabella di vendite di vari prodotti. È una tabella di base che include il totale delle vendite per ogni categoria.

![Oggetto visivo matrice che illustra una tabella di vendite](media/desktop-quick-measures/quick-measures_05.png)

Selezionare l'oggetto visivo matrice e quindi selezionare la freccia dell'elenco a discesa **TotalSales** nell'area **Valori** e selezionare **Nuova misura rapida**. 

In **Calcolo** nella finestra **Misure rapide** selezionare **Media per categoria**. 

Trascinare **Average Unit Price** (Prezzo unitario medio) dal riquadro **Campi** nel campo **Valore di base**. Lasciare **Categoria** nel campo **Categoria** e selezionare **OK**. 

![](media/desktop-quick-measures/quick-measures_06.png)

Quando si seleziona **OK**, vengono eseguite alcune operazioni interessanti.

![Nuova misura rapida nell'oggetto visivo, nella barra della formula e nell'elenco Campi](media/desktop-quick-measures/quick-measures_07.png)

1. L'oggetto visivo matrice ha una nuova colonna che visualizza il valore **Average Unit Price average per Category** (Media prezzo unitario medio per Categoria) calcolato.
   
2. Nella barra della formula compare la formula DAX per la nuova misura rapida. Per altre informazioni sulla formula DAX, vedere la [prossima sezione](#learn-dax-by-using-quick-measures).
   
3. La nuova misura rapida viene visualizzata selezionata ed evidenziata nel riquadro **Campi**. 

La nuova misura rapida è disponibile per qualsiasi oggetto visivo nel report, non solo per l'oggetto visivo creato per cui è stata creata. L'immagine seguente illustra un oggetto visivo grafico a colonne rapido creato usando il nuovo campo misura rapida.

![Nuovo oggetto visivo grafico a barre basato sul campo misura rapida](media/desktop-quick-measures/quick-measures_09.png)

## <a name="learn-dax-by-using-quick-measures"></a>Apprendere DAX con le misure rapide
Un grande vantaggio delle misure rapide è la visualizzazione della formula DAX che implementa la misura. Quando si seleziona una misura rapida nel riquadro **Campi**, viene visualizzata la **barra della formula** con la formula DAX creata da Power BI per implementare la misura.

![Formula della misura rapida nella barra della formula](media/desktop-quick-measures/quick-measures_10.png)

La barra della formula non solo visualizza la formula alla base della misura, ma, forse ancora più importante, consente di vedere come creare le formule DAX sottostanti delle misure rapide.

Si supponga di dover calcolare una variazione rispetto all'anno precedente e di non sapere con certezza come strutturare la formula DAX o di non avere idea di dove cominciare. Invece di arrovellarsi inutilmente, è possibile creare una misura rapida con il calcolo **Variazione rispetto all'anno precedente** e vedere come viene visualizzata nell'oggetto visivo e come funziona la formula DAX. È quindi possibile apportare modifiche direttamente alla formula DAX oppure creare una misura simile che soddisfi le esigenze e le aspettative. È come avere a disposizione un insegnante che risponda immediatamente alle domande dell'utente con pochi clic. 

È sempre possibile eliminare le misure rapide dal modello, se non sembrano utili. È sufficiente fare clic con il pulsante destro del mouse o selezionare **...** accanto alla misura e selezionare **Elimina**. È anche possibile rinominare una misura rapida nel modo preferito selezionando **Rinomina** dal menu. 

![Eliminare o rinominare una misura rapida](media/desktop-quick-measures/quick-measures_11.png)

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Occorre tenere presenti alcune limitazioni e considerazioni.

- È possibile usare le misure rapide aggiunte al riquadro **Campi** con qualsiasi oggetto visivo del report.
- È sempre possibile visualizzare la formula DAX associata a una misura rapida selezionando la misura nell'elenco **Campi**. La formula verrà visualizzata nella barra della formula.
- Le misure rapide sono disponibili solo se è possibile modificare il modello. Questo non è possibile se si usano alcuni tipi di connessione dinamica. Le connessioni dinamiche tabulari SSAS sono supportate, come descritto in precedenza.
- Non è possibile creare misure rapide di Business Intelligence per le gerarchie temporali in modalità DirectQuery. Le funzioni DAX usate in queste misure rapide hanno implicazioni relative alle prestazioni quando vengono convertite nelle istruzioni T-SQL che vengono inviate all'origine dati.

> [!IMPORTANT]
> Per i separatori di argomento, le istruzioni DAX per le misure rapide usano solo virgole. Se la versione di Power BI Desktop in uso è in una lingua che usa le virgole come separatori decimali, le misure rapide non funzioneranno correttamente.

### <a name="time-intelligence-and-quick-measures"></a>Funzionalità di Business Intelligence per le gerarchie temporali e misure rapide
È possibile usare tabelle data personalizzate con misure rapide con funzionalità di Business Intelligence per le gerarchie temporali. Se si sta usando un modello tabulare esterno, assicurarsi che al momento della creazione del modello la colonna della data primaria nella tabella sia stata contrassegnata come tabella data, come descritto in [Specificare Contrassegna come tabella data per l'uso con le funzionalità di Business Intelligence per le gerarchie temporali](https://docs.microsoft.com/sql/analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular). Se si sta importando una tabella data personalizzata, verificare di averla contrassegnata come tabella data, come descritto in [Impostare e usare tabelle data in Power BI Desktop](desktop-date-tables.md).

### <a name="additional-information-and-examples"></a>Altre informazioni ed esempi
Si hanno idee per misure rapide non ancora disponibili? interessanti, Vedere la pagina [Idee per Power BI](https://go.microsoft.com/fwlink/?linkid=842906) e inviare le idee e le formule DAX di misure rapide che si vuole che siano rese disponibili in Power BI Desktop. Verranno prese in considerazione ed eventualmente aggiunte all'elenco delle misure rapide in una versione futura.

