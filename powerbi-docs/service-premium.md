---
title: 'Power BI Premium: di cosa si tratta?'
description: Power BI Premium offre una capacità dedicata all'organizzazione o al team, con prestazioni più affidabili e volumi di dati superiori, senza richiedere l'acquisto di licenze per ogni utente.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2018
ms.author: mblythe
LocalizationGroup: Premium
ms.openlocfilehash: 81a03c7728d92bcc78dba9a02cbe4c45f582fd3d
ms.sourcegitcommit: 8b2ae15eb0e39cce29f3bf466ab7768f3f7c7815
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40257016"
---
# <a name="power-bi-premium---what-is-it"></a>Power BI Premium: di cosa si tratta?
Power BI Premium offre risorse dedicate per l'esecuzione del servizio Power BI per l'organizzazione o il team, garantendo prestazioni più affidabili e con il supporto di volumi di dati superiori. Premium consente anche la distribuzione generalizzata dei contenuti senza dover acquistare licenze per utente per i visualizzatori.

È possibile sfruttare Power BI Premium assegnando alle aree di lavoro una capacità Premium. La *capacità Premium* è una risorsa dedicata per l'organizzazione. Le aree di lavoro a cui non è stata assegnata una capacità Premium, disporranno di una capacità condivisa.

Con la *capacità condivisa* i carichi di lavoro vengono eseguiti nelle risorse di calcolo condivise da altri clienti. La capacità condivisa presenta più limiti sui singoli utenti in modo da garantire la qualità dell'esperienza per tutti gli utenti.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Livelli di capacità
In Power BI ci sono due tipi di pacchetti di capacità. La capacità condivisa e la capacità Power BI Premium. Di seguito vengono illustrate le differenze tra queste tipologie.

|  | Capacità condivisa | Capacità Power BI Premium |
| --- | --- | --- |
| **Frequenza di aggiornamento** |8/giorno |48/giorno |
| **Isolamento con hardware dedicato** |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile") |
| **Distribuzione aziendale per** ***tutti gli utenti*** | | |
| App e condivisione |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile")<sup>1</sup> |
| API e controlli incorporati |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile")<sup>2</sup> |
| **Pubblicazione dei report di Power BI locali** |![](media/service-premium/not-available.png "Non disponibile") |![](media/service-premium/available.png "Disponibile") |

*<sup>1</sup> Per altre informazioni, vedere [Differenze tra la versione gratuita e la versione Pro di Power BI](service-free-vs-pro.md).*  
*<sup>2</sup> Miglioramenti in arrivo per Power BI Premium post GA.*

### <a name="premium-capacity"></a>Capacità Premium
Per iniziare a usare una capacità Power BI Premium, è necessario assegnare una capacità all'area di lavoro. Per altre informazioni su come assegnare una capacità Premium a un'area di lavoro, vedere [Manage Power BI Premium](service-admin-premium-manage.md) (Gestire Power BI Premium).

Quando un'area di lavoro dispone di capacità Premium, l'utente può sfruttare i vantaggi di Power BI Premium.

* **Aggiornamenti pianificati**: con la capacità condivisa, gli aggiornamenti pianificati per i modelli importati sono limitati a 8 volte al giorno. Il numero di aggiornamenti viene aumentato a 48 volte al giorno per i set di dati nelle aree di lavoro Premium. Non viene applicata alle impostazioni di aggiornamento pianificato della cache per DirectQuery, che sono le stesse sia per la capacità Premium che per la capacità condivisa.
* **Isolamento con hardware dedicato**: la caratteristica principale della capacità condivisa è che le prestazioni di report e dashboard potrebbero essere influenzate dalle richieste di risorse di altri carichi di lavoro nella capacità, nonostante la prevenzione. Al contrario, la capacità Premium offre prestazioni più coerenti e affidabili per i carichi di lavoro isolandola da carichi di lavoro non correlati.

Se un'app è dotata di capacità Premium, vale a dire è stata pubblicata da un'area di lavoro per le app attualmente assegnata a Premium, l'app pubblicata può essere usata da qualsiasi utente nell'organizzazione, indipendentemente dalla licenza assegnata.

