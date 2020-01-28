---
title: Concetti sugli oggetti visivi di Power BI
description: Questo articolo descrive come gli oggetti visivi si integrano con Power BI e come un utente può interagire con un oggetto visivo in Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bb0834527ba23c6cfcc155cc65cd0318b296ba84
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925605"
---
# <a name="visuals-in-power-bi"></a>Oggetti visivi in Power BI

Questo articolo descrive come gli oggetti visivi si integrano con Power BI e come un utente può interagire con un oggetto visivo in Power BI. 

La figura seguente illustra in che modo le azioni comuni basate sugli oggetti visivi eseguite da un utente, ad esempio la selezione di un segnalibro, vengono elaborate in Power BI.

![Diagramma delle azioni su un oggetto visivo di Power BI](./media/visual-concept.svg)

## <a name="visuals-get-updates-from-power-bi"></a>Aggiornamenti degli oggetti visivi da Power BI

Un oggetto visivo chiama un metodo `update` per ottenere gli aggiornamenti da Power BI. Il metodo `update` contiene in genere la logica principale dell'oggetto visivo ed è responsabile del rendering di un grafico o della visualizzazione dei dati.

Gli aggiornamenti vengono attivati quando l'oggetto visivo chiama il metodo `update`.

## <a name="action-and-update-patterns"></a>Modelli di azione e di aggiornamento

Le azioni e i successivi aggiornamenti degli oggetti visivi di Power BI si verificano sulla base di uno dei tre modelli seguenti:

* L'utente interagisce con un oggetto visivo tramite Power BI.
* L'utente interagisce direttamente con l'oggetto visivo.
* L'oggetto visivo interagisce con Power BI.

### <a name="user-interacts-with-a-visual-through-power-bi"></a>L'utente interagisce con un oggetto visivo tramite Power BI

* Un utente apre il pannello delle proprietà dell'oggetto visivo.

    Quando un utente apre il pannello delle proprietà dell'oggetto visivo, Power BI recupera gli oggetti e le proprietà supportati dal file *capabilities.json* dell'oggetto visivo. Per ricevere i valori effettivi delle proprietà, Power BI chiama il metodo `enumerateObjectInstances` dell'oggetto visivo. L'oggetto visivo restituisce i valori effettivi delle proprietà.

    Per altre informazioni, vedere [Funzionalità e proprietà degli oggetti visivi di Power BI](capabilities.md).

