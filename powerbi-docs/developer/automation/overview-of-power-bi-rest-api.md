---
title: Cosa si può fare con l'API Power BI
description: Cosa si può fare con l'API Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 03/25/2019
ms.openlocfilehash: 1a74d856ad46dc6843546919aa4234dc86d2be5c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488433"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Quali operazioni possono eseguire gli sviluppatori con l'API Power BI?

L'API REST di Power BI consente di creare app che si integrano con i report, i dashboard e i riquadri di Power BI.

Con l'API REST di Power BI è possibile eseguire attività di gestione su oggetti di Power BI come i report, i set di dati e le aree di lavoro.

Ecco alcune delle operazioni che è possibile eseguire con le API di Power BI.

| **Per altre informazioni** | **Vedere questo argomento** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Incorporare report, dashboard e riquadri per utenti di Power BI e utenti esterni a Power BI. | [Come incorporare i dashboard, i report e i riquadri di Power BI](../embedded/embed-sample-for-customers.md) |
| Eseguire attività di gestione per oggetti di Power BI. | [Riferimento all'API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/) |
| Estendere un flusso di lavoro aziendale esistente per eseguire il push dei dati in un dashboard di Power BI. | [Eseguire il push dei dati in un dashboard](walkthrough-push-data.md) |
| Eseguire l'autenticazione a Power BI. | [Eseguire l'autenticazione in Power BI](../embedded/get-azuread-access-token.md) |

> [!NOTE]
> Le API Power BI fanno ancora riferimento alle aree di lavoro come gruppi. I riferimenti ai gruppi indicano che si stanno usando le aree di lavoro.

## <a name="api-developer-tools"></a>Strumenti per sviluppatori di API

| Strumento/i | Description |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [Strumento playground](https://microsoft.github.io/PowerBI-JavaScript/demo) | Un esempio d'uso completo delle API JavaScript di Power BI. Questo strumento consente di riprodurre in modo rapido vari tipi di esempi di Power BI Embedded. |  |  |
| [Wiki JavaScript di Power BI](https://github.com/Microsoft/powerbi-javascript/wiki) | Offre informazioni aggiuntive sulle API JavaScript di Power BI. |  |  |
| [Postman](https://www.getpostman.com/) | Consente di eseguire richieste, test, operazioni di debug, monitoraggio, test automatici e altro ancora. |

## <a name="push-data-into-power-bi"></a>Push dei dati in Power BI

È possibile usare l'API Power BI per [eseguire il push dei dati in un set di dati](walkthrough-push-data.md). Questa funzionalità consente di aggiungere una riga a una tabella all'interno di un set di dati. I nuovi dati vengono quindi riportati nei riquadri di un dashboard e negli oggetti visivi inclusi in un report.

![Esempio di push dei dati](media/overview-of-power-bi-rest-api/powerbi-push-data.png)

## <a name="github-repositories"></a>Repository GitHub

* [Esempi di Power BI Developer](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>Passaggi successivi

* [Eseguire il push dei dati in un set di dati](walkthrough-push-data.md)
* [Sviluppo di un oggetto visivo di Power BI](../visuals/custom-visual-develop-tutorial.md)
* [Riferimento all'API REST di Power BI](rest-api-reference.md)
* [API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
