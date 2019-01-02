---
title: Funzionalità di analisi incorporata per incorporare contenuto di Power BI nell'applicazione per i clienti
description: Informazioni su come integrare o incorporare un report, un dashboard o un riquadro in un'applicazione tramite le API di Power BI per l'analisi incorporata per i clienti. Informazioni su come integrare Power BI nell'applicazione usando software di analisi incorporata, strumenti di analisi incorporata o strumenti di business intelligence incorporata.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: 96cd04385bec6d4b9b47e3e05a30820b2f19f3dd
ms.sourcegitcommit: 9913c213d40b45ba83c6c3b3a7ef0b757800e3ad
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53301874"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Esercitazione: Incorporare un report, un dashboard o un riquadro di Power BI in un'applicazione per i clienti

Con **Power BI Embedded in Azure**, è possibile incorporare report, dashboard o riquadri in un'applicazione usando dati di proprietà dell'app. **I dati di proprietà dell'app** consistono nel disporre di un'applicazione che usa Power BI come piattaforma di analisi incorporata. Gli **sviluppatori ISV** possono creare contenuti Power BI che visualizzano report, dashboard o riquadri in un'applicazione completamente integrata e interattiva, senza richiedere agli utenti di disporre di una licenza Power BI. Questa esercitazione illustra come integrare un report in un'applicazione tramite .NET SDK di Power BI insieme all'API JavaScript di Power BI quando si usa **Power BI Embedded in Azure** per i clienti.

In questa esercitazione viene illustrato come:
> [!div class="checklist"]
> * Registrare un'applicazione in Azure.
> * Incorporare un report di Power BI in un'applicazione.

## <a name="prerequisites"></a>Prerequisiti

Per iniziare, è necessario un account **Power BI Pro**, che costituirà il proprio **account master** e una sottoscrizione **Microsoft Azure**.

* Se non si è ancora iscritti a **Power BI Pro**, [iscriversi per ottenere una versione di prova gratuita](https://powerbi.microsoft.com/en-us/pricing/) prima di iniziare.
* Se non si ha una sottoscrizione di Azure, [creare un account gratuito](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) prima di iniziare.
* È necessario disporre del proprio [tenant di Azure Active Directory](create-an-azure-active-directory-tenant.md) configurato.
* È richiesta l'installazione di [Visual Studio](https://www.visualstudio.com/) (versione 2013 o successive).

## <a name="set-up-your-embedded-analytics-development-environment"></a>Configurare l'ambiente di sviluppo di analisi incorporata

Prima di iniziare a incorporare report, dashboard o riquadri in un'applicazione, è necessario assicurarsi che l'ambiente consenta l'incorporamento con Power BI.

È possibile usare lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup/AppOwnsData) per iniziare rapidamente scaricando un'applicazione di esempio che facilita l'esecuzione della procedura di creazione di un ambiente e di incorporamento di un report.

Se tuttavia si sceglie di configurare l'ambiente manualmente, è possibile continuare con le istruzioni che seguono.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrare un'applicazione in Azure Active Directory (Azure AD)

La registrazione dell'applicazione in Azure Active Directory consente all'applicazione di accedere alle API REST di Power BI. La registrazione consente di definire un'identità per l'applicazione e di specificare le autorizzazioni per accedere alle risorse REST di Power BI.

