---
title: "Novità del Server di report di Power BI"
description: "Informazioni sulle novità del Server di report di Power BI. Questa sezione riguarda le funzionalità principali e viene aggiornata con il rilascio di nuovi elementi."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/31/2017
ms.author: asaxton
ms.openlocfilehash: d351a117307e86c7b0750e9bcdf813b08b28bb0f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="whats-new-in-power-bi-report-server"></a>Novità del Server di report di Power BI
Informazioni sulle novità del Server di report di Power BI. Questa sezione riguarda le funzionalità principali e viene aggiornata con il rilascio di nuovi elementi.

Per scaricare il server di report di Power BI e Power BI Desktop ottimizzati per il server di report di Power BI, visitare [Creazione di report in locale con il server di report di Power BI](https://powerbi.microsoft.com/report-server/).

![suggerimento](media/whats-new/fyi-tip.png "suggerimento") Per le note sulla versione corrente, vedere [Server di Report di Power BI - Note sulla versione](release-notes.md).

per le relative informazioni incluse nelle "Novità", vedere:

* [Novità del servizio Power BI](../service-whats-new.md)
* [Novità di Power BI Desktop](../desktop-latest-update.md)
* [Novità delle app per dispositivi mobili per Power BI](../mobile-whats-new-in-the-mobile-apps.md)
* [Blog del team di Power BI](https://powerbi.microsoft.com/blog/)

## <a name="october-2017-release"></a>Versione di ottobre 2017
### <a name="power-bi-report-data-sources"></a>Origini dati dei report di Power BI
I report di Power BI nel server di report di Power BI possono connettersi a diverse origini dati. È possibile importare i dati e pianificare l'aggiornamento dei dati oppure eseguire direttamente query sui dati usando DirectQuery o una connessione dinamica a SQL Server Analysis Services. Per un elenco delle origini dati che supportano gli aggiornamenti pianificati e delle origini dati che supportano DirectQuery, vedere "Origini dati dei report di Power BI nel server di report di Power BI".

### <a name="scheduled-data-refresh-for-imported-data"></a>Aggiornamento pianificato dei dati per i dati importati
Nel server di report di Power BI è possibile configurare un aggiornamento pianificato dei dati per mantenere aggiornati i dati dei report di Power BI con un modello incorporato, invece che tramite una connessione dinamica o DirectQuery. Con un modello incorporato i dati vengono importati, quindi risultano disconnessi dall'origine dati originale. È quindi necessario aggiornare i dati per assicurarsi che siano recenti e un aggiornamento pianificato è l'approccio ottimale. Per altre informazioni, vedere "Aggiornamento pianificato per i report di Power BI nel server di report di Microsoft Power BI".

### <a name="editing-power-bi-reports-from-the-server"></a>Modifica dei report di Power BI dal server
È possibile aprire e modificare i file di report di Power BI (con estensione pbix) dal server, ma viene restituito il file originale caricato.  Quindi, **se i dati sono stati aggiornati dal server, non verranno aggiornati alla prima apertura del file**. È necessario eseguire l'aggiornamento manuale in locale per visualizzare le modifiche.

### <a name="large-file-uploaddownload"></a>Caricamento/Download di file di grandi dimensioni
È possibile caricare file di dimensioni massime di 2 GB, anche se per impostazione predefinita questo limite è impostato su 1 GB in nelle impostazioni del server di report in SQL Server Management Studio (SSMS).  Questi file vengono archiviati nel database, analogamente a SharePoint, e non è necessaria alcuna configurazione speciale per il catalogo di SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Accesso ai set di dati condivisi come feed OData
È possibile accedere ai set di dati condivisi da Power BI Desktop con un feed OData. Per altre informazioni, vedere [Accessing shared datasets as OData feeds in Power BI Report Server](access-dataset-odata.md) (Accesso ai set di dati condivisi come feed OData nel server di report di Power BI).

### <a name="scale-out"></a>Aumento delle istanze
Questa versione supporta l'aumento delle istanze. Usare un servizio di bilanciamento del carico e configurare l'affinità del server per ottenere un'esperienza ottimale. Si noti che questo scenario non è stato ancora ottimizzato per l'aumento delle istanze, quindi è possibile che i modelli vengano replicati in più nodi. Lo scenario funziona senza il servizio di bilanciamento del carico di rete e le sessioni permanenti. Si noterà tuttavia un uso eccessivo della memoria nei nodi, perché il modello viene caricato N volte, e le prestazioni risulteranno rallentate tra le connessioni, poiché il modello viene sottoposto a streaming quando raggiunge un nuovo nodo tra le richieste.  

### <a name="administrator-settings"></a>Impostazioni dell'amministratore
Gli amministratori possono configurare le proprietà seguenti in Proprietà avanzate di SSMS per la server farm:

* EnableCustomVisuals: True/False.
* EnablePowerBIReportEmbeddedModels: True/False.
* EnablePowerBIReportExportData: True/False.
* MaxFileSizeMb: l'impostazione predefinita è ora 1000.
* ModelCleanupCycleMinutes: frequenza della verifica per la rimozione dei modelli dalla memoria.
* ModelExpirationMinutes: tempo di attesa prima della scadenza e della rimozione del modello in base all'ora dell'ultimo uso.
* ScheduleRefreshTimeoutMinutes: tempo necessario per l'aggiornamento dei dati per un modello. L'impostazione predefinita è due ore.  Non è previsto alcun limite rigido massimo.

**File di configurazione rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API Developer
L'API Developer (API REST) introdotta per SSRS 2017 è stata estesa per consentire il funzionamento del Server di report di Power BI con i file di Excel e i file con estensione pbix. Un caso d'uso possibile consiste nello scaricare i file dal server a livello di codice, aggiornarli e quindi pubblicarli di nuovo. Questo è l'unico modo per aggiornare le cartelle di lavoro di Excel con i modelli PowerPivot, ad esempio.

Si noti che è disponibile una nuova API separata per file di grandi dimensioni, che verrà aggiornata nella versione del server di report di Power BI di Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>Footprint di memoria di SQL Server Analysis Services (SSAS) e del server di report di Power BI
Il server di report di Power BI ospita ora internamente SQL Server Analysis Services (SSAS). Ciò non riguarda in modo specifico l'aggiornamento pianificato. L'hosting di SSAS può espandere notevolmente il footprint di memoria del server di report. Il file di configurazione AS.ini è disponibile nei nodi del server. Se quindi si ha familiarità con SSAS, è consigliabile aggiornare le impostazioni, inclusi il limite massimo di memoria, la memorizzazione nella cache del disco e così via. Per informazioni dettagliate, vedere [Proprietà del server in Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services).

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Visualizzazione e interazione con le cartelle di lavoro di Excel
Excel e Power BI includono strumenti unici nel settore. Insieme consentono ai business analyst di raccogliere, strutturare, analizzare ed esplorare visivamente i dati con maggiore facilità. Oltre a visualizzare i report di Power BI nel portale Web, gli utenti aziendali possono ora visualizzare le cartelle di lavoro di Excel nel Server di report di Power BI e hanno quindi ha disposizione un'unica posizione per la pubblicazione e la visualizzazione del proprio contenuto self-service di Microsoft BI.

È stata pubblicata una [procedura dettagliata per l'aggiunta di Office Online Server (OOS) all'ambiente di anteprima del Server di report di Power BI](excel-oos.md). I clienti con un account per contratti multilicenza possono scaricare Office Online Server dal Volume License Servicing Center senza costi aggiuntivi e con funzionalità di sola visualizzazione. Dopo la configurazione, gli utenti possono visualizzare e interagire con le cartelle di lavoro di Excel che hanno le caratteristiche seguenti:

* Nessuna dipendenza da origini dati esterne
* Connessione dinamica a un'origine dati esterna di SQL Server Analysis Services
* Modello di dati di PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Supporto per nuovi oggetti visivi di tipo tabella e matrice
Il server di report di Power BI supporta ora i nuovi oggetti visivi di tipo tabella e matrice di Power BI. Per creare report con tali oggetti visivi, sarà necessaria una versione aggiornata di Power BI Desktop per la versione di ottobre 2017. Non è possibile installarla side-by-side alla versione di Power BI Desktop (giugno 2017). Per la versione più aggiornata di Power BI Desktop, nella [pagina di download del server di report di Power BI](https://powerbi.microsoft.com/report-server/) selezionare **Opzioni avanzate di download**.

## <a name="june-2017"></a>Giugno 2017
* Il server di report di Power BI è disponibile a livello generale (GA).

## <a name="may-2017"></a>Maggio 2017
* L'anteprima di server di report di Power BI è stata resa disponibile
* Possibilità di pubblicare report di Power BI locali
  * Supporto per oggetti visivi personalizzati
  * Supporto solo per connessioni dinamiche di Analysis Services con altre origini dati previste.
  * App Power BI per dispositivi mobili aggiornata in modo da visualizzare i report di Power BI ospitati nel Server di Report di Power BI
* Miglioramento della collaborazione nei report con commenti

## <a name="next-steps"></a>Passaggi successivi
[Note sulla versione del Server di report di Power BI](release-notes.md)  
[Manuale per l'utente](user-handbook-overview.md)  
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Avvio rapido: installazione del Server di report di Power BI](quickstart-install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

