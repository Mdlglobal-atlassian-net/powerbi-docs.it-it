---
title: Usare l'oggetto visivo Matrice in Power BI
description: Informazioni su come l'oggetto visivo Matrice consenta i layout con rientri e l'evidenziazione granulare in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6ad8900e5a95148b3f8333aa1953cc939d56f0e6
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375516"
---
# <a name="use-the-matrix-visual-in-power-bi"></a>Usare l'oggetto visivo Matrice in Power BI
Il **matrix** visual è simile a un **tabella**.  Una tabella supporta le dimensioni di 2 e i dati sono flat, vengono visualizzati e non aggregati i valori duplicati di significato. Una matrice rende più semplice per visualizzare i dati in modo significativo in più dimensioni, supporta un layout con rientri. La matrice viene automaticamente aggrega i dati e consente il drill-. 

È possibile creare oggetti visivi matrice nel **Power BI Desktop** e **servizio Power BI** report e l'evidenziazione incrociata elementi all'interno della matrice con altri oggetti visivi in tale pagina del report. Ad esempio, è possibile selezionare le righe, colonne e persino singole celle e l'evidenziazione incrociata. Inoltre, le singole celle e le selezioni multiple celle possono essere copiate e incollate in altre applicazioni. 

![Cross evidenziato matrice e grafico ad anello](media/desktop-matrix-visual/matrix-visual_2a.png)

Alla matrice sono associate molte funzionalità, che verranno illustrate nelle sezioni seguenti di questo articolo.


## <a name="understanding-how-power-bi-calculates-totals"></a>Informazioni sulla modalità di calcolo dei totali in Power BI

Prima di passare a informazioni su come usare l'oggetto visivo **Matrice**, è importante comprendere come Power BI calcola i valori totali e subtotali in tabelle e matrici. Per le righe di subtotale e totale, la misura viene valutata su tutte le righe nei dati sottostanti. *Non* si tratta semplicemente dell'addizione dei valori nelle righe visibili o visualizzate. Questo significa che la riga del totale può in effetti contenere valori diversi dal previsto. 

Esaminare gli oggetti visivi matrice seguenti. 

![Confronta tabella e matrice](media/desktop-matrix-visual/matrix-visual_3.png)

In questo esempio, ogni riga della matrice visual più a destra viene visualizzato il *quantità* per ogni combinazione di venditore e Data. Tuttavia, poiché un venditore viene visualizzato per più date, i numeri possono comparire più volte. Per questo motivo, un totale accurato calcolato dai dati sottostanti e la semplice addizione dei valori visibili non si equivalgono. Si tratta di una condizione comune quando i valori da sommare si trovano sul lato "uno" di una relazione uno-a-molti.

Quando si esaminano i totali e subtotali, tenere presente che tali valori sono basati sui dati sottostanti e non unicamente sui valori visibili. 

<!-- use Nov blog post video

## Expanding and collapsing row headers
There are two ways you can expand row headers. The first is through the right-click menu. You’ll see options to expand the specific row header you clicked on, the entire level or everything down to the very last level of the hierarchy. You have similar options for collapsing row headers as well.

![](media/desktop-matrix-visual/power-bi-expand1.png)

You can also add +/- buttons to the row headers through the formatting pane under the row headers card. By default, the icons will match the formatting of the row header, but you can customize the icons’ color and size separately if you want. 
Once the icons are turned on, they work similarly to the icons from PivotTables in Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

The expansion state of the matrix will save with your report. It can be pinned to dashboards as well, but consumers will need to open up the report to change the state. Conditional formatting will only apply to the inner most visible level of the hierarchy. Note that this expand/collapse experience is not currently supported when connecting to AS servers older than 2016 or MD servers.

![](media/desktop-matrix-visual/power-bi-expand3.png)

Watch the following video to learn more about expand/collapse in the matrix:

-->
## <a name="using-drill-down-with-the-matrix-visual"></a>Usando il drill down con l'oggetto visivo matrice
Con l'oggetto visivo matrice, è possibile eseguire moltissime interessanti drill-down attività che non erano disponibili prima. Tra queste, la possibilità di eseguire il drill-down usando righe e colonne e persino con sezioni e celle singole. Ecco una spiegazione del funzionamento di ognuna di queste attività.

### <a name="drill-down-on-row-headers"></a>Drill-down in intestazioni di riga
Nel riquadro **Visualizzazioni**, quando si aggiungono più campi alla sezione **Righe** dell'area **Campi** si abilita il drill-down per le righe dell'oggetto visivo matrice. La procedura è simile alla creazione di una gerarchia, che consente poi di eseguire il drill-down (e in seguito il backup) tramite la gerarchia stessa e di analizzare i dati a ogni livello.

Nell'immagine seguente, il **righe** sezione sono contenute *Sales stage* e *Opportunity size*, creazione di un raggruppamento (o gerarchia) nelle righe a cui è possibile il drill-through.

![Scheda che mostra le righe che vengono scelti i filtri](media/desktop-matrix-visual/power-bi-rows-matrix.png)