1. Accettare le [condizioni relative all'API di Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Accedere al [portale di Azure](https://portal.azure.com).

    ![Pagina principale del portale di Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. Nel riquadro di spostamento a sinistra scegliere **Tutti i servizi**, selezionare **Registrazioni per l'app** e quindi scegliere **Registrazione nuova applicazione**.

    ![Ricerca di Registrazioni per l'app](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Registrazione nuova applicazione](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Seguire le istruzioni e creare una nuova applicazione. Per i dati di proprietà delle app è necessario usare **Nativa** per il tipo di applicazione. È anche necessario specificare un **URI di reindirizzamento**, che verrà usato da **Azure AD** per restituire le risposte del token. Immettere un valore specifico per l'applicazione (ad esempio: `http://localhost:13526/Redirect`).

    ![Creare l'app](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Applicare le autorizzazioni all'applicazione in Azure Active Directory

Abilitare autorizzazioni aggiuntive per l'applicazione, incluse quelle fornite nella pagina di registrazione dell'app. Accedere con l'account *master* usato per l'incorporamento. L'account master dev'essere un account amministratore globale.

### <a name="use-the-azure-active-directory-portal"></a>Usare il portale di Azure Active Directory

1. Passare a [Registrazioni per l'app](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) nel portale di Azure e selezionare l'app che si usa per l'incorporamento.

    ![Scelta dell'app](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Selezionare **Impostazioni** e quindi in **Accesso all'API** selezionare **Autorizzazioni necessarie**.

    ![Autorizzazioni necessarie](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Selezionare **Microsoft Azure Active Directory** e quindi accertarsi che l'opzione **Accede alla directory come utente registrato** sia selezionata. Selezionare **Salva**.

    ![Autorizzazioni di Microsoft Azure AD](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Selezionare **Aggiungi**.

    ![Aggiungere autorizzazioni](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Fare clic su **Selezionare un'API**.

    ![Aggiungere l'accesso all'API](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Selezionare **Servizio Power BI** e quindi **Seleziona**.

    ![Selezionare i servizi PBI](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Selezionare tutte le autorizzazioni in **Autorizzazioni delegate**. Al termine, selezionare **Salva**.

    ![Selezionare le autorizzazioni delegate](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. In **Autorizzazioni necessarie** selezionare **Concedi autorizzazioni**.

    Per l'azione **Concedi autorizzazioni** è necessaria la presenza dell'*account master* per evitare che venga richiesto il consenso da Azure AD. Se l'account che esegue questa azione è un amministratore globale, è necessario concedere autorizzazioni per questa applicazione a tutti gli utenti dell'organizzazione. Se l'account che esegue questa azione è l'*account master* e non un amministratore globale, è necessario concedere autorizzazioni per questa applicazione solo all'*account master*.

    ![Concedere autorizzazioni nella finestra di dialogo Autorizzazioni necessarie](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

## <a name="set-up-your-power-bi-environment"></a>Configurare l'ambiente di Power BI

### <a name="create-an-app-workspace"></a>Crea area di lavoro per le app

Se si incorporano report, dashboard o riquadri per i clienti, è necessario inserire il contenuto all'interno di un'area di lavoro per le app. L'account *master* deve essere un amministratore dell'area di lavoro per le app.

1. Iniziare creando l'area di lavoro. Selezionare **Aree di lavoro** > **Creare un'area di lavoro per le app**. In Crea area di lavoro per le app inserire il contenuto a cui l'applicazione deve accedere.

    ![Creare l'area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Assegnare un nome all'area di lavoro. Se il corrispondente **ID area di lavoro** non è disponibile, modificarlo in modo da ottenere un ID univoco.

    ![Assegnare un nome all'area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Ci sono alcune opzioni da impostare. Se si sceglie **Pubblica**, chiunque nell'organizzazione potrà visualizzare il contenuto dell'area di lavoro. Se si sceglie **Privata**, solo i membri dell'area di lavoro potranno visualizzarne il contenuto.

    ![Pubblica/Privata](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    Dopo aver creato il gruppo, non è possibile modificare l'impostazione di gruppo pubblico o privato.

4. È anche possibile scegliere se i membri possono **modificare** o avere l'accesso di **sola visualizzazione**.

    ![Aggiunta di membri](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Aggiungere gli indirizzi di posta elettronica delle persone che avranno accesso all'area di lavoro e selezionare **Aggiungi**. Non è possibile aggiungere alias di gruppo, soli singoli utenti.

6. Decidere se ogni persona è un membro o un amministratore. Gli amministratori possono modificare l'area di lavoro stessa, inclusa l'aggiunta di altri membri. I membri possono modificare il contenuto nell'area di lavoro, a meno che non abbiano accesso in sola visualizzazione. Sia gli amministratori che i membri possono pubblicare l'app.

    È ora possibile visualizzare la nuova area di lavoro. Power BI crea l'area di lavoro, che verrà aperta e visualizzata nell'elenco delle aree di lavoro di cui si è membri. Gli amministratori potranno a questo punto selezionare i puntini di sospensione (…) per tornare indietro e apportare modifiche, aggiungere nuovi membri o modificarne le autorizzazioni.

    ![Nuova area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Creare e pubblicare i report

È possibile creare report e set di dati usando Power BI Desktop e quindi pubblicando tali report in un'area di lavoro per le app. Per poter pubblicare in un'area di lavoro dell'app, l'utente finale che pubblica report deve avere una licenza di Power BI Pro.

1. Scaricare l'esempio [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) da GitHub.

    ![Esempio di report](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Aprire il report di esempio con estensione pbix in **Power BI Desktop**.

   ![Report di PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Eseguire la pubblicazione nell'**area di lavoro per le app**.

   ![Pubblicare il report di PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    È ora possibile visualizzare il report nel servizio Power BI online.

   ![Visualizzazione del report di PBI Desktop nel servizio](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content-using-the-sample-application"></a>Incorporare il contenuto usando l'applicazione di esempio

Seguire questi passaggi per avviare l'incorporamento dei contenuti usando un'applicazione di esempio.

1. Scaricare l'esempio [App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) da GitHub per iniziare.

    ![Applicazione di esempio App Owns Data](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Aprire il file Web.config nell'applicazione di esempio. Per eseguire correttamente l'applicazione è necessario compilare 5 campi: **applicationId**, **workspaceId**, **reportId**, **pbiUsername** e **pbiPassword**.

    ![File Web.config](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    In **applicationId** inserire il valore di **ID applicazione** di **Azure**. Il valore **applicationId** viene usato per l'identificazione dell'applicazione per gli utenti ai quali si richiedono le autorizzazioni. Per ottenere il valore **applicationId** seguire questa procedura:

    Accedere al [portale di Azure](https://portal.azure.com).

    ![Pagina principale del portale di Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

    Nel riquadro di spostamento a sinistra, scegliere **Tutti i servizi** e selezionare **Registrazioni app**.

    ![Ricerca di Registrazioni per l'app](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

    Selezionare l'applicazione per cui si vuole recuperare il valore **applicationId**.

    ![Scelta dell'app](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

    Dovrebbe essere visualizzato un **ID applicazione** che viene elencato come GUID. Usare questo **ID applicazione** come **applicationId** per l'applicazione.

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

    Compilare il campo **workspaceId** con il **GUID dell'area di lavoro per le app** di Power BI.

    ![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    Compilare il campo **reportId** con il **GUID del report** di Power BI.

    ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

    * Compilare il campo **pbiUsername** con l'account utente master Power BI.
    * Compilare il campo **pbiPassword** con la password per l'account utente master Power BI.

3. Eseguire l'applicazione.

    Per prima cosa, selezionare **Esegui** in **Visual Studio**.

    ![Eseguire l'applicazione](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Selezionare quindi **Incorpora report**. A seconda del contenuto con cui si sceglie di eseguire il test (report, dashboard o riquadri), selezionare l'opzione corrispondente nell'applicazione.

    ![Selezionare il contenuto](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

    È ora possibile visualizzare il report nell'applicazione di esempio.

    ![Visualizzare l'applicazione](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-your-content-within-your-application"></a>Incorporare il contenuto all'interno dell'applicazione

Anche se la procedura per incorporare il contenuto può essere eseguita con le [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/), i codici di esempio descritti in questo articolo vengono creati con il **.NET SDK**.

L'incorporamento per i clienti all'interno dell'applicazione richiede l'ottenimento di un **token di accesso** per l'account master da **Azure AD**. È necessario ottenere un [token di accesso di Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) per l'applicazione Power BI usando **dati di proprietà dell'app** prima di effettuare chiamate alle [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/).

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

*Un esempio di come recuperare un elemento di contenuto da incorporare, che si tratti di un report, dashboard o riquadro, è disponibile all'interno del file Controllers\HomeController.cs nell'[applicazione di esempio](#embed-your-content-within-a-sample-application).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Creare il token di incorporamento

Generare un token di incorporamento che possa essere usato dall'API JavaScript. Il token di incorporamento è specifico per l'elemento da incorporare. Ogni volta che si incorpora una parte di contenuto di Power BI, è pertanto necessario creare un nuovo token di incorporamento specifico. Per altre informazioni, incluso il valore **accessLevel** da usare, vedere [GenerateToken API](https://msdn.microsoft.com/library/mt784614.aspx) (API GenerateToken).

Ecco un esempio di come aggiungere all'applicazione un token di incorporamento per un report.

*Un esempio di come creare un token di incorporamento per un report, dashboard o riquadro, è disponibile all'interno del file Controllers\HomeController.cs nell'[applicazione di esempio](#embed-your-content-within-a-sample-application).*

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

Viene creata una classe per **EmbedConfig** e **TileEmbedConfig**. Un esempio è disponibile nel file **Models\EmbedConfig.cs** e nel file **Models\TileEmbedConfig.cs**.

### <a name="load-an-item-using-javascript"></a>Caricare un elemento con JavaScript

È possibile usare JavaScript per caricare un report in un elemento div nella pagina Web.

Per un esempio completo dell'uso dell'API JavaScript, è possibile usare lo [strumento Playground](https://microsoft.github.io/PowerBI-JavaScript/demo), Lo strumento Playground consente di riprodurre in modo rapido esempi di Power BI Embedded di tipo diverso. È anche possibile ottenere maggiori informazioni sull'API JavaScript visitando la pagina del [wiki Power BI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Segue un esempio che usa un modello **EmbedConfig** e un modello **TileEmbedConfig** insieme a visualizzazioni per un report.

*Un esempio di come aggiungere una visualizzazione per un report, dashboard o riquadro è disponibile nei file Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml o Views\Home\Embedtile.cshtml nell'[applicazione di esempio](#embed-your-content-within-a-sample-application).*

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

    // Embed configuration used to describe the what and how to embed.
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

Dopo aver terminato lo sviluppo dell'applicazione, è necessario eseguire il backup dell'area di lavoro dell'app con una capacità dedicata. La capacità dedicata è necessaria per passare alla produzione.

### <a name="create-a-dedicated-capacity"></a>Creare una capacità dedicata

Tramite la creazione di una capacità dedicata è possibile trarre vantaggio dalla disponibilità di una risorsa dedicata destinata ai clienti. È possibile acquistare una capacità dedicata all'interno del [portale di Microsoft Azure](https://portal.azure.com). Per informazioni dettagliate su come creare una capacità per Power BI Embedded, vedere [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) (Creare capacità per Power BI Embedded nel portale di Azure).

Usare la tabella seguente per individuare la capacità di Power BI Embedded più adatta alle proprie esigenze.

| Nodo della capacità | Totale core<br/>*(Back-end + front-end)* | Core di back-end | Core di front-end | Limiti di connessione dinamica/DirectQuery|
| --- | --- | --- | --- | --- | --- |
| A1 |1 vCore |0,5 core, 3 GB RAM |0,5 core |0-5 al secondo |
| A2 |2 vCore |1 core, 5 GB RAM |1 core | 10 al secondo |
| A3 |4 vCore |2 core, 10 GB RAM |2 core | 15 al secondo |
| A4 |8 vCore |4 core, 25 GB RAM |4 core |30 al secondo |
| A5 |16 vCore |8 core, 50 GB RAM |8 core |60 al secondo |
| A6 |32 vCore |16 core, 100 GB RAM |16 core |120 al secondo |

**_Con gli SKU A, non è possibile accedere al contenuto di Power BI con una licenza di Power BI gratuita._**

I token di incorporamento con licenze Pro sono destinati al test dello sviluppo, pertanto il numero di token di incorporamento che un account master Power BI può generare è limitato. È richiesta una capacità dedicata per l'incorporamento in un ambiente di produzione. Con una capacità dedicata è possibile generare un numero illimitato di token di incorporamento. Vedere [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) (Funzionalità disponibili) per controllare il valore di utilizzo che indica l'attuale utilizzo incorporato espresso come percentuale. La quantità di utilizzo è calcolata per ogni account master.

Per altre informazioni, vedere [Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità di analisi incorporata).

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Assegnare un'area di lavoro per le app a una capacità dedicata

Dopo aver creato una capacità dedicata, è possibile assegnare l'area di lavoro dell'app alla capacità dedicata. Per assegnare una capacità dedicata a un'area di lavoro, seguire questa procedura.

1. All'interno del **servizio Power BI** espandere le aree di lavoro e selezionare i puntini di sospensione relativi all'area di lavoro in cui incorporare il contenuto. Quindi selezionare **Edit workspaces** (Modifica aree di lavoro).

    ![Modifica area di lavoro](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Espandere **Avanzate**, abilitare **Capacità dedicata** e quindi selezionare la capacità dedicata creata. Selezionare quindi **Salva**.

    ![Assegnare la capacità dedicata](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. Dopo aver selezionato **Salva** viene visualizzato un **rombo** accanto al nome dell'area di lavoro dell'app.

    ![area di lavoro dell'app assegnata a una capacità](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come incorporare il contenuto di Power BI in un'applicazione per i clienti. È anche possibile provare a incorporare il contenuto di Power BI per l'organizzazione.

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
