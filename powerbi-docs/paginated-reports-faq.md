---
title: 'Report impaginati in Power BI: DOMANDE FREQUENTI'
description: Questo articolo include le risposte alle domande frequenti sui report impaginati. Questi report includono output con formattazione avanzata e perfetto al pixel ottimizzato per la stampa o per la creazione di PDF.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 07/15/2019
ms.openlocfilehash: 2e59499b93f4d1b4879cdec5b807f863a80718aa
ms.sourcegitcommit: 805d52e57a935ac4ce9413d4bc5b31423d33c5b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68665362"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Report impaginati in Power BI: DOMANDE FREQUENTI 

Questo articolo include le risposte alle domande frequenti sui report impaginati. Questi report includono output con formattazione avanzata e perfetto al pixel ottimizzato per la stampa o per la creazione di PDF. Vengono definiti "impaginati" perché sono formattati per adattarsi al meglio a più pagine. I report impaginati sono basati sulla tecnologia di report RDL in SQL Server Reporting Services. 

Questo articolo risponde a molte domande comuni sui report impaginati in Power BI Premium e su Generatore report, lo strumento autonomo per la creazione di report impaginati. È necessaria una licenza di Power BI Pro per pubblicare un report nel servizio. È possibile pubblicare e condividere i report impaginati nell'area di lavoro personale o in aree di lavoro per le app, purché l'area di lavoro sia in una capacità Power BI Premium. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Quale capacità Premium è necessaria per i report impaginati?

Il carico di lavoro per i report impaginati è disponibile negli SKU P1-P3.  È anche possibile usarlo con gli SKU A4-A6 per scenari di incorporamento SaaS.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual è la soglia di memoria massima che è possibile impostare per i report impaginati per la capacità?

Entro la fine del 2019, sarà possibile usare fino al 100% della memoria per questo carico di lavoro. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Come funziona l'accesso utente per i report impaginati?

L'accesso utente per i report impaginati è lo stesso valido per tutti gli altri contenuti nel servizio Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Come si attiva/disattiva il carico di lavoro per i report impaginati?

L'amministratore della capacità può abilitare o disabilitare il carico di lavoro per report impaginati nella pagina del portale di amministrazione della capacità.  Per impostazione predefinita, il carico di lavoro sarà attivo per tutte le nuove capacità create.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Come è possibile monitorare l'utilizzo dei report impaginati nel tenant?

I log di controllo di Office 365 offrono informazioni dettagliate sull'utilizzo di questo tipo di report negli eventi seguenti: 

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

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Qual è la memoria predefinita per ogni SKU Premium supportato per i report impaginati?

Memoria predefinita in ogni SKU Premium per i report impaginati:

- **P1/A4**: 20% predefinita; 10% minima
- **P2/A5**: 20% predefinita; 5% minima
- **P3/A6**: 20% predefinita; 2,5% minima

## <a name="general"></a>Generale

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quando è consigliabile usare un report impaginato invece di un report di Power BI?

I report impaginati sono ideali per scenari che richiedono output con formattazione avanzata e perfetto al pixel ottimizzato per la stampa o la creazione di PDF.  Un conto profitti e perdite è un buon esempio del tipo di report che è probabile si voglia creare come report impaginato.  

I report di Power BI sono ottimizzati per l'esplorazione e l'interattività.  Un report delle vendite in cui diversi venditori vogliono analizzare i dati nello stesso report in base ad area/settore/cliente specifici per esaminare le variazioni, è un esempio di report che è consigliabile gestire come report di Power BI.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>La documentazione indica Generatore report di Power BI come strumento di creazione preferito. È possibile creare report impaginati in SQL Server Data Tools per Power BI?

Sì, ma il servizio Power BI consente solo di caricare un singolo elemento alla volta, quindi molti degli scenari usati dagli autori con SQL Server Data Tools (SSDT) non sono ancora supportati. Visualizzare l'[elenco completo delle funzionalità non supportate](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) disponibile più avanti in queste domande frequenti.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quali versioni di Generatore report sono supportate?

