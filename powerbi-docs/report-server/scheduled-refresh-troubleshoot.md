---
title: Risolvere i problemi degli aggiornamenti pianificati nel server di report di Power BI
description: Questo articolo illustra le risorse disponibili per la risoluzione dei problemi degli aggiornamenti pianificati nel server di report di Power BI.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: cf084492a7b5d1ecc10ff933eeaef4cdbdc14022
ms.sourcegitcommit: bdb1fee3612bcc66153dcad8c4db2e99fb041014
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Risolvere i problemi degli aggiornamenti pianificati nel server di report di Power BI
Questo articolo illustra le risorse disponibili per la risoluzione dei problemi degli aggiornamenti pianificati nel server di report di Power BI.

In caso di rilevamento di altri problemi, l'articolo verrà aggiornato con informazioni utili per la risoluzione.

## <a name="common-issues"></a>Problemi comuni
Ecco i problemi più comuni durante un tentativo di pianificazione di un aggiornamento per un report. 

### <a name="driver-related-problems"></a>Problemi correlati al driver
La connessione a diverse origini dati potrebbe richiedere driver di terze parti che devono essere installati per stabilire correttamente la connessione. È necessario installarli non solo nel computer in cui si usa Power BI Desktop, ma anche nel server di report.

Il driver può essere a 32 bit e 64 bit. Assicurarsi di installare il driver a 64 bit, perché il server di report di Microsoft Power BI è a 64 bit.

Per informazioni sull'installazione e sulla configurazione di driver di terze parti, contattare il produttore.

### <a name="memory-pressure"></a>Utilizzo elevato di memoria
È possibile che si verifichi un utilizzo elevato di memoria quando i report necessitano di una quantità maggiore di memoria per l'elaborazione e il rendering. La pianificazione dell'aggiornamento ai report potrebbe richiedere una quantità significativa di memoria nel computer, in particolare per i report di grandi dimensioni. L'utilizzo elevato di memoria può provocare errori dei report, oltre a un potenziale arresto anomalo del server di report stesso.

Se viene rilevato spesso un utilizzo elevato di memoria, prendere in considerazione una distribuzione con aumento delle istanze per il server di report, in modo da distribuire uniformemente il carico delle risorse. È anche possibile specificare che un determinato server di report viene usato per l'aggiornamento dei dati tramite l'impostazione `IsDataModelRefreshService` in rsreportserver.config. Questa impostazione consente di definire uno o più server da usare come server front-end per la gestione di report su richiesta e di specificare un altro set di server da usare solo per gli aggiornamenti pianificati.

