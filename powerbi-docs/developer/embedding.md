---
title: Analisi incorporata con Power BI
description: Power BI offre API per l'uso dell'analisi incorporata per dashboard e report nelle applicazioni. Informazioni sull'incorporamento con Power BI, sia in ambiente PaaS che in ambiente SaaS, tramite software di analisi incorporata, strumenti di analisi incorporata o strumenti di business intelligence incorporata.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: d2e52ff986bb2bba0caf5168c5038bb55011144a
ms.sourcegitcommit: c799941c8169cd5b6b6d63f609db66ab2af93891
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70391520"
---
# <a name="embedded-analytics-with-power-bi"></a>Analisi incorporata con Power BI

Il servizio Power BI (SaaS) e il servizio Power BI Embedded in Azure (PaaS) offrono API per l'incorporamento di dashboard e report. Quando si incorpora del contenuto, è possibile accedere alle funzionalità di Power BI più recenti, ad esempio dashboard, gateway e aree di lavoro per le app.

È possibile usare lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup) per iniziare rapidamente e scaricare un'applicazione di esempio.

Scegliere la soluzione adatta alle proprie esigenze:

* L'[incorporamento per l'organizzazione](embedding.md#embedding-for-your-organization) consente di estendere il servizio Power BI. A questo scopo, eseguire la soluzione di [incorporamento per l'organizzazione](https://aka.ms/embedsetup/UserOwnsData).
* L'[incorporamento per i clienti](embedding.md#embedding-for-your-customers) consente di incorporare dashboard e report per gli utenti che non hanno un account Power BI. Per eseguirlo, implementare la soluzione di [incorporamento per i clienti](https://aka.ms/embedsetup/AppOwnsData).

![Esempio di Power BI Embedded](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Usare le API

Esistono due scenari principali per incorporare il contenuto di Power BI:
- Incorporamento per gli utenti dell'organizzazione (che hanno una licenza di Power BI). 
 
- Incorporamento per utenti e clienti senza licenze di Power BI. 

L'[API REST di Power BI](https://docs.microsoft.com/rest/api/power-bi/) consente entrambi gli scenari.

Per i clienti e gli utenti senza licenza di Power BI, sarà possibile incorporare dashboard e report nell'applicazione personalizzata usando la stessa API per l'organizzazione o per i clienti. I clienti visualizzano i dati gestiti dall'applicazione. Gli utenti di Power BI dell'organizzazione hanno anche opzioni aggiuntive per visualizzare *i propri dati* direttamente in Power BI o nel contesto dell'applicazione incorporata. È possibile usufruire delle API REST e JavaScript per soddisfare le proprie esigenze di incorporamento.

Per capire come funziona l'incorporamento, vedere l'[esempio di incorporamento di JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporamento per l'organizzazione

L'**incorporamento per l'organizzazione** consente di estendere il servizio Power BI. Questo tipo di incorporamento richiede che gli utenti dell'applicazione eseguano l'accesso al servizio Power BI per visualizzare il contenuto. Quando un utente dell'organizzazione esegue l'accesso, potrà accedere solo ai dashboard e ai report di cui è proprietario o che sono stati condivisi con l'utente nel servizio Power BI.

Gli esempi di incorporamento per l'organizzazione includono applicazioni interne come [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), l'[integrazione di Microsoft Teams (che richiede diritti di amministratore)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) e [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Per eseguire l'incorporamento per l'organizzazione, vedere [Esercitazione: Incorporare contenuto di Power BI in un'applicazione per l'organizzazione](embed-sample-for-your-organization.md).

Le funzionalità self-service, quali la modifica, il salvataggio e altro ancora, sono disponibili tramite le [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) durante l'incorporamento per gli utenti di Power BI.

È possibile usare lo [strumento di installazione dell'incorporamento](https://aka.ms/embedsetup/UserOwnsData) per iniziare scaricando un'applicazione di esempio che facilita l'esecuzione dell'integrazione di un report per l'organizzazione.

## <a name="embedding-for-your-customers"></a>Incorporamento per i clienti

L'**incorporamento per i clienti** consente di incorporare dashboard e report per gli utenti che non hanno un account Power BI. Questo tipo di incorporamento è noto anche come *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) è un servizio di **Microsoft Azure** che consente ai fornitori di software indipendenti (ISV) e agli sviluppatori di incorporare rapidamente oggetti visivi, report e dashboard in un'applicazione. Questo tipo di incorporamento avviene tramite un modello a consumo orario e basato sulla capacità.

![Flusso di incorporamento per l'incorporamento per i clienti](media/embedding/powerbi-embed-flow.png)

Power BI Embedded offre vantaggi ai fornitori di software indipendenti, agli sviluppatori e ai clienti. Ad esempio un fornitore di software indipendente può iniziare a creare gratuitamente oggetti visivi con Power BI Desktop. Riducendo il lavoro di sviluppo di elementi visivi e analisi, i fornitori di software indipendenti possono ottenere un time to market più rapido e distinguersi dalla concorrenza grazie all'offerta di esperienze di dati differenziate. Possono anche decidere di addebitare un costo per il valore aggiunto creato con le analisi incorporate.

Con Power BI Embedded non è necessario che i clienti abbiano informazioni su Power BI. È possibile usare due metodi diversi per creare un'applicazione incorporata:
- Un account Power BI Pro 
- Entità servizio 

L'account Power BI Pro viene usato come account master per l'applicazione, ovvero come un account proxy. Questo account consente di generare i token di incorporamento che offrono accesso ai dashboard e ai report di Power BI dell'applicazione.

L'[entità servizio](embed-service-principal.md) può incorporare il contenuto di Power BI in un'applicazione con un token **solo app**. Consente anche di generare i token di incorporamento che offrono accesso ai dashboard e ai report di Power BI dell'applicazione.

Gli sviluppatori che usano Power BI Embedded possono concentrarsi sulla funzionalità principale dell'applicazione anziché dedicarsi allo sviluppo di oggetti visivi e analisi. Possono soddisfare rapidamente le richieste di report e dashboard dei clienti e incorporare facilmente questi elementi con API e SDK completamente documentati. Abilitando l'esplorazione dei dati semplificata nelle app, gli ISV consentono ai clienti di prendere decisioni rapide, basate sui dati nel contesto appropriato e da qualsiasi dispositivo.

> [!IMPORTANT]
> Mentre l'incorporamento richiede il servizio Power BI, i clienti non devono necessariamente avere un account Power BI per visualizzare il contenuto incorporato dell'applicazione. 

Quando si è pronti per passare alla produzione, l'area di lavoro per le app deve essere assegnata a una capacità dedicata. Power BI Embedded in Microsoft Azure offre [capacità dedicate](azure-pbie-create-capacity.md) da usare con le applicazioni.

Per informazioni dettagliate sull'incorporamento, vedere [Come incorporare il contenuto di Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Passaggi successivi

È ora possibile provare a incorporare contenuto di Power BI in un'applicazione o provare a incorporare contenuto di Power BI per i clienti.

> [!div class="nextstepaction"]
> [Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Che cos'è Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Incorporamento per i clienti](embed-sample-for-customers.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
