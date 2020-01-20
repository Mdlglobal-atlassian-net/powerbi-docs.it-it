---
title: Configurare le credenziali a livello di codice per Power BI
description: Come configurare le credenziali a livello di codice per Power BI per l'automazione
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836583"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurare le credenziali a livello di codice per Power BI

Eseguire la procedura seguente per configurare le credenziali a livello di codice per Power BI.

## <a name="configure-a-credential-flow-for-data-sources"></a>Configurare un flusso di credenziali per le origini dati

1. Chiamare [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) (Ottieni origini dati) per individuare le origini dati del set di dati. Nel corpo della risposta per ogni origine dati sono indicati tipo, dettagli della connessione, gateway e ID origine dati.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Compilare la stringa di credenziali in base agli [esempi di aggiornamento dell'origine dati](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) a seconda del tipo di credenziali.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Compilare i dettagli delle credenziali.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Chiamare [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Aggiorna origine dati) per impostare le credenziali, usando il gateway e l'ID origine dati del passaggio 1 e i dettagli delle credenziali del passaggio 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Flusso delle credenziali dell'origine dati locale scaduto

1. [Seguire i passaggi 1 e 2 dello scenario precedente](#configure-a-credential-flow-for-data-sources).

2. Chiamare [Ottieni gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) per recuperare la chiave pubblica del gateway.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Crittografare la stringa delle credenziali con la chiave pubblica del gateway. A versioni diverse del gateway possono corrispondere dimensioni diverse per le chiavi pubbliche.
    
    Vedere l'esempio nel codice SDK, disponibile nel repository GitHub Power bi-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. Compilare i dettagli delle credenziali con le credenziali crittografate.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Chiamare [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Aggiorna origine dati) per impostare le credenziali.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurare una nuova origine dati per un gateway dati

1. Installare il [gateway dati locale](https://powerbi.microsoft.com/gateway/) sul computer.

2. Chiamare [Ottieni gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) per recuperare l'ID e la chiave pubblica del gateway.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Compilare i dettagli delle credenziali come nello scenario precedente tramite la chiave pubblica del gateway recuperata nel passaggio [Flusso delle credenziali dell'origine dati locale scaduto](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway).

4. compilare il corpo della richiesta

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

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Nessun gateway e ID di origine dati trovato durante la chiamata Get data sources (Ottieni origini dati)

Questo problema significa che il set di dati non è associato a un gateway. Quando si crea un nuovo set di dati, per ogni connessione cloud viene creata automaticamente un'origine dati senza credenziali nel gateway cloud dell'utente. Questo gateway viene usato per archiviare le credenziali per le connessioni cloud.

Dopo aver creato il set di dati, viene stabilita un'associazione automatica tra il set di dati e un gateway appropriato, che contiene le origini dati corrispondenti per tutte le connessioni. In mancanza di tale gateway o di più gateway appropriati, l'associazione automatica ha esito negativo.

Creare le origini dati locali eventualmente mancanti e associare manualmente il set di dati a un gateway usando [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (Associa al gateway).

Per individuare i gateway che possono essere associati, usare [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Individua gateway).