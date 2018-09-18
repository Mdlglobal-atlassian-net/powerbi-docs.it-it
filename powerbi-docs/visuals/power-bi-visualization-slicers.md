---
title: Filtri dei dati in Power BI
description: Filtri dei dati in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: v-thepet
LocalizationGroup: Visualizations
ms.openlocfilehash: 5758bb53fe4a8a3658d242c3bd72da0a78500579
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44737509"
---
# <a name="slicers-in-power-bi"></a>Filtri dei dati in Power BI
Si desidera consentire ai lettori dei report di esaminare le metriche relative alle vendite complessive, ma anche evidenziare le prestazioni per i singoli direttori di zona relative a diversi intervalli di tempo. A tal fine, è possibile creare report separati o grafici comparativi oppure usare i filtri dei dati. Un filtro dei dati offre una modalità di filtro alternativa che consente di ridurre la parte del set di dati mostrata nelle altre visualizzazioni all'interno di un report. 

In questa esercitazione viene usato l'[esempio di analisi delle vendite al dettaglio](../sample-retail-analysis.md) disponibile gratuitamente per illustrare una procedura dettagliata per creare, formattare e usare filtri dei dati basati su un elenco o un intervallo di date. Si noterà che vi sono molti modi per formattare e usare i filtri dei dati. 

