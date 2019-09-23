---
title: Configurare le credenziali a livello di codice per Power BI
description: Come configurare le credenziali a livello di codice per Power BI per l'automazione
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: f93119a621330d673fd2cf6035e0416646bd5e6a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61380180"
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

3. Crittografare la stringa di credenziali con chiave pubblica del gateway usando l'algoritmo di crittografia RSA.

    Usare la classe helper seguente per la crittografia:

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

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
