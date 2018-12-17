---
title: Introduzione ai dashboard per le finestre di progettazione di Power BI
description: I dashboard sono una funzionalità chiave del servizio Power BI. I dashboard sono costituiti da una singola pagina, spesso chiamata area di disegno, che offre una narrazione tramite le visualizzazioni.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 7a1187373304387ac511053d241e5cfb31f7fcd9
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280582"
---
# <a name="intro-to-dashboards-for-power-bi-designers"></a>Introduzione ai dashboard per le finestre di progettazione di Power BI

Un ***dashboard*** di Power BI è costituito da una singola pagina, spesso chiamata area di disegno, che offre una narrazione tramite le visualizzazioni. Essendo limitato a una pagina, un dashboard ben progettato contiene solo gli elementi più importanti della narrazione. I lettori possono visualizzare i report correlati per i dettagli.

![dashboard](media/service-dashboards/power-bi-dashboard2.png)

I dashboard sono una funzionalità del servizio Power BI. Non sono disponibili in Power BI Desktop. Non è possibile creare dashboard nei dispositivi mobili, ma è possibile [visualizzarli e condividerli](mobile-apps-view-dashboard.md).

## <a name="dashboard-basics"></a>Nozioni di base sui dashboard 

Le visualizzazioni mostrate nel dashboard sono chiamate *riquadri*. I riquadri vengono *aggiunti* a un dashboard dai report. Se non si ha familiarità con Power BI, è possibile imparare le nozioni di base utili leggendo [Concetti di base di Power BI](service-basic-concepts.md).

> [!IMPORTANT]
> Per creare i dashboard è necessaria una licenza [Power BI Pro](service-free-vs-pro.md).

Le visualizzazioni in un dashboard provengono dai report e ogni report è basato su un set di dati. Un dashboard può essere considerato una via d'accesso ai report e ai set di dati sottostanti. Selezionando una visualizzazione si accede al report e al set di dati su cui è basata.

![Diagramma che illustra la relazione tra dashboard, report e set di dati](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantaggi dei dashboard
I dashboard sono uno strumento molto utile per monitorare l'attività aziendale e visualizzare tutte le metriche più importanti. Le visualizzazioni in un dashboard potrebbero provenire da uno o più set di dati e report sottostanti. Un dashboard combina i dati locali e quelli del cloud, offrendo una visualizzazione consolidata indipendentemente dalla posizione dei dati.

Un dashboard non è solo un bel quadro d'insieme, ma è estremamente interattivo e i riquadri si aggiornano al variare dei dati sottostanti.

## <a name="dashboards-versus-reports"></a>Dashboard e report a confronto
I [report](service-reports.md) e i dashboard appaiono simili poiché sono entrambi aree di disegno contenenti visualizzazioni. Esistono tuttavia alcune importanti differenze.

| **Capacità** | **Dashboard** | **Report** |
| --- | --- | --- |
| Pagine |Una pagina |Una o più pagine |
| Origini dati |Uno o più report e uno o più set di dati per dashboard |Un singolo set di dati per report |
| Disponibile in Power BI Desktop |No | È possibile creare e visualizzare i report in Power BI Desktop |
| Sottoscrivi |È possibile sottoscrivere un dashboard |È possibile sottoscriversi alle pagine del report |
| Applicazione di filtri |Non è possibile filtrare o sezionare |Molti modi diversi di filtrare, evidenziare e sezionare |
| In primo piano |Permette di impostare un dashboard come dashboard "in primo piano" |Non permette di creare un report in primo piano |
| Preferito | È possibile impostare i dashboard come *preferiti* | È possibile impostare i report come *preferiti*
| Impostazione di avvisi |Disponibile per i riquadri del dashboard in determinate circostanze |Non disponibile dai report |
| Query in linguaggio naturale (Domande e risposte) |Disponibili nei dashboard | Disponibili nei report |
| Permette di visualizzare i campi e le tabelle del set di dati sottostante |No. Consente di esportare i dati ma le tabelle e i campi nel dashboard stesso non sono visibili. |Sì. È possibile visualizzare le tabelle, i campi e valori del set di dati. |


## <a name="next-steps"></a>Passaggi successivi
* Per acquisire familiarità con i dashboard, consultare la presentazione di uno dei [dashboard di esempio](sample-tutorial-connect-to-the-samples.md).
* Ottenere informazioni sui [riquadri del dashboard](service-dashboard-tiles.md).
* Si desidera monitorare un singolo riquadro del dashboard e ricevere un'e-mail quando raggiunge una certa soglia? [Creare avvisi sui riquadri](service-set-data-alerts.md).
* Informazioni su come usare lo strumento [Domande e risposte di Power BI](power-bi-tutorial-q-and-a.md) per porre una domanda sui dati e ottenere una risposta sotto forma di visualizzazione.
