---
title: Autenticare gli utenti e ottenere un token di accesso di Azure AD per l'applicazione
description: Informazioni su come registrare un'applicazione in Azure Active Directory per incorporare il contenuto di Power BI.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: a38547807fbbcf3c76366f32caa46945e57ca8bc
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710309"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Ottenere un token di accesso di Azure AD per l'applicazione Power BI

Informazioni su come eseguire l'autenticazione di utenti nell'applicazione Power BI e come recuperare un token di accesso da usare con l'API REST.

Prima di potere chiamare l'API REST di Power BI, è necessario ottenere un **token di accesso per l'autenticazione** (token di accesso) di Azure Active Directory (Azure AD) . Un **token di accesso** viene usato per consentire all'app di accedere ai dashboard, ai riquadri e ai report di **Power BI**. Per altre informazioni sul flusso di **token di accesso** di Azure Active Directory, vedere [Flusso di concessione del codice di autorizzazione](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

La modalità di recupero del token di accesso dipende dal modo in cui si incorpora il contenuto. In questo articolo vengono usati due approcci diversi.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token di accesso per utenti di Power BI (i dati sono di proprietà dell'utente)

Questo esempio è relativo agli scenari in cui gli utenti accedono manualmente ad Azure AD con le credenziali di accesso dell'organizzazione. Questa attività viene usata quando si incorpora contenuto per utenti di Power BI che accedono al contenuto a cui sono autorizzati ad accedere nel servizio Power BI.

### <a name="get-an-authorization-code-from-azure-ad"></a>Ottenere un codice di autorizzazione da Azure AD

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
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

Dopo aver creato una stringa di query, reindirizzarla ad **Azure AD** per ottenere un **codice di autorizzazione**.  Di seguito è riportato un metodo C# completo per creare una stringa di query per il **codice di autorizzazione** e reindirizzarla ad **Azure AD**. Dopo aver ottenuto il codice di autorizzazione, si ottiene un **token di accesso** usando il **codice di autorizzazione**.

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
        {"redirect_uri", "http://localhost:13526/Redirect"}
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

A questo punto si sarà ottenuto un codice di autorizzazione da Azure AD. Dopo che **Azure AD** avrà reindirizzato all'utente l'app Web con un **codice di autorizzazione**, si userà il **codice di autorizzazione** per ottenere un token di accesso. Di seguito è disponibile un esempio in C# che può essere usato nella pagina di reindirizzamento e nell'evento Page_Load per la pagina default.aspx.

Lo spazio dei nomi **Microsoft.IdentityModel.Clients.ActiveDirectory** può essere recuperato dal pacchetto NuGet [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

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

Questo approccio viene in genere usato per applicazioni di tipo fornitore di software indipendente, in cui l'app è proprietaria dell'accesso ai dati. Gli utenti non sono necessariamente utenti di Power BI e l'applicazione controlla l'autenticazione e l'accesso per gli utenti finali.

### <a name="access-token-with-a-master-account"></a>Token di accesso con un account master

Per questo approccio viene usato un singolo account *master* corrispondente a un utente di Power BI Pro. Le credenziali per questo account vengono archiviate insieme all'applicazione. L'applicazione esegue l'autenticazione in Azure AD con queste credenziali archiviate. Il codice di esempio seguente è tratto da [App owns data sample](https://github.com/guyinacube/PowerBI-Developer-Samples) (Esempio "App owns data").

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

* Scaricare [ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) se si verifica un "'AuthenticationContext' non contiene una definizione per 'AcquireToken' e non AcquireToken accessibile' ' e di che accetta un primo argomento di tipo ' AuthenticationContext' è stato trovato (probabilmente manca un utilizzo della direttiva o un riferimento all'assembly?) "errore.

## <a name="next-steps"></a>Passaggi successivi

Quando è disponibile il token di accesso, è possibile chiamare l'API REST di Power BI per incorporare il contenuto. Per informazioni su come incorporare il contenuto, vedere l'articolo che spiega [come incorporare il contenuto di Power BI](embed-sample-for-customers.md#embed-content-within-your-application).

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)