![filtro dei dati](./media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quando usare un filtro dei dati
I filtri dei dati rappresentano un'ottima scelta quando si vuole eseguire quanto segue:

* Visualizzare filtri importanti o di uso comune nell'area di disegno del report in modo da facilitare l'accesso.
* Facilitare la visualizzazione dello stato filtrato corrente senza dover aprire un elenco a discesa. 
* Filtrare per colonne non necessarie e nascoste nelle tabelle di dati.
* Creare più report mirati inserendo i filtri dei dati in corrispondenza di oggetti visivi importanti.

I filtri dei dati di Power BI presentano le limitazioni seguenti:

- I filtri dei dati non supportano i campi di input.
- I filtri dei dati non possono essere aggiunti a un dashboard.
- Il drill-down non è supportato per i filtri dei dati.
- I filtri dei dati non supportano i filtri a livello di oggetto visivo.

## <a name="create-slicers"></a>Creare filtri dei dati

Per creare un nuovo filtro dei dati, è possibile selezionare l'icona corrispondente e quindi selezionare il campo dati in base al quale applicare il filtro oppure trascinarlo nella casella **Campi** nel riquadro **Visualizzazioni**. In alternativa, è possibile prima selezionare o trascinare il campo dati per creare una visualizzazione e dopo selezionare l'icona del filtro dei dati per convertire la visualizzazione in un filtro. A seconda del tipo di dati, vengono creati tipi diversi di filtri dei dati, con effetti e opzioni differenti. 

La prima volta che si modifica un report, il pulsante **Ripristina impostazioni predefinite** diventa attivo. L'attivazione indica che è stata apportata una modifica alle impostazioni del report originale. Se si esce dal report, la modifica viene salvata. Quando si visualizza nuovamente il report non è necessario filtrare nuovamente i dati del report.  Tuttavia, se si vuole ripristinare le impostazioni predefinite dell'autore del report, selezionare il pulsante **Ripristina impostazioni predefinite** dalla barra dei menu superiore.

![pulsante Ripristina impostazioni predefinite](./media/power-bi-visualization-slicers/power-bi-reset-to-default.png)

> [!NOTE]
> Se il pulsante **Ripristina impostazioni predefinite** rimane disabilitato, significa che l'autore del report ha disabilitato la funzionalità per il report o che il report contiene un oggetto visivo personalizzato. È sufficiente passare il mouse sul pulsante per leggere la descrizione comando per una spiegazione. 

**Per creare un nuovo filtro dei dati in base al direttore di zona**

1. In Power BI Desktop o nel servizio Power BI aprire l'[esempio di analisi delle vendite al dettaglio](../sample-retail-analysis.md). Nel servizio Power BI selezionare **Modifica report** in alto a sinistra.
2. Nella pagina **Panoramica**, senza elementi selezionati nel canvas, selezionare l'icona **Filtro dei dati** ![icona del filtro dei dati](./media/power-bi-visualization-slicers/slicer-icon.png) nel riquadro **Visualizzazioni** per creare un nuovo filtro dei dati. 
3. Con il nuovo filtro dei dati selezionato, selezionare **District Manager** (Direttore di zona) in **District** (Zona) nel riquadro **Campi** per popolare il filtro dei dati. Il nuovo filtro dei dati è costituito da un elenco di nomi preceduti da caselle di selezione. 
    
    ![Nuovo filtro dei dati](./media/power-bi-visualization-slicers/2-slicer.png)
    
4. Ridimensionare e trascinare il filtro dei dati e gli altri elementi nel canvas per liberare spazio per il filtro. Si noti che i nomi degli elementi del filtro dei dati vengono troncati se si riducono troppo le dimensioni del filtro. 
5. Selezionare i nomi nel filtro dei dati e osservare gli effetti prodotti sulle altre visualizzazioni nella pagina. Selezionare di nuovo i nomi per deselezionarli e tenere premuto **CTRL** per selezionare più nomi. Selezionando tutti i nomi si ottiene lo stesso effetto di quando nessun nome è selezionato. 

>[!TIP]
>Per impostazione predefinita, gli elementi del filtro dei dati con elenco sono disposti in ordine alfanumerico crescente. Per visualizzarli in ordine decrescente, selezionare i puntini di sospensione (**...**) nell'angolo superiore destro del filtro dei dati e scegliere **Ordina per District Manager** nell'elenco a discesa. 

**Per creare un nuovo filtro dei dati in base a un intervallo di date**

1. Senza elementi selezionati nel canvas, selezionare l'elenco a discesa **Tempo** nel riquadro Campi e trascinare **Mese** (oppure **Data** nel servizio Power BI) nella casella **Valori** nel riquadro Visualizzazioni per creare una nuova visualizzazione.
2. Con la nuova visualizzazione selezionata, selezionare l'icona **Filtro dei dati** per convertire la nuova visualizzazione in un filtro dei dati. Quest'ultimo consiste in un dispositivo di scorrimento con un intervallo di date specificato.
    
    ![Nuovo filtro dei dati basato su intervallo](./media/power-bi-visualization-slicers/2a-date-slicer.png)
    
4. Ridimensionare e trascinare il filtro dei dati e gli altri elementi nel canvas per liberare spazio per il filtro. Si noti che le dimensioni del dispositivo di scorrimento cambiano in base a quelle del filtro dei dati, ma il controllo non è più visibile e le date vengono troncate se si riducono troppo le dimensioni del filtro. 
4. Selezionare diversi intervalli di date con il dispositivo di scorrimento oppure selezionare un campo data per digitare un valore o visualizzare un calendario popup per una selezione più precisa. Osservare gli effetti sulle altre visualizzazioni nella pagina.
    
    >[!NOTE]
    >I tipi di dati numerici e data/ora generano per impostazione predefinita filtri dei dati con dispositivi di scorrimento per intervalli. A partire dall'aggiornamento di Power BI del mese di febbraio 2018, i dispositivi di scorrimento per intervalli di numeri interi si allineano ai numeri interi anziché mostrare i valori decimali. 

>[!TIP]
>Anche se il campo dati **Mese** genera per impostazione predefinita un tipo di filtro dei dati con dispositivo di scorrimento per un intervallo **Tra**, è possibile impostare altri tipi di filtro dei dati e altre opzioni di selezione. Per modificare il tipo di filtro dei dati, passare il puntatore del mouse sull'area in alto a destra del filtro selezionato, selezionare la freccia in giù e scegliere una delle altre opzioni, ad esempio **Elenco** o **Prima**. Osservare come cambiano le opzioni di selezione e l'aspetto del filtro dei dati. 

Per altre informazioni sulla creazione e l'uso di filtri dei dati per un intervallo numerico, guardare il video seguente e vedere [Usare il filtro dei dati per l'intervallo numerico in Power BI Desktop](../desktop-slicer-numeric-range.md).
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 

## <a name="control-which-page-visuals-are-affected-by-slicers"></a>Controllare su quali oggetti visivi della pagina hanno effetto i filtri dei dati
Per impostazione predefinita, i filtri dei dati in una pagina di report hanno effetto su tutte le altre visualizzazioni nella pagina, incluse le interazioni tra le visualizzazioni. Mentre si scelgono i valori nell'elenco e nei dispositivi di scorrimento delle date appena creati, osservare gli effetti prodotti sulle altre visualizzazioni. I dati filtrati risultano da un'intersezione dei valori selezionati in entrambi i filtri dei dati. 

