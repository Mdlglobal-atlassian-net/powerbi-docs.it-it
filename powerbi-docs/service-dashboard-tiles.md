---
title: Introduzione ai riquadri del dashboard per le finestre di progettazione di Power BI
description: Questo articolo descrive i riquadri del dashboard in Power BI, inclusi i riquadri creati dai report di SQL Server Reporting Services (SSRS).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 4577ca5d12002e18406b66036244d895fa7ee5fd
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68994858"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introduzione ai riquadri del dashboard per le finestre di progettazione di Power BI

Un riquadro è uno snapshot dei dati, aggiunto al dashboard. È possibile creare un riquadro da un report, da un set di dati, da un dashboard, dalla casella Domande e risposte, da Excel, dai report di SQL Server Reporting Services (SSRS) e da altre origini.  Questo screenshot mostra numerosi riquadri diversi aggiunti a un dashboard.

![Dashboard di Power BI](media/service-dashboard-tiles/power-bi-dashboard.png)

I dashboard e i riquadri del dashboard sono una funzionalità del servizio Power BI, non di Power BI Desktop. Non è possibile creare dashboard nei dispositivi mobili, ma è possibile [visualizzarli e condividerli](mobile-apps-view-dashboard.md).

Oltre ad aggiungere riquadri, è possibile creare riquadri autonomi direttamente nel dashboard usando il controllo [Aggiungi riquadro](service-dashboard-add-widget.md). I riquadri autonomi includono caselle di testo, immagini, video, streaming di dati e contenuto Web.

Per saperne di più sui componenti essenziali di Power BI, Vedere [Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md).

> [!NOTE]
> Se la visualizzazione originale usata per creare il riquadro viene modificata, il riquadro non cambia.  Ad esempio, se è stato aggiunto un grafico a linee da un report che è stato modificato successivamente in un grafico a barre, il riquadro del dashboard continua a mostrare un grafico a linee. I dati vengono aggiornati ma il tipo di visualizzazione rimane uguale.
> 
> 

## <a name="pin-a-tile"></a>Aggiungere un riquadro
Per aggiungere un riquadro a un dashboard si può procedere in diversi modi. È possibile aggiungere riquadri da:

