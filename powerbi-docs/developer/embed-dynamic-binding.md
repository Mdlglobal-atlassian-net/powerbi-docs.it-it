---
title: Binding dinamico
description: Informazioni su come incorporare un report tramite il binding dinamico.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776238"
---
# <a name="dynamic-binding"></a>Binding dinamico

Il binding dinamico consente di selezionare in modo dinamico un set di dati durante l'incorporamento di un report. Il report e il set di dati non devono necessariamente trovarsi nella stessa area di lavoro. Gli utenti finali visualizzano risultati diversi, a seconda del set di dati selezionato.

Entrambe le aree di lavoro (quella contenente il report e quella contenente il set di dati) devono essere assegnate a una capacità.

L'incorporamento di un report tramite binding dinamico è costituito da due fasi:
1. Generazione di un token
2. Modifica dell'oggetto di configurazione

## <a name="generating-a-token"></a>Generazione di un token
Per generare un token, usare l'[API per la generazione di un token di incorporamento per più elementi](embed-sample-for-customers.md#multiEmbedToken).

Il binding dinamico è supportato per entrambi gli scenari di incorporamento, ovvero per l'*incorporamento per l'organizzazione* e per l'*incorporamento per i clienti*.

| Solution                   | Token                               | Requisiti                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Incorporamento per l'organizzazione* | Token di accesso per utenti di Power BI     | L'utente di cui viene usato il token di Azure AD deve avere le autorizzazioni appropriate per tutti gli artefatti.                                                                    |
| *Incorporamento per i clienti*    | Token di accesso per utenti non di Power BI | Deve includere le autorizzazioni sia per il report che per il set di dati associato in modo dinamico. Usare la nuova API per generare un token di incorporamento che supporta più artefatti. |

## <a name="adjusting-the-config-object"></a>Modifica dell'oggetto di configurazione
Aggiungere `datasetBinding` all'oggetto di configurazione. Usare l'esempio nella parte inferiore della pagina come riferimento.

Se non si ha familiarità con l'incorporamento in Power BI, per informazioni su come incorporare contenuto di Power BI vedere queste esercitazioni:
* [Incorporare contenuto di Power BI in un'applicazione per i clienti](embed-sample-for-customers.md)
* [Esercitazione: Incorporare contenuto di Power BI in un'applicazione per l'organizzazione](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Esempio
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```