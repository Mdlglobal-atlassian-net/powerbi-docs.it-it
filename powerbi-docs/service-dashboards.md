---
title: Che cos'è un dashboard per i consumer del servizio Power BI?
description: I dashboard sono una funzionalità chiave del servizio Power BI.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/02/2018
ms.author: maggie
LocalizationGroup: Dashboards
ms.openlocfilehash: 6be3d095ca68cf83ff7a2ba4c7fd02a9340f3474
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48908441"
---
# <a name="dashboards-in-power-bi-service"></a>Dashboard nel servizio Power BI

Un ***dashboard*** Power BI è una singola pagina, spesso denominata area di disegno, che usa le visualizzazioni per raccontare una storia. Essendo limitato a una pagina, un dashboard ben progettato contiene solo gli elementi più importanti per tale storia.

![dashboard](media/service-dashboards/power-bi-dashboard2.png)

I dashboard sono una funzionalità del servizio Power BI e non sono disponibili in Power BI Desktop. Sui dispositivi mobili i dashboard non possono essere creati, ma solo [visualizzati e condivisi](mobile-apps-view-dashboard.md).

## <a name="dashboard-creators-and-dashboard-consumers"></a>Autori dei dashboard e utenti dei dashboard
In base al ruolo, si potrebbe essere un utente che crea i dashboard per uso personale o da condividere con i colleghi. Le informazioni per l'utente sono reperibili nella sezione sui **dashboard per gli autori**. Oppure l'utente riceve i dashboard da altri utenti. Si desidera imparare a comprendere e interagire con il dashboard. Questo articolo può essere utile.


### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Se si intende ricevere e usare i dashboard

Le visualizzazioni che appaiono sul dashboard sono dette *riquadri* e vengono *aggiunte* al dashboard dai report dagli *autori* del dashboard. Se non si ha familiarità con Power BI, è possibile imparare le nozioni di base utili leggendo [Concetti di base di Power BI](service-basic-concepts.md).

> [!IMPORTANT]
> [Power BI Pro](service-free-vs-pro.md) è necessario per visualizzare un dashboard condiviso.

Le visualizzazioni in un dashboard provengono dai report e ogni report è basato su un set di dati. Infatti, un dashboard può essere inteso come una via d'accesso ai report e ai set di dati sottostanti. Selezionando una visualizzazione si accede al report (e al set di dati) usato per crearla.

![Diagramma che illustra la relazione tra dashboard, report e set di dati](media/service-dashboards/power-bi-diagram.png)



## <a name="advantages-of-dashboards"></a>Vantaggi dei dashboard
I dashboard sono uno strumento eccezionale per monitorare l'attività aziendale, per cercare le risposte e per esaminare tutte le metriche più importanti al primo colpo. Le visualizzazioni in un dashboard potrebbero provenire da uno o più set di dati e report sottostanti. Un dashboard combina i dati locali e quelli generati dal cloud, offrendo una visualizzazione consolidata indipendentemente da dove si trovano i dati.

Un dashboard non è solo un'immagine accattivante: è estremamente interattivo e i riquadri si aggiornano al variare dei dati sottostanti.

## <a name="dashboards-versus-reports"></a>Dashboard e report a confronto
I [report](service-reports.md) sono spesso confusi con i dashboard poiché sono composti da troppe aree di contenuto con le visualizzazioni. Tuttavia, ci sono alcune importanti differenze per i consumer di Power BI.

| **Capacità** | **Dashboard** | **Report** |
| --- | --- | --- |
| Pagine |Una pagina |Una o più pagine |
| Origini dati |Uno o più report e uno o più set di dati per dashboard |Un singolo set di dati per report |
| Disponibile in Power BI Desktop |No |Sì, gli ***autori*** possono creare e visualizzare i report in Desktop |
| Sottoscrivi |È possibile sottoscrivere un dashboard |È possibile sottoscriversi alle pagine del report |
| Applicazione di filtri |Non è possibile filtrare o sezionare |Molti modi diversi di filtrare, evidenziare e sezionare |
| In primo piano |Permette di impostare un dashboard come dashboard "in primo piano" |Non permette di creare un report in primo piano |
| Preferito | È possibile impostare i dashboard come *preferiti* | È possibile impostare i report come *preferiti*
| Impostazione di avvisi |Disponibile per i riquadri del dashboard in determinate circostanze |Non disponibile dai report |
| Query in linguaggio naturale |Disponibile dal dashboard |Non disponibile dai report |
| Permette di visualizzare i campi e le tabelle del set di dati sottostante |No. Consente di esportare i dati ma le tabelle e i campi nel dashboard stesso non sono visibili. |Sì. È possibile visualizzare le tabelle, i campi e valori del set di dati. |
| Customization |No |Nella visualizzazione di lettura è possibile pubblicare, incorporare, filtrare, esportare, scaricare come file PBIX, visualizzare il contenuto correlato, generare codici QR, analizzare in Excel e altro ancora.  |

## <a name="next-steps"></a>Passaggi successivi
* Per acquisire familiarità con i dashboard, consultare la presentazione di uno dei [dashboard di esempio](sample-tutorial-connect-to-the-samples.md).
* Informazioni sui [riquadri del dashboard](service-dashboard-tiles.md) e cosa succede quando se ne seleziona uno.
* Si desidera monitorare un singolo riquadro del dashboard e ricevere un'e-mail quando raggiunge una certa soglia? [Creare avvisi sui riquadri](service-set-data-alerts.md).
* È possibile porre liberamente le domande al dashboard. Informazioni su come usare lo strumento [Domande e risposte di Power BI](power-bi-tutorial-q-and-a.md) per porre una domanda sui dati e ottenere una risposta sotto forma di visualizzazione.