È possibile usare **Interazioni oggetti visivi** per impedire che alcune visualizzazioni nella pagina abbiano effetto su altre. Nella pagina **Panoramica** il grafico "Total Sales Variance by FiscalMonth and District Manager" (Varianza vendite complessive per mese fiscale e direttore di zona) mostra i dati comparativi delle vendite complessive per i responsabili di zona in base al mese, che si desidera mantenere sempre visibili. Per impedire alle selezioni del filtro dei dati di filtrare i dati in questo grafico, è possibile usare **Interazioni oggetti visivi**. 

1. Con il filtro dei dati District Manager (Direttore di zona) selezionato:
    - In Power BI Desktop fare clic sul menu **Formatta** in **Strumenti visivi** e selezionare **Modifica interazioni**.
    - Nel servizio Power BI dalla barra dei menu selezionare **Interazioni oggetti visivi** e attivare **Modifica interazioni**. 
   
   I controlli del filtro ![controlli del filtro](./media/power-bi-visualization-slicers/filter-controls.png) vengono visualizzati sopra tutti gli altri oggetti visivi della pagina. Inizialmente tutte le icone **Filtro** sono selezionate.
   
2. Selezionare l'icona **Nessuno** sopra il grafico **Total Sales Variance by FiscalMonth and District Manager** (Varianza vendite complessive per mese fiscale e direttore di zona) per impedire l'applicazione del filtro dei dati al grafico. 
3. Selezionare il filtro dei dati **Mese** e quindi di nuovo l'icona **Nessuno** sopra il grafico **Total Sales Variance da FiscalMonth and District Manager** (Varianza vendite complessive per mese fiscale e direttore di zona) per impedire l'applicazione del filtro dei dati al grafico. Per effetto di queste impostazioni, quando si selezionano nomi e intervalli di date nei filtri dei dati, il grafico Total Sales Variance dal grafico FiscalMonth and District Manager (Varianza vendite complessive per mese fiscale e direttore di zona) rimane invariato. 

Per altre informazioni sulla modifica delle interazioni, vedere [Interazioni tra le visualizzazioni in un report di Power BI](../service-reports-visual-interactions.md).

## <a name="sync-and-use-slicers-on-other-pages"></a>Sincronizzare e usare i filtri dei dati in altre pagine
A partire dall'aggiornamento di febbraio 2018 di Power BI, è possibile sincronizzare un filtro dei dati e usarlo in una pagina qualsiasi o in tutte le pagine di un report. 

Nel report corrente anche la pagina **District Monthly Sales** (Vendite mensili zona) include un filtro dei dati **District Manager** (Direttore di zona), che tuttavia non è sincronizzato con quello creato nella pagina **Panoramica**. Nei due filtri dei dati sono infatti selezionati elementi diversi. La pagina **New Stores** (Nuovi punti vendita) ha solo un filtro dei dati **Store Name** (Nome punto vendita). È possibile sincronizzare il nuovo filtro dei dati **District Manager** (Direttore di zona) con queste pagine in modo che le selezioni del filtro in una delle tre abbiano effetto sulle visualizzazioni in tutte le altre. 

1. Scegliere **Sincronizza filtri dei dati** dal menu **Visualizza** in Power BI Desktop o attivare **Riquadro Sincronizza filtri dei dati** nel servizio Power BI. Verrà visualizzato il riquadro **Sincronizza filtri dei dati**. 
2. Nella pagina **Panoramica** selezionare il filtro dei dati **District Manager** (Direttore di zona). Si noti che per la pagina **District Monthly Sales** (Vendite mensili zona) la casella nella colonna **Visibile** è già selezionata, perché anche in tale pagina è presente un filtro dei dati District Manager (Direttore di zona), mentre la casella nella colonna **Sincronizza** non è selezionata. 
    
    ![Sincronizza filtri dei dati](./media/power-bi-visualization-slicers/9-sync-slicers.png)
    
3. Nella colonna **Sincronizza** selezionare le caselle relative alle pagine **New Stores** (Nuovi punti vendita) e **District Monthly Sales** (Vendite mensili zona) per sincronizzare il filtro dei dati di **Panoramica** con tali pagine. 
    
