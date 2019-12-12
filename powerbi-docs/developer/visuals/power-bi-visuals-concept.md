---
title: Concetto di oggetto visivo in Power BI
description: L'articolo descrive come un oggetto visivo si integra con Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700847"
---
# <a name="power-bi-visual-concept"></a>Concetto di oggetto visivo in Power BI

Questo articolo illustra come un utente e un oggetto visivo interagiscono con Power BI e come un utente interagisce con l'oggetto visivo di Power BI. Nel diagramma sono visualizzate le azioni che influenzano l'oggetto visivo direttamente o tramite Power BI (ad esempio, quando l'utente seleziona i segnalibri).

![Oggetto visivo di Power BI](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>L'oggetto visivo ottiene l'aggiornamento da Power BI

L'oggetto visivo ha il metodo `update` che in genere contiene la logica principale dell'oggetto visivo ed è responsabile del rendering del grafico o della visualizzazione dei dati.

Il metodo `update` viene chiamato in più aggiornamenti.

### <a name="user-interacts-with-visual-through-power-bi"></a>L'utente interagisce con l'oggetto visivo tramite Power BI

* L'utente apre il pannello delle proprietà degli oggetti visivi.

    Power BI recupera gli oggetti e le proprietà supportati dall'oggetto visivo `capabilities.json` e, per ricevere i valori effettivi delle proprietà, Power BI chiama il metodo `enumerateObjectInstances` dell'oggetto visivo.

    L'oggetto visivo deve restituire i valori effettivi delle proprietà.

    Per altre informazioni, vedere [Funzionalità e proprietà degli oggetti visivi di Power BI](capabilities.md).

* L'[utente modifica la proprietà dell'oggetto visivo](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) nel pannello di formattazione.

    Dopo la modifica del valore di una proprietà, Power BI chiama il metodo `update` dell'oggetto visivo e passa nel metodo update il nuovo elemento `options` con i nuovi valori degli oggetti.

    Per altre informazioni, vedere [Oggetti e proprietà degli oggetti visivi di Power BI](objects-properties.md).

* L'utente ridimensiona l'oggetto visivo.

    Quando un utente modifica una dimensione dell'oggetto visivo, Power BI chiama il metodo `update` con il nuovo oggetto `option`. Le opzioni hanno un oggetto `viewport` annidato con la nuova larghezza e altezza dell'oggetto visivo.

* L'utente applica un filtro a livello di report, pagina o oggetto visivo.

    Power BI filtra i dati in base alle condizioni del filtro e chiama il metodo `update` dell'oggetto visivo per fornire i nuovi dati all'oggetto visivo.

    L'oggetto visivo ottiene il nuovo aggiornamento di `options` con nuovi dati in uno degli oggetti annidati. Dipende dalla configurazione del mapping di viste dati dell'oggetto visivo.

    Per altre informazioni, vedere [Informazioni sul mapping di viste dati in oggetti visivi di Power BI](dataview-mappings.md).

* L'utente seleziona un punto dati in un altro oggetto visivo del report.

    Power BI filtra o evidenzia i punti dati selezionati e chiama il metodo `update` dell'oggetto visivo.

    L'oggetto visivo ottiene i nuovi dati filtrati o gli stessi dati con la matrice di evidenziazioni.

    Per altre informazioni, vedere [Evidenziare i punti dati in oggetti visivi di Power BI](highlight.md).

* L'utente seleziona il segnalibro nel pannello dei segnalibri del report.

    Possono verificarsi due azioni:

    1. Power BI chiama la funzione passata registrata dal metodo `registerOnSelectionCallback` e la funzione di callback ottiene le matrici di selezioni per il segnalibro corrispondente.

    2. Power BI chiama il metodo `update` con l'oggetto per il filtro corrispondente all'interno di `options`.

    In entrambi i casi, l'oggetto visivo deve modificare lo stato della visualizzazione in base alle selezioni ricevute o all'oggetto per il filtro.

    Per altre informazioni dettagliate sui segnalibri, vedere [API dei filtri degli oggetti visivi negli oggetti visivi di Power BI](filter-api.md).

    Per altre informazioni sui filtri, vedere [API dei filtri degli oggetti visivi negli oggetti visivi di Power BI](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>L'utente interagisce direttamente con l'oggetto visivo

* L'utente passa il mouse sull'elemento dati

    L'oggetto visivo può visualizzare informazioni aggiuntive sul punto dati tramite l'API delle descrizioni comando di Power BI.
    Quando l'utente passa il mouse sull'elemento visivo, l'oggetto visivo può gestire l'evento e visualizzare i dati sull'elemento della descrizione comando.

    L'oggetto visivo può visualizzare la descrizione comando standard o la descrizione comando della pagina del report.

    Per altre informazioni, vedere la guida [Come aggiungere descrizioni comando](add-tooltips.md).

* L'utente modifica le proprietà dell'oggetto visivo, ad esempio espande l'albero e l'oggetto visivo salva lo stato nelle proprietà

    L'oggetto visivo può salvare i valori delle proprietà tramite l'API Power BI. Ad esempio, quando l'utente interagisce con l'oggetto visivo e l'oggetto visivo deve salvare o aggiornare i valori delle proprietà, l'oggetto visivo può chiamare il metodo `presistProperties`.

* L'utente fa clic sul collegamento URL.

    Per impostazione predefinita, l'oggetto visivo non può aprire l'URL. Per aprire l'URL nella nuova scheda, l'oggetto visivo deve chiamare il metodo `launchURL` e passare l'URL come parametro.

    Per altre informazioni, vedere [Creare un URL di avvio](launch-url.md).

* L'utente applica il filtro tramite l'oggetto visivo

    L'oggetto visivo chiama `applyJSONFilter` e passa le condizioni del filtro per filtrare i dati in altri oggetti visivi.

    L'oggetto visivo può usare diversi tipi di filtro, ad esempio un filtro di base, un filtro avanzato, un filtro di tuple.

    Per altre informazioni sui filtri, vedere [API dei filtri degli oggetti visivi negli oggetti visivi di Power BI](filter-api.md).

* L'utente fa clic o seleziona gli elementi nell'oggetto visivo.

    Per altre informazioni sulle selezioni, vedere [Aggiungere interattività negli oggetti visivi tramite le selezioni degli oggetti visivi di Power BI](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>L'oggetto visivo interagisce con Power BI

* L'oggetto visivo richiede altri dati a Power BI.

    L'oggetto visivo può elaborare una parte dei dati alla volta. Il metodo dell'API FetchMoreData richiede il frammento successivo del set di dati.

    Per altre informazioni su `fetchMoreData`, vedere [Recuperare altri dati da Power BI](fetch-more-data.md)

* Servizio eventi

    Power BI può esportare i report in formato PDF o inviarli tramite posta elettronica. Sono supportati solo gli oggetti visivi certificati. Per notificare a Power BI che il rendering è stato completato ed è pronto per l'acquisizione di PDF/posta elettronica, l'oggetto visivo deve chiamare l'API per gli eventi di rendering.

    Per altre informazioni, vedere [Esportare report da Power BI in PDF](../../consumer/end-user-pdf.md)

    Vedere anche altre [informazioni sul servizio eventi](event-service.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori Web interessati a creare visualizzazioni personalizzate e ad aggiungerle in AppSource, possono Vedere [Sviluppo di un oggetto visivo di Power BI](./custom-visual-develop-tutorial.md) e le informazioni su come [pubblicare oggetti visivi di Power BI in AppSource](../office-store.md).
