---
title: Introduzione ai dashboard per le finestre di progettazione di Power BI
description: I dashboard sono una funzionalità chiave del servizio Power BI. I dashboard sono costituiti da una singola pagina, spesso chiamata area di disegno, che offre una narrazione tramite le visualizzazioni.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 7ee083de9800b55c4f7d998a113c1a63df112b7b
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68624034"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Introduzione ai dashboard di Power BI per i progettisti

Un *dashboard* di Power BI è costituito da una singola pagina, spesso chiamata area di disegno, che offre una narrazione tramite le visualizzazioni. Essendo limitato a una pagina, un dashboard ben progettato contiene solo gli elementi più importanti della narrazione. I lettori possono visualizzare i report correlati per i dettagli.

![Dashboard](media/service-dashboards/power-bi-dashboard2.png)

I dashboard sono una funzionalità solo del servizio Power BI. Non sono disponibili in Power BI Desktop. Non è possibile creare dashboard nei dispositivi mobili, ma è possibile [visualizzarli e condividerli](mobile-apps-view-dashboard.md) in tali dispositivi.

## <a name="dashboard-basics"></a>Nozioni di base sui dashboard 

Le visualizzazioni mostrate nel dashboard sono chiamate *riquadri*. I riquadri vengono *aggiunti* a un dashboard dai report. Se non si ha familiarità con Power BI, è possibile apprendere le nozioni di base utili leggendo [Basic concepts for designers in the Power BI service](service-basic-concepts.md) (Concetti di base sul servizio Power BI per i progettisti).

> [!IMPORTANT]
> Per creare i dashboard è necessaria una licenza [Power BI Pro](service-free-vs-pro.md).

Le visualizzazioni in un dashboard provengono da report e ogni report è basato su un set di dati. Un dashboard può essere considerato una via d'accesso ai report e ai set di dati sottostanti. Selezionando una visualizzazione si accede al report e al set di dati su cui è basata.

![Diagramma che illustra la relazione tra dashboard, report e set di dati](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantaggi dei dashboard
I dashboard sono uno strumento molto utile per monitorare l'attività aziendale e visualizzare tutte le metriche più importanti. Le visualizzazioni in un dashboard possono provenire da uno o più set di dati e uno o più report sottostanti. Un dashboard combina i dati locali e quelli del cloud, offrendo una visualizzazione consolidata indipendentemente dalla posizione dei dati.

Un dashboard non è solo un bel quadro d'insieme, ma è estremamente interattivo e i riquadri si aggiornano al variare dei dati sottostanti.

## <a name="dashboards-versus-reports"></a>Dashboard e report a confronto
I [report](service-reports.md) e i dashboard appaiono simili poiché sono entrambi aree di disegno contenenti visualizzazioni. Esistono tuttavia alcune differenze principali, come si può notare nella tabella seguente.

| **Capacità** | **Dashboard** | **Report** |
| --- | --- | --- |
| Pagine |Una pagina |Una o più pagine |
| Origini dati |Uno o più report e uno o più set di dati per dashboard |Un singolo set di dati per report |
| Disponibile in Power BI Desktop |No | Sì. È possibile creare e visualizzare i report in Power BI Desktop |
| Sottoscrivi |Sì. È possibile sottoscrivere un dashboard |Sì. È possibile sottoscrivere una pagina di un report |
| Applicazione di filtri |No. Non è possibile filtrare o sezionare |Sì. Molti modi diversi di filtrare, evidenziare e sezionare |
| In primo piano |Sì. È possibile impostare un dashboard come *in primo piano* |No |
| Preferito | Sì. È possibile impostare più dashboard come *preferiti* | Sì. È possibile impostare più report come *preferiti*
| Impostazione di avvisi |Sì. Disponibile per i riquadri del dashboard in determinate circostanze |No |
| Query in linguaggio naturale (Domande e risposte) |Sì | Sì, purché si disponga delle autorizzazioni di modifica per il report e per il set di dati sottostante |
| Permette di visualizzare i campi e le tabelle del set di dati sottostante |No. È possibile esportare i dati, ma le tabelle e i campi nel dashboard stesso non sono visibili. |Sì |


## <a name="next-steps"></a>Passaggi successivi
* Per acquisire familiarità con i dashboard, consultare la presentazione di uno dei [dashboard di esempio](sample-tutorial-connect-to-the-samples.md).
* Ottenere informazioni sui [riquadri del dashboard](service-dashboard-tiles.md).
* Si desidera monitorare un singolo riquadro del dashboard e ricevere un'e-mail quando raggiunge una certa soglia? [Creare un avviso in un riquadro](service-set-data-alerts.md).
* Informazioni su come usare lo strumento [Domande e risposte di Power BI](power-bi-tutorial-q-and-a.md) per porre una domanda sui dati e ottenere una risposta sotto forma di visualizzazione.