3. Nella colonna **Visibile** selezionare la casella relativa alla pagina **New Stores** (Nuovi punti vendita) e lasciare selezionata quella relativa a **District Monthly Sales** (Vendite mensili zona). 
4. Osservare gli effetti delle impostazioni di sincronizzazione e visibilità del filtro dei dati nelle altre pagine. Nella pagina **District Monthly Sales** (Vendite mensili zona) il filtro dei dati **District Manager** (Direttore di zona) mostra ora le stesse selezioni del filtro dei dati nella pagina **Panoramica**. Nella pagina **New Stores** (Nuovi punti vendita) le selezioni del filtro dei dati **District Manager** (Direttore di zona) hanno effetto su quelle disponibili nel filtro dei dati **Store Name** (Nome punto vendita). 
    
    >[!TIP]
    >Anche se inizialmente il filtro dei dati appare nelle pagine sincronizzate con le stesse dimensioni e nella stessa posizione rispetto alla pagina originale, è possibile spostare, ridimensionare e formattare in modo indipendente i filtri dei dati sincronizzati nelle varie pagine. 

>[!NOTE]
>Se si sincronizza un filtro dei dati con una pagina, senza renderlo visibile in tale pagina, le selezioni dei filtro definite nelle altre pagine hanno comunque effetto sui dati visualizzati nella pagina.
 
## <a name="format-slicers"></a>Formattare i filtri dei dati
A seconda del tipo di filtro dei dati sono disponibili diverse opzioni di formattazione. Usando l'orientamento **Orizzontale**, il layout **Reattivo** e la colorazione **Elemento**, è possibile generare pulsanti o riquadri, anziché voci di elenco standard, e ridimensionare gli elementi del filtro dei dati in base a layout e dimensioni dello schermo differenti.  

1. Con il filtro dei dati **District Manager** (Direttore di zona) selezionato in una pagina qualsiasi, nel riquadro **Visualizzazioni** selezionare l'icona **Formatta** ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) per visualizzare i controlli di formattazione. 
    
    ![Formattazione](./media/power-bi-visualization-slicers/3-format.png)
    
2. Selezionare la freccia a discesa accanto a ogni categoria per visualizzare e modificare le opzioni. 

### <a name="general-options"></a>Opzioni generali
1. Selezionare il rosso in **Colore bordo** e modificare **Spessore bordo** impostandolo su "2". In questo modo vengono impostati il colore e lo spessore dei bordi e delle sottolineature degli elementi e delle intestazioni, se abilitati. 
2. In **Orientamento** è selezionata per impostazione predefinita l'opzione **Verticale**. Selezionare **Orizzontale** per generare un filtro dei dati con riquadri o pulsanti disposti in orizzontale e frecce di scorrimento per accedere agli elementi che non rientrano nell'area visualizzata del filtro.
    
    ![Orizzontale](./media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Attivare il layout **Reattivo** per modificare le dimensioni e la disposizione degli elementi del filtro dei dati in base alle dimensioni dello schermo e del filtro. Per i filtri dei dati con elenco, il layout reattivo è disponibile solo nell'orientamento orizzontale e impedisce che gli elementi vengano troncati su schermi di piccole dimensioni. Per i filtri dei dati con dispositivo di scorrimento per intervalli, la formattazione reattiva modifica lo stile di tale dispositivo, che può essere ridimensionato in modo più flessibile. Entrambi i tipi di filtri dei dati diventano icone di filtro in caso di dimensioni di visualizzazione molto ridotte. 
    
    ![Reattivo](./media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >Le modifiche del layout reattivo possono sostituire formattazioni specifiche di intestazioni o elementi impostate precedentemente. 
    
4. Impostare le dimensioni e la posizione del filtro dei dati con precisione numerica in **Posizione X**, **Posizione Y**, **Larghezza**, e **Altezza** o spostare e ridimensionare il filtro dei dati direttamente nel canvas. Provare a impostare dimensioni e disposizioni diverse per gli elementi e osservare come la formattazione reattiva cambia di conseguenza.  

    ![Pulsanti orizzontali](./media/power-bi-visualization-slicers/6-buttons.png)

Per altre informazioni sull'orientamento orizzontale e il layout reattivo, vedere [Creare un filtro dei dati reattivo e ridimensionabile in Power BI](../power-bi-slicer-filter-responsive.md).

### <a name="selection-controls-options-list-slicers-only"></a>Opzioni dei comandi di selezione (solo per filtri dei dati con elenco)
1. **Mostra l'opzione "Seleziona tutto"** è disattivata per impostazione predefinita **.** Attivarla per aggiungere al filtro dei dati un'opzione **Seleziona tutto** che consenta di selezionare o deselezionare alternativamente tutti gli elementi **.** Quando tutti gli elementi sono selezionati, è possibile fare clic o toccare un elemento per deselezionarlo, attivando così un filtro di tipo "esclusivo". 
    
    ![Seleziona tutto](./media/power-bi-visualization-slicers/7-select-all.png)
    
2. L'opzione **Selezione singola** è attivata per impostazione predefinita **.** Fare clic o toccare ogni singolo elemento per selezionarlo e fare clic o toccare tenendo premuto **CTRL** per selezionare più elementi. Disattivare **Selezione singola** per consentire la selezione di più elementi senza tenere premuto **CTRL****.** Fare clic o toccare di nuovo un elemento per deselezionarlo. 

### <a name="header-options"></a>Opzioni delle intestazioni
L'opzione **Intestazione** è attivata per impostazione predefinita e visualizza il nome del campo dati nella parte superiore del filtro dei dati **.** 
1. Formattare il testo dell'intestazione per rendere il **Colore carattere** rosso, le **Dimensioni testo** pari a 14 pt, e la **Famiglia di caratteri** Arial Black. 
2. In **Bordo** scegliere **Solo inferiore** per generare una linea di sottolineatura con le dimensioni e il colore impostati nelle opzioni **Generali**. 

### <a name="item-options-list-slicers-only"></a>Opzioni degli elementi (solo per filtri dei dati con elenco)
1. Formattare il testo e lo sfondo degli elementi in modo che il **Colore carattere** sia nero, lo **Sfondo** rosso chiaro, le **Dimensioni testo** pari a 10 pt e la **Famiglia di caratteri** Arial. 
2. In **Bordo** scegliere **Cornice** per disegnare un bordo intorno a ogni elemento con le dimensioni e il colore impostati nelle opzioni **Generali**. 
    
    ![Formattato](./media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Con **Orientamento > Orizzontale**, gli elementi deselezionati vengono visualizzati con i colori del testo e dello sfondo selezionati, mentre gli elementi selezionati usano l'impostazione predefinita, in genere sfondo nero con testo bianco.
    >- Con **Orientamento > Verticale**, gli elementi vengono visualizzati sempre con i colori impostati e le caselle di selezione sono sempre nere quando sono selezionate. 

### <a name="datenumeric-inputs-and-slider-options-range-slider-slicers-only"></a>Opzioni degli input di date/numerici e del dispositivo di scorrimento (solo per filtri dei dati con dispositivo di scorrimento per intervalli)
- Le opzioni degli input di date/numerici sono identiche a quelle degli **elementi** per i filtri dei dati con elenco, ad eccezione del fatto non è disponibile l'opzione **Bordo** o quella per la sottolineatura.
- Le opzioni del dispositivo di scorrimento per intervalli consentono di impostare il colore del dispositivo oppure di disattivare il dispositivo lasciando solo gli input numerici **.**

### <a name="other-formatting-options"></a>Altre opzioni di formattazione
Le altre opzioni di formattazione sono disattivate per impostazione predefinita. Quando vengono impostate su **On**: 
- **Titolo:** consente di aggiungere e formattare un titolo, in aggiunta e oltre all'intestazione, nella parte superiore del filtro dei dati. 
- **Sfondo:** consente di aggiungere un colore di sfondo per tutto il filtro dei dati e ne imposta la trasparenza.
- **Bloccare proporzioni:** mantiene la forma del filtro dei dati se viene ridimensionato.
- **Bordo:** consente di aggiungere un bordo di 1 pixel intorno al filtro dei dati e ne imposta il colore. Il bordo del filtro dei dati è indipendente dall'impostazione Bordo nelle impostazioni generali e non ne viene influenzato. 

## <a name="next-steps"></a>Passaggi successivi
[Iscriversi per una versione di valutazione gratuita](https://powerbi.microsoft.com/get-started/)

Idee su come migliorare Power BI? [Inviare un'idea](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

[Aggiungere una visualizzazione a un report](power-bi-report-add-visualizations-i.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI - Concetti di base](../service-basic-concepts.md)

