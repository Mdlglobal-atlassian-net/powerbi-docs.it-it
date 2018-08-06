---
title: Incorporamento con Power BI
description: Power BI offre API per l'incorporamento di dashboard e report nelle applicazioni.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: overview
ms.date: 07/31/2018
ms.author: maghan
ms.openlocfilehash: 8f200450e5359124ffcc3447c68c6bd755c57896
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39359864"
---
# <a name="embedding-with-power-bi"></a>Incorporamento con Power BI
Il servizio Power BI (SaaS) e il servizio Power BI Embedded in Azure (PaaS) offrono API per l'incorporamento di dashboard e report. Questo significa che sono disponibili un set di funzionalità e l'accesso alle ultime funzionalità di Power BI, ad esempio dashboard, gateway e aree di lavoro per le app, quando si incorpora il contenuto.

È possibile usare lo [strumento esperienza di onboarding](https://aka.ms/embedsetup) per iniziare rapidamente e scaricare un'applicazione di esempio.

Scegliere la soluzione adatta alle proprie esigenze:

* L'[incorporamento per l'organizzazione](embedding.md#embedding-for-your-organization) consente di estendere il servizio Power BI. Eseguire la soluzione [Incorporare per l'organizzazione](https://aka.ms/embedsetup/UserOwnsData).
* L'[incorporamento per i clienti](embedding.md#embedding-for-your-customers) offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Eseguire la soluzione [Incorporare per i clienti](https://aka.ms/embedsetup/AppOwnsData).

![Esempio di Power BI Embedded](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>Uso delle API
Esistono due scenari principali quando si incorpora il contenuto di Power BI.  Incorporamento per gli utenti dell'organizzazione (che dispongono di licenze per Power BI) e incorporamento per utenti e clienti senza che venga loro richiesta una licenza di Power BI. Le API REST di Power BI consentono entrambi gli scenari.

Per i clienti e gli utenti senza licenza di Power BI, sarà possibile incorporare dashboard e report nell'applicazione personalizzata usando la stessa API per l'organizzazione o per i clienti. I clienti visualizzeranno i dati gestiti dall'applicazione. Gli utenti di Power BI dell'organizzazione potranno invece usufruire di opzioni aggiuntive per visualizzare *i propri dati* direttamente in Power BI o nel contesto dell'applicazione incorporata. È possibile usufruire delle API REST e JavaScript per soddisfare le proprie esigenze di incorporamento.

Per visualizzare un esempio di come funziona l'incorporamento, vedere l'[esempio di incorporamento di JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporamento per l'organizzazione
L'**incorporamento per l'organizzazione** consente di estendere il servizio Power BI. A questo scopo, gli utenti dell'applicazione dovranno eseguire l'accesso al servizio Power BI quando vogliono visualizzare il contenuto. Quando un utente dell'organizzazione esegue l'accesso, potrà accedere solo ai dashboard e ai report di cui è proprietario o che sono stati condivisi con tale utente nel servizio Power BI.

*Gli esempi di incorporamento per l'organizzazione includono l'applicazione Web interna, la web part di SharePoint Online e [l'integrazione di Microsoft Teams](https://powerbi.microsoft.com/en-us/blog/power-bi-teams-up-with-microsoft-teams/), per cui sono necessari diritti di amministratore.*

Per l'incorporamento per l'organizzazione, vedere quanto segue:

* [Integrare un report in un'app](embed-sample-for-your-organization.md)

Le funzionalità self-service, quali la modifica, il salvataggio e altro ancora, sono disponibili tramite le [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) durante l'incorporamento per gli utenti di Power BI.

È possibile usare lo [strumento esperienza di onboarding](https://aka.ms/embedsetup/UserOwnsData) per l'incorporamento per l'organizzazione per iniziare rapidamente scaricando un'applicazione di esempio che facilita l'esecuzione della procedura di integrazione di un report per l'organizzazione.

## <a name="embedding-for-your-customers"></a>Incorporamento per i clienti

L'**incorporamento per i clienti** offre la possibilità di incorporare dashboard e report per gli utenti che non hanno un account per Power BI. Non è necessario che i clienti abbiano informazioni su Power BI. Per creare un'applicazione incorporata, è necessario almeno un account Power BI Pro. Tale account verrà usato come account master per l'applicazione. Basta immaginarlo come un account del proxy. L'account Power BI Pro consente anche di generare i token di incorporamento che forniscono l'accesso a dashboard e report di proprietà o gestiti dall'applicazione nel servizio Power BI.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) offre ai fornitori di software indipendenti (ISV) e agli sviluppatori la possibilità di incorporare elementi per i clienti e aggiungere rapidamente oggetti visivi di grande effetto, report e dashboard alle applicazioni mediante un modello basato sulla capacità e quantificato su base oraria.

![Flusso di incorporamento per l'incorporamento per i clienti](media/embedding/powerbi-embed-flow.png)

Power BI Embedded offre vantaggi ai fornitori di software indipendenti, agli sviluppatori e ai clienti. Ad esempio un fornitore di software indipendente può iniziare a creare gratuitamente oggetti visivi con Power BI Desktop. I fornitori di software indipendenti possono comprimere i tempi di immissione sul mercato, riducendo il lavoro di sviluppo di elementi visivi e analisi e nel contempo distinguersi dalla concorrenza grazie all'offerta di esperienze di dati differenziate. Inoltre gli ISV possono decidere di addebitare un costo per il valore aggiunto creato con le analisi incorporate.

Gli sviluppatori possono concentrarsi sulla funzionalità principale dell'applicazione anziché dedicarsi allo sviluppo di oggetti visivi e analisi. Allo stesso tempo gli sviluppatori possono soddisfare rapidamente le richieste di report e dashboard dei clienti e incorporare facilmente questi elementi con API e SDK completamente documentati. Infine, abilitando l'esplorazione dei dati semplificata nelle proprie app, gli ISV consentono ai clienti di prendere decisioni rapide, informate e basate sui dati nel contesto appropriato e da qualsiasi dispositivo.

> [!IMPORTANT]
> Mentre l'incorporamento ha una dipendenza dal servizio Power BI, non esiste alcuna dipendenza da Power BI per i clienti. Gli utenti non dovranno eseguire l'iscrizione a Power BI per visualizzare il contenuto incorporato nell'applicazione.

Quando si è pronti a passare in produzione, è richiesta l'assegnazione dell'area di lavoro per le app a una capacità dedicata. Power BI Embedded in Microsoft Azure offre capacità dedicate da usare con le applicazioni.

Per informazioni dettagliate su come incorporare, vedere [Come incorporare i dashboard, i report e i riquadri di Power BI](embed-sample-for-customers.md).

È possibile usare lo [strumento esperienza di onboarding](https://aka.ms/embedsetup/AppOwnsData) per iniziare rapidamente scaricando un'applicazione di esempio che facilita l'esecuzione della procedura di integrazione di un report nell'applicazione.

Se si usa il servizio Raccolta di aree di lavoro di Power BI in Azure, vedere [Eseguire la migrazione di contenuto dal servizio Raccolta di aree di lavoro di Power BI](migrate-from-powerbi-embedded.md) per ottenere informazioni sulla procedura di migrazione del contenuto.

## <a name="next-steps"></a>Passaggi successivi
È ora possibile provare a incorporare contenuto di Power BI in un'applicazione o provare a incorporare contenuto di Power BI per i clienti.

> [!div class="nextstepaction"]
> [Che cos'è Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
> [Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Incorporare contenuto per i clienti](embed-sample-for-customers.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)