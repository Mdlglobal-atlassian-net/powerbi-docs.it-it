---
title: Creare pacchetti di contenuto modello in Power BI
description: Creazione di pacchetti di contenuto modello
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 10/09/2017
ms.author: maghan
ms.openlocfilehash: 9b8de53534c94ad995e2d953cfc6994b93915bd8
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="author-template-content-packs-in-power-bi"></a>Creare pacchetti di contenuto modello in Power BI
La creazione di un pacchetto di contenuto modello usa Power BI Desktop e PowerBI.com. Per il pacchetto di contenuto esistono quattro componenti:

* Query, che consentono di [connettersi](../desktop-connect-to-data.md) e [trasformare](../desktop-query-overview.md) i dati, nonché di definire [parametri](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* Modello di dati per creare [relazioni](../desktop-create-and-manage-relationships.md), [misure](../desktop-measures.md), e i miglioramenti di domande e risposte  
* [Pagine](../desktop-report-view.md) di report, che includono elementi visivi e filtri per fornire informazioni sui dati  
* [Dashboard](../service-dashboards.md) e [riquadri](../service-dashboard-create.md), che offrono una panoramica delle informazioni incluse  

Ogni elemento potrebbe essere noto come funzionalità di Power BI esistente. Quando si compila un pacchetto di contenuto, esistono altri fattori da considerare per ogni aspetto; vedere le singole sezioni di seguito per maggiori informazioni.

<a name="queries"></a>

## <a name="queries"></a>Query
Per i pacchetti di contenuto modello, le query sviluppate in Power BI Desktop vengono usate per connettersi all'origine dati e importare i dati. Queste query sono necessarie per restituire uno schema coerente e sono supportate per l'aggiornamento dati pianificato (la query diretta non è supportata).

I pacchetti di contenuto modello supportano una sola origine dati per ogni pacchetto di contenuto, quindi definire le query con attenzione. Una singola origine dati è definita come un'origine che richiede la stessa autenticazione. Se tutte le chiamate vengono eseguite allo stesso endpoint API e usano la stessa autenticazione, è possibile effettuare più chiamate API in query diverse. I pacchetti di contenuto di Power BI non supportano più origini che richiedono criteri di autenticazione diversi.

### <a name="connect-to-your-api"></a>Connettersi all'API
Per iniziare, è necessario connettersi all'API da Power BI Desktop per avviare la compilazione di query.

È possibile usare i connettori di dati che sono disponibili per impostazione predefinita in Power BI Desktop per connettersi all'API. È possibile usare il connettore dati Web (Recupera dati -> Web) per connettersi all'API Rest oppure il connettore OData (Recupera dati -> Feed OData) per connettersi al proprio feed OData. Si noti che questi connettori funzioneranno automaticamente solo se l'API supporta l'autenticazione di base.

> [!NOTE]
> Se l'API usa altri tipi di autenticazione, ad esempio OAuth 2.0 o la chiave API Web, sarà necessario sviluppare il proprio connettore dati per consentire a Power BI Desktop di connettersi correttamente e autenticarsi nell'API. Per informazioni dettagliate su come sviluppare il proprio connettore dati per il pacchetto di contenuto, vedere la documentazione sui connettori dati [qui](https://aka.ms/DataConnectors). 
> 
> 

### <a name="consider-the-source"></a>Considerare l'origine
Le query definiscono i dati che verranno inclusi nel modello di dati. A seconda delle dimensioni del sistema, le query devono includere anche i filtri per garantire che i clienti usino una dimensione gestibile, idonea allo scenario aziendale.

I pacchetti di contenuto di Power BI possono eseguire più query in parallelo e per più utenti contemporaneamente.  Pianificare in anticipo la strategia di concorrenza e limitazione delle richieste e rivolgersi a Microsoft per informazioni su come rendere il pacchetto di contenuto a tolleranza d'errore.

### <a name="schema-enforcement"></a>Imposizione dello schema
Verificare che le query siano resilienti alle modifiche nel sistema perché le modifiche dello schema al momento dell'aggiornamento possono causare interruzioni del modello. Se l'origine può restituire uno schema null o mancante per alcune query, provare a restituire una tabella vuota o a generare messaggi di errore personalizzati che siano significativi per l'utente.

### <a name="parameters"></a>Parametri
I [parametri](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) in Power BI Desktop consentono agli utenti di fornire i valori di input che consentono di personalizzare i dati recuperati dall'utente. Considerare subito i parametri per evitare di dover effettuare rielaborazioni dopo aver dedicato molto tempo alla creazione di query o report dettagliati.

> [!NOTE]
> Attualmente i pacchetti di contenuto modello supportano solo i parametri di testo. Durante lo sviluppo è possibile usare altri tipi di parametri, ma durante la parte di [test](template-content-pack-testing.md#templates) tutti i valori forniti dagli utenti saranno letterali.
> 
> 

### <a name="additional-query-tips"></a>Suggerimenti aggiuntivi per le query
* Verificare che tutte le colonne siano tipizzate in modo appropriato  
* Le colonne presentano nomi descrittivi (vedere domande e risposte)  
* Per la logica condivisa, è consigliabile usare le funzioni o le query  
* I livelli di privacy non sono attualmente supportati nel servizio; se viene visualizzato un prompt dei comandi sui livelli di privacy, potrebbe essere necessario riscrivere la query per usare i percorsi relativi  

## <a name="data-model"></a>Modello di dati
Un modello di dati ben definito assicura che i clienti possano interagire in modo facile e intuitivo con il pacchetto di contenuto. Creare il modello di dati in Power BI Desktop.

> [!NOTE]
> La maggior parte della modellazione di base (tipizzazione, nomi di colonna) deve essere eseguita nelle [query](#queries).
> 
> 

### <a name="qa"></a>Domande e risposte
La modellazione avrà effetto anche sul modo in cui le domande e risposte possono fornire risultati per i clienti. Assicurarsi di aggiungere sinonimi alle colonne usate di frequente e che le colonne siano denominate in modo corretto nelle [query](#queries).

### <a name="additional-data-model-tips"></a>Suggerimenti aggiuntivi per il modello di dati
* A tutte le colonne di valore è applicata la formattazione
    >[!NOTE]
    >I tipi devono essere applicati nella query.  
* La formattazione è applicata tutte le misure  
* Il riepilogo predefinito è impostato, in particolare "Non riepilogare", se applicabile (ad esempio, per i valori univoci)  
* La categoria di dati è stata impostata, se applicabile  
* Le relazioni sono impostate, in base alle esigenze  

## <a name="reports"></a>Relazioni
Le pagine del report offrono maggiori informazioni sui dati inclusi nel pacchetto di contenuto. Usare le pagine dei report per rispondere alle principali domande aziendali che il pacchetto di contenuto cerca di risolvere. Creare il report usando Power BI Desktop.

> [!NOTE]
> È possibile includere un solo report in un pacchetto di contenuto; sfruttare le diverse pagine per richiamare sezioni specifiche dello scenario.
> 
> 

### <a name="additional-report-tips"></a>Suggerimenti aggiuntivi per i report
* Usare più di un elemento visivo per ogni pagina per il filtro incrociato  
* Allineare attentamente gli elementi visivi (evitare la sovrapposizione)  
* Impostare la pagina sulla modalità di layout "4:3" o "16:9"  
* Tutte le aggregazioni presentate devono essere significative dal punto di vista numerico (medie, valori univoci)  
* Il sezionamento deve produrre risultati razionali  
* Il logo deve essere presente almeno nel report principale  
* Gli elementi devono essere resi, per quanto possibile, nella combinazione di colori del cliente  

<a name="dashboard"></a>

## <a name="dashboard"></a>Dashboard
Il dashboard è il principale punto di interazione con il pacchetto di contenuto per i clienti. Deve includere una panoramica del contenuto, in particolare le metriche importanti per lo scenario aziendale.

Per creare un dashboard per il pacchetto di contenuto modello, è sufficiente caricare il PBIX usando Recupera dati > File o la pubblicazione diretta da Power BI Desktop.

> [!NOTE]
> I pacchetti di contenuto modello richiedono un singolo report e set di dati per ogni pacchetto di contenuto. Non aggiungere contenuto di più report o set di dati al dashboard usato nel pacchetto di contenuto.
> 
> 

### <a name="additional-dashboard-tips"></a>Suggerimenti aggiuntivi per il dashboard
* Mantenere lo stesso tema durante l'aggiunta per garantire la coerenza dei riquadri nel dashboard  
* Aggiungere un logo al tema in modo che i clienti conoscano l'origine del pacchetto  
* Il layout consigliato per la maggior parte delle risoluzioni dello schermo prevede la presenza di 5-6 riquadri di piccole dimensioni  
* Tutti i riquadri del dashboard devono avere titoli o sottotitoli appropriati  
* Prendere in considerazione i raggruppamenti nel dashboard per diversi scenari, verticalmente oppure orizzontalmente  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>Riepilogo delle restrizioni
Come indicato nelle sezioni precedenti, i pacchetti di contenuto modello presentano una serie di restrizioni:  

| Supportato | *Non supportato* |
| --- | --- |
| Set di dati integrati in PB Desktop |*Set di dati di altri pacchetti di contenuto o input, ad esempio i file Excel* |
| Origine dati supportata per l'aggiornamento nel cloud di dati pianificati |*La query diretta o la connettività locale non è supportata* |
| Query che restituiscono uno schema coerente o errori laddove appropriato |*Schemi dinamici o personalizzati* |
| Una sola origine dati per ogni set di dati |*Più origini dati, ad esempio mashup o URL che vengono rilevati come più origini dati* |
| Parametri di tipo testo |*Altri tipi di parametro (ad esempio la data) o "elenco consentito di valori"* |
| Un solo dashboard, report e set di dati |*Più dashboard, report o set di dati* |

## <a name="next-step"></a>Passaggio successivo
[Test e invio dei pacchetti di contenuto](template-content-pack-testing.md)