Per informazioni su come monitorare un'istanza di Analysis Services, vedere [Monitorare un'istanza di Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Per informazioni sulle impostazioni della memoria in Analysis Services, vedere [Proprietà della memoria](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Configurazione di Kerberos
La connessione a un'origine dati con le credenziali di Windows potrebbe richiedere la configurazione della delega vincolata di Kerberos per stabilire una connessione corretta. Per altre informazioni su come configurare la delega vincolata di Kerberos, vedere [Configurare Kerberos per l'uso di report di Power BI](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Problemi noti
Le informazioni sui problemi noti verranno elencate qui non appena saranno disponibili.

## <a name="configuration-settings"></a>Impostazioni di configurazione
Le impostazioni seguenti possono essere usate per influire sugli aggiornamenti pianificati. Le impostazioni configurate in SQL Server Management Studio (SSMS) sono applicabili a tutti i server di report in una distribuzione con aumento delle istanze. Le impostazioni configurate in rsreportserver.config sono destinate al server specifico in cui vengono configurate.

**Impostazioni in SSMS:**

| Impostazione | Descrizione |
| --- | --- |
| MaxFileSizeMb |Dimensioni massime dei file per i report caricati. Il valore predefinito è 1000 MB (1 GB). Il valore massimo è 2000 MB (2 GB). |
| ModelCleanupCycleMinutes |Definisce la frequenza con cui il modello viene verificato per la rimozione dalla memoria. L'impostazione predefinita è 15 minuti. |
| ModelExpirationMinutes |Definisce il periodo di attesa prima della scadenza e della rimozione del modello in base all'ora dell'ultimo uso. L'impostazione predefinita è 60 minuti. |
| ScheduleRefreshTimeoutMinutes |Definisce il tempo necessario per l'aggiornamento dei dati per un modello. L'impostazione predefinita è 120 minuti. Non è previsto alcun limite massimo. |

**Impostazioni in rsreportserver.config:**

```
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Strumenti per la risoluzione dei problemi
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Log rilevanti per l'aggiornamento pianificato dei report di Power BI
I file di log che includono le informazioni sugli aggiornamenti pianificati sono i log RSPowerBI_. Si trovano nella cartella LogFiles del percorso di installazione del server di report. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Condizione di errore**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Aggiornamento riuscito***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Credenziali non corrette**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Abilitazione della registrazione dettagliata
La procedura di abilitazione della registrazione dettagliata nel server di report di Power BI è uguale a quella per SQL Server Reporting Services.

1. Aprire `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. In `<system.diagnostics>` impostare **DefaultTraceSwitch** su **4**.
3. In `<RStrace>` impostare **Componenti** su **all:4**. 

### <a name="executionlog"></a>ExecutionLog
Ogni volta che viene eseguito il rendering di un report di Power BI o viene eseguito un piano di aggiornamento pianificato, vengono aggiunte nuove voci al log di esecuzione nel database. Queste voci sono disponibili nella visualizzazione **ExecutionLog3** entro il database del catalogo del server di report.

Le voci del log di esecuzione per i report di Power BI sono diverse dalle voci per altri tipi di report.

* La colonna TimeRendering è sempre 0. Il rendering dei report di Power BI viene eseguito nel browser, non nel server.
* Sono disponibili due tipi di richieste e le successive azioni elemento:
  * **Interactive**: ogni volta che viene visualizzato un report.
    * **ASModelStream**: quando viene eseguito lo streaming del modello di dati in Analysis Services dal catalogo.
    * **ConceptualSchema**: quando un utente fa clic sul report per visualizzarlo.
    * **QueryData**: ogni volta che vengono richiesti dati dal client.
  * **Refresh Cache**: ogni volta che viene eseguito un piano di aggiornamento pianificato.
    * **ASModelStream**: ogni volta che viene eseguito lo streaming del modello di dati in Analysis Services dal catalogo.
    * **DataRefresh**: ogni volta che i dati vengono aggiornati da una o più origini dati.
    * **SaveToCatalog**: ogni volta che il modello di dati viene salvato nel catalogo.

## <a name="analysis-services"></a>Analysis Services
È possibile che in alcuni casi si voglia modificare Analysis Services per diagnosticare problemi o per modificare i limiti di memoria.

> [!IMPORTANT]
> Queste impostazioni verranno reimpostate ogni volta che si aggiorna il server di report. Assicurarsi di mantenere una copia delle modifiche e riapplicarle se necessario.
> 
> 

### <a name="install-location"></a>Percorso di installazione
Il percorso predefinito per il server di report di Power BI e Analysis Services è il seguente.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Configurazione delle impostazioni di Analysis Services (msmdsrv.ini)
Nella directory `<install directory>\PBIRS\ASEngine` è disponibile il file *msmdsrv.ini*, che consente di controllare diverse impostazioni di Analysis Services. Quando si apre questo file, si nota immediatamente che non include tutte le impostazioni che ci si aspetta nel file msmdsrv.ini. 

Ciò è dovuto al fatto che il processo effettivo di Analysis Services eseguito dal server di report di Power BI viene avviato in `<install directory>\PBIRS\ASEngine\workspaces`. In tale cartella è disponibile il file *msmdsrv.ini* completo a cui si è abituati. È importante non modificare il file nella cartella dell'area di lavoro, perché viene riscritto ogni volta che viene avviato il processo di Analysis Services. Se si vuole controllare un'impostazione, modificare il file msmdsrv.ini nella directory `<install directory>\PBIRS\ASEngine`.

Le impostazioni seguenti vengono ripristinate ogni volta che viene avviato il processo di Analysis Services. Eventuali modifiche apportate a queste impostazioni verranno ignorate.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Profilatura del processo locale di Analysis Services
Una traccia di SQL Profiler può essere eseguita nel processo locale di Analysis Services per finalità di diagnostica. Per connettersi all'istanza locale di Analysis Services, seguire questa procedura.

La traccia di SQL Server Profiler è inclusa nel [download di SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

1. Avviare **SQL Server Profiler** come amministratore.
2. Selezionare il pulsante **Nuova traccia**.
3. Nella finestra di dialogo **Connetti al server** selezionare **Analysis Services** e immettere **localhost:5132** come nome del server.
4. Nella finestra di dialogo **Proprietà traccia** selezionare gli eventi da acquisire e quindi selezionare **Esegui**.

## <a name="lock-pages-in-memory-windows-privilege"></a>Privilegio Blocco di pagine in memoria di Windows
Se non si riesce a eseguire il rendering di un report di Power BI, l'assegnazione del privilegio **Blocco di pagine in memoria** all'account del servizio che esegue il server di report di Power BI potrebbe consentire di risolvere il problema. Per altre informazioni sulla configurazione di **Blocco di pagine in memoria**, vedere [Privilegi di Windows assegnati all'account del servizio Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

