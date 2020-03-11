---
title: Configurare le credenziali a livello di codice per Power BI
description: Come configurare le credenziali a livello di codice durante l'automazione di Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/23/2020
ms.openlocfilehash: 1c8741736f0639cba7f8df3f9891a6fe20397d8e
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079509"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurare le credenziali a livello di codice per Power BI

Eseguire la procedura seguente per configurare le credenziali a livello di codice per Power BI.

## <a name="update-credentials-flow-for-data-sources"></a>Aggiornare un flusso di credenziali per le origini dati

1. Chiamare [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) (Ottieni origini dati) per individuare le origini dati del set di dati. Nel corpo della risposta per ogni origine dati sono indicati tipo, dettagli della connessione, gateway e ID origine dati.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Compilare la stringa di credenziali in base agli [esempi di aggiornamento dell'origine dati](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) a seconda del tipo di credenziali.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Chiamare [Ottieni gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) per recuperare la chiave pubblica del gateway.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Crittografare le credenziali.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    Crittografare la stringa delle credenziali con la chiave pubblica del gateway indicata nel passaggio 2. A versioni diverse del gateway possono corrispondere dimensioni diverse per le chiavi pubbliche. Vedere gli esempi seguenti nel codice dell'SDK, disponibile nel [repository GitHub Power bi-CSharp](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Compilare i dettagli delle credenziali con le credenziali crittografate.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    Usare la classe AssymetricKeyEncriptor con la chiave pubblica recuperata nel **passaggio 3**.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. Chiamare [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Aggiorna origine dati) per impostare le credenziali.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurare una nuova origine dati per un gateway dati

1. Installare il [gateway dati locale](https://powerbi.microsoft.com/gateway/) sul computer.

2. Chiamare [Ottieni gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) per recuperare l'ID e la chiave pubblica del gateway.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Compilare i dettagli delle credenziali come descritto in [Aggiornare un flusso di credenziali per le origini dati](#update-credentials-flow-for-data-sources) usando la chiave pubblica del gateway recuperata nel **passaggio 2**.

4. Compilare il corpo della richiesta.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Chiamare l'API [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Crea origine dati).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Tipi di credenziali

Quando si chiama [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Crea origine dati) o [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Aggiorna origine dati) in un **gateway enterprise locale** usando l'[API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/), i valori delle credenziali devono essere crittografati mediante la chiave pubblica del gateway.

>[!NOTE]
>.NET SDK V3 può eseguire anche gli esempi di .NET SDK v2 elencati di seguito.

### <a name="windows-and-basic-credentials"></a>Credenziali di Windows e di base

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Credenziali della chiave

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**Credenziali OAuth2**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Credenziali anonime**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Nessun gateway e ID di origine dati trovato durante la chiamata Get data sources (Ottieni origini dati)

Questo problema significa che il set di dati non è associato a un gateway. Quando si crea un nuovo set di dati, per ogni connessione cloud viene creata automaticamente un'origine dati senza credenziali nel gateway cloud dell'utente. Questo gateway viene usato per archiviare le credenziali per le connessioni cloud.

Dopo aver creato il set di dati, viene stabilita un'associazione automatica tra il set di dati e un gateway appropriato, che contiene le origini dati corrispondenti per tutte le connessioni. In mancanza di tale gateway o di più gateway appropriati, l'associazione automatica ha esito negativo.

Se si usano set di dati locali, creare le origini dati locali eventualmente mancanti e associare manualmente il set di dati a un gateway usando [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (Associa al gateway).

Per individuare i gateway che possono essere associati, usare [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Individua gateway).