Quando per l'oggetto visivo sono stati creati raggruppamenti nella sezione **Righe**, vengono visualizzate le icone per il *drill-down* e l'*espansione* nell'angolo in alto a sinistra dell'oggetto visivo.

![matrice con i controlli di drill descritta](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

Analogamente al comportamento di drill-down ed espansione in altri oggetti visivi, questi pulsanti consentono di eseguire il drill-down (o il backup) nella gerarchia. In questo caso, è possibile il drill-down dal *Sales stage* al *Opportunity size*, come illustrato nell'immagine seguente, in cui è stato selezionato il drill-down un livello (diapason il).

![matrice con forchetta descritta](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Oltre a usare queste icone, è possibile selezionare una qualsiasi delle intestazioni di riga e il drill-down scegliendo dal menu visualizzato.

![opzioni di menu per le righe nella matrice](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Si noti che nel menu visualizzato sono presenti alcune opzioni, che generano risultati diversi:

Selezionando **drill-Down** espande la matrice per *che* livello di riga, *esclusione* tutte le altre intestazioni di riga eccetto l'intestazione di riga che è stato selezionato. Nell'immagine seguente, **proposta** > **drill-Down** è stato selezionato. Si noti che le altre righe di livello principale non compaiono più nella matrice. Questa modalità di drilling è molto utile e risulterà particolarmente interessante nella sezione dedicata all'**evidenziazione incrociata**.

![il drill-down un livello di matrice](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Selezionare il **drill-up** icona per tornare alla visualizzazione di primo livello precedente. Se si seleziona **proposta** > **Mostra il livello successivo**, si ottiene un elenco crescente di tutti gli elementi di livello successivo (in questo caso, il *Opportunity size* campo), senza la categorizzazione della gerarchia di livello superiore.

![matrice con livello successivo Show](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Selezionare il **drill-up** icona nell'angolo superiore sinistro per visualizzare tutte le categorie di livello superiore, che quindi selezionare la matrice **proposta** > **Espandi al livello successivo**, a vedere tutti i valori per entrambi i livelli della gerarchia - *Sales stage* e *Opportunity size*.

![Matrice usando Espandi livello successivo](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

È anche possibile usare la **Espandi** voce di menu per controllare ulteriormente la visualizzazione.  Ad esempio, selezionare **proposta** > **Espandi** > **selezione**. Power BI Visualizza una riga del totale per ogni *Sales stage* e tutte le *Opportunity size* le opzioni per *proposta*.

![Matrice dopo l'espansione applicato alla proposta](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Drill-down in intestazioni di colonna
Simile alla possibilità di eseguire il drill-nelle righe, è possibile anche il drill-down nel **colonne**. Nell'immagine seguente, sono presenti due campi nel **colonne** well campo, la creazione di una gerarchia simile a quella usata per le righe in precedenza in questo articolo. Nel **colonne** campo bene, abbiamo *area* e *segmento*. Non appena è stato aggiunto il secondo campo a **colonne**, un nuovo menu a discesa visualizzato sull'oggetto visivo, è attualmente visualizzata **righe**.

![Matrice dopo il secondo valore della colonna aggiunto](media/desktop-matrix-visual/power-bi-matrix-row.png)

Per eseguire il drill-nelle colonne, selezionare **colonne** dalle *il drill-* menu che può essere trovato nell'angolo superiore sinistro della matrice. Selezionare il *orientale* area e scegliere **drill-Down**.

![menu di scelta per il drill-down per le colonne](media/desktop-matrix-visual/power-bi-matrix-column.png)

Quando si seleziona **drill-Down**, il livello successivo della gerarchia di colonne per *area > orientale* consente di visualizzare, in questo caso *Opportunity count*. Altra area consente di visualizzare, ma è disattivata.

![eseguire il drill-down un livello di matrice con colonne](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

Il resto delle voci di menu per le colonne funzionano esattamente come per le righe (vedere la sezione precedente **drill-down nelle intestazioni di riga**). È possibile **Mostra il livello successivo** e **Espandi al livello successivo** con colonne nello stesso modo è possibile con le righe.

> [!NOTE]
> Le icone per il drill-down e il drill-up nell'angolo superiore sinistro dell'oggetto visivo matrice si applicano solo alle righe. Per eseguire il drill-down nelle colonne, è necessario usare il menu di scelta rapida.
> 
> 

## <a name="stepped-layout-with-matrix-visuals"></a>Layout con rientri con gli oggetti visivi matrice
L'oggetto visivo **Matrice** applica automaticamente un rientro alle sottocategorie in una gerarchia al di sotto di ogni elemento padre. Questa funzionalità è detta **Layout con rientri**.

Nella versione *originale* dell'oggetto visivo matrice, le sottocategorie sono visualizzate in una colonna totalmente diversa, occupando più spazio nell'oggetto visivo. L'immagine seguente illustra la tabella nell'oggetto visivo **Matrice** originale, con le sottocategorie visualizzate in una colonna separata.

![vecchia maniera del formato predefinita per le matrici](media/desktop-matrix-visual/matrix-visual_14.png)

Nell'immagine seguente è presente un oggetto visivo **Matrice** con la funzionalità **Layout con rientri** attiva. La categoria *Computers* include alcune sottocategorie (Computers Accessories, Desktops, Laptops, Monitors e così via) leggermente rientrate, per cui l'oggetto visivo risulta più chiaro e conciso.

![modo in cui tale matrice formati di dati corrente](media/desktop-matrix-visual/matrix-visual_13.png)

È possibile regolare facilmente le impostazioni di Layout con rientri. Con l'oggetto visivo **Matrice** selezionato, nella sezione **Formato** (icona del rullo) del riquadro **Visualizzazioni** espandere la sezione **Intestazioni di riga**. Sono disponibili due opzioni: l'interruttore **Layout con rientri** (per attivarlo o disattivarlo) e **Rientro del layout con rientri** (per specificare il rientro, in pixel).

![Le intestazioni di riga di schede di memoria con controllo di layout con rientri](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Se si disattiva **Layout con rientri**, le sottocategorie vengono visualizzate in un'altra colonna anziché rientrate sotto la categoria padre.

## <a name="subtotals-with-matrix-visuals"></a>Subtotali con oggetti visivi matrice
Negli oggetti visivi matrice è possibile attivare o disattivare i subtotali, sia per le righe che per le colonne. L'immagine seguente mostra che i subtotali delle righe sono impostati su **Sì**.

![subtotali e totali con matrice](media/desktop-matrix-visual/matrix-visual_20.png)

Nella sezione **Formato** del riquadro **Visualizzazioni** espandere la scheda **Subtotali** e impostare il dispositivo di scorrimento **Subtotali righe** su **No**. In questo caso, i subtotali non vengono visualizzati.

![matrice con i subtotali disattivata](media/desktop-matrix-visual/matrix-visual_21.png)

Lo stesso processo vale per i subtotali delle colonne.

## <a name="cross-highlighting-with-matrix-visuals"></a>Evidenziazione incrociata con gli oggetti visivi matrice
Con l'oggetto visivo **Matrice** è possibile selezionare qualsiasi elemento nella matrice come base per l'evidenziazione incrociata. Quando si seleziona una colonna in un oggetto visivo **Matrice**, la colonna viene evidenziata, come anche gli altri oggetti visivi nella pagina del report. Questo tipo di evidenziazione incrociata accomuna da sempre altri oggetti visivi e le selezioni di un punto dati, quindi ora è estesa anche all'oggetto visivo **Matrice**.

Anche per l'evidenziazione incrociata è possibile usare CTRL+clic per selezionare. Nell'immagine seguente, ad esempio, è stato selezionato un insieme di sottocategorie dall'oggetto visivo **Matrice**. Si noti come gli elementi che non sono stati selezionati nell'oggetto visivo sono visualizzati in grigio, mentre gli altri oggetti visivi nella pagina riflettono le selezioni effettuate nell'oggetto visivo **Matrice**.

![report pagina incrociato highighted per una matrice](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Copia di valori da Power BI per l'uso in altre applicazioni

La matrice o la tabella può avere contenuto che si desidera usare in altre applicazioni, ad esempio Dynamics CRM, Excel e anche altri report di Power BI. Con il menu di scelta rapida di Power BI è possibile copiare una singola cella o una selezione di celle negli Appunti e incollare la selezione nell'altra applicazione.

![Opzioni di copia](media/desktop-matrix-visual/power-bi-cell-copy.png)

* Per copiare il valore di una singola cella, selezionare la cella, fare clic con il pulsante destro del mouse e scegliere **Copia valore**. Con il valore della cella non formattato negli Appunti, è ora possibile incollarlo in un'altra applicazione.

    ![Opzioni di copia](media/desktop-matrix-visual/power-bi-copy.png)

* Per copiare più di una singola cella, selezionare un intervallo di celle o usare CTRL per selezionare una o più celle. La copia includerà le intestazioni di colonna e riga.

    ![Incollare in Excel](media/desktop-matrix-visual/power-bi-copy-selection.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Ombreggiatura e colore carattere con gli oggetti visivi matrice
Con l'oggetto visivo matrice, è possibile applicare **formattazione condizionale** (colori e ombreggiatura e barre dei dati) allo sfondo delle celle della matrice, nonché applicare la formattazione condizionale al testo e ai valori stessi.

Per applicare la formattazione condizionale, selezionare la matrice visual e aprire il **formato** riquadro. Espandere la **formattazione condizionale** carta e per **colore di sfondo**, **colore carattere**, o **barre dei dati**, attivare il dispositivo di scorrimento **Su**. Attivazione di una di queste opzioni viene visualizzato un collegamento per *controlli avanzati*, che consente di personalizzare i colori e i valori per la formattazione dei colori.
  
  ![Controllo di barre dei dati visualizzata nel riquadro di formato](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Selezionare *controlli avanzati* per visualizzare una finestra di dialogo che consente di apportare modifiche. Questo esempio mostra la finestra di dialogo per **barre dei dati**.

![Riquadro di barre dei dati](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Passaggi successivi

[Grafici a dispersione e grafici a bolle in Power BI](power-bi-visualization-scatter.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)