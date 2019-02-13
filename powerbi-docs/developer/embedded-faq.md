---
title: Domande frequenti su Power BI Embedded
description: Esplorare un elenco di domande frequenti e risposte relative a Power BI Embedded.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: da5394c0d1e63619229542b914ae7fd4deed7447
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56223744"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Domande frequenti su Power BI Embedded

* Per altre domande, [provare a rivolgersi alla community di Power BI](http://community.powerbi.com/).
* Ci sono ancora problemi? Visitare la [pagina del supporto tecnico di Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Generali

### <a name="what-is-power-bi-embedded"></a>Che cos'è Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) consente agli sviluppatori di applicazioni di incorporare straordinari report completamente interattivi nelle applicazioni evitando i tempi e i costi derivanti dalla creazione di controlli e visualizzazioni dei dati da zero.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>A chi è destinato Power BI Embedded?

A sviluppatori e aziende di sviluppo software che creano applicazioni personalizzate, denominati anche fornitori di software indipendenti (ISV).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual è la differenza tra Power BI Embedded e il servizio Power BI?

Power BI Embedded è destinato a ISV o sviluppatori che creano applicazioni e che vogliono incorporare oggetti visivi in tali applicazioni per consentire ai clienti di prendere decisioni senza dover creare una soluzione di analisi da zero. [L'analisi incorporata](embedding.md) consente agli utenti aziendali di accedere ai dati aziendali ed eseguire query per generare informazioni dettagliate basate sui dati all'interno dell'applicazione.

Power BI è una soluzione di analisi distribuita come servizio che offre alle organizzazioni una visualizzazione centralizzata dei dati aziendali più strategici.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual è la differenza tra Power BI Premium e Power BI Embedded?

Power BI Premium garantisce una capacità destinata alle aziende che necessitano di una soluzione di business intelligence completa che offra una visualizzazione centralizzata dell'organizzazione stessa, dei partner, dei clienti e dei fornitori. Power BI Premium semplifica il processo decisionale dell'organizzazione. Power BI Premium è un prodotto SaaS e permette agli utenti di fruire del contenuto tramite il portale di Power BI, l'app per dispositivi mobili e app sviluppate internamente.

Power BI Embedded è destinato a ISV o sviluppatori che creano applicazioni e che vogliono incorporare oggetti visivi in tali applicazioni. Power BI Embedded agevola i processi decisionali dei clienti e poiché è progettato per gli sviluppatori di applicazioni, i clienti di queste applicazioni possono fruire del contenuto archiviato nella capacità di Power BI Embedded, che si trovino all'interno o all'esterno dell'organizzazione. Il contenuto della capacità di Power BI Embedded non può essere condiviso tramite pubblicazione con un clic sul Web o su SharePoint e non supporta i report SSRS.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Quali sono le indicazioni di Microsoft per scegliere tra Power BI Premium e Power BI Embedded?

Microsoft consiglia alle aziende di acquistare Power BI Premium, una soluzione di business intelligence cloud self-service di livello aziendale, mentre gli ISV dovrebbero acquistare Power BI Embedded, vale a dire componenti di analisi incorporati basati sul cloud. Non esistono tuttavia restrizioni in merito al prodotto che un cliente può acquistare.

In alcuni casi, un ISV (in genere di grandi dimensioni) avrà la necessità di usare uno SKU P per usufruire dei vantaggi aggiuntivi offerti dal servizio Power BI preconfezionato all'interno dell'organizzazione, nonché di incorporare gli oggetti visivi nelle applicazioni che sviluppa. Alcune aziende possono decidere di usare SKU A in Azure, se sono interessate solo a creare applicazioni line-of-business incorporandovi le analisi e non necessitano del servizio Power BI preconfezionato.

### <a name="how-many-embed-tokens-can-i-create"></a>Quanti token di incorporamento è possibile creare?

I token di incorporamento con licenza Pro sono destinati al test dello sviluppo, pertanto il numero di token di incorporamento che un account master Power BI o un'[entità servizio](embed-service-principal.md) può generare è limitato. [Acquistare una capacità](#technical) per l'incorporamento in un ambiente di produzione. Dopo l'acquisto della capacità è possibile generare un numero illimitato di token di incorporamento. Vedere [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) (Funzionalità disponibili) per controllare il valore di utilizzo che indica l'attuale utilizzo incorporato espresso come percentuale.

## <a name="technical"></a>Informazioni tecniche

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Qual è la differenza tra gli SKU A in Azure e gli SKU EM in Office 365?

PowerBI.com è una soluzione aziendale che include molte funzionalità, ad esempio la collaborazione, la sottoscrizione dei messaggi di posta elettronica e così via, in un'offerta SaaS (software distribuito come servizio)

Power BI Embedded è un set di API per sviluppatori che consente di creare una soluzione di analisi incorporata in un'offerta PaaS (piattaforma distribuita come servizio). Per lo scenario di analisi incorporata, PowerBI.com semplifica a ISV e sviluppatori la gestione del contenuto della soluzione di analisi incorporata e delle impostazioni a livello del tenant.

Di seguito è riportato un elenco parziale con le differenze che è possibile usare con ognuno di essi.

| Funzionalità | Power BI Embedded | Capacità Power BI Premium | Capacità Power BI Premium |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (SKU A) | (SKU EM) | (SKU P) |
| Incorporamento di artefatti di un'area di lavoro per le app di Power BI | Capacità di Azure | Capacità di Office 365 | Capacità di Office 365 |
| Uso dei report di Power BI in un'applicazione incorporata | Sì | Sì | Sì |
| Utilizzo dei report di Power BI in SharePoint | No | Sì | Sì |
| Utilizzo dei report di Power BI in Dynamics | No | Sì | Sì |
| Utilizzo dei report di Power BI in Teams (esclude l'app per dispositivi mobili) | No | Sì | Sì |
| Accesso ai contenuti con una licenza gratuita di Power BI in Powerbi.com e Power BI per dispositivi mobili | No | No | Sì |
| Accesso ai contenuti con una licenza gratuita di Power BI incorporata nelle app di MS Office | No | Sì | Sì |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Ora Power BI offre tre tipi di SKU per l'incorporamento: SKU A, SKU EM e SKU P. Quale devo acquistare per il mio scenario?

|  |SKU A (Power BI Embedded)  |SKU EM (Power BI Premium)  |SKU P (Power BI Premium)  |
|---------|---------|---------|---------|
|Acquisto  |Portale di Azure |Office |Office |
|Casi d'uso | Incorporamento di contenuto in un'applicazione personalizzata | <li> Incorporamento di contenuto in un'applicazione personalizzata <br><br><br> <li> Incorporamento di contenuto nelle applicazioni di MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (esclude l'app per dispositivi mobili)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Incorporamento di contenuto in un'applicazione personalizzata <br><br><br> <li> Incorporamento di contenuto nelle applicazioni di MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (esclude l'app per dispositivi mobili)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Condivisione di contenuto con gli utenti di Power BI tramite il [servizio Power BI](https://powerbi.microsoft.com/)  |
|Fatturazione |Ogni ora |Ogni mese |Mensile |
|Impegno  |Nessun impegno |Annuale  |Mensile/Annuale |
|Differenze |Elasticità completa: aumento/riduzione delle prestazioni, sospensione/ripresa delle risorse nel portale di Azure o tramite l'API  |Consente di incorporare contenuto in SharePoint Online e Microsoft Teams (esclude l'app per dispositivi mobili) |Combina l'incorporamento nelle applicazioni e usa il servizio Power BI nella stessa capacità |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quali sono i prerequisiti per creare una capacità PBIE in Azure?

* È necessario accedere alla directory dell'organizzazione. Gli account MSA non sono supportati.
* È necessario avere un tenant di Power BI, ovvero è necessario che almeno un utente nella directory abbia effettuato l'iscrizione a Power BI. 
* È necessario avere una sottoscrizione di Azure nella directory dell'organizzazione.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>In che modo è possibile monitorare il consumo della capacità di Power BI Embedded?

* Utilizzo del [portale di amministrazione di Power BI](../service-admin-portal.md#power-bi-embedded).

* Download dell'[app metrica](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) in Power BI.

* Utilizzo della [registrazione diagnostica di Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>La capacità può ridimensionarsi automaticamente in base all'utilizzo dell'app?

Al momento il ridimensionamento automatico non è disponibile, ma è possibile ridimensionare le API in qualsiasi momento.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Per quale motivo la creazione, il ridimensionamento o la ripresa di una capacità ne comporta l'inserimento in uno stato sospeso?

Il provisioning di una capacità (ridimensionamento, ripresa o creazione) potrebbe non riuscire. Il chiamante della chiamata al provisioning deve controllare l'oggetto ProvisioningState della capacità usando l'API per il recupero dei dettagli: [Capacities - Get Details](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>È possibile creare le capacità di Power BI Embedded solo in un'area specifica?

Con la funzionalità [Multi-Geo (anteprima)](embedded-multi-geo.md), è possibile acquistare una [capacità di Power BI Embedded](azure-pbie-create-capacity.md) in un'area diversa dalla località del tenant principale di Power BI

### <a name="how-can-i-find-what-is-my-pbi-tenant-region"></a>Come si reperisce la propria area del tenant PBI?

È possibile usare il portale PBI per risalire alla propria area del tenant PBI.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > Informazioni su Power BI

![Informazioni su Power BI](media/embedded-faq/about-01.png)
![Area del tenant](media/embedded-faq/tenant-location-01.png)

### <a name="what-is-supported-by-the-cloud-solution-provider-csp-channel"></a>Cosa supporta il canale Cloud Solution Provider (CSP)?

* Con la sottoscrizione di tipo CSP è possibile creare PBIE per il proprio tenant
* L'account partner può accedere al tenant del cliente, acquistare PBIE per il tenant del cliente e specificare l'utente del tenant del cliente come amministratore della capacità Power BI

### <a name="why-do-i-get-an-unsupported-account-message"></a>Perché viene visualizzato il messaggio di account non è supportato?

Power BI richiede l'iscrizione con un account aziendale. L'iscrizione a Power BI usando un account Microsoft non è supportata.

### <a name="can-i-use-apis-to-create--manage-azure-capacities"></a>È possibile usare le API per creare e gestire le capacità di Azure?

Sì, esistono API Azure Resource Manager e cmdlet di PowerShell che è possibile usare per creare e gestire le risorse Power BI Embedded.

* API REST - https://docs.microsoft.com/rest/api/power-bi-embedded/
* Cmdlet di PowerShell - https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Che cos'è il ruolo della capacità dedicata Power PBI Embedded in una soluzione Power PBI Embedded?

Per [alzare di livello della soluzione per la produzione](https://docs.microsoft.com/power-bi/developer/embedding-content#step-3-promote-your-solution-to-production), è necessario che il contenuto di Power BI, vale a dire l'area di lavoro per le app usata nell'applicazione, venga assegnato a una capacità Power BI Embedded (SKU A).

### <a name="what-are-the-azure-regions-pbi-embedded-is-available"></a>Quali sono le aree di Azure in cui Power PBI Embedded è disponibile?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager): vedere Privileged Access Management

Aree disponibili (16 - stesse aree di Power BI)

* STATI 6 - Stati Uniti orientali, Stati Uniti orientali 2, Stati Uniti centro-settentrionali, Stati Uniti centro-meridionali, Stati Uniti occidentali, Stati Uniti occidentali 2
* Europa (2) - Europa settentrionale, Europa occidentale
* Asia Pacifico (2) - Asia sudorientale, Asia orientale
* Brasile (1) - Brasile meridionale
* Giappone (1) - Giappone orientale
* Australia (1) - Australia sudorientale
* India (1) - India occidentale
* Canada (1) - Canada centrale
* Regno Unito (1) - Regno Unito meridionale

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Qual è il modello di autenticazione per Power BI Embedded?

Power BI Embedded continua a usare Azure AD per l'autenticazione dell'utente master (un utente designato con licenza di Power BI Pro), oppure un'[entità servizio](embed-service-principal.md) per l'autenticazione dell'applicazione all'interno di Power BI.  

L'autenticazione e l'autorizzazione degli utenti dell'applicazione vengono implementate dall'ISV, che può implementarne l'autenticazione per le relative applicazioni.

Se si dispone già di un tenant di Azure AD, è possibile usare la directory esistente oppure si può creare un nuovo tenant di Azure AD per la sicurezza del contenuto dell'applicazione incorporato.

Per ottenere un token AAD, è possibile usare una delle [librerie di autenticazione di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Sono disponibili librerie client per più piattaforme.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>L'applicazione già utilizza AAD per l'autenticazione utente. Come si usa questa identità per l'autenticazione a Power BI in uno scenario "i dati sono di proprietà dell'utente"?

Si tratta di un flusso standard OAuth "per conto di" (https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#web-application-to-web-api)) L'applicazione deve essere configurata per richiedere le autorizzazioni al servizio Power BI con gli ambiti necessari. Dopo che si è ottenuto un token utente per l'app, è sufficiente effettuare una chiamata AcquireTokenAsync all'API ADAL tramite il token di accesso utente e specificare l'URL della risorsa Power BI come ID della risorsa. Segue un frammento di codice che illustra come può essere eseguita questa operazione:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual è la differenza tra Power BI Embedded e altri servizi di Azure?

L'ISV/sviluppatore deve avere un account Power BI per poter acquistare Power BI Embedded in Azure. L'area di distribuzione di Power BI Embedded determina l'account Power BI. Gestire la risorsa Power BI Embedded per:

* Aumentare e ridurre le prestazioni
* Aggiungere amministratori della capacità
* Sospendere e riprendere il servizio

Usare PowerBI.com per assegnare o annullare l'assegnazione di aree di lavoro alla capacità di Power BI Embedded.

### <a name="what-deploy-regions-are-supported"></a>Quali sono le aree di distribuzione supportate?

Australia sud-orientale, Brasile meridionale, Canada centrale, Stati Uniti orientali 2, India occidentale, Giappone orientale, Stati Uniti centro-settentrionali, Europa settentrionale, Stati Uniti centro-meridionali, Asia sud-orientale, Regno Unito meridionale, Europa occidentale, Stati Uniti occidentali e Stati Uniti occidentali 2.

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>Quali tipi di dati del pacchetto di contenuto è possibile incorporare?

I **dashboard** e i **riquadri** compilati dai set di dati del pacchetto di contenuto *non possono* essere incorporati, mentre i **report** compilati da un set di dati del pacchetto di contenuto *possono* essere incorporati.

### <a name="what-is-the-difference-between-using-rls-vs-javascript-filters"></a>Qual è la differenza tra l'uso della sicurezza a livello di riga e dei filtri JavaScript?

La scelta di usare la sicurezza a livello di riga o i filtri JavaScript genera spesso confusione, perché un metodo riguarda come controllare quello che può vedere un utente specifico e l'altro come ottimizzare la visualizzazione dell'utente.

Per la sicurezza a livello di riga, lo sviluppatore ISV controlla il filtraggio dei dati come parte della creazione del modello e della generazione dei token di incorporamento. L'utente finale vede solo ciò che l'ISV gli consente di vedere. In questo caso, l'utente può scegliere di vedere meno di ciò che consente il filtro, ma non potrà ignorare la configurazione della sicurezza a livello di riga e visualizzare più informazioni di quanto consentito.

Per i filtri sul lato client (JavaScript), l'ISV può decidere cosa vede l'utente finale nella visualizzazione iniziale, ma non può controllare le modifiche che l'utente finale potrebbe applicare alla visualizzazione stessa. Anche se il filtro dei dati può essere applicato nel back-end, viene attivato da codice client JavaScript e pertanto può essere modificato da un utente finale e non può essere considerato sicuro.

Per altri dettagli, vedere [Sicurezza a livello di riga e filtri JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Come si gestiscono le autorizzazioni per le entità servizio con Power BI?

Dopo aver abilitato l'[entità servizio](embed-service-principal.md) da usare con Power BI, le autorizzazioni AD dell'applicazione non hanno più effetto. Le autorizzazioni dell'applicazione vengono quindi gestite dal portale di amministrazione di Power BI.

Le entità servizio ereditano le autorizzazioni relative a tutte le impostazioni del tenant di Power BI dal relativo gruppo di sicurezza. Per limitare le autorizzazioni, creare un gruppo di sicurezza dedicato per le entità servizio e aggiungerlo all'elenco "Eccetto gruppi di sicurezza specifici" relativo alle impostazioni pertinenti abilitate di Power BI.

Questa situazione è importante quando l'entità servizio viene aggiunta come **amministratore** alla nuova area di lavoro. È possibile gestire questa attività tramite le [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) o il servizio Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Quando si usa un ID applicazione o un ID oggetto dell'entità servizio?

L'**[ID applicazione](embed-sample-for-customers.md#application-id)**  viene usato per creare il token di accesso quando si passa l'ID applicazione per l'autenticazione.

Per fare riferimento a un'entità servizio per le operazioni o apportare modifiche, usare l'**[ID oggetto dell'entità servizio](embed-service-principal.md#how-to-get-the-service-principal-object-id)**, applicando ad esempio un'entità servizio come amministratore a un'area di lavoro.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>È possibile gestire un gateway dati locale con un'entità servizio?

Non è possibile gestire un gateway dati locale (gateway dati) usando un'[entità servizio](embed-service-principal.md), così come è invece possibile con un account master.

Con un account master, è possibile installare un gateway dati, aggiungere utenti al gateway, connettersi a origini dati ed eseguire altre attività amministrative.

Con un'entità servizio, è possibile configurare la [sicurezza a livello di riga](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) usando un'origine dati con connessione dinamica locale SQL Server Analysis Services (SSAS). In questo modo è possibile gestire gli utenti e il relativo accesso ai dati in SSAS durante il processo di integrazione con **Power BI Embedded** usando un'entità servizio.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>È possibile accedere al servizio Power BI con un'entità servizio?

No, non è possibile accedere a Power BI usando un'entità servizio.

Non è possibile usare il contenuto come utente in applicazioni esterne (incorporamento di SaaS), solo quando si genera un token di incorporamento.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Quali sono le procedure consigliate per migliorare le prestazioni?

[Prestazioni di Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Gestione delle licenze

### <a name="how-do-i-purchase-power-bi-embedded"></a>Come si acquista Power BI Embedded?

Power BI Embedded è disponibile tramite Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>Che cosa accade se ho già acquistato Power BI Premium e ora desidero usufruire di alcuni dei vantaggi offerti da Power BI Embedded in Azure?

I clienti continuano a pagare gli eventuali acquisti di Power BI Premium esistenti fino al termine del contratto e a quel punto potranno scegliere se sostituire le licenze di Power BI Premium in base alle esigenze.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>È comunque necessario acquistare Power BI Premium per avere accesso a Power BI Embedded?

No. Power BI Embedded include la capacità basata su Azure necessaria per distribuire la soluzione ai clienti.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Qual è l'impegno di acquisto per Power BI Embedded?

I clienti possono cambiare l'utilizzo su base oraria. Non sono previsti impegni mensili o annuali per il servizio Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>In che modo verrà visualizzato l'utilizzo di Power BI Embedded nella fattura?

Power BI Embedded viene fatturato secondo una tariffa oraria prevedibile in base al tipo di nodi distribuiti. Mentre la risorsa è attiva, il costo corrispondente continua a essere addebitato, anche se la risorsa non viene usata. Per interrompere l'addebito, è necessario sospendere la risorsa attivamente.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Chi necessita di una licenza di Power BI Pro per Power BI Embedded e perché?

Gli sviluppatori devono avere una licenza di Power BI Pro o un'[entità servizio](embed-service-principal.md) per poter usare le API REST. Gli analisti devono avere una licenza di Power BI Pro o devono usare un'entità servizio per poter aggiungere report a un'area di lavoro di Power BI. Gli amministratori del tenant devono avere una licenza di Power BI Pro per poter gestire il tenant e la capacità di Power BI.

Power BI Embedded consente l'uso del portale di Power BI per gestire e convalidare il contenuto incorporato. La licenza di Power BI Pro è quindi necessaria per autenticare l'app in PowerBI.com e accedere ai report nei repository corretti.

Tuttavia, per la [creazione/modifica dei report incorporati](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) all'interno dell'applicazione, l'utente finale non deve avere una licenza Pro perché l'utente non deve essere un utente di Power BI.

### <a name="can-i-get-started-for-free"></a>È possibile iniziare a usare il prodotto gratuitamente?

Sì. È possibile usare i [crediti Azure](https://azure.microsoft.com/free/) per Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>È possibile accedere a un'esperienza di valutazione per Power BI Embedded in Azure?

Dato che Power BI Embedded fa parte di Azure, è possibile usare il servizio con il [credito di $ 200 ricevuto al momento dell'iscrizione ad Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-sovereign-clouds-us-government-germany-china"></a>Power BI Embedded è disponibile per i cloud sovrani (US Government, Germania, Cina)?

Power BI Embedded è disponibile per alcuni [cloud sovrani](embed-sample-for-customers-sovereign-clouds.md). **NON** è ancora disponibile per il cloud Cina.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded è disponibile per le organizzazioni no profit e gli istituti didattici?

Le organizzazioni no profit e gli istituti didattici possono acquistare Azure. Non sono previsti prezzi speciali per questi tipi di clienti in Azure.

## <a name="power-bi-workspace-collection"></a>Raccolta di aree di lavoro di Power BI

### <a name="what-is-power-bi-workspace-collection"></a>Che cos'è la raccolta di aree di lavoro di Power BI?

La **raccolta di aree di lavoro di Power BI** (**Power BI Embedded** versione 1) è una soluzione basata sulla risorsa di Azure **Raccolta di aree di lavoro di Power BI**. Questa soluzione consente di creare applicazioni **Power BI Embedded** per i clienti usando il contenuto di Power BI nella soluzione **Raccolta di aree di lavoro di Power BI**, API dedicate e chiavi della raccolta di aree di lavoro per autenticare l'applicazione per Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>È possibile eseguire la migrazione dalla raccolta di aree di lavoro di Power BI a Power BI Embedded?

1. È possibile usare lo strumento di migrazione per clonare il contenuto della **raccolta di aree di lavoro di Power BI** in Power BI - https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Iniziare con il modello di verifica (PoC) dell'applicazione **Power BI Embedded** che usa il contenuto di Power BI.

3. Quando si è pronti per la produzione, acquistare una capacità dedicata di **Power BI Embedded** e assegnare il contenuto di Power BI (area di lavoro) a tale capacità.

    > [!Note]
    > È possibile continuare a usare la **raccolta di aree di lavoro di Power BI** durante la compilazione in parallelo con una soluzione **Power BI Embedded**. A questo punto, è possibile spostare il cliente alla nuova soluzione **Power BI Embedded** e ritirare la soluzione **Raccolta di aree di lavoro di Power BI**.

Per altre informazioni, fare riferimento a [Come eseguire la migrazione del contenuto della raccolta di aree di lavoro di Power BI in Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-path-to-be-deprecated"></a>La raccolta di aree di lavoro di Power BI è in procinto di essere deprecata?

Sì, ma i clienti che stanno già usando la soluzione **Raccolta di aree di lavoro di Power BI** possono continuare a usarla fino a quando non sarà deprecata. I clienti possono anche creare nuove raccolte di aree di lavoro e altre applicazioni **Power BI Embedded** che continuano a usare la soluzione **Raccolta di aree di lavoro di Power BI**.

In questo modo però le nuove funzionalità non vengono aggiunte a eventuali soluzioni **Raccolta di aree di lavoro di Power BI** e i clienti sono invitati a pianificare la migrazione alla nuova soluzione **Power BI Embedded**.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Quando viene sospeso il supporto per la raccolta di aree di lavoro di Power BI?

I clienti che stanno già usando la soluzione **Raccolta di aree di lavoro di Power BI** possono continuare a usarla fino alla fine del mese di giugno 2018 o fino al termine del contratto di supporto.

### <a name="in-what-regions-can-pbi-workspace-collection-be-created"></a>In quali regioni può essere creata la raccolta di aree di lavoro di Power BI?

Le regioni disponibili sono Australia sud-orientale, Brasile meridionale, Canada centrale, Stati Uniti orientali 2, Giappone orientale, Stati Uniti centro-settentrionali, Europa settentrionale, Stati Uniti centro-meridionali, Asia sud-orientale, Regno Unito meridionale, Europa occidentale, India occidentale e Stati Uniti occidentali.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Perché occorre eseguire la migrazione dalla raccolta di aree di lavoro di Power BI a Power BI Embedded?

Nella soluzione **Power BI Embedded** sono state introdotte nuove caratteristiche e funzionalità che non sono disponibili in **Raccolta di aree di lavoro di Power BI**.

Ecco alcune delle funzionalità:

* Sono supportate tutte le origini dati di Power BI, a differenza delle due origini dati supportate in **Raccolta di aree di lavoro di Power BI**. 
* Nuove funzionalità come domande e risposte, aggiornamenti, segnalibri, incorporamento di dashboard e riquadri e menu personalizzati sono supportate solo nella soluzione **Power BI Embedded**.
* Modello di fatturazione della capacità.

## <a name="embedding-setup-tool"></a>Strumento di installazione dell'incorporamento

### <a name="what-is-the-embedding-setup-tool"></a>Che cos'è lo strumento di installazione dell'incorporamento?

Lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup) consente di scaricare un'applicazione di esempio per iniziare rapidamente a usare la funzionalità di incorporamento con Power BI.

### <a name="which-solution-should-i-choose"></a>Quale soluzione è consigliabile scegliere?

* L'[incorporamento per i clienti](embedding.md#embedding-for-your-customers) offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Eseguire la soluzione [Incorporare per i clienti](https://aka.ms/embedsetup/AppOwnsData).
* L'[incorporamento per l'organizzazione](embedding.md#embedding-for-your-organization) consente di estendere il servizio Power BI. Eseguire la soluzione [Incorporare per l'organizzazione](https://aka.ms/embedsetup/UserOwnsData).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Dopo aver scaricato l'app di esempio, quale soluzione si deve scegliere?

Se si usa l'esperienza **Incorporare per i clienti**, salvare e decomprimere il file *PowerBI-Developer-Samples.zip*. Aprire quindi la cartella *PowerBI-Developer-Samples-master\App Owns Data* ed eseguire il file *PowerBIEmbedded_AppOwnsData.sln*.

Se si usa l'esperienza **Incorporare per l'organizzazione**, salvare e decomprimere il file *PowerBI-Developer-Samples.zip*. Aprire quindi la cartella *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* ed eseguire il file *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>Come si può modificare l'applicazione registrata?

Le informazioni su come modificare le applicazioni registrate con AAD sono disponibili [qui](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Come è possibile modificare il proprio profilo utente o i propri dati in Power BI?

Le informazioni su come modificare i propri dati in Power BI sono disponibili [qui](https://docs.microsoft.com/power-bi/service-basic-concepts).

Per altre informazioni, vedere [Risoluzione dei problemi dell'applicazione incorporata](embedded-troubleshoot.md).

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)