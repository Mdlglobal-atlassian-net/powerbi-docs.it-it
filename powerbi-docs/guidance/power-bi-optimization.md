---
title: Guida all'ottimizzazione per Power BI
description: Guida all'ottimizzazione per Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d718c9c7f627d735c083a46c1483815e3744faca
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378870"
---
# <a name="optimization-guide-for-power-bi"></a>Guida all'ottimizzazione per Power BI

Questo articolo offre indicazioni che consentono agli sviluppatori e agli amministratori di produrre e gestire soluzioni Power BI ottimizzate. È possibile ottimizzare la soluzione a livelli diversi dell'architettura. I livelli sono:

- Origini dati
- Modello di dati
- Visualizzazioni, inclusi dashboard e report (impaginati o meno) di Power BI
- Ambiente, inclusi capacità, gateway dati e rete

## <a name="optimizing-the-data-model"></a>Ottimizzazione del modello di dati

Il modello di dati supporta l'intera esperienza di visualizzazione. I modelli di dati, ospitati esternamente o internamente, in Power BI sono detti _set di dati_. È importante comprendere le opzioni disponibili e scegliere il tipo di set di dati appropriato per la soluzione. Esistono tre modalità di set di dati: Importazione, DirectQuery e Composito. Per altre informazioni, vedere [Set di dati nel servizio Power BI](../service-datasets-understand.md) e [Modalità del set di dati nel servizio Power BI](../service-dataset-modes-understand.md).

Per indicazioni specifiche sulla modalità del set di dati, vedere:

