---
title: Suggerimenti per la creazione di app modello in Power BI (anteprima)
description: Suggerimenti per la creazione di query, modelli di dati, report e dashboard per app modello efficaci
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/05/2019
ms.author: maggies
ms.openlocfilehash: 282638c7c1c8a60ee93292602766d63fd0fe436e
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249855"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>Suggerimenti per la creazione di app modello in Power BI (anteprima)

Il processo di [creazione di un'app modello](service-template-apps-create.md) in Power BI include la logistica per creare l'area di lavoro, il test e la produzione. L'altro aspetto importante del processo di creazione è la creazione del report e del dashboard. Il processo di creazione può essere suddiviso in quattro componenti principali. Il lavoro su questi componenti consente di creare la miglior app modello possibile:

* Le **query** consentono di [connettere](desktop-connect-to-data.md) e [trasformare](desktop-query-overview.md) i dati e definire i [parametri](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* Nel **modello di dati** si creano le [relazioni](desktop-create-and-manage-relationships.md), le [misure](desktop-measures.md) e i miglioramenti di Domande e risposte.  
* Le **[pagine dei report](desktop-report-view.md)** includono oggetti visivi e filtri che consentono di offrire informazioni dettagliate sui dati.  
* I **[dashboard](consumer/end-user-dashboards.md)** e i [riquadri](service-dashboard-create.md) offrono una panoramica delle informazioni dettagliate incluse.  

Ogni elemento potrebbe essere noto come funzionalità di Power BI esistente. Quando si compila un'app modello è necessario considerare altri aspetti per ogni singolo componente. Vedere le sezioni seguenti per ulteriori dettagli.

<a name="queries"></a>

## <a name="queries"></a>Queries
Per le app modello, le query sviluppate in Power BI Desktop vengono usate per connettere l'origine dati e importare i dati. Queste query sono necessarie per restituire uno schema coerente e sono supportate per l'aggiornamento dei dati pianificato (DirectQuery non è supportata).

### <a name="connect-to-your-api"></a>Connettersi all'API
Per iniziare, è necessario connettersi all'API da Power BI Desktop per avviare la compilazione delle query.

È possibile usare i connettori di dati che sono disponibili per impostazione predefinita in Power BI Desktop per connettersi all'API. È possibile usare il connettore dati Web (Recupera dati -> Web) per connettersi all'API Rest oppure il connettore OData (Recupera dati -> Feed OData) per connettersi al proprio feed OData. Questi connettori possono essere usati immediatamente solo se l'API supporta l'autenticazione di base.

> [!NOTE]
> Se l'API usa altri tipi di autenticazione, ad esempio OAuth 2.0 o la chiave API Web, è necessario sviluppare il proprio connettore dati per consentire a Power BI Desktop di connettersi correttamente ed eseguire l'autenticazione nell'API. Per informazioni dettagliate su come sviluppare il proprio connettore dati per l'app modello, vedere la [documentazione sui connettori dati](https://aka.ms/DataConnectors). 
>
>

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
>


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

> [!NOTE]
> Poiché è possibile includere un solo report in un'app modello, usare le diverse pagine per richiamare sezioni specifiche dello scenario.
>
>

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

> [!NOTE]
> Le app modello richiedono un singolo report e set di dati per ogni app modello. Non aggiungere contenuto di più report o set di dati al dashboard usato nell'app modello.
>
>

### <a name="additional-dashboard-tips"></a>Suggerimenti aggiuntivi per il dashboard

* Mantenere lo stesso tema durante l'aggiunta per garantire la coerenza dei riquadri nel dashboard.  
* Aggiungere un logo al tema in modo che i clienti conoscano l'origine del pacchetto.  
* Il layout consigliato per la maggior parte delle risoluzioni dello schermo prevede la presenza di 5-6 riquadri di piccole dimensioni.  
* Tutti i riquadri del dashboard devono avere titoli o sottotitoli appropriati.  
* Prendere in considerazione i raggruppamenti nel dashboard per diversi scenari, verticalmente oppure orizzontalmente.  

## <a name="known-limitations"></a>Limitazioni note

| Funzionalità | Limitazione nota |
|---------|---------|
|Contenuto:  Datasets   | È necessario che sia presente un solo set di dati. Sono consentiti solo i set di dati creati in Power BI Desktop (file con estensione pbix). <br>Non supportati: Set di dati di altre app modello, set di dati di più aree di lavoro, report impaginati (file con estensione rdl), cartelle di lavoro di Excel |
|Contenuto: Report     | Un solo report    |
| Contenuto: Dashboard | Un solo dashboard non vuoto <br>Non supportati: Riquadri in tempo reale (PushDataset o pubnub non supportato) |
| Contenuto: Dataflows | Non supportati: Dataflows |
| Contenuti dei file | Sono supportati solo i file PBIX. <br>Non supportati: file con estensione rdl (report impaginati), cartelle di lavoro di Excel   |
| Origini dati | Le origini dati supportate per l'aggiornamento dati pianificato nel cloud sono consentite. <br>Non supportati: <br>DirectQuery <br>Connessioni dinamiche (non Azure AD) <br>Origini dati locali (gateway personali e aziendali non sono supportati) <br>Tempo reale (pushdataset non supportato) <br>Modelli compositi |
| Set di dati: di più aree di lavoro | Non sono consentiti set di dati di più aree di lavoro  |
| Contenuto: Dashboard | Non sono consentiti riquadri in tempo reale (PushDataset o pubnub non supportato) |
| Parametri di query | Non supportati: Parametri di tipo "Any" o "Binary" bloccano l'operazione di aggiornamento per il set di dati |
| Oggetti visivi personalizzati | Sono supportati solo gli oggetti visivi personalizzati disponibili pubblicamente. [Oggetti visivi personalizzati dell'organizzazione](power-bi-custom-visuals-organization.md) non supportati |

## <a name="next-steps"></a>Passaggi successivi

[Che cosa sono le app modello di Power BI? (anteprima)](service-template-apps-overview.md)