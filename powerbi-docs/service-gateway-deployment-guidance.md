---
title: Indicazioni per la distribuzione di un gateway dati per Power BI
description: Procedure consigliate e considerazioni per la distribuzione di un gateway per Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: a9d30d1346bf2801cd6cba44cc7cc33d734fccbb
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699568"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Indicazioni per la distribuzione di un gateway dati per Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Questo articolo contiene indicazioni e considerazioni per la distribuzione di un gateway dati per Power BI nell'ambiente di rete.

Per informazioni su come scaricare, installare, configurare e gestire il gateway dati locale, vedere [Informazioni sul gateway dati locale](/data-integration/gateway/service-gateway-onprem). Per altre informazioni sul gateway dati locale e su Power BI, visitare il [blog di Microsoft Power BI](https://powerbi.microsoft.com/blog/) e il sito [Microsoft Power BI Community](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Considerazioni sull'installazione per il gateway dati locale

Prima di installare il gateway dati locale per il servizio cloud Power BI, è necessario tenere presenti alcune considerazioni, Le sezioni seguenti descrivono queste considerazioni.

### <a name="number-of-users"></a>Numero di utenti

Il numero di utenti che usano un report correlato al gateway è una metrica importante nella decisione relativa alla posizione in cui installarlo. Di seguito sono riportate alcune domande da considerare:

* Gli utenti useranno i report in momenti diversi del giorno?
* Quali tipi di connessioni usano (DirectQuery o importazione)?
* Tutti gli utenti usano lo stesso report?

Se tutti gli utenti accedono a un determinato report alla stessa ora ogni giorno, verificare di installare il gateway in un computer in grado di gestire tutte le richieste. Vedere le sezioni seguenti per i contatori delle prestazioni e i requisiti minimi che consentono di determinare se un computer è adeguato.

Un vincolo presente in Power BI consente solo *un* gateway per *report*. Anche se un report si basa su più origini dati, tutte queste origini devono passare attraverso un singolo gateway. Se un dashboard si basa su *più* report, è possibile usare un gateway dedicato per ogni report che contribuisce. In questo modo il carico del gateway viene distribuito tra i diversi report che contribuiscono al singolo dashboard.

### <a name="connection-type"></a>Tipo di connessione

In Power BI sono disponibili due tipi di connessioni, ovvero DirectQuery e importazione. Non tutte le origini dati supportano entrambi i tipi di connessione. Molti fattori possono contribuire a una scelta rispetto all'altra, ad esempio i requisiti di sicurezza, le prestazioni, i limiti dei dati e le dimensioni del modello di dati. Per altre informazioni sui tipi di connessione e sulle origini dati supportate, vedere l'[elenco dei tipi di origini dati disponibili](service-gateway-data-sources.md#list-of-available-data-source-types).

A seconda del tipo di connessione in uso, l'utilizzo del gateway può essere diverso. Provare ad esempio a separare le origini dati DirectQuery dalle origini dati di aggiornamento pianificato, quando possibile. Si presuppone che le origini dati si trovino in report diversi e che possano essere separate. La separazione delle origini impedisce al gateway di accumulare migliaia di richieste DirectQuery, accodate contemporaneamente all'aggiornamento pianificato del mattino, di un modello di dati di grandi dimensioni usato per il dashboard principale della società. 

Di seguito vengono indicati i fattori da considerare per ogni opzione.

* **Aggiornamento pianificato**: a seconda delle dimensioni della query e del numero di aggiornamenti giornalieri, è possibile scegliere di mantenere i requisiti hardware minimi consigliati oppure di eseguire l'aggiornamento a un computer con prestazioni superiori. Se una determinata query non è stata ridotta, le trasformazioni vengono eseguite nel computer del gateway che pertanto trae vantaggio dalla maggiore disponibilità della RAM.

* **DirectQuery**: viene inviata una query ogni volta che un utente apre il report o esamina i dati. Se si prevede che più di 1.000 utenti accedano contemporaneamente ai dati, verificare che il computer disponga di componenti hardware affidabili e idonei. Un numero maggiore di core CPU garantisce una migliore velocità effettiva per una connessione DirectQuery.

Per i requisiti di installazione del computer, vedere i [requisiti di installazione](/data-integration/gateway/service-gateway-install#requirements) del gateway dati locale.

### <a name="location"></a>Posizione

La posizione di installazione del gateway può avere un impatto significativo sulle prestazioni delle query, quindi verificare che il gateway, i percorsi delle origini dati e il tenant di Power BI siano il più vicino possibile tra loro per ridurre al minimo la latenza di rete. Per determinare la posizione del tenant di Power BI, nel servizio Power BI selezionare l'icona **?** nell'angolo in alto a destra e quindi scegliere **Informazioni su Power BI**.

![Determinare il percorso del tenant Power BI](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Se si intende usare il gateway Power BI con Azure Analysis Services, verificare che le aree dati di entrambi corrispondano. Per altre informazioni su come impostare le aree dati per più servizi, guardare [questo video](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Passaggi successivi

* [Configurazione delle impostazioni proxy](/data-integration/gateway/service-gateway-proxy)  
* [Risolvere i problemi relativi ai gateway - Power BI](service-gateway-onprem-tshoot.md)  
* [Domande frequenti sul gateway dati locale - Power BI](service-gateway-power-bi-faq.md)  

Altre domande? Provare la [Community di Power BI](https://community.powerbi.com/).

