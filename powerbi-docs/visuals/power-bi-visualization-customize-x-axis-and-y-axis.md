---
title: Personalizzare le proprietà degli assi X e Y
description: Personalizzare le proprietà degli assi X e Y
author: mihart
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 393f6f25fedddd9ff17d635ae67ce473ab57eea4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880933"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Personalizzare le proprietà degli assi X e Y

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Questa esercitazione illustra i diversi modi disponibili per personalizzare gli assi X e Y degli oggetti visivi. Non tutti gli oggetti visivi contengono assi. I grafici a torta, ad esempio, non hanno assi. Le opzioni di personalizzazione variano inoltre da un oggetto visivo all'altro. Le opzioni disponibili sono troppe per poterle descrivere tutte in un singolo articolo, quindi verranno presentate alcune delle personalizzazioni usate più di frequente e verrà illustrato l'uso del riquadro **Formato** per gli oggetti visivi nell'area di disegno report di Power BI.  

Nel video Amanda personalizzerà gli assi X e Y dimostrando anche i diversi modi disponibili per controllare la concatenazione quando si usano le funzionalità di drill-down e drill-up.

> [!NOTE]
> Questo video usa una versione precedente di Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Prerequisiti

- Power BI Desktop

- [Esempio di analisi delle vendite al dettaglio ](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)


## <a name="add-a-new-visualization"></a>Aggiungere una nuova visualizzazione

Prima di poter personalizzare la visualizzazione, è necessario crearla.

1. In Power BI Desktop aprire l'esempio di analisi delle vendite al dettaglio.  

2. Nella parte inferiore selezionare l'icona con il segno più giallo per aggiungere una nuova pagina. 

    ![segno più giallo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-new-page-icon.png)

1. Nel riquadro **Visualizzazioni** selezionare l'icona dell'istogramma a colonne in pila. Viene aggiunto un modello vuoto all'area di disegno report.

    ![Screenshot del riquadro Visualizzazioni e di un istogramma a colonne in pila vuoto](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-column-chart.png)

1. Per impostare i valori dell'asse X, nel riquadro **Campi** selezionare **Time** > **FiscalMonth**.

