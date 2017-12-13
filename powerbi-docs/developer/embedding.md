---
title: Incorporamento con Power BI
description: Power BI offre API per l'incorporamento di dashboard e report nelle applicazioni.
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
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/30/17
ms.author: mihart
ms.openlocfilehash: 38860e6535f44e8831c62c045e7c5d0e130c35aa
ms.sourcegitcommit: 910258a5ad8b6861e81ae02c57286db221c37375
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="embedding-with-power-bi"></a>Incorporamento con Power BI
Power BI offre API per l'incorporamento di dashboard e report nelle applicazioni. Le API di Power BI offrono un set coerente di funzionalità e l'accesso alle funzionalità più recenti di Power BI, ad esempio dashboard, gateway e aree di lavoro per le app, quando si incorpora il contenuto.

## <a name="a-single-api"></a>Una singola API
Esistono due scenari principali quando si incorpora il contenuto di Power BI.  Incorporamento per gli utenti dell'organizzazione (che dispongono di licenze per Power BI) e incorporamento per utenti e clienti senza che venga loro richiesta una licenza di Power BI. Le API REST di Power BI consentono entrambi gli scenari. 

Per i clienti e gli utenti senza licenza di Power BI, sarà possibile incorporare dashboard e report nell'applicazione personalizzata usando la stessa API per l'organizzazione o per i clienti. I clienti visualizzeranno i dati gestiti dall'applicazione. Gli utenti di Power BI dell'organizzazione potranno invece usufruire di opzioni aggiuntive per visualizzare *i propri dati* direttamente in Power BI o nel contesto dell'applicazione incorporata. È possibile usufruire delle API REST e JavaScript per soddisfare le proprie esigenze di incorporamento.

Per visualizzare un esempio di come funziona l'incorporamento, vedere l'[esempio di incorporamento di JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporamento per l'organizzazione
L'incorporamento per l'organizzazione consente di estendere il servizio Power BI. A questo scopo, gli utenti dell'applicazione dovranno eseguire l'accesso al servizio Power BI quando vogliono visualizzare il contenuto. Quando un utente dell'organizzazione esegue l'accesso, potrà accedere solo ai dashboard e ai report di cui è proprietario o che sono stati condivisi con tale utente nel servizio Power BI. 

*Gli esempi di incorporamento per l'organizzazione includono l'applicazione Web interna, la web part di SharePoint Online e l'integrazione di Microsoft Teams.*

Per l'incorporamento per l'organizzazione, vedere quanto segue:

* [Integrare un dashboard in un'app](integrate-dashboard.md)
* [Integrare un riquadro in un'app](integrate-tile.md)
* [Integrare un report in un'app](integrate-report.md)

Le funzionalità self-service, quali la modifica, il salvataggio e altro ancora, sono disponibili tramite le [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) durante l'incorporamento per gli utenti di Power BI.

## <a name="embedding-for-your-customers"></a>Incorporamento per i clienti
L'incorporamento per i clienti offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Non è necessario che i clienti abbiano informazioni su Power BI. Per creare un'applicazione incorporata, è necessario almeno un account Power BI Pro. Tale account verrà usato come account master per l'applicazione. Basta immaginarlo come un account del proxy. L'account Power BI Pro consente anche di generare i token di incorporamento che forniscono l'accesso a dashboard e report di proprietà o gestiti dall'applicazione nel servizio Power BI. 

*Un esempio di incorporamento per i clienti è costituito da un'applicazione ISV venduta ad altre aziende.*

![Flusso di incorporamento per l'incorporamento per i clienti](media/embedding/powerbi-embed-flow.png)

Per incorporare dashboard, report e riquadri, usare le stesse API usate per l'incorporamento per l'organizzazione.

> [!IMPORTANT]
> Mentre l'incorporamento ha una dipendenza dal servizio Power BI, non esiste alcuna dipendenza da Power BI per i clienti. Gli utenti non dovranno eseguire l'iscrizione a Power BI per visualizzare il contenuto incorporato nell'applicazione.
> 
> 

Quando si è pronti per passare alla produzione, all'area di lavoro per le app viene assegnata una capacità. Power BI Embedded in Microsoft Azure offre capacità da usare con le applicazioni.

Per informazioni dettagliate su come incorporare, vedere [Come incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md).

Se si usa il servizio Raccolta di aree di lavoro di Power BI in Azure, vedere [Eseguire la migrazione di contenuto dal servizio Raccolta di aree di lavoro di Power BI](migrate-from-powerbi-embedded.md) per ottenere informazioni sulla procedura di migrazione del contenuto.

## <a name="next-steps"></a>Passaggi successivi
[Come incorporare i dashboard, i report e i riquadri di Power BI](embedding-content.md)  
[Come eseguire la migrazione del contenuto della raccolta di aree di lavoro di Power BI Embedded in Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium: di cosa si tratta?](../service-premium.md)  
[Archivio GIT API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Archivio GIT C# di Power BI](https://github.com/Microsoft/PowerBI-CSharp)  
[Esempio di incorporamento JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Embedded analytics capacity planning whitepaper](https://aka.ms/pbiewhitepaper) (White paper sulla pianificazione della capacità di analisi incorporata)  
[White paper su Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

