---
title: Come configurare i carichi di lavoro in Power BI Premium
description: Informazioni su come configurare i carichi di lavoro in una capacità Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564869"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurare i carichi di lavoro in una capacità Premium

Questo articolo descrive l'abilitazione e la configurazione di carichi di lavoro per le capacità Power BI Premium. Per impostazione predefinita le capacità supportano solo il carico di lavoro associato all'esecuzione delle query di Power BI. È anche possibile abilitare e configurare carichi di lavoro aggiuntivi per **[intelligenza artificiale (Servizi cognitivi)](service-cognitive-services.md)** , **[flussi di dati](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[report impaginati](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Impostazioni predefinite della memoria

I carichi di lavoro delle query sono ottimizzati e limitati alle risorse determinate dallo SKU di capacità Premium. Le capacità Premium supportano anche carichi di lavoro aggiuntivi che possono usare le risorse della capacità. I valori di memoria predefiniti per questi carichi di lavoro si basano sui nodi di capacità disponibili per lo SKU. Le impostazioni della memoria massima non sono cumulative. La memoria massima specificata viene allocata in modo dinamico per l'intelligenza artificiale e i flussi di dati, ma staticamente viene allocata per i report impaginati. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKU di Microsoft Office per scenari SaaS (Software as a Service)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N/D | N/D | impostazione predefinita il 20%. 20% minimo | 20% predefinita; 10% minima | 20% predefinita; 5% minima |
| Dataflows | N/D |20% predefinita; 12% minima  | 20% predefinita; 5% minima  | 20% predefinita; 3% minima | 20% predefinita; 2% minima  |
| Report impaginati | N/D |N/D | 20% predefinita; 10% minima | 20% predefinita; 5% minima | 20% predefinita; 2,5% minima |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKU di Microsoft Azure per scenari PaaS (Platform as a Service)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N/D                      | impostazione predefinita il 20%. minimo di 100%                     | impostazione predefinita il 20%. 50% minimo                     | impostazione predefinita il 20%. 20% minimo | 20% predefinita; 10% minima | 20% predefinita; 5% minima |
| Dataflows         | 40% predefinita; 40% minima | 24% predefinita; 24% minima | 20% predefinita; 12% minima | 20% predefinita; 5% minima  | 20% predefinita; 3% minima | 20% predefinita; 2% minima   |
| Report impaginati | N/D                      | N/D                      | N/D                     | 20% predefinita; 10% minima | 20% predefinita; 5% minima | 20% predefinita; 2,5% minima |
| | | | | | |

## <a name="workload-settings"></a>Impostazioni di carico di lavoro

### <a name="ai-preview"></a>Intelligenza artificiale (anteprima)

Oltre al **Max Memory** impostazione, il carico di lavoro di intelligenza artificiale è un'impostazione aggiuntiva, **consentire l'utilizzo da Power BI Desktop**. Il valore predefinito è **disattivata**. Questa impostazione è riservata per usi futuri e non può contenere tutti i tenant.

### <a name="datasets-preview"></a>Set di dati (anteprima)

Per impostazione predefinita, il carico di lavoro di set di dati è abilitata e non può essere disabilitata. Questo carico di lavoro contiene un'impostazione aggiuntiva, **Endpoint XMLA**. Il valore predefinito è **1**, significato abilitato. Questa impostazione specifica le connessioni dalle applicazioni client rispettano l'appartenenza al gruppo di sicurezza impostata a livello di area di lavoro e app. Per altre informazioni, vedere [Connetti al set di dati con strumenti e applicazioni client](service-premium-connect-tools.md).

### <a name="dataflows"></a>Dataflows

Oltre al **Max Memory** l'impostazione, il carico di lavoro di flussi di dati ha un'impostazione aggiuntiva, **le dimensioni del contenitore**. Questa impostazione consente di ottimizzare le prestazioni del carico di lavoro del flusso di dati per l'elaborazione di flussi di dati più complessi e con intensa attività di calcolo.

Quando si aggiornano un flusso di dati, il carico di lavoro del flusso di dati genera un contenitore per ogni entità nel flusso di dati. Ogni contenitore può richiedere fino al volume di memoria specificato nell'impostazione delle dimensioni del contenitore. Il valore predefinito per tutti gli SKU è **700 MB**. È possibile modificare questa impostazione se:

- Flussi di dati richiede troppo tempo per aggiornare o l'aggiornamento del flusso di dati non riesce in un timeout.
- Le entità del flusso di dati includono passaggi di calcolo, ad esempio, un join.  

Le consigliata è usare il [le metriche della capacità di Power BI Premium](service-admin-premium-monitor-capacity.md) analizzare le prestazioni del carico di lavoro del flusso di dati dell'app. 

In alcuni casi, aumentando le dimensioni del contenitore può non migliorare le prestazioni. Ad esempio, se il flusso di dati stia ottenendo i dati solo da un'origine senza eseguire calcoli significativi, modificare le dimensioni del contenitore probabilmente non risultare utile. Se abiliterà il carico di lavoro del flusso di dati allocare altra memoria per l'entità, le operazioni di aggiornamento, può essere utile aumentare le dimensioni del contenitore. Grazie all'uso maggiore quantità di memoria allocata, è possibile ridurre il tempo che necessario per aggiornare le entità larga misura calcolate. 

Il valore di dimensione del contenitore non può superare la memoria massima per il carico di lavoro di flussi di dati. Ad esempio, una capacità di P1 è 25GB di memoria. Se il carico di lavoro del flusso di dati Max Memory (%) è impostato su 20%, contenitore di dimensioni (MB) non può superare 5000. In tutti i casi, le dimensioni del contenitore non può superare la Max Memory, anche se si imposta un valore più alto. 

### <a name="paginated-reports-preview"></a>Report impaginati (anteprima)

I report impaginati consentono al codice personalizzato da eseguire durante il rendering di un report. Ad esempio, in modo dinamico la modifica di colore del testo in base al contenuto, che può richiedere ulteriore memoria. Power BI Premium esegue i report impaginati in uno spazio contenuto all'interno della capacità. Max Memory specificato viene usato *o meno* il carico di lavoro è attiva. Se la modifica l'impostazione di memoria massima per impostazione predefinita, assicurarsi di impostare lo bassa sufficiente che l'it non influire negativamente sulle altri carichi di lavoro.

In alcuni casi, il carico di lavoro di report impaginati può diventare non disponibile. In questo caso, il carico di lavoro mostra uno stato di errore nel portale di amministrazione e gli utenti visualizzano i timeout per il rendering del report. Per attenuare il problema, disabilitare il carico di lavoro e quindi riabilitarla.

## <a name="configure-workloads"></a>Configurare i carichi di lavoro

È possibile ottimizzare le risorse disponibili della capacità abilitando i carichi di lavoro solo se verranno effettivamente usati. Cambiare le impostazioni della memoria solo dopo aver stabilito che le impostazioni predefinite non soddisfano i requisiti relativi alle risorse della capacità.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Per configurare i carichi di lavoro nel portale di amministrazione di Power BI

1. In **Impostazioni di capacità** > **Capacità Premium** selezionare una capacità.

1. In **ALTRE OPZIONI** espandere **Carichi di lavoro**.

1. Abilitare uno o più carichi di lavoro e impostare un valore per **Memoria massima**.   

    
    ![Abilitare i carichi di lavoro](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Fare clic su **Applica**.

### <a name="rest-api"></a>API REST

I carichi di lavoro possono essere abilitati e assegnati a una capacità usando le API REST [Capacità](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitoraggio dei carichi di lavoro

L'[app Metrica per la capacità Power BI Premium](service-admin-premium-monitor-capacity.md) fornisce metriche per set di dati, flussi di dati e report impaginati per monitorare i carichi di lavoro abilitati per le capacità. 

## <a name="next-steps"></a>Passaggi successivi

[Ottimizzazione della capacità di Power BI Premium](service-premium-capacity-optimize.md)     
[Preparazione dei dati self-service in Power BI con flusso di dati](service-dataflows-overview.md)   
[Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Altre domande? [Inviare una domanda alla community di Power BI](http://community.powerbi.com/)