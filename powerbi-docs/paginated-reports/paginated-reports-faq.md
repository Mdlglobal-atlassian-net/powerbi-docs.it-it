---
title: 'Report impaginati in Power BI: Domande frequenti'
description: Questo articolo include le risposte alle domande frequenti sui report impaginati. Questi report includono output con formattazione avanzata e perfetto al pixel ottimizzato per la stampa o per la creazione di PDF.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 0089a38c852d82acaebc8cab0f0fb653c6a304cb
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565627"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Report impaginati in Power BI: Domande frequenti 

Questo articolo include le risposte alle domande frequenti sui report impaginati. Questi report includono output con formattazione avanzata e perfetto al pixel ottimizzato per la stampa o per la creazione di PDF. Vengono definiti "impaginati" perché sono formattati per adattarsi al meglio a più pagine. I report impaginati sono basati sulla tecnologia di report RDL in SQL Server Reporting Services. 

Questo articolo risponde a molte domande comuni sui report impaginati in Power BI Premium e su Generatore report, lo strumento autonomo per la creazione di report impaginati. È necessaria una licenza di Power BI Pro per pubblicare un report nel servizio. È possibile pubblicare e condividere i report impaginati nell'area di lavoro personale o in aree di lavoro, purché l'area di lavoro sia in una capacità Power BI Premium. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Quale capacità Premium è necessaria per i report impaginati?

Il carico di lavoro per i report impaginati è disponibile negli SKU P1-P3.  È anche possibile usarlo con gli SKU A4-A6 per scenari di incorporamento o di test/sviluppo.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual è la soglia di memoria massima che è possibile impostare per i report impaginati per la capacità?

È possibile usare fino al 100% della memoria per questo carico di lavoro.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Come funziona l'accesso utente per i report impaginati?

L'accesso utente per i report impaginati è lo stesso valido per tutti gli altri contenuti nel servizio Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Come si attiva/disattiva il carico di lavoro per i report impaginati?

L'amministratore della capacità può abilitare o disabilitare il carico di lavoro per report impaginati nella pagina del portale di amministrazione della capacità.  Per impostazione predefinita, il carico di lavoro è disponibile per tutte le nuove capacità create, ma non utilizza la memoria fino a quando il primo report impaginato non viene caricato.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Come è possibile monitorare l'utilizzo dei report impaginati nel tenant?

I log di controllo offrono informazioni dettagliate sull'utilizzo di questo tipo di report negli eventi seguenti:

- View Power BI Report (Visualizza report Power BI)
- Delete Power BI report (Elimina report Power BI)
- Create Power BI report (Crea report Power BI)
- Report di Power BI scaricato

Il valore ReportType del campo è "PaginatedReport" per distinguere i report impaginati dai report di Power BI.

Inoltre, i log di controllo offrono gli eventi seguenti per i report impaginati:

- Binded Power BI dataset to gateway (Set di dati di Power BI associato al gateway)
- Discover Power BI Datasource (Individuazione origine dati di Power BI)
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>È possibile monitorare questo carico di lavoro tramite l'app di monitoraggio della capacità Premium?

Sì, il monitoraggio è disponibile in una nuova scheda con gli stessi dettagli disponibili per i set di dati di Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>È necessaria una licenza Pro per creare e pubblicare report impaginati?

È possibile caricare report impaginati nell'Area di lavoro personale senza una licenza Pro se l'area di lavoro è assegnata a una capacità Premium.  Per altre aree di lavoro, è necessario disporre di una licenza Pro per creare e pubblicare contenuti. È consigliabile scaricare e usare Generatore report di Power BI anche senza la licenza Pro, ma in questo caso, non sarà possibile pubblicare i report impaginati creati. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Cosa accade se esiste un report impaginato in un'area di lavoro e il carico di lavoro per i report impaginati viene disattivato?

Viene visualizzato un messaggio di errore e non è possibile visualizzare il report fino a quando il carico di lavoro non viene nuovamente attivato. È comunque possibile eliminare il report dall'area di lavoro.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>Qual è la memoria predefinita per ogni SKU Premium che supporta i report impaginati?

Memoria predefinita in ogni SKU Premium per i report impaginati:

- **P1/A4**: 20% predefinita; 10% minima
- **P2/A5**: 20% predefinita; 5% minima
- **P3/A6**: 20% predefinita; 2,5% minima

Gli amministratori del tenant di Power BI possono modificare la percentuale massima di memoria predefinita nel portale di amministrazione. Vedere la sezione del carico di lavoro **Report impaginati** in **Power BI Premium** nella scheda **Impostazioni di capacità**.

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="Scheda Impostazioni di capacità, Report impaginati":::

## <a name="general"></a>Generale

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quando è consigliabile usare un report impaginato invece di un report di Power BI?

I report impaginati sono ideali per scenari che richiedono output con formattazione avanzata e perfetto al pixel ottimizzato per la stampa o la creazione di PDF.  Un conto profitti e perdite è un buon esempio del tipo di report che è probabile si voglia creare come report impaginato.  

I report di Power BI sono ottimizzati per l'esplorazione e l'interattività.  Un report delle vendite in cui diversi venditori vogliono analizzare i dati nello stesso report in base ad area/settore/cliente specifici per esaminare le variazioni, è un esempio di report che è consigliabile gestire come report di Power BI.

Per altre informazioni, vedere [Quando usare report impaginati in Power BI](../guidance/report-paginated-or-power-bi.md).

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>La documentazione indica Generatore report di Power BI come strumento di creazione preferito. È possibile creare report impaginati in SQL Server Data Tools per Power BI?

