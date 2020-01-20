---
title: Crittografare le credenziali
description: 'Procedura dettagliata: Crittografare le credenziali per le origini dati gateway locali'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836616"
---
# <a name="encrypt-credentials"></a>Crittografare le credenziali

Quando si chiama [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Crea origine dati) o [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Aggiorna origine dati) in un **gateway enterprise locale** usando l'[API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/), i valori delle credenziali devono essere crittografati mediante la chiave pubblica del gateway.

Vedere nell'esempio di codice seguente come crittografare le credenziali in .NET.

Le credenziali fornite al metodo EncodeCredentials seguente devono essere in uno dei formati seguenti, a seconda del tipo di credenziali:

**Credenziali di base/di Windows**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Credenziali della chiave**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**Credenziali OAuth2**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Credenziali anonime**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Credenziali di crittografia**

Crittografare il valore delle credenziali usando la chiave pubblica del gateway. A versioni diverse del gateway possono corrispondere dimensioni diverse per le chiavi pubbliche.

Vedere l'esempio nel codice SDK, disponibile nel repository GitHub Power bi-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)