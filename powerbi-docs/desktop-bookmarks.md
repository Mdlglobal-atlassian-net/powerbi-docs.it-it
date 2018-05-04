---
title: Uso dei segnalibri in Power BI
description: I segnalibri in Power BI Desktop consentono di salvare visualizzazioni e impostazioni nei report e creare presentazioni di tipo storia
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
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 492eed949fd47b8f057bc67b127ba774b2218887
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Usare i segnalibri per condividere informazioni dettagliate e creare storie in Power BI 
I **segnalibri** in Power BI consentono di acquisire la visualizzazione attualmente configurata di una pagina di report, inclusi i filtri e lo stato degli oggetti visivi, e di tornare a tale stato anche in un momento successivo semplicemente selezionando il segnalibro salvato. 

È anche possibile creare una raccolta di segnalibri, disporli nell'ordine desiderato e successivamente passare da un segnalibro all'altro in una presentazione per evidenziare una serie di informazioni dettagliate oppure la storia che si vuole narrare tramite gli oggetti visivi e i report. 

![Segnalibri in Power BI](media/desktop-bookmarks/bookmarks_01.png)

I segnalibri possono avere diversi usi. È possibile usarli per tenere traccia dello stato di avanzamento per la creazione dei report (i segnalibri sono facili da aggiungere, eliminare e rinominare) oppure per creare una presentazione in stile PowerPoint che scorre i segnalibri nell'ordine specificato per comunicare una storia con un report. È anche possibile usare i segnalibri in altri modi, a seconda di come si ritiene più opportuno.

### <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>Abilitare l'anteprima dei segnalibri (versioni precedenti all'aggiornamento di marzo 2018)
A partire dalla versione di marzo 2018 di Power BI Desktop i segnalibri sono disponibili a livello generale. 

È sempre consigliabile eseguire l'aggiornamento alla versione più recente. Tuttavia, se la versione di Power BI Desktop in uso è precedente, è possibile provare la nuova funzionalità **segnalibri** a partire dalla versione di **Power BI Desktop** di **ottobre 2017** e anche nel **servizio Power BI** per i report abilitati per i segnalibri. Per abilitare la funzionalità di anteprima, selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità in anteprima**, quindi selezionare la casella di controllo accanto a **Segnalibri**. 

![Abilitare i segnalibri nella finestra Opzioni](media/desktop-bookmarks/bookmarks_02.png)

Dopo aver effettuato la selezione è necessario riavviare **Power BI Desktop** per abilitare la versione di anteprima dei segnalibri.

## <a name="using-bookmarks"></a>Utilizzo dei segnalibri
Per usare i segnalibri, selezionare la barra multifunzione **Visualizza**, quindi selezionare la casella per **Riquadro dei segnalibri**. 

![Visualizzare il riquadro dei segnalibri attivandolo nella barra multifunzione Visualizza.](media/desktop-bookmarks/bookmarks_03.png)

Quando si crea un segnalibro, insieme al segnalibro stesso vengono salvati gli elementi seguenti:

* Pagina corrente
* Filtri
* Filtri dei dati
* Ordinamento
* Posizione drill
* Visibilità (di un oggetto, usando il riquadro **Selezione**)
* Modalità messa a fuoco o **In evidenza** di qualsiasi oggetto visibile

Attualmente i segnalibri non salvano lo stato di evidenziazione incrociata. 

Configurare una pagina di report nel modo in cui si vuole che venga visualizzata nel segnalibro. Dopo aver disposto la pagina del report e gli oggetti visivi nel modo desiderato, per aggiungere un segnalibro selezionare **Aggiungi** nel riquadro **Segnalibri**. 

![Aggiungere un segnalibro](media/desktop-bookmarks/bookmarks_04.png)

**Power BI Desktop** crea un segnalibro e gli assegna un nome generico. Per *rinominare*, *eliminare* o *aggiornare* un segnalibro facilmente, selezionare i puntini di sospensione accanto al nome del segnalibro e quindi scegliere un'azione dal menu visualizzato.

![Usare i puntini di sospensione per visualizzare il sottomenu per un segnalibro](media/desktop-bookmarks/bookmarks_05.png)

Una volta creato un segnalibro, è possibile visualizzarlo facendo clic sul segnalibro nel riquadro **Segnalibri**. 

È anche possibile specificare se ogni segnalibro applicherà le proprietà dei *dati*, ad esempio filtri e filtri dei dati, le proprietà di *visualizzazione*, come evidenziazioni e relativa visibilità e le modifiche della pagina che presentano la pagina che era visibile quando è stato aggiunto il segnalibro. Queste funzionalità sono utili quando si usano i segnalibri per passare tra i tipi di oggetti visivi. In questo caso è probabile che si voglia disattivare la proprietà dei dati, in modo che i filtri non vengano reimpostati quando gli utenti cambiano tipo di oggetto visivo. 

