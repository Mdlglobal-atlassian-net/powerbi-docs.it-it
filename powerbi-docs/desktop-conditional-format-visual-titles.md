---
title: Titles basate su espressioni in Power BI Desktop
description: Creare i titoli dinamici in Power BI Desktop che modificano basati su espressioni a livello di codice, usando la formattazione condizionale a livello di codice
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769752"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Titles basate su espressioni in Power BI Desktop

È possibile creare dinamica, personalizzare i titoli per gli oggetti visivi di Power BI. Tramite la creazione di Data Analysis Expressions (DAX) basato su campi, variabili o altri elementi a livello di codice, i titoli degli oggetti visivi regola automaticamente in base alle esigenze. Queste modifiche sono basate sui filtri, le selezioni, o altre interazioni dell'utente e le configurazioni.

![Opzione di formattazione condizionale screenshot di Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

La creazione dinamici titoli, talvolta detta *titles basate su espressioni*, è molto semplice. 

## <a name="create-a-field-for-your-title"></a>Creare un campo per il titolo

Il primo passaggio nella creazione di un titolo per l'ordinamento basato su espressione consiste nel creare un campo nel modello da utilizzare per il titolo. 

Sono incluse numerose soluzioni creative per avere il titolo visual riflette ciò che si desidera venga ad esempio, o ciò che si desidera esprimere. Esaminiamo alcuni esempi.

È possibile creare un'espressione che cambia in base al contesto di filtro che riceve l'oggetto visivo per nome del marchio del prodotto. L'immagine seguente mostra la formula DAX per tale campo.

![Formula screenshot di DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Un altro esempio consiste nell'usare un titolo dinamico che le modifiche basate sulla lingua o le impostazioni cultura dell'utente. È possibile creare specifiche del linguaggio titoli in una misura DAX con la `USERCULTURE()` (funzione). Questa funzione restituisce il codice delle impostazioni cultura dell'utente, in base al sistema operativo o le impostazioni del browser. È possibile utilizzare l'istruzione switch DAX seguente per selezionare il valore tradotto corretto. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Oppure è possibile recuperare la stringa da una tabella di ricerca che contiene tutte le traduzioni. Tale tabella, inserire nel modello. 

Si tratta di un paio di esempi che è possibile usare per creare titoli dinamici e basati su espressioni per gli oggetti visivi in Power BI Desktop. Operazioni eseguibili con i titoli sono limitate solo per la tua immaginazione e il modello.


## <a name="select-your-field-for-your-title"></a>Selezionare il campo per il titolo

Dopo aver creato l'espressione DAX per il campo creato nel modello, è necessario applicarlo al titolo dell'oggetto visivo.

Per selezionare il campo e metterle in pratica, vedere la **visualizzazioni** riquadro. Nel **formato** area, selezionare **titolo** per mostrare le opzioni del titolo per l'oggetto visivo. 

Quando destro **testo titolo**, viene visualizzato un menu di scelta rapida che consente di selezionare ***fx * formattazione condizionale**. Quando si seleziona tale voce di menu, una **testo titolo** verrà visualizzata la finestra di dialogo. 

![Finestra di dialogo testo screenshot di titolo](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Da tale finestra, è possibile selezionare il campo creato per l'uso per il titolo.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Esistono alcune limitazioni per l'implementazione corrente delle titles basate su espressioni per gli oggetti visivi:

* Formattazione basata su espressione non è attualmente supportata in oggetti visivi di Python, gli oggetti visivi R o oggetto visivo di fattori di influenza chiave.
* Il campo creato per il titolo deve essere un tipo di dati stringa. Misure che restituiscano i numeri o data/ora (o qualsiasi altro tipo di dati) non sono attualmente supportate.

## <a name="next-steps"></a>Passaggi successivi

Questo articolo descrive come creare le espressioni DAX che trasformano i titoli degli oggetti visivi in campi dinamici che possono cambiare quando gli utenti interagiscono con i report. Possono essere utili gli articoli seguenti anche.

* [Usare cross-report drill-through in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md)