Sì, ma il servizio Power BI consente solo di caricare un singolo elemento alla volta, quindi molti degli scenari usati dagli autori con SQL Server Data Tools (SSDT) non sono ancora supportati. Visualizzare l'[elenco completo delle funzionalità non supportate](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) disponibile più avanti in queste domande frequenti.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quali versioni di Generatore report sono supportate?

Power BI Report Builder è stato rilasciato come strumento principale per la creazione di report impaginati nel servizio Power BI. Installare [Generatore report di Power BI dall'Area download Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Come si possono trasferire in Power BI i report esistenti salvati in SQL Server Reporting Services?

Un progetto in GitHub supporta ora la migrazione del contenuto da SQL Server Reporting Services a Power BI.  Visualizzare i dettagli e scaricare lo strumento qui: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>È possibile aprire i report e pubblicarli direttamente nel servizio?

Sì. È stato aggiunto il supporto per l'apertura e la pubblicazione dei report direttamente nel servizio da Power BI Report Builder.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quali funzionalità dei report impaginati di SSRS non sono ancora supportate in Power BI?

Attualmente, i report impaginati non supportano quanto segue:

- Origini dati condivise
- Set di dati condivisi
- Drill-through e click-through in altri report
- Report collegati
- Tipi di carattere personalizzati

Viene visualizzato un messaggio di errore se si prova a caricare un file con una funzionalità non supportata nel servizio Power BI, diversa da attivazione/disattivazione e ordinamento.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quali origini dati sono attualmente supportate per i report impaginati?

Per un elenco di origini dati, vedere l'articolo [Origini dati supportate per i report impaginati di Power BI](paginated-reports-data-sources.md). 

### <a name="what-authentication-methods-do-you-support"></a>Quali metodi di autenticazione sono supportati?

L'accesso SSO è supportato per Azure Analysis Services, il database SQL di Azure e le origini dati Power BI.  È supportato anche OAuth per il database SQL di Azure e Azure Analysis Services.  Per le altre origini dati, attualmente è necessario archiviare un nome utente e una password con l'origine dati nel portale o nel gateway.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>È possibile usare un set di dati di Power BI come origine dati per il report impaginato?

Sì, i set di dati di Power BI sono supportati come origini dati per i report impaginati.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>È possibile usare stored procedure tramite il gateway?

Sì, le stored procedure tramite il gateway sono supportate per le origini dati di SQL Server, incluse quelle che usano i parametri.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quali formati di esportazione sono disponibili per il report nel servizio Power BI?

È possibile esportare in Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>È possibile stampare i report impaginati?

Sì, la stampa è disponibile per i report impaginati e include un'esperienza di anteprima di stampa nuova e migliorata. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>Sono disponibili sottoscrizioni tramite posta elettronica per i report impaginati?

Sì, le sottoscrizioni di posta elettronica sono pienamente supportate per i report impaginati ed è incluso il supporto per sei diversi formati di file e valori dei parametri.

### <a name="can-i-run-custom-code-in-my-report"></a>È possibile eseguire codice personalizzato nel report?

Sì, è supportata la possibilità di eseguire il codice nei report come in SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>È possibile usare Power BI Embedded per incorporare i report impaginati in un'app ospitata?

L'incorporamento SaaS, incluso il supporto per Secure embed, è già disponibile. Per l'incorporamento PaaS, vedere l'esercitazione [Incorporare report impaginati di Power BI in un'applicazione per i clienti](../developer/embedded/embed-paginated-reports-customers.md).

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>È possibile eseguire il drill-through da un report di Power BI a un report impaginato?

Sì, questa operazione può essere eseguita usando i parametri URL con i report impaginati.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>È possibile condividere il contenuto di un report impaginato tramite un'app Power BI?

Sì, è supportata la distribuzione dei report impaginati con le app dalle aree di lavoro sia v1 che v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Le altre funzionalità specifiche dei report in Power BI, come l'aggiunta di riquadri di report ai dashboard, saranno disponibili anche con i report impaginati?

È previsto che i report supportino gli stessi scenari principali nel servizio quanto più possibile.  In teoria, anche se lo strumento di creazione è diverso, dal punto di vista dell'utente finale si tratta semplicemente di un altro report nel relativo elenco nel portale. Per questi utenti è irrilevante come è stato creato, se consente loro di fare ciò che serve.  Un buon esempio di questa parità delle funzionalità è il supporto previsto dei commenti. Anche se la funzionalità stessa potrebbe essere leggermente diversa per ogni tipo di report, sarà possibile usare i commenti per entrambi.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Esiste un controllo visualizzatore report per i report impaginati nel servizio Power BI?

No, non è attualmente disponibile un controllo visualizzatore report.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>È possibile cercare report impaginati dalla nuova esperienza della Home page nel servizio Power BI?

Sì, attualmente è possibile cercare i report impaginati dalla Home.  Tali report sono visibili anche in altre parti della nuova esperienza Home.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
Ecco alcuni aspetti da tenere presenti quando si usano i campi DateTime nei report impaginati.

- Attualmente esistono alcune limitazioni di globalizzazione correlate ai parametri DateTime. Tutti i parametri DateTime nel servizio Power BI vengono recuperati nel formato US (MM/GG/AAAA) indipendentemente dalla modalità di progettazione di DataTime in Power BI Report Builder.

## <a name="next-steps"></a>Passaggi successivi

- [Installare Generatore report di Power BI dall'Area download Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Esercitazione: Creare un report impaginato](paginated-reports-quickstart-aw.md)
