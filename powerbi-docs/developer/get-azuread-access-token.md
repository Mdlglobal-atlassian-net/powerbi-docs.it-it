---
title: Autenticare gli utenti e ottenere un token di accesso di Azure AD per l'applicazione
description: Informazioni su come registrare un'applicazione in Azure Active Directory per incorporare il contenuto di Power BI.
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
ms.date: 08/11/2017
ms.author: maghan
ms.openlocfilehash: 3ff0fa3c83654ac577e98e730dc68ce3686e1198
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="authenticate-users-and-get-an-azure-ad-access-token-for-your-power-bi-app"></a>Autenticare gli utenti e ottenere un token di accesso di Azure AD per l'app Power BI
Informazioni su come eseguire l'autenticazione di utenti nell'applicazione Power BI e come recuperare un token di accesso da usare con l'API REST.

Prima di potere chiamare l'API REST di Power BI, è necessario ottenere un **token di accesso per l'autenticazione** (token di accesso) di Azure Active Directory (Azure AD) . Un **token di accesso** viene usato per consentire all'app di accedere ai dashboard, ai riquadri e ai report di **Power BI**. Per altre informazioni sul flusso di **token di accesso** di Azure Active Directory, vedere [Flusso di concessione del codice di autorizzazione](https://msdn.microsoft.com/library/azure/dn645542.aspx).

La modalità di recupero del token di accesso dipende dal modo in cui si incorpora il contenuto. In questo articolo vengono usati due approcci diversi.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Token di accesso per utenti di Power BI (i dati sono di proprietà dell'utente)
Questo esempio è relativo agli scenari in cui gli utenti accedono manualmente ad Azure AD con le credenziali di accesso dell'organizzazione. Questo approccio viene usato quando si incorpora contenuto da utenti di Power BI che accederanno al contenuto a cui sono autorizzati ad accedere nel servizio Power BI.

### <a name="get-an-authorization-code-from-azure-ad"></a>Ottenere un codice di autorizzazione da Azure AD
Il primo passaggio per ottenere un **token di accesso** consiste nell'ottenere un codice di autorizzazione da **Azure AD**. A questo scopo, creare una stringa di query con le proprietà seguenti e reindirizzarla ad **Azure AD**.

**Stringa di query del codice di autorizzazione**

```
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

In redirect.aspx.cs verrà effettuata una chiamata a [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) per la generazione del token.

**Ottenere il codice di autorizzazione**

```
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
    // AADAuthorityUri = https://login.windows.net/common/oauth2/authorize/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Ottenere un token di accesso dal codice di autorizzazione
A questo punto si sarà ottenuto un codice di autorizzazione da Azure AD. Dopo che **Azure AD** avrà reindirizzato all'utente l'app Web con un **codice di autorizzazione**, si userà il **codice di autorizzazione** per ottenere un token di accesso. Di seguito è disponibile un esempio in C# che può essere usato nella pagina di reindirizzamento e nell'evento Page_Load per la pagina default.aspx.

Lo spazio dei nomi **Microsoft.IdentityModel.Clients.ActiveDirectory** può essere recuperato dal pacchetto NuGet [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

**Redirect.aspx.cs**

```
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

**Default.aspx**

```
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
Questo approccio viene in genere usato per applicazioni di tipo fornitore di software indipendente, in cui l'app è proprietaria dell'accesso ai dati. Gli utenti non saranno necessariamente utenti di Power BI e l'applicazione controlla l'autenticazione e l'accesso per gli utenti finali.

Per questo approccio verrà usato un singolo account *master* corrispondente a un utente di Power BI Pro. Le credenziali per questo account vengono archiviate insieme all'applicazione. L'applicazione eseguirà l'autenticazione in Azure AD con queste credenziali archiviate. Il codice di esempio seguente è tratto da [App owns data sample](https://github.com/guyinacube/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data) (Esempio "App owns data").

**HomeController.cs**

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;

// Create a user password cradentials.
var credential = new UserPasswordCredential(Username, Password);

// Authenticate using created credentials
var authenticationContext = new AuthenticationContext(AuthorityUrl);
var authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, ClientId, credential);

if (authenticationResult == null)
{
    return View(new EmbedConfig()
    {
        ErrorMessage = "Authentication Failed."
    });
}

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

Per informazioni su come usare **await**, vedere [await (Riferimenti per C#)](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/await)

## <a name="next-steps"></a>Passaggi successivi
Quando è disponibile il token di accesso, è possibile chiamare l'API REST di Power BI per incorporare il contenuto. Per informazioni su come incorporare il contenuto, vedere [Come incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md#step-2-embed-your-content).

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

