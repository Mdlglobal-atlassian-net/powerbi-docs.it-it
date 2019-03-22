---
title: Che cos'è Microsoft Power BI Premium?
description: Power BI Premium offre una capacità dedicata all'organizzazione o al team, con prestazioni più affidabili e volumi di dati superiori, senza richiedere l'acquisto di licenze per ogni utente.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f327cb95c10756f079778d20e62cba4871b95c02
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964940"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Che cos'è Microsoft Power BI Premium?

> [!NOTE]
> Questo articolo è in corso di aggiornamento per descrivere le nuove funzionalità, offrire più dettagli e migliorare la leggibilità. Per le informazioni più recenti, vedere [Distribuzione e gestione delle capacità Power BI Premium](whitepaper-powerbi-premium-deployment.md).

Power BI Premium offre risorse dedicate per l'esecuzione del servizio Power BI per l'organizzazione. garantendo prestazioni più affidabili e con il supporto di volumi di dati superiori. Premium consente anche la distribuzione generalizzata dei contenuti senza dover acquistare licenze Pro per utente singolo per i consumer del contenuto.  

## <a name="premium-capacity-and-shared-capacity"></a>Capacità Premium e capacità condivisa

È possibile sfruttare Power BI Premium assegnando alle aree di lavoro una *capacità Premium*. La capacità Premium è una risorsa dedicata per l'organizzazione. Le aree di lavoro a cui non viene assegnata una capacità Premium hanno una *capacità condivisa*. Con la capacità condivisa i carichi di lavoro vengono eseguiti in risorse di calcolo condivise da altri clienti.

L'immagine seguente visualizza la relazione tra capacità Premium e capacità condivisa, con l'organizzazione Contoso come esempio.

![Illustrazione di Power BI Premium](media/service-premium/premium-chart.png)

| Area | Descrizione |
| --- | --- |
| **(1)** Elementi all'interno di una capacità Premium | <ul><li>L'accesso alle aree di lavoro delle app, come membri o amministratori, e la pubblicazione di app richiedono una licenza di Power BI Pro.<li>Per condividere un'app è necessaria una licenza Pro, per usarla invece non occorre.<li>Tutti i destinatari del dashboard, indipendentemente dalla licenza loro assegnata, possono impostare gli avvisi dati.<li>Le API REST per l'incorporamento usano un account del servizio con una licenza Pro, invece di un account utente.</ul> |
| **(2)** Area di lavoro personale nella capacità condivisa | <ul><li>Sia per condividere che per usare un'app è necessaria una licenza Pro.</ul> |
| **(3)** Aree di lavoro delle app nella capacità condivisa | <ul><li>L'uso di qualsiasi app richiede una licenza Pro.</ul>|
| | |

Nella capacità condivisa, Power BI pone più limiti sui singoli utenti in modo da garantire la qualità dell'esperienza per tutti gli utenti. Per impostazione predefinita, l'area di lavoro ha una capacità condivisa, incluse l'*Area di lavoro personale* e le Aree di lavoro per le app.

La tabella seguente offre un riepilogo delle differenze tra la capacità condivisa e la capacità Premium:

|  | Capacità condivisa | Capacità Power BI Premium |
| --- | --- | --- |
| **Frequenza di aggiornamento** |8/giorno |48/giorno |
| Isolamento con hardware dedicato |![Non disponibile](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Distribuzione aziendale a *tutti gli utenti* | | |
| App e condivisione |![Non disponibile](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| API e controlli incorporati |![Non disponibile](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Pubblica report di Power BI locali |![Non disponibile](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Miglioramenti futuri in arrivo per Power BI Premium.



### <a name="premium-capacity-nodes"></a>Nodi della capacità Premium

Power BI Premium è disponibile nelle configurazioni del nodo con diverse capacità v-core. Per altre informazioni sulle offerte e i prezzi delle SKU specifiche, vedere [Prezzi di Power BI](https://powerbi.microsoft.com/pricing/). È disponibile un [calcolatore dei costi](https://powerbi.microsoft.com/calculator/). Per informazioni sulla pianificazione della capacità analitica incorporata, vedere [Planning a Power BI Enterprise Deployment whitepaper](https://aka.ms/pbienterprisedeploy) (White paper sulla pianificazione della distribuzione aziendali di Power BI) Per riassumere:

* I nodi P possono essere usati per le distribuzioni di servizi o incorporate.

* I nodi EM possono essere usati solo per le distribuzioni incorporate. I nodi EM non hanno accesso alle funzionalità Premium, ad esempio la condivisione di app per gli utenti che non hanno una licenza di Power BI Pro.

| Nodo della capacità | Totale vCore<br/>*(Back-end + front-end)*  | vCore back-end <sup>[1](#fn1)</sup> | vCore front-end <sup>[2](#fn2)</sup> | Limiti di connessione dinamica/DirectQuery | Max aggiornamenti simultanei |
| --- | --- | --- | --- | --- | --- |
| EM1 (mensile) |1 vCore |0,5 v-core, 2.5 GB di RAM |0,5 v-core |3,75 al secondo |  1 |
| EM2 (mensile) |2 v-core |1 v-core, 5 GB di RAM |1 vCore |7,5 al secondo |  2 |
| EM3 (mensile) |4 v-core |2 v-core, 10 GB di RAM |2 v-core | 15 | 3 |
| P1 |8 v-core |4 v-core, 25 GB di RAM |4 v-core |30 al secondo | 6 |
| P2 |16 v-core |8 v-core, 50 GB di RAM |8 v-core |60 al secondo | 12 |
| P3 |32 v-core |16 v-core, 100 GB di RAM |16 v-core |120 al secondo | 24 |
| | | | | | |

<a name="fn1">1</a>: i vCore front-end sono responsabili per il servizio Web. Ad esempio, gestione dei documenti per dashboard e report, gestione dei diritti di accesso, pianificazione, API, caricamenti e download e in genere tutto ciò che riguarda l'esperienza utente. 

<a name="fn2">2</a>: I vCore back-end sono responsabili del lavoro più oneroso, come elaborazione delle query, gestione della cache, esecuzione dei server R, aggiornamento dei dati, elaborazione del linguaggio naturale, feed in tempo reale e rendering lato server di report e immagini. Con i vCore di back-end viene riservata anche una certa quantità di memoria. Le disponibilità di uno spazio in memoria sufficiente è particolarmente importante quando si usano modelli di dati di grandi dimensioni o un numero elevato di set di dati attivi.

## <a name="workloads-in-premium-capacity"></a>Carichi di lavoro nella capacità Premium

Per impostazione predefinita, le capacità Power BI Premium e Power BI Embedded supportano solo il carico di lavoro associato all'esecuzione di query di Power BI nel cloud. Premium supporta anche carichi di lavoro aggiuntivi per **intelligenza artificiale**, **flussi di dati** e **report impaginati**. Per consentire a questi carichi di lavoro di usare le risorse della capacità, è necessario abilitarli nel portale di amministrazione di Power BI o tramite l'API REST di Power BI. Ogni carico di lavoro ha impostazioni predefinite per la quantità massima di memoria che ogni carico di lavoro può utilizzare. È tuttavia possibile configurare impostazioni di utilizzo della memoria diverse per determinare quanto i carichi di lavoro interferiscono tra loro e come utilizzano le risorse della capacità. Per altre informazioni, vedere [Configurare i carichi di lavoro](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Server di report di Power BI

Power BI Premium include anche la capacità di eseguire il Server di report di Power BI in locale nell'organizzazione. Per altre informazioni, vedere [Introduzione a Server di report di Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Passaggi successivi

[Distribuzione e gestione delle capacità Power BI Premium](whitepaper-powerbi-premium-deployment.md)   
[Come acquistare Power BI Premium](service-admin-premium-purchase.md)   
[Power BI Premium FAQ](service-premium-faq.md) (Domande frequenti su Power BI Premium)   



Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
