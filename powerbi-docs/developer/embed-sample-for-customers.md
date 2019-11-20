---
title: Funzionalità di analisi incorporata per incorporare contenuto di Power BI nell'applicazione per i clienti
description: Informazioni su come integrare o incorporare un report, un dashboard o un riquadro in un'applicazione tramite le API di Power BI per l'analisi incorporata per i clienti. Informazioni su come integrare Power BI nell'applicazione usando software di analisi incorporata, strumenti di analisi incorporata o strumenti di business intelligence incorporata.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 04/02/2019
ms.openlocfilehash: 24a9c0069cb80a20a84823655437a27a4f6c0e9e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877702"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-customers"></a>Esercitazione: Incorporare contenuto di Power BI in un'applicazione per i clienti

Con **Power BI Embedded in Azure** o l'**incorporamento di Power BI in Office** è possibile incorporare report, dashboard e riquadri in un'applicazione usando i dati dell'app. **I dati di proprietà dell'app** consistono nel disporre di un'applicazione che usa Power BI come piattaforma di analisi incorporata. Gli **ISV** e gli **sviluppatori** possono creare contenuti Power BI che visualizzano report, dashboard o riquadri in un'applicazione completamente integrata e interattiva, senza richiedere agli utenti il possesso di una licenza di Power BI. Questa esercitazione illustra come integrare un report in un'applicazione tramite .NET SDK di Power BI e l'API JavaScript di Power BI.

