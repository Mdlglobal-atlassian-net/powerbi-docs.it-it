---
title: Eseguire il drill-down e il drill-up in un oggetto visivo
description: Questo articolo illustra come eseguire il drill-down in un oggetto visivo nel servizio Microsoft Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/1/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: bc6a6557d01ba8145659bb244be8eb5786220665
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71943995"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Modalità di espansione in un oggetto visivo in Power BI

Questo articolo illustra come eseguire il drill-down in un oggetto visivo nel servizio Microsoft Power BI. Usando il drill-down e il drill-up nei punti dati, è possibile analizzare le informazioni dettagliate disponibili sui dati. 

## <a name="drill-requires-a-hierarchy"></a>L'espansione richiede una gerarchia

Quando un oggetto visivo ha una gerarchia, è possibile eseguire il drill-down per rivelare dettagli aggiuntivi. Ad esempio, potrebbe esserci un oggetto visivo che calcola il numero di medaglie olimpiche in base a una gerarchia composta da sport, disciplina ed eventi. Per impostazione predefinita, l'oggetto visivo indicherà il numero di medaglie per sport: ginnastica, sci, sport acquatici e così via, ma, poiché contiene una gerarchia, selezionando uno degli oggetti visivi (ad esempio una barra, una riga o una bolla), potrebbe essere visualizzata un'immagine sempre più dettagliata. Selezionando l'elemento **aquatics**, verranno visualizzati i dati relativi a nuoto, tuffi e pallanuoto.  Selezionando l'elemento **diving**. verranno visualizzati i dettagli relativi a trampolino, piattaforma e tuffi sincronizzati.

Le date sono un tipo univoco di gerarchia.  I progettisti di report spesso aggiungono gerarchie di date agli oggetti visivi. Una delle comuni gerarchie di date contiene anno, trimestre, mese e giorno. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Trovare gli oggetti visivi di cui è possibile eseguire il drill
Se non si è certi di quali oggetti visivi di Power BI contengano una gerarchia, passare il mouse sopra un oggetto visivo. Se nella parte superiore viene visualizzata una combinazione di questi controlli di drill, significa che l'oggetto visivo ha una gerarchia.

![Screenshot delle icone di drill.](./media/end-user-drill/power-bi-drill-icons.png)  

## <a name="learn-how-to-drill-down-and-up"></a>Informazioni su come eseguire il drill-down e il drill-up

In questo esempio si userà una mappa ad albero con una gerarchia costituita da territorio, città, codice postale e nome del negozio. La mappa ad albero, prima del drill, visualizza le unità totali vendute durante l'anno per territorio. 

