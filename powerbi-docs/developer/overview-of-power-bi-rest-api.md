---
title: Cosa si può fare con l'API Power BI
description: Cosa si può fare con l'API Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: d8cad602b178dd55184e00e2a318c374433b1a46
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762330"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Quali operazioni possono eseguire gli sviluppatori con l'API Power BI?

Power BI visualizza dashboard interattivi, che possono essere creati e aggiornati da molte origini dati diverse in tempo reale. Usando un qualsiasi linguaggio di programmazione che supporti chiamate REST, è possibile creare un'app in grado di integrarsi con un dashboard di Power BI in tempo reale. È anche possibile integrare riquadri e report di Power BI nelle app.

Gli sviluppatori possono anche creare le proprie visualizzazioni dei dati che possono essere usate nei dashboard e nei report interattivi.

Ecco alcune delle operazioni che è possibile eseguire con le API di Power BI.

| **Operazione da eseguire** | **Risorsa utile** |
| --- | --- |
| Incorporare dashboard, report e riquadri per gli utenti di Power BI e per gli utenti che non usano Power BI (con dati di proprietà dell'app) |[Come incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md) |
| Estendere un flusso di lavoro aziendale esistente per eseguire il push dei dati in un dashboard di Power BI. |[Eseguire il push dei dati in un dashboard](walkthrough-push-data.md) |
| Eseguire l'autenticazione a Power BI. |[Eseguire l'autenticazione a Power BI](get-azuread-access-token.md) |
| Creare un oggetto visivo personalizzato. |[Developing a Power BI custom visual](custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI) |

> [!NOTE]
> Le API di Power BI fanno ancora riferimento alle aree di lavoro per le app come gruppi. I riferimenti ai gruppi indicano che si stanno usando le aree di lavoro per le app.

## <a name="power-bi-developer-samples"></a>Esempi di Power BI Developer

Gli esempi di Power BI Developer includono gli elementi per l'incorporamento di dashboard, report e riquadri.

[Esempi di Power BI Developer](https://github.com/Microsoft/PowerBI-Developer-Samples)

* Gli esempi in **Dati dell'app** riguardano l'incorporamento per gli utenti esterni a Power BI.
* Gli esempi in **Dati dell'utente** riguardano l'incorporamento per gli utenti di Power BI.

## <a name="github-repositories"></a>Repository GitHub

* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)
* [Oggetti visivi personalizzati](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>Strumenti per sviluppatori

Di seguito sono riportati gli strumenti che è possibile usare per semplificare lo sviluppo degli elementi di Power BI.

È possibile usare lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup) per iniziare rapidamente e scaricare un'applicazione di esempio su come incorporare il contenuto di Power BI.

Scegliere la soluzione adatta alle proprie esigenze:

* L'[incorporamento per i clienti](embedding.md#embedding-for-your-customers) offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Eseguire la soluzione [Incorporare per i clienti](https://aka.ms/embedsetup/AppOwnsData).

* L'[incorporamento per l'organizzazione](embedding.md#embedding-for-your-organization) consente di estendere il servizio Power BI. Eseguire la soluzione [Incorporare per l'organizzazione](https://aka.ms/embedsetup/UserOwnsData).

Per un esempio completo dell'uso dell'API JavaScript, è possibile usare lo [strumento Playground](https://microsoft.github.io/PowerBI-JavaScript/demo), che consente di riprodurre in modo rapido esempi di Power BI Embedded di tipo diverso. È anche possibile ottenere maggiori informazioni sull'API JavaScript visitando la pagina del [wiki Power BI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

## <a name="push-data-into-power-bi"></a>Push dei dati in Power BI

È possibile usare l'API Power BI per eseguire il push dei dati in un set di dati. Questa funzionalità consente di aggiungere una riga a una tabella all'interno di un set di dati. I nuovi dati possono quindi essere riflessi nei riquadri in un dashboard e all'interno di oggetti visivi in un report.

![Esempio di push dei dati](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Passaggi successivi

[Eseguire il push dei dati in un set di dati](walkthrough-push-data.md)  
[Developing a Power BI custom visual](custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI)  
[Riferimento all'API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
