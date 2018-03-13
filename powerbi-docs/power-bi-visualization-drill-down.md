---
title: Eseguire il drill-down in una visualizzazione in Power BI
description: Questo documento illustra come eseguire il drill down in una visualizzazione nel servizio Microsoft Power BI e in Power BI Desktop
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: MNAaHw4PxzE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fb834c92953c2cafcbca77bc1b3828b385755bca
ms.sourcegitcommit: 743e44fc8730fea0f7149916080b0c6d7eb6359d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>Eseguire il drill-down in una visualizzazione in Power BI
## <a name="drill-down-requires-a-hierarchy"></a>Il drill-down richiede una gerarchia
Quando un oggetto visivo ha una gerarchia, è possibile eseguire il drill-down per rivelare dettagli aggiuntivi. Ad esempio, potrebbe esserci una visualizzazione che calcola il numero di medaglie olimpiche in base a una gerarchia composta da sport, disciplina ed eventi. Per impostazione predefinita, la visualizzazione indicherà il numero di medaglie per sport: ginnastica, sci, sport acquatici e così via, ma, poiché contiene una gerarchia, selezionando uno degli oggetti visivi (ad esempio una barra, una riga o una bolla), potrebbe essere visualizzata un'immagine sempre più dettagliata. Selezionare l'elemento **acquatici** per visualizzare dati relativi a nuoto, tuffi e pallanuoto.  Selezionare l'elemento **tuffi** per visualizzare dettagli relativi a trampolino, piattaforma e tuffi sincronizzati.

È possibile aggiungere gerarchie ai report di cui si è proprietari, ma non a quelli condivisi.
Se non si è certi di quali visualizzazioni di Power BI contengano una gerarchia,  passare il mouse sopra una visualizzazione: se vengono visualizzati i controlli di drill-down negli angoli superiori, la visualizzazione contiene una gerarchia.

![](media/power-bi-visualization-drill-down/power-bi-drill-icon4.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon3.png)
![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) ![](media/power-bi-visualization-drill-down/power-bi-drill-icon6.png)  

