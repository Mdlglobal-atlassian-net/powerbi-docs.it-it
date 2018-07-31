---
title: Novità del Server di report di Power BI
description: Informazioni sulle novità del Server di report di Power BI. Questa sezione riguarda le funzionalità principali e viene aggiornata con il rilascio di nuovi elementi.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: maggies
ms.openlocfilehash: 07c393425d2a04376a4fcf81c2c35a0e115eeaee
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34481959"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novità del Server di report di Power BI
Informazioni sulle novità del Server di report di Power BI. Questa sezione riguarda le funzionalità principali e viene aggiornata con il rilascio di nuovi elementi.

Per scaricare il server di report di Power BI e Power BI Desktop ottimizzati per il server di report di Power BI, visitare [Creazione di report in locale con il server di report di Power BI](https://powerbi.microsoft.com/report-server/).

Consultare queste fonti per tenersi aggiornati sulle nuove funzionalità di Server di report di Power BI.

* [Blog di Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blog del team Server SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* Il [canale YouTube Guy in a Cube](https://aka.ms/guyinacube)

Per informazioni sulle "Novità" di Power BI, vedere:

* [Novità del servizio Power BI](../service-whats-new.md)
* [Novità di Power BI Desktop](../desktop-latest-update.md)
* [Novità delle app per dispositivi mobili per Power BI](../mobile-whats-new-in-the-mobile-apps.md)

## <a name="may-2018"></a>Maggio 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Configurare le app per dispositivi mobili iOS di Power BI per server di report in modalità remota

In qualità di amministratori IT, è ora possibile usare lo strumento MDM dell'organizzazione per configurare in modalità remota l'accesso delle app per dispositivi mobili iOS di Power BI a un server di report. Per informazioni dettagliate, vedere [Configurare l'accesso delle app per dispositivi mobili iOS di Power BI in modalità remota](configure-powerbi-mobile-apps-remote.md).

## <a name="march-2018-release"></a>Versione di marzo 2018

La versione di marzo 2018 presenta molte nuove funzionalità aggiunte alla versione di Power BI Desktop ottimizzate per Server di report di Power BI. Sono riportate di seguito, suddivise per area: 
- [Oggetti visivi](#visuals-updates)
- [Creazione di report](#reporting)
- [Analisi](#analytics)
- [Prestazioni](#performance)
- [Server di report](#report-server)
- [Altro](#other-improvements)

### <a name="highlights-of-this-release"></a>Caratteristiche principali di questa versione

Nel lungo elenco di nuove funzionalità emergono quelle riportate di seguito, particolarmente interessanti.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Formattazione condizionale basata su regole per oggetti visivi tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)
 
Permette di creare regole per applicare colore in modo condizionale allo sfondo o al carattere di una colonna in base a una specifica logica di business in una tabella o matrice.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Mostrare e nascondere pagine](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Talvolta si desidera che i lettori accedano al report, ma alcune delle pagine non sono ancora finite; ora è possibile nasconderle fino a quando non saranno pronte. In alternativa, è possibile nascondere le pagine dalla consultazione normale e i lettori potranno accedere alla pagina tramite segnalibri o drill-through.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Aggiunta di segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Per quanto riguarda i segnalibri, è possibile creare segnalibri in modo da fare una sintesi con i dati del report.

- [Evidenziazione incrociata per i segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): i segnalibri gestiscono e visualizzano lo stato di evidenziazione incrociata della pagina del report nel momento in cui è stato creato il segnalibro.
- [Più flessibilità nei segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): i segnalibri riflettono le proprietà definite nel report e influiscono solo sugli oggetti visivi scelti.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Selezione multipla di punti dati in più grafici](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selezionare più punti dati in più grafici e applicare il filtro incrociato all'intera pagina.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Sincronizzazione dei filtri dei dati tra più pagine di un report](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

È possibile applicare un filtro dei dati a una, due o più pagine in un report.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Misure rapide](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Creare nuove misure basate su misure e colonne numeriche esistenti in una tabella.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Drill-down di filtri su altri oggetti visivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Quando si esegue il drill-down in una categoria specificata in un oggetto visivo, è possibile che filtri tutti gli oggetti visivi nella pagina in base alla stessa categoria.

### <a name="visuals-updates"></a>Aggiornamenti di oggetti visivi

- [Allineamento delle celle per tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Visualizzazione di unità e controllo di precisione per colonne tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Overflow delle etichette dati per gli oggetti visivi grafici a barre e istogrammi](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Controllo del colore di sfondo delle etichette dati per oggetti visivi cartesiani e mappe](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Controllo del riempimento di barre/colonne](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Incremento dell'area usata per le etichette degli assi nei grafici](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Oggetto visivo a dispersione da raggruppamenti dell'asse x e y](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Campionamento ad alta densità per le mappe in base a latitudine e longitudine](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Filtri dei dati reattivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Aggiunta di una data di ancoraggio a un filtro dei dati per la data relativa](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Reporting

- [Disattivare l'intestazione dell'oggetto visivo in modalità di lettura per un report](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Opzioni del report per le origini dati lente](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Posizionamento migliorato degli oggetti visivi predefiniti](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Controllo dell'ordinamento degli oggetti visivi attraverso il riquadro di selezione](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Blocco di oggetti nel report](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Ricerca nei riquadri formattazione e analisi](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Riquadro delle proprietà del campo e descrizioni del campo](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>flusso

- [UTCNOW() e UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Contrassegnare una tabella con data personalizzata](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Applicare filtri di drill su altri oggetti visivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formattazione a livello di cella per modelli multidimensionali di Analysis Services (AS) per schede con più righe](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)
 
### <a name="performance"></a>Performance

- [Miglioramenti delle prestazioni del filtro](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Miglioramenti delle prestazioni di DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Miglioramenti delle prestazioni di apertura e salvataggio](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Miglioramenti per "Mostra elementi senza dati"](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)
 
### <a name="report-server"></a>Server di report 

#### <a name="export-to-accessible-pdf"></a>Esportare in formato PDF accessibile

Quando si esporta un report impaginato (RDL) in formato PDF, è possibile ottenere un file PDF accessibile/con tag. Ha dimensioni maggiori ma è più agevole la sua lettura e consultazione tramite lettori a schermo e altre tecnologie per l'accesso facilitato. Il PDF accessibile si abilita impostando le informazioni sul dispositivo **PDF accessibile** su **True**. Vedere [Impostazioni relative alle informazioni sul dispositivo PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) e [Changing Device Information Settings](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings) (Modifica delle impostazioni sul dispositivo).


### <a name="other-improvements"></a>Altri miglioramenti

- [Aggiungere una colonna da miglioramenti di esempi](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Collegamento veloce a Servizi di consulenza](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Segnalazione errori migliorata](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Visualizzare gli errori precedentemente riscontrati](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

 
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
[Che cos'è Server di report di Power BI?](get-started.md) 
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Installare il server di report di Power BI](install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

