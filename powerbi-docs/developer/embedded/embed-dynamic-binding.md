---
title: Connettere un report a un set di dati tramite binding dinamico
description: Informazioni su come incorporare un report tramite il binding dinamico.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: e2c59ba84700aaf83c4cc9d16d009696c42dfc54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114590"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Connettere un report a un set di dati tramite binding dinamico 

Quando un report è connesso a un set di dati è possibile usare il binding dinamico. La connessione tra il report e il set di dati è nota come *binding*. Quando il binding viene determinato al momento dell'incorporamento, anziché essere predeterminato in precedenza, è detto binding dinamico.

Quando si incorpora un report di Power BI tramite *binding dinamico*, è possibile connettere lo stesso report a set di dati diversi a seconda delle credenziali dell'utente.

Questo significa che è possibile usare un report per visualizzare informazioni diverse, a seconda del set di dati a cui è connesso. Ad esempio, un report che mostra i valori delle vendite al dettaglio può essere connesso a set di dati diversi del rivenditore e produrre risultati diversi a seconda del set di dati del rivenditore a cui è connesso.

Il report e il set di dati non devono necessariamente trovarsi nella stessa area di lavoro. Entrambe le aree di lavoro (quella contenente il report e quella contenente il set di dati) devono essere assegnate a una [capacità](azure-pbie-create-capacity.md).

Come parte del processo di incorporamento, assicurarsi di *generare un token con autorizzazioni sufficienti* e di *adattare l'oggetto di configurazione*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Generazione di un token con autorizzazioni sufficienti

Il binding dinamico è supportato sia per l'*incorporamento per l'organizzazione* che per l'*incorporamento per i clienti*. Nella tabella seguente vengono descritte le considerazioni per ogni scenario.

|Scenario  |Proprietà dei dati  |token  |Requisiti  |
|---------|---------|---------|---------|
|*Incorporamento per l'organizzazione*    |I dati sono di proprietà dell'utente         |Token di accesso per utenti di Power BI         |L'utente di cui viene usato il token di Azure AD deve avere le autorizzazioni appropriate per tutti gli artefatti.         |
|*Incorporamento per i clienti*     |I dati sono di proprietà dell'app         |Token di accesso per utenti non di Power BI         |Deve includere le autorizzazioni sia per il report che per il set di dati associato in modo dinamico. Usare l'[API per generare un token di incorporamento per più elementi](embed-sample-for-customers.md#multiEmbedToken), per generare un token di incorporamento che supporta più artefatti.         |

## <a name="adjusting-the-config-object"></a>Modifica dell'oggetto di configurazione
Aggiungere `datasetBinding` all'oggetto di configurazione. Usare l'esempio riportato di seguito come riferimento.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Passaggi successivi

Se non si ha familiarità con l'incorporamento in Power BI, per informazioni su come incorporare contenuto di Power BI vedere queste esercitazioni:
* [Esercitazione: Incorporare contenuto di Power BI in un'applicazione per i clienti](embed-sample-for-customers.md)
* [Esercitazione: Incorporare contenuto di Power BI in un'applicazione per l'organizzazione](embed-sample-for-your-organization.md)