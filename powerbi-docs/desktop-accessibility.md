---
title: Accessibilità al report di Power BI Desktop
description: Funzionalità e suggerimenti per la creazione di report accessibili a Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: bd0565420382fc22af67b1363b41f6d8ed6e92ab
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="accessibility-in-power-bi-desktop-reports"></a>Accessibilità al report di Power BI Desktop
**Power BI Desktop** dispone di funzionalità che consentono agli utenti con particolari esigenze di usare e interagire più facilmente con i report di **Power BI Desktop**. Queste funzionalità includono la possibilità di usare un report tramite la tastiera o un'utilità per la lettura dello schermo, la tabulazione per evidenziare vari oggetti in una pagina e l'uso ponderato dei marcatori nelle visualizzazioni.

![Usare marcatori diversi per i grafici a linee e i grafici ad area per migliorare l'accessibilità](media/desktop-accessibility/accessibility_01.png)

> [!NOTE]
> Queste funzionalità di accessibilità sono disponibili con le versioni di giugno 2017 di **Power BI Desktop** e le versioni successive. Sono previste funzionalità di accessibilità aggiuntive anche per le versioni future.
> 
> 

## <a name="consuming-a-power-bi-desktop-report-with-a-keyboard-or-screen-reader"></a>Uso di un report di Power BI Desktop con la tastiera o l'utilità per la lettura dello schermo
A partire dalla versione di settembre 2017 di **Power BI Desktop**, è possibile fare clic su **?** per visualizzare una finestra che descrive i tasti di scelta rapida per l'accessibilità disponibili in **Power BI Desktop**.

![Fare clic su ? in Power BI Desktop per visualizzare i tasti di scelta rapida per l'accessibilità](media/desktop-accessibility/accessibility_03.png)

Con i miglioramenti di accessibilità, è possibile usare un report di **Power BI Desktop** con la tastiera o l'utilità di lettura dello schermo servendosi delle tecniche seguenti:

È possibile spostare lo stato attivo tra le schede della pagina del report o gli oggetti in una determinata pagina del report, usando **CTRL+F6**.

* Quando le *schede della pagina del report* sono attive, usare i tasti di *tabulazione* o le *frecce* per spostare lo stato attivo da una pagina del report a quella successiva. Il titolo della pagina del report, se selezionato, viene letto dall'utilità di lettura dello schermo. Per caricare la pagina del report attualmente attiva, utilizzare tasto *Invio* o la *barra dello spazio*.
* Quando la *pagina del report* caricata è attiva, usare il tasto di *tabulazione* per spostare lo stato attivo su ogni oggetto nella pagina, ad esempio tutte le caselle di testo, le immagini, le forme e i grafici. L'utilità di lettura dello schermo legge il tipo di oggetto e una descrizione dell'oggetto inserita dall'autore. 

È possibile premere **Alt + Maiusc + F10** per spostare lo stato attivo su un menu di oggetti visivi.

È possibile premere **Alt + Maiusc + F11** per visualizzare una versione accessibile della finestra *Visualizza dati*.

![Premere Alt + Maiusc + F11 in Power BI Desktop per visualizzare una finestra Visualizza dati accessibile per un oggetto visivo](media/desktop-accessibility/accessibility_04.png)

Queste opzioni di accessibilità aggiuntive sono state create per consentire agli utenti di utilizzare appieno i report di **Power BI Desktop** tramite una utilità per la lettura dello schermo e la tastiera.

## <a name="tips-for-creating-accessible-reports"></a>Suggerimenti per la creazione di report accessibili
I suggerimenti seguenti consentono di creare report di **Power BI Desktop** più accessibili.

* Per gli oggetti visivi **Riga**, **Area** e **Casella combinata** e per gli oggetti visivi **Dispersione** e **Bolle** attivare i marcatori e usare una *Forma del marcatore* diversa per ogni riga.
  
  * Per attivare i *Marcatori* , selezionare la sezione **Formato** sezione nel riquadro **Visualizzazioni**, espandere la sezione **Forme**, quindi scorrere verso il basso per trovare il tasto di attivazione e disattivazione **Marcatori** e *attivarlo*.
  * Quindi, selezionare il nome di ogni riga (o l'area, se si usa un grafico ad **area**) dalla casella di riepilogo a discesa nella sezione **Forme**. Sotto l'elenco a discesa, è possibile regolare molti aspetti del marcatore usato per la riga selezionata, tra cui la forma, il colore e le dimensioni.
  
  ![Usare marcatori diversi per i grafici a linee e i grafici ad area per migliorare l'accessibilità](media/desktop-accessibility/accessibility_01.png)
  
  * L'uso di una *forma del marcatore* diversa per ogni riga semplifica per gli utenti dei report la distinzione tra le righe o le aree.
* A titolo di precisazione del punto precedente, è consigliabile non fare affidamento sui colori per veicolare le informazioni. Come descritto in precedenza, l'uso di forme sulle linee, ovvero di marcatori, risulta l'approccio più utile.
* Selezionare un *tema* a contrasto elevato e facile da usare per i daltonici dalla raccolta dei temi e importarlo usando la funzione di anteprima del [**Tema**](desktop-report-themes.md).
* Per ogni oggetto nel report, inserire il *Testo alternativo*. In questo modo gli utenti del report comprendono il messaggio che l'utente vuole comunicare con un oggetto visivo, anche se non possono vedere l'oggetto visivo, l'immagine, la forma o la casella di testo. È possibile specificare *Testo alternativo* per qualsiasi oggetto in un report **Power BI Desktop**. A tale scopo, selezionare l'oggetto, ad esempio l'oggetto visivo, la forma e così via, e nel riquadro **Visualizzazioni** selezionare la sezione **Formato**, espandere **Generale**, quindi scorrere fino alla fine e immettere il testo nella casella **Testo alternativo**.
  
  ![Il testo alternativo per gli oggetti in un report può essere aggiunto in Visualizzazioni > Formato > Generale > casella Testo alternativo](media/desktop-accessibility/accessibility_02.png)
* Assicurarsi che il contrasto tra testo e colori di sfondo nei report sia sufficiente.
* Usare dimensioni di testo e tipi di carattere facilmente leggibili. Testo di piccole dimensioni o tipi di carattere difficili da leggere non favoriscono l'accessibilità.
* Includere il titolo, le etichette degli assi e le etichette dei dati in tutti gli oggetti visivi.

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni
Sono state rilevate problematiche e limitazioni note relative alle funzionalità di accessibilità, descritte nell'elenco seguente:

* JAWS è supportato nei report che vengono visualizzati nel **servizio Power BI**, inclusi tutti i report incorporati. JAWS è anche supportato in **Power BI Desktop**, ma è necessario aprire l'utilità per la lettura dello schermo prima di aprire i file di **Power BI Desktop** affinché funzioni correttamente.

## <a name="next-steps"></a>Passaggi successivi
* [Usare i temi dei report in Power BI Desktop (anteprima)](desktop-report-themes.md)