![Incorporare report di Power BI](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

In questa esercitazione viene illustrato come:
> [!div class="checklist"]
> * Registrare un'applicazione in Azure.
> * Incorporare un report di Power BI in un'applicazione.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare, è necessario avere:

* Un [account Power BI Pro](../service-self-service-signup-for-power-bi.md) (un account master con nome utente e password per accedere all'account Power BI Pro,) o un'[entità servizio (token solo app)](embed-service-principal.md).
* È necessario aver configurato un [tenant di Azure Active Directory](create-an-azure-active-directory-tenant.md).

Se non si è ancora iscritti a **Power BI Pro**, [iscriversi per ottenere una versione di prova gratuita](https://powerbi.microsoft.com/pricing/) prima di iniziare.

## <a name="set-up-your-embedded-analytics-development-environment"></a>Configurare l'ambiente di sviluppo di analisi incorporata

Prima di iniziare a incorporare report, dashboard o riquadri in un'applicazione, è necessario assicurarsi che l'ambiente consenta l'incorporamento con Power BI.

È possibile usare lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup/AppOwnsData) per iniziare rapidamente e scaricare un'applicazione di esempio che facilita la creazione di un ambiente e l'incorporamento di un report.

Se tuttavia si sceglie di configurare l'ambiente manualmente, è possibile continuare con le istruzioni che seguono.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrare un'applicazione in Azure Active Directory (Azure AD)

[Registrare l'applicazione](register-app.md) in Azure Active Directory per consentire all'applicazione di accedere alle [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/). La registrazione consente di definire un'identità per l'applicazione e di specificare le autorizzazioni per accedere alle risorse REST di Power BI. A seconda che si voglia usare un account master oppure un'[entità servizio](embed-service-principal.md), la registrazione di un'applicazione varia.

Il metodo scelto influisce sul tipo di applicazione da registrare in Azure.

Se si usa account master, procedere con la registrazione di un'app **nativa**. Si sceglie un'app nativa in quanto l'accesso in uso non è interattivo.

Se invece si usa l'entità servizio, è necessario procedere con la registrazione di un'**applicazione Web sul lato server**. Si registra un'applicazione Web sul lato server per creare un segreto dell'applicazione.

## <a name="set-up-your-power-bi-environment"></a>Configurare l'ambiente di Power BI

### <a name="create-a-workspace"></a>Crea un'area di lavoro

Se si incorporano report, dashboard o riquadri per i clienti, è necessario inserire il contenuto all'interno di un'area di lavoro. Esistono diversi tipi di aree di lavoro configurabili: le [aree di lavoro tradizionali](../service-create-workspaces.md) o le [nuove aree di lavoro](../service-create-the-new-workspaces.md). Se si usa un account *master*, non è importante il tipo di area di lavoro usato. Se invece si usa l' *[entità servizio](embed-service-principal.md)* per accedere all'applicazione, è necessario usare le nuove aree di lavoro. In entrambi gli scenari sia l'account *master* sia l'*entità servizio* deve essere un amministratore delle aree di lavoro interessate dall'applicazione.

### <a name="create-and-publish-your-reports"></a>Creare e pubblicare i report

È possibile creare report e set di dati usando Power BI Desktop e quindi pubblicando tali report in un'area di lavoro. Esistono due modi per eseguire questa attività. Un utente finale può pubblicare i report in un'area di lavoro tradizionale usando un account master (licenza di Power BI Pro). Se si usa l'entità servizio, è possibile pubblicare i report nelle nuove aree di lavoro usando le [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/imports/postimportingroup).

La procedura seguente illustra come pubblicare il report in formato PBIX nell'area di lavoro di Power BI.

1. Scaricare l'esempio [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) da GitHub.

    ![Esempio di report](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Aprire il report in formato PBIX di esempio in **Power BI Desktop**.

   ![Report di PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Pubblicare nelle **aree di lavoro**. Questo processo varia a seconda che si stia usando un account master (licenza di Power Pro) oppure un'entità servizio. Se si usa un account master, è possibile pubblicare il report tramite Power BI Desktop.  Se si usa l'entità servizio, è necessario usare le API REST di Power BI.

## <a name="embed-content-using-the-sample-application"></a>Incorporare il contenuto usando l'applicazione di esempio

Questo esempio è volutamente semplice per scopo dimostrativo. Sarà l'utente o lo sviluppatore a scegliere se proteggere il segreto dell'applicazione o le credenziali dell'account master.

Seguire questa procedura per avviare l'incorporamento del contenuto usando l'applicazione di esempio.

1. Scaricare [Visual Studio](https://www.visualstudio.com/) (2013 o versione successiva). Assicurarsi di scaricare la versione più recente [del pacchetto NuGet](https://www.nuget.org/profiles/powerbi).

2. Scaricare l'esempio [App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) da GitHub per iniziare.

    ![Applicazione di esempio App Owns Data](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

3. Aprire il file **Web.config** nell'applicazione di esempio. Per eseguire l'applicazione, è necessario compilare alcuni campi. È possibile scegliere **MasterUser** oppure **ServicePrincipal** per **AuthenticationType**. A seconda del tipo di metodo di autenticazione scelto, è necessario compilare campi diversi.

    > [!Note]
    > Il valore predefinito per **AuthenticationType** in questo esempio è MasterUser.

    <center>

    | **MasterUser** <br> (licenza di Power BI Pro) | **ServicePrincipal** <br> (token solo app)|
    |---------------|-------------------|
    | [applicationId](#application-id) | [applicationId](#application-id) |
    | [workspaceId](#workspace-id) | [workspaceId](#workspace-id) |
    | [reportId](#report-id) | [reportId](#report-id) |
    | [pbiUsername](#power-bi-username-and-password) |  |
    | [pbiPassword](#power-bi-username-and-password) |  |
    |  | [applicationsecret](#application-secret) |
    |  | [tenant](#tenant) |

   </center>

    ![File Web.config](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

### <a name="application-id"></a>ID applicazione

Questo attributo è necessario per entrambe le opzioni di AuthenticationTypes (account master ed [entità servizio](embed-service-principal.md)).

In **applicationId** inserire il valore di **ID applicazione** di **Azure**. Il valore **applicationId** viene usato per l'identificazione dell'applicazione per gli utenti ai quali si richiedono le autorizzazioni.

Per ottenere il valore **applicationId** seguire questa procedura:

1. Accedere al [portale di Azure](https://portal.azure.com).

2. Nel riquadro di spostamento selezionare **Tutti i servizi** e quindi selezionare **Registrazioni app**.

    ![Ricerca di Registrazioni per l'app](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Selezionare l'applicazione che deve usare il valore **applicationId**.

    ![Scelta dell'app](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

4. Viene visualizzato un **ID applicazione** che viene elencato come GUID. Usare questo **ID applicazione** come **applicationId** per l'applicazione.

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

### <a name="workspace-id"></a>ID area di lavoro

Questo attributo è necessario per entrambe le opzioni di AuthenticationTypes (account master ed [entità servizio](embed-service-principal.md)).

Compilare il campo **workspaceId** con il GUID dell'area di lavoro (del gruppo) di Power BI. È possibile ottenere queste informazioni dall'URL di accesso al servizio Power BI o usando Powershell.

URL <br>

![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test"
```

   ![workspaceId ottenuto da Powershell](media/embed-sample-for-customers/embed-sample-for-customers-031-ps.png)

### <a name="report-id"></a>ID del report

Questo attributo è necessario per entrambe le opzioni di AuthenticationTypes (account master ed [entità servizio](embed-service-principal.md)).

Compilare il campo **reportId** con il GUID del report di Power BI. È possibile ottenere queste informazioni dall'URL di accesso al servizio Power BI o usando Powershell.

URL<br>

![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test" | Get-PowerBIReport
```

![reportId ottenuto da Powershell](media/embed-sample-for-customers/embed-sample-for-customers-032-ps.png)

### <a name="power-bi-username-and-password"></a>Nome utente e password di Power BI

Questi attributi sono necessari solo se per AuthenticationType si usa l'account master.

Se si usa l'[entità servizio](embed-service-principal.md) per eseguire l'autenticazione, non è necessario specificare gli attributi di nome utente o password.

* Compilare il campo **pbiUsername** con l'account master Power BI.
* Compilare il campo **pbiPassword** con la password per l'account master Power BI.

### <a name="application-secret"></a>Segreto dell'applicazione

Questo attributo è necessario solo se per AuthenticationType si usa l'opzione [entità servizio](embed-service-principal.md).

Specificare le informazioni per **ApplicationSecret** dalla sezione **Chiavi** in **Registrazioni app** in **Azure**.  Questo attributo si usa con l'[entità servizio](embed-service-principal.md).

Per ottenere il valore **ApplicationSecret**, seguire questa procedura:

1. Accedere al [portale di Azure](https://portal.azure.com).

2. Nel riquadro di spostamento selezionare **Tutti i servizi** e quindi selezionare **Registrazioni app**.

    ![Ricerca di Registrazioni per l'app](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. Selezionare l'applicazione che deve usare il valore **ApplicationSecret**.

    ![Scegliere un'app](media/embed-sample-for-customers/embed-sample-for-customers-0038.png)

4. Selezionare **Certificati e segreti** in **Gestisci**.

5. Selezionare **New client secrets** (Nuovi segreti client).

6. Immettere un nome nella casella **Descrizione** e selezionare una durata. Quindi selezionare **Salva** per ottenere il **Valore** per l'applicazione. Chiudendo il riquadro **Chiavi** dopo aver salvato il valore della chiave, il campo del valore viene visualizzato solo come nascosto. A questo punto, non è possibile recuperare il valore della chiave. Se il valore della chiave viene perso, crearne uno nuovo all'interno del portale di Azure.

    ![Valore chiave](media/embed-sample-for-customers/embed-sample-for-customers-042.png)

### <a name="tenant"></a>Tenant

Questo attributo è necessario solo se per AuthenticationType si usa l'opzione [entità servizio](embed-service-principal.md).

Compilare il campo **tenant** con l'ID tenant di Azure. È possibile ottenere queste informazioni dall'[interfaccia di amministrazione di Azure AD](/onedrive/find-your-office-365-tenant-id) quando si accede al servizio Power BI o tramite PowerShell.

### <a name="run-the-application"></a>Eseguire l'applicazione

1. Selezionare **Esegui** in **Visual Studio**.

    ![Eseguire l'applicazione](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

2. Selezionare quindi **Incorpora report**. A seconda del contenuto con cui si sceglie di eseguire il test (report, dashboard o riquadri), selezionare l'opzione corrispondente nell'applicazione.

    ![Selezionare il contenuto](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

3. È ora possibile visualizzare il report nell'applicazione di esempio.

    ![Visualizzare l'applicazione](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-content-within-your-application"></a>Incorporare il contenuto all'interno dell'applicazione

Anche se la procedura per incorporare il contenuto viene eseguita con le [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/), i codici di esempio descritti in questo articolo vengono creati con **.NET SDK**.

L'incorporamento per i clienti all'interno dell'applicazione richiede l'ottenimento di un **token di accesso** per l'account master o l'[entità servizio](embed-service-principal.md) di **Azure AD**. È necessario ottenere un [token di accesso di Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) per l'applicazione Power BI usando prima di effettuare chiamate alle [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Per creare il client Power BI con il **token di accesso** è consigliabile creare l'oggetto client Power BI, che consente di interagire con le [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/). L'oggetto client Power BI viene creato eseguendo il wrapping di **AccessToken** in un oggetto ***Microsoft.Rest.TokenCredentials***.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Ottenere l'elemento di contenuto da incorporare

Usare l'oggetto client Power BI per recuperare un riferimento all'elemento da incorporare.

Ecco un esempio del codice per recuperare il primo report da un'area di lavoro specifica.

*Un esempio di come recuperare un elemento di contenuto da incorporare, che si tratti di un report, dashboard o riquadro, è disponibile all'interno del file Services\EmbedService.cs nell'[applicazione di esempio](https://github.com/Microsoft/PowerBI-Developer-Samples).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Creare il token di incorporamento
Generare un token di incorporamento che possa essere usato dall'API JavaScript. Esistono due tipi di API. Il primo gruppo contiene cinque API, ognuna delle quali genera un token di incorporamento per un elemento specifico. Il secondo gruppo, che contiene una sola API, genera un token che può essere usato per incorporare più elementi.

**API per la generazione di un token di incorporamento per un elemento specifico**

Il token di incorporamento creato con queste API è specifico per l'elemento da incorporare. Ogni volta che si incorpora un elemento di Power BI (ad esempio un report, un dashboard o un riquadro) con queste API, è necessario creare un nuovo token di incorporamento per l'elemento.
* [GenerateTokenInGroup per i dashboard](https://docs.microsoft.com/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)
* [GenerateTokenInGroup per i set di dati](https://docs.microsoft.com/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)
* [GenerateTokenForCreateInGroup per i report](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)
* [GenerateTokenInGroup per i report](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokeningroup)
* [GenerateTokenInGroup per i riquadri](https://docs.microsoft.com/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

Esempi di creazione di un token di incorporamento per un report, un dashboard o un riquadro sono disponibili nei file seguenti dell'[applicazione di esempio](https://github.com/Microsoft/PowerBI-Developer-Samples).
* Services\EmbedService.cs
* Models\EmbedConfig.cs
* Models\TileEmbedConfig.cs

Di seguito è riportato un esempio di codice per l'uso dell'API del token di incorporamento GenerateTokenInGroup per i report.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

**API per la generazione di un token di incorporamento per più elementi**<a id="multiEmbedToken"></a>

L'API di incorporamento [GenerateToken](https://docs.microsoft.com/rest/api/power-bi/embedtoken/generatetoken) genera un token che può essere usato per incorporare più elementi.

Può anche essere usato per selezionare in modo dinamico un set di dati durante l'incorporamento di un report. Per altre informazioni su questo uso dell'API, vedere il [binding dinamico](embed-dynamic-binding.md).


Di seguito è riportato un esempio di uso di questa API.
 
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var reports = new List<GenerateTokenRequestV2Report>()
{ 
    new GenerateTokenRequestV2Report()
    {
        AllowEdit = false,
        Id = report1.Id
    },
    new GenerateTokenRequestV2Report()
    {
        AllowEdit = true,
        Id = report2.Id
    }
};

var datasets= new List<GenerateTokenRequestV2Dataset>()
{
    new GenerateTokenRequestV2Dataset(dataset1.Id),
    new GenerateTokenRequestV2Dataset(dataset2.Id),
    new GenerateTokenRequestV2Dataset(dataset3.Id),
};

var targetWorkspaces = new List<GenerateTokenRequestV2TargetWorkspace>()
{
    new GenerateTokenRequestV2TargetWorkspace(workspace1.Id),
    new GenerateTokenRequestV2TargetWorkspace(workspace2.Id),
};

var request = new GenerateTokenRequestV2()
{
    Datasets = datasetsRequestDetails ?? null,
    Reports = reportsRequestDetails,
    TargetWorkspaces = targetWSRequestdetials ?? null,
};

var token = client.GetClient().EmbedToken.GenerateToken(request);
```

### <a name="load-an-item-using-javascript"></a>Caricare un elemento con JavaScript

È possibile usare JavaScript per caricare un report in un elemento div nella pagina Web.

Per un esempio completo dell'uso dell'API JavaScript, è possibile usare lo [strumento Playground](https://microsoft.github.io/PowerBI-JavaScript/demo), Lo strumento Playground consente di riprodurre in modo rapido esempi di Power BI Embedded di tipo diverso. È anche possibile ottenere maggiori informazioni sull'API JavaScript visitando la pagina del [wiki Power BI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Segue un esempio che usa un modello **EmbedConfig** e un modello **TileEmbedConfig** insieme a visualizzazioni per un report.

*Un esempio di come aggiungere una visualizzazione per un report, dashboard o riquadro è disponibile nei file Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml o Views\Home\Embedtile.cshtml nell'[applicazione di esempio](#embed-content-using-the-sample-application).*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>Passare alla produzione

Lo sviluppo dell'applicazione è terminato. È ora necessario eseguire il backup dell'area di lavoro con una capacità dedicata. 

> [!Important]
> La capacità dedicata è necessaria per passare alla produzione. Tutte le aree di lavoro (quelle contenenti i report o i dashboard e quelle contenenti il set di dati) devono essere assegnate a una capacità.

### <a name="create-a-dedicated-capacity"></a>Creare una capacità dedicata

Tramite la creazione di una capacità dedicata è possibile trarre vantaggio dalla disponibilità di una risorsa dedicata destinata ai clienti. È possibile scegliere tra due tipi di capacità:
* **Power BI Premium**: sottoscrizione di Office 356 a livello di tenant disponibile in due famiglie di SKU, *EM* e *P*. Quando si incorpora contenuto di Power BI, questa soluzione viene definita *incorporamento di Power BI*. Per altre informazioni su questa sottoscrizione, vedere [Che cos'è Power BI Premium?](../service-premium-what-is.md)
* **Azure Power BI Embedded**: è possibile acquistare una capacità dedicata dal [portale di Microsoft Azure](https://portal.azure.com). Questa sottoscrizione usa gli SKU *A*. Per informazioni dettagliate su come creare una capacità per Power BI Embedded, vedere [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) (Creare capacità per Power BI Embedded nel portale di Azure).
> [!NOTE]
> Con gli SKU A non è possibile accedere al contenuto di Power BI con una licenza di Power BI gratuita.

La tabella seguente descrive le risorse e i limiti di ogni SKU. Per determinare la capacità più adatta alle proprie esigenze, vedere la tabella [Quale SKU devo acquistare per il mio scenario](https://docs.microsoft.com/power-bi/developer/embedded-faq#power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario).

| Nodi delle capacità | Totale vCore | vCore back-end | RAM (GB) | vCore front-end | Connessione dinamica/DirectQuery (al secondo) | Parallelismo di aggiornamento dei modelli |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="development-testing"></a>Test dello sviluppo

I token di incorporamento con licenza Pro sono destinati al test dello sviluppo, pertanto il numero di token di incorporamento che un account master Power BI o un'entità servizio può generare è limitato. È richiesta una capacità dedicata per l'incorporamento in un ambiente di produzione. Con una capacità dedicata è possibile generare un numero illimitato di token di incorporamento. Vedere [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) (Funzionalità disponibili) per controllare il valore di utilizzo che indica l'attuale utilizzo incorporato espresso come percentuale. La quantità di utilizzo è calcolata per ogni account master.

Per altre informazioni, vedere [Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità di analisi incorporata).

### <a name="assign-a-workspace-to-a-dedicated-capacity"></a>Assegnare un'area di lavoro a una capacità dedicata

Dopo aver creato una capacità dedicata, è possibile assegnare a questa l'area di lavoro.

Per assegnare una capacità dedicata a un'area di lavoro con un'[entità servizio](embed-service-principal.md), usare l'[API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/capacities/groups_assigntocapacity). Quando si usano le API REST di Power BI, assicurarsi di usare l'[ID oggetto dell'entità servizio](embed-service-principal.md#how-to-get-the-service-principal-object-id).

Seguire questa procedura per assegnare una capacità dedicata a un'area di lavoro usando un **account master**.

1. All'interno del **servizio Power BI** espandere le aree di lavoro e selezionare i puntini di sospensione relativi all'area di lavoro in cui incorporare il contenuto. Quindi selezionare **Edit workspaces** (Modifica aree di lavoro).

    ![Modifica area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Espandere **Avanzate**, abilitare **Capacità dedicata** e quindi selezionare la capacità dedicata creata. Selezionare quindi **Salva**.

    ![Assegnare la capacità dedicata](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. Dopo aver selezionato **Salva** è possibile vedere l'icona di un **diamante** accanto al nome dell'area di lavoro.

    ![Area di lavoro collegata a una capacità](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come incorporare il contenuto di Power BI in un'applicazione per i clienti. È anche possibile provare a incorporare il contenuto di Power BI per l'organizzazione.

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
