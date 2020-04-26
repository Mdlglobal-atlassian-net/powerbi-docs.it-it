---
title: Connettersi ai set di dati nel servizio Power BI da Power BI Desktop
description: Usare un set di dati comune per più report di Power BI Desktop in più aree di lavoro e gestire il ciclo di vita del report
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1312e56edfb17c57334af263b9f38c3dd97c1894
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81525427"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Connettersi ai set di dati nel servizio Power BI da Power BI Desktop

È possibile stabilire una connessione dinamica a un set di dati condiviso nel *servizio Power BI* e creare report diversi dallo stesso set di dati. Si può creare il modello di dati ideale in Power BI Desktop e pubblicarlo nel servizio Power BI. Partendo da tale modello di dati comune, tutti possono così creare più report diversi (in file con estensione *pbix* separati) e salvarli in aree di lavoro diverse. Questa funzionalità è denominata *Connessione dinamica al servizio Power BI*.

![Ottenere i dati dal servizio Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

Questa funzionalità comporta vari vantaggi, tra cui le procedure consigliate che vengono illustrate in questo articolo. È consigliabile esaminare le [considerazioni e limitazioni](#limitations-and-considerations) di questa funzionalità.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Uso di una connessione dinamica al servizio Power BI per la gestione del ciclo di vita

Uno dei problemi relativi alla popolarità di Power BI è la proliferazione di rapporti, dashboard e dei relativi modelli di dati sottostanti. È facile creare report interessanti in Power BI Desktop e quindi [pubblicarli](desktop-upload-desktop-files.md) nel servizio Power BI e creare dashboard eccezionali in base a tali set di dati. Dato che molti utenti procedono in questo modo, spesso usando gli stessi (o quasi) set di dati, sapere quale report sia basato su quale set di dati e quanto sia aggiornato ogni set di dati è diventato un problema. La connessione dinamica al servizio Power BI risolve questo problema e rende più semplici e coerenti le operazioni di creazione, condivisione ed espansione dei report e dei dashboard dei set di dati comuni.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Creare un set di dati che tutti possano usare, quindi condividerlo

Si supponga che Anna sia un'analista aziendale del team. Anna è specializzata nella creazione di modelli di dati efficaci, spesso denominati set di dati. Anna può creare un set di dati e un report e quindi condividere tale report nel servizio Power BI.

![Pubblicare nel servizio Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Tutti apprezzano il report e il set di dati di Anna ed è qui che iniziano i guai: ogni membro del team vuole provare a creare una *versione personalizzata* del set di dati e quindi condividere i propri report con il team. All'improvviso, l'area di lavoro del team nel servizio Power BI si riempie di moltissimi report, provenienti da diversi set di dati. Qual è il più recente? I set di dati erano gli stessi o quasi? Quali erano le differenze? Con la funzionalità di connessione dinamica al servizio Power BI, tutto questo può cambiare in meglio. Nella sezione successiva si vedrà in che modo gli altri colleghi possono usare il set di dati pubblicato da Anna per personalizzare i report nelle proprie aree di lavoro e consentire a chiunque di usare lo stesso set di dati comune, esaminato e pubblicato per compilare i report univoci.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Connettersi a un set di dati del servizio Power BI usando una connessione dinamica

Anna crea un report e il set di dati su cui si basa. Lo pubblica quindi nel servizio Power BI. Il report viene visualizzato nell'area di lavoro del team nel servizio Power BI. Se Anna lo salva in un'*area di lavoro della nuova esperienza*, può impostare l'*autorizzazione di compilazione* affinché il report diventi disponibile per la visualizzazione e l'uso per tutti i colleghi all'interno o all'esterno della sua area di lavoro.

Per altre informazioni sulle aree di lavoro della nuova esperienza, vedere le [aree di lavoro](service-new-workspaces.md).

Altri membri all'interno e all'esterno dell'area di lavoro di Anna possono ora stabilire una connessione dinamica al suo modello di dati condiviso usando la funzionalità di connessione dinamica al servizio Power BI. Possono creare report personalizzati basati sul *set di dati originale* nelle *proprie aree di lavoro della nuova esperienza*.

Nella figura seguente si vede come Anna crea un report di Power BI Desktop e lo pubblica (incluso il modello di dati) nel servizio Power BI. Altri colleghi possono quindi connettersi al modello di dati di Anna usando la funzionalità di connessione dinamica al servizio Power BI e creare report personalizzati basati sul set di dati di Anna nelle proprie aree di lavoro.

![Più report basati sullo stesso set di dati](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Se si salva il set di dati in un'[area di lavoro condivisa classica](service-create-workspaces.md), solo i membri di quell'area di lavoro potranno compilare report basandosi sul set di dati in questione. Per stabilire una connessione dinamica al servizio Power BI, il set di dati a cui connettersi deve trovarsi in un'area di lavoro condivisa di cui si è membri.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Procedura dettagliata per usare la connessione dinamica al servizio Power BI

Ora che si conosce l'utilità della funzionalità di connessione dinamica al servizio Power BI e come è possibile usarla come approccio ottimale alla gestione del ciclo di vita del report, si passerà a esaminare i passaggi che portano dall'utile report (e set di dati) di Anna a un set di dati condiviso che i suoi colleghi di Power BI potranno usare.

### <a name="publish-a-power-bi-report-and-dataset"></a>Pubblicare un report e un set di dati di Power BI

Il primo passaggio nella gestione del ciclo di vita del report con una connessione dinamica al servizio Power BI consiste nel creare un report e un set di dati che i colleghi vorranno usare. Anna deve quindi prima *pubblicare* il report da Power BI Desktop. Selezionare **Pubblica** dalla barra multifunzione **Home** in Power BI Desktop.

![Pubblicare un report](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Se Anna non ha ancora eseguito l'accesso all'account del servizio Power BI, viene visualizzata una notifica popup in cui viene chiesto di farlo.

![Accedere a Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

A questo punto, Anna può scegliere l'area di lavoro di destinazione nella quale verranno pubblicati il report e il set di dati. Tenere presente che se Anna salva il report in un'area di lavoro della nuova esperienza, chiunque abbia l'autorizzazione di creazione potrà accedere al set di dati. L'autorizzazione di compilazione viene impostata nel servizio Power BI dopo la pubblicazione. Se il lavoro viene salvato in un'area di lavoro classica, solo i membri che hanno accesso all'area di lavoro in cui è pubblicato il report potranno accedere al relativo set di dati usando la funzionalità di connessione dinamica al servizio Power BI.

![Pubblicare nel servizio Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

Inizia il processo di pubblicazione e Power BI Desktop visualizza lo stato di avanzamento.

![Pubblicazione in corso](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Una volta completato, Power BI Desktop visualizza l'esito positivo e indica alcuni collegamenti al report stesso nel servizio Power BI e un collegamento per ottenere informazioni rapide sul report.

![Pubblicazione riuscita](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Ora che il report con il relativo set di dati si trova nel servizio Power BI, è anche possibile *promuoverlo* per attestarne la qualità e l'affidabilità. È anche possibile richiedere che sia *certificato* da un'autorità centrale nel tenant di Power BI. Con una di queste approvazioni, il set di dati viene sempre visualizzato all'inizio dell'elenco ogni volta che si esegue una ricerca di set di dati. Per altre informazioni, vedere [Promuovere il set di dati](service-datasets-promote.md).

L'ultimo passaggio consiste nell'impostare l'autorizzazione di compilazione per il set di dati su cui è basato il report. L'autorizzazione di compilazione determina chi può visualizzare e usare il set di dati. È possibile impostarla nell'area di lavoro stessa o quando si condivide un'app dall'area di lavoro. Per altre informazioni, vedere [Autorizzazione di compilazione per set di dati condivisi](service-datasets-build-permissions.md).

Vediamo ora in che modo gli altri colleghi che hanno accesso all'area di lavoro in cui sono stati pubblicati il report e il set di dati possono connettersi al set di dati e creare report personalizzati.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Stabilire una connessione dinamica al servizio Power BI con il set di dati pubblicato

Per stabilire una connessione al report pubblicato e creare un report personalizzato sulla base del set di dati pubblicato, selezionare **Recupera dati** dalla barra multifunzione **Home** in Power BI Desktop, selezionare **Power Platform** dal riquadro sinistro e quindi selezionare **Set di dati Power BI**.

Se non è stato fatto, Power BI chiede di eseguire l'accesso. Una volta eseguito l'accesso, Power BI visualizza le aree di lavoro di cui si è membri. È possibile selezionare l'area di lavoro contenente il set di dati per il quale si desidera stabilire una connessione dinamica al servizio Power BI.

I set di dati elencati sono tutti set di dati condivisi per i quali si ha autorizzazione di compilazione in qualsiasi area di lavoro. È possibile eseguire la ricerca di un set di dati specifico e visualizzarne il nome, il proprietario, l'area di lavoro in cui si trova e la data dell'ultimo aggiornamento. Nella parte superiore dell'elenco è anche possibile visualizzare l'**APPROVAZIONE** dei set di dati, per verificare se sono certificati o promossi.

![Elenco di set di dati disponibili](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

Quando si seleziona **Crea** viene stabilita una connessione dinamica al set di dati selezionato. Power BI Desktop carica in tempo reale i campi e i relativi valori visualizzati in Power BI Desktop.

![Campi di set di dati nel riquadro Campi](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

A questo punto tutti possono creare e condividere i report personalizzati dallo stesso set di dati. Questo approccio è un ottimo modo per fare sì che una persona esperta, come Anna in questo esempio, crei un set di dati utile e corretto. Molti colleghi possono usare il set di dati condiviso per creare report personalizzati.

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Quando si usa la connessione dinamica al servizio Power BI occorre tenere presenti alcune limitazioni e considerazioni.

* Solo gli utenti con autorizzazione di compilazione per un set di dati possono connettersi a un set di dati pubblicato usando la funzionalità di connessione dinamica al servizio Power BI.
* Gli utenti del piano gratuito visualizzano solo i set di dati dell'**Area di lavoro personale** e delle aree di lavoro con capacità Premium.
* Poiché si tratta di una connessione dinamica, la navigazione a sinistra e la modellazione sono disabilitate. È possibile connettersi a un solo set di dati in ogni report. Questo comportamento è simile a quello riscontrato quando si è connessi a *SQL Server Analysis Services*.
* Poiché si tratta di una connessione dinamica, viene applicata la sicurezza a livello di riga (RLS) e altri comportamenti di connessione simili. Questo comportamento si ha anche quando si è connessi a SQL Server Analysis Services.
* Se si modifica il file originale con estensione *pbix* condiviso, il set di dati e il report condivisi nel servizio Power BI vengono sovrascritti. I report basati su tale set di dati non vengano sovrascritti, ma eventuali modifiche al set di dati saranno visibili nel report.
* I membri di un'area di lavoro non possono sostituire il report condiviso in origine. Se si prova a farlo, verrà visualizzato un avviso che richiede di rinominare il file e pubblicarlo.
* Se si elimina il set di dati condiviso nel servizio Power BI, gli altri report basati su tale set di dati non funzioneranno più correttamente né visualizzeranno gli oggetti visivi.
* Per i pacchetti di contenuto, è necessario creare una copia di un pacchetto di contenuto prima di usarlo come base per la condivisione di un report con estensione *pbix* e un set di dati con il servizio Power BI.
* Per i pacchetti di contenuto da *Organizzazione*, dopo aver eseguito la copia non è possibile sostituire il report creato nel servizio o un report creato come parte della copia di un pacchetto di contenuto con una connessione dinamica. Se si prova a farlo, verrà visualizzato un avviso che richiede di rinominare il file e pubblicarlo. In questo caso, è possibile sostituire solo i report pubblicati con connessione dinamica.
* Se viene eliminato un set di dati condiviso nel servizio Power BI, nessuno potrà più accedere a tale set di dati da Power BI Desktop.
* I report che condividono un set di dati nel servizio Power BI non supportano le distribuzioni automatiche con l'API REST di Power BI.