Le date sono un tipo univoco di gerarchia. Quando si aggiunge un campo data a una visualizzazione, Power BI aggiunge automaticamente una gerarchia temporale che contiene anno, trimestre, mese e giorno. Per altre informazioni, vedere [Gerarchie e comportamento di esplorazione degli oggetti visivi](guided-learning/visualizations.yml#step-18) o guardare il video seguente.


  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Per informazioni sulla creazione di gerarchie tramite Power BI Desktop, guardare il video su [come creare e aggiungere le gerarchie](https://youtu.be/q8WDUAiTGeU)
> 
> 

## <a name="two-methods-to-drill-down"></a>Due metodi per eseguire il drill-down
Esistono due modi per eseguire il drill-down e il drill-up in una visualizzazione,  entrambi descritti in questo articolo. Poiché eseguono la stessa operazione, usare quella che si preferisce.

> [!NOTE]
> Per proseguire, [aprire l'esempio di analisi di vendita al dettaglio](sample-datasets.md) nel servizio Power BI e creare una mappa ad albero che esamini **Total Units This Year** (Values) per **Territory**, **City**, **PostalCode** e **Name** (Group).  
> 
> 

## <a name="method-one-for-drill-down"></a>Primo metodo per eseguire il drill-down
Questo metodo usa le icone di drill-down visualizzate negli angoli superiori della visualizzazione stessa.

1. Aprire un report in [Visualizzazione di lettura o Visualizzazione di modifica](service-reading-view-and-editing-view.md) in Power BI. Il drill-down richiede una visualizzazione con una gerarchia. 
   
   Nell'animazione seguente è visualizzata una gerarchia.  La visualizzazione presenta una gerarchia composta da territorio, città, codice postale e nome città. Ogni territorio include una o più città, ogni città include uno o più codici di avviamento postale e così via. Per impostazione predefinita, la visualizzazione mostra solo i dati del territorio, perché *Territory* viene visualizzato per primo nell'elenco.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Per abilitare il drill down, selezionare l'icona a forma di freccia nell'angolo in alto a destra della visualizzazione. Quando l'icona è scura, il drill-down è abilitato. Se non si attiva il drill-down, selezionando un elemento visivo (ad esempio una barra o una bolla) verranno filtrati in modo incrociato gli altri grafici nella pagina del report.    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. Per eseguire il drill-down di **un campo alla volta**, selezionare uno degli elementi nella visualizzazione. In un grafico a barre è necessario fare clic su una delle barre. In una mappa ad albero è necessario fare clic su una delle **foglie**. Si noti che il titolo viene modificato durante il drill-down e il drill-up. In questa animazione, il titolo cambia da "Total Units This Year by Territory" in "Total Units This Year by Territory and City" e quindi a "Total Units This Year by Territory, City and Postal Code" a "Total Units This Year by Territory, City, Postal Code, and Name". Per eseguire il drill-up, selezionare l'icona **Drill-up** ![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) nell'angolo in alto a sinistra della visualizzazione, come mostrato di seguito.
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. Per eseguire il drill-down di ***tutti i campi contemporaneamente***, selezionare la doppia freccia nell'angolo in alto a sinistra della visualizzazione.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. Per rieseguire il drill-up, selezionare la freccia rivolta verso l'alto nell'angolo in alto a sinistra della visualizzazione.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-two-for-drill-down"></a>Secondo metodo per eseguire il drill-down
Questo metodo usa l'elenco a discesa **Esplora** dalla barra dei menu superiore di Power BI.

1. Aprire un report in [Visualizzazione di lettura o Visualizzazione di modifica](service-reading-view-and-editing-view.md) in Power BI. Il drill-down richiede una visualizzazione con una gerarchia. 
   
   Nell'immagine seguente è visualizzata una gerarchia.  La visualizzazione presenta una gerarchia composta da territorio, città, codice postale e nome città. Ogni territorio include una o più città, ogni città include uno o più codici di avviamento postale e così via. Per impostazione predefinita, la visualizzazione mostra solo i dati del territorio, perché *Territory* viene visualizzato per primo nell'elenco.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Per abilitare il drill-down, selezionare una visualizzazione per renderla attiva e dalla barra dei menu di Power BI in alto selezionare **Esplora** > **Drill-down**. L'icona di drill-down nell'angolo in alto a destra della visualizzazione diventa uno sfondo nero. ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. Dopo l’abilitazione, eseguire il drill-down di un campo alla volta selezionando una delle foglie della mappa ad albero. In questo esempio, viene selezionato il territorio denominato **NC** per visualizzare il totale delle unità vendute quest'anno nella Carolina del Nord in base alla città.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. Per eseguire il drill down di tutti i campi contemporaneamente, selezionare **Esplora** > **Mostra il livello successivo**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. Per eseguire il drill-up, selezionare **Esplora** > **Drill-up**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)

6. Per visualizzare i dati usati per creare l'oggetto visivo, selezionare **Visualizza dati**. I dati vengono visualizzati in un riquadro sotto l'oggetto visivo. Questo riquadro rimane presente mentre si continua il drill-through dell’oggetto visivo. Per altre informazioni, vedere [Visualizzare i dati usati per creare l’oggetto visivo](service-reports-show-data.md).

## <a name="understanding-the-hierarchy-axis-and-hierarchy-group"></a>Informazioni sull'asse della gerarchia e sul gruppo della gerarchia
L'asse della gerarchia e il gruppo della gerarchia possono essere considerati come i meccanismi che è possibile usare per aumentare e diminuire la granularità dei dati che si vuole visualizzare. Tutti i dati che possono essere organizzati in categorie e sottocategorie possono avere una gerarchia. Ciò, naturalmente, include date e ore.

È possibile creare una visualizzazione in Power BI in modo che abbia una gerarchia selezionando uno o più campi dati da aggiungere all'area **Asse** o all'area **Gruppo**, con i dati che si vuole esaminare come campi dati nell'area **Valori**. Per sapere se i dati sono gerarchici, verificare la presenza delle icone della modalità di espansione negli angoli in alto a sinistra e a destra della visualizzazione. 

In pratica, è utile considerare due tipi di dati gerarchici:
- Dati di data e ora: se si ha un campo dati con un tipo di dati DateTime, sono già presenti dati gerarchici. Power BI crea automaticamente una gerarchia per i campi dati i cui valori possono essere analizzati in una struttura [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx). È sufficiente aggiungere un campo DateTime all'area **Asse** o **Gruppo**.
- Dati categorici: se i dati derivano da raccolte che includono sottoraccolte oppure contengono righe di dati che condividono valori comuni, sono presenti dati gerarchici.

Power BI consente di espandere uno o tutti i subset. È possibile eseguire il drill-down dei dati per visualizzare un singolo subset a ogni livello o per visualizzare tutti i subset contemporaneamente a ogni livello. È ad esempio possibile eseguire il drill-down fino a visualizzare un anno specifico oppure visualizzare tutti i risultati per ogni anno man mano che si scende nella gerarchia. Al contrario, è possibile eseguire il drill-up nello stesso modo.

Le sezioni seguenti descrivono il drill-down dalla visualizzazione superiore a quella centrale e infine a quella inferiore.

### <a name="hierarchical-data-and-time-data"></a>Dati gerarchici di data e ora
Per questo esempio, seguire l'[Esempio di analisi delle vendite al dettaglio](sample-datasets.md) e creare una visualizzazione istogramma in pila che esamini il **mese** (asse) in base alle **vendite totali** (valori).  

Anche se il campo dati Asse è **Mese**, viene tuttavia creata una categoria **Anno** nell'area **Asse**, perché Power BI fornisce la struttura DateTime completa per tutti i valori letti. Nella parte superiore della gerarchia vengono visualizzati i dati per l'anno.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-datetime-1.png)

Con la modalità drill-down attiva, fare clic sulla bar nel grafico per scendere di un livello nella gerarchia. Verranno visualizzate tre barre per i dati dei trimestri disponibili. Dalle icone in alto a sinistra scegliere quindi **Expand all down one level of the hierarchy** (Espandi tutto di un livello verso il basso nella gerarchia), quindi ripetere l'operazione per visualizzare il livello più basso della gerarchia, che mostra i risultati per ogni mese.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-datetime-2.png)

Oltre che nella visualizzazione, la gerarchia è visibile nei dati restituiti per ogni report. La tabella seguente illustra i risultati di **Mostra dati** in seguito al drill-down in un report da un singolo mese o da tutti i mesi. 

Si noti che i dati sono gli stessi per i report dell'anno e del trimestre, ma, dopo avere eseguito il drill-down fino al livello di dettaglio specificato per **Valori**, è possibile osservare che il report singolo è più specifico e che il report relativo a tutti i mesi include più dati.


|Modalità di espansione|Anno|Trimestre|Mese|Giorno|
| ---|:---:|:---:|:---:|---|
|Singola|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-year.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-quarter.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-month.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-day.png)|
|Tutte|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-year.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-quarter.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-month.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-day.png)|


