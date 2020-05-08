---
title: Aggiornamento dei dati in Power BI
description: Questo articolo descrive le funzionalità di aggiornamento dei dati di Power BI e le relative dipendenze a livello concettuale.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/26/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: e51361d910c558824f33fb9ed00f6332aa3bba07
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "81440033"
---
# <a name="data-refresh-in-power-bi"></a>Aggiornamento dei dati in Power BI

Power BI consente di passare rapidamente dai dati alle informazioni dettagliate e all'azione, ma è necessario verificare che i dati nei report e nei dashboard di Power BI siano recenti. Sapere come si devono aggiornare i dati spesso è essenziale per ottenere risultati precisi.

Questo articolo descrive le funzionalità di aggiornamento dei dati di Power BI e le relative dipendenze a livello concettuale. Contiene inoltre procedure consigliate e suggerimenti che consentono di evitare i problemi di aggiornamento più comuni. Il contenuto offre una base utile per la comprensione del funzionamento dell'aggiornamento dei dati. Per istruzioni dettagliate mirate per la configurazione dell'aggiornamento dei dati, vedere le esercitazioni e le guide pratiche elencate nella sezione Passaggi successivi alla fine di questo articolo.

## <a name="understanding-data-refresh"></a>Informazioni sull'aggiornamento dei dati

Ogni volta che si aggiornano i dati, Power BI deve eseguire una query sulle origini dati sottostanti, se possibile caricare i dati di origine in un set di dati e quindi aggiornare tutte le visualizzazioni nei report o dashboard che si basano sul set di dati aggiornato. L'intero processo è costituito da più fasi, a seconda delle modalità di archiviazione dei set di dati, come illustrato nelle sezioni seguenti.

Per capire in che modo Power BI aggiorna i set di dati, i report e i dashboard, è necessario conoscere i concetti seguenti:

- **Modalità di archiviazione e tipi di set di dati**: Le modalità di archiviazione e i tipi di set di dati supportati da Power BI hanno requisiti di aggiornamento diversi. È possibile scegliere tra la reimportazione dei dati in Power BI per visualizzare eventuali modifiche apportate e l'esecuzione di query sui dati direttamente nell'origine.
- **Tipi di aggiornamento di Power BI**: Indipendentemente dalle specifiche del set di dati, conoscere i vari tipi di aggiornamento aiuta a capire dove potrebbe impiegare il proprio tempo Power BI durante un'operazione di aggiornamento. E la combinazione di questi dettagli con le specifiche della modalità di archiviazione consente di capire esattamente che operazioni esegue Power BI quando si seleziona **Aggiorna ora** per un set di dati.

### <a name="storage-modes-and-dataset-types"></a>Modalità di archiviazione e tipi di set di dati

Un set di dati di Power BI può funzionare in una delle seguenti modalità per accedere ai dati da un'ampia gamma di origini dati. Per altre informazioni, vedere [Modalità di archiviazione in Power BI Desktop](desktop-storage-mode.md).

- Modalità importazione
- Modalità DirectQuery
- Modalità LiveConnect
- Modalità push

Il diagramma seguente illustra i diversi flussi di dati, in base alla modalità di archiviazione. Il punto più significativo è che solo i set di dati in modalità importazione richiedono un aggiornamento dei dati di origine. L'aggiornamento è necessario perché solo questo tipo di set di dati importa i dati dalle proprie origini dati e i dati importati potrebbero essere aggiornati a intervalli regolari o ad hoc. I set di dati di DirectQuery e i set di dati in modalità LiveConnect per Analysis Services non importano i dati, ma eseguono query sull'origine dati sottostante ad ogni interazione dell'utente. I set di dati in modalità push non accedono direttamente alle origini dati ma attendono il push dei dati in Power BI da parte dell'utente. I requisiti di aggiornamento dei set di dati variano a seconda del tipo di modalità di archiviazione e set di dati.

