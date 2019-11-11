---
title: Procedure consigliate per i flussi di dati di Power BI
description: Procedure consigliate per i flussi di dati di Power BI
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4bbc8b71455d01405854304dd4b889f664ce8575
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877283"
---
# <a name="dataflows-best-practice"></a>Procedura consigliata per i flussi di dati

Questo articolo illustra le procedure consigliate per la progettazione dei flussi di dati in Power BI. È possibile usare queste linee guida per apprendere come creare i flussi di dati e applicare queste procedure ai propri flussi di dati.

> [!NOTE]
> Le raccomandazioni contenute in questo articolo sono linee guida. Per ogni procedura consigliata descritta in questo articolo possono esistere motivi legittimi per non attenersi completamente alle linee guida. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Suddividere l'inserimento e la trasformazione per l'uso del motore di calcolo avanzato

Quando si creano i flussi di dati si può essere tentati di creare un singolo flusso con tutte le entità, le trasformazioni, i join e i miglioramenti in un'unica posizione. Per i set di dati più piccoli può essere più comodo usare un singolo flusso di dati. Ma quando si gestiscono volumi di dati di dimensioni maggiori, l'esecuzione di join o di determinate trasformazioni a volte può risentire di limitazioni della memoria o di altro tipo. Per risolvere questi problemi, è stato rilasciato un motore avanzato per gli utenti di Power BI Premium che gestiscono volumi di dati molto più grandi. Il motore di calcolo avanzato funziona solo con entità collegate o calcolate, quindi la creazione di un flusso di dati separato per l'inserimento e di un flusso di dati collegato per eseguire tutte le operazioni di unione e trasformazione più complesse può trarre vantaggio dal motore avanzato.

La suddivisione dei flussi di dati è utile anche per la diagnosi e il debug dei problemi di aggiornamento, soprattutto quando si lavora con origini con limitazioni.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Eseguire azioni che possono usare il motore di calcolo avanzato

Assicurarsi di usare il motore di calcolo avanzato effettuando le trasformazioni di join e filtri in un'entità calcolata prima di eseguire altri tipi di trasformazioni.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Suddividere i flussi di dati durante la connessione a SharePoint

Quando si usa SharePoint e si effettua la connessione a più file, si possono verificare errori sporadici. SharePoint limita le richieste in modo da rimanere affidabile e reattivo. Di conseguenza, quando ci si connette ai file di Excel da SharePoint, si può ritenere opportuno scaricare tutti i file in un singolo flusso di dati. Se si scaricano molti file, più di 20, creare due o più flussi di dati per suddividere il carico di aggiornamento e superare i limiti di SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Evitare di pianificare l'aggiornamento per le entità collegate all'interno della stessa area di lavoro

Se si viene regolarmente bloccati se si tenta di accedere ai flussi di dati che contengono entità collegate, è possibile che un flusso di dati dipendente corrispondente all'interno della stessa area di lavoro venga bloccato durante l'aggiornamento del flusso di dati. Tale blocco garantisce che le transazioni siano accurate e che entrambi i flussi di dati vengano aggiornati correttamente, ma può impedire la modifica da parte dell'utente. 

Se si configura una pianificazione separata per il flusso di dati collegato, è possibile che i flussi di dati si aggiornino inutilmente e impediscano all'utente di modificare il flusso di dati. Esistono due raccomandazioni per evitare questo problema: 

* Evitare di impostare una pianificazione degli aggiornamenti per un flusso di dati collegato nella stessa area di lavoro del flusso di dati di origine
* Se si vuole configurare separatamente una pianificazione degli aggiornamenti e si vuole evitare il comportamento di blocco, separare il flusso di dati in un'altra area di lavoro.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Creare un'area di lavoro separata per l'inserimento, la trasformazione

Per consentire l'accesso ai dati del flusso di dati sottostante a molti utenti, senza consentire l'accesso ai dati non elaborati del sistema di origine sottostante, creare un'area di lavoro separata che contenga tutti i dati che è necessario condividere e assegnare le autorizzazioni. Le singole autorizzazioni del flusso di dati attualmente non sono supportate.

### <a name="ensure-capacity-is-in-the-same-region"></a>Verificare che la capacità si trovi nella stessa area

I flussi di dati attualmente non supportano più aree geografiche. La capacità Premium deve essere nella stessa area del tenant di Power BI.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Separare le origini locali dalle origini cloud

Oltre alle procedure consigliate descritte in precedenza, è possibile creare un flusso di dati separato per ogni tipo di origine, ad esempio locale, cloud, SQL Server, Spark, Dynamics e così via. È consigliabile suddividere il flusso di dati in base al tipo di origine dati. Tale separazione per tipo di origine semplifica la risoluzione dei problemi ed evita i limiti interni quando si aggiornano i flussi di dati.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Separare i flussi di dati in una capacità separata

Se si riscontra la presenza di limitazioni o si verificano regolarmente errori dei flussi di dati a causa di limiti di memoria rispetto alla capacità, è consigliabile separare i flussi di dati o aumentare la capacità Premium per aggiungere memoria.

## <a name="next-steps"></a>Passaggi successivi

Questo articolo ha illustrato le procedure consigliate relative ai flussi di dati. Per altre informazioni sui flussi di dati, possono essere utili gli articoli seguenti:

* [Preparazione dei dati self-service con flussi di dati](service-dataflows-overview.md)
* [Creare e usare flussi di dati in Power BI](service-dataflows-create-use.md)
* [Uso delle entità calcolate in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso di flussi di dati con origini dati locali](service-dataflows-on-premises-gateways.md)

Per informazioni sullo sviluppo CDM e risorse per esercitarsi, vedere gli argomenti seguenti:
* [Panoramica del modello CDM (Common Data Model)](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Cartelle CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Definizione del file del modello CDM](https://go.microsoft.com/fwlink/?linkid=2045521)


Per altre informazioni su Power Query e sull'aggiornamento pianificato, è possibile leggere questi articoli:
* [Panoramica delle query in Power BI Desktop](desktop-query-overview.md)
* [Configurazione dell'aggiornamento pianificato](refresh-scheduled-refresh.md)
