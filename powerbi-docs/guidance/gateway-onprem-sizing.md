---
title: Servizio gateway dati locale
description: Linee guida per il ridimensionamento del gateway dati locale.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: de84dd7e9021abf1198f2dc4f910afb8bd078ac6
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279527"
---
# <a name="on-premises-data-gateway-sizing"></a>Servizio gateway dati locale

Questo articolo è destinato agli amministratori di Power BI che devono installare e gestire il [gateway dati locale](../connect-data/service-gateway-onprem.md).

Il gateway è necessario ogni volta che Power BI deve accedere a dati non accessibili direttamente tramite Internet. Può essere installato in un server locale o in un'infrastruttura distribuita come servizio (IaaS) ospitata in macchine virtuali.

## <a name="gateway-workloads"></a>Carichi di lavoro del gateway

Il gateway dati locale supporta due carichi di lavoro. È importante comprendere questi carichi di lavoro prima di illustrare il ridimensionamento del gateway con relative raccomandazioni.

### <a name="cached-data-workload"></a>Carico di lavoro dei dati memorizzati nella cache

Il carico di lavoro dei _dati memorizzati nella cache_ recupera e trasforma i dati di origine per il caricamento in set di dati di Power BI. Questa operazione viene eseguita in tre passaggi:

1. **Connessione**: il gateway si connette ai dati di origine
1. **Recupero e trasformazione dei dati**: i dati vengono recuperati e, quando necessario, trasformati. Quando possibile, il motore mashup di Power Query esegue il push dei passaggi di trasformazione nell'origine dati, operazione nota come _[riduzione delle query](power-query-folding.md)_ . Quando non è possibile, le trasformazioni devono essere eseguite dal gateway. In questo caso, il gateway utilizzerà più risorse di CPU e memoria.
1. **Trasferimento**: i dati vengono trasferiti al servizio Power BI. È importante disporre di una connessione Internet affidabile e veloce, specialmente per i volumi di dati di grandi dimensioni.

