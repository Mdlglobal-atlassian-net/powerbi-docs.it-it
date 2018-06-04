---
title: Visualizzazione di lettura e Visualizzazione di modifica dei report nel servizio Power BI
description: Informazioni generali sulle differenze tra la Visualizzazione di lettura e la Visualizzazione di modifica per il report del servizio Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: eacadb04935dd0c929a85904335b613f3d5d4d58
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34251668"
---
# <a name="reading-view-and-editing-view-in-power-bi-service-reports"></a>Visualizzazione di lettura e Visualizzazione di modifica nel servizio Power BI
Nel servizio Power BI (ma non in Power BI Desktop) sono disponibili due modalità per visualizzare e interagire con i report: la Visualizzazione di lettura e la Visualizzazione di modifica. La visualizzazione di lettura è disponibile per tutti gli utenti ed è stata progettata in modo specifico per i *consumer* di dati, mentre la visualizzazione di modifica è disponibile solo per gli *autori* e i proprietari dei report.

![Immagine di creatori di report e fruitori di report](media/service-reading-view-and-editing-view/power-bi-creators-consumers.png)

## <a name="report-reading-view"></a>Visualizzazione di lettura del report

 La visualizzazione di lettura consente di esplorare e interagire con il report. Si tratta di un modo semplice e sicuro per modificare e ottenere informazioni sui dati. La visualizzazione di lettura è stata progettata per i *consumer* di report, per gli utenti che aprono report dalle app o per cli utenti [con cui sono stati condivisi](service-share-dashboards.md) report. La visualizzazione di lettura garantisce che ogni singolo consumer di un report specifico visualizzi lo stesso report e le stesse visualizzazioni e, facoltativamente, con i medesimi filtri applicati.  I consumer possono interagire con i report, modificare i filtri esistenti, nel qual caso le modifiche vengono salvate con il report, ma non possono aggiungere nuovi filtri.

>**NOTA**: in alcuni casi, i consumer dei report possono visualizzare dati diversi a seconda delle autorizzazioni per i dati e della sicurezza a livello di riga.

## <a name="report-editing-view"></a>Visualizzazione di modifica del report

