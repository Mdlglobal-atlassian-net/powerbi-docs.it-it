---
title: Risoluzione dei problemi dell'applicazione incorporata
description: Questo articolo illustra alcuni problemi comuni che possono verificarsi quando si incorpora il contenuto da Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 07/03/2018
ms.author: maghan
ms.openlocfilehash: b3c9599ea3ce01094bb75d9b036fb25b1ca7109a
ms.sourcegitcommit: 627918a704da793a45fed00cc57feced4a760395
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2018
ms.locfileid: "37926560"
---
# <a name="troubleshooting-your-embedded-application"></a>Risoluzione dei problemi dell'applicazione incorporata

Questo articolo illustra alcuni problemi comuni che possono verificarsi quando si incorpora il contenuto da Power BI.

## <a name="tools-for-troubleshooting"></a>Strumenti per la risoluzione dei problemi

### <a name="fiddler-trace"></a>Traccia di Fiddler

[Fiddler](http://www.telerik.com/fiddler) è uno strumento gratuito di Telerik che monitora il traffico HTTP.  È possibile visualizzare il traffico in entrata e in uscita con le API Power BI dal computer client. Potrebbero essere illustrati errori e altre informazioni correlate.

![Traccia di Fiddler](../includes/media/gateway-onprem-tshoot-tools-include/fiddler.png)

### <a name="f12-in-browser-for-front-end-debugging"></a>F12 nel browser per il debug del front-end

F12 avvierà la finestra degli strumenti di sviluppo nel browser. Questo consentirà di osservare il traffico di rete e altre informazioni.

![Debug del browser con F12](media/embedded-troubleshoot/browser-f12.png)

### <a name="extracting-error-details-from-power-bi-response"></a>Estrazione di dettagli dell'errore dalla risposta di Power BI

Questo frammento di codice mostra come estrarre i dettagli dell'errore dall'eccezione HTTP:

```
public static string GetExceptionText(this HttpOperationException exc)
{
    var errorText = string.Format("Request: {0}\r\nStatus: {1} ({2})\r\nResponse: {3}",
    exc.Request.Content, exc.Response.StatusCode, (int)exc.Response.StatusCode, exc.Response.Content);
    if (exc.Response.Headers.ContainsKey("RequestId"))
    {
        var requestId = exc.Response.Headers["RequestId"].FirstOrDefault();
        errorText += string.Format("\r\nRequestId: {0}", requestId);
    }

    return errorText;
}
```
È consigliabile registrare gli ID richiesta e i dettagli dell'errore per la risoluzione dei problemi.
Specificare l'ID richiesta quando si contatta il supporto tecnico Microsoft.

## <a name="app-registration"></a>Registrazione dell'app

**Errore di registrazione dell'app**

Messaggi di errore nel portale di Azure o nella pagina di registrazione dell'app di Power BI che indicano che i privilegi non sono sufficienti. Per registrare un'applicazione, è necessario essere un amministratore nel tenant di Azure AD oppure è necessario che siano state abilitate le registrazioni delle applicazioni per gli utenti non amministratori.

**Il servizio Power BI non è visualizzato nel portale di Azure quando si registra una nuova app**

Almeno un utente deve aver effettuato l'iscrizione a Power BI. Se il **Servizio Power BI** non è visualizzato nell'elenco delle API, nessun utente ha effettuato l'iscrizione a Power BI.

## <a name="rest-api"></a>API REST

**Chiamata API che restituisce un errore con codice 401**

Potrebbe essere necessaria un'acquisizione Fiddler per ulteriori indagini. È possibile che manchi l'ambito di autorizzazioni necessarie per l'applicazione registrata in Azure AD. Verificare che l'ambito necessario sia presente nella registrazione dell'app per Azure AD nel portale di Azure.

**Chiamata API che restituisce un errore con codice 403**

Potrebbe essere necessaria un'acquisizione Fiddler per ulteriori indagini. Le cause possibili per un errore con codice 403 sono più di una.

* L'utente ha superato la quantità di token di incorporamento che può essere generata in una capacità condivisa. È necessario acquistare capacità di Azure per generare token di incorporamento e assegnare l'area di lavoro a tale capacità. Vedere [Creare la capacità di Power BI Embedded nel portale di Azure](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity).
* Il token di autenticazione di Azure AD è scaduto.
* L'utente autenticato non è un membro del gruppo (area di lavoro dell'app).
* L'utente autenticato non è un amministratore del gruppo (area di lavoro dell'app).
* L'intestazione dell'autorizzazione potrebbe non essere corretta. Assicurarsi che non siano presenti errori di ortografia.

Il back-end dell'applicazione potrebbe dover aggiornare il token di autenticazione prima di chiamare GenerateToken.

```
    GET https://wabi-us-north-central-redirect.analysis.windows.net/metadata/cluster HTTP/1.1
    Host: wabi-us-north-central-redirect.analysis.windows.net
    ...
    Authorization: Bearer eyJ0eXAiOi...
    ...
 
    HTTP/1.1 403 Forbidden
    ...
     
    {"error":{"code":"TokenExpired","message":"Access token has expired, resubmit with a new access token"}}
```

## <a name="authentication"></a>Autenticazione

### <a name="authentication-failed-with-aadsts70002-or-aadsts50053"></a>Autenticazione non riuscita con AADSTS70002 o AADSTS50053

**(AADSTS70002: Errore durante la convalida delle credenziali. AADSTS50053: Si è tentato di accedere troppe volte con un ID utente o una password non corretti)**

Se si usa Power BI Embedded con l'autenticazione diretta di Azure AD e si ricevono messaggi in fase di accesso, ad esempio ***eerror:unauthorized_client,error_description:AADSTS70002: Errore durante la convalida delle credenziali. AADSTS50053: Hai tentato di accedere troppe volte con una password o un account non corretto***, significa che l'autenticazione diretta è stato disattivata a partire dal 14 giugno 2018.

Si consiglia pertanto di usare il supporto all'[accesso condizionale di Azure AD](https://cloudblogs.microsoft.com/enterprisemobility/2018/06/07/azure-ad-conditional-access-support-for-blocking-legacy-auth-is-in-public-preview/) per bloccare l'autenticazione legacy o l'[Autenticazione pass-through della directory di Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication).

Esiste comunque un modo per riattivare questa funzionalità usando [criteri HRD](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/configure-authentication-for-federated-users-portal#enable-direct-authentication-for-legacy-applications) di Azure AD impostando come ambito l'organizzazione o un'[entità servizio](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects#service-principal-object).

**_Si consiglia di abilitare questa funzionalità solo in base alle singole app e solo se necessario per risolvere il problema._**

Per creare questo criterio, è necessario essere un **amministratore globale** per la directory in cui si crea e si assegna il criterio. Ecco un esempio di script per la creazione del criterio e la sua assegnazione alla stored procedure per questa applicazione:

1. Installare il [modulo PowerShell dell'anteprima di Azure AD](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).

2. Eseguire i seguenti comandi powershell riga per riga assicurandosi che la variabile $sp non abbia più di 1 applicazione come risultato.

```powershell
Connect-AzureAD
```

```powershell
$sp = Get-AzureADServicePrincipal -SearchString "Name_Of_Application"
```

```powershell
$policy = New-AzureADPolicy -Definition @("{`"HomeRealmDiscoveryPolicy`":{`"AllowCloudPasswordValidation`":true}}") -DisplayName EnableDirectAuth -Type HomeRealmDiscoveryPolicy -IsOrganizationDefault $false
```

```powershell
Add-AzureADServicePrincipalPolicy -Id $sp.ObjectId -RefObjectId $policy.Id 
```

Dopo aver assegnato i criteri, attendere circa 15-20 secondi per la propagazione prima di avviare il test.

**Si verifica un errore del metodo GenerateToken quando viene specificata l'identità effettiva**

Le cause di un errore del metodo GenerateToken quando viene specificata l'identità effettiva possono essere diverse.

* Il set di dati non supporta l'identità effettiva
* Il nome utente non è stato specificato
* Il ruolo non è stato specificato
* L'ID del set di dati non è stato specificato
* L'utente non dispone delle autorizzazioni corrette

Per verificare qual è la causa, seguire questa procedura.

* Eseguire [get dataset](https://docs.microsoft.com/rest/api/power-bi/datasets). La proprietà IsEffectiveIdentityRequired è impostata su true?
* Il nome utente è obbligatorio per qualsiasi identità effettiva.
* Se la proprietà IsEffectiveIdentityRolesRequired è impostata su true, il ruolo è obbligatorio.
* L'ID del set di dati è obbligatorio per qualsiasi identità effettiva.
* Per Analysis Services, l'utente master deve essere un amministratore del gateway.

### <a name="aadsts90094-the-grant-requires-admin-permission"></a>AADSTS90094: The grant requires admin permission (La concessione richiede l'autorizzazione di amministratore)

**_Sintomi:_**</br>
Quando un utente non amministratore tenta di accedere a un'applicazione per la prima volta e di concedere l'autorizzazione, si verifica l'errore seguente:
* Per accedere alle risorse aziendali, ConsentTest necessita di un'autorizzazione che può essere concessa solo da un amministratore. Prima di usarla, è necessario chiedere a un amministratore di concedere l'autorizzazione a questa app.
* AADSTS90094: The grant requires admin permission (La concessione richiede l'autorizzazione di amministratore).

    ![ConsentTest](media/embedded-troubleshoot/consent-test-01.png)

Un utente amministratore può accedere e concedere l'autorizzazione correttamente.

**_Causa principale:_**</br>
Il consenso dell'utente è disabilitato per il tenant.

**_Sono possibili diverse correzioni:_**

*Abilitare il consenso dell'utente per l'intero tenant (tutti gli utenti, tutte le applicazioni)*
1. Nel portale di Azure passare ad "Azure Active Directory" = > "Utenti e gruppi" = > "Impostazioni utente"
2. Abilitare l'impostazione "Gli utenti possono fornire il consenso alle app che accedono ai dati aziendali per loro conto" e salvare le modifiche

    ![Correzione di ConsentTest](media/embedded-troubleshoot/consent-test-02.png)

*Concessione delle autorizzazioni da parte di un amministratore* Un amministratore concede le autorizzazioni per l'applicazione per l'intero tenant o per un utente specifico.

## <a name="data-sources"></a>Origini dati

**L'ISV vuole avere diverse credenziali per la stessa origine dati**

Un'origine dati può avere un solo set di credenziali per un utente master. Se sono necessarie credenziali diverse, creare altri utenti master. Quindi, assegnare le diverse credenziali in ogni contesto degli utenti master e incorporarle usando il token di Azure AD per l'utente corrispondente.

## <a name="content-rendering"></a>Rendering del contenuto

**Il rendering, o utilizzo, del contenuto incorporato non riesce o raggiunge il timeout**

Assicurarsi che il token di incorporamento non sia scaduto. Assicurarsi di controllare la scadenza del token di incorporamento e di aggiornarlo. Per altre informazioni, vedere come [aggiornare il token tramite JavaScript SDK](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Refresh-token-using-JavaScript-SDK-example).

**Il report o il dashboard non viene caricato**

Se l'utente non visualizza il report o il dashboard, assicurarsi che il report o il dashboard venga caricato correttamente in powerbi.com. Se il caricamento non riesce in powebi.com, il report o il dashboard non funzionerà nell'applicazione.

**Le prestazioni del report o del dashboard risultano rallentate**

Aprire il file in Power BI Desktop o in powerbi.com e verificare che le prestazioni siano accettabili per escludere problemi con l'applicazione o con le API di incorporamento.

## <a name="onboarding-experience-tool-for-embedding"></a>Strumento esperienza di onboarding per l'incorporamento

È possibile usare lo [strumento esperienza di onboarding](https://aka.ms/embedsetup) per scaricare rapidamente un'applicazione di esempio, confrontando quindi l'applicazione e l'esempio.

### <a name="prerequisites"></a>Prerequisiti

Prima di usare lo strumento esperienza di onboarding, verificare di avere tutti i prerequisiti appropriati. Sono necessari un account **Power BI Pro** e una sottoscrizione di **Microsoft Azure**.

* Se non si è ancora iscritti a **Power BI Pro**, [iscriversi per ottenere una versione di prova gratuita](https://powerbi.microsoft.com/en-us/pricing/) prima di iniziare.
* Se non si ha una sottoscrizione di Azure, [creare un account gratuito](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) prima di iniziare.
* È necessario disporre del proprio [tenant di Azure Active Directory](create-an-azure-active-directory-tenant.md) configurato.
* È richiesta l'installazione di [Visual Studio](https://www.visualstudio.com/) (versione 2013 o successive).

### <a name="common-issues"></a>Problemi comuni

Ecco alcuni problemi comuni che possono verificarsi durante il test con lo strumento esperienza di onboarding:

#### <a name="using-the-embed-for-your-customers-sample-application"></a>Uso dell'incorporamento per l'applicazione di esempio per i clienti

Se si usa l'esperienza **Incorporare per i clienti**, salvare e decomprimere il file *PowerBI-Developer-Samples.zip*. Aprire quindi la cartella *PowerBI-Developer-Samples-master\App Owns Data* ed eseguire il file *PowerBIEmbedded_AppOwnsData.sln*.

Quando si seleziona **Concedi autorizzazioni** (passaggio Concedi autorizzazioni), viene visualizzato l'errore seguente:

    AADSTS70001: Application with identifier <client ID> was not found in the directory <directory ID>

La soluzione sta per chiudere la finestra popup, attendere qualche secondo e riprovare. Può essere necessario ripetere l'azione più volte. Il problema tra il completamento del processo di registrazione dell'applicazione e il momento in cui l'applicazione è disponibile per le API esterne è causato da un intervallo di tempo.

Quando si esegue l'app di esempio, viene visualizzato il messaggio di errore seguente:

    Password is empty. Please fill password of Power BI username in web.config.

Questo errore si verifica perché l'unico valore che non viene inserito nell'applicazione di esempio è la password dell'utente. Aprire il file Web.config nella soluzione e compilare il campo pbiPassword con la password dell'utente.

#### <a name="using-the-embed-for-your-organization-sample-application"></a>Uso dell'incorporamento per l'applicazione di esempio per l'organizzazione

Se si usa l'esperienza **Incorporare per l'organizzazione**, salvare e decomprimere il file *PowerBI-Developer-Samples.zip*. Aprire quindi la cartella *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* ed eseguire il file *pbi-saas-embed-report.sln*.

Quando si esegue l'app di esempio **Incorporare per l'organizzazione**, viene visualizzato l'errore seguente:

    AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: <client ID>

La causa è che l'URL di reindirizzamento specificato per il server Web dell'applicazione è diverso dall'URL dell'esempio. Se si vuole registrare l'applicazione di esempio, usare `http://localhost:13526/` come URL di reindirizzamento.

Se si vuole modificare l'applicazione registrata, vedere come a modificare l'[applicazione registrata con AAD ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application), in modo che l'applicazione possa consentire l'accesso alle API Web.

Se vuole modificare il profilo utente o i dati di Power BI, vedere come modificare i [dati di Power BI](https://docs.microsoft.com/en-us/power-bi/service-basic-concepts).

Per altre informazioni, vedere [Power BI Embedded FAQ](embedded-faq.md) (Domande frequenti su Power BI Embedded).

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)