- [Tecniche di riduzione dei dati per i modelli di importazione](import-modeling-data-reduction.md)
- [Linee guida per il modello DirectQuery in Power BI Desktop](directquery-model-guidance.md)
- [Linee guida per i modelli compositi in Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Ottimizzazione delle visualizzazioni

Le visualizzazioni di Power BI possono essere dashboard o report (impaginati o meno) di Power BI. Ognuna ha architetture diverse e quindi per ognuna valgono indicazioni specifiche. 

### <a name="dashboards"></a>Dashboard

È importante comprendere che Power BI gestisce una cache per i riquadri del dashboard, ad eccezione dei riquadri dei report dinamici e dei riquadri di streaming. Per altre informazioni, vedere [Aggiornamento dei dati in Power BI (aggiornamento del riquadro)](../refresh-data.md#tile-refresh). Se il set di dati impone la [sicurezza a livello di riga ](../service-admin-rls.md) dinamica, assicurarsi di comprendere le implicazioni relative alle prestazioni, dato che i riquadri vengono memorizzati nella cache in base all'utente.

Quando si aggiungono riquadri di report dinamici a un dashboard, questi non vengono forniti dalla cache di query, ma si comportano in modo analogo ai report ed eseguono query su core back-end immediatamente.

Come indicato dal nome, il recupero dei dati dalla cache offre prestazioni migliori e più coerenti rispetto al recupero dall'origine dati. Per sfruttare al meglio questa funzionalità, è consigliabile impostare i dashboard come prima pagina di destinazione per gli utenti. Aggiungere gli oggetti visivi più richiesti e usati di frequente ai dashboard. In questo modo, i dashboard diventano una "prima linea di difesa" che offre prestazioni coerenti con un minor carico sulla capacità. Gli utenti possono comunque fare clic su un report per analizzare i dettagli.

Per DirectQuery e i set di dati di connessioni dinamiche, la cache viene aggiornata su base periodica tramite l'esecuzione di query sull'origine dati. Per impostazione predefinita, questo aggiornamento viene eseguito ogni ora, anche se è possibile configurare una frequenza diversa nelle impostazioni del set di dati. Ogni aggiornamento della cache invia query all'origine dati sottostante. Il numero di query generate dipende dal numero di oggetti visivi aggiunti ai dashboard che si basano sull'origine dati. Tenere presente che se è abilitata la sicurezza a livello di riga, vengono generate query per ogni contesto di sicurezza diverso. Si consideri, ad esempio, l'esistenza di due ruoli diversi per la categorizzazione degli utenti con due visualizzazioni diverse dei dati. Durante l'aggiornamento della cache di query, Power BI genera due set di query.

### <a name="power-bi-reports"></a>Report di Power BI

Per l'ottimizzazione delle progettazioni dei report di Power BI è possibile seguire diversi consigli.

> [!NOTE]
> Se i report si basano su un set di dati DirectQuery, per altre ottimizzazioni della progettazione dei report vedere [Linee guida per il modello DirectQuery in Power BI Desktop (ottimizzare le progettazioni di report)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Applicare i filtri più restrittivi

Maggiore è il numero dei dati da visualizzare in un oggetto visivo, più lento sarà il caricamento dell'oggetto stesso. Sebbene questo principio possa sembrare ovvio, spesso lo si dimentica. Si supponga ad esempio di avere un set di dati di grandi dimensioni. Su questo set di dati si crea un report con una tabella. Gli utenti finali usano i filtri dei dati nella pagina per visualizzare le righe volute, in genere qualche decina.

Un errore comune è lasciare la visualizzazione predefinita della tabella non filtrata, ovvero con oltre 100 milioni di righe. I dati di queste righe vengono caricati nella memoria e decompressi a ogni aggiornamento, provocando una notevole richiesta di memoria. Soluzione: usare il filtro "Primi N" per ridurre il numero massimo di elementi visualizzati dalla tabella. È possibile impostare il numero massimo di elementi su un valore maggiore rispetto a quello necessario per gli utenti, ad esempio 10.000. L'esperienza dell'utente finale non cambia, ma l'uso della memoria diminuisce in modo significativo e, soprattutto, le prestazioni migliorano.

Un approccio di progettazione simile a quello precedente è consigliato per ogni oggetto visivo del report. È importante chiedersi se tutti i dati presenti nell'oggetto visivo sono effettivamente necessari e se è possibile filtrare la quantità di dati visualizzati nell'oggetto visivo con un impatto minimo sull'esperienza dell'utente finale. Si ricordi che le tabelle, in particolare, possono far uso di una quantità considerevole di memoria.

#### <a name="limit-visuals-on-report-pages"></a>Limitare gli oggetti visivi nelle pagine dei report

Il principio precedente si applica allo stesso modo al numero di oggetti visivi aggiunti a una pagina di un report. È consigliabile limitare il numero di oggetti visivi in una pagina di report specifica al minimo necessario. Le [pagine drill-through](report-drillthrough.md) e le [descrizioni comando delle pagine dei report](report-page-tooltips.md) sono un'ottima soluzione per offrire dettagli aggiuntivi senza sovraccaricare la pagina di oggetti visivi.

#### <a name="evaluate-custom-visual-performance"></a>Valutare le prestazioni degli oggetti visivi

Assicurarsi di testare ogni oggetti visivo personalizzato per garantirne le prestazioni elevate. Gli oggetti visivi di Power BI non ottimizzati possono influire negativamente sulle prestazioni dell'intero report.

### <a name="power-bi-paginated-reports"></a>Report impaginati di Power BI

È possibile ottimizzare le progettazioni di report impaginati di Power BI applicando le procedure consigliate di progettazione al recupero dati dei report. Per altre informazioni, vedere [Linee guida per il recupero dei dati per i report impaginati](report-paginated-data-retrieval.md).

Assicurarsi anche che nella capacità sia allocata memoria sufficiente al [carico di lavoro dei report impaginati](../service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Ottimizzazione dell'ambiente

È possibile ottimizzare l'ambiente Power BI configurando le impostazioni di capacità, ridimensionando i gateway dati e riducendo la latenza di rete.

### <a name="capacity-settings"></a>Impostazioni di capacità

Se si usano le capacità dedicate, disponibili con Power BI Premium (SKU P) o Power BI Embedded (SKU A, A4-A6), è possibile gestire le impostazioni di capacità. Per altre informazioni, vedere [Gestione delle capacità Premium](../service-premium-capacity-manage.md). Per indicazioni su come ottimizzare la capacità, vedere [Ottimizzare le capacità Premium](../service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Ridimensionamento del gateway

Un gateway è necessario ogni volta che Power BI deve accedere a dati non accessibili direttamente tramite Internet. È possibile installare un [gateway dati locale](../service-gateway-onprem.md) in un server locale o in un'infrastruttura IaaS (Infrastructure-as-a-Service) ospitata in una macchina virtuale.

Per comprendere i carichi di lavoro del gateway e per consigli sul ridimensionamento, vedere [Ridimensionamento del gateway dati locale](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Latenza di rete

La latenza di rete può influire sulle prestazioni dei report allungando i tempi necessari alle richieste per raggiungere il servizio Power BI e per restituire le risposte. I tenant in Power BI sono assegnati a un'area specifica.

> [!TIP]
> Per determinare la posizione del tenant, vedere [Dove si trova il tenant di Power BI?](../service-admin-where-is-my-tenant-located.md)

Quando gli utenti in un tenant accedono al servizio Power BI, le richieste vengono sempre indirizzate a quest'area. Quando le richieste raggiungono il servizio Power BI, il servizio può inviare richieste aggiuntive, ad esempio al gateway dati o all'origine dati sottostante, a loro volta soggette alla latenza di rete.

Alcuni strumenti, come il [test di velocità di Azure](https://azurespeedtest.azurewebsites.net/), forniscono un'indicazione della latenza di rete tra il client e l'area di Azure. In generale, per ridurre al minimo l'impatto della latenza di rete, cercare di tenere le origini dati, i gateway e il cluster di Power BI il più vicini possibile. Preferibilmente all'interno della stessa area. Se la latenza di rete costituisce un problema, provare a cambiare l'area di gateway e origini dati posizionandoli in macchine virtuali ospitate nel cloud in un'area più vicina al cluster di Power BI.

## <a name="monitoring-performance"></a>Monitoraggio delle prestazioni

È possibile monitorare le prestazioni del server per identificare colli di bottiglia. Le query o gli oggetti visivi con esecuzione lenta dovranno essere sottoposti a un'ottimizzazione continua. Il monitoraggio può essere eseguito in fase di progettazione in Power BI Desktop o in carichi di lavoro di produzione in capacità Power BI Premium. Per altre informazioni, vedere [Monitorare le prestazioni dei report in Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su questo articolo, vedere le risorse seguenti:

- [Linee guida per Power BI](index.yml)
- [Monitoraggio delle prestazioni dei report](monitor-report-performance.md)
- White paper: [Pianificazione della distribuzione aziendale di Power BI](https://go.microsoft.com/fwlink/?linkid=2057861)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
- Se si hanno suggerimenti, [Contribuire con idee per migliorare Power BI](https://ideas.powerbi.com/)
