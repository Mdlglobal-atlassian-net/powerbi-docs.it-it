---
title: Ottenere un set di dati per aggiungere righe
description: Procedura dettagliata per il push dei dati - Ottenere un set di dati per aggiungere righe in una tabella di Power BI
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: f0ca594b6f87ab2e186909f10a8ba4b7e1bce062
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>Passaggio 4: Ottenere un set di dati per aggiungere righe in una tabella di Power BI
Questo articolo fa parte di una procedura dettagliata per il [push dei dati in un set di dati](walkthrough-push-data.md).

Nel **passaggio 3** [Creare un set di dati in Power BI](walkthrough-push-data-create-dataset.md) della procedura dettagliata per il push dei dati in un set di dati è stata chiamata l'operazione [Create Dataset](https://msdn.microsoft.com/library/mt203562.aspx) per creare un set di dati in Power BI. In questo passaggio si usa l'operazione [Get Datasets](https://msdn.microsoft.com/library/mt203567.aspx) e Newtonsoft.Json per ottenere un ID set di dati. Per aggiungere righe a un set di dati viene usato l'ID set di dati ottenuto nel passaggio 4. Per esempi su come usare l'API REST di Power BI, vedere [API REST di Power BI in APIARY](http://docs.powerbi.apiary.io/).

Per eseguire il push dei dati in un set di dati di Power BI, è necessario fare riferimento alla tabella nel set di dati. Per fare riferimento a una tabella in un set di dati, occorre prima di tutto ottenere un **ID set di dati**. Per ottenere un **ID set di dati** viene usata l'operazione [Get Dataset](https://msdn.microsoft.com/library/mt203567.aspx). L'operazione **Get Dataset** restituisce una stringa JSON contenente un elenco di tutti i set di dati in Power BI. Per deserializzare una stringa JSON è consigliabile usare [Newtonsoft.Json](http://www.newtonsoft.com/json).

Ecco come ottenere un set di dati.

## <a name="get-a-power-bi-dataset"></a>Ottenere un set di dati di Power BI
> **NOTA**: prima di iniziare, assicurarsi di aver seguito i passaggi precedenti della procedura dettagliata per il [push dei dati in un set di dati](walkthrough-push-data.md).
> 
> 

1. Nel progetto Applicazione console creato nel passaggio 2 [Ottenere un token di accesso per l'autenticazione](walkthrough-push-data-get-token.md) della procedura dettagliata per il push dei dati, installare il pacchetto NuGet Newtonsoft.Json. Ecco come installare il pacchetto:
   
     a. In Visual Studio 2015 scegliere **Strumenti** > **Gestione pacchetti NuGet** > **Console di Gestione pacchetti**.
   
     b. In **Console di Gestione pacchetti**immettere Install-Package Newtonsoft.Json.
2. Dopo l'installazione del pacchetto, aggiungere **using Newtonsoft.Json;** a Program.cs.
3. In Program.cs aggiungere il codice seguente per ottenere un **ID set di dati**.
4. Eseguire l'app console e accedere al proprio account di Power BI. Nella finestra della console dovrebbe comparire **ID set di dati** seguito da un ID.

**Esempio di recupero di un set di dati**

Aggiungere questo codice in Program.cs.

* In static void Main(string[] args):
  
  ```
  static void Main(string[] args)
  {
  
    //Get an authentication access token
    token = GetToken();
  
    //Create a dataset in Power BI
    CreateDataset();
  
    //Get a dataset to add rows into a Power BI table
    string datasetId = GetDataset();
  }
  ```
* Aggiungere un metodo GetDatset():
  
  ```
    #region Get a dataset to add rows into a Power BI table
    private static string GetDataset()
    {
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "GET";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        string datasetId = string.Empty;
        //Get HttpWebResponse from GET request
        using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
        {
            //Get StreamReader that holds the response stream
            using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
            {
                string responseContent = reader.ReadToEnd();
  
                //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                //and add using Newtonsoft.Json
                var results = JsonConvert.DeserializeObject<dynamic>(responseContent);
  
                //Get the first id
                datasetId = results["value"][0]["id"];
  
                Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                Console.ReadLine();
  
                return datasetId;
            }
        }
    }
    #endregion
  ```

Il passaggio successivo illustra come [aggiungere righe a una tabella di Power BI](walkthrough-push-data-add-rows.md).

Di seguito è riportato il [listato di codice completo](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Listato di codice completo
    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net;
    using System.IO;
    using Newtonsoft.Json;

    namespace walkthrough_push_data
    {
        class Program
        {
            private static string token = string.Empty;

            static void Main(string[] args)
            {

                //Get an authentication access token
                token = GetToken();

                //Create a dataset in Power BI
                CreateDataset();

                //Get a dataset to add rows into a Power BI table
                string datasetId = GetDataset();

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

            #region Create a dataset in Power BI
            private static void CreateDataset()
            {
                //TODO: Add using System.Net and using System.IO

                string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                //POST web request to create a dataset.
                //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                request.KeepAlive = true;
                request.Method = "POST";
                request.ContentLength = 0;
                request.ContentType = "application/json";

                //Add token to the request header
                request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                //Create dataset JSON for POST request
                string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                    "[{\"name\": \"Product\", \"columns\": " +
                    "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                    "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                    "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                    "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                    "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                    "]}]}";

                //POST web request
                byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
                request.ContentLength = byteArray.Length;

                //Write JSON byte[] into a Stream
                using (Stream writer = request.GetRequestStream())
                {
                    writer.Write(byteArray, 0, byteArray.Length);

                    var response = (HttpWebResponse)request.GetResponse();

                    Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                    Console.ReadLine();
                }
            }
            #endregion

            #region Get a dataset to add rows into a Power BI table
            private static string GetDataset()
            {
                string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                //POST web request to create a dataset.
                //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                request.KeepAlive = true;
                request.Method = "GET";
                request.ContentLength = 0;
                request.ContentType = "application/json";

                //Add token to the request header
                request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                string datasetId = string.Empty;
                //Get HttpWebResponse from GET request
                using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
                {
                    //Get StreamReader that holds the response stream
                    using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                    {
                        string responseContent = reader.ReadToEnd();

                        //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                        //and add using Newtonsoft.Json
                        var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                        //Get the first id
                        datasetId = results["value"][0]["id"];

                        Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                        Console.ReadLine();

                        return datasetId;
                    }
                }
            }
            #endregion
        }
    }

[Passaggio successivo >](walkthrough-push-data-add-rows.md)

## <a name="next-steps"></a>Passaggi successivi
[Aggiungere righe a una tabella di Power BI](walkthrough-push-data-add-rows.md)  
[Newtonsoft.Json](http://www.newtonsoft.com/json)  
[Recupera set di dati](https://msdn.microsoft.com/library/mt203567.aspx)  
[Push dei dati in Power BI](walkthrough-push-data.md)  
[Panoramica dell'API REST di Power BI](overview-of-power-bi-rest-api.md)  
[Riferimento all'API REST di Power BI](https://msdn.microsoft.com/library/mt147898.aspx)  
[API REST di Power BI in APIARY](http://docs.powerbi.apiary.io/)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