* [Domande e risposte di Power BI](service-dashboard-pin-tile-from-q-and-a.md)
* [Un report](service-dashboard-pin-tile-from-report.md)
* [un altro dashboard](service-pin-tile-to-another-dashboard.md)
* [Cartella di lavoro di Excel in OneDrive for Business](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher per Excel](publisher-for-excel.md)
* [Quick Insights (Informazioni rapide)](service-insights.md)
* [Un report impaginato locale in Server di report di Power BI o in SQL Server Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Per creare riquadri autonomi per immagini, caselle di testo, video, dati in streaming e contenuto Web direttamente nel dashboard, usare il controllo [Aggiungi riquadro](service-dashboard-add-widget.md).

  ![Icona Aggiungi riquadro](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>Interagire con i riquadri in un dashboard
Dopo aver aggiunto un riquadro a un dashboard, è possibile spostarlo e ridimensionarlo oppure modificarne l'aspetto e il comportamento.

### <a name="move-and-resize-a-tile"></a>Spostare e ridimensionare un riquadro
[Spostare un riquadro nel dashboard](service-dashboard-edit-tile.md) trascinandolo. Passare il puntatore e selezionare il quadratino ![Quadratino del riquadro](media/service-dashboard-tiles/resize-handle.jpg) per ridimensionare il riquadro.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Passare il puntatore del mouse su un riquadro per modificarne l'aspetto e il comportamento
1. Passare il puntatore del mouse sul riquadro per visualizzare i puntini di sospensione.
   
    ![Riquadro con puntini di sospensione](media/service-dashboard-tiles/ellipses_new.png)
2. Selezionare i puntini di sospensione per aprire il menu Azione per il riquadro.
   
    ![Icona dei puntini di sospensione](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Da qui è possibile:
   
     * [Aggiungere commenti al dashboard](consumer/end-user-comment.md).
     * [Aprire il report usato per creare questo riquadro](service-reports.md).  
     * [Visualizzare il riquadro nella modalità messa a fuoco](service-focus-mode.md).   
     * [Esportare i dati usati nel riquadro](visuals/power-bi-visualization-export-data.md).
     * [Modificare il riquadro e il sottotitolo e aggiungere un collegamento ipertestuale](service-dashboard-edit-tile.md). 
     * [Eseguire analisi su informazioni dettagliate](service-insights.md). 
     * [Aggiungere il riquadro a un altro dashboard](service-pin-tile-to-another-dashboard.md).
     * [Eliminare il riquadro](service-dashboard-edit-tile.md).

3. Per chiudere il menu delle azioni, selezionare un'area vuota nel dashboard.

### <a name="select-a-tile"></a>Selezionare un riquadro
Quando si seleziona un riquadro, gli elementi visualizzati dipendono da come è stato creato il riquadro. In caso contrario, selezionando il riquadro si viene reindirizzati al report, alla cartella di lavoro di Excel Online, al report di Reporting Services locale o alla domanda di Domande e risposte usata per creare il riquadro. Se invece è presente un [collegamento personalizzato](service-dashboard-edit-tile.md), selezionando il riquadro si viene reindirizzati a tale collegamento.

> [!NOTE]
> Fanno eccezione i riquadri video creati direttamente nel dashboard usando **Aggiungi riquadro**. Se si seleziona un riquadro video creato in questo modo, il video viene riprodotto direttamente nel dashboard.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

* Se il report usato per creare la visualizzazione non è stato salvato, selezionando il riquadro non viene eseguita alcuna azione.
* Se il riquadro è stato creato da una cartella di lavoro in Excel Online, è necessario avere almeno le autorizzazioni di lettura per la cartella di lavoro. In caso contrario, se si seleziona il riquadro non verrà aperta la cartella di lavoro in Excel Online.
* Si supponga di creare un riquadro direttamente nel dashboard usando **Aggiungi riquadro** e di impostare un collegamento ipertestuale personalizzato per il riquadro. In questo caso la selezione del titolo, del sottotitolo o del riquadro apre l'URL. In caso contrario, per impostazione predefinita, quando si seleziona un riquadro creato direttamente nel dashboard per un'immagine, un codice Web o una casella di testo, non viene eseguita alcuna operazione.
* I riquadri possono essere creati da report impaginati locali in Server di report di Power BI o in SQL Server Reporting Services. Se non si è autorizzati ad accedere al report locale, selezionando il riquadro si viene reindirizzati a una pagina indicante che non si ha accesso (rsAccessDenied).
* Si supponga di selezionare un riquadro creato da un report impaginato locale in Server di report di Power BI o in SQL Server Reporting Services. Se non si ha accesso alla rete in cui si trova il server di report, selezionando un riquadro creato da tale report impaginato si viene reindirizzati a una pagina indicante che non è possibile individuare il server (HTTP 404). Il dispositivo deve avere accesso al server di report per visualizzare il report.
* Se la visualizzazione originale usata per creare il riquadro viene modificata, il riquadro non cambia. Ad esempio, se è stato aggiunto un grafico a linee da un report e successivamente si modifica il grafico in un grafico a barre, il riquadro del dashboard continuerà a visualizzare un grafico a linee. I dati vengono aggiornati, ma il tipo di visualizzazione rimane uguale.

## <a name="next-steps"></a>Passaggi successivi
- [Creare una scheda (riquadro per numeri elevati) per il dashboard](power-bi-visualization-card.md)
- [Introduzione ai dashboard di Power BI per i progettisti](service-dashboards.md)  
- [Aggiornamento dei dati in Power BI](refresh-data.md)
- [Concetti di base del servizio Power BI](service-basic-concepts.md)
- [Integrating Power BI tiles into Office documents (Integrazione dei riquadri di Power BI nei documenti di Office)](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)
- [Aggiungere elementi di Reporting Services ai dashboard di Power BI](https://msdn.microsoft.com/library/mt604784.aspx)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/).

