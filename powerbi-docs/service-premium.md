---
title: Che cos'è Microsoft Power BI Premium?
description: Power BI Premium offre una capacità dedicata all'organizzazione o al team, con prestazioni più affidabili e volumi di dati superiori, senza richiedere l'acquisto di licenze per ogni utente.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 0723ddb57131fed499d4ac86666b3cd6d8bcbd2d
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271809"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Che cos'è Microsoft Power BI Premium?

Microsoft Power BI Premium offre risorse dedicate per l'esecuzione del servizio Power BI per l'organizzazione o il team, garantendo prestazioni più affidabili e con il supporto di volumi di dati superiori. Premium consente anche la distribuzione generalizzata dei contenuti senza dover acquistare licenze Pro per utente per i visualizzatori.

È possibile sfruttare Power BI Premium assegnando alle aree di lavoro una *capacità Premium*. La capacità Premium è una risorsa dedicata per l'organizzazione. Le aree di lavoro a cui non viene assegnata una capacità Premium hanno una *capacità condivisa*. Con la capacità condivisa i carichi di lavoro vengono eseguiti in risorse di calcolo condivise da altri clienti. 

Nella capacità condivisa, Power BI pone più limiti sui singoli utenti in modo da garantire la qualità dell'esperienza per tutti gli utenti. Per impostazione predefinita, l'area di lavoro ha una capacità condivisa, incluse l'*Area di lavoro personale* e le Aree di lavoro per le app.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Livelli di capacità

Ecco un riepilogo delle differenze tra la capacità condivisa e la capacità Premium.

|  | Capacità condivisa | Capacità Power BI Premium |
| --- | --- | --- |
| **Frequenza di aggiornamento** |8/giorno |48/giorno |
| **Isolamento con hardware dedicato** |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile") |
| **Distribuzione aziendale per** ***tutti gli utenti*** | | |
| App e condivisione |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile")<sup>1</sup> |
| API e controlli incorporati |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile")<sup>2</sup> |
| **Pubblicazione dei report di Power BI locali** |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile") |

*<sup>1</sup> Per altre informazioni, vedere [Funzionalità in base al tipo di licenza](service-features-license-type.md).*  
*<sup>2</sup> Miglioramenti in arrivo per Power BI Premium.*

Per iniziare a usare una capacità Power BI Premium, assegnare una capacità all'area di lavoro. Quando un'area di lavoro è associata alla capacità Premium, si ottengono:

* **Aggiornamenti pianificati**: con la capacità condivisa, gli aggiornamenti pianificati per i set di dati dei modelli importati sono limitati a otto volte al giorno. Per i set di dati delle aree di lavoro Premium, è possibile pianificare aggiornamenti fino a 48 volte al giorno. Gli aggiornamenti della cache DirectQuery sono ancora limitati a otto volte al giorno nella capacità Premium.

* **Isolamento con hardware dedicato**: nella capacità condivisa, le richieste di risorse di altri carichi di lavoro possono influire sulle prestazioni di report e dashboard. Al contrario, la capacità Premium offre prestazioni più coerenti e affidabili per i carichi di lavoro isolandoli da carichi di lavoro non correlati.

Se un'app è dotata di capacità Premium, vale a dire è stata pubblicata da un'area di lavoro per le app attualmente assegnata alla capacità Premium, l'app pubblicata può essere usata da qualsiasi utente nell'organizzazione, indipendentemente dalla licenza assegnata.

Per altre informazioni sull'assegnazione delle aree di lavoro alla capacità Premium, vedere [Gestire Power BI Premium](service-admin-premium-manage.md).

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nodi della capacità Premium

Power BI Premium è disponibile nelle configurazioni del nodo con diverse capacità v-core. Per altre informazioni sulle offerte e i prezzi delle SKU specifiche, vedere [Prezzi di Power BI](https://powerbi.microsoft.com/pricing/). È disponibile un [calcolatore dei costi](https://powerbi.microsoft.com/calculator/). Per informazioni sulla pianificazione della capacità analitica incorporata, vedere [Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendali di Power BI)

* I nodi P possono essere usati per le distribuzioni di servizi o incorporate.

* I nodi EM possono essere usati solo per le distribuzioni incorporate. I nodi EM non hanno accesso alle funzionalità Premium, ad esempio la condivisione di app per gli utenti che non hanno una licenza di Power BI Pro.

>[!NOTE]
>I collegamenti disponibili in questa tabella funzionano correttamente solo per gli utenti che sono amministratori globali di Office 365. Gli altri utenti ricevono un errore di tipo 404.

| Nodo della capacità | Totale vCore<br/>*(Back-end + front-end)* | vCore back-end | vCore front-end | Limiti di connessione dinamica/DirectQuery | Rendering massimo della pagina all'ora di punta | Disponibilità |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mensile)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 vCore |0,5 v-core, 2.5 GB di RAM |0,5 v-core |3,75 al secondo |150-300 |Disponibile |
| [EM2 (mensile)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 v-core |1 v-core, 5 GB di RAM |1 vCore |7,5 al secondo |301-600 |Disponibile |
| [EM3 (mensile)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 v-core |2 v-core, 10 GB di RAM |2 v-core | |601-1.200 |Disponibile |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-core |4 v-core, 25 GB di RAM |4 v-core |30 al secondo |1.201-2.400 |Disponibile (è disponibile anche l'opzione [mensile](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-core |8 v-core, 50 GB di RAM |8 v-core |60 al secondo |2.401-4.800 |Disponibile |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-core |16 v-core, 100 GB di RAM |16 v-core |120 al secondo |4.801-9600 |Disponibile |

* I vCore di front-end sono responsabili della gestione dei documenti relativi a servizio Web, dashboard e report, della gestione dei diritti di accesso, della pianificazione, delle API, dei caricamenti e dei download e in genere di tutto ciò che riguarda l'esperienza utente.

* I vCore di back-end sono responsabili del lavoro più oneroso: elaborazione delle query, gestione della cache, esecuzione dei server R, aggiornamento dei dati, elaborazione del linguaggio naturale, feed in tempo reale e rendering lato server di report e immagini. Con i vCore di back-end viene riservata anche una certa quantità di memoria. Le disponibilità di uno spazio in memoria sufficiente è particolarmente importante quando si usano modelli di dati di grandi dimensioni o un numero elevato di set di dati attivi.

## <a name="power-bi-report-server"></a>Server di report Power BI
Power BI Premium include anche la capacità di eseguire il Server di report di Power BI in locale nell'organizzazione. Per altre informazioni, vedere [Introduzione a Server di report di Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Passaggi successivi
[Power BI Premium FAQ](service-premium-faq.md) (Domande frequenti su Power BI Premium)  
[Power BI Premium release notes](service-premium-release-notes.md) (Note sulla versione di Power BI Premium)  
[How to purchase Power BI Premium](service-admin-premium-purchase.md) (Come acquistare Power BI Premium)  
[Managing Power BI Premium](service-admin-premium-manage.md) (Gestione di Power BI Premium)  
[Microsoft Power BI Premium whitepaper](https://aka.ms/pbipremiumwhitepaper) (White paper su Microsoft Power BI Premium)  
[Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendale di Power BI)  
[Amministrazione di Power BI nell'organizzazione](service-admin-administering-power-bi-in-your-organization.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
