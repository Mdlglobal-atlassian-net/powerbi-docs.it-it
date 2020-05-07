---
title: Estendere gli oggetti visivi con descrizioni comando per le pagine dei report
description: Linee guida per l'utilizzo delle descrizioni comando per le pagine dei report.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 5a6b7bda8bf5e8d80ae8b22a71035f8bc362fb89
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377743"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Estendere gli oggetti visivi con descrizioni comando per le pagine dei report

Questo articolo è destinato ai progettisti di report di Power BI. Fornisce suggerimenti e consigli per la creazione di [descrizioni comando basate sulle pagine del report](../desktop-tooltips.md).

## <a name="suggestions"></a>Suggerimenti

Le descrizioni comando delle pagine del report possono migliorare l'esperienza degli utenti del report. Le descrizioni comando delle pagine consentono agli utenti del report di ottenere informazioni approfondite in modo rapido ed efficiente da un oggetto visivo. Possono essere associate a oggetti del report diversi:

- **Oggetti visivi:** è possibile configurare quali oggetti visivi mostreranno la descrizione comando della pagina. È possibile fare in modo che ogni singolo oggetto visivo non mostri descrizioni comando, che mostri le descrizioni comando degli oggetti visivi (configurate nel riquadro dei campi degli oggetti visivi) per impostazione predefinita o che usi una specifica descrizione comando della pagina.
- **Intestazioni dell'oggetto visivo:** è possibile configurare oggetti visivi specifici in modo che visualizzino una descrizione comando della pagina. Gli utenti del report possono visualizzare la descrizione comando della pagina quando passano il cursore sull'icona dell'intestazione dell'oggetto visivo. Assicurarsi quindi che gli utenti siano informati di questa icona.

> [!NOTE]
> Un oggetto visivo del report può mostrare una descrizione comando della pagina solo quando i filtri della pagina della descrizione comando sono compatibili con la progettazione dell'oggetto visivo. Ad esempio, un oggetto visivo che crea un raggruppamento per _prodotto_ è compatibile con una pagina di descrizione comando che applica un filtro per _prodotto_.
>
> Le descrizioni comando delle pagine non supportano l'interattività. Se si vuole che gli utenti del report interagiscano, creare invece una [pagina drill-through](../desktop-drillthrough.md).
>
> Gli oggetti visivi di Power BI non supportano le descrizioni comando delle pagine.

Ecco alcuni scenari di progettazione consigliati:

- [Punto di vista diverso](#different-perspective)
- [Aggiungere un dettaglio](#add-detail)
- [Aggiungere il contenuto della Guida](#add-help)

### <a name="different-perspective"></a>Punto di vista diverso

Una descrizione comando di pagina può visualizzare gli stessi dati dell'oggetto visivo di origine. È possibile usare lo stesso oggetto visivo e trasformare i gruppi tramite Pivot oppure usare tipi di oggetti visivi diversi. Le descrizioni comando della pagina possono anche applicare filtri diversi da quelli applicati all'oggetto visivo di origine.

L'esempio seguente illustra che cosa accade quando l'utente del report passa il cursore sul valore **EnabledUsers**. Il contesto del filtro per il valore è Yammer a novembre 2018.

![Un oggetto visivo matrice visualizza una griglia di valori raggruppati nelle righe per anno e mese. Un utente del report ha passato il cursore su un singolo valore. È apparsa una descrizione comando della pagina.](media/report-page-tooltips/suggestion-different-perspective.png)

Viene mostrata una descrizione comando della pagina che presenta un oggetto visivo dati diverso (grafico a linee e istogramma a colonne raggruppate) e applica un filtro temporale a differente. Si noti che il contesto del filtro per il punto dati è novembre 2018, ma la descrizione comando della pagina visualizza la tendenza per _dodici interi mesi_.

### <a name="add-detail"></a>Aggiungere un dettaglio

Una descrizione comando della pagina può visualizzare altri dettagli e aggiungere il contesto.

L'esempio seguente illustra che cosa accade quando l'utente del report passa il cursore sul valore **Average of Violation Points** per il codice postale 98022.

![Un oggetto visivo tabella visualizza una griglia di valori e la tabella contiene tre colonne. È apparsa una descrizione comando della pagina.](media/report-page-tooltips/suggestion-add-details.png)

Viene mostrata una descrizione comando della pagina che presenta statistiche e attributi specifici del codice postale 98022.

### <a name="add-help"></a>Aggiungere il contenuto della Guida

Le intestazioni degli oggetti visivi possono essere configurate per mostrare le descrizioni comando della pagina per le intestazioni degli oggetti visivi. È possibile aggiungere la documentazione della Guida a una descrizione comando della pagina usando caselle di testo con formattazione RTF. È anche possibile aggiungere immagini e forme.

È interessante notare che pulsanti, immagini, caselle di testo e forme possono anche mostrare una descrizione comando di pagina per l'intestazione di un oggetto visivo.

L'esempio seguente illustra che cosa accade quando l'utente del report passa il cursore sull'[icona dell'intestazione dell'oggetto visivo](../desktop-visual-elements-for-reports.md).

![Un utente del report ha passato il cursore sull'icona dell'intestazione di un oggetto visivo (icona del punto interrogativo). È apparsa una descrizione comando con formattazione RTF.](media/report-page-tooltips/suggestion-add-help.png)

Viene mostrata una descrizione comando della pagina Presenta il testo con formattazione RTF in quattro caselle di testo e una forma (riga). La descrizione comando di pagina fornisce informazioni che descrivono ogni acronimo visualizzato nell'oggetto visivo.

## <a name="recommendations"></a>Consigli

In fase di progettazione del report, è consigliabile seguire queste procedure:

- **Dimensioni pagina:** configurare una descrizione comando della pagina di piccole dimensioni. È possibile usare l'opzione **Descrizione comando** predefinita (320 pixel di larghezza e 240 pixel di altezza) o impostare dimensioni personalizzate. Cercare di non usare dimensioni della pagina troppo grandi perché possono nascondere gli oggetti visivi nella pagina di origine.
- **Visualizzazione pagina:** in Progettazione report impostare la visualizzazione della pagina su **Dimensioni effettive**. La visualizzazione predefinita della pagina è **Adatta alla pagina**. In questo modo è possibile vedere le dimensioni effettive della descrizione comando della pagina mentre la si progetta.
- **Stile:** provare a progettare la descrizione comando della pagina in modo da usare lo stesso tema e lo stesso stile del report. In questo modo, agli utenti sembrerà di essere nello stesso report. In alternativa, progettare uno stile complementare per le descrizioni comando e assicurarsi di applicare questo stile a tutte le descrizioni comando della pagina.
- **Filtri della descrizione comando:** assegnare filtri alla descrizione comando della pagina in modo da visualizzare un'anteprima realistica del risultato già durante la progettazione. Assicurarsi di rimuovere questi filtri prima di pubblicare il report.
- **Visibilità della pagina:** nascondere sempre le pagine di descrizione comando perché gli utenti non devono passare direttamente a queste pagine.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Creare descrizioni comando basate sulle pagine del report in Power BI Desktop](../desktop-tooltips.md)
- [Personalizzazione delle descrizioni comando in Power BI Desktop](../desktop-custom-tooltips.md)
- [Usare gli elementi visivi per migliorare i report di Power BI](../desktop-visual-elements-for-reports.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
