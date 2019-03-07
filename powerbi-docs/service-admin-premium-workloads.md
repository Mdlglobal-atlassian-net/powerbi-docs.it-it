---
title: Come configurare i carichi di lavoro in Power BI Premium
description: Informazioni su come configurare i carichi di lavoro in una capacità Power BI Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/26/2019
LocalizationGroup: Premium
ms.openlocfilehash: 5b9bec67fef672d219b11bf3b3750959e72410b6
ms.sourcegitcommit: 364ffa1178cdfb0a20acffc0fd79922ebc892d72
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57226067"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurare i carichi di lavoro in una capacità Premium

Questo articolo descrive l'abilitazione e la configurazione di carichi di lavoro per le capacità Power BI Premium. Per impostazione predefinita le capacità supportano solo il carico di lavoro associato all'esecuzione delle query di Power BI. I carichi di lavoro delle query sono ottimizzati e limitati alle risorse determinate dallo SKU di capacità Premium. Le capacità Premium supportano anche carichi di lavoro aggiuntivi che possono usare le risorse di capacità.

## <a name="configure-workloads"></a>Configurare i carichi di lavoro

È possibile abilitare e configurare carichi di lavoro aggiuntivi per [flussi di dati](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) e [report impaginati](paginated-reports-save-to-power-bi-service.md). I valori di memoria predefiniti per questi carichi di lavoro si basano sui nodi di capacità disponibili per lo SKU. Le impostazioni della memoria massima non sono cumulative. La memoria massima specificata viene allocata in modo dinamico per i flussi di dati, ma staticamente viene allocata per i report impaginati. 

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Per configurare i carichi di lavoro nel portale di amministrazione di Power BI

1. In **Impostazioni di capacità** > **Capacità Premium** selezionare una capacità.

1. In **ALTRE OPZIONI** espandere **Carichi di lavoro**.

1. Abilitare uno o più carichi di lavoro e impostare un valore per **Memoria massima**.   

    
    ![Abilitare i carichi di lavoro](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Fare clic su **Applica**.

> [!NOTE]
> Se si abilita il carico di lavoro per i report impaginati, i report impaginati consentiranno di eseguire il codice quando si esegue il rendering di un report, ad esempio quando il colore del testo cambia in modo dinamico in base al contenuto. Power BI Premium esegue i report impaginati in uno spazio contenuto all'interno della capacità. Viene usata la memoria massima specificata per questo spazio, indipendentemente dal fatto che il carico di lavoro sia attivo o meno. Se si usano i report o i flussi di dati di Power BI nella stessa capacità, assicurarsi di impostare per i report impaginati una memoria sufficientemente bassa da non influire negativamente sugli altri carichi di lavoro. in rari casi, il carico di lavoro per i report impaginati può diventare non disponibile. In questo caso, per il carico di lavoro viene visualizzato uno stato di errore nel portale di amministrazione e gli utenti vedono il timeout per il rendering del report. Per attenuare questo problema, disabilitare il carico di lavoro, quindi riabilitarlo.


### <a name="rest-api"></a>API REST

I carichi di lavoro possono essere abilitati e assegnati a una capacità usando le API REST [Capacità](https://docs.microsoft.com/rest/api/power-bi/capacities).


## <a name="next-steps"></a>Passaggi successivi

[Ottimizzazione e gestione delle risorse della capacità Power BI Premium](service-premium-understand-how-it-works.md)   
[Preparazione dei dati self-service in Power BI con flusso di dati](service-dataflows-overview.md)   
[Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Altre domande? [Inviare una domanda alla community di Power BI](http://community.powerbi.com/)