1. Per impostare i valori dell'asse Y, nel riquadro **Campi** selezionare**Sales** > **Last Year Sales** e **Sales** > **This Year Sales** > **Valore**.

    ![Screenshot dell'istogramma a colonne in pila popolato.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-build-visual.png)

    A questo punto è possibile personalizzare l'asse X. Power BI offre opzioni quasi illimitate per la formattazione della visualizzazione. 

## <a name="customize-the-x-axis"></a>Personalizzare l'asse X
Sono disponibili molte funzionalità personalizzabili per l'asse X. È possibile aggiungere e modificare le etichette dati e il titolo dell'asse X. Per le categorie, è possibile modificare la larghezza, le dimensioni e la spaziatura interna di barre, colonne, linee e aree. Per i valori è possibile modificare le unità visualizzate, le posizioni decimali e le linee della griglia. L'esempio seguente mostra la personalizzazione di un istogramma. Aggiungere alcune personalizzazioni per acquisire familiarità con le opzioni, quindi esplorare il resto autonomamente.

### <a name="customize-the-x-axis-labels"></a>Personalizzare le etichette dell'asse X
Le etichette dell'asse X vengono visualizzate sotto le colonne del grafico. Al momento, sono grigie, piccoli e difficili da leggere, quindi verranno cambiate.

1. Nel riquadro **Visualizzazioni** selezionare **Formato** (icona del rullo ![Screenshot dell'icona del rullo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller-icon.png). ) per visualizzare le opzioni di personalizzazione.

2. Espandere le opzioni dell'asse X.

   ![Screenshot delle opzioni dell'asse X.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-x.png)

3. Spostare il dispositivo di scorrimento per **Asse X** su **Attiva**.

    ![Screenshot del dispositivo di scorrimento impostato su Attiva.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-slider-on.png)

    Si potrebbe scegliere di impostare l'asse X su **Disattiva** se, ad esempio, la visualizzazione è autoesplicativa senza etichette oppure se la pagina del report è piena ed è necessario creare spazio per visualizzare più dati.

4. Formattare il colore, le dimensioni e il tipo di carattere del testo:

    - **Colore**: selezionare nero

    - **Dimensioni testo**: immettere *14*

    - **Famiglia di caratteri**: selezionare **Arial Black**

    - **Spaziatura interna**: immettere *40%*

        ![Screenshot con etichette in diagonale](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-x.png)
    
5. Se il testo dell'asse X visualizzato in diagonale non è di proprio gradimento, sono disponibili diverse opzioni. 
    - Impostare le dimensioni del testo su un valore inferiore a 14.
    - Ingrandire la visualizzazione. 
    - Visualizzare un numero minore di colonne e aggiungere una barra di scorrimento aumentando il valore di **Larghezza minima categoria**. 
    
    In questo esempio è stata selezionata la seconda opzione ed è stata ingrandita la visualizzazione trascinando una delle barre di ridimensionamento. Ora il testo di 14 punti rientra nella visualizzazione senza la necessità di mostrarlo in diagonale o con una barra di scorrimento. 

   ![Grafico e riquadro di formattazione con le etichette in orizzontale](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stretch.png)

### <a name="customize-the-x-axis-title"></a>Personalizzare il titolo dell'asse X
Quando è **attivato**, il titolo dell'asse X viene visualizzato sotto le etichette dell'asse X. 

1. Per iniziare, impostare il titolo dell'asse X su **Attiva**.  

    ![Dispositivo di scorrimento del titolo](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-title-on.png)

    La prima cosa da notare è che la visualizzazione ha ora un titolo predefinito dell'asse X.  In questo caso, il titolo è **FiscalMonth**.

   ![Grafico con titolo visualizzato nella parte inferiore](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title.png)

1. Formattare il colore, le dimensioni e il tipo di carattere del testo del titolo:

    - **Colore titolo**: selezionare arancione

    - **Titolo asse**: digitare *Fiscal Month* (con uno spazio)

    - **Dimensioni testo titolo**: immettere *18*

    Dopo aver completato le personalizzazioni, l'istogramma in pila avrà un aspetto simile al seguente:

    ![Screenshot dell'istogramma a colonne in pila personalizzato.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title-formatted.png)

1. Salvare le modifiche apportate e passare alla sezione successiva. Se dovesse risultare necessario annullare tutte le modifiche, selezionare **Ripristina valori predefiniti** nella parte inferiore del riquadro di personalizzazione **Asse X**. Si vedrà ora come personalizzare l'asse Y.

## <a name="customize-the-y-axis"></a>Personalizzare l'asse Y
Per l'asse Y è possibile personalizzare molte funzionalità. È possibile aggiungere e modificare le etichette dati, il titolo e le linea della griglia dell'asse Y. Per i valori, è possibile modificare le unità visualizzate, le posizioni decimali, il punto iniziale e il punto finale. Per le categorie, è possibile modificare la larghezza, le dimensioni e la spaziatura interna di barre, colonne, linee e aree. 

Nell'esempio seguente viene proseguita la personalizzazione di un istogramma. Apportare alcune modifiche per acquisire familiarità con le opzioni, quindi esplorare il resto autonomamente.

### <a name="customize-the-y-axis-labels"></a>Personalizzare le etichette dell'asse Y
Per impostazione predefinita, le etichette dell'asse Y vengono visualizzate a sinistra. Al momento, sono grigie, piccoli e difficili da leggere, quindi verranno cambiate.

1. Espandere le opzioni di Asse Y.

   ![Screenshot delle opzioni dell'asse Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-y.png)

1. Spostare il dispositivo di scorrimento per **Asse Y** su **Attiva**.  

    ![Screenshot del dispositivo di scorrimento impostato su Attiva.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-on.png)

    Talvolta potrebbe essere preferibile disattivare l'asse Y per visualizzare una maggiore quantità di dati.

1. Formattare il colore, le dimensioni e il tipo di carattere del testo:

    - **Colore**: selezionare nero

    - **Dimensioni testo**: immettere *10*

    - **Unità visualizzate**: selezionare **Milioni**

    ![Grafico dopo la formattazione dell'asse Y](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-y.png)

### <a name="customize-the-y-axis-title"></a>Personalizzare il titolo dell'asse Y
Quando è **attivato**, il titolo dell'asse Y viene visualizzato accanto alle etichette dell'asse X. Per questa visualizzazione, un titolo dell'asse Y non migliorerà l'aspetto visivo, quindi lasciare **Titolo** impostato su **Disattiva**. I titoli dell'asse Y verranno aggiunti a un oggetto visivo a doppio asse più avanti in questa esercitazione. 

### <a name="customize-the-gridlines"></a>Personalizzare le linea della griglia
È ora possibile evidenziare le linee della griglia modificando il colore e aumentando lo spessore del tratto:

- **Colore**: selezionare arancione

- **Spessore tratto**: immettere *2*

Dopo tutte queste personalizzazioni, l'aspetto dell'istogramma dovrebbe essere simile al seguente:

![Screenshot del grafico con l'asse Y personalizzato.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-gridline.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Personalizzazione di visualizzazioni con due assi Y

Alcune visualizzazioni possono beneficiare dalla presenza di due assi Y. I grafici combinati rappresentano un esempio valido. Prima di formattare i due assi Y, creare un grafico combinato che confronta le tendenze per le vendite e il margine lordo.  

### <a name="create-a-chart-with-two-y-axes"></a>Creare un grafico con due assi Y

1. Selezionare l'istogramma e cambiarlo in *Grafico a linee e istogramma a colonne in pila*. 

    ![Screenshot del riquadro Visualizzazioni con l'icona Grafico a linee e istogramma a colonne in pila evidenziata.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo.png)
   

2. Trascinare **Sales** > **Gross Margin Last Year %** dal riquadro Campi al bucket **Valori riga**.

    ![Screenshot del grafico a linee e istogramma a colonne in pila con i tre valori rappresentati in modo chiaro.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-add-line.png)

    
3. Riformattare la visualizzazione per rimuovere le etichette dell'asse X in diagonale. 

   ![Grafico combinato e riquadro Formato con dimensioni del carattere ridotte a 12](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-font-size.png)

   Power BI crea due assi Y consentendo di ridimensionare separatamente i valori. L'asse di sinistra misura i dollari, mentre quello di destra misura le percentuali.

### <a name="format-the-second-y-axis"></a>Formattare il secondo asse Y
Poiché all'inizio la visualizzazione includeva un unico asse Y formattato, Power BI ha creato il secondo asse Y usando le stesse impostazioni. Ma è possibile cambiarle. 

1. Nel riquadro **Visualizzazioni** selezionare l'icona del rullo per visualizzare le opzioni di formattazione.

1. Espandere le opzioni di Asse Y.

1. Scorrere verso il basso fino a individuare l'opzione **Mostra secondario**. Verificare che sia impostata su **Attiva**. L'asse Y secondario rappresenta il grafico a linee.

   ![Screenshot dell'opzione Mostra secondario.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-secondary.png)

1. (Facoltativo) Personalizzare il colore del carattere, le dimensioni e le unità visualizzate per i due assi. Se si cambia **Posizione** per l'asse delle colonne o l'asse di riga, le due assi si scambiano di posto.

### <a name="add-titles-to-both-axes"></a>Aggiungere titoli a entrambi gli assi

Con una visualizzazione così complessa, può risultare utile aggiungere titoli agli assi.  I titoli consentono ai colleghi di comprendere il senso della visualizzazione.

1. Impostare **Titolo** su **Sì** per **Asse Y (colonna)** e **Asse Y (riga)** .

1. Impostare **Stile** su **Mostra solo titolo** per entrambi gli assi.

   ![Screenshot delle opzioni Titolo e Stile.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-title.png)

1. Il grafico combinato mostra ora due assi, entrambi con titoli.

   ![Screenshot del grafico con due assi Y personalizzato.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-titles-on.png)

1. Formattare i titoli. In questo esempio uno dei titoli è stato abbreviato e sono state ridotte le dimensioni dei caratteri di entrambi. 
    - Dimensioni carattere: **9**
    - **Titolo asse** abbreviato per il primo asse Y (istogramma): Sales last year & this year

    ![Screenshot del grafico combinato con i titoli completi visualizzati.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual.png)



Per altre informazioni, vedere [Suggerimenti e consigli per la formattazione dei colori in Power BI](service-tips-and-tricks-for-color-formatting.md) e [Personalizzare i titoli, le legende e gli sfondi delle visualizzazioni](power-bi-visualization-customize-title-background-and-legend.md). Prossimamente saranno disponibili nuovi aggiornamenti per la formattazione dei titoli. 

## <a name="next-steps"></a>Passaggi successivi

- [Visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
