---
title: Autenticare gli utenti e ottenere un token di accesso di Azure AD per l'applicazione
description: Informazioni su come registrare un'applicazione in Azure Active Directory per incorporare il contenuto di Power BI.
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: 1655843d9e3175b9c428434fd533a601cc42d847
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875751"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Ottenere un token di accesso di Azure AD per l'applicazione Power BI

Questo articolo illustra come eseguire l'autenticazione di utenti nell'applicazione Power BI e come recuperare un token di accesso da usare con l'[API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Prima di potere chiamare l'API REST, l'applicazione deve ottenere un **token di accesso per l'autenticazione** di Azure Active Directory (Azure AD). Il token consente all'app di accedere a dashboard, riquadri e report di Power BI. Per altre informazioni, vedere [Autorizzare l'accesso alle applicazioni Web di Azure Active Directory con il flusso di concessione del codice di autorizzazione di OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

La modalità di recupero del token di accesso dipende dal modo in cui si incorpora il contenuto. In questo articolo vengono illustrati due approcci diversi.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token di accesso per utenti di Power BI (i dati sono di proprietà dell'utente)

Questo esempio è relativo agli scenari in cui gli utenti accedono manualmente ad Azure AD con le credenziali di accesso dell'organizzazione. Questa attività viene usata quando si incorpora contenuto per gli utenti che hanno accesso al servizio Power BI.

### <a name="get-an-azure-ad-authorization-code"></a>Ottenere un codice di autorizzazione di Azure AD

Il primo passaggio per ottenere un **token di accesso** consiste nell'ottenere un codice di autorizzazione da **Azure AD**. Creare una stringa di query con le proprietà seguenti e reindirizzarla ad **Azure AD**.

#### <a name="authorization-code-query-string"></a>Stringa di query del codice di autorizzazione

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

Dopo aver creato una stringa di query, reindirizzarla ad **Azure AD** per ottenere un **codice di autorizzazione**.  Di seguito è riportato un metodo C# completo per creare una stringa di query per il **codice di autorizzazione** e reindirizzarla ad **Azure AD**. È quindi possibile usare il **codice di autorizzazione** per ottenere un **token di accesso**.

In redirect.aspx.cs [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) effettua una chiamata per generare il token.

#### <a name="get-authorization-code"></a>Ottenere il codice di autorizzazione

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Ottenere un token di accesso dal codice di autorizzazione

Dopo che **Azure AD** avrà reindirizzato l'utente all'app Web con un **codice di autorizzazione**, è possibile usarlo per ottenere un token di accesso. Di seguito è disponibile un esempio in C# che può essere usato nella pagina di reindirizzamento e nell'evento `Page_Load` per default.aspx.

È possibile recuperare lo spazio dei nomi **Microsoft.IdentityModel.Clients.ActiveDirectory** dal pacchetto NuGet [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Token di accesso per utenti non Power BI (i dati sono di proprietà dell'app)

Questo approccio viene in genere usato per applicazioni di tipo fornitore di software indipendente (ISV), in cui l'app è proprietaria dell'accesso ai dati. Gli utenti non sono necessariamente utenti di Power BI e l'applicazione controlla l'autenticazione e l'accesso degli utenti.

### <a name="access-token-with-a-master-account"></a>Token di accesso con un account master

Per questo approccio viene usato un singolo account *master* corrispondente a un utente di Power BI Pro. Le credenziali dell'account vengono archiviate con l'applicazione. L'applicazione esegue l'autenticazione in Azure AD con queste credenziali archiviate. Il codice di esempio seguente è tratto da [App owns data sample](https://github.com/guyinacube/PowerBI-Developer-Samples) (Esempio "App owns data").

### <a name="access-token-with-service-principal"></a>Token di accesso con entità servizio

Per questo approccio si usa un'[entità servizio](embed-service-principal.md) che è un token **App-Only**. L'applicazione esegue l'autenticazione in Azure AD con l'entità servizio. Il codice di esempio seguente è tratto da [App owns data sample](https://github.com/guyinacube/PowerBI-Developer-Samples) (Esempio "App owns data").

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Risoluzione dei problemi

Messaggio di errore: "'AuthenticationContext' doesn't contain a definition for 'AcquireToken' and no accessible 'AcquireToken' accepting a first argument of type 'AuthenticationContext' could be found (are you missing a using directive or an assembly reference?)" ('AuthenticationContext' non contiene una definizione per 'AcquireToken' e non è possibile trovare alcun 'AcquireToken' accessibile che accetti un primo argomento di tipo 'AuthenticationContext' (direttiva using o riferimento assembly mancante)).

   Se viene visualizzato questo errore, provare a scaricare [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727).

## <a name="next-steps"></a>Passaggi successivi

Quando è disponibile il token di accesso, è possibile chiamare l'API REST di Power BI per incorporare il contenuto. Per informazioni, vedere [Come incorporare contenuti di Power BI](embed-sample-for-customers.md#embed-content-within-your-application).

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