Di recente è stato rilasciato Generatore report di Power BI come strumento principale di creazione per i report impaginati nel servizio Power BI. Installare [Generatore report di Power BI dall'Area download Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Come si possono trasferire in Power BI i report esistenti salvati in SQL Server Reporting Services?

È necessario scaricare il report dal server e quindi caricarlo in Power BI tramite il portale.  Non è attualmente disponibile alcuno strumento di migrazione, ma ne è prevista la creazione al termine del periodo di anteprima pubblica dopo aver raccolto informazioni accurate sul livello corretto di parità delle funzionalità tra i prodotti.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>È possibile aprire i report e pubblicarli direttamente nel servizio?

Sì. Di recente, è stato aggiunto il supporto per l'apertura dei report e la loro pubblicazione direttamente nel servizio da Generatore report di Power BI.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quali funzionalità dei report impaginati di SSRS non sono ancora supportate in Power BI?

Attualmente, i report impaginati non supportano quanto segue:

- Origini dati condivise
- Set di dati condivisi
- Sottoreport
- Drill-through e click-through in altri report
- Report collegati
- Livelli mappa di Bing
- Tipi di carattere personalizzati

Viene visualizzato un messaggio di errore se si prova a caricare un file con una funzionalità non supportata nel servizio Power BI, diversa da attivazione/disattivazione e ordinamento.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quali origini dati sono attualmente supportate per i report impaginati?

Sono supportate le origini dati seguenti: 

- Set di dati di Power BI (tramite Single Sign-On (SSO))
- Azure Analysis Services (tramite Single Sign-On (SSO) e oAuth)
- Azure SQL Data Warehouse
- Database SQL di Azure (nome utente/password, SSO e oAuth)
- SQL Server*
- Modelli tabulari (DAX) e multidimensionali (MDX) di SQL Server Analysis Services (SSAS)* 
- Oracle* 
- Teradata* 

* è richiesto il gateway locale.

Quando si accede a SSAS tramite il gateway, l'utente con le credenziali archiviate deve avere autorizzazioni con privilegi elevati in SSAS per lavorare tramite il gateway.

### <a name="what-authentication-methods-do-you-support"></a>Quali metodi di autenticazione sono supportati?

L'accesso SSO è supportato per Azure Analysis Services, il database SQL di Azure e le origini dati Power BI.  È supportato anche OAuth per il database SQL di Azure e Azure Analysis Services.  Per le altre origini dati, attualmente è necessario archiviare un nome utente e una password con l'origine dati nel portale o nel gateway.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>È possibile usare un set di dati di Power BI come origine dati per il report impaginato?

Sì, i set di dati di Power BI sono supportati come origini dati per i report impaginati.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>È possibile usare stored procedure tramite il gateway?

È possibile usare una stored procedure tramite il gateway, ma potrebbero verificarsi dei problemi in alcuni scenari se la stored procedure include parametri.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quali formati di esportazione sono disponibili per il report nel servizio Power BI?

È possibile esportare in Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>È possibile stampare i report impaginati?

Sì, la stampa è disponibile per i report impaginati e include un'esperienza di anteprima di stampa nuova e migliorata. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>Sono già disponibili sottoscrizioni tramite posta elettronica per i report impaginati?

Sì, le sottoscrizioni di posta elettronica sono pienamente supportate per i report impaginati ed è incluso il supporto per sei diversi formati di file e valori dei parametri.

### <a name="can-i-run-custom-code-in-my-report"></a>È possibile eseguire codice personalizzato nel report?

Sì, è supportata la possibilità di eseguire il codice nei report come in SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>È possibile usare Power BI Embedded per incorporare i report impaginati in un'app ospitata?

L'incorporamento in SaaS è già supportato. L'incorporamento in PaaS al momento non è supportato.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>È possibile eseguire il drill-through da un report di Power BI a un report impaginato?

Non ancora, ma è assolutamente previsto il supporto di questo scenario.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>È possibile condividere il contenuto di un report impaginato tramite un'app Power BI?

Sì, è supportata la distribuzione dei report impaginati con le app dalle aree di lavoro sia v1 che v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Le altre funzionalità specifiche dei report in Power BI, come l'aggiunta di riquadri di report ai dashboard, saranno disponibili anche con i report impaginati?

È previsto che i report supportino gli stessi scenari principali nel servizio quanto più possibile.  In teoria, anche se lo strumento di creazione è diverso, dal punto di vista del consumatore si tratta semplicemente di un altro report nel relativo elenco nel portale. Per questi utenti è irrilevante come è stato creato, se consente loro di fare ciò che serve.  Un buon esempio di questa parità delle funzionalità è il supporto previsto dei commenti. Anche se la funzionalità stessa potrebbe essere leggermente diversa per ogni tipo di report, sarà possibile usare i commenti per entrambi.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>È previsto uno strumento di migrazione per consentire ai clienti di SSRS di trasferire report e asset esistenti in Power BI?

Verranno valutate opzioni per consentire lo spostamento del contenuto in Power BI in modo automatico, ma non saranno disponibili prima della versione GA.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Esiste un controllo visualizzatore report per i report impaginati nel servizio Power BI?

No, non è attualmente disponibile un controllo visualizzatore report.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>È possibile cercare report impaginati dalla nuova esperienza della Home page nel servizio Power BI?

Sì, attualmente è possibile cercare i report impaginati dalla Home.  Tali report sono visibili anche in altre parti della nuova esperienza Home.

## <a name="next-steps"></a>Passaggi successivi

- [Installare Generatore report di Power BI dall'Area download Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Esercitazione: Creare un report impaginato](paginated-reports-quickstart-aw.md)