![Diagramma che mostra il gateway dati locale che si connette a origini locali: database relazionale, cartella di lavoro di Excel e file CSV. Il gateway recupera e trasforma i dati.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Carico di lavoro di connessione dinamica e DirectQuery

Il carico di lavoro di _connessione dinamica e DirectQuery_ funziona principalmente in modalità pass-through. Il servizio Power BI invia query e il gateway risponde con i risultati delle query. In genere, i risultati delle query hanno dimensioni ridotte.

- Per altre informazioni sulla connessione dinamica, vedere [Set di dati nel servizio Power BI (modelli ospitati esternamente)](../connect-data/service-datasets-understand.md#external-hosted-models).
- Per altre informazioni su DirectQuery, vedere [Modalità del set di dati nel servizio Power BI (modalità DirectQuery)](../connect-data/service-dataset-modes-understand.md#directquery-mode).

Questo carico di lavoro richiede risorse della CPU per il routing delle query e dei risultati delle query. In genere, la richiesta di CPU è molto inferiore rispetto al carico di lavoro dei dati memorizzati nella cache, soprattutto quando è necessario trasformare i dati per la memorizzazione nella cache.

Una connettività affidabile, veloce e costante è importante per assicurare esperienze reattive agli utenti del report.

![Diagramma che visualizza il gateway dati locale che si connette alle origini locali: database tabulare di Analysis Services e relazionale. Il gateway opera principalmente in modalità pass-through.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Considerazioni sul ridimensionamento

Determinare le dimensioni corrette per il computer del gateway può dipendere dalle variabili seguenti:

- Per i carichi di lavoro dei dati memorizzati nella cache:
  - Numero di aggiornamenti del set di dati simultanei
  - Tipi di origini dati (database relazionale, database analitico, feed di dati o file)
  - Volume dei dati da recuperare dalle origini dati
  - Tutte le trasformazioni che devono essere eseguite dal motore mashup di Power Query
  - Volume dei dati da trasferire al servizio Power BI
- Per i carichi di lavoro di connessione dinamica e DirectQuery:
  - Numero di utenti di report simultanei
  - Numero di oggetti visivi nelle pagine del report (ogni oggetto visivo invia almeno una query)
  - Frequenza degli aggiornamenti della cache delle query del dashboard di Power BI
  - Numero di report in tempo reale che usano la funzionalità [Aggiornamento pagina automatico](../create-reports/desktop-automatic-page-refresh.md)
  - Se i set di dati impongono la [sicurezza a livello di riga](../create-reports/desktop-rls.md)

In genere, i carichi di lavoro di connessione dinamica e DirectQuery richiedono risorse CPU sufficienti, mentre i carichi di lavoro dei dati memorizzati nella cache richiedono più CPU e memoria. Entrambi i carichi di lavoro dipendono da una buona connettività con il servizio Power BI e le origini dati.

> [!NOTE]
> Le capacità di Power BI impongono limiti al parallelismo di aggiornamento e alla velocità effettiva di connessione dinamica e DirectQuery. Non ha senso ridimensionare il gateway per offrire capacità maggiori rispetto a quelle supportate dal servizio Power BI. I limiti differiscono in base allo SKU Premium (e allo SKU A di dimensioni equivalenti). Per altre informazioni, vedere [Che cos'è Power BI Premium? (nodi delle capacità)](../admin/service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Consigli

Le raccomandazioni per il ridimensionamento del gateway dipendono da molte variabili. In questa sezione vengono fornite raccomandazioni generali che è possibile prendere in considerazione.

### <a name="initial-sizing"></a>Ridimensionamento iniziale

Può essere difficile stimare accuratamente le dimensioni corrette. Si consiglia di iniziare con un computer con almeno 8 core CPU, 8 GB di RAM e schede di rete da più gigabit. È quindi possibile misurare un carico di lavoro tipico del gateway registrando i contatori di sistema per CPU e memoria. Per altre informazioni, vedere [Monitorare e ottimizzare le prestazioni del gateway dati locale](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Connettività

Pianificare la migliore connettività possibile tra il servizio Power BI e il gateway e il gateway e le origini dati.

- Cercare di ottenere affidabilità, velocità elevate e latenze basse e costanti
- Eliminare o ridurre gli hop tra il gateway e le origini dati
- Rimuovere eventuali limitazioni della larghezza di banda della rete imposte dal livello proxy del firewall. Per altre informazioni sugli endpoint di Power BI, vedere [URL di Power BI per l'elenco elementi consentiti](../admin/power-bi-whitelist-urls.md).
- Configurare [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) per stabilire connessioni private e gestite a Power BI
- Per le origini dati in macchine virtuali di Azure, assicurarsi che le macchine virtuali si trovino nella [stessa posizione del servizio Power BI](../admin/service-admin-where-is-my-tenant-located.md)
- Per i carichi di lavoro di connessione dinamica con SQL Server Analysis Services (SSAS) che coinvolgono la sicurezza a livello di riga dinamica, garantire una buona connettività tra il computer del gateway e Active Directory locale

### <a name="clustering"></a>Clustering

Per le distribuzioni su larga scala, è possibile creare un gateway di installazioni cluster. I cluster evitano singoli punti di guasto e possono bilanciare il carico del traffico tra i gateway. È possibile:

- Installare uno o più gateway in un cluster
- Isolare i carichi di lavoro in gateway autonomi o in cluster di server gateway

Per altre informazioni, vedere [Gestire i cluster a disponibilità elevata e il bilanciamento del carico del gateway dati locale](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Progettazione e impostazioni dei set di dati

La progettazione dei set di dati e le relative impostazioni possono avere un effetto sui carichi di lavoro del gateway. Per ridurre il carico di lavoro del gateway, è possibile prendere in considerazione le azioni seguenti.

Per i set di dati di importazione:

- Configurare un aggiornamento dei dati meno frequente
- Configurare l'[aggiornamento incrementale](../admin/service-premium-incremental-refresh.md) per ridurre al minimo la quantità di dati da trasferire
- Quando possibile, assicurarsi che venga eseguita la [riduzione delle query](power-query-folding.md)
- In particolare per i volumi di dati di grandi dimensioni o se sono necessari risultati con bassa latenza, convertire il progetto in un modello DirectQuery o [composito](../connect-data/service-dataset-modes-understand.md#composite-mode)

Per i set di dati di DirectQuery:

- Ottimizzare le origini dati, il modello e le progettazioni dei report. Per altre informazioni, vedere [Linee guida per il modello DirectQuery in Power BI Desktop](directquery-model-guidance.md)
- Creare [aggregazioni](../transform-model/desktop-aggregations.md) per memorizzare nella cache i risultati di livello superiore per ridurre il numero di richieste DirectQuery
- Limitare gli intervalli di [aggiornamento automatico delle pagine](../create-reports/desktop-automatic-page-refresh.md) nelle progettazioni dei report e nelle impostazioni delle capacità
- Soprattutto quando viene applicata la sicurezza a livello di riga dinamica, limitare la frequenza di aggiornamento della cache del dashboard
- In particolare per i volumi di dati più piccoli o per i dati non volatili, convertire il progetto in un modello di importazione o [composito](../connect-data/service-dataset-modes-understand.md#composite-mode)

Per i set di dati di connessione dinamica:

- Soprattutto quando viene applicata la sicurezza a livello di riga dinamica, limitare la frequenza di aggiornamento della cache del dashboard

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni correlate a questo articolo, vedere le risorse seguenti:

- [Indicazioni per la distribuzione di un gateway dati per Power BI](../connect-data/service-gateway-deployment-guidance.md)
- [Configurare le impostazioni del proxy per il gateway dati locale](/data-integration/gateway/service-gateway-proxy)
- [Monitorare e ottimizzare le prestazioni del gateway dati locale](/data-integration/gateway/service-gateway-performance)
- [Risolvere i problemi relativi ai gateway - Power BI](../connect-data/service-gateway-onprem-tshoot.md)
- [Risolvere i problemi del gateway dati locale](/data-integration/gateway/service-gateway-tshoot)
- [Importanza della riduzione delle query](power-query-folding.md)
- Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com)
