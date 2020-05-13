---
title: Usare i pulsanti in Power BI
description: È possibile aggiungere pulsanti nei report di Power BI, in modo che il comportamento dei report sia simile a quello delle app per un maggiore coinvolgimento degli utenti.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c703a4b67b642af5199413e80ff1e140905a2338
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83298551"
---
# <a name="use-buttons-in-power-bi"></a>Usare i pulsanti in Power BI
L'uso dei **pulsanti** in Power BI consente di creare report con un comportamento simile alle app e in tal modo di creare un ambiente coinvolgente in modo che gli utenti possano passare il mouse, fare clic e interagire in altri modi con il contenuto di Power BI. È possibile aggiungere pulsanti ai report in **Power BI Desktop** e nel **servizio Power BI**. Quando si condividono i report nel servizio Power BI, questi forniscono un'esperienza simile a un'app per gli utenti.

![Pulsanti in Power BI](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Creare pulsanti nei report

### <a name="create-a-button-in-power-bi-desktop"></a>Creare un pulsante in Power BI Desktop

Per creare un pulsante in **Power BI Desktop**, selezionare **Pulsanti** nella barra multifunzione **Inserisci**. Viene visualizzato un menu a discesa in cui è possibile selezionare il pulsante desiderato da una raccolta di opzioni, come illustrato nella figura seguente. 

![Aggiungere un controllo pulsante in Power BI Desktop](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Creare un pulsante nel servizio Power BI

Per creare un pulsante nel **servizio Power BI**, aprire il report nella visualizzazione di modifica. Selezionare **Pulsanti** nella barra dei menu superiore. Viene visualizzato un menu a discesa in cui è possibile selezionare il pulsante desiderato da una raccolta di opzioni, come illustrato nella figura seguente. 

![Aggiungere un controllo pulsante nel servizio Power BI](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Personalizzare un pulsante

Indipendentemente dal fatto che il pulsante venga creato in Power BI Desktop o nel servizio Power BI, il resto della procedura è uguale. Quando si seleziona un pulsante nell'area di disegno report, il riquadro **Visualizzazioni** mostra i diversi modi per personalizzare il pulsante in base alle specifiche esigenze. Ad esempio, è possibile attivare o disattivare **Testo pulsante**, spostando il dispositivo di scorrimento in tale sezione del riquadro **Visualizzazioni**. È anche possibile modificare l'icona del pulsante, il riempimento del pulsante, il titolo e l'azione eseguita quando gli utenti selezionano il pulsante in un report, tra le altre proprietà.

![Formattare un pulsante in un report di Power BI](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Impostare le proprietà dei pulsanti per lo stato inattivo, al passaggio del mouse o selezionato

I pulsanti in Power BI presentano tre stati: predefinito (aspetto dei pulsanti quando non sono selezionati o non vi si passa il mouse sopra), al passaggio del mouse o selezionato (azione spesso indicata come *fare clic*). Molte delle sezioni nel riquadro **Visualizzazioni** possono essere modificate singolarmente in base a questi tre stati, con una grande flessibilità per la personalizzazione dei pulsanti.

Le sezioni seguenti nel riquadro **Visualizzazioni** consentono di modificare la formattazione o il comportamento di un pulsante in base ai relativi tre stati:

* Testo del pulsante
* Icona
* Struttura
* Riempimento

Per specificare l'aspetto del pulsante per ogni stato, espandere una di queste sezioni e selezionare l'elenco a discesa visualizzato nella parte superiore della sezione. Nella figura seguente è visualizzata la sezione **Icona** espansa con l'elenco a discesa selezionato per mostrare i tre stati.

![Tre stati di un pulsante in un report di Power BI](media/desktop-buttons/power-bi-button-format.png)


## <a name="select-the-action-for-a-button"></a>Selezionare l'azione per un pulsante

È possibile selezionare l'azione da eseguire quando un utente seleziona un pulsante in Power BI. È possibile accedere alle opzioni per le azioni del pulsante dalla sezione **Azione** nel riquadro **Visualizzazioni**.

![Azione per un pulsante in Power BI](media/desktop-buttons/power-bi-button-action.png)

Le opzioni per le azioni dei pulsanti sono le seguenti:

- **Indietro** consente all'utente di tornare alla pagina precedente del report. Questa operazione è utile per le pagine di drill-through.
- **Segnalibro** visualizza la pagina del report associata a un segnalibro definito per il report corrente. Vedere altre informazioni sui [segnalibri in Power BI](desktop-bookmarks.md). 
- **Drill-through (anteprima)** sposta l'utente in una pagina di drill-through filtrata in base alla selezione, senza usare i segnalibri. Vedere altre informazioni sui [pulsanti di drill-through nei report](desktop-drill-through-buttons.md).
- **Navigazione sulle pagine** sposta l'utente in un'altra pagina all'interno del report, anche in questo caso senza usare i segnalibri. Per informazioni dettagliate, vedere [Creare l'esperienza di navigazione tra le pagine](#create-page-navigation) in questo articolo.
- **Domande e risposte** apre una finestra **Esplora domande e risposte**. 

Per alcuni pulsanti è disponibile un'azione predefinita selezionata automaticamente. Ad esempio, per il tipo di pulsante **Domande e risposte** è selezionata automaticamente l'azione **Domande e risposte**. Per altre informazioni su **Esplora domande e risposte**, vedere [questo post di blog](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer).

È possibile provare o testare i pulsanti creati per il report usando *CTRL+clic* sul pulsante da provare. 

### <a name="create-page-navigation"></a>Creare l'esperienza di navigazione tra le pagine

Con il tipo di **Azione** **Navigazione sulle pagine** è possibile creare rapidamente un'intera esperienza di navigazione senza dover salvare o gestire alcun segnalibro.

Per impostare un pulsante di navigazione tra le pagine, creare un pulsante con il tipo di azione **Navigazione sulle pagine** e selezionare la pagina **Destinazione**.

![Azione Navigazione sulle pagine](media/desktop-buttons/power-bi-page-navigation.png)

È possibile creare rapidamente un riquadro di spostamento personalizzato. Si possono così evitare la modifica e la gestione dei segnalibri se si vogliono cambiare le pagine da visualizzare nel riquadro di spostamento.

![Creare una pagina di navigazione](media/desktop-buttons/power-bi-build-navigation-pane.png)

È anche possibile formattare in modo condizionale la descrizione comando come per gli altri tipi di pulsanti.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sulle funzionalità simili o su come interagire con i pulsanti, vedere gli articoli seguenti:

* [Usare il drill-through nei report di Power BI](desktop-drillthrough.md)
* [Usare i segnalibri per condividere informazioni dettagliate e creare storie in Power BI](desktop-bookmarks.md)

