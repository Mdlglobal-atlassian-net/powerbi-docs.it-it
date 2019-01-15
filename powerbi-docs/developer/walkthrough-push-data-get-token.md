---
title: Ottenere un token di accesso per l'autenticazione
description: Procedura dettagliata per il push dei dati - Ottenere un token di accesso per l'autenticazione
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: 2cba79a98400ba517bca8e61fca743bc0024a122
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54288866"
---
# <a name="step-2-get-an-authentication-access-token"></a>Passaggio 2: Ottenere un token di accesso per l'autenticazione
Questo articolo fa parte di una procedura dettagliata per il [push dei dati in un set di dati](walkthrough-push-data.md).

Nel **passaggio 1** [Registrare l'app in Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) della procedura per il push dei dati in un set di dati è stata registrata un'app client in Azure AD. In questo passaggio si ottiene un token di accesso per l'autenticazione. Le app di Power BI sono integrate con **Azure AD** per fornire funzionalità sicure di accesso e autorizzazione per l'app. Si usa un token per l'autenticazione in **Azure AD** e l'accesso alle risorse di Power BI.

Ecco come ottenere un token di accesso per l'autenticazione.

## <a name="get-an-authentication-access-token"></a>Ottenere un token di accesso per l'autenticazione
> **NOTA**: Prima di iniziare, assicurarsi di aver seguito i passaggi precedenti della procedura dettagliata per il [push dei dati in un set di dati](walkthrough-push-data.md).
> 
> 

1. In Visual Studio 2015 creare un progetto **Applicazione console** .
2. Installare il [pacchetto NuGet Azure AD Authentication Library per .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/). Questo pacchetto viene usato per ottenere un token di sicurezza per l'autenticazione in un'app .NET. Ecco come installare il pacchetto:
   
     a. In Visual Studio 2015 scegliere **Strumenti** > **Gestione pacchetti NuGet** > **Console di Gestione pacchetti**.
   
     b. In **Console di Gestione pacchetti**immettere Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612.
3. Aggiungere il codice seguente nella classe Program {…}.
4. Sostituire "{ClientID}" con l' **ID client** ottenuto in fase di registrazione dell'app. Vedere [Registrare l'app in Azure AD](walkthrough-push-data-register-app-with-azure-ad.md).
5. Dopo aver installato il pacchetto Microsoft.IdentityModel.Clients.ActiveDirectory, aggiungere **using Microsoft.IdentityModel.Clients.ActiveDirectory;** a Program.cs.
6. Eseguire l'app console e accedere al proprio account di Power BI. Nella finestra della console dovrebbe essere presente una stringa di token.

**Codice di esempio per ottenere il token di sicurezza per l'autenticazione**

Aggiungere questo codice a Program {...}.

* Una variabile token per chiamare le operazioni:
  
  ```
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* In static void Main(string[] args):
  
  ```
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Aggiungere un metodo GetToken():

```
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
           string authorityUri = "https://login.windows.net/common/oauth2/authorize";

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

Dopo avere ottenuto un token di autenticazione, è possibile chiamare qualsiasi operazione di Power BI. Il passaggio successivo illustra come chiamare l'operazione [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) per creare un set di dati ed eseguire il push dei dati in un dashboard.

Il passaggio successivo illustra come [creare un set di dati in Power BI](walkthrough-push-data-create-dataset.md).

Di seguito è riportato il [listato di codice completo](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Listato di codice completo
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
                string authorityUri = "https://login.windows.net/common/oauth2/authorize";

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


[Passaggio successivo >](walkthrough-push-data-create-dataset.md)

## <a name="next-steps"></a>Passaggi successivi
[Creare un set di dati in Power BI](walkthrough-push-data-create-dataset.md)  
[Registrare un'app in Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)  
[Azure AD Authentication Library per il pacchetto NuGet .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)  
[Eseguire il push dei dati in un set di dati di Power BI](walkthrough-push-data.md)  
[Panoramica dell'API REST di Power BI](overview-of-power-bi-rest-api.md)  
[Riferimento all'API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

