---
title: Usare il drill-through nelle pagine dei report
description: Linee guida per l'uso del drill-through nelle pagine dei report.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: 853f6d7f5cd6696be55edeea101bc0ca51922ad3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278078"
---
# <a name="use-report-page-drillthrough"></a>Usare il drill-through nelle pagine dei report

Questo articolo è destinato agli autori di report che progettano report di Power BI. Fornisce suggerimenti e consigli per la creazione di funzionalità di [drill-through nelle pagine dei report](../create-reports/desktop-drillthrough.md).

È consigliabile progettare il report in modo da consentire agli utenti dei report di ottenere il flusso seguente:

1. Visualizzare una pagina del report.
2. Identificare un elemento visivo da analizzare più a fondo.
3. Fare clic con il pulsante destro del mouse sull'elemento visivo per eseguire il drill-through.
4. Eseguire analisi complementari.
5. Tornare alla pagina del report di origine.

## <a name="suggestions"></a>Suggerimenti

Si consiglia di considerare due tipi di scenari di drill-through:

- [Approfondimento](#additional-depth)
- [Prospettiva più ampia](#broader-perspective)

### <a name="additional-depth"></a>Approfondimento

Quando nella pagina del report vengono visualizzati risultati riepilogati, una pagina di drill-through può condurre gli utenti del report ai dettagli a livello di transazione. Questo approccio di progettazione consente loro di visualizzare le transazioni di supporto e solo quando necessario.

Nell'esempio seguente viene illustrato cosa accade quando un utente del report esegue il drill-through da un riepilogo delle vendite mensili. La pagina di drill-through contiene un elenco dettagliato degli ordini per un mese specifico.

![Un oggetto visivo matrice denominato "Sales Summary" raggruppa le vendite in base ad anno e mese per le righe e in base al paese per le colonne. Viene visualizzata anche una pagina di drill-through.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Prospettiva più ampia

Una pagina di drill-through può offrire l'opposto dell'approfondimento. Questo scenario è utile per eseguire il drill-through in una visualizzazione olistica.

Nell'esempio seguente viene illustrato cosa accade quando un utente del report esegue il drill-through da un codice postale. Nella pagina di drill-through vengono visualizzate informazioni generali sul codice postale.

![In un oggetto visivo tabella sono presenti tre colonne: Zip Code, Average of Violation Points e Average of Grade Rating. Viene visualizzata anche la pagina di drill-through.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Consigli

In fase di progettazione del report, è consigliabile seguire queste procedure:

- **Stile:** provare a progettare la pagina di drill-through in modo da usare lo stesso tema e lo stesso stile del report. In questo modo, agli utenti sembrerà di essere nello stesso report.
- **Filtri di drill-through:** impostare i filtri di drill-through in modo da poter visualizzare in anteprima un risultato realistico durante la progettazione della pagina di drill-through. Assicurarsi di rimuovere questi filtri prima di pubblicare il report.
- **Funzionalità aggiuntive:** una pagina di drill-through è come una pagina qualsiasi del report. È anche possibile migliorarla con funzionalità interattive aggiuntive, inclusi filtri dei dati o filtri.
- **Valori BLANK:** evitare di aggiungere oggetti visivi che potrebbero visualizzare valori BLANK o produrre errori quando vengono applicati i filtri di drill-through.
- **Visibilità della pagina:** considerare la possibilità di nascondere le pagine di drill-through. Se si decide di mantenere visibile una pagina di drill-through, assicurarsi di aggiungere un pulsante che consenta agli utenti di cancellare tutti i filtri di drill-through impostati in precedenza. Assegnare un [segnalibro](../create-reports/desktop-bookmarks.md) al pulsante. Il segnalibro deve essere configurato per rimuovere tutti i filtri.
- **Pulsante Indietro:** un [pulsante](../create-reports/desktop-buttons.md) Indietro viene aggiunto automaticamente quando si assegna un filtro di drill-through. È consigliabile mantenerlo. In questo modo, gli utenti del report possono tornare facilmente alla pagina di origine.
- **Individuazione:** contribuire a promuovere la conoscenza di una pagina di drill-through impostando il testo dell'icona dell'intestazione dell'oggetto visivo o aggiungendo istruzioni in una casella di testo. È anche possibile progettare una sovrimpressione, come descritto in [questo post di blog](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> È anche possibile configurare il drill-through per i report impaginati di Power BI. Questa operazione può essere eseguita aggiungendo collegamenti ai report di Power BI. I collegamenti possono definire [parametri URL](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Usare il drill-through in Power BI Desktop](../create-reports/desktop-drillthrough.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
