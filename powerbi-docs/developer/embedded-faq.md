---
title: Domande frequenti su Power BI Embedded
description: Esplorare un elenco di domande frequenti e risposte relative a Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222184"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Domande frequenti su Power BI Embedded

* Per altre domande, [provare a rivolgersi alla community di Power BI](http://community.powerbi.com/).
* Ci sono ancora problemi? Visitare la [pagina del supporto tecnico di Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Generali

### <a name="what-is-power-bi-embedded"></a>Che cos'è Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) consente agli sviluppatori di applicazioni di incorporare report accattivanti e completamente interattivi nelle proprie applicazioni senza dover compilare le proprie visualizzazioni dei dati e i controlli da zero.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>A chi è destinato Power BI Embedded?

Gli sviluppatori e aziende di software, fornitori di software noto anche come indipendenti (ISV), codifica di applicazioni.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Qual è la differenza tra Power BI Embedded e il servizio Power BI?

Power BI è una soluzione di analisi distribuita come servizio che offre alle organizzazioni una visualizzazione centralizzata dei dati aziendali più strategici.

Microsoft ha sviluppato Power BI Embedded per gli ISV che desiderano incorporare oggetti visivi nelle proprie applicazioni per consentire ai clienti di prendere decisioni di analisi. Parti di ricambio ISV di dover compilare soluzione delle proprie analitica stessi. [Embedded analitica](embedding.md) consente agli utenti aziendali accedere ai dati aziendali ed eseguire query su di essa per generare informazioni dettagliate all'interno dell'applicazione.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Qual è la differenza tra Power BI Premium e Power BI Embedded?

Power BI Premium è una capacità destinata alle aziende che desiderano una soluzione BI completa che fornisce una singola visualizzazione della relativa organizzazione, partner, clienti e fornitori. Power BI Premium semplifica il processo decisionale dell'organizzazione. Power BI Premium è un prodotto SaaS che consente agli utenti di utilizzare il contenuto tramite App per dispositivi mobili, App sviluppate internamente o nel portale di Power BI.

Power BI Embedded è per gli ISV che vogliono incorporare oggetti visivi nelle proprie applicazioni. Power BI Embedded agevola i processi decisionali dei clienti e poiché è progettato per gli sviluppatori di applicazioni, i clienti di queste applicazioni possono fruire del contenuto archiviato nella capacità di Power BI Embedded, che si trovino all'interno o all'esterno dell'organizzazione. Non è possibile condividere Power BI Embedded il contenuto della capacità tramite un solo clic pubblica sul Web o un solo clic pubblicare in SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Quali sono le indicazioni di Microsoft per scegliere tra Power BI Premium e Power BI Embedded?

È consigliabile che le aziende dovrebbero acquistare Power BI Premium, un livello aziendale, una soluzione di Business Intelligence cloud self-service. È consigliabile che gli ISV dovrebbero acquistare Power BI Embedded per i relativi componenti analitica incorporata basata sul cloud. Tuttavia, un cliente non presenta alcuna restrizione sui quali prodotti da acquistare.

Potrebbero esserci casi in cui vuole che un'applicazione ISV (in genere grandi dimensioni), oltre all'incorporamento delle app, usare uno SKU P per ottenere i vantaggi aggiuntivi del servizio Power BI preconfezionato all'interno dell'organizzazione. Alcune aziende possono decidere di usare SKU A in Azure, se sono interessate solo a creare applicazioni line-of-business incorporandovi le analisi e non necessitano del servizio Power BI preconfezionato.

### <a name="how-many-embed-tokens-can-i-create"></a>Quanti token di incorporamento è possibile creare?

Incorporare i token con licenza PRO sono destinati a test di sviluppo, in modo che l'account master Power BI oppure [entità servizio](embed-service-principal.md) possono generare solo un numero limitato di token. [Acquistare una capacità](#technical) per l'incorporamento in un ambiente di produzione. Non è previsto alcun limite per il numero è possibile generare quando si acquista una capacità di token di incorporamento. Vedere [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) (Funzionalità disponibili) per controllare il valore di utilizzo che indica l'attuale utilizzo incorporato espresso come percentuale.

## <a name="technical"></a>Informazioni tecniche

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Qual è la differenza tra gli SKU A in Azure e gli SKU EM in Office 365?

PowerBI.com è un'azienda Software come soluzione di servizio (SaaS) con numerose funzionalità, ad esempio collaborazione sociale, sottoscrizione messaggio di posta elettronica e altre funzionalità. PowerBI.com consente agli ISV di gestire la propria soluzione analitica incorporata del contenuto e le impostazioni a livello del tenant.

Power BI Embedded è che una piattaforma come servizio (PaaS), set di API gli sviluppatori possa usare per creare una soluzione analitica incorporata.

Ecco un elenco parziale delle differenze nelle funzionalità.

| Feature | Power BI Embedded | Capacità Power BI Premium | Capacità Power BI Premium |
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
|Purchase  |Portale di Azure |Office |Office |
|Casi d'uso | Incorporamento di contenuto in un'applicazione personalizzata | <li> Incorporamento di contenuto in un'applicazione personalizzata <br><br><br> <li> Incorporamento di contenuto nelle applicazioni di MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (esclude l'app per dispositivi mobili)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Incorporamento di contenuto in un'applicazione personalizzata <br><br><br> <li> Incorporamento di contenuto nelle applicazioni di MS Office: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (esclude l'app per dispositivi mobili)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Condivisione di contenuto con gli utenti di Power BI tramite il [servizio Power BI](https://powerbi.microsoft.com/)  |
|Fatturazione |Ogni ora |Ogni mese |Mensile |
|Impegno  |Nessun impegno |Annuale  |Mensile/Annuale |
|Differenze |Elasticità completa: aumento/riduzione delle prestazioni, sospensione/ripresa delle risorse nel portale di Azure o tramite l'API  |È possibile usare per incorporare il contenuto in SharePoint Online e Microsoft Teams (esclude l'app per dispositivi mobili) |Combina l'incorporamento nelle applicazioni e usa il servizio Power BI nella stessa capacità |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quali sono i prerequisiti per creare una capacità PBIE in Azure?

