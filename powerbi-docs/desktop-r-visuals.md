---
title: Creare oggetti visivi di Power BI usando R
description: Creare oggetti visivi di Power BI usando R
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f75b769fdebd162507f1e54ead3f38412440c2ed
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="create-power-bi-visuals-using-r"></a>Creare oggetti visivi di Power BI usando R
Con **Power BI Desktop**, è possibile usare **R** per visualizzare i dati.

## <a name="install-r"></a>Installare R
**Power BI Desktop** non include, distribuisce o installa il motore **R**. Per eseguire gli script R in **Power BI Desktop**, è necessario installare **R** nel computer locale. È possibile scaricare e installare **R** gratuitamente da molte posizioni, tra cui la [pagina di download di Revolution Open](https://mran.revolutionanalytics.com/download/) e il [repository CRAN](https://cran.r-project.org/bin/windows/base/). La versione corrente dello script R in **Power BI Desktop** supporta i caratteri Unicode oltre agli spazi (caratteri vuoti) nel percorso di installazione.

## <a name="enable-r-visuals"></a>Abilitare gli oggetti visivi R
Per abilitare gli oggetti visivi R, selezionare **File > Opzioni e impostazioni > Opzioni** e, nella pagina **Opzioni** visualizzata, verificare che l'installazione locale di R sia specificata nella sezione **Script R** della finestra **Opzioni**, come illustrato nella figura seguente. Nella figura seguente, il percorso dell’installazione locale di R è **C:\Program Files\R\R-3.2.0** e questo percorso è indicato in modo esplicito nella casella di testo. Assicurarsi che il percorso visualizzato rifletta correttamente l'installazione locale di R che **Power BI Desktop** dovrà usare.
   
   ![](media/desktop-r-visuals/r-visuals-2.png)

Dopo aver specificato l'installazione di R, è possibile iniziare la creazione di oggetti visivi R.

## <a name="create-r-visuals-in-power-bi-desktop"></a>Creare oggetti visivi R in Power BI Desktop
1. Per aggiungere un oggetto visivo R, selezionare l'icona **Oggetto visivo R** nel riquadro **Visualizzazione**, come illustrato nella figura seguente.
   
   ![](media/desktop-r-visuals/r-visuals-3.png)

   Quando si aggiunge un oggetto visivo R a un report, **Power BI Desktop** esegue queste operazioni:
   
   - Un'immagine segnaposto dell'oggetto visivo R viene visualizzata nell'area di disegno del report.
   
   - L'**editor di script R** viene visualizzato nella parte inferiore del riquadro centrale.
   
   ![](media/desktop-r-visuals/r-visuals-4.png)

2. Successivamente, aggiungere i campi da usare nello script R nella sezione **Valori** dell’area **Campi**, esattamente come si farebbe con qualsiasi altro oggetto visivo **Power BI Desktop**. 
    
    Solo i campi aggiunti nell'area **Campi** sono disponibili per lo script R. È possibile aggiungere nuovi campi o rimuovere i campi non necessari dall'area **Campi** quando si modifica lo script R nell'**editor di script R di Power BI Desktop**. **Power BI Desktop** rileva automaticamente i campi aggiunti o rimossi.
   
   > [!NOTE]
   > Il tipo di aggregazione predefinito per gli oggetti visivi R è *Non riepilogare*.
   > 
   > 
   
3. A questo punto è possibile usare i dati selezionati per creare un tracciato. 

    Quando si selezionano i campi, l’ **editor di script R** genera un codice di associazione script R di supporto in base alle selezioni nell'area grigia nella parte superiore del riquadro dell'editor. Quando si selezionano o rimuovono campi aggiuntivi, il codice di supporto nell'editor di script R viene generato o rimosso automaticamente di conseguenza.
   
   Nell'esempio illustrato nella figura seguente, sono stati selezionati tre campi: hp, gear e drat. A seguito di queste selezioni, l'editor di script R genera il seguente codice di associazione:
   
   * Viene creato un frame di dati denominato **dataset**
     * Questo frame di dati è costituito dai diversi campi selezionati dall'utente
   * L'aggregazione predefinita è *Non riepilogare*
   * Analogamente agli oggetti visivi della tabella, i campi vengono raggruppati e le righe duplicate sono visualizzate una sola volta
   
   ![](media/desktop-r-visuals/r-visuals-5.png)
   
   > [!TIP]
   > Talvolta può essere opportuno impedire il raggruppamento automatico o la visualizzazione di tutte le righe, incluse quelle duplicate. In tal caso, è possibile aggiungere un campo di indice al set di dati in modo che tutte le righe siano considerate univoche, impedendo così il raggruppamento.
   > 
   > 
   
   Il frame di dati generato è detto **set di dati** ed è possibile accedere alle colonne selezionate in base ai rispettivi nomi. È ad esempio possibile accedere al campo gear scrivendo *dataset$gear* nello script R. Per i campi con spazi o caratteri speciali, usare le virgolette singole.

4. Con il frame di dati generato automaticamente in base ai campi selezionati, si è pronti a scrivere uno script R che genera il tracciato per il dispositivo predefinito R. Una volta completato lo script, selezionare **Esegui** dalla barra del titolo dell’ **editor di script R** (**Esegui** è sul lato destro della barra del titolo).
   
    Quando si seleziona **Esegui**, **Power BI Desktop** identifica il tracciato e lo visualizza nel canvas. Poiché il processo viene eseguito nell'installazione R locale, verificare che siano installati i pacchetti necessari.
   
   **Power BI Desktop** ritraccia l'oggetto visivo quando si verifica uno degli eventi seguenti:
   
   * Quando si seleziona **Esegui** dalla barra del titolo dell'**editor di script R**
   * Ogni volta che si modificano i dati, a causa dell'aggiornamento, del filtraggio o dell’evidenziazione dei dati stessi

    L'immagine seguente presenta un esempio di codice del tracciato di correlazione e illustra le correlazioni tra gli attributi di tipi diversi di automobili.

    ![](media/desktop-r-visuals/r-visuals-6.png)

5. Per ottenere una vista ingrandita delle visualizzazioni, è possibile ridurre a icona l’ **editor di script R**. Naturalmente, come altri oggetti visivi in **Power BI Desktop**, è possibile applicare un filtro incrociato al tracciato di correlazione selezionando solo auto sportive nell'oggetto visivo anello, ovvero l'oggetto rotondo a destra nell'immagine di esempio precedente.

    ![](media/desktop-r-visuals/r-visuals-7.png)

6. È inoltre possibile modificare lo script R per personalizzare l'oggetto visivo e sfruttare la potenza di R aggiungendo parametri al comando di tracciamento.

    Il comando di tracciamento originale era il seguente:

    corrplot(M, method = "color",  tl.cex=0.6, tl.srt = 45, tl.col = "black")

    Con poche modifiche nello script R, il comando è ora il seguente:

    corrplot(M, method = "circle", tl.cex=0.6, tl.srt = 45, tl.col = "black", type= "upper", order="hclust")

    Di conseguenza, l’oggetto visivo R ora traccia cerchi, prende in considerazione solo la metà superiore e riordina la matrice per raggruppare gli attributi correlati, come illustrato nella figura seguente.

    ![](media/desktop-r-visuals/r-visuals-8.png)

    Quando si esegue uno script R che genera un errore, l'oggetto visivo R non viene tracciato e viene visualizzato un messaggio di errore nell'area di disegno. Per informazioni dettagliate sull'errore, selezionare **Visualizza i dettagli** dall’errore dell’oggetto visivo R nell'area di disegno.

    ![](media/desktop-r-visuals/r-visuals-9.png)

    > **Sicurezza degli script R** Gli oggetti visivi R vengono creati in base agli script R, che potrebbero contenere codice con rischi per la sicurezza o per la privacy. Quando prova a visualizzare o a interagire con un oggetto visivo R per la prima volta, un utente riceve un messaggio di avviso di sicurezza. Abilitare gli oggetti visivi R solo se l'autore e l'origine sono considerati attendibili o dopo aver esaminato e acquisito informazioni sullo script R.
    > 
    > 

## <a name="known-limitations"></a>Limitazioni note
Gli oggetti visivi R in **Power BI Desktop** hanno poche limitazioni:

* Limitazioni relative alle dimensioni di dati: i dati utilizzati dall’oggetto visivo R per il tracciato sono limitati a 150.000 righe. Se vengono selezionate più di 150.000 righe, vengono utilizzate solo le prime 150.000 righe e viene visualizzato un messaggio sull'immagine.
* Limitazione relativa al tempo di calcolo: se un calcolo dell'oggetto visivo R supera di cinque minuti il timeout di esecuzione, viene generato un errore.
* Relazioni: come con altri oggetti visivi Power BI Desktop, se vengono selezionati campi di dati da diverse tabelle senza una relazione definita tra di esse, si verifica un errore.
* Gli oggetti visivi R vengono aggiornati al momento dell’aggiornamento, del filtraggio e dell’evidenziazione dei dati. Tuttavia, l'immagine in sé non è interattiva e non può essere l'origine del filtro incrociato.
* Gli oggetti visivi R rispondono all'evidenziazione di altri oggetti visivi, ma è possibile fare clic sugli elementi nell’oggetto visivo R per applicare un filtro incrociato ad altri elementi.
* Solo i tracciati sul dispositivo di visualizzazione predefinito R vengono visualizzati correttamente nell'area di disegno. Evitare di usare in modo esplicito un altro dispositivo di visualizzazione R.
* In questa versione, le installazioni di RRO non sono automaticamente identificate dalla versione a 32 bit di Power BI Desktop, quindi è necessario specificare manualmente il percorso della directory di installazione di R in **Opzioni e impostazioni > Opzioni > Script R**.

## <a name="next-steps"></a>Passaggi successivi
Esaminare le informazioni aggiuntive seguenti su R in Power BI.

* [Esecuzione di script R in Power BI Desktop](desktop-r-scripts.md)
* [Usare un IDE R esterno con Power BI](desktop-r-ide.md)