![Screenshot della mappa ad albero e dei filtri.](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Due modi per accedere alle funzionalità di drill

Sono disponibili due modi per l'accesso alle funzionalità di drill-down, drill-up ed espansione per gli oggetti visivi con gerarchie. Provarli entrambi e usare quello preferito.

- Primo modo: passare il mouse su un oggetto visivo per visualizzare e usare le icone.  

    ![Screenshot dell'esempio di passaggio del mouse.](./media/end-user-drill/power-bi-hover.png)

- Secondo modo: fare clic con il pulsante destro del mouse su un oggetto visivo per visualizzare e usare il menu.

    ![Screenshot dell'esempio di clic con il pulsante destro del mouse.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>Percorsi di drill-down

### <a name="drill-down-all-fields-at-once"></a>Drill-down di tutti i campi contemporaneamente
![Icona Drill-down](./media/end-user-drill/power-bi-drill-icon3.png)

Sono disponibili diversi modi per eseguire il drill-down nell'oggetto visivo. Selezionando l'icona di drill-down, è possibile passare al livello successivo della gerarchia. Se si sta esaminando il livello **Territory** per Kentucky e Tennessee, è possibile eseguire il drill-down fino al livello di città per entrambi gli stati, quindi al livello di codice postale per entrambi gli stati e infine al livello di nome del negozio per entrambi gli stati. Ogni passaggio del percorso visualizza nuove informazioni.

![Diagramma che mostra il percorso di drill-down](./media/end-user-drill/power-bi-drill-path.png)

Selezionare l'icona di drill-up ![Icona Drill-up](./media/end-user-drill/power-bi-drill-icon5.png) fino a tornare a "Total units this year by territory".

### <a name="expand-all-fields-at-once"></a>Espandere tutti i campi contemporaneamente
![L'icona di espansione](./media/end-user-drill/power-bi-drill-icon6.png)

**Espandi** aggiunge un altro livello della gerarchia alla visualizzazione corrente. Di conseguenza, dal livello **Territory** (Territorio) è possibile espandere e aggiungere città, codice postale e nome alla mappa ad albero. Ogni passaggio nel percorso visualizza le stesse informazioni e aggiunge un livello di nuove informazioni.

![Diagramma che mostra il percorso di espansione](./media/end-user-drill/power-bi-expand-path.png)

È anche possibile scegliere di eseguire il drill-down o di espandere un campo alla volta.


### <a name="drill-down-one-field-at-a-time"></a>Drill-down di un campo


1. Selezionare l'icona di drill-down per attivarla ![Screenshot dell'icona di attivazione/disattivazione del drill-down attivata.](./media/end-user-drill/power-bi-drill-icon2.png).

    È ora possibile eseguire il drill-down di **un campo alla volta** selezionando un elemento visivo. Esempi di elementi visivi sono: barra, bolla e foglia.

    ![Screenshot dell'oggetto visivo con freccia che punta all'icona di attivazione/disattivazione del drill-down attivata.](media/end-user-drill/power-bi-drill-icon-selected.png)

    Se non si attiva il drill-down, la selezione di un elemento visivo (come una barra, una bolla o una foglia) non eseguirà il drill-down, ma filtrerà in modo incrociato gli altri grafici nella pagina del report.

1. Selezionare la foglia per **TN**. La mappa ad albero mostra ora tutte le città e i territori del Tennessee con un negozio.

    ![Screenshot della mappa ad albero che mostra i dati solo per TN.](media/end-user-drill/power-bi-drill-down-one.png)

1. A questo punto, è possibile:

    1. Continuare a eseguire il drill-down per il Tennessee.

    1. Eseguire il drill-down per una città del Tennessee specifica.

    1. Eseguire l'espansione.

    Continuare a eseguire il drill-down di un campo alla volta.  Selezionare **Knoxville, TN**. La mappa ad albero mostra ora il codice postale del negozio di Knoxville.

    ![Screenshot della mappa ad albero che mostra il codice postale 37919.](media/end-user-drill/power-bi-drill-two.png)

    Si noti che il titolo viene modificato durante il drill-down e il drill-up.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Espandere tutti i campi ed espandere un campo alla volta

La visualizzazione di una mappa ad albero che mostra solo un codice postale non è informativa.  *Espandere* di un livello verso il basso nella gerarchia.  

1. Con la mappa ad albero attiva, selezionare l'icona di *espansione verso il basso* ![Screenshot dell'icona di espansione verso il basso](./media/end-user-drill/power-bi-drill-icon6.png). La mappa ad albero mostra ora due livelli della gerarchia: codice postale e nome del negozio.

    ![Screenshot della mappa ad albero che mostra il codice postale e il nome del negozio](./media/end-user-drill/power-bi-expand-one.png)

1. Per visualizzare tutti e quattro i livelli di gerarchia dei dati per il Tennessee, selezionare la freccia di drill-up fino a raggiungere il secondo livello, **Total units this year by territory and city** (Unità totali di quest'anno per territorio e città), della mappa ad albero.

    ![Screenshot della mappa ad albero che mostra tutti i dati per TN.](media/end-user-drill/power-bi-expand-two.png)

1. Assicurarsi che il drill-down sia ancora attivato ![Screenshot dell'icona di attivazione/disattivazione del drill-down attivata](./media/end-user-drill/power-bi-drill-icon2.png) e selezionare l'icona di *espansione verso il basso* ![Screenshot dell'icona di espansione verso il basso](./media/end-user-drill/power-bi-drill-icon6.png). La mappa ad albero ora mostra lo stesso numero di foglie (caselle), ma ogni foglia presenta dettagli aggiuntivi. Invece di mostrare solo città e stato, la mappa mostra anche il codice postale.

    ![Screenshot dell'oggetto visivo che mostra città, stato e codice postale.](./media/end-user-drill/power-bi-expand-three.png)

1. Selezionare l'icona di *espansione verso il basso* ancora una volta per visualizzare tutti e quattro i livelli di dettaglio della gerarchia per il Tennessee nella mappa ad albero. Passare il mouse su una foglia per visualizzare altri dettagli.

    ![Screenshot della mappa ad albero che mostra una descrizione comando con dati specifici della foglia.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>Visualizzare i dati durante il drill
Usare **Mostra i dati** per vedere che cosa accade in background. Ogni volta che si esegue il drill o l'espansione, **Mostra i dati** visualizza i dati che vengono usati per compilare l'oggetto visivo. Questo può essere utile per comprendere come le gerarchie, il drill e l'espansione interagiscono per compilare gli oggetti visivi. 

Nell'angolo in alto a destra selezionare i puntini di sospensione (...) e quindi selezionare **Mostra i dati**. 

![Screenshot del menu dei puntini di sospensione.](./media/end-user-drill/power-bi-ellipses.png)

La tabella seguente illustra i risultati del drill-down di tutti i campi contemporaneamente dal territorio al nome del negozio.  


![Screenshot della visualizzazione dei dati per tutti e quattro i livelli di drill-down.](./media/end-user-drill/power-bi-show-data.png)

Si noti che i totali sono gli stessi per **City**, **PostalCode** e **Name**, ma non sarà sempre così.  Per questi dati, tuttavia, è presente un solo negozio per ogni codice postale e per ogni città.  



## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
Per impostazione predefinita, il drill-down non filtra altri oggetti visivi in un report. Il progettista del report, tuttavia, può modificare questo comportamento predefinito. Quando si esegue il drill, verificare se agli altri oggetti visivi nella pagina viene applicato il filtro incrociato o l'evidenziazione incrociata.


## <a name="next-steps"></a>Passaggi successivi

[Oggetti visivi nei report di Power BI](../visuals/power-bi-report-visualizations.md)

[Report di Power BI](end-user-reports.md)

[Power BI - Concetti di base](end-user-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
