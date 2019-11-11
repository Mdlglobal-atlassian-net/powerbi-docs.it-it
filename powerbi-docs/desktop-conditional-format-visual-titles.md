---
title: Titoli basati su espressione in Power BI Desktop
description: Creare titoli dinamici in Power BI Desktop che cambiano in base a espressioni programmatiche, usando la formattazione condizionale programmatica
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f3c1f047e3be7520005458294381877d1198ee21
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878622"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Titoli basati su espressione in Power BI Desktop

È possibile creare titoli dinamici e personalizzati per gli oggetti visivi di Power BI. Creando espressioni DAX (Data Analysis Expressions) basate su campi, variabili o altri elementi programmatici, i titoli degli oggetti visivi possono essere modificati automaticamente in base alle esigenze. Queste modifiche sono basate su filtri, selezioni o altre interazioni e configurazioni dell'utente.

![Screenshot dell'opzione di formattazione condizionale di Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

La creazione di titoli dinamici, talvolta detti anche *titoli basati su espressioni*, è semplice. 

## <a name="create-a-field-for-your-title"></a>Creare un campo per il titolo

Il primo passaggio per la creazione di un titolo basato su espressione consiste nel creare un campo nel modello da usare per il titolo. 

Ci sono moltissime opzioni creative per fare in modo che il titolo dell'oggetto visivo rifletta ciò che si vuole comunicare o esprimere. Verranno ora analizzati un paio di esempi.

È possibile creare un'espressione che cambia in base al contesto di filtro che l'oggetto visivo riceve per il nome del marchio del prodotto. La figura seguente mostra la formula DAX per un campo di questo tipo.

![Screenshot della formula DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Un altro esempio consiste nell'usare un titolo dinamico che cambia in base alla lingua o alle impostazioni cultura dell'utente. È possibile creare titoli specifici della lingua in una misura DAX usando la funzione `USERCULTURE()`. Questa funzione restituisce il codice delle impostazioni cultura per l'utente, in base alle impostazioni del sistema operativo o del browser. È possibile usare l'istruzione SWITCH DAX seguente per selezionare il valore tradotto corretto. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

In alternativa, è possibile recuperare la stringa da una tabella di ricerca che contiene tutte le traduzioni. Inserire la tabella nel modello. 

Questi sono solo due esempi che è possibile usare per creare titoli dinamici basati su espressione per gli oggetti visivi in Power BI Desktop. I limiti a ciò che è possibile fare con i titoli dipendono solo dal modello.


## <a name="select-your-field-for-your-title"></a>Selezionare il campo per il titolo

Dopo aver creato l'espressione DAX per il campo creato nel modello, è necessario applicarla al titolo dell'oggetto visivo.

Per selezionare il campo e applicare l'espressione, passare al riquadro **Visualizzazioni**. Nell'area **Formato** selezionare **Titolo** per visualizzare le opzioni per il titolo per l'oggetto visivo. 

Quando si fa clic con il pulsante destro del mouse su **Testo titolo**, viene visualizzato un menu di scelta rapida che consente di scegliere **<em>fx</em>Formattazione condizionale**. Quando si seleziona tale voce di menu, viene visualizzata una finestra di dialogo **Testo titolo**. 

![Screenshot della finestra di dialogo Testo titolo](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Da tale finestra è possibile selezionare il campo creato da usare per il titolo.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Ci sono alcune limitazioni all'implementazione corrente dei titoli basati su espressione per gli oggetti visivi:

* La formattazione basata su espressione non è attualmente supportata negli oggetti visivi Python, R o Fattori di influenza chiave.
* Il campo creato per il titolo deve essere un tipo di dati stringa. Le misure che restituiscono numeri o valori di data/ora (o qualsiasi altro tipo di dati), non sono attualmente supportate.
* I titoli basati su espressione non vengono trasferiti quando si aggiunge un oggetto visivo a un dashboard.

## <a name="next-steps"></a>Passaggi successivi

Questo articolo descrive come creare espressioni DAX che trasformano i titoli degli oggetti visivi in campi dinamici che possono cambiare quando gli utenti interagiscono con i report. Potrebbero risultare interessanti anche gli articoli seguenti.

* [Formattazione condizionale nelle tabelle](desktop-conditional-table-formatting.md)
* [Usare il drill-through tra report in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Usare il drill-through in Power BI Desktop](desktop-drillthrough.md)