![Modalità di archiviazione e tipi di set di dati](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Set di dati in modalità importazione

Power BI importa i dati dalle origini dati originali nel set di dati. Le query di report e dashboard di Power BI eseguite sul set di dati restituiscono i risultati dalle tabelle e dalle colonne importate. È possibile considerare questo set di dati una copia temporizzata. Poiché Power BI copia i dati, è necessario aggiornare il set di dati per recuperare le modifiche dalle origini dati sottostanti.

Power BI memorizza i dati nella cache, quindi le dimensioni dei set di dati in modalità importazione possono essere significative. Fare riferimento alla tabella seguente per le dimensioni massime dei set di dati per ogni capacità. Mantenere le dimensioni dei set di dati ben al di sotto dei valori massimi per evitare problemi di aggiornamento che potrebbero verificarsi se i set di dati richiedono un numero di risorse superiore alla quantità massima disponibile durante un'operazione di aggiornamento.

| Tipo di capacità | Dimensione massima set di dati |
| --- | --- |
| Condiviso, A1, A2 o A3 | 1 GB |
| A4 o P1 | 3 GB |
| A5 o P2 | 6 GB |
| A6 o P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>Set di dati in modalità DirectQuery/LiveConnect

Power BI non importa i dati su connessioni che funzionano in modalità DirectQuery/LiveConnect. In questo caso il set di dati restituisce i risultati dall'origine dati sottostante ogni volta che un report o un dashboard esegue una query sul set di dati. Power BI trasforma e inoltra le query all'origine dati.

Anche se la modalità DirectQuery e la modalità LiveConnect sono simili per il fatto che Power BI inoltra le query all'origine, è importante notare che Power BI non deve trasformare le query in modalità LiveConnect. Le query passano direttamente all'istanza di Analysis Services che ospita il database senza consumare risorse nella capacità condivisa o in una capacità Premium.

Poiché Power BI non importa i dati, non è necessario eseguire un aggiornamento dei dati. Tuttavia, Power BI esegue comunque gli aggiornamenti dei riquadri e possibilmente gli aggiornamenti dei report, come illustra la sezione successiva sui tipi di aggiornamento. Un riquadro è un oggetto visivo del report aggiunto a un dashboard e gli aggiornamenti dei riquadri del dashboard vengono eseguiti circa ogni ora in modo che nei riquadri siano visualizzati risultati recenti. È possibile modificare la pianificazione nelle impostazioni del set di dati, come illustra lo screenshot seguente, oppure forzare un aggiornamento del dashboard manualmente usando l'opzione **Aggiorna ora**.

![Pianificare gli aggiornamenti](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> La sezione **Aggiornamento pianificato della cache** della scheda **Set di dati** non è disponibile per i set di dati in modalità importazione. Questi set di dati non richiedono un aggiornamento separato dei riquadri poiché Power BI aggiorna automaticamente i riquadri durante ogni aggiornamento dei dati pianificato o su richiesta.

#### <a name="push-datasets"></a>Set di dati di push

I set di dati di push non contengono una definizione formale di un'origine dati, quindi non richiedono l'esecuzione di un aggiornamento dei dati in Power BI. Per aggiornarli, eseguire il push dei dati nel set di dati usando un processo o servizio esterno, ad esempio Analisi di flusso di Azure. Si tratta di un approccio comune le analisi in tempo reale con Power BI. Power BI esegue comunque gli aggiornamenti della cache per tutti i riquadri usati per un set di dati di push. Per una procedura dettagliata, vedere l'[esercitazione: Analisi di flusso e Power BI: un dashboard di analisi in tempo reale per il flusso di dati](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> La modalità push presenta diverse limitazioni, come spiegato in [Limitazioni dell'API REST di Power BI](developer/automation/api-rest-api-limitations.md).

### <a name="power-bi-refresh-types"></a>Tipi di aggiornamento di Power BI

Un'operazione di aggiornamento di Power BI può essere costituita da più tipi di aggiornamento, tra cui l'aggiornamento dei dati, l'aggiornamento OneDrive, l'aggiornamento delle cache delle query, l'aggiornamento dei riquadri e l'aggiornamento degli oggetti visivi dei report. Benché Power BI determini automaticamente le procedure di aggiornamento necessarie per un determinato set di dati, è necessario sapere come tali procedure contribuiscono alla complessità e alla durata di un'operazione di aggiornamento. Per un riferimento rapido, vedere la tabella seguente.

| Modalità di archiviazione | Aggiornamento dati | Aggiornamento OneDrive | Cache delle query | Aggiornamento del riquadro | Oggetti visivi del report |
| --- | --- | --- | --- | --- | --- |
| Importa | Pianificato e su richiesta | Sì, per i set di dati connessi | Se abilitato per la capacità Premium | Automaticamente e su richiesta | No |
| DirectQuery | Non applicabile | Sì, per i set di dati connessi | Se abilitato per la capacità Premium | Automaticamente e su richiesta | No |
| LiveConnect | Non applicabile | Sì, per i set di dati connessi | Se abilitato per la capacità Premium | Automaticamente e su richiesta | Sì |
| Push | Non applicabile | Non applicabile | Non pratico | Automaticamente e su richiesta | No |
| | | | | | |

#### <a name="data-refresh"></a>Aggiornamento dati

Per gli utenti di Power BI aggiornare i dati in genere significa importare i dati dalle origini dati originali in un set di dati, in base a un aggiornamento pianificato o su richiesta. È possibile eseguire più aggiornamenti del set di dati ogni giorno, operazione che potrebbe essere necessaria se i dati di origine sottostanti cambiano di frequente. Power BI limita i set di dati nella capacità condivisa a otto aggiornamenti al giorno. Se il set di dati si trova in una capacità Premium, è possibile pianificare fino a 48 aggiornamenti al giorno nelle impostazioni dei set di dati. Per altre informazioni, vedere [Configurare l'aggiornamento pianificato](#configure-scheduled-refresh) più avanti in questo articolo. I set di dati in una capacità Premium con l'[endpoint XMLA](service-premium-connect-tools.md) abilitato per la lettura/scrittura supportano operazioni di aggiornamento illimitate se configurati a livello di codice con TMSL o PowerShell.

È anche importante sottolineare che il limite di capacità condivisa per gli aggiornamenti giornalieri è valido sia per gli aggiornamenti pianificati che per quelli delle API e per le combinazioni dei due tipi. È anche possibile attivare un aggiornamento su richiesta selezionando **Aggiorna ora** nel menu del set di dati, come illustra lo screenshot seguente. Gli aggiornamenti su richiesta non sono inclusi nella limitazione dell'aggiornamento. Si noti anche che i set in dati di una capacità Premium non impongono limitazioni per gli aggiornamenti dell'API. Se si è interessati a realizzare una propria soluzione di aggiornamento usando l'API REST di Power BI, vedere [Set di dati - Aggiornare i set di dati](/rest/api/power-bi/datasets/refreshdataset).

![Aggiorna adesso](media/refresh-data/refresh-now.png)

> [!NOTE]
> Gli aggiornamenti dei dati devono essere completati in meno di 2 ore nella capacità condivisa. Se i set di dati richiedono operazioni di aggiornamento più lunghe, si consiglia di spostare il set di dati in una capacità Premium. Nella versione Premium la durata massima dell'aggiornamento è 5 ore.

#### <a name="onedrive-refresh"></a>Aggiornamento OneDrive

Se i set di dati e i report sono stati creati in base a un file di Power BI Desktop, una cartella di lavoro di Excel o un file con valori delimitati da virgole (CSV) in OneDrive o SharePoint Online, Power BI esegue un altro tipo di aggiornamento, noto come aggiornamento OneDrive. Per altre informazioni, vedere [Ottenere dati dai file per Power BI](service-get-data-from-files.md).

A differenza di un aggiornamento di set di dati durante il quale Power BI importa i dati da un'origine dati in un set di dati, l'aggiornamento OneDrive sincronizza i set di dati e i report con i relativi file di origine. Per impostazione predefinita, Power BI verifica circa ogni ora se un set di dati connessi a un file in OneDrive o SharePoint Online richiede la sincronizzazione.

> [!IMPORTANT]
> Prestare attenzione al modo in cui si gestiscono i file in OneDrive. Se si imposta un file di OneDrive come origine dati, quando Power BI esegue l'aggiornamento fa riferimento all'ID elemento del file. Questo può causare problemi in alcuni scenari. Si consideri lo scenario in cui è presente un file master _A_ e una copia di produzione di tale file, _B_ e si configura l'aggiornamento di OneDrive per il file B. Se quindi si _copia_ il file A sul file B, l'operazione di copia elimina il file B precedente e crea un nuovo file B con un ID elemento diverso, che interrompe l'aggiornamento di OneDrive. È invece necessario caricare e sostituire il file B. In questo modo l'ID elemento rimane lo stesso.

È possibile spostare il file in un altra posizione, ad esempio trascinandolo, e l'aggiornamento continuerà a funzionare perché PBI riconosce ancora il fileID. Se tuttavia si copia il file in un'altra posizione, viene creata una nuova istanza del file e un nuovo fileID. Il riferimento al file di Power BI, quindi, non è più valido e l'aggiornamento avrà esito negativo.

Per esaminare i cicli di sincronizzazione precedenti, controllare la scheda OneDrive nella cronologia degli aggiornamenti. Lo screenshot seguente illustra un ciclo di sincronizzazione completato per un set di dati di esempio.

![Cronologia aggiornamenti](media/refresh-data/refresh-history.png)

Come illustra lo screenshot precedente, Power BI ha identificato questo aggiornamento OneDrive come aggiornamento **pianificato**, ma non è possibile configurare l'intervallo di aggiornamento. È possibile disattivare l'aggiornamento OneDrive solo nelle impostazioni del set di dati. Disattivare l'aggiornamento è utile se non si vuole che i set di dati e i report di Power BI selezionino automaticamente eventuali modifiche dai file di origine.

Si noti che la pagina delle impostazioni del set di dati contiene solo le pagine delle **credenziali di OneDrive** e dell'**aggiornamento OneDrive** se il set di dati è connesso a un file in OneDrive o SharePoint Online, come nello screenshot seguente. I set di dati che non sono connessi al file di origine in OneDrive o SharePoint Online non visualizzano queste sezioni.

![Credenziali di OneDrive e aggiornamento OneDrive](media/refresh-data/onedrive-credentials-refresh.png)

Se si disabilita l'aggiornamento OneDrive per un set di dati, è comunque possibile sincronizzare il set di dati su richiesta selezionando **Aggiorna ora** nel menu del set di dati. Come parte dell'aggiornamento su richiesta, Power BI verifica se il file di origine in OneDrive o SharePoint Online è più recente rispetto al set di dati in Power BI e in questo caso sincronizza il set di dati. Nella **cronologia degli aggiornamenti** queste attività sono elencate come aggiornamenti su richiesta nella scheda **OneDrive**.

Tenere presente che l'aggiornamento OneDrive non esegue il pull dei dati dalle origini dati originali. L'aggiornamento OneDrive si limita ad aggiornare le risorse in Power BI con i metadati e i dati del file PBIX, XLSX o CSV, come illustrato nel diagramma seguente. Per assicurarsi che il set di dati contenga i dati più recenti delle origini dati, Power BI attiva anche un aggiornamento dei dati come parte di un aggiornamento su richiesta. È possibile verificarlo nella **cronologia degli aggiornamenti** se si passa alla scheda **Pianificato**.

![Diagramma dell'aggiornamento OneDrive](media/refresh-data/onedrive-refresh-diagram.png)

Se si mantiene abilitato l'aggiornamento OneDrive per un set di dati connesso a OneDrive o SharePoint Online e si vuole eseguire l'aggiornamento dei dati in base a una pianificazione, assicurarsi di configurare la pianificazione in modo che Power BI esegua l'aggiornamento dei dati dopo l'aggiornamento OneDrive. Ad esempio, se si è creato un proprio servizio o processo per aggiornare il file di origine in OneDrive o SharePoint Online ogni notte alle ore 1:00, è possibile configurare l'aggiornamento pianificato per le 2:30 in modo che Power BI abbia abbastanza tempo per completare l'aggiornamento OneDrive prima di avviare l'aggiornamento dei dati.

#### <a name="refresh-of-query-caches"></a>Aggiornamento delle cache delle query

Se il set di dati si trova in una capacità Premium, è possibile migliorare le prestazioni degli eventuali report e dashboard associati abilitando la memorizzazione di query nella cache, come nello screenshot seguente. La memorizzazione di query nella cache imposta la capacità Premium in modo che usi il servizio di memorizzazione nella cache locale per la gestione dei risultati, evitandone il calcolo nell'origine dati sottostante. Per altre informazioni, vedere [Memorizzazione di query nella cache in Power BI Premium](power-bi-query-caching.md).

![Memorizzazione di query nella cache](media/refresh-data/query-caching.png)

Dopo un aggiornamento dei dati, tuttavia, i risultati delle query memorizzate in precedenza nella cache non sono più validi. Power BI ignora i risultati memorizzati nella cache ed è necessario ricompilarli. Per questo motivo, la memorizzazione di query nella cache può non essere vantaggiosa per i report e i dashboard associati ai set di dati che si aggiornano molto spesso, ad esempio 48 volte al giorno.

#### <a name="tile-refresh"></a>Aggiornamento del riquadro

Power BI mantiene una cache per ogni oggetto visivo dei riquadri nei dashboard e aggiorna in modo proattivo le cache dei riquadri quando i dati vengono modificati. In altre parole, l'aggiornamento dei riquadri viene eseguita automaticamente dopo un aggiornamento dei dati. Questo vale per le operazioni di aggiornamento sia pianificate che su richiesta. È anche possibile forzare l'aggiornamento dei riquadri selezionando **Altre opzioni** (...) in alto a destra nel dashboard e quindi **Aggiorna riquadri del dashboard**.

![Aggiorna riquadri del dashboard](media/refresh-data/refresh-dashboard-tiles.png)

Poiché tutto avviene automaticamente, l'aggiornamento dei riquadri si può considerare parte integrante dell'aggiornamento dei dati. Tra le altre cose, si può notare che la durata dell'aggiornamento aumenta con il numero di riquadri. L'overhead di aggiornamento dei riquadri può essere significativo.

Per impostazione predefinita, Power BI mantiene una sola cache per ogni riquadro, ma se si usa la sicurezza dinamica per limitare l'accesso ai dati in base ai ruoli utente, come descritto nell'articolo sulla [sicurezza a livello di riga con Power BI](service-admin-rls.md), Power BI deve mantenere un cache per ogni ruolo e ogni riquadro. Il numero di cache dei riquadro viene moltiplicato per il numero di ruoli.

La situazione può diventare ancora più complessa se il set di dati usa una connessione dinamica a un modello di dati di Analysis Services con sicurezza a livello di riga, come descritto nell'esercitazione [Sicurezza a livello di riga dinamica con il modello tabulare di Analysis Services](desktop-tutorial-row-level-security-onprem-ssas-tabular.md). In questa situazione Power BI deve mantenere e aggiornare una cache per ogni riquadro e ogni utente che ha visualizzato il dashboard. Non è insolito che la porzione dell'aggiornamento dei riquadri di tale operazione di aggiornamento dei dati superi di gran lunga il tempo necessario per recuperare i dati dall'origine. Per informazioni dettagliate sull'aggiornamento dei riquadri, vedere [Risoluzione degli errori del riquadro](refresh-troubleshooting-tile-errors.md).

#### <a name="refresh-of-report-visuals"></a>Aggiornamento di oggetti visivi del report

Questo processo di aggiornamento è meno importante, perché è rilevante solo per le connessioni in tempo reale ad Analysis Services. Per queste connessioni, Power BI memorizza nella cache l'ultimo stato degli oggetti visivi del report in modo che quando si visualizza di nuovo il report, Power BI non deve eseguire query sul modello tabulare di Analysis Services. Quando si interagisce con il report, ad esempio modificando un filtro del report, Power BI esegue una query sul modello tabulare e aggiorna automaticamente gli oggetti visivi del report. Se si sospetta che un report visualizzi dati non aggiornati, è anche possibile selezionare il pulsante Aggiorna del report per attivare un aggiornamento di tutti gli oggetti visivi, come illustrato nello screenshot seguente.

![Aggiornare gli oggetti visivi del report](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Esaminare le dipendenze dell'infrastruttura dei dati

Indipendentemente dalla modalità di archiviazione, nessun aggiornamento dei dati può avere esito se le origini dati sottostanti non sono accessibili. Esistono tre scenari principali di accesso ai dati:

- Un set di dati usa le origini dati locali
- Un set di dati usa le origini dati nel cloud
- Un set di dati usa i dati di origini sia locali che nel cloud

### <a name="connecting-to-on-premises-data-sources"></a>Connessione a origini dati locali

Se il set di dati usa un'origine dati a cui Power BI non è in grado di accedere usando una connessione diretta alla rete, è necessario configurare una connessione gateway per il set di dati per poter abilitare una pianificazione dell'aggiornamento o eseguire un aggiornamento dei dati su richiesta. Per altre informazioni sui gateway dati e sul relativo funzionamento, vedere [Informazioni sui gateway dati locali](service-gateway-onprem.md).

Sono disponibili le opzioni seguenti:

- Scegliere un gateway dati aziendale con la definizione di origine dati richiesta
- Distribuire un gateway dati personale

> [!NOTE]
> È possibile trovare un elenco di tipi di origini dati che richiedono un gateway dati nell'articolo [Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md).

#### <a name="using-an-enterprise-data-gateway"></a>Uso di un gateway dati aziendale

Microsoft consiglia di usare un gateway dati aziendale anziché un gateway personale per connettere un set di dati a un'origine dati locale. Assicurarsi che il gateway sia configurato correttamente, ovvero che abbia gli aggiornamenti più recenti e tutte le definizioni di origini dati richieste. Con la definizione di origine dati Power BI ha a disposizione le informazioni di connessione per una determinata origine, tra cui gli endpoint di connessione, la modalità di autenticazione e le credenziali. Per altre informazioni sulla gestione delle origini dati in un gateway, vedere [Gestire l'origine dati - Importazione/aggiornamento pianificato](service-gateway-enterprise-manage-scheduled-refresh.md).

La connessione di un set di dati a un gateway aziendale è relativamente semplice se si è un amministratore del gateway. Con le autorizzazioni di amministratore, è possibile aggiornare rapidamente il gateway e aggiungere le origini dati mancanti, se necessario. Di fatto è possibile aggiungere un'origine dati mancante al gateway direttamente dalla pagina delle impostazioni del set di dati. Espandere il pulsante di attivazione e disattivazione per visualizzare le origini dati e selezionare il collegamento **Aggiungi al gateway**, come nello screenshot seguente. Se invece non si è un amministratore del gateway, è necessario contattarne uno per aggiungere la definizione dell'origine dati richiesta.

> [!NOTE]
> Solo gli amministratori del gateway possono aggiungere origini dati a un gateway. Assicurarsi anche che l'amministratore del gateway aggiunga l'account utente all'elenco di utenti con le autorizzazioni per l'uso dell'origine dati. La pagina delle impostazioni del set di dati consente solo di selezionare un gateway aziendale con un'origine dati corrispondente per cui si hanno le autorizzazioni.

![Aggiungi al gateway](media/refresh-data/add-to-gateway.png)

Assicurarsi di eseguire il mapping all'origine dati della definizione dell'origine dati corretta. Come risulta chiaro dallo screenshot precedente, gli amministratori del gateway possono creare più definizioni in un singolo gateway e connetterli alla stessa origine dati, ognuno con credenziali diverse. Nell'esempio illustrato, il proprietario di un set di dati del reparto Sales sceglierebbe la definizione dell'origine dati AdventureWorksProducts-Sales mentre il proprietario di un set di dati del reparto Support eseguirebbe il mapping del set di dati alla definizione AdventureWorksProducts-Support. Se i nomi della definizione dell'origine dati non sono intuitivi, contattare l'amministratore del gateway per capire quale definizione selezionare.

> [!NOTE]
> Un set di dati può usare solo una singola connessione gateway. In altre parole, non è possibile accedere alle origini dati locali usando più connessioni gateway. Di conseguenza, è necessario aggiungere tutte le definizioni di origini dati necessarie allo stesso gateway.

#### <a name="deploying-a-personal-data-gateway"></a>Distribuzione di un gateway dati personale

Se l'utente non ha accesso a un gateway dati aziendale ed è l'unica persona che gestisce i set di dati, per cui non deve condividere le origini dati con altri utenti, può distribuire un gateway dati in modalità personale. Nella sezione **Connessione gateway** selezionare **Installa ora** in **Non ci sono gateway personali installati**. Il gateway dati personale presenta diverse limitazioni, come illustrato in [Gateway dati locale (modalità personale)](service-gateway-personal-mode.md).

A differenza di un gateway dati aziendale, non è necessario aggiungere definizioni di origini dati a un gateway personale. La configurazione dell'origine dati si gestisce usando la sezione **Credenziali origine dati** nelle impostazioni del set di dati, come illustrato nello screenshot seguente.

![Configurare le credenziali dell'origine dati per il gateway](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> Il gateway dati personale non supporta i set di dati in modalità DirectQuery/LiveConnect. La pagina delle impostazioni del set di dati potrebbe richiederne l'installazione, ma se si usa solo un gateway personale, non è possibile configurare una connessione gateway. Assicurarsi di avere un gateway dati aziendale che supporta questi tipi di set di dati.

### <a name="accessing-cloud-data-sources"></a>Accesso a origini dati nel cloud

I set di dati che usano origini dati nel cloud, ad esempio il database SQL di Azure, non richiedono un gateway dati se Power BI è in grado di stabilire una connessione di rete diretta all'origine. Di conseguenza, è possibile gestire la configurazione di queste origini dati usando la sezione **Credenziali origine dati** nelle impostazioni del set di dati. Come illustra lo screenshot seguente, non è necessario configurare una connessione gateway.

![Configurare le credenziali dell'origine dati senza un gateway](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Accesso a origini locali e cloud nella stessa query di origine

Un set di dati può ottenere dati da più origini e queste origini possono risiedere in locale o nel cloud. Tuttavia, un set di dati può usare solo una singola connessione gateway, come indicato in precedenza. Benché le origini dati cloud non richiedano necessariamente un gateway, un gateway si rende necessario se un set di dati si connette a origini sia in locale che nel cloud in un'unica query di mashup. In questo scenario Power BI deve usare un gateway anche per le origini dati cloud. Il diagramma seguente illustra l'accesso di un set di dati alle relative origini dati.

![Origini dati cloud e locali](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Se un set di dati usa query di mashup separate per connettersi a origini locali e cloud, Power BI usa una connessione gateway per raggiungere le origini locali e una connessione di rete diretta per le origini cloud. Se una query di mashup unisce o accoda i dati di origini locali e cloud, Power BI passa alla connessione gateway anche per le origini cloud.

I set di dati di Power BI si basano su Power Query per accedere e recuperare i dati di origine. L'elenco di mashup seguente rappresenta un esempio di base di una query che unisce i dati di un'origine locale e un'origine cloud.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Esistono due opzioni per configurare un gateway dati in modo che sia possibile unire o accodare i dati di origini locali e cloud:

- Aggiungere al gateway dati una definizione di origine dati per l'origine cloud oltre alle origini dati locali.
- Selezionare la casella di controllo **Consente l'aggiornamento delle origini dati cloud dell'utente tramite questo cluster di gateway**.

![Aggiornamento con il cluster di gateway](media/refresh-data/refresh-gateway-cluster.png)

Se si seleziona la casella di controllo **Consenti l'aggiornamento delle origini dati cloud dell'utente tramite questo cluster di gateway**, come illustrato in questo screenshot, Power BI potrà usare la configurazione definita dall'utente per l'origine cloud in **Credenziali origine dati** nelle impostazioni del set di dati. Ciò può favorire la riduzione dell'overhead della configurazione del gateway. D'altra parte, se si vuole avere un maggiore controllo sulle connessioni stabilite dal gateway, non è consigliabile abilitare questa casella di controllo. In questo caso è necessario aggiungere al gateway una definizione di origine dati esplicita per ogni origine cloud da supportare. È anche possibile abilitare la casella di controllo e aggiungere a un gateway le definizioni di origini dati esplicite per le origini cloud. In questo caso il gateway usa le definizioni di origini dati per tutte le origini corrispondenti.

### <a name="configuring-query-parameters"></a>Configurazione dei parametri di query

La complessità delle query di mashup o M create con Power Query può variare da procedure molto semplici a costrutti con parametri. Nell'elenco seguente è riportata una piccola query di mashup di esempio che usa due parametri denominati _SchemaName_ e _TableName_ per accedere a una determinata tabella di un database AdventureWorks.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> I parametri di query sono supportati solo per i set di dati in modalità importazione. La modalità DirectQuery/LiveConnect non supporta le definizioni dei parametri di query.

Per garantire che un set di dati con parametri acceda ai dati corretti, è necessario configurare i parametri della query di mashup nelle impostazioni del set di dati. È anche possibile aggiornare i parametri a livello di codice usando l'[API REST di Power BI](/rest/api/power-bi/datasets/updateparametersingroup). Lo screenshot seguente illustra l'interfaccia utente per configurare i parametri di query per un set di dati che usa la query di mashup vista in precedenza.

![Configurare i parametri di query](media/refresh-data/configure-query-parameters.png)

> [!NOTE]
> Power BI attualmente non supporta le definizioni di origini dati con parametri, note anche come origini dati dinamiche. Ad esempio, non è possibile impostare parametri per la funzione di accesso ai dati Sql.Database("SqlServer01", "AdventureWorks"). Se il set di dati si basa su origini dati dinamiche, Power BI indica che ha rilevato origini dati sconosciute o non supportate. Se si vuole che Power BI sia in grado di identificare e connettersi alle origini dati, è necessario sostituire i parametri nelle funzioni di accesso ai dati con valori statici. Per altre informazioni, vedere [Risoluzione dei problemi relativi all'origine dati non supportata per l'aggiornamento](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="configure-scheduled-refresh"></a>Configurare l'aggiornamento pianificato

Stabilire la connettività tra Power BI e le origini dati è di gran lunga l'attività più impegnativa nella configurazione di un aggiornamento dei dati. I passaggi rimanenti sono relativamente semplici e includono l'impostazione della pianificazione dell'aggiornamento e l'abilitazione delle notifiche degli errori di aggiornamento. Per le istruzioni dettagliate, vedere la guida pratica [Configurazione dell'aggiornamento pianificato](refresh-scheduled-refresh.md).

### <a name="setting-a-refresh-schedule"></a>Impostazione della pianificazione di un aggiornamento

Nella sezione **Aggiornamento pianificato** è possibile definire la frequenza e gli orari per l'aggiornamento di un set di dati. Come accennato in precedenza, è possibile configurare fino a otto orari giornalieri se il set di dati si trova in una capacità condivisa o 48 orari in Power BI Premium. Lo screenshot seguente illustra una pianificazione dell'aggiornamento con un intervallo di dodici ore.

![Configurare l'aggiornamento pianificato](media/refresh-data/configure-scheduled-refresh.png)

Se è stata configurata una pianificazione dell'aggiornamento, nella pagina delle impostazioni del set di dati viene visualizzato l'orario dell'aggiornamento successivo, come illustrato nello screenshot precedente. Per aggiornare i dati prima dell'orario pianificato, ad esempio per testare la configurazione del gateway e dell'origine dati, eseguire un aggiornamento su richiesta usando l'opzione **Aggiorna adesso** nel menu del set di dati nel riquadro di spostamento. Gli aggiornamenti on demand non influiscono sull'orario del prossimo aggiornamento pianificato.

Si noti inoltre che l'orario configurato per l'aggiornamento potrebbe non essere esattamente l'ora in cui Power BI avvia il processo pianificato successivo. Power BI avvia gli aggiornamenti pianificati in base ad approssimazioni ottimali. L'obiettivo è avviare l'aggiornamento entro 15 minuti dall'orario pianificato, ma può verificarsi un ritardo fino a un'ora se il servizio non è in grado di allocare prima le risorse necessarie.

> [!NOTE]
> Power BI disattiva la pianificazione dell'aggiornamento dopo quattro tentativi consecutivi non riusciti o quando il servizio rileva un errore irreversibile che richiede un aggiornamento della configurazione, ad esempio credenziali non valide o scadute. Non è possibile modificare la soglia per i tentativi consecutivi non riusciti.

### <a name="getting-refresh-failure-notifications"></a>Notifiche di aggiornamento non riuscito

Per impostazione predefinita, Power BI invia notifiche relative agli errori di aggiornamento via posta elettronica al proprietario del set di dati in modo che possa agire in modo tempestivo in caso di problemi. Power BI invia una notifica anche quando il servizio disabilita la pianificazione a causa di ripetuti tentativi non riusciti. Microsoft consiglia di lasciare selezionata la casella di controllo **Invia messaggi di notifica di aggiornamento non riuscito a me**.

È anche consigliabile specificare altri destinatari usando la casella di testo **Invia un messaggio di posta elettronica a questi utenti quando l'aggiornamento non riesce**. Oltre al proprietario del set di dati, anche i destinatari specificati ricevono le notifiche degli errori di aggiornamento. Tali destinatari possono essere, ad esempio, il collega che si occupa dei propri set di dati quando si è in vacanza. Oppure l'alias di posta elettronica del team di supporto che si occupa dei problemi di aggiornamento per il reparto o l'organizzazione. L'invio delle notifiche degli errori di aggiornamento ad altri utenti oltre al proprietario del set di dati è utile per garantire che i problemi vengano rilevati e risolti in modo tempestivo.

Si noti che Power BI invia notifiche non solo in caso di aggiornamento non riuscito, ma anche quando il servizio sospende un aggiornamento pianificato a causa di inattività. Dopo due mesi, se un utente non ha visitato alcun dashboard o report creato nel set di dati, Power BI considera il set di dati non attivo. In questa situazione, Power BI invia un messaggio di posta elettronica al proprietario del set di dati per informarlo che il servizio ha sospeso la pianificazione aggiornamenti per il set di dati. Vedere lo screenshot seguente per un esempio di tale notifica.

![Messaggio di posta elettronica per l'aggiornamento in pausa](media/refresh-data/email-paused-refresh.png)

Per riprendere l'aggiornamento pianificato, visitare un report o un dashboard creato con questo set di dati o aggiornare manualmente il set di dati usando l'opzione **Aggiorna ora**.

### <a name="checking-refresh-status-and-history"></a>Controllo della cronologia e dello stato degli aggiornamenti

Anche se vengono inviate notifiche in caso di problemi, è consigliabile verificare periodicamente che i set di dati non presentino errori di aggiornamento. Un modo rapido è visualizzare l'elenco dei set di dati in un'area di lavoro. I set di dati con errori sono contrassegnati da una piccola icona di avviso. Selezionare l'icona di avviso per ottenere informazioni aggiuntive, come nello screenshot seguente. Per altre informazioni sulla risoluzione dei problemi specifici degli aggiornamenti, vedere [Risoluzione dei problemi negli scenari di aggiornamento](refresh-troubleshooting-refresh-scenarios.md).

![Avviso sullo stato dell'aggiornamento](media/refresh-data/refresh-status-warning.png)

L'icona di avviso consente di rilevare i problemi correnti dei set di dati, ma è consigliabile controllare occasionalmente anche la cronologia degli aggiornamenti. Come suggerisce il nome, la cronologia degli aggiornamenti consente di esaminare l'esito positivo o negativo dei cicli di sincronizzazione precedenti. Ad esempio, un amministratore del gateway potrebbe aver aggiornato un set di credenziali del database scaduto. Come si può vedere nello screenshot seguente, la cronologia degli aggiornamenti viene visualizzata quando un aggiornamento interessato è di nuovo in funzione.

![Messaggi della cronologia degli aggiornamenti](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> È possibile trovare un collegamento per visualizzare la cronologia degli aggiornamenti nelle impostazioni del set di dati. È anche possibile attivare la cronologia degli aggiornamenti a livello di codice usando l'[API REST di Power BI](/rest/api/power-bi/datasets/getrefreshhistoryingroup). Usando una soluzione personalizzata, è possibile monitorare la cronologia degli aggiornamenti di più set di dati in modo centralizzato.

## <a name="automatic-page-refresh"></a>Aggiornamento automatico delle pagine

L'aggiornamento automatico delle pagine funziona a livello di pagina del report e consente agli autori di report di impostare un intervallo di aggiornamento per gli oggetti visivi in una pagina che si attiva solo quando viene usata la pagina. L'aggiornamento automatico delle pagine è disponibile solo per le origini dati DirectQuery. L'intervallo di aggiornamento minimo dipende dal tipo di area di lavoro in cui viene pubblicato il report e dalle impostazioni di amministrazione della capacità per le aree di lavoro Premium e le [aree di lavoro incorporate](developer/embedded/embedding.md).

Per altre informazioni sull'aggiornamento automatico delle pagine, vedere l'articolo [Aggiornamento automatico della pagina](desktop-automatic-page-refresh.md).

## <a name="best-practices"></a>Procedure consigliate

Controllare regolarmente la cronologia degli aggiornamenti dei set di dati è una delle procedure consigliate più importanti da adottare per garantire che i report e i dashboard usino dati aggiornati. Se si rilevano problemi, risolverli tempestivamente e verificare l'esito con i proprietari delle origini dati e gli amministratori di gateway, se necessario.

Inoltre, prendere in considerazione i seguenti consigli per stabilire e gestire processi di aggiornamento dei dati affidabili per i set di dati:

- Pianificare gli aggiornamenti negli orari di minor traffico, soprattutto se i set di dati sono in Power BI Premium. Se si distribuiscono i cicli di aggiornamento per i set di dati in un intervallo di tempo più ampio, è possibile evitare i picchi che altrimenti possono sovraccaricare le risorse disponibili. I ritardi nell'avvio di un ciclo di aggiornamento sono un indicatore di sovraccarico delle risorse. Se una capacità Premium è completamente esaurita, Power BI potrebbe addirittura saltare un ciclo di aggiornamento.
- Tenere presenti i limiti di aggiornamento. Se i dati di origine cambiano di frequente o il volume dei dati è consistente, considerare la possibilità di usare la modalità DirectQuery/LiveConnect anziché la modalità importazione se l'aumento del carico nell'origine e l'impatto sulle prestazioni delle query è accettabile. Evitare di aggiornare costantemente un set di dati in modalità importazione. Tuttavia, la modalità DirectQuery/LiveConnect presenta diverse limitazioni, ad esempio un limite di un milione di righe per la restituzione dei dati e un limite di tempo di risposta di 225 secondi per l'esecuzione di query, come illustrato in [Usare DirectQuery in Power BI Desktop](desktop-use-directquery.md). Queste limitazioni possono rendere necessario l'uso della modalità importazione. Per i volumi di dati molto grandi, prendere in considerazione l'uso delle [aggregazioni in Power BI](desktop-aggregations.md).
- Verificare che la durata dell'aggiornamento dei set di dati non superi la durata massima dell'aggiornamento. Usare Power BI Desktop per controllare la durata dell'aggiornamento. Se richiede più di 2 ore, considerare la possibilità di spostare il set di dati in Power BI Premium. Il set di dati potrebbe non essere aggiornabile in una capacità condivisa. È anche consigliabile usare l'[aggiornamento incrementale in Power BI Premium](service-premium-incremental-refresh.md) per i set di dati di dimensioni superiori a 1 GB o il cui aggiornamento richiede diverse ore.
- Ottimizzare i set di dati in modo da includere solo le tabelle e le colonne usate da report e dashboard. Ottimizzare le query di mashup e, se possibile, evitare le definizioni di origini dati in tempo reale e calcoli DAX costosi. In particolare, evitare le funzioni DAX che testano tutte le righe di una tabella e sono impegnative in termini di consumo di memoria e overhead di elaborazione.
- Applicare le stesse impostazioni della privacy di Power BI Desktop per assicurarsi che Power BI sia in grado di generare query efficienti sulle origini. Tenere presente che Power BI Desktop non pubblica le impostazioni della privacy. È necessario riapplicare manualmente le impostazioni nelle definizioni di origini dati dopo aver pubblicato il set di dati.
- Limitare il numero di oggetti visivi nei dashboard, in particolare se si usa la [sicurezza a livello di riga](service-admin-rls.md). Come spiegato in precedenza in questo articolo, un numero eccessivo di riquadri dei dashboard può aumentare notevolmente la durata dell'aggiornamento.
- Usare una distribuzione affidabile con gateway dati aziendale per connettere i set di dati alle origini dati locali. Se si verificano errori di aggiornamento correlati al gateway, ad esempio gateway non disponibile o sovraccarico, rivolgersi agli amministratori dei gateway per aggiungere altri gateway a un cluster esistente o distribuire un nuovo cluster (scalabilità verticale e orizzontale).
- Usare gateway dati separati per i set di dati di importazione e i set di dati DirectQuery/LiveConnect in modo che le importazioni di dati durante l'aggiornamento pianificato non influiscano sulle prestazioni di report e dashboard dei set di dati DirectQuery/LiveConnect, che eseguono query sulle origini dati ad ogni interazione dell'utente.
- Verificare che Power BI sia in grado di inviare le notifiche relative agli errori di aggiornamento alla propria cassetta postale. A causa dei filtri per la posta indesiderata, i messaggi di posta elettronica potrebbero essere bloccati o spostati in una cartella separata e passare inosservati.


## <a name="next-steps"></a>Passaggi successivi

[Configurazione dell'aggiornamento pianificato](refresh-scheduled-refresh.md)  
[Strumenti per la risoluzione dei problemi di aggiornamento](service-gateway-onprem-tshoot.md)  
[Scenari per la risoluzione dei problemi di aggiornamento](refresh-troubleshooting-refresh-scenarios.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
