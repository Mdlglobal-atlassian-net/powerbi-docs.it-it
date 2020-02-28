---
title: Eseguire la migrazione di report di SQL Server Reporting Services in Power BI
description: Informazioni per eseguire la migrazione di report di SQL Server Reporting Services (SSRS) in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: e65dd42e8ec787d0c6edba534f79cdb06e5ba14c
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527293"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Eseguire la migrazione di report di SQL Server Reporting Services in Power BI

Questo articolo è destinato agli autori di report di SQL Server Reporting Services (SSRS) e agli amministratori di Power BI. Fornisce informazioni per la migrazione dei report [RDL (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) in Power BI.

> [!NOTE]
> È possibile eseguire la migrazione solo dei report RDL. In Power BI i report RDL sono detti _report impaginati_.

Le informazioni sono suddivise in quattro fasi. Prima di eseguire la migrazione dei report, è consigliabile leggere l'intero articolo.

1. [Prima di iniziare](#before-you-start)
1. [Fase pre-migrazione](#pre-migration-stage)
1. [Fase di migrazione](#migration-stage)
1. [Fase post-migrazione](#post-migration-stage)

È possibile eseguire la migrazione senza tempi di inattività per i server SSRS né interruzioni per gli utenti dei report. È importante comprendere che non è necessario rimuovere dati né report. È quindi possibile mantenere attivo l'ambiente corrente fino a quando non si è pronti per ritirarlo.

## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare la migrazione, è necessario verificare che l'ambiente soddisfi determinati prerequisiti. Verranno descritti questi prerequisiti e verrà inoltre presentato un utile strumento di migrazione.

### <a name="preparing-for-migration"></a>Preparazione alla migrazione

In preparazione alla migrazione dei report in Power BI, verificare innanzitutto che l'organizzazione abbia una sottoscrizione di [Power BI Premium](../service-premium-what-is.md). Questa sottoscrizione è necessaria per ospitare ed eseguire i report impaginati di Power BI.

### <a name="supported-versions"></a>Versioni supportate

È possibile eseguire la migrazione di istanze di SSRS in esecuzione in locale o in macchine virtuali ospitate da provider di servizi cloud, ad esempio Azure.

L'elenco seguente contiene le versioni di SQL Server supportate per la migrazione in Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

È anche possibile eseguire la migrazione dal server di report di Power BI.

### <a name="migration-tool"></a>Strumento di migrazione

È consigliabile usare lo [strumento di migrazione RDL](https://github.com/microsoft/RdlMigration) per preparare ed eseguire la migrazione dei report. Questo strumento è stato sviluppato da Microsoft per aiutare i clienti a eseguire la migrazione dei report RDL dai server SSRS in Power BI. È disponibile in GitHub e consente di seguire una procedura dettagliata completa dello scenario di migrazione.

Lo strumento automatizza le attività seguenti:

- Controllo della presenza di [origini dati non supportate](../paginated-reports-data-sources.md) e [funzionalità dei report non supportate](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
- Conversione delle risorse _condivise_ in risorse _incorporate_:
  - Le **origini dati** condivise diventano origini dati incorporate
  - I **set di dati** condivisi diventano set di dati incorporati
- Pubblicazione dei report (che superano i controlli) come report impaginati in un'area di lavoro di Power BI specificata (in una capacità Premium)

I report esistenti non vengono modificati né rimossi. Al termine, lo strumento restituisce un riepilogo di tutte le azioni completate, con esito positivo o negativo.

Nel tempo lo strumento verrà migliorato da Microsoft. La community è invitata a contribuire al suo miglioramento.

## <a name="pre-migration-stage"></a>Fase pre-migrazione

Dopo aver verificato che l'organizzazione soddisfa i prerequisiti, è possibile iniziare la fase _pre-migrazione_. Questa fase è costituita a sua volta da tre fasi:

1. Rileva
1. Valutare
1. Prepara

### <a name="discover"></a>Rileva

L'obiettivo della fase di _individuazione_ è quello di identificare le istanze di SSRS esistenti. Questo processo comporta l'analisi della rete per identificare tutte le istanze di SQL Server nell'organizzazione.

È possibile usare [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). Questo strumento, noto anche come "MAP Toolkit", individua e segnala le istanze, le versioni e le funzionalità installate di SQL Server. Si tratta di un potente strumento di inventario, valutazione e report che consente di semplificare il processo di pianificazione della migrazione.

### <a name="assess"></a>Valutare

Dopo aver individuato le istanze di SSRS, l'obiettivo della fase di _valutazione_ è comprendere se sono presenti report SSRS, o elementi del server, di cui non è possibile eseguire la migrazione.

È possibile eseguire la migrazione dai server SSRS in Power BI solo dei report RDL. Ogni report RDL di cui viene eseguita la migrazione diventa un report impaginato di Power BI.

Non è tuttavia possibile eseguire la migrazione in Power BI dei tipi di elementi SSRS seguenti:

- Origini dati condivise<sup>1</sup>
- Set di dati condivisi<sup>1</sup>
- Risorse, ad esempio file di immagine
- Indicatori KPI (SSRS 2016 o versione successiva, solo edizione Enterprise)
- Report per dispositivi mobili (SSRS 2016 o versione successiva, solo edizione Enterprise)
- Modelli di report (deprecati)
- Parti di report (deprecate)

<sup>1</sup> Lo [strumento di migrazione RDL](https://github.com/microsoft/RdlMigration) converte automaticamente le origini dati condivise e i set di dati condivisi, a condizione che usino origini dati supportate.

Se i report RDL si basano su funzionalità [non ancora supportate dai report impaginati di Power BI](../paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), è possibile decidere di svilupparli di nuovo come [report di Power BI](../consumer/end-user-reports.md). Anche se è possibile eseguire la migrazione dei report RDL, è consigliabile valutarne la modernizzazione come report di Power BI, quando opportuno.

Se i report RDL devono recuperare dati da _origini dati locali_, non possono usare la funzione Single Sign-On (SSO). Tutte le operazioni di recupero dei dati da queste origini vengono attualmente eseguite tramite il contesto di sicurezza dell'_account utente dell'origine dati del gateway_. Per SQL Server Analysis Services (SSAS) non è possibile applicare la sicurezza a livello di riga per utente singolo.

In genere, i report impaginati di Power BI sono ottimizzati per la **stampa** o la **generazione di PDF**. I report di Power BI sono ottimizzati per **esplorazione e interattività**. Per altre informazioni, vedere [Quando usare report impaginati in Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Prepara

L'obiettivo della fase di _preparazione_ è quello di preparare tutti gli elementi. In questa fase si configura l'ambiente Power BI, si pianificano gli aspetti relativi a sicurezza e pubblicazione dei report e si raccolgono idee per sviluppare di nuovo gli elementi SSRS di cui non verrà eseguita la migrazione.

1. Verificare che il [carico di lavoro Report impaginati](../service-admin-premium-workloads.md#paginated-reports) sia abilitato per la capacità Power BI Premium e che disponga di memoria sufficiente.
1. Verificare il supporto per le [origini dati](../paginated-reports-data-sources.md) dei report e configurare un'istanza di [Power BI Gateway](../service-gateway-onprem.md) per consentire la connettività con le origini dati locali.
1. Acquisire familiarità con la sicurezza di Power BI e pianificare [come verranno riprodotte le cartelle e le autorizzazioni di SSRS](/sql/reporting-services/security/secure-folders) con [aree di lavoro e ruoli dell'area di lavoro di Power BI ](../service-new-workspaces.md).
1. Acquisire familiarità con la condivisione di Power BI e stabilire come verrà distribuito il contenuto mediante la pubblicazione di [app Power BI](../service-create-distribute-apps.md).
1. Prendere in considerazione l'uso di [set di dati di Power BI condivisi](../service-datasets-build-permissions.md) al posto delle origini dati condivise di SSRS.
1. Usare [Power BI Desktop](../desktop-what-is-desktop.md) per lo sviluppo di report ottimizzati per i dispositivi mobili, eventualmente usando l'[oggetto visivo personalizzato Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) al posto di indicatori KPI e report per dispositivi mobili di SSRS.
1. Rivalutare l'uso del campo predefinito **ID utente** nei report. Se si fa affidamento sull'**ID utente** per proteggere i dati dei report, è necessario comprendere che per i report impaginati (se ospitati nel servizio Power BI) viene restituito il nome dell'entità utente (UPN, User Principal Name). Invece di restituire il nome dell'account NT, ad esempio _AW\mblythe_, il campo predefinito restituirà quindi qualcosa di simile a _m.blythe&commat;adventureworks.com_. Sarà necessario rivedere le definizioni del set di dati e, forse, i dati di origine. Dopo la revisione e la pubblicazione, è consigliabile testare accuratamente i report per verificare che le autorizzazioni per i dati funzionino come previsto.
1. Rivalutare l'uso del campo predefinito **ExecutionTime** nei report. Per i report impaginati (se ospitati nel servizio Power BI), il campo predefinito restituisce la data e l'ora _nell'ora UTC_. Questo può influire sui valori predefiniti dei parametri dei report e sulle etichette dell'ora di esecuzione dei report, aggiunte in genere nel piè di pagina dei report.
1. Se l'origine dati è SQL Server (locale), verificare che i report non usino visualizzazioni mappa. La visualizzazione mappa dipende dai tipi di dati spaziali di SQL Server e questi non sono supportati dal gateway. Per altre informazioni, vedere [Linee guida per il recupero dei dati per i report impaginati (tipi di dati complessi di SQL Server)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Assicurarsi che gli autori dei report dispongano di [Power BI Report Builder](../report-builder-power-bi.md) e che le versioni successive possano essere distribuite facilmente in tutta l'organizzazione.

## <a name="migration-stage"></a>Fase di migrazione

Dopo aver preparato l'ambiente Power BI e i report, si è pronti per la fase di _migrazione_.

Sono disponibili due opzioni di migrazione: _manuale_ e _automatica_. La migrazione manuale è indicata per un numero ridotto di report o per i report che richiedono modifiche prima della migrazione. La migrazione automatica è adatta in presenza di un numero elevato di report.

### <a name="manual-migration"></a>Migrazione manuale

Chiunque disponga dell'autorizzazione di accesso all'istanza di SSRS e all'area di lavoro di Power BI può eseguire manualmente la migrazione di report in Power BI. Ecco i passaggi da seguire:

1. Aprire il portale SSRS contenente i report di cui eseguire la migrazione.
1. Scaricare ogni definizione di report, salvando i file RDL in locale.
1. Aprire la _versione più recente_ di Power BI Report Builder e connettersi al servizio Power BI usando le credenziali di Azure AD.
1. Aprire ogni report in Power BI Report Builder e quindi:
   1. Verificare che tutte le origini dati e i set di dati siano incorporati nella definizione di report e che si tratti di [origini dati supportate](../paginated-reports-data-sources.md).
   1. Visualizzare in anteprima il report per assicurarsi che il rendering venga eseguito correttamente.
   1. Scegliere l'opzione _Salva con nome_ e quindi selezionare _Servizio Power BI_.
   1. Selezionare l'area di lavoro che conterrà il report.
   1. Verificare che il report venga salvato. Se alcune funzionalità della progettazione del report non sono ancora supportate, l'operazione di salvataggio avrà esito negativo. Verrà visualizzata una notifica con le motivazioni. Sarà quindi necessario modificare la progettazione del report e riprovare a salvare.

### <a name="automated-migration"></a>Migrazione automatica

Sono disponibili due opzioni per la migrazione automatica. È possibile usare:

- Lo strumento di migrazione RDL
- Le API disponibili pubblicamente per SSRS e Power BI

Lo [strumento di migrazione RDL](#migration-tool) è già stato descritto in questo articolo.

È anche possibile usare le API di SSRS e Power BI disponibili pubblicamente per automatizzare la migrazione dei contenuti. Sebbene lo strumento di migrazione RDL usi già queste API, è possibile sviluppare uno strumento personalizzato per rispondere ai propri requisiti specifici.

Per altre informazioni sulle API, vedere:

- [Riferimento all'API REST di Power BI](../developer/rest-api-reference.md)
- [API REST di SQL Server Reporting Services](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Fase post-migrazione

Dopo aver completato la migrazione, si è pronti per la fase _post-migrazione_. Questa fase prevede l'esecuzione di una serie di attività post-migrazione per garantire che tutto funzioni correttamente e in modo efficiente.

### <a name="configure-data-sources"></a>Configurare le origini dati

Dopo aver eseguito la migrazione dei report in Power BI, è necessario verificare che le origini dati siano configurate correttamente. Può essere necessario eseguire l'assegnazione alle origini dati del gateway e [archiviare in modo sicuro le credenziali delle origini dati](../paginated-reports-data-sources.md#azure-sql-database-authentication). Queste operazioni non vengono eseguite dallo strumento di migrazione RDL.

### <a name="review-report-performance"></a>Esaminare le prestazioni dei report

È consigliabile completare le operazioni seguenti per garantire la migliore esperienza utente possibile per i report:

1. Testare i report in ogni [browser supportato da Power BI](../power-bi-browsers.md) per verificare che il rendering venga eseguito correttamente.
1. Eseguire test per confrontare i tempi di rendering dei report in SSRS e Power BI. Verificare che il rendering dei report di Power BI venga eseguito in un tempo accettabile.
1. Se non è possibile eseguire il rendering dei report di Power BI a causa di memoria insufficiente, allocare [risorse aggiuntive alla capacità Power BI Premium](../service-admin-premium-workloads.md#paginated-reports).
1. Per i report con tempi di rendering lunghi, è consigliabile impostare Power BI per recapitarli agli utenti come [sottoscrizioni di posta elettronica con report allegati](../consumer/paginated-reports-subscriptions.md).
1. Per i report di Power BI basati su set di dati di Power BI, esaminare le progettazioni dei modelli per assicurarsi che siano completamente ottimizzate.

### <a name="reconcile-issues"></a>Risolvere i problemi

La fase post-migrazione è fondamentale per risolvere eventuali problemi e aspetti relativi alle prestazioni. L'aggiunta del carico di lavoro Report impaginati a una capacità può contribuire a rallentare le prestazioni, per i report impaginati _e altri contenuti_ archiviati nella capacità.

Per altre informazioni su questi problemi, inclusi i passaggi specifici per comprenderli e attenuarli, vedere gli articoli seguenti:

- [Ottimizzare le capacità Premium](../service-premium-capacity-optimize.md)
- [Monitorare le capacità Premium con l'app](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Che cosa sono i report impaginati in Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- [Linee guida per il recupero dei dati per i report impaginati](report-paginated-data-retrieval.md)
- Video Guy in a Cube: [Introduzione ai report impaginati in Power BI](https://www.youtube.com/watch?v=wfqn45XNK3M)
- [Quando usare report impaginati in Power BI](report-paginated-or-power-bi.md)
- [Report impaginati in Power BI: Domande frequenti](../paginated-reports-faq.md)
- [Power BI Premium FAQ](../service-premium-faq.md) (Domande frequenti su Power BI Premium)
- [Strumento di migrazione RDL](https://github.com/microsoft/RdlMigration)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)

Sono disponibili partner Power BI per aiutare l'organizzazione a svolgere con successo il processo di migrazione. Per collaborare con un partner Power BI, visitare il [portale dei partner Power BI](https://powerbi.microsoft.com/partners/).