### <a name="hierarchical-category-data"></a>Dati di categorie gerarchici
I dati modellati da raccolte e sottoraccolte sono gerarchici. Un esempio valido sono i dati località. Si consideri una tabella in un'origine dati le cui colonne sono Paese, Stato, Città e CAP. I dati che condivide lo stesso paese, stato e città sono gerarchici.

Per questo esempio, seguire l'[esempio di analisi delle vendite al dettaglio](sample-datasets.md). Creare una visualizzazione istogramma in pila che esamini le **unità totali di quest'anno** (valori) per **territorio**, **città**, **codice postale** e **nome** (gruppo).  

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-category-1.png)

Con la modalità drill-down attivata, dalle icone in alto a sinistra scegliere quindi **Expand all down one level of the hierarchy** (Espandi tutto di un livello verso il basso nella gerarchia) tre volte.
Verrà visualizzato il livello più basso della gerarchia, che mostra i risultati per territorio, città e codice postale.

![](media\power-bi-visualization-drill-down/power-bi-hierarchical-axis-category-2.png)

Oltre che nella visualizzazione, la gerarchia è visibile nei dati restituiti per ogni report. La tabella seguente illustra i risultati di **Mostra dati** in seguito al drill-down in un report per un singolo mese o per tutti i territori. Quando si esegue il drill-down, è possibile osservare che il report singolo è più specifico e che il report relativo a tutti i territori include più dati.


| Modalità di espansione|Territorio|Città|Codice postale|Nome|
| ---|:---:|:---:|:---:|---|
|Singola|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-territory.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city-postal.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Tutte|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-territory.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city-postal.png)|![](media\power-bi-visualization-drill-down/power-bi-hierarchical-all-territory-city-postal-name.png)|


## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
* Se l'aggiunta di un campo data a una visualizzazione non crea una gerarchia, è possibile che il campo"data" non sia stato effettivamente salvato come data. Se si è proprietari del set di dati, aprirlo nella visualizzazione *Dati* in Power BI Desktop, selezionare la colonna che contiene la data e nella scheda Modellazione cambiare il **Tipo di dati** in **Data** o **Data/ora**. Se il report è stato condiviso con l'utente, contattare il proprietario per richiedere la modifica.  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Passaggi successivi
[Visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)

[Report di Power BI](service-reports.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