La visualizzazione di modifica è disponibile solo agli autori del report o ai colleghi che sono [comproprietari di un report in quanto membri o amministratori di un'area di lavoro delle app](service-create-distribute-apps.md).

La visualizzazione di modifica è stata progettata per gli *autori* dei report. In questa visualizzazione gli autori possono importare e connettersi a set di dati, esplorare i dati e creare report e dashboard. Nella visualizzazione di modifica gli *autori* possono esaminare più in dettaglio i dati aggiungendo e rimuovendo campi, cambiando il tipo di visualizzazione, creando nuove visualizzazioni e aggiungendo ed eliminando visualizzazioni e pagine dal report. Possono quindi condividere i report creati con i colleghi.

## <a name="reading-view-versus-editing-view"></a>Confronto tra la visualizzazione di lettura e la visualizzazione di modifica
Questo grafico non elenca tutte le funzionalità dei report disponibili nel servizio Power BI. Elenca solo le attività dei report non disponibili in **entrambe** le visualizzazioni, ovvero nella visualizzazione di lettura e nella visualizzazione di modifica.


|Attività  | Visualizzazione di lettura  | Visualizzazione di modifica |
|-------------------------|-------|-------|
|**Interi report**  |
| [Creare o modificare un report](service-report-create-new.md) | No  | Sì |
| [Condividere un report](service-share-reports.md)| Sì | Sì, ed è inoltre possibile gestire le autorizzazioni, concedendo anche ad altri utenti le autorizzazioni di *proprietario*. |
| [Creare filtri persistenti (permanenti) a livello visivo, filtri di drill-through, filtri a livello di pagina e filtri a livello di report dal riquadro Filtri](power-bi-report-add-filter.md) | No  | Sì |
| [Usare il riquadro Filtri del report](power-bi-how-to-report-filter.md) | Sì, è possibile utilizzare i filtri esistenti e le modifiche possono essere salvate con il report, ma non è possibile aggiungere nuovi filtri. | Sì |
| [Usare il riquadro Analisi del report](service-analytics-pane.md) | No | Sì |
| [Opzioni di **visualizzazione** del report](power-bi-report-display-settings.md) | Sì, con alcune eccezioni. | Sì, tutte, incluse le linee della griglia, l'allineamento e il blocco. |
| [Creare una pianificazione dell'aggiornamento](refresh-data.md) | No  | Sì |
| [Sottoscrivere un report](service-report-subscribe.md) | Sì | No |
| [Domande e risposte - Porre le domande nei report](power-bi-q-and-a.md) | No  | Sì |
| [Visualizzare le metriche di utilizzo](service-usage-metrics.md) | Sì, nell'area di disegno report. | Sì, nell'elenco di report (visualizzazione contenuto) |
| [Visualizzare elementi correlati](service-related-content.md) | Sì, nell'area di disegno report. | Sì, nell'elenco di report (visualizzazione contenuto) |
| [Salvare un report](service-report-save.md) | Sì, ma solo usando **Salva con nome**. | Sì |
| [Eliminare un report](service-delete.md) | No  | Sì |
|**Pagine del report** |
| [Aggiungere o rinominare una pagina del report](power-bi-report-add-page.md)  | No  | Sì  |
| [Duplicare una pagina di un report](power-bi-report-copy-paste-page.md) | No  | Sì |
| [Eliminare una pagina di un report](service-delete.md) | no | sì |
|**Uso delle visualizzazioni dei report**|
| [Aggiungere visualizzazioni a un report](power-bi-report-add-visualizations-i.md) | No  | Sì |
| [Aggiungere caselle di testo e forme a un report](power-bi-reports-add-text-and-shapes.md) | No  | Sì |
| [Usare il riquadro Formattazione del report](service-the-report-editor-take-a-tour.md) | No | Sì |
| [Configurare le interazioni con gli oggetti visivi](service-reports-visual-interactions.md) | No  | Sì |
| [Mostrare i dati usati per creare la visualizzazione](service-reports-show-data.md) | No  | Sì |
| [Configurare l'esplorazione](power-bi-visualization-drill-down.md) | No  | Sì |
| [Modificare la visualizzazione in uso](power-bi-report-change-visualization-type.md) | No | Sì|
| [Eliminare una visualizzazione, una casella di testo o una forma](service-delete.md)| No | Sì |


## <a name="navigating-between-editing-view-and-reading-view"></a>Passare dalla Visualizzazione di modifica alla Visualizzazione di lettura
Tenere presente che solo l'autore e i proprietari dei report possono aprire un report in Visualizzazione di modifica.

1. Per impostazione predefinita, il report viene aperto in Visualizzazione di lettura. Se è disponibile l'opzione **Modifica report**, significa che è attiva la Visualizzazione di lettura. Se l'opzione **Modifica report** è disabilitata, significa che l'utente non è autorizzato ad aprire il report in Visualizzazione di modifica.

   ![Modifica report disabilitata](media/service-reading-view-and-editing-view/power-bi-edit-report-grey.png)

2. Se l'opzione **Modifica report** non è disabilitata, selezionarla per aprire il report in Visualizzazione di modifica.

   ![Opzione Modifica report](media/service-reading-view-and-editing-view/power-bi-edit-report.png)

   Il report è ora nella Visualizzazione di modifica e presenta le ultime [impostazioni di visualizzazione](power-bi-report-display-settings.md) usate nella Visualizzazione di lettura.

2. Per tornare alla Visualizzazione di lettura, selezionare **Visualizzazione di lettura** nella barra di spostamento superiore.

    ![Opzione Visualizzazione di lettura](media/service-reading-view-and-editing-view/power-bi-reading-view.png)



### <a name="next-steps"></a>Passaggi successivi
Esistono moltissimi modi per interagire con un report nella Visualizzazione di lettura, ad esempio filtrando e trasformando i dati per ottenere informazioni dettagliate e risposte alle domande.  L'argomento successivo, [Interagire con un report nella Visualizzazione di lettura](service-interact-with-a-report-in-editing-view.md), illustra in modo dettagliato alcuni approcci.    
Tornare ai [report in Power BI](service-reports.md)    
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
