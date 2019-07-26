---
title: Indicazioni per la distribuzione di un gateway dati per Power BI
description: Procedure consigliate e considerazioni per la distribuzione di un gateway per Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271715"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Indicazioni per la distribuzione di un gateway dati per Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Questo articolo contiene indicazioni e considerazioni per la distribuzione di un gateway dati per Power BI nell'ambiente di rete.

Per informazioni su come scaricare, installare, configurare e gestire il gateway dati locale, vedere [Informazioni sul gateway dati locale](/data-integration/gateway/service-gateway-onprem). Per altre informazioni sul gateway dati locale e su Power BI, visitare il [blog di Microsoft Power BI](https://powerbi.microsoft.com/blog/) e il sito [Microsoft Power BI Community](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Considerazioni sull'installazione per il gateway dati locale

Prima di installare il gateway dati locale per il servizio cloud Power BI, è necessario tenere presenti alcune considerazioni. Le sezioni seguenti descrivono queste considerazioni.

### <a name="number-of-users"></a>Numero di utenti

Il numero di utenti che utilizzano un report che usa il gateway è un parametro importante per decidere dove installare il gateway. Di seguito sono riportate alcune domande da considerare:

* Gli utenti useranno questi report in momenti diversi del giorno?
* Quali tipi di connessioni sono in uso (DirectQuery o importazione)?
* Tutti gli utenti usano lo stesso report?

Se gli utenti hanno tutti accesso a un determinato report alla stessa ora di ogni giorno, è consigliabile assicurarsi di installare il gateway in un computer che possa gestire tutte le richieste (vedere le sezioni seguenti per i contatori delle prestazioni e i requisiti minimi che consentono di determinarlo).

In **Power BI** esiste un vincolo che consente *un solo* gateway per *report*, pertanto anche se un report si basa su più origini dati, tutte queste origini dati devono transitare attraverso un singolo gateway. Tuttavia, se un dashboard è basato su *più* report, è possibile usare un gateway dedicato per ogni report partecipante e quindi distribuire il carico di gateway tra quei report che contribuiscono a tale dashboard singolo.

### <a name="connection-type"></a>Tipo di connessione

**Power BI** offre due tipi di connessioni: **DirectQuery** e **importazione**. Non tutte le origini dati supportano entrambi i tipi di connessione e diversi motivi possono contribuire alla scelta di uno di essi, ad esempio requisiti di sicurezza, prestazioni, limiti di dati e le dimensioni dei modelli di dati. Per altre informazioni sui tipi di connessione e sulle origini dati supportate vedere l'[elenco dei tipi di origini dati disponibili](service-gateway-data-sources.md#list-of-available-data-source-types).

A seconda del tipo di connessione in uso, l'utilizzo del gateway può essere diverso. Ad esempio, è consigliabile separare le origini dati **DirectQuery** dalle origini dati di **Aggiornamento pianificato** laddove possibile (presupponendo che si trovino in report diversi e possano essere separate). Ciò impedisce al gateway di accumulare migliaia di richieste DirectQuery in coda, contemporaneamente all'aggiornamento pianificato del mattino di un modello di dati di grandi dimensioni che viene usato per il dashboard principale della società. Ecco i fattori da considerare per ciascuno di essi:

* Per **Aggiornamento pianificato**: a seconda delle dimensioni della query e del numero di aggiornamenti che si verificano ogni giorno, è possibile scegliere di restare nei requisiti hardware minimi consigliati oppure eseguire l'aggiornamento a un computer con prestazioni superiori. Se una determinata query non è stata ridotta, si verificano trasformazioni nel computer del gateway e, di conseguenza, il computer del gateway trae vantaggio dalla maggiore quantità di RAM disponibile.

* Per **DirectQuery**: viene inviata una query ogni volta che un utente apre il report o esamina i dati. Dunque, se si prevede l'accesso simultaneo di più di 1.000 utenti, è consigliabile assicurarsi che il computer abbia componenti hardware soli di affidabili. Un numero maggiore di memorie centrali CPU garantisce una migliore velocità effettiva per una connessione **DirectQuery**.

I requisiti per un computer in cui si esegue l'installazione sono reperibili nei [requisiti di installazione](/data-integration/gateway/service-gateway-install#requirements) del gateway dati locale.

### <a name="location"></a>Località

La posizione di installazione del gateway può avere un impatto significativo sulle prestazioni delle query, quindi assicurarsi che il gateway, i percorsi di origine dati e il tenant di Power BI siano più vicino possibile tra loro per ridurre al minimo la latenza di rete. Per determinare la posizione del tenant di Power BI, nel servizio Power BI selezionare l'icona **?** nell'angolo in alto a destra e quindi scegliere **Informazioni su Power BI**.

![Determinare il percorso del tenant Power BI](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Inoltre, se si intende usare il gateway Power BI con Azure Analysis Services, assicurarsi che le aree dati di entrambi corrispondano. Per altre informazioni sull'impostazione delle aree dati per più servizi, guardare [questo video](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Passaggi successivi

* [Configurazione delle impostazioni proxy](/data-integration/gateway/service-gateway-proxy)  
* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)  
* [Domande frequenti sul gateway dati locale - Power BI](service-gateway-power-bi-faq.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