Per apportare tali modifiche, selezionare i puntini di sospensione accanto al nome del segnalibro, come mostrato nell'immagine precedente, quindi selezionare o deselezionare i segni di spunta accanto a *Dati*, *Visualizzazione* e altri controlli. 

## <a name="arranging-bookmarks"></a>Disposizione dei segnalibri
Man mano che si creano i segnalibri, è possibile che l'ordine in cui vengono creati non è necessariamente lo stesso con cui si vuole presentarli ai destinatari. Riorganizzare l'ordine dei segnalibri è facile.

Nel riquadro **Segnalibri** è sufficiente trascinare i segnalibri per modificarne l'ordine, come mostrato nell'immagine seguente. La barra gialla tra i segnalibri indica la posizione in cui verrà collocato il segnalibro trascinato.

![Modificare l'ordine dei segnalibri mediante trascinamento della selezione](media/desktop-bookmarks/bookmarks_06.png)

L'ordine dei segnalibri diventa importante quando si usa la funzionalità **Visualizzazione** dei segnalibri, come descritto nella sezione successiva.

## <a name="bookmarks-as-a-slide-show"></a>Segnalibri come presentazione
Se si vuole presentare una raccolta di segnalibri nell'ordine in cui sono disposti, selezionare **Visualizzazione** nel riquadro **Segnalibri** per avviare una presentazione.

Quando si passa alla modalità **Visualizzazione**, è necessario tenere conto degli aspetti seguenti:

1. Il nome del segnalibro viene visualizzato nella barra del titolo del segnalibro nella parte inferiore dell'area di disegno.
2. Le frecce disponibili nella barra del titolo del segnalibro consentono di passare al segnalibro precedente o successivo.
3. Per uscire dalla modalità **Visualizzazione**, selezionare **Esci** nel riquadro **Segnalibri** o la **X** nella barra del titolo del segnalibro. 

![Funzionalità della barra del titolo del segnalibro](media/desktop-bookmarks/bookmarks_07.png)

Nella modalità **Visualizzazione** è possibile chiudere il riquadro **Segnalibri** (facendo clic sulla X nel riquadro stesso) per lasciare più spazio alla presentazione. Sempre nella modalità **Visualizzazione**, tutti gli oggetti visivi sono interattivi e disponibili per l'evidenziazione incrociata, come accade normalmente quando si interagisce con essi. 

## <a name="visibility---using-the-selection-pane"></a>Visibilità: utilizzo del riquadro Selezione
Con i segnalibri, è stato introdotto anche il nuovo riquadro **Selezione**. Il riquadro **Selezione** fornisce un elenco di tutti gli oggetti nella pagina corrente e consente di selezionare l'oggetto e specificare se questo è visibile o meno. 

![Abilitare il riquadro Selezione](media/desktop-bookmarks/bookmarks_08.png)

È possibile selezionare un oggetto usando il riquadro **Selezione**. È anche possibile attivare/disattivare la visibilità dell'oggetto facendo clic sull'icona a forma di occhio sulla destra dell'oggetto visivo. 

![Riquadro Selezione](media/desktop-bookmarks/bookmarks_09.png)

Quando viene aggiunto un segnalibro, viene anche salvato lo stato di visibilità di ogni oggetto in base all'impostazione corrispondente nel riquadro **Selezione**. 

È importante notare che i **filtri dei dati** continueranno a filtrare una pagina di report indipendentemente dal fatto che siano visibili o meno. Di conseguenza, è possibile creare molti segnalibri diversi, con impostazioni differenti per i filtri dei dati e ottenere una visualizzazione diversa (evidenziando informazioni dettagliate diverse) per una singola pagina di report in vari segnalibri.

## <a name="bookmarks-for-shapes-and-images"></a>Segnalibri per forme e immagini
È anche possibile collegare forme e immagini ai segnalibri. Con questa funzionalità, quando si fa clic su un oggetto, verrà mostrato il segnalibro associato a tale oggetto. Ciò può risultare particolarmente utile quando si utilizzano i pulsanti. Vedere l'articolo [Uso dei pulsanti in Power BI](desktop-buttons.md) per altre informazioni. 

Per assegnare un segnalibro a un oggetto, selezionare l'oggetto, quindi espandere la sezione **Azione** nel riquadro **Formato forma**, come mostrato nell'immagine seguente.

![Aggiungere un collegamento a un segnalibro a un oggetto](media/desktop-bookmarks/bookmarks_10.png)

Dopo aver impostato il dispositivo di scorrimento **Azione** su **Attiva** è possibile specificare se l'oggetto è un pulsante Indietro, un segnalibro o un comando Domande e risposte. Se si seleziona il segnalibro, è quindi possibile specificare a quale segnalibro è collegato l'oggetto.

Con i segnalibri collegati agli oggetti, è possibile effettuare diverse operazioni. Si può creare un sommario visivo nella pagina del report o fornire visualizzazioni diverse, ad esempio tipi di oggetti visivi, delle stesse informazioni, semplicemente facendo clic su un oggetto.

Nella modalità di modifica è possibile usare la combinazione CTRL+clic per seguire il collegamento quando non è attivata la modalità di modifica è sufficiente fare clic sull'oggetto per aprire il collegamento. 

## <a name="using-spotlight"></a>Utilizzo della funzionalità In evidenza
La funzionalità **In evidenza** è un'altra novità introdotta con i segnalibri. **In evidenza** consente di attirare l'attenzione su un grafico specifico, ad esempio, quando si presentano i segnalibri nella modalità **Visualizzazione**.

Ecco un confronto tra la modalità **In evidenza** e la modalità **messa a fuoco** e le relative differenze.

1. Nella modalità **messa a fuoco** un oggetto visivo può riempire l'intera area di disegno selezionando l'icona **modalità messa a fuoco**.
2. Con la funzionalità **In evidenza**, è possibile evidenziare un oggetto visivo nelle sue dimensioni originali grazie a un effetto di dissolvenza che rende tutti gli altri oggetti visivi nella pagina quasi trasparenti. 

![Confronto tra modalità messa a fuoco e in evidenza](media/desktop-bookmarks/bookmarks_11.png)

Quando viene fatto clic sull'icona **messa a fuoco** dell'oggetto visivo nell'immagine precedente, l'aspetto della pagina è simile al seguente:

![modalità messa a fuoco](media/desktop-bookmarks/bookmarks_12.png)

Al contrario, quando viene selezionata l'opzione **In evidenza** dal menu dei puntini di sospensione dell'oggetto visivo, l'aspetto della pagina è simile al seguente:

![modalità in evidenza](media/desktop-bookmarks/bookmarks_13.png)

Se quando viene aggiunto un segnalibro è selezionata l'una o l'altra modalità, la modalità attiva (messa a fuoco o in evidenza) viene mantenuta nel segnalibro.

## <a name="bookmarks-in-the-power-bi-service"></a>Segnalibri nel servizio Power BI
Quando si pubblica nel **servizio Power BI** un report con segnalibri, è possibile visualizzare e interagire con tali segnalibri nel **servizio Power BI**. Quando in un report sono disponibili segnalibri, è possibile selezionare **Visualizza > riquadro Selezione** oppure **Visualizza > riquadro Segnalibri** per visualizzare questi riquadri.

![Visualizzare i riquadri Segnalibri e Selezione nel servizio Power BI](media/desktop-bookmarks/bookmarks_14.png)

Nel **servizio Power BI** il **riquadro Segnalibri** funziona esattamente come in **Power BI Desktop** e consente di selezionare **Visualizza** per mostrare i segnalibri nell'ordine definito, come in una presentazione.

Si noti che per spostarsi tra i segnalibri è necessario usare la barra del titolo del segnalibro grigia e non le frecce nere, in quanto le frecce nere consentono di spostarsi tra le pagine del report e non tra i segnalibri.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
Per questa versione dei **segnalibri**, tenere presenti alcune limitazioni e considerazioni.

* La maggior parte degli oggetti visivi personalizzati dovrebbero funzionare bene con i segnalibri. Se si verificano problemi con i segnalibri e un oggetto visivo personalizzato, contattare l'autore di tale oggetto visivo personalizzato e richiedere l'aggiunta del supporto dei segnalibri all'oggetto visivo. 
* Se si aggiunge un oggetto visivo in una pagina del report dopo aver creato un segnalibro, l'oggetto visivo verrà visualizzato nel suo stato predefinito. Questo significa anche se si aggiunge un filtro dei dati a una pagina in cui sono stati creati segnalibri in precedenza, il filtro dei dati si comporterà in base allo stato predefinito.
* Se dopo aver creato un segnalibro gli oggetti visivi vengono spostati, le modifiche si rifletteranno nel segnalibro. 


## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sulle funzionalità simili o su come interagire con i segnalibri, vedere gli articoli seguenti:

* [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md)
* [Visualizzare un riquadro del dashboard o un oggetto visivo di un report in modalità messa a fuoco](service-focus-mode.md)