### <a name="shared-capacity"></a>Capacità condivisa
Per impostazione predefinita, l'area di lavoro avrà la capacità condivisa. Ciò include l'*area di lavoro personale* con le aree di lavoro per le app. La capacità condivisa è l'esperienza generalmente usata in Power BI, in cui i carichi di lavoro vengono eseguiti nelle risorse di calcolo condivise da altri clienti.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nodi della capacità Premium
Power BI Premium è disponibile nelle configurazioni del nodo con diverse capacità v-core. Per altre informazioni sulle offerte e i prezzi delle SKU specifiche, vedere [Prezzi di Power BI](https://powerbi.microsoft.com/pricing/). È disponibile un [calcolatore dei costi](https://powerbi.microsoft.com/calculator/). Per informazioni sulla pianificazione della capacità analitica incorporata, vedere [Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendali di Power BI)

* I nodi P possono essere usati per le distribuzioni di servizi o incorporate.
* I nodi EM possono essere usati solo per le distribuzioni incorporate. I nodi EM non hanno accesso alle funzionalità Premium, ad esempio la condivisione di app per gli utenti che non hanno una licenza di Power BI Pro.

>[!NOTE]
>I collegamenti disponibili in questa tabella funzionano correttamente solo per gli utenti che sono amministratori globali di Office 365. Gli altri utenti ricevono un errore di tipo 404. 

| Nodo della capacità | Totale vCore<br/>*(Back-end + front-end)* | vCore back-end | vCore front-end | Limiti di connessione dinamica/DirectQuery | Rendering massimo della pagina all'ora di punta | Disponibilità |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mensile)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 vCore |0.5 v-core, 2,5 GB RAM |0,5 v-core |3,75 al secondo |150-300 |Disponibile |
| [EM2 (mensile)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 v-core |1 v-core, 5 GB di RAM |1 vCore |7,5 al secondo |301-600 |Disponibile |
| [EM3 (mensile)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 v-core |2 v-core, 10 GB di RAM |2 v-core | |601-1.200 |Disponibile |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-core |4 v-core, 25 GB di RAM |4 v-core |30 al secondo |1.201-2.400 |Disponibile (è disponibile anche l'opzione [mensile](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-core |8 v-core, 50 GB di RAM |8 v-core |60 al secondo |2.401-4.800 |Disponibile |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-core |16 v-core, 100 GB di RAM |16 v-core |120 al secondo |4.801-9600 |Disponibile |

* I vCore di front-end sono responsabili della gestione dei documenti relativi a servizio Web, dashboard e report, della gestione dei diritti di accesso, della pianificazione, delle API, dei caricamenti e dei download e in genere di tutto ciò che riguarda l'esperienza utente.
* I vCore di back-end sono responsabili del lavoro più oneroso: elaborazione delle query, gestione della cache, esecuzione dei server R, aggiornamento dei dati, elaborazione del linguaggio naturale, feed in tempo reale e rendering lato server di report e immagini. Con i vCore di back-end viene riservata anche una certa quantità di memoria. Le disponibilità di uno spazio in memoria sufficiente è particolarmente importante quando si usano modelli di dati di grandi dimensioni o un numero elevato di set di dati attivi.

## <a name="power-bi-report-server"></a>Server di report Power BI
Power BI Premium include il diritto di esecuzione del server di report di Power BI in locale. Per altre informazioni vedere [Introduzione al server di report di Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Passaggi successivi
[Power BI Premium FAQ](service-premium-faq.md) (Domande frequenti su Power BI Premium)  
[Power BI Premium release notes](service-premium-release-notes.md) (Note sulla versione di Power BI Premium)  
[How to purchase Power BI Premium](service-admin-premium-purchase.md) (Come acquistare Power BI Premium)  
[Managing Power BI Premium](service-admin-premium-manage.md) (Gestione di Power BI Premium)  
[Microsoft Power BI Premium whitepaper](https://aka.ms/pbipremiumwhitepaper) (White paper su Microsoft Power BI Premium)  
[Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendale di Power BI)  
[Amministrazione di Power BI nell'organizzazione](service-admin-administering-power-bi-in-your-organization.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

