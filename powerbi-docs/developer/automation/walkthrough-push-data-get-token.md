---
title: Ottenere un token di accesso per l'autenticazione
description: "Procedura dettagliata per il push dei dati: Ottenere un token di accesso per l'autenticazione"
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488270"
---
# <a name="step-2-get-an-authentication-access-token"></a>Passaggio 2: Ottenere un token di accesso per l'autenticazione

Questo articolo è il secondo passaggio della serie [Eseguire il push dei dati in un set di dati di Power BI](walkthrough-push-data.md).

Nel passaggio 1 è stata eseguita la [registrazione di un'app client in Azure AD](../embedded/register-app.md). In questo passaggio si ottiene un token di accesso per l'autenticazione. Le app di Power BI sono integrate con Azure Active Directory per offrire accesso e autorizzazione sicuri per l'app. L'app usa un token per l'autenticazione in Azure AD e per l'accesso alle risorse di Power BI.

## <a name="get-an-authentication-access-token"></a>Ottenere un token di accesso per l'autenticazione

Prima di iniziare, assicurarsi di aver completato il [passaggio precedente](../embedded/register-app.md) della serie [Eseguire il push dei dati in un set di dati di Power BI](walkthrough-push-data.md). 

Questa procedura richiede Visual Studio 2015 o versione successiva.

1. In Visual Studio creare un nuovo progetto **Applicazione console** in C#.

2. Installare il [pacchetto NuGet Azure AD Authentication Library per .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). Questo pacchetto viene usato dall'app .NET per ottenere un token di sicurezza per l'autenticazione. 

     a. Selezionare **Strumenti** > **Gestione pacchetti NuGet** > **Console di Gestione pacchetti**.

     b. Immettere **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. In Program.cs aggiungere `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Aggiungere a Program.cs il codice di esempio riportato dopo la procedura.

4. Sostituire "{ClientID}", con l'**ID Client** ottenuto nel [precedente articolo della serie](../embedded/register-app.md) quando l'app è stata registrata.

5. Eseguire l'app console e accedere al proprio account di Power BI. 

   Nella finestra della console dovrebbe essere presente una stringa di token.

**Codice di esempio per ottenere il token di sicurezza per l'autenticazione**

Aggiungere questo codice a Program {...}.

* Una variabile token per chiamare le operazioni: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* In static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Aggiungere un metodo GetToken():

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Dopo avere ottenuto un token di autenticazione, è possibile chiamare qualsiasi operazione di Power BI.

L'articolo successivo della serie illustra come [creare un set di dati in Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Listato di codice completo

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Passaggi successivi

* L'articolo successivo della serie è [Creare un set di dati in Power BI](walkthrough-push-data-create-dataset.md)
* [Panoramica dell'API REST di Power BI](overview-of-power-bi-rest-api.md)  
* [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)