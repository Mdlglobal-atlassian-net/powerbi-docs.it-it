---
title: Monitorare le capacità di Power BI Premium nell'organizzazione
description: Usare il portale di amministrazione di Power BI e l'app Power BI Premium Capacity Metrics
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/26/2018
LocalizationGroup: Premium
ms.openlocfilehash: 069a7d6c6d1503dd207eea9208f90d70e9ca1264
ms.sourcegitcommit: 8138220c42606069e2f5f97c6e4d29888dbdd036
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47420701"
---
# <a name="monitor-power-bi-premium-and-power-bi-embedded-capacities"></a>Monitorare le capacità di Power BI Premium e Power BI Embedded

Questo articolo offre una panoramica del monitoraggio delle metriche per le capacità di Power BI Premium. L'utilizzo del monitoraggio delle capacità consente di adottare un approccio informato per gestire le capacità.

È possibile monitorare la capacità con l'app Power BI Premium Capacity Metrics o nel portale di amministrazione. È consigliata l'app perché offre molti più dettagli, ma questo articolo descrive entrambe le opzioni.

## <a name="install-the-premium-capacity-metrics-app"></a>Installare l'app Premium Capacity Metrics

È possibile passare direttamente all'[app Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) o installarla come per le altre app in Power BI.

1. In Power BI fare clic su **App**.

    ![Passare ad App](media/service-admin-premium-monitor-capacity/apps.png)

2. Sul lato destro fare clic su **Get apps** (Ottieni app).

3. Nella categoria **Apps** (App) cercare **app Power BI Premium Capacity Metrics**.

4. Eseguire la sottoscrizione per installare l'app.

Dopo aver installato l'app, è possibile visualizzare le metriche sulle capacità all'interno dell'organizzazione. Di seguito vengono descritte alcune delle principali metriche disponibili.

## <a name="use-the-metrics-app"></a>Usare l'app per le metriche

Quando si apre l'app, viene prima di tutto visualizzato un dashboard con un riepilogo di tutte le capacità per cui si hanno diritti di amministratore.

![Dashboard dell'app per le metriche](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Il report ha tre schede, che verranno descritte più dettagliatamente nelle sezioni seguenti.

* **Filters applied to all pages** (Filtri applicati a tutte le pagine): consente di filtrare le altre pagine del report in base a una capacità specifica.
* **Datasets** (Set di dati): visualizza metriche dettagliate sull'integrità dei set di dati all'interno delle capacità.
* **System** (Sistema): visualizza metriche di capacità complessive, ad esempio metriche di utilizzo elevato della CPU e della memoria. 

### <a name="filters-applied-to-all-pages-tab"></a>Scheda Filters applied to all pages (Filtri applicati a tutte le pagine)

La scheda **Filters applied to all pages** (Filtri applicati a tutte le pagine) consente di selezionare una capacità, un set di dati e un intervallo di date negli ultimi sette giorni. I filtri vengono quindi applicati a tutte le pagine e a tutti i riquadri del report. Se non viene selezionato alcun filtro, per impostazione predefinita il report visualizza le metriche della settimana precedente per ogni capacità di cui si ha la proprietà.

![Scheda Filters (Filtri)](media/service-admin-premium-monitor-capacity/filters-tab.png)

### <a name="datasets-tab"></a>Scheda Set di dati

La scheda **Datasets** (Set di dati) rende disponibile la maggior parte delle metriche nell'app. Usare i quattro pulsanti nella parte superiore della scheda per passare ad aree diverse: **Summary** (Riepilogo), **Refreshes** (Aggiornamenti), **Queries** (Query) e **Datasets** (Set di dati).

![Scheda Set di dati](media/service-admin-premium-monitor-capacity/datasets-tab.png)

#### <a name="summary-area"></a>Area Summary (Riepilogo)

![Pulsante Summary (Riepilogo)](media/service-admin-premium-monitor-capacity/summary-button.png)

L'area **Summary** (Riepilogo) presenta una visualizzazione delle capacità per entità, risorse di sistema e carichi di lavoro dei set di dati.

| | **Metriche** |
| --- | --- |
| **Entities** (Entità) | * Numero di capacità di cui si è proprietari<br> * Numero di set di dati nella capacità<br> * Numero di aree di lavoro nella capacità |
| **System** (Sistema) | * Utilizzo medio della memoria in GB negli ultimi sette giorni<br> * Utilizzo massimo della memoria in GB nel corso degli ultimi sette giorni e l'ora locale in cui si è verificato<br> * Numero di volte in cui la CPU ha superato l'80% delle soglie negli ultimi sette giorni, suddiviso in bucket di tre minuti<br> * La maggior parte delle volte in cui la CPU ha superato l'80% negli ultimi sette giorni, suddivise in bucket di un'ora e l'ora locale in cui si è verificato l'evento<br> * Numero di volte in cui le connessioni DirectQuery/dinamiche hanno superato l'80% delle soglie negli ultimi sette giorni, suddiviso in bucket di tre minuti<br> * La maggior parte delle volte in cui le connessioni DirectQuery/dinamiche hanno superato l'80% negli ultimi sette giorni, suddivise in bucket di un'ora e l'ora locale in cui si è verificato l'evento |
| **Dataset Workloads** (Carichi di lavoro dei set di dati) | * Numero totale di aggiornamenti negli ultimi sette giorni<br> * Numero totale di aggiornamenti riusciti negli ultimi sette giorni<br> * Numero totale di aggiornamenti non riusciti negli ultimi sette giorni<br> * Numero totale di aggiornamenti non riusciti a causa di memoria insufficiente<br> * La durata media degli aggiornamenti viene misurata in minuti, il tempo impiegato per completare l'operazione<br> * Il tempo di attesa medio degli aggiornamenti viene misurato in minuti, il ritardo medio tra l'ora pianificata e l'inizio dell'operazione<br> * Numero totale di query eseguite negli ultimi sette giorni<br> * Numero totale di query completate negli ultimi sette giorni<br> * Numero totale di query non riuscite negli ultimi sette giorni<br> * La durata media delle query viene misurata in minuti, il tempo impiegato per completare l'operazione<br> * Numero totale di modelli rimossi a causa di un utilizzo elevato della memoria |
|  |  |

#### <a name="refreshes-area"></a>Area Refreshes (Aggiornamenti)

![Pulsante Refreshes (Aggiornamenti)](media/service-admin-premium-monitor-capacity/refreshes-button.png)

L'area **Refreshes** (Aggiornamenti) elenca gli aggiornamenti completati, le misure con esito positivo, il tempo di attesa medio/massimo degli aggiornamenti e la durata media/massima degli aggiornamenti suddivisi in base ai set di dati negli ultimi sette giorni. I due grafici in basso mostrano gli aggiornamenti in rapporto all'utilizzo della memoria in GB e i tempi di attesa medi suddivisi in bucket di un'ora, indicati nell'ora locale. I grafici a barre superiori elencano i primi cinque set di dati in base al tempo medio impiegato per completarne l'aggiornamento (durata dell'aggiornamento), nonché il tempo di attesa medio per l'aggiornamento. La presenza di più picchi elevati per i tempi di attesa degli aggiornamenti è indicativa di un livello di utilizzo molto alto della capacità.

#### <a name="queries-area"></a>Area Queries (Query)

![Pulsante Queries (Query)](media/service-admin-premium-monitor-capacity/queries-button.png)

L'area **Queries** (Query) elenca il numero totale di query eseguite, il numero totale di query in attesa per le query dinamiche e le query dirette, la durata media e massima, il tempo medio e massimo di attesa espresso in millisecondi. Questi dati sono suddivisi per set di dati, area di lavoro e bucket orari negli ultimi sette giorni. I grafici nella parte inferiore illustrano il numero delle query, la durata media (in millisecondi) e il tempo di attesa (in millisecondi) rispetto al consumo di memoria in GB. Questi dati sono suddivisi in bucket di un'ora nell'ora locale. I due grafici superiori a destra elencano i primi cinque set di dati per durata media delle query e tempo di attesa per il completamento di queste. Una durata notevole delle query e tempi di attesa lunghi sono indicativi di un livello di utilizzo molto alto della capacità. Questi sintomi possono indicare anche che il problema è causato da un unico set di dati e che è necessario indagarne le cause.

#### <a name="datasets-area"></a>Area Datasets (Set di dati)

![Pulsante Datasets (Set di dati)](media/service-admin-premium-monitor-capacity/datasets-button.png)

