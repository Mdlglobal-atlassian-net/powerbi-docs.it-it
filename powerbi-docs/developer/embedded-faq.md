---
title: Domande frequenti su Power BI Embedded
description: Esplorare un elenco di domande frequenti e risposte relative a Power BI Embedded.
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
ms.date: 03/07/2018
ms.author: maghan
ms.openlocfilehash: 52ff1095c063be867354a23e0e8e4908a4b4e1d7
ms.sourcegitcommit: ee5d044db99e253c27816e0ea6bdeb9e39a2cf41
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Domande frequenti su Power BI Embedded

* Per altre domande, [provare a rivolgersi alla community di Power BI](http://community.powerbi.com/).
* Ci sono ancora problemi? Visitare la [pagina del supporto tecnico di Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Generale

### <a name="what-is-power-bi-embedded"></a>Che cos'è Power BI Embedded?

Microsoft Power BI Embedded consente agli sviluppatori di applicazioni di incorporare straordinari riquadri, dashboard e report completamente interattivi nelle applicazioni evitando i tempi e i costi derivanti dalla creazione di controlli e visualizzazioni dei dati da zero.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>A chi è destinato Power BI Embedded?

A sviluppatori e aziende di sviluppo software che creano applicazioni personalizzate, anche denominate fornitori di software indipendenti (ISV).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual è la differenza tra Power BI Embedded e il servizio Power BI?

Power BI Embedded è destinato a ISV o sviluppatori che creano applicazioni e che vogliono incorporare oggetti visivi in tali applicazioni per consentire ai clienti di prendere decisioni senza dover creare una soluzione di analisi da zero. Le analisi incorporate permettono agli utenti aziendali di accedere ai dati aziendali ed eseguire query per generare informazioni dettagliate basate sui dati all'interno dell'applicazione.

Power BI, invece, è una soluzione di analisi distribuita come servizio che offre alle organizzazioni una visualizzazione centralizzata dei dati aziendali più strategici.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual è la differenza tra Power BI Premium e Power BI Embedded?

Power BI Premium garantisce una capacità destinata alle aziende che necessitano di una soluzione di business intelligence completa che offra una visualizzazione centralizzata dell'organizzazione stessa, dei partner, dei clienti e dei fornitori. Power BI Premium semplifica il processo decisionale dell'organizzazione. Power BI Premium è un prodotto SaaS e permette agli utenti di fruire del contenuto tramite il portale di Power BI, l'app per dispositivi mobili e app sviluppate internamente.

Power BI Embedded è destinato a ISV o sviluppatori che creano applicazioni e che vogliono incorporare oggetti visivi in tali applicazioni. Power BI Embedded agevola i processi decisionali dei clienti e poiché è progettato per gli sviluppatori di applicazioni, i clienti di queste applicazioni possono fruire del contenuto archiviato nella capacità di Power BI Embedded, che si trovino all'interno o all'esterno dell'organizzazione. Il contenuto della capacità di Power BI Embedded non può essere condiviso tramite pubblicazione con un clic sul Web o su SharePoint e non supporta i report SSRS.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Quali sono le indicazioni di Microsoft per scegliere tra Power BI Premium e Power BI Embedded?

Secondo le indicazioni di Microsoft, le aziende dovrebbero acquistare Power BI Premium, una soluzione di business intelligence cloud self-service di livello aziendale, mentre gli ISV dovrebbero acquistare Power BI Embedded, ovvero componenti di analisi incorporati basati sul cloud. Non esistono tuttavia restrizioni in merito al prodotto che un cliente può acquistare.

In alcuni casi, un ISV (in genere di grandi dimensioni) avrà la necessità di usare uno SKU P per usufruire dei vantaggi aggiuntivi offerti dal servizio Power BI preconfezionato all'interno dell'organizzazione, nonché di incorporare gli oggetti visivi nelle applicazioni che sviluppa. Allo stesso modo, un'azienda può decidere di usare SKU A in Azure, se è interessata solo a creare applicazioni line-of-business incorporandovi le analisi e non necessita del servizio Power BI preconfezionato.

### <a name="how-many-embed-tokens-can-i-create"></a>Quanti token di incorporamento è possibile creare?

I token di incorporamento con licenza Pro sono destinati alle attività di sviluppo e test, pertanto il numero di token di incorporamento che un account master Power BI può generare è limitato. È necessario [acquistare una capacità](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) per l'incorporamento in un ambiente di produzione. Dopo l'acquisto della capacità è possibile generare un numero illimitato di token di incorporamento.

### <a name="when-will-power-bi-embedded-be-available-in-azure"></a>Quando sarà disponibile Power BI Embedded in Azure?

Power BI Embedded è ora disponibile.

## <a name="technical"></a>Informazioni tecniche

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Qual è la differenza tra gli SKU A in Azure e gli SKU EM in Office 365?

PowerBI.com è una soluzione aziendale che include molte funzionalità, come la collaborazione tramite social network, la sottoscrizione dei messaggi di posta elettronica e così via, in un'offerta SaaS (software distribuito come servizio)

Power BI Embedded è un set di API per sviluppatori che consente di creare una soluzione di analisi incorporata in un'offerta PaaS (piattaforma distribuita come servizio). Per lo scenario di analisi incorporata, è necessario usare PowerBI.com per semplificare a ISV e sviluppatori la gestione del contenuto della soluzione di analisi incorporata e delle impostazioni a livello del tenant.

Di seguito è riportato un elenco parziale con le differenze che è possibile usare con ognuno di essi.

|Funzionalità  |Power BI Embedded<br>(SKU A) |Capacità Power BI Premium<br>(SKU EM)  |
|---------|---------|---------|
|Incorporamento di elementi dalle aree di lavoro dell'app Power BI     |Capacità di Azure |Capacità di Office 365 |
|Licenza di Power BI necessaria per utilizzare i report |No  |Sì |
|Utilizzo dei report di Power BI in un'applicazione incorporata |Sì  |Sì |
|Utilizzo dei report di Power BI in SharePoint |No |Sì |
|Utilizzo dei report di Power BI in Microsoft Teams |No |Sì |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Ora Power BI offre tre SKU per l'incorporamento, gli SKU A, gli SKU EM e gli SKU P. Quale devo acquistare per il mio scenario?

|  |SKU A (Power BI Embedded)  |SKU EM (Power BI Premium)  |SKU P (Power BI Premium)  |
|---------|---------|---------|---------|
|Acquista     |Portale di Azure |Office |Office |
|Casi d'uso |* Incorporamento di contenuto in un'applicazione personalizzata |* Incorporamento di contenuto in un'applicazione personalizzata<br>* Condivisione di contenuto con utenti della versione GRATUITA di Power BI all'esterno di PowerBI.com e incorporamento in altre applicazioni SaaS (SharePoint, Microsoft Teams) |* Incorporamento di contenuto in un'applicazione personalizzata<br>* Condivisione di contenuto con utenti della versione GRATUITA di Power BI all'esterno di PowerBI.com e incorporamento in altre applicazioni SaaS (SharePoint, Microsoft Teams)<br>* Condivisione di contenuto con gli utenti della versione GRATUITA di Power BI tramite PowerBI.com  |
|Fatturazione |Ogni ora |Mensile |Mensile |
|Impegno  |Nessun impegno |Annuale  |Mensile/Annuale |
|Differenze |Elasticità completa: aumento/riduzione delle prestazioni, sospensione/ripresa delle risorse nel portale di Azure o tramite l'API  |Consente di incorporare contenuto in SharePoint Online e Microsoft Teams |Combina l'incorporamento nelle applicazioni e usa il servizio Power BI nella stessa capacità |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quali sono i prerequisiti per creare una capacità PBIE in Azure?

- È necessario accedere alla directory dell'organizzazione (gli account MSA non sono supportati).
- È necessario avere un tenant di Power BI, ovvero è necessario che almeno un utente nella directory abbia effettuato l'iscrizione a Power BI. 
- È necessario avere una sottoscrizione di Azure nella directory dell'organizzazione.

### <a name="how-can-i-monitor-capacity-consumption"></a>Come si può monitorare l'utilizzo della capacità?

Il monitoraggio tramite Azure sarà implementato nel breve termine. La risorsa di Azure, Power BI Embedded, includerà indicatori KPI che mostreranno l'integrità e l'utilizzo.

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>La capacità si ridimensiona automaticamente in base all'utilizzo dell'app?

Al momento il ridimensionamento automatico non è disponibile, ma è possibile ridimensionare le API in qualsiasi momento.

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Qual è il modello di autenticazione per Power BI Embedded?

Power BI Embedded continuerà a usare Azure AD per l'autenticazione dell'utente master (un utente con licenza di Power BI Pro designato), autenticando l'applicazione all'interno di Power BI.

L'autenticazione e l'autorizzazione degli utenti dell'applicazione verranno implementate dall'ISV e quest'ultimo potrà implementare un'autenticazione personalizzata per le relative applicazioni.

Se si dispone già di un tenant di Azure AD, è possibile usare la directory esistente oppure si può creare un nuovo tenant di Azure AD per la sicurezza del contenuto dell'applicazione incorporato.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual è la differenza tra Power BI Embedded e altri servizi di Azure?

L'ISV/sviluppatore deve avere un account Power BI per poter acquistare Power BI Embedded in Azure. L'area di distribuzione di Power BI Embedded è determinata dall'account Power BI. Gestire la risorsa Power BI Embedded per:

* Aumentare e ridurre le prestazioni
* Aggiungere amministratori della capacità
* Sospendere e riprendere il servizio

Usare PowerBI.com per assegnare o annullare l'assegnazione di aree di lavoro alla capacità di Power BI Embedded.

### <a name="what-deploy-regions-are-supported"></a>Quali sono le aree di distribuzione supportate?

Australia sud-orientale, Brasile meridionale, Canada centrale, Stati Uniti orientali 2, India occidentale, Giappone orientale, Stati Uniti centro-settentrionali, Europa settentrionale, Stati Uniti centro-meridionali, Asia sud-orientale, Regno Unito meridionale, Europa occidentale, Stati Uniti occidentali e Stati Uniti occidentali 2.

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>Quali tipi di dati del pacchetto di contenuto è possibile incorporare?

I **dashboard** e i **riquadri** che sono compilati dal set di dati del pacchetto di contenuto *non possono* essere incorporati, mentre i **report** compilati da un set di dati del pacchetto di contenuto *possono* essere incorporati.

## <a name="licensing"></a>Gestione delle licenze

### <a name="how-do-i-purchase-power-bi-embedded"></a>Come si acquista Power BI Embedded?

Power BI Embedded è disponibile tramite Azure.

### <a name="how-power-bi-embedded-be-metered"></a>In che modo verrà misurato Power BI Embedded?

Power BI Embedded avrà un contatore orario.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>In che modo verrà visualizzato l'utilizzo di Power BI Embedded nella fattura?

Power BI Embedded viene fatturato secondo una tariffa oraria prevedibile in base al tipo di nodi distribuiti. Si noti che mentre la risorsa è attiva il costo corrispondente continua a essere addebitato, anche se la risorsa non viene usata. Per interrompere l'addebito è necessario intervenire per sospendere la risorsa. La sospensione può essere eseguita tramite Azure o tramite le API di ARM.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>Che cosa accade se ho già acquistato Power BI Premium e ora desidero usufruire di alcuni dei vantaggi offerti da Power BI Embedded in Azure?

I clienti continueranno a pagare gli eventuali acquisti di Power BI Premium esistenti fino al termine del contratto e a quel punto potranno scegliere se sostituire le licenze di Power BI Premium in base alle esigenze.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>È comunque necessario acquistare Power BI Premium per avere accesso a Power BI Embedded?

No. Power BI Embedded include la capacità basata su Azure necessaria per distribuire la soluzione ai clienti.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Chi necessita di una licenza di Power BI Pro per Power BI Embedded e perché?

Gli analisti che devono aggiungere report a un'area di lavoro di Power BI, gli sviluppatori che devono usare le API REST e gli amministratori del tenant che devono gestire la capacità e il tenant di Power BI necessitano di una licenza di Power BI Pro.

Poiché Power BI Embedded consente l'uso del portale di Power BI per gestire e convalidare il contenuto incorporato, la licenza di Power BI Pro è necessaria per autenticare l'app in PowerBI.com per accedere ai report nei repository corretti.

### <a name="can-i-get-started-for-free"></a>È possibile iniziare a usare il prodotto gratuitamente?

Sì. È possibile usare i [crediti Azure](https://azure.microsoft.com/free/) per Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>È possibile accedere a un'esperienza di valutazione per Power BI Embedded in Azure?

Poiché Power BI Embedded fa parte di Azure, è possibile usare il servizio con il [credito di $ 200 ricevuto al momento dell'iscrizione ad Azure](https://azure.microsoft.com/free/).

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Qual è l'impegno di acquisto per Power BI Embedded? 

I clienti possono cambiare l'utilizzo su base oraria. Non sono previsti impegni mensili o annuali per il servizio Power BI Embedded.

### <a name="where-is-power-bi-embedded-available-us-government-germany-china-what-is-the-timing"></a>Dove è disponibile Power BI Embedded? US Government? Germania? Cina? Quali sono le tempistiche?

Power BI Embedded è disponibile nei cloud commerciali di Azure e nel cloud del Governo degli Stati Uniti.  In futuro verrà aggiunta la disponibilità dei cloud sovrani per la Germania e la Cina.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded è disponibile per le organizzazioni no profit e gli istituti didattici?

Le organizzazioni no profit e gli istituti didattici possono acquistare Azure. Non sono previsti prezzi speciali per questi tipi di clienti in Azure.

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
