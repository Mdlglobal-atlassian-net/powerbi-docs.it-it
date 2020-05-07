---
title: Creare un pulsante di drill-through in Power BI
description: È possibile aggiungere pulsanti di drill-through nei report di Power BI, in modo che il comportamento dei report sia simile a quello delle app per un maggiore coinvolgimento degli utenti.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d3cb3c8093446d4417a59c5f64ab6b85a765e3c8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79206448"
---
# <a name="create-a-drill-through-button-in-power-bi-preview"></a>Creare un pulsante di drill-through in Power BI (anteprima)

Quando si crea un pulsante in Power BI, è possibile selezionare l'azione **Drill-through (anteprima)** . Questo tipo di azione crea un pulsante che esegue il drill-through in una pagina specifica con dettagli filtrati in base a un contesto selezionato.

Un pulsante di drill-through può essere utile se si vogliono rendere più facilmente individuabili scenari di drill-through importanti nei report.

In questo esempio, quando l'utente seleziona la barra di Word nel grafico, viene abilitato il pulsante **See details** (Visualizza dettagli).

![Pulsante See details](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Quando viene selezionato il pulsante **See details**, si esegue il drill-through alla pagina Market Basket Analysis. Come si può notare dall'oggetto visivo a sinistra, la pagina di drill-through è ora filtrata per Word.

![Oggetto visivo filtrato](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Configurare un pulsante di drill-through

Per configurare un pulsante di drill-through, è prima necessario [configurare una pagina di drill-through valida](desktop-drillthrough.md) all'interno del report. È poi necessario creare un pulsante con tipo di azione **Drill-through** e selezionare la pagina di drill-through come **Destinazione**.

Poiché il pulsante di drill-through ha due stati (drill-through abilitato o disabilitato), si noterà che sono disponibili due opzioni per la descrizione comando.

![Configurare il pulsante di drill-through](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Se si lasciano vuote le caselle delle descrizioni comando, Power BI le genera automaticamente in base ai campi di destinazione e di drill-through.

Di seguito è riportato un esempio della descrizione comando generata automaticamente quando il pulsante è disabilitato:

"To drill through to Market Basket Analysis (pagina di destinazione), select a single data point from Product (campo di drill-through). (Per eseguire il drill-through in Market Basket Analysis selezionare un singolo punto dati da Product).

![Descrizione comando generata automaticamente per il pulsante disabilitato](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Di seguito è riportato un esempio della descrizione comando generata automaticamente quando il pulsante è abilitato:

"Click to drill through to Market Basket Analysis (pagina di destinazione)."(Fare clic per eseguire il drill-through in Market Basket Analysis).

![Descrizione comando generata automaticamente per il pulsante abilitato](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Per fornire descrizioni comando personalizzate, è comunque sempre possibile immettere una stringa statica. Non è ancora supportata la formattazione condizionale per le descrizioni comando.

È possibile usare la formattazione condizionale per modificare il testo del pulsante in base al valore selezionato di un campo. A tale scopo, è necessario creare una misura che restituisce la stringa desiderata in base alla funzione DAX SELECTEDVALUE.

Di seguito è riportato un esempio di misura che restituisce "See product details" (Vedere i dettagli del prodotto) se NON è selezionato un singolo valore Product e che in caso contrario restituisce "See details for [the selected Product]" (Vedere i dettagli per [prodotto selezionato]):

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Dopo aver creato questa misura, selezionare l'opzione **Formattazione condizionale** per il testo del pulsante:

![Selezionare la formattazione condizionale](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Selezionare quindi la misura creata per il testo del pulsante:

![Valore basato sul campo](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Quando viene selezionato un singolo prodotto, il testo del pulsante sarà:

"See details for Word"

![Quando viene selezionato un singolo valore](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Quando non viene selezionato alcun prodotto oppure vengono selezionati più prodotti, il pulsante è disabilitato e il testo del pulsante sarà:

"See product details"

![Quando vengono selezionati più valori](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>Passare il contesto di filtro

Il pulsante funziona come il drill-through normale, quindi è anche possibile passare filtri per campi aggiuntivi applicando il filtro incrociato agli oggetti visivi che contengono il campo di drill-through. Ad esempio, usando **CTRL** + **clic** e filtro incrociato, è possibile passare più filtri per Store nella pagina di drill-through, perché le selezioni applicano il filtro incrociato all'oggetto visivo che contiene Product, ovvero il campo di drill-through:

![Passaggio del contesto di filtro](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Quando si seleziona il pulsante di drill-through, vengono passati i filtri sia per Store che per Product alla pagina di destinazione:

![Filtri in questa pagina](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Contesto di filtro ambiguo

Poiché il pulsante di drill-through non è associato a un singolo oggetto visivo, se la selezione è ambigua, il pulsante viene disabilitato.

In questo esempio il pulsante è disabilitato perché due oggetti visivi contengono entrambi una singola selezione per Product. L'ambiguità riguarda a quale punto dati di quale oggetto visivo associare l'azione drill-through:

![Contesto di filtro ambiguo](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>Limitazioni

- Questo pulsante non consente più destinazioni usando un solo pulsante.
- Questo pulsante supporta solo i drill-through all'interno dello stesso report. In altre parole, non supporta il drill-through tra report.
- La formattazione dello stato disabilitato per il pulsante è associata alle classi di colore nel tema del report. Altre informazioni sulle [classi di colori](desktop-report-themes.md#setting-structural-colors).
- L'azione drill-through funziona per tutti gli oggetti visivi predefiniti e funziona con *alcuni* oggetti visivi importati da AppSource. Tuttavia, non è garantito che funzioni con *tutti* gli oggetti visivi importati da AppSource.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sulle funzionalità simili o su come interagire con i pulsanti, vedere gli articoli seguenti:

* [Creare pulsanti](desktop-buttons.md)
* [Usare il drill-through nei report di Power BI](desktop-drillthrough.md)
* [Usare i segnalibri per condividere informazioni dettagliate e creare storie in Power BI](desktop-bookmarks.md)

