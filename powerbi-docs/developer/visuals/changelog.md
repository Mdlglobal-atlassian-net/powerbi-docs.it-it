---
title: Log delle modifiche dell'API per gli oggetti visivi di Power BI
description: Questo articolo descrive le modifiche principali nelle diverse versioni dell'API per gli oggetti visivi di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: fa8759d7edb519240140263bcd01bfdddd9c7d86
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141067"
---
# <a name="power-bi-visuals-api-changelog"></a>Log delle modifiche dell'API per gli oggetti visivi di Power BI
Questa pagina contiene un rapido riepilogo delle versioni dell'API. Le versioni elencate di seguito sono considerate stabili e non verranno modificate.

## <a name="api-v26"></a>API v2.6
  * Aggiunge **isInFocus** all'opzione di aggiornamento e il metodo **switchFocusModeState** all'host degli oggetti visivi
  * Supporta la personalizzazione dei **subtotali**

## <a name="api-v25"></a>API v2.5
  * Supporta il **[riquadro Analisi](./analytics-pane.md)**
  * Supporta i metodi `SelectionIdBuilder` **withMatrixNode** e **withTable**
  * Non supporta più l'interfaccia `DataRepetitionSelector`, sostituita con l'interfaccia `data.CustomVisualOpaqueIdentity`

## <a name="api-v23"></a>API v2.3
  * **[API della pagina di destinazione](./landing-page.md)**
  * **[API di archiviazione locale](./local-storage.md)**
  * **[API del filtro di tuple (filtro multicolonna)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API degli eventi di rendering](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v22"></a>API v2.2
  * Supporta il **[ripristino del filtro JSON da DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[API ContextMenu](./context-menu.md)**

## <a name="api-v21"></a>API v2.1
  * Miglioramenti delle prestazioni:
    * Tempi di caricamento più brevi
    * Footprint della memoria di dimensioni inferiori
    * Ottimizzazione delle transazioni di dati ed eventi  

**Note sulla versione**
* Le API di filtro sottoposte a refactoring saranno disponibili nell'API v2.2 e non sono supportate nell'API v2.1.
* Gli oggetti visivi ricevono solo il tipo dataView dichiarato nelle rispettive funzionalità. A seguito di questo aggiornamento, gli oggetti visivi che usavano più tipi dataView smetteranno di funzionare.
* Non è più supportata l'interfaccia `DataViewScopeIdentity`, sostituita con l'interfaccia `data.DataRepetitionSelector`. Se si usava la proprietà Key dell'interfaccia `DataViewScopeIdentity`, è possibile sostituirla con `JSON.stringify(identity)`
* `undefined` viene sostituito da `null` all'interno del dataView. Quando si esegue l'iterazione in una matrice tramite `var item in myArray`, `undefined` viene ignorato, ma non viene ignorato `null`. Gli oggetti visivi che usano questo modello possono smettere di funzionare a seguito di questo aggiornamento. Assicurarsi di controllare l'eventuale presenza di `null` nelle matrici:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* La proprietà `proto` non memorizza più metadati/dati nascosti all'interno di dataView. Gli oggetti visivi che accedono alle proprietà tramite `proto` possono smettere di funzionare a seguito di questo aggiornamento.

## <a name="api-v113"></a>API v1.13
* Supporta la funzione **[Sincronizza filtri dei dati](./enable-sync-slicers.md)** . Si noti che questa funziona solo per i filtri dei dati di campi singoli a causa dello stato del codice corrente di Power BI. [Altre informazioni](/power-bi/desktop-slicers).
* Accessibilità: [Supporto del contrasto elevato](./high-contrast-support.md) 
* Accessibilità: Flag Allow Keyboard Focus (Consenti messa a fuoco tastiera)

## <a name="api-v112"></a>API v1.12
* Supporta i temi
* Supporta **[fetchMoreData](./fetch-more-data.md)** . Si noti che l'**API per il recupero di altri dati** può superare il limite assoluto di 30.000 punti dati
* **[API delle descrizioni comandi del canvas](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v111"></a>API v1.11
* **[API FilterManager](./filter-api.md)**
* Supporta i **[segnalibri](./bookmarks-support.md)** 

## <a name="api-v110"></a>API v1.10
* Aggiunge `ILocalizationManager`
* **API di autenticazione**

## <a name="api-v19"></a>API v1.9
* **[API launchUrl](./launch-url.md)**

## <a name="api-v18"></a>API v1.8
* Supporta il nuovo tipo **fillRule** (gradiente) nello schema delle funzionalità
* Supporta la proprietà **rule** nello schema delle funzionalità per le proprietà degli oggetti

## <a name="api-v17"></a>API v1.7
* Supporta **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Supporta la **[modalità di modifica](./advanced-edit-mode.md)** per il passaggio degli oggetti visivi alla modalità di modifica
* Supporta gli **[oggetti visivi di Power BI R (HTML) interattivi](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** , basati su HTML

## <a name="api-v150"></a>API v1.5.0
* Supporta la funzione **[Consenti interazioni](./visuals-interactions.md)** per l'interattività degli oggetti visivi

## <a name="api-v140"></a>API v1.4.0
* Supporta la **[localizzazione](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Supporta le **[descrizioni comandi](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Aggiunge **colorPalette** per gestire i colori usati per l'oggetto visivo.
* Supporta la **selezione multipla**: selectionManager può accettare una matrice di `SelectionId`.
* Supporta **[oggetti visivi R](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** usando script R

## <a name="api-v110"></a>API v1.1.0
* Supporta oggetti visivi di debug in iFrame
* Aggiunge una sandbox leggera con inizializzazione più veloce dell'iFrame
* Corregge il problema [Lo schema funzionalità.oggetto non supporta il tipo "text"](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)
* Supporta `pbiviz update` per aggiornare le definizioni e lo schema dei tipi di API degli oggetti visivi
* Supporta il flag `--api-version` in `pbiviz new` per la creazione di oggetti visivi con una versione dell'API specifica
* Supporta la versione alfa dell'API v1.2.0

**Host di oggetti visivi**
* Aggiunge **createSelectionIdBuilder** per la creazione di identificatori univoci usati per la selezione di dati
* Aggiunge **createSelectionManager** per la gestione dello stato della selezione dell'oggetto visivo e comunica le modifiche all'host dell'oggetto visivo
* Aggiunge una matrice di **colori** predefiniti da usare negli oggetti visivi

## <a name="api-v100"></a>API v1.0.0
* Versione iniziale dell'API