* Un utente [modifica un proprietà dell'oggetto visivo](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) nel pannello di formattazione.

    Quando un utente modifica il valore di una proprietà nel pannello di formattazione, Power BI chiama il metodo `update` dell'oggetto visivo. Power BI passa il nuovo oggetto `options` al metodo `update`. Gli oggetti contengono i nuovi valori.

    Per altre informazioni, vedere [Oggetti e proprietà](objects-properties.md).

* Un utente ridimensiona l'oggetto visivo.

    Quando un utente modifica le dimensioni di un oggetto visivo, Power BI chiama il metodo `update` con il nuovo oggetto `options`. Gli oggetti `options` includono gli oggetti `viewport` annidati che contengono i nuovi valori di larghezza e altezza dell'oggetto visivo.

* Un utente applica un filtro a livello di report, pagina oppure oggetto visivo.

    Power BI filtra i dati in base alle condizioni di filtro. Power BI chiama il metodo `update` dell'oggetto visivo per aggiornare l'oggetto visivo con i nuovi dati.

    L'oggetto visivo ottiene un nuovo aggiornamento degli oggetti `options` quando in uno degli oggetti annidati sono presenti nuovi dati. La modalità di aggiornamento dipende dalla configurazione del mapping delle viste dati dell'oggetto visivo.

    Per altre informazioni, vedere [Mapping di viste dati in oggetti visivi di Power BI](dataview-mappings.md).

* Un utente seleziona un punto dati in un altro oggetto visivo del report.

    Quando un utente seleziona un punto dati in un altro oggetto visivo nel report, Power BI filtra o evidenzia i punti dati selezionati e chiama il metodo `update` dell'oggetto visivo. L'oggetto visivo ottiene i nuovi dati filtrati o gli stessi dati con una matrice di evidenziazioni.

    Per altre informazioni,, vedere [Evidenziare i punti dati in oggetti visivi di Power BI](highlight.md).

* Un utente seleziona un segnalibro nel pannello dei segnalibri del report.

    Quando un utente seleziona un segnalibro nel pannello dei segnalibri del report, può verificarsi una delle due azioni seguenti:

    * Power BI chiama una funzione che viene passata e registrata dal metodo `registerOnSelectionCallback`. La funzione di callback ottiene le matrici delle selezioni per il segnalibro corrispondente.

    * Power BI chiama il metodo `update` con un oggetto `filter` corrispondente all'interno dell'oggetto `options`.

    In entrambi i casi l'oggetto visivo deve modificare lo stato in base alle selezioni ricevute o all'oggetto `filter`.

    Per altre informazioni sui segnalibri e sui filtri, vedere [API dei filtri degli oggetti visivi negli oggetti visivi di Power BI](filter-api.md).

### <a name="user-interacts-with-the-visual-directly"></a>L'utente interagisce direttamente con l'oggetto visivo

* Un utente passa il puntatore del mouse su un elemento dati.

    Un oggetto visivo può visualizzare più informazioni su un punto dati tramite l'API delle descrizioni comando di Power BI. Quando un utente passa il puntatore del mouse su un elemento dell'oggetto visivo, l'oggetto visivo può gestire l'evento e visualizzare i dati relativi all'elemento descrizione comando associato. L'oggetto visivo può visualizzare una descrizione comando standard oppure una descrizione comando della pagina del report.

    Per altre informazioni, vedere [Descrizioni comando negli oggetti visivi di Power BI](add-tooltips.md).

* Un utente modifica le proprietà dell'oggetto visivo, ad esempio un utente espande un albero e l'oggetto visivo salva lo stato nelle proprietà dell'oggetto visivo.

    Un oggetto visivo può salvare i valori delle proprietà tramite l'API Power BI. Quando ad esempio un utente interagisce con l'oggetto visivo e l'oggetto visivo deve salvare o aggiornare i valori delle proprietà, l'oggetto visivo può chiamare il metodo `presistProperties`.

* Un utente seleziona un URL.

    Per impostazione predefinita, un oggetto visivo non può aprire direttamente un URL. Per aprire un URL in una nuova scheda, l'oggetto visivo può invece chiamare il metodo `launchUrl` e passare l'URL come parametro.

    Per altre informazioni, vedere [Creare un URL di avvio](launch-url.md).

* Un utente applica un filtro tramite l'oggetto visivo.

    Un oggetto visivo può chiamare il metodo `applyJsonFilter` e passare le condizioni per filtrare i dati in altri oggetti visivi. Sono disponibili diversi tipi di filtri, inclusi i filtri di tipo base, avanzato e tupla.

    Per altre informazioni, vedere [API dei filtri degli oggetti visivi negli oggetti visivi di Power BI](filter-api.md).

* Un utente seleziona gli elementi nell'oggetto visivo.

    Per altre informazioni sulle selezioni in un oggetto visivo di Power BI, vedere [Aggiungere interattività usando le selezioni degli oggetti visivi di Power BI](selection-api.md).

### <a name="visual-interacts-with-power-bi"></a>Un oggetto visivo interagisce con Power BI

* Un oggetto visivo richiede più dati a Power BI.

    Un oggetto visivo elabora una parte dei dati per volta. Il metodo API `fetchMoreData` richiede il frammento successivo dei dati nel set di dati.

    Per altre informazioni, vedere [Recuperare altri dati da Power BI](fetch-more-data.md).

* Viene attivato il servizio eventi.

    Power BI può esportare un report in formato PDF o inviare un report tramite posta elettronica (applicabile solo agli oggetti visivi certificati). Per notificare a Power BI che il rendering è completato e che l'oggetto visivo è pronto per essere acquisito come PDF o messaggio di posta elettronica, l'oggetto visivo deve chiamare l'API per gli eventi di rendering.

    Per altre informazioni, vedere [Esportare report da Power BI in PDF](../../consumer/end-user-pdf.md).

    Per informazioni sul servizio eventi, vedere [Eseguire il rendering degli eventi negli oggetti visivi di Power BI](event-service.md).

## <a name="next-steps"></a>Passaggi successivi

Sono disponibili altre informazioni sulla creazione di visualizzazioni e la relativa aggiunta a Microsoft AppSource. Vedere i seguenti articoli:

* [Sviluppare un oggetto visivo di Power BI](./custom-visual-develop-tutorial.md)
* [Pubblicare oggetti visivi di Power BI nel Centro per i partner](../office-store.md)
