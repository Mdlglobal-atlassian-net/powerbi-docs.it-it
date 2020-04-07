---
title: Connettività e gestione dei set di dati con l'endpoint XMLA in Power BI Premium (anteprima)
description: Descrive come connettersi ai set di dati in Power BI Premium da applicazioni client e strumenti.
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/26/2020
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: fe349e9eb29f85315e568d5851ce8206186cb61b
ms.sourcegitcommit: bcc42e938fa28abe433287fecb9abb28c253b6bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2020
ms.locfileid: "80302538"
---
# <a name="dataset-connectivity-with-the-xmla-endpoint-preview"></a>Connettività ai set di dati con l'endpoint XMLA (anteprima)

Le aree di lavoro e i set di dati di Power BI Premium al livello di compatibilità 1500 e superiore supportano la connettività open platform da applicazioni client e strumenti Microsoft e di terze parti tramite un *endpoint XMLA*.

> [!NOTE]
> Questa funzionalità è disponibile in **anteprima**. Non è consigliabile usare le funzionalità in anteprima in un ambiente di produzione. Alcune funzionalità, il supporto e la documentazione sono limitati.  Per informazioni dettagliate, vedere [Condizioni dei servizi online Microsoft](https://www.microsoft.com/licensing/product-licensing/products?rtc=1).

## <a name="whats-an-xmla-endpoint"></a>Che cos'è un endpoint XMLA?

Power BI Premium usa il protocollo [XML for Analysis](https://docs.microsoft.com/analysis-services/xmla/xml-for-analysis-xmla-reference?view=power-bi-premium-current) (XMLA) per le comunicazioni tra le applicazioni client e il motore che gestisce le aree di lavoro e i set di dati di Power BI. Queste comunicazioni avvengono attraverso elementi comunemente chiamati endpoint XMLA. XMLA è lo stesso protocollo di comunicazione usato dal motore di Microsoft Analysis Services che esegue in background la modellazione semantica, la governance, il ciclo di vita e la gestione dei dati di Power BI.

Per impostazione predefinita, la connettività in *sola lettura* che usa l'endpoint è abilitata per il **carico di lavoro Set di dati** in una capacità. In sola lettura, le applicazioni e gli strumenti di visualizzazione dei dati possono eseguire query nei dati del modello, nei metadati, negli eventi e nello schema del set di dati. Le operazioni in *lettura/scrittura* che usano l'endpoint possono essere abilitate specificando gestione, governance, modellazione semantica avanzata, debug e monitoraggio del set di dati. Con la lettura/scrittura abilitata, i set di dati di Power BI Premium hanno maggiore parità con gli strumenti e i processi di modellazione tabulare a livello aziendale di Azure Analysis Services e SQL Server Analysis Services.

## <a name="data-modeling-and-management-tools"></a>Strumenti di gestione e modellazione dei dati

Di seguito sono descritti alcuni degli strumenti più comuni usati con Azure Analysis Services e SQL Server Analysis Services e ora supportati dai set di dati di Power BI Premium:

**Visual Studio con progetti di Analysis Services** : chiamato anche SQL Server Data Tools o semplicemente **SSDT** è uno strumento di creazione di livello aziendale per i modelli tabulari di Analysis Services. Le estensioni dei progetti di Analysis Services sono supportate in tutte le edizioni di Visual Studio 2017 e versioni successive, inclusa l'edizione Community gratuita. Per distribuire i modelli tabulari in un'area di lavoro Premium è necessaria la versione dell'estensione 2.9.6 o successiva. Quando si esegue la distribuzione in un'area di lavoro Premium, il modello deve avere un livello di compatibilità 1500 o superiore. La lettura/scrittura XMLA è necessaria per il carico di lavoro dei set di dati. Per altre informazioni, vedere [Strumenti per Analysis Services](https://docs.microsoft.com/analysis-services/tools-and-applications-used-in-analysis-services?view=power-bi-premium-current).

**SQL Server Management Studio (SSMS)**  : supporta le query DAX, MDX e XMLA. Eseguire operazioni di aggiornamento con granularità fine e script dei metadati del set di dati usando il linguaggio [TMSL (Tabular Model Scripting Language)](https://docs.microsoft.com/analysis-services/tmsl/tabular-model-scripting-language-tmsl-reference). La sola lettura è necessaria per le operazioni di query. Per i metadati di script è necessaria la lettura/scrittura. Richiede SSMS versione 18.4 o successiva. Il download è disponibile  [qui](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

**SQL Server Profiler** : installato con SSMS, questo strumento offre funzionalità di analisi e debug degli eventi dei set di dati. Sebbene sia stato deprecato ufficialmente per SQL Server, Profiler continua a essere incluso in SSMS e supportato per Analysis Services e Power BI Premium. È richiesta la sola lettura XMLA. Per altre informazioni, vedere  [SQL Server Profiler per Analysis Services](https://docs.microsoft.com/analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services?view=power-bi-premium-current).

**Distribuzione guidata Analysis Services** : installato con SSMS, questo strumento consente di distribuire i progetti di modelli tabulari creati di Visual Studio nelle aree di lavoro di Analysis Services e Power BI Premium. Può essere eseguito in modo interattivo o dalla riga di comando per l'automazione. È richiesta la lettura/scrittura XMLA. Per altre informazioni, vedere [Distribuzione guidata Analysis Services](https://docs.microsoft.com/analysis-services/deployment/deploy-model-solutions-using-the-deployment-wizard?view=power-bi-premium-current).

**Cmdlet di PowerShell** : i cmdlet di Analysis Services possono essere usati per automatizzare le attività di gestione dei set di dati, ad esempio le operazioni di aggiornamento. È richiesta la lettura/scrittura XMLA. È necessaria la versione **21.1.18221** o successiva del [modulo PowerShell SqlServer](https://www.powershellgallery.com/packages/SqlServer/). I cmdlet di Azure Analysis Services nel modulo Az.AnalysisServices non sono supportati per Power BI Premium. Per altre informazioni, vedere [Guida di riferimento a PowerShell per Analysis Services](https://docs.microsoft.com/analysis-services/powershell/analysis-services-powershell-reference?view=power-bi-premium-current).

**Power BI Report Builder** : strumento per la creazione di report impaginati. Creare una definizione di report che specifica i dati da recuperare, dove recuperarli e come visualizzarli. È possibile visualizzare in anteprima il report in Report Builder e quindi pubblicarlo nel servizio Power BI. È richiesta la sola lettura XMLA. Per altre informazioni, vedere  [Power BI Report Builder](https://docs.microsoft.com/power-bi/report-builder-power-bi).

**Tabular Editor**: strumento open source per la creazione, la manutenzione e la gestione dei modelli tabulari con un editor semplice e intuitivo. Una visualizzazione gerarchica mostra tutti gli oggetti del modello tabulare. Gli oggetti sono suddivisi in cartelle di visualizzazione con supporto per la modifica delle proprietà a selezione multipla e l'evidenziazione della sintassi DAX. La sola lettura XMLA è necessaria per le operazioni di query. Per le operazioni sui metadati è necessaria la lettura/scrittura. Per altre informazioni, vedere [tabulareditor.github.io](https://tabulareditor.github.io/).

**DAX Studio** : strumento open source per la creazione, la diagnosi, l'ottimizzazione delle prestazioni e l'analisi DAX. Le funzionalità includono l'esplorazione degli oggetti, la traccia integrata, la visualizzazione dell'esecuzione delle query con statistiche dettagliate, l'evidenziazione e la formattazione della sintassi DAX. La sola lettura XMLA è necessaria per le operazioni di query. Per altre informazioni, vedere  [daxstudio.org](https://daxstudio.org/).

**ALM Toolkit**: strumento open source per il confronto degli schemi per i set di dati di Power BI, usato più spesso per gli scenari di gestione del ciclo di vita delle applicazioni (ALM). Eseguire la distribuzione negli ambienti e mantenere i dati cronologici dell'aggiornamento incrementale. Differenziare e unire i file di metadati, i rami e i repository. Riutilizzare le definizioni comuni ai set di dati. La sola lettura è necessaria per le operazioni di query. Per le operazioni sui metadati è necessaria la lettura/scrittura. Per altre informazioni, vedere  [alm-toolkit.com](http://alm-toolkit.com/).

**Microsoft Excel**: le tabelle pivot di Excel sono uno degli strumenti più comuni usati per riepilogare, analizzare, esplorare e presentare dati di riepilogo di set di dati di Power BI. La sola lettura è necessaria per le operazioni di query. È richiesta la versione A portata di clic di Office 16.0.11326.10000 o successiva.

**Terze parti**: include applicazioni e strumenti di visualizzazione dei dati dei client che possono connettersi, eseguire query e usare i set di dati in Power BI Premium. La maggior parte degli strumenti richiede le versioni più recenti delle librerie client MSOLAP, ma alcuni possono usare ADOMD. L'endpoint XMLA di sola lettura o di lettura/scrittura varia a seconda delle operazioni.

### <a name="client-libraries"></a>Librerie client

Le applicazioni client non comunicano direttamente con l'endpoint XMLA. Usano invece *librerie client* come livello di astrazione. Si tratta delle stesse applicazioni delle librerie client usate per connettersi ad Azure Analysis Services e SQL Server Analysis Services. Le applicazioni Microsoft come Excel e SQL Server Management Studio (SSMS) e l'estensione dei progetti Analysis Services per Visual Studio installano tutte e tre le librerie client e le aggiornano con gli aggiornamenti periodici delle applicazioni e delle estensioni. Gli sviluppatori possono anche usare le librerie client per creare applicazioni personalizzate. In alcuni casi, in particolare con le applicazioni di terze parti, potrebbe essere necessario installare versioni più recenti delle librerie client, se non sono state installate con l'applicazione. Le librerie client vengono aggiornate ogni mese. Per altre informazioni, vedere  [Librerie client per la connessione ad Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="supported-write-operations"></a>Operazioni di scrittura supportate

I metadati del set di dati vengono esposti tramite le librerie client in base al modello a oggetti tabulare (TOM) per consentire agli sviluppatori di creare applicazioni personalizzate. In questo modo, Visual Studio e gli strumenti della community open source come Tabular Editor offrono funzionalità di modellazione e distribuzione dei dati aggiuntive supportate dal motore di Analysis Services ma non ancora supportate in Power BI Desktop. Le funzionalità di modellazione dei dati aggiuntive includono:

- [Gruppi di calcolo](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups?view=power-bi-premium-current) per il riutilizzo dei calcoli e l'uso semplificato dei modelli complessi.

- [Traduzioni dei metadati](https://docs.microsoft.com/analysis-services/tabular-models/translations-in-tabular-models-analysis-services?view=power-bi-premium-current) per il supporto di report e set di dati in più lingue.

- [Prospettive](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular?view=power-bi-premium-current) per la definizione di visualizzazioni mirate e specifiche del dominio aziendale dei metadati del set di dati.

La sicurezza a livello di oggetto non è ancora supportata nei set di dati di Power BI Premium.

## <a name="optimize-datasets-for-write-operations"></a>Ottimizzare i set di dati per le operazioni di scrittura

Quando si usa l'endpoint XMLA per la gestione dei set di dati con operazioni di scrittura, è consigliabile abilitare il set di dati per i modelli di grandi dimensioni. In questo modo si riduce il sovraccarico delle operazioni di scrittura, rendendole notevolmente più veloci. Per i set di dati con dimensioni superiori a 1 GB (dopo la compressione), la differenza può essere significativa. Per altre informazioni, vedere [Modelli di grandi dimensioni in Power BI Premium](service-premium-large-models.md).

## <a name="enable-xmla-read-write"></a>Abilitare la lettura/scrittura XMLA

Per impostazione predefinita, per una capacità Premium l'impostazione della proprietà dell'endpoint XMLA è abilitata per la sola lettura. Ciò significa che le applicazioni possono eseguire query solo su un set di dati. Per consentire alle applicazioni di eseguire operazioni di scrittura, è necessario che la proprietà dell'endpoint XMLA sia abilitata per la lettura/scrittura. L'impostazione della proprietà dell'endpoint XMLA per una capacità è configurata nel **carico di lavoro Set di dati**. L'impostazione dell'endpoint XMLA si applica a *tutte le aree di lavoro e a tutti i set di dati* assegnati alla capacità.

### <a name="to-enable-read-write-for-a-capacity"></a>Per abilitare la lettura/scrittura per una capacità

1. Nel portale di amministrazione fare clic su **Impostazioni di capacità** > **Power BI Premium** > nome della capacità.
2. Espandere **Carichi di lavoro**. Nell'impostazione **Endpoint XMLA** selezionare **Lettura/Scrittura**.

    ![Abilitare l'endpoint XMLA](media/service-premium-connect-tools/xmla-endpoint-enable.png)

## <a name="connecting-to-a-premium-workspace"></a>Connessione a un'area di lavoro Premium

Le aree di lavoro assegnate a una capacità dedicata includono una stringa di connessione in formato URL come `powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]`.

Le applicazioni che si connettono all'area di lavoro usano l'URL come nome del server di Analysis Services. Ad esempio: `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`.

Gli utenti con UPN nello stesso tenant (non B2B) possono sostituire il nome del tenant con `myorg`. Ad esempio,  `powerbi://api.powerbi.com/v1.0/myorg/Sales Workspace`.

### <a name="to-get-the-workspace-connection-url"></a>Per ottenere l'URL di connessione dell'area di lavoro

Nell'area di lavoro in **Impostazioni** > **Premium** > **Connessione all'area di lavoro** fare clic su **Copia**.

![Stringa di connessione all'area di lavoro](media/service-premium-connect-tools/xmla-endpoint-workspace-connection.png)

## <a name="connection-requirements"></a>Requisiti di connessione

### <a name="initial-catalog"></a>Catalogo iniziale

Per alcuni strumenti, ad esempio SQL Server Profiler, può essere necessario specificare un *Catalogo iniziale*. Specificare un set di dati (database) nell'area di lavoro. Nella finestra di dialogo **Connetti al server** fare clic su **Opzioni** > **Proprietà connessione** > **Connetti al database** e immettere il nome del set di dati.

### <a name="duplicate-workspace-names"></a>Nomi di area di lavoro duplicati

Le [nuove aree di lavoro](service-new-workspaces.md) (create usando la nuova esperienza di area di lavoro) in Power BI impongono la convalida per impedire la creazione o la ridenominazione delle aree di lavoro con nomi duplicati. Le aree di lavoro di cui non è stata eseguita la migrazione possono causare nomi duplicati. Quando si stabilisce la connessione a un'area di lavoro con lo stesso nome di un'altra area di lavoro, è possibile che venga visualizzato l'errore seguente:

**Non è possibile connettersi a powerbi://api.powerbi.com/v1.0/[nome tenant]/[nome area di lavoro].**

Per risolvere questo errore, oltre al nome dell'area di lavoro, specificare ObjectIDGuid che può essere copiato da objectID dell'area di lavoro nell'URL. Aggiungere objectID alla fine dell'URL di connessione. Ad esempio,  
'powerbi://api.powerbi.com/v1.0/myorg/Contoso Sales - 9d83d204-82a9-4b36-98f2-a40099093830'.

### <a name="duplicate-dataset-name"></a>Nome del set di dati duplicato

Quando ci si connette a un set di dati con lo stesso nome di un altro set di dati nella stessa area di lavoro, aggiungere il GUID del set di dati al nome del set di dati. È possibile ottenere il nome e il GUID del set di dati quando si è connessi all'area di lavoro in SSMS.

### <a name="delay-in-datasets-shown"></a>Ritardo della visualizzazione dei set di dati

Quando si stabilisce una connessione a un'area di lavoro, la visualizzazione delle modifiche dei set di dati nuovi, eliminati e rinominati può richiedere alcuni minuti.

### <a name="unsupported-datasets"></a>Set di dati non supportati

I set di dati seguenti non sono accessibili tramite l'endpoint XMLA. I set di dati seguenti non verranno visualizzati nell'area di lavoro in SSMS o in altri strumenti:

- Set di dati basati su una connessione dinamica a un modello di Azure Analysis Services o SQL Server Analysis Services. 
- Set di dati basati su una connessione dinamica a un set di dati di Power BI in un'altra area di lavoro. Per altre informazioni, vedere [Introduzione ai set di dati in aree di lavoro diverse](service-datasets-across-workspaces.md).
- Set di dati con dati push tramite l'API REST.
- Se di dati delle cartelle di lavoro di Excel.

## <a name="security"></a>Sicurezza

Oltre alla proprietà dell'endpoint XMLA abilitata per la lettura/scrittura da parte dell'amministratore della capacità, è necessario abilitare l'impostazione **Esporta dati** a livello di tenant nel portale di amministrazione di Power BI, necessaria anche per l'analisi in Excel.

![Abilitare Esporta dati](media/service-premium-connect-tools/xmla-endpoint-export-data.png)

L'accesso tramite l'endpoint XMLA rispetta l'appartenenza a gruppi di sicurezza impostati a livello di area di lavoro o app.

I collaboratori dell'area di lavoro e i ruoli superiori hanno accesso in scrittura al set di dati e sono pertanto equivalenti agli amministratori di database di Analysis Services. Possono distribuire nuovi set di dati da Visual Studio ed eseguire script TMSL in SSMS.

Le operazioni che richiedono le autorizzazioni di amministratore del server di Analysis Services, anziché dell'amministratore del database, ad esempio le tracce a livello di server e la rappresentazione utente tramite la proprietà della stringa di connessione [EffectiveUserName](https://docs.microsoft.com/analysis-services/instances/connection-string-properties-analysis-services?view=power-bi-premium-current#bkmk_auth) non sono attualmente supportate in Power BI Premium.

Gli altri utenti che hanno l'[autorizzazione di creazione](service-datasets-build-permissions.md) per un set di dati sono equivalenti ai lettori di database di Analysis Services. Possono connettersi ai set di dati e visualizzarli per l'uso e la visualizzazione dei dati. Le regole di sicurezza a livello di riga vengono rispettate e non possono visualizzare i metadati interni del set di dati.

### <a name="model-roles"></a>Ruoli del modello

I metadati del set di dati tramite l'endpoint XMLA possono creare, modificare o eliminare i ruoli del modello da un set di dati, inclusa l'impostazione di filtri di sicurezza a livello di riga. I ruoli del modello in Power BI vengono usati solo per la sicurezza a livello di riga. Usare il modello di sicurezza di Power BI per controllare le autorizzazioni oltre la sicurezza a livello di riga.

Quando si usano i ruoli del set di dati tramite l'endpoint XMLA, si applicano le limitazioni seguenti:

- **Durante l'anteprima pubblica non è possibile specificare l'appartenenza ai ruoli per un set di dati usando l'endpoint XMLA**. In alternativa, specificare i membri del ruolo nella pagina Sicurezza a livello di riga per un set di dati nel servizio Power BI.
- L'unica autorizzazione per un ruolo che può essere impostata per i set di dati di Power BI è l'autorizzazione Lettura. Per l'accesso in lettura tramite l'endpoint XMLA è necessaria l'autorizzazione di compilazione per un set di dati, indipendentemente dall'esistenza dei ruoli del set di dati. Usare il modello di sicurezza di Power BI per controllare le autorizzazioni oltre la sicurezza a livello di riga.
- Le regole di sicurezza a livello di oggetto non sono attualmente supportate in Power BI.

### <a name="setting-data-source-credentials"></a>Impostazione delle credenziali dell'origine dati

I metadati specificati tramite l'endpoint XMLA possono creare connessioni alle origini dati, ma non possono impostare le credenziali dell'origine dati. In alternativa, è possibile impostare le credenziali nella pagina Impostazioni set di dati del servizio Power BI.

### <a name="service-principals"></a>Entità servizio

Durante l'anteprima pubblica, la connessione con l'endpoint XMLA tramite un'[entità servizio](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals) per gli scenari di automazione non è ancora supportata.

## <a name="deploy-model-projects-from-visual-studio-ssdt"></a>Distribuire progetti di modello da Visual Studio (SSDT)

La distribuzione di un progetto di modello tabulare in Visual Studio in un'area di lavoro di Power BI Premium è molto simile alla distribuzione in un server Azure o SQL Server Analysis Services. Le uniche differenze si trovano nella proprietà Server di distribuzione specificata per il progetto e nella modalità con cui vengono specificate le credenziali dell'origine dati in modo che le operazioni di elaborazione possano importare dati dalle origini dati nel nuovo set di dati nell'area di lavoro.

> [!IMPORTANT]
> Durante l'anteprima pubblica, le appartenenze ai ruoli non possono essere specificate dagli strumenti che usano l'endpoint XMLA. Se la distribuzione del progetto di modello non riesce, assicurarsi che non siano stati specificati utenti nei ruoli. Al termine della distribuzione del modello, specificare gli utenti per i ruoli del set di dati nel servizio Power BI. Per altre informazioni, vedere [Ruoli del modello](#model-roles) in questo articolo.

Per distribuire un progetto di modello tabulare creato in Visual Studio, è necessario innanzitutto impostare l'URL di connessione dell'area di lavoro nella proprietà **Server di distribuzione** del progetto. In Visual Studio in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto > **Proprietà**. Nella proprietà **Server** incollare l'URL di connessione dell'area di lavoro.

![Proprietà di distribuzione](media/service-premium-connect-tools/xmla-endpoint-ssdt-deploy-property.png)

Dopo aver specificato la proprietà Server di distribuzione, è possibile distribuire il progetto.

**Quando viene distribuito per la prima volta**, viene creato un set di dati nell'area di lavoro usando i metadati di model.bim. Nell'ambito dell'operazione di distribuzione, dopo che il set di dati è stato creato nell'area di lavoro dai metadati del modello, l'elaborazione per caricare i dati nel set di dati dalle origini dati avrà esito negativo.

L'elaborazione non riesce perché, a differenza di quando si esegue la distribuzione in un'istanza di Azure o SQL Server Analysis Server in cui le credenziali dell'origine dati vengono richieste come parte dell'operazione di distribuzione, quando si distribuisce in un'area di lavoro Premium le credenziali dell'origine dati non possono essere specificate durante l'operazione di distribuzione. Al contrario, dopo la distribuzione dei metadati e la creazione del set di dati, le credenziali dell'origine dati vengono specificate nel servizio Power BI nelle impostazioni del set di dati. Nell'area di lavoro fare clic su **Set di dati** > **Impostazioni** > **Credenziali origine dati** > **Modifica credenziali**.

![Credenziali origine dati](media/service-premium-connect-tools/xmla-endpoint-datasource-credentials.png)

Quando vengono specificate le credenziali dell'origine dati, è possibile aggiornare il set di dati nel servizio Power BI, configurare l'aggiornamento pianificato o elaborare (aggiornare) da SQL Server Management Studio per caricare i dati nel set di dati.

Viene applicata la proprietà **Opzione di elaborazione** della distribuzione specificata nel progetto in Visual Studio. Tuttavia, se non sono state ancora specificate le credenziali per un'origine dati nel servizio Power BI, anche se la distribuzione dei metadati viene eseguita correttamente, l'elaborazione avrà esito negativo. È possibile impostare la proprietà su **Non elaborare**, impedendo un tentativo di elaborazione come parte della distribuzione, ma potrebbe essere necessario reimpostare la proprietà su **Predefinito** poiché dopo aver specificato le credenziali dell'origine dati nelle impostazioni dell'origine dati per il nuovo set di dati, l'elaborazione come parte delle successive operazioni di distribuzione avrà esito positivo.

## <a name="connect-with-ssms"></a>Connettersi a SSMS

L'uso di SSMS per connettersi a un'area di lavoro è analogo alla connessione a un server di Azure o SQL Server Analysis Services. L'unica differenza è rappresentata dall'impostazione dell'URL dell'area di lavoro nel nome del server e dalla necessità di usare l'autenticazione **Active Directory - Universale con supporto MFA**.

### <a name="connect-to-a-workspace-by-using-ssms"></a>Connettersi a un'area di lavoro usando SSMS

1. In SQL Server Management Studio fare clic su **Connetti** > **Connetti al server**.

2. In **Tipo di server** selezionare **Analysis Services**. In **Nome server** immettere l'URL dell'area di lavoro. In **Autenticazione** selezionare **Active Directory - Universale con supporto MFA** e quindi in **Nome utente** immettere l'ID utente dell'organizzazione.

    ![Connettersi al server in SSMS](media/service-premium-connect-tools/xmla-endpoint-connect-server.png)

Dopo aver stabilito la connessione, l'area di lavoro viene visualizzata come server di Analysis Services e i set di dati dell'area di lavoro sono visualizzati come database.  

![SSMS](media/service-premium-connect-tools/xmla-endpoint-ssms.png)

Per altre informazioni sull'uso di SSMS per generare script per i metadati, vedere [Creare script di Analysis Services](https://docs.microsoft.com/analysis-services/instances/create-analysis-services-scripts-in-management-studio?view=power-bi-premium-current) e [TMSL (Tabular Model Scripting Language)](https://docs.microsoft.com/analysis-services/tmsl/tabular-model-scripting-language-tmsl-reference?view=power-bi-premium-current).

## <a name="dataset-refresh"></a>Aggiornamento del set di dati

L'endpoint XMLA offre un'ampia gamma di scenari per le funzionalità di aggiornamento con granularità fine che usano SSMS, l'automazione con PowerShell, [Automazione di Azure](https://docs.microsoft.com/azure/automation/automation-intro) e [Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview) con TOM. È possibile, ad esempio, aggiornare alcune partizioni cronologiche di [aggiornamento incrementale](service-premium-incremental-refresh.md) senza dover ricaricare tutti i dati cronologici.

A differenza della configurazione dell'aggiornamento nel servizio Power BI, le operazioni di aggiornamento tramite l'endpoint XMLA non sono limitate a 48 aggiornamenti al giorno e il [timeout di aggiornamento pianificato](refresh-troubleshooting-refresh-scenarios.md#scheduled-refresh-timeout) non viene imposto.

## <a name="dynamic-management-views-dmv"></a>DMV (Dynamic Management View)

Le [DMV](https://docs.microsoft.com/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) di Analysis Services garantiscono la visibilità dei metadati del set di dati, della derivazione e dell'utilizzo delle risorse. Le DMV disponibili per l'esecuzione di query in Power BI tramite l'endpoint XMLA sono limitate al massimo a quelle che richiedono autorizzazioni di amministratore di database. Alcune DMV, ad esempio, non sono accessibili poiché richiedono le autorizzazioni di amministratore del server di Analysis Services.

## <a name="power-bi-desktop-authored-datasets"></a>Set di dati creati di Power BI Desktop

### <a name="enhanced-metadata"></a>Metadati avanzati

Per le operazioni di scrittura XMLA nei set di dati creati in Power BI Desktop e pubblicati in un'area di lavoro Premium è necessario abilitare i metadati avanzati. Per altre informazioni, vedere [Metadati dei set di dati avanzati](desktop-enhanced-dataset-metadata.md).

> [!CAUTION]
> Attualmente, un'operazione di scrittura in un set di dati creato in Power BI Desktop ne impedisce il download come file PBIX. Assicurarsi di conservare il file PBIX originale.

### <a name="data-source-declaration"></a>Dichiarazione dell'origine dati

Quando si stabilisce una connessione alle origini dati e si esegue una query sui dati, Power BI Desktop usa le espressioni Power Query M come dichiarazioni di origini dati inline. Sebbene sia supportata nelle aree di lavoro di Power BI Premium, la dichiarazione dell'origine dati inline Power Query M non è supportata da Azure Analysis Services o SQL Server Analysis Services. Al contrario, gli strumenti di modellazione dei dati di Analysis Services, ad esempio Visual Studio, creano metadati usando dichiarazioni di origine dati *strutturate* e/o *provider*. Con l'endpoint XMLA, Power BI Premium supporta anche origini dati strutturate e provider, ma non come parte delle dichiarazioni di origini dati inline Power Query M nei modelli di Power BI Desktop. Per altre informazioni, vedere [Informazioni sui provider](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource#understanding-providers).

### <a name="power-bi-desktop-in-live-connect-mode"></a>Power BI Desktop in modalità Live Connect

Power BI Desktop è in grado di connettersi a un set di dati di Power BI Premium come un database modello distribuito in Azure Analysis Services o SQL Server Analysis Services. In questo caso, Power BI Desktop usa l'endpoint XMLA. Tuttavia, è consigliabile che gli utenti di Power BI Desktop usino la funzionalità Live Connect creata appositamente per i set di dati di Power BI. L'uso di Live Connect offre un'esperienza di individuazione migliorata che mostra il livello di verifica dell'autenticità dei set di dati e gli utenti non devono tenere traccia degli URL dell'area di lavoro ma possono semplicemente digitare il nome del set di dati. Per altre informazioni, vedere [Connettersi ai set di dati nel servizio Power BI da Power BI Desktop](desktop-report-lifecycle-datasets.md).

## <a name="audit-logs"></a>Log di controllo

Quando le applicazioni si connettono a un'area di lavoro, l'accesso tramite gli endpoint XMLA viene registrato nei log di controllo di Power BI con le operazioni seguenti:

|Nome descrittivo dell'operazione   |Nome operazione   |
|---------|---------|
|Connesso al set di dati di Power BI da un'applicazione esterna      |  ConnectFromExternalApplication        |
|Aggiornamento del set di dati di Power BI richiesto da un'applicazione esterna      | RefreshDatasetFromExternalApplication        |
|Set di dati di Power BI creato da un'applicazione esterna      |  CreateDatasetFromExternalApplication        |
|Sei di dati di Power BI modificato da un'applicazione esterna     |  EditDatasetFromExternalApplication        |
|Set di dati di Power BI eliminato da un'applicazione esterna      |  DeleteDatasetFromExternalApplication        |

Per altre informazioni, vedere  [Controllo di Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Vedere anche

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