L'area **Datasets** (Set di dati) visualizza i set di dati completi rimossi a causa di un utilizzo elevato della memoria su base oraria.

### <a name="system-tab"></a>Scheda System (Sistema)

La scheda **System** (Sistema) visualizza informazioni sull'utilizzo elevato della CPU (numero di volte in cui l'utilizzo ha superato l'80%), nonché sull'utilizzo elevato di connessioni di query dirette/dinamiche e sull'utilizzo della memoria.

![Report sul sistema Premium](media/service-admin-premium-monitor-capacity/system-tab.png)

## <a name="monitor-power-bi-embedded-capacity"></a>Monitorare la capacità di Power BI Embedded

È anche possibile usare l'app Power BI Premium Capacity Metrics per monitorare le capacità dello *SKU A* in Power BI Embedded. Tali capacità verranno visualizzate nel report per gli amministratori della capacità. Tuttavia, l'aggiornamento del report ha esito negativo a meno che non si concedano autorizzazioni specifiche a Power BI per gli SKU A:

1. Aprire la capacità nel portale di Azure.
1. Fare clic su **Controllo di accesso (IAM)** e aggiungere l'app "Power BI Premium" al ruolo lettore. Se non si riesce a trovare l'app in base al nome, è possibile aggiungerla anche in base al relativo ID client: cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Autorizzazioni per Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> È possibile monitorare l'utilizzo della capacità di Power BI Embedded nell'app o nel portale di Azure, ma non nel portale di amministrazione di Power BI.

## <a name="basic-monitoring-in-the-admin-portal"></a>Monitoraggio di base nel portale di amministrazione

L'area **Impostazioni di capacità** del portale di amministrazione fornisce quattro misuratori che indicano i carichi e le risorse utilizzate dalla capacità per gli ultimi sette giorni. Questi quattro riquadri mostrano le informazioni su base oraria e indicano il numero di ore negli ultimi sette giorni in cui la metrica corrispondente è stata superiore all'80%. Questa metrica indica una potenziale riduzione delle prestazioni per l'esperienza utente finale.

![Utilizzo nei 7 giorni](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Metrica** | **Descrizione** |
| --- | --- |
| CPU |Numero di volte per cui la CPU supera l'80% di uso. |
| Thrashing di memoria |Rappresenta l'uso elevato di memoria nei core di back-end. In particolare registra la frequenza con cui i set di dati vengono rimossi dalla memoria a causa dell'uso elevato di memoria, dovuto alla gestione di più set di dati. |
| Utilizzo memoria |Uso medio della memoria, specificato in gigabyte (GB). |
| DQ/s | Numero di volte per il quale il conteggio di DirectQuery e connessioni dinamiche ha superato l'80% del limite. <br> * Il numero totale di DirectQuery e di query di connessione dinamica al secondo è limitato. * I limiti sono 30/s per P1, 60/s per P2 e 120/s per P3. * Il numero di DirectQuery e il numero di query di connessione dinamica contribuiscono a questa limitazione. Ad esempio, se si hanno 15 DirectQuery e 15 connessioni dinamiche in un secondo, si raggiunge il limite<br>* Questo vale per le connessioni sia in che nel cloud. |
|  |  |

Le metriche riflettono l'uso nell'ultima settimana.  Per aprire una visualizzazione più dettagliata delle metriche, fare clic su uno dei riquadri di riepilogo.  Vengono visualizzati grafici dettagliati per ogni metrica della capacità Premium. Il grafico seguente mostra i dettagli per la metrica della CPU.

![Grafico d'uso dettagliato - CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Questi grafici sono un riepilogo su base oraria dell'ultima settimana e facilitano il rilevamento di eventi specifici associati alle prestazioni nella capacità Premium.

È anche possibile esportare i dati corrispondenti a qualsiasi metrica in un file con estensione csv.  Questa esportazione fornisce informazioni dettagliate con intervalli di tre minuti per ogni giorno della settimana precedente.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere appreso come monitorare le capacità di Power BI Premium, è possibile consultare informazioni su come ottimizzare le capacità.

> [!div class="nextstepaction"]
> [Ottimizzazione e gestione delle risorse della capacità Power BI Premium](service-premium-understand-how-it-works.md)
