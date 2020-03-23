---
title: Suggerimenti per la creazione di app modello in Power BI
description: Suggerimenti per la creazione di query, modelli di dati, report e dashboard per app modello efficaci
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: tebercov
ms.openlocfilehash: dcb7ba5dabbbb0387b92908f7e299d61f2145d44
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376593"
---
# <a name="tips-for-authoring-template-apps-in-power-bi"></a>Suggerimenti per la creazione di app modello in Power BI

Il processo di [creazione di un'app modello](service-template-apps-create.md) in Power BI include la logistica per creare l'area di lavoro, il test e la produzione. L'altro aspetto importante del processo di creazione è la creazione del report e del dashboard. Il processo di creazione può essere suddiviso in quattro componenti principali. Il lavoro su questi componenti consente di creare la miglior app modello possibile:

* Le **query** consentono di [connettere](desktop-connect-to-data.md) e [trasformare](desktop-query-overview.md) i dati e definire i [parametri](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* Nel **modello di dati** si creano le [relazioni](desktop-create-and-manage-relationships.md), le [misure](desktop-measures.md) e i miglioramenti di Domande e risposte.  
* Le **[pagine dei report](desktop-report-view.md)** includono oggetti visivi e filtri che consentono di offrire informazioni dettagliate sui dati.  
* I **[dashboard](consumer/end-user-dashboards.md)** e i [riquadri](service-dashboard-create.md) offrono una panoramica delle informazioni dettagliate incluse.
* I dati di esempio rendono l'app individuabile immediatamente dopo l'installazione.

Ogni elemento potrebbe essere noto come funzionalità di Power BI esistente. Quando si compila un'app modello è necessario considerare altri aspetti per ogni singolo componente. Vedere le sezioni seguenti per ulteriori dettagli.

<a name="queries"></a>

## <a name="queries"></a>Query
Per le app modello, le query sviluppate in Power BI Desktop vengono usate per connettere l'origine dati e importare i dati. Queste query sono necessarie per restituire uno schema coerente e sono supportate per l'aggiornamento dei dati pianificato (DirectQuery non è supportata).

### <a name="connect-to-your-api"></a>Connettersi all'API
Per iniziare, è necessario connettersi all'API da Power BI Desktop per avviare la compilazione delle query.

È possibile usare i connettori di dati disponibili in Power BI Desktop per connettersi all'API. È possibile usare il connettore dati Web (Recupera dati -> Web) per connettersi all'API Rest oppure il connettore OData (Recupera dati -> Feed OData) per connettersi al proprio feed OData.

> [!NOTE]
> Attualmente le app modello non supportano i connettori personalizzati. È consigliabile esaminare l'uso di Odatafeed Auth 2.0 come mitigazione per alcuni casi d'uso relativi alla connessione oppure inviare un connettore personalizzato per la certificazione. Per informazioni dettagliate su come sviluppare un connettore e ottenere la certificazione, vedere la [documentazione sui connettori di dati](https://aka.ms/DataConnectors).

### <a name="consider-the-source"></a>Considerare l'origine
Le query definiscono i dati inclusi nel modello di dati. A seconda delle dimensioni del sistema, le query devono includere anche i filtri per garantire che i clienti usino una dimensione gestibile, idonea allo scenario aziendale.

Le app modello di Power BI possono eseguire più query in parallelo e per più utenti contemporaneamente.  Pianificare in anticipo la strategia di concorrenza e limitazione delle richieste e rivolgersi a Microsoft per informazioni su come rendere l'app modello a tolleranza di errore.

### <a name="schema-enforcement"></a>Imposizione dello schema
Verificare che le query siano resilienti alle modifiche nel sistema perché le modifiche dello schema al momento dell'aggiornamento possono causare interruzioni del modello. Se l'origine può restituire uno schema Null o mancante per alcune query, provare a restituire una tabella vuota o un messaggio di errore personalizzato significativo.

### <a name="parameters"></a>Parametri
I [parametri](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) in Power BI Desktop consentono agli utenti di fornire i valori di input che consentono di personalizzare i dati recuperati dall'utente. Considerare subito i parametri per evitare di dover effettuare rielaborazioni dopo aver dedicato tempo alla creazione di query o report dettagliati.

> [!NOTE]
> Le app modello supportano tutti i parametri, ad eccezione di Any e Binary.
>

### <a name="additional-query-tips"></a>Suggerimenti aggiuntivi per le query

* Verificare che tutte le colonne siano tipizzate in modo appropriato.
* Le colonne hanno nomi descrittivi (vedere [Domande e risposte](#qa)).  
* Per la logica condivisa, è consigliabile usare le funzioni o le query.  
* I livelli di privacy non sono attualmente supportati nel servizio. Se viene visualizzata una richiesta relativa ai livelli di privacy, può essere necessario riscrivere la query per usare i percorsi relativi.  

## <a name="data-models"></a>Modelli di dati

Un modello di dati ben definito garantisce che i clienti possano interagire in modo facile e intuitivo con l'app modello. Creare il modello di dati in Power BI Desktop.

> [!NOTE]
> La maggior parte della modellazione di base (tipizzazione, nomi di colonna) deve essere eseguita nelle [query](#queries).

### <a name="qa"></a>Domande e risposte
La modellazione ha effetto anche sull'efficacia dei risultati di Domande e risposte per i clienti. Assicurarsi di aggiungere sinonimi alle colonne usate di frequente e che le colonne siano denominate in modo corretto nelle [query](#queries).

### <a name="additional-data-model-tips"></a>Suggerimenti aggiuntivi per il modello di dati

Assicurarsi di avere:

* Applicato la formattazione a tutte le colonne di valori. Applicato i tipi nella query.  
* Applicato la formattazione a tutte le misure.
* Impostato l'esecuzione del riepilogo predefinita. In particolare "Non riepilogare", se applicabile (ad esempio, per i valori univoci).  
* Impostato la categoria di dati, se applicabile.  
* Impostato le relazioni, in base alle esigenze.  

## <a name="reports"></a>Report
Le pagine dei report offrono maggiori informazioni sui dati inclusi nell'app modello. Usare le pagine dei report per rispondere alle principali domande aziendali che l'app modello cerca di risolvere. Creare il report usando Power BI Desktop.


### <a name="additional-report-tips"></a>Suggerimenti aggiuntivi per i report

* Usare più di un oggetto visivo per ogni pagina per il filtro incrociato.  
* Allineare attentamente gli oggetti visivi (evitare la sovrapposizione).  
* Impostare la pagina sulla modalità di layout "4:3" o "16:9".  
* Tutte le aggregazioni presentate devono essere significative dal punto di vista numerico (medie, valori univoci).  
* Il sezionamento deve produrre risultati razionali.  
* Il logo deve essere presente almeno nel report principale.  
* Gli elementi devono essere resi, per quanto possibile, nella combinazione di colori del cliente.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Dashboard
Il dashboard è il principale punto di interazione con l'app modello per i clienti. Deve includere una panoramica del contenuto, in particolare le metriche importanti per lo scenario aziendale.

Per creare un dashboard per l'app modello, è sufficiente caricare il PBIX scegliendo Recupera dati > File o tramite la pubblicazione diretta da Power BI Desktop.


### <a name="additional-dashboard-tips"></a>Suggerimenti aggiuntivi per il dashboard

* Mantenere lo stesso tema durante l'aggiunta per garantire la coerenza dei riquadri nel dashboard.  
* Aggiungere un logo al tema in modo che i clienti conoscano l'origine del pacchetto.  
* Il layout consigliato per la maggior parte delle risoluzioni dello schermo prevede la presenza di 5-6 riquadri di piccole dimensioni.  
* Tutti i riquadri del dashboard devono avere titoli o sottotitoli appropriati.  
* Prendere in considerazione i raggruppamenti nel dashboard per diversi scenari, verticalmente oppure orizzontalmente.  

## <a name="sample-data"></a>Dati di esempio
Le app modello, nella fase di creazione di app, eseguono il wrapping dei dati della cache nell'area di lavoro come parte dell'app:

* Viene consentito al programma di installazione di comprendere la funzionalità e lo scopo dell'app prima della connessione dei dati.
* Viene creata un'esperienza che porta il programma di installazione a esplorare ulteriormente le funzionalità dell'app e, di conseguenza, a connettere il set di dati dell'app.

È consigliabile predisporre dati di esempio di alta qualità prima di creare l'app. Assicurarsi che i dashboard e i report per l'app vengano popolati con dati.

## <a name="publishing-on-appsource"></a>Pubblicazione in AppSource
Le app modello possono essere pubblicate in AppSource. Seguire queste linee guida prima di inviare l'app ad AppSource:

* Assicurarsi di creare un'app modello con dati di esempio significativi, che possono aiutare, in fase di installazione, a comprendere ciò che l'app può fare (report e dashboard vuoti non vengono approvati).
Le app modello supportano le app con soli dati di esempio, assicurarsi di selezionare la casella di controllo relativa all'app statica. [Altre informazioni](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Creare istruzioni che il team di convalida deve seguire includendo le credenziali e i parametri necessari per la connessione ai dati.
* L'applicazione deve includere un'icona dell'app in Power BI e nell'offerta CPP. [Altre informazioni](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Configurare la pagina di destinazione. [Altre informazioni](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Assicurarsi di seguire la documentazione in [Offerta di app Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
* Nel caso in cui un dashboard faccia parte dell'app, assicurarsi che non sia vuoto.
* Installare l'app usando il collegamento all'app prima dell'invio, verificare che sia possibile connettersi al set di dati e che l'esperienza dell'app sia conforme a quanto previsto.
* Prima di caricare il file con estensione pbix nell'area di lavoro modello, assicurarsi di scaricare tutte le connessioni non necessarie.
* Seguire quanto indicato in [Procedure consigliate per la progettazione di report e oggetti visivi](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-best-practices) di Power BI per ottimizzare l'impatto sugli utenti e ottenere l'approvazione per la distribuzione.
<!--- * In general, only application with valuable functionality can be approved for general use on AppSource. Application with sample data content only must have either a guidance or statistical value.) -->

## <a name="create-a-download-link-for-the-app"></a>Creare un collegamento per il download dell'app

Dopo la pubblicazione dell'app modello in AppSource, provare a creare un collegamento di download dal sito Web a:
* Pagina di download di AppSource: può essere visualizzata pubblicamente. Ottenere il collegamento dalla pagina di AppSource.
* Power BI: può essere visualizzato da un utente di Power BI.

Per reindirizzare un utente al collegamento di download dell'app in Power BI, vedere l'esempio di codice seguente: [Repository GitHub](https://github.com/microsoft/Template-apps-examples/tree/master/src).
[![Collegamento di download dell'app](media/service-template-apps-tips/service-template-apps-tips-download.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)



## <a name="known-limitations"></a>Limitazioni note

| Feature | Limitazione nota |
|---------|---------|
|Contenuto:  Set di dati   | È necessario che sia presente un solo set di dati. Sono consentiti solo i set di dati creati in Power BI Desktop (file con estensione pbix). <br>Non supportati: Set di dati di altre app modello, set di dati di più aree di lavoro, report impaginati (file con estensione rdl), cartelle di lavoro di Excel |
|Contenuto: Dashboard | Non sono consentiti riquadri in tempo reale (in altre parole, non è disponibile il supporto per set di dati di push o di streaming) |
|Contenuto: Flussi di dati | Non supportati: Flussi di dati |
|Contenuti dei file | Sono supportati solo i file PBIX. <br>Non supportati: file con estensione rdl (report impaginati), cartelle di lavoro di Excel   |
| Origini dati | Le origini dati supportate per l'aggiornamento dati pianificato nel cloud sono consentite. <br>Non supportati: <li> DirectQuery</li><li>Connessioni dinamiche (non Azure AD)</li> <li>Origini dati locali (i gateway personali e aziendali non sono supportati)</li> <li>Tempo reale (nessun supporto per set di dati di push)</li> <li>Modelli compositi</li></ul> |
| Set di dati: di più aree di lavoro | Non sono consentiti set di dati di più aree di lavoro  |
| Parametri di query | Non supportati: Parametri di tipo "Any" o "Binary" bloccano l'operazione di aggiornamento per il set di dati |
| Oggetti visivi di Power BI | Sono supportati solo gli oggetti visivi di Power BI disponibili pubblicamente. Gli [oggetti visivi di Power BI dell'organizzazione](developer/visuals/power-bi-custom-visuals-organization.md) non sono supportati |

## <a name="next-steps"></a>Passaggi successivi

[Che cosa sono le app modello di Power BI?](service-template-apps-overview.md)