* Accedere alla directory dell'organizzazione (non sono supportati gli account Microsoft).
* È necessario disporre di un tenant di Power BI, vale a dire, almeno un utente nella directory ha effettuato l'iscrizione per Power BI. 
* È necessario avere una sottoscrizione di Azure nella directory dell'organizzazione.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>In che modo è possibile monitorare il consumo della capacità di Power BI Embedded?

* Utilizzo del [portale di amministrazione di Power BI](../service-admin-portal.md#power-bi-embedded).

* Download dell'[app metrica](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) in Power BI.

* Utilizzo della [registrazione diagnostica di Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>La capacità è possibile scalare automaticamente per regolare per l'utilizzo di mia app?

Sebbene non sia non momento il ridimensionamento automatico, tutte le API sono disponibili per la scalabilità in qualsiasi momento.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Per quale motivo la creazione, il ridimensionamento o la ripresa di una capacità ne comporta l'inserimento in uno stato sospeso?

Il provisioning della capacità (scalabilità o ripresa/creare) potrebbe non riuscire. È possibile usare l'API Ottieni dettagli controllare ProvisioningState della capacità: [Capacities - Get Details](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>È possibile creare le capacità di Power BI Embedded solo in un'area specifica?

Con la funzionalità [Multi-Geo (anteprima)](embedded-multi-geo.md), è possibile acquistare una [capacità di Power BI Embedded](azure-pbie-create-capacity.md) in un'area diversa dalla località del tenant principale di Power BI

### <a name="how-can-i-find-my-pbi-tenant-region"></a>Come è possibile trovare l'area del tenant di PBI?

È possibile usare il portale di PBI a individuare l'area del Tenant di PBI.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > Informazioni su Power BI

![Informazioni su Power BI](media/embedded-faq/about-01.png)
![Area del tenant](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Ciò che supporta il canale di Cloud Solution Provider (CSP)?

* Con la sottoscrizione di tipo CSP è possibile creare PBIE per il proprio tenant
* L'account partner può accedere al tenant del cliente, acquistare PBIE per il tenant del cliente e specificare l'utente del tenant del cliente come amministratore della capacità Power BI

### <a name="why-do-i-get-an-unsupported-account-message"></a>Perché viene visualizzato il messaggio di account non è supportato?

Power BI richiede l'iscrizione con un account aziendale. Non è supportata per l'iscrizione per Power BI usando un account Microsoft.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>È possibile usare le API per creare e gestire le capacità di Azure?

Sì, sono presenti i cmdlet di Powershell e API REST di Azure Resource Manager è possibile usare per creare e gestire le risorse PBIE.

* [API REST](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [Cmdlet di PowerShell](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Che cos'è il ruolo della capacità dedicata Power PBI Embedded in una soluzione Power PBI Embedded?

Per [Promuovi la tua soluzione nell'ambiente di produzione](embed-sample-for-customers.md#move-to-production), è necessario assegnare l'applicazione usa il contenuto di Power BI (area di lavoro di app) a una capacità Power BI Embedded (una SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>In quali aree di Azure è incorporato PBI disponibile?

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

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Che cos'è modello di autenticazione del Power BI Embedded?

Power BI Embedded continuerà a usare Azure AD per l'autenticazione utente master (un utente Power BI Pro con licenza designato) o con [entità servizio](embed-service-principal.md) per autenticare l'applicazione all'interno di Power BI.  

 Un ISV può implementare i propri autenticazione e autorizzazione per le proprie applicazioni.

Se si dispone già di un tenant di Azure AD, è possibile usare la directory esistente. È anche possibile creare un nuovo tenant di Azure AD per la protezione del contenuto dell'applicazione incorporate.

Per ottenere un token AAD, è possibile usare una delle [librerie di autenticazione di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Sono disponibili librerie client per più piattaforme.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>L'applicazione già utilizza AAD per l'autenticazione utente. Come si usa questa identità per l'autenticazione a Power BI in uno scenario "i dati sono di proprietà dell'utente"?

È standard OAuth flusso on-behalf-of (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). È necessario configurare l'applicazione in modo da richiedere le autorizzazioni del servizio (con gli ambiti necessari) di Power BI. Dopo aver ottenuto un token utente per l'app, è sufficiente chiamare ADAL API AcquireTokenAsync usando l'accesso dell'utente del token e specificare l'URL della risorsa Power BI come l'ID risorsa:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Quale oggetto che ID è l'ID di oggetto entità servizio?

Il *ID di oggetto* dalla schermata principale di un'app registrata è l'ID oggetto per l'app.

L'oggetto trovato nell'ID di *applicazione gestita nella directory locale > proprietà* sezione è l'ID di oggetto entità servizio è necessario usare. Questo ID di oggetto è per fare riferimento a un'entità servizio per le operazioni o apportare modifiche all'oggetto entità servizio di ID. Ad esempio applicando un'entità servizio l'amministratore a un'area di lavoro.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Qual è la differenza tra Power BI Embedded e altri servizi di Azure?

È necessario un account di Power BI prima di acquistare Power BI Embedded in Azure. L'area di Power BI Embedded distribuita determina l'account Power BI. Gestire la risorsa Power BI Embedded per:

* Aumentare e ridurre le prestazioni
* Aggiungere amministratori della capacità
* Sospensione/ripresa del servizio

Usare PowerBI.com per assegnare o annullare l'assegnazione di aree di lavoro alla capacità di Power BI Embedded.

### <a name="what-are-the-supported-deploy-regions"></a>Quali sono supportate le aree di distribuzione?

Australia sud-orientale, Brasile meridionale, Canada centrale, Stati Uniti orientali 2, India occidentale, Giappone orientale, Stati Uniti centro-settentrionali, Europa settentrionale, Stati Uniti centro-meridionali, Asia sud-orientale, Regno Unito meridionale, Europa occidentale, Stati Uniti occidentali e Stati Uniti occidentali 2.

### <a name="what-content-pack-data-types-can-you-embed"></a>Quali tipi di dati del pacchetto di contenuto è possibile incorporare?

Si *Impossibile* incorporare **dashboard** e **riquadri** compilati dal set di dati di pacchetto di contenuto. Tuttavia, si *può* incorporare **report** compilata da un set di dati del pacchetto di contenuto.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Qual è la differenza tra l'uso di Visual Studio di sicurezza a livello di riga (RLS). e dei filtri JavaScript?

È spesso confusione su quando usare a livello di riga e filtri di JavaScript, perché è un metodo su come controllare ciò che è possibile visualizzare un utente specifico e l'altro è come ottimizzare la visualizzazione dell'utente.

Per la sicurezza a livello di riga, lo sviluppatore ISV controlla il filtraggio dei dati come parte della creazione del modello e della generazione dei token di incorporamento. L'utente finale vede solo ciò che l'ISV gli consente di vedere. In questo caso, l'utente può scegliere di vedere meno di ciò che consente il filtro, ma non potrà ignorare la configurazione della sicurezza a livello di riga e visualizzare più informazioni di quanto consentito.

Per client-side filtro (JavaScript), l'ISV può decidere quali l'utente finale vede la visualizzazione iniziale, ma non è possibile controllare le modifiche apportate che all'utente finale potrebbe applicare alla visualizzazione stessa. Poiché il codice Javascript client utente può attivare il filtro al back-end di dati, non può essere considerata sicura.

Per altri dettagli, vedere [Sicurezza a livello di riga e filtri JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Come si gestiscono le autorizzazioni per le entità servizio con Power BI?

Dopo aver abilitato [entità servizio](embed-service-principal.md) per l'uso con Power BI, le autorizzazioni dell'applicazione AD non hanno più effetto. Le autorizzazioni dell'applicazione vengono quindi gestite dal portale di amministrazione di Power BI.

Le entità servizio ereditano le autorizzazioni per tutte le impostazioni del tenant di Power BI dal relativo gruppo di sicurezza. Per limitare le autorizzazioni, creare un gruppo di sicurezza dedicato per le entità servizio e aggiungerlo al **eccetto gruppi di sicurezza specifico** elenco per le impostazioni di Power BI rilevante, abilitate.

Questa situazione è importante quando l'entità servizio viene aggiunta come **amministratore** alla nuova area di lavoro. È possibile gestire questa attività tramite le [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) o il servizio Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Quando si usa un ID applicazione o un ID oggetto dell'entità servizio?

L' **[ID applicazione](embed-sample-for-customers.md#application-id)**  viene usato per creare il token di accesso quando si passa l'ID applicazione per l'autenticazione.

Per fare riferimento a un'entità servizio per le operazioni o apportare modifiche, usare l' **[ID oggetto dell'entità servizio](embed-service-principal.md#how-to-get-the-service-principal-object-id)** , applicando ad esempio un'entità servizio come amministratore a un'area di lavoro.

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

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Cosa accade se ho già acquistato Power BI Premium e ora desidero alcuni Power BI Embedded in vantaggi della piattaforma Azure?

I clienti continuano a pagamento per eventuali acquisti di Power BI Premium esistenti fino alla fine del proprio attuale termine di contratto e quindi, a questo punto, potrebbero passare degli acquisti di Power BI Premium in base alle esigenze.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>È comunque necessario acquistare Power BI Premium per avere accesso a Power BI Embedded?

No. Power BI Embedded include la capacità basata su Azure necessaria per distribuire la soluzione ai clienti.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Qual è l'impegno di acquisto per Power BI Embedded?

I clienti possono cambiare l'utilizzo su base oraria. Non è previsto alcun impegno mensile o annua per il servizio Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>In che modo verrà visualizzato l'utilizzo di Power BI Embedded nella fattura?

Power BI Embedded viene fatturato secondo una tariffa oraria prevedibile in base al tipo di nodi distribuiti. Verrà addebitato fino a quando la risorsa è attiva, anche se non viene usata. È necessario sospendere la risorsa di interrompere la fatturazione.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Chi necessita di una licenza di Power BI Pro per Power BI Embedded e perché?

È necessaria una licenza Power BI Pro o [entità servizio](embed-service-principal.md) usare le API REST. Per aggiungere report a un'area di lavoro di Power BI, un analista che richiede una licenza di Power BI Pro o servizio dell'entità. Per gestire capacità e il tenant di Power BI, un amministratore è necessario disporre di una licenza Power BI Pro.

Perché Power BI Embedded consente l'uso del portale di Power BI per la gestione e convalidare il contenuto incorporato, è necessaria la licenza Power BI Pro per autenticare l'app in PowerBI.com per ottenere l'accesso ai report nei repository corretti.

Tuttavia, per la [creazione/modifica dei report incorporati](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) all'interno dell'applicazione, l'utente finale non deve avere una licenza Pro perché l'utente non deve essere un utente di Power BI.

### <a name="can-i-get-started-for-free"></a>È possibile iniziare a usare il prodotto gratuitamente?

Sì. È possibile usare i [crediti Azure](https://azure.microsoft.com/free/) per Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>È possibile accedere a un'esperienza di valutazione per Power BI Embedded in Azure?

Poiché Power BI Embedded è una parte di Azure, è possibile usare il servizio con il [$200 di credito ricevuto durante l'iscrizione ad Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Power BI Embedded è disponibile per i cloud nazionali (US Government, Germania, Cina)?

Power BI Embedded è disponibile anche per [cloud nazionali](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded è disponibile per le organizzazioni no profit e gli istituti didattici?

Non è nessuna speciali prezzi di Azure di No profii e gli istituti didattici.

## <a name="power-bi-workspace-collection"></a>Raccolta di aree di lavoro di Power BI

### <a name="what-is-power-bi-workspace-collection"></a>Che cos'è la raccolta di aree di lavoro di Power BI?

**Power BI Embedded** (**Power BI Embedded** versione 1) è una soluzione basata sul **raccolta di aree di lavoro di Power BI** risorse di Azure. Questa soluzione consente di creare applicazioni **Power BI Embedded** per i clienti usando il contenuto di Power BI nella soluzione **Raccolta di aree di lavoro di Power BI**, API dedicate e chiavi della raccolta di aree di lavoro per autenticare l'applicazione per Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>È possibile eseguire la migrazione dalla raccolta di aree di lavoro di Power BI a Power BI Embedded?

1. È possibile usare lo strumento di migrazione per clonare il contenuto della **raccolta di aree di lavoro di Power BI** in Power BI - https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Iniziare con il modello di verifica (PoC) dell'applicazione **Power BI Embedded** che usa il contenuto di Power BI.

3. Quando si è pronti per la produzione, acquistare una capacità dedicata di **Power BI Embedded** e assegnare il contenuto di Power BI (area di lavoro) a tale capacità.

    > [!Note]
    > È possibile continuare a usare la **raccolta di aree di lavoro di Power BI** durante la compilazione in parallelo con una soluzione **Power BI Embedded**. A questo punto, è possibile spostare il cliente alla nuova soluzione **Power BI Embedded** e ritirare la soluzione **Raccolta di aree di lavoro di Power BI**.

Per altre informazioni, fare riferimento a [Come eseguire la migrazione del contenuto della raccolta di aree di lavoro di Power BI in Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Raccolta di aree di lavoro di Power BI si trova in un percorso deprecation?

Sì, ma i clienti che usano già il **raccolta di aree di lavoro di Power BI** soluzione possibile continuare a usarlo fino a elementi deprecati. I clienti possono anche creare nuove raccolte di aree di lavoro e altre applicazioni **Power BI Embedded** che continuano a usare la soluzione **Raccolta di aree di lavoro di Power BI**.

Tuttavia, significa anche che non vengono aggiunte nuove funzionalità a qualsiasi **raccolta di aree di lavoro di Power BI** soluzioni. E invita i clienti a pianificare la migrazione al nuovo **Power BI Embedded** soluzione.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Quando viene sospeso il supporto per la raccolta di aree di lavoro di Power BI?

I clienti che stanno già usando la soluzione **Raccolta di aree di lavoro di Power BI** possono continuare a usarla fino alla fine del mese di giugno 2018 o fino al termine del contratto di supporto.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>In quali aree è possibile creare una raccolta di aree di lavoro PBI?

Le regioni disponibili sono Australia sud-orientale, Brasile meridionale, Canada centrale, Stati Uniti orientali 2, Giappone orientale, Stati Uniti centro-settentrionali, Europa settentrionale, Stati Uniti centro-meridionali, Asia sud-orientale, Regno Unito meridionale, Europa occidentale, India occidentale e Stati Uniti occidentali.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Perché occorre eseguire la migrazione dalla raccolta di aree di lavoro di Power BI a Power BI Embedded?

Sono disponibili alcune nuove **Power BI Embedded** le funzionalità che è possibile eseguire con soluzione **raccolta di aree di lavoro di Power BI**.

Ecco alcune delle funzionalità:
* Sono supportate tutte le origini dati PBI. Solo due **raccolta di aree di lavoro di Power BI** sono supportate le origini dati. 
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

Per informazioni su come modificare le applicazioni registrate con Azure AD, vedere [Avvio rapido: Aggiornare un'applicazione in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Come è possibile modificare il proprio profilo utente o i propri dati in Power BI?

Le informazioni su come modificare i propri dati in Power BI sono disponibili [qui](https://docs.microsoft.com/power-bi/service-basic-concepts).

Per altre informazioni, vedere [Risoluzione dei problemi dell'applicazione incorporata](embedded-troubleshoot.md).

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
