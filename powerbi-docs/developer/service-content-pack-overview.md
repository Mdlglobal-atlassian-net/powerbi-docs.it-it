---
title: Panoramica del programma dei pacchetti di contenuto del servizio Power BI
description: Programma di certificazione dei pacchetti di contenuto
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/20/2018
ms.author: maghan
ms.openlocfilehash: cfb9727a41d602ce14bfd2a403a87e82d2f0e94d
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Panoramica del programma dei pacchetti di contenuto del servizio Power BI
Un pacchetto di contenuto è un set di contenuto predefinito che consente agli utenti di ottenere immediatamente informazioni da un'origine. In genere, un pacchetto di contenuto è incentrato su uno scenario aziendale specifico che fornisce informazioni per un ruolo, un dominio o un flusso di lavoro.

Gli ISV possono compilare pacchetti di contenuto modello che consentono agli utenti di connettersi e creare un'istanza con i propri account. In qualità di esperti di dominio, possono sbloccare i dati in modo da renderli facilmente utilizzabili dagli utenti aziendali. I pacchetti di contenuto offrono ai clienti strumenti di monitoraggio e analisi ad hoc senza necessità di effettuare elevati investimenti di capitale in infrastruttura per la creazione di report. 

Questi pacchetti di contenuto modello compilati dagli ISV possono essere inviati al team di Power BI per renderli disponibili pubblicamente nella raccolta di pacchetti di contenuto di Power BI (app.powerbi.com/getdata/services) e su Microsoft AppSource (appsource.microsoft.com). Un esempio di esperienza di pacchetto di contenuto pubblico è disponibile [qui](template-content-pack-experience.md).

## <a name="overview"></a>Panoramica
Il processo generale di sviluppo e invio di un pacchetto di contenuto modello comporta diversi passaggi.

 ![Processo](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Rivedere i requisiti](#requirements) e assicurarsi di soddisfarli
2. [Creare il contenuto](template-content-pack-authoring.md#queries) in Power BI Desktop
3. [Creare un dashboard](template-content-pack-authoring.md#dashboard) in PowerBI.com
4. [Testare il pacchetto di contenuto](template-content-pack-testing.md) personalmente all'interno dell'organizzazione
5. [Inviare](template-content-pack-testing.md#submission) il contenuto a Power BI per la pubblicazione

<a name="requirements"></a>

## <a name="requirements"></a>Requisiti
Per compilare e inviare un pacchetto di contenuto da pubblicare nel servizio Power BI e in AppSource, è necessario soddisfare i requisiti seguenti:

* Disponibilità di un'applicazione SaaS usata dagli utenti aziendali.
* L'applicazione SaaS contiene dati dell'utente che possono essere visualizzati in Power BI.
* L'applicazione SaaS è un'API accessibile attraverso la rete Internet pubblica. Idealmente l'API è un'API basata su REST o un feed OData. I pacchetti di contenuto di Power BI supportano più tipi di autenticazione come l'autenticazione di base, OAuth 2.0 e Chiave API. 
* L'applicazione SaaS è stata approvata per la pubblicazione di un pacchetto di contenuti. Inviare la richiesta a pbiservicesapps@microsoft.com. La rilevanza e l'utilizzo previsto di ogni invio verranno esaminati. 
* Contratto di partner firmato. Questa operazione verrà eseguita nel [passaggio di invio](template-content-pack-testing.md#submission).

Consultare la sezione [Template Content Pack Authoring](template-content-pack-authoring.md) (Creazione di pacchetti di contenuto modello) per maggiori informazioni sui requisiti tecnici.

## <a name="business-scenario"></a>Scenario aziendale
I pacchetti di contenuto forniscono informazioni e metriche incentrate su uno specifico scenario aziendale. L'identificazione dei destinatari e dei vantaggi che otterranno dal pacchetto di contenuto sarà utile per garantire un uso ottimale del contenuto fornito.

### <a name="tips"></a>Suggerimenti
* Identificare i destinatari e l'attività che intendono eseguire  
* Concentrarsi su un determinato periodo di tempo (ultimi 90 giorni) o sugli ultimi N risultati  
* Importare solo tabelle/colonne correlate allo scenario  
* Valutare la possibilità di offrire più di un pacchetto di contenuto per scenari univoci separati  

## <a name="frequently-asked-questions"></a>Domande frequenti
**Una terza parte può compilare un pacchetto di contenuto del servizio Power BI per un'applicazione SaaS di cui non è proprietaria?**

È necessaria la firma di un contratto tra partner con il proprietario dell'applicazione SaaS prima di pubblicare un pacchetto di contenuto nel servizio. Una terza parte dovrà facilitare la firma del contratto tra partner con il proprietario dell'applicazione SaaS.

**Non è disponibile un'API per sviluppatori pubblica per il servizio. È comunque possibile compilare un pacchetto di contenuto del servizio Power BI che estragga i dati direttamente dall'archivio dati?**

No. I pacchetti di contenuto del servizio Power BI richiedono un'API per sviluppatori che è accessibile attraverso la rete Internet pubblica.

**Quale tipo di API è supportato dai pacchetti di contenuto del servizio e con quali tipi di autenticazione possono funzionare?**

I pacchetti di contenuto del servizio Power BI supportano qualsiasi API REST o feed OData. Power BI può funzionare con più tipi di autenticazione, tra cui l'autenticazione di base, OAuth 2.0 e la chiave API Web. Altre informazioni sui requisiti tecnici sono disponibili nell'articolo [Template Content Pack Authoring](template-content-pack-authoring.md#dashboard) (Creazione di pacchetti di contenuto modello).

**È disponibile un pacchetto di contenuto pubblicato in Power BI. Come è possibile aggiornarlo?**

I pacchetti di contenuto pubblicati possono essere aggiornati una volta al mese. Le richieste di aggiornamento inviate a [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com) entro l'ultimo giorno del mese corrente verranno pubblicate la prima settimana del mese seguente.

**Per altre domande sui pacchetti di contenuto del servizio come è possibile contattarvi?**

Inviare le domande all'indirizzo [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com)

## <a name="support"></a>Support
Per il supporto durante lo sviluppo, usare [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). che viene attivamente monitorato e gestito. Le richieste dei clienti vengono indirizzate rapidamente al team appropriato.

## <a name="next-step"></a>Passaggio successivo
[Creazione](template-content-pack-authoring.md)

