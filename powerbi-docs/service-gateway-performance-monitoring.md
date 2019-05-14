---
title: Prestazioni del gateway monitoring (anteprima pubblica)
description: Questo articolo fornisce informazioni sul monitoraggio delle prestazioni delle attività gateway dati locale.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535368"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Prestazioni del gateway monitoring (anteprima pubblica)

Per monitorare le prestazioni, gli amministratori del gateway sono in genere dipendono manualmente il monitoraggio dei contatori delle prestazioni tramite lo strumento Windows Performance Monitor. Offriamo ora la registrazione delle query aggiuntive e una [file di modello di Gateway prestazioni PBI](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) per visualizzare i risultati. Questa funzionalità offre nuovi approfondimenti nell'utilizzo del gateway e consente di risolvere i problemi di query con prestazioni ridotte.

> [!NOTE]
> Questa funzionalità è attualmente disponibile solo per il gateway dati locale in modalità standard e non per la modalità personale.

## <a name="enable-performance-logging"></a>Abilitare la registrazione delle prestazioni

Per abilitare questa funzionalità, apportare le modifiche seguenti per il *gatewaycore* del file nei "\Program Files\On-del gateway dati locale" cartella:

1. Update **QueryExecutionReportOn** al _True_ per abilitare la registrazione aggiuntiva per le query eseguite tramite il gateway. L'abilitazione di questa opzione consente di creare Report di esecuzione di Query sia i file di rapporto di aggregazione l'esecuzione di Query.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Update **SystemCounterReportOn** al _True_ per abilitare la registrazione aggiuntiva per i contatori di sistema della CPU e memoria. L'abilitazione di questa opzione consente di creare il file di rapporto di aggregazione del contatore di sistema.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Sono presenti altri valori nel file di configurazione che è possibile aggiornare in base alle esigenze.

    - **ReportFilePath**: Determina il percorso in cui sono archiviati i tre file di log. Per impostazione predefinita, questo percorso è "\Users\PBIEgwService\AppData\Local\Microsoft\On-premises dati gateway\Report" o "Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On-premises data gateway\Report", a seconda della versione del sistema operativo. Se si usa un account del servizio per il gateway diverso da _PBIEgwService_, sostituire questa parte del percorso con il nome dell'account del servizio.
    - **ReportFileCount**: Determina il numero di file di log di ogni tipo da mantenere. Il valore predefinito è 10.
    - **ReportFileSizeInBytes**: Determina le dimensioni del file da mantenere. Il valore predefinito è 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Determina il numero di minuti per il quale viene aggregate le informazioni sull'esecuzione di query. Il valore predefinito è 5.
    - **SystemCounterAggregationTimeInMinutes**: Determina il numero di minuti per cui vengono aggregati i contatori di sistema. Il valore predefinito è 5.

1. Dopo aver apportato le modifiche apportate al file di configurazione, riavviare il gateway per questi valori di configurazione rendere effettive. A questo punto verranno visualizzati i file di report generati nel percorso specificato per **ReportFilePath**.

    > [!NOTE]
    > Può richiedere fino a 10 minuti oltre l'intervallo di tempo impostato per **QuerExecutionAggregationTimeInMinutes** nel file di configurazione fino a quando i file di avvio visualizzata nella cartella.

## <a name="understand-performance-logs"></a>Comprendere i registri di prestazioni

Quando si attiva questa funzionalità, abbiamo creare tre nuovi file di log:

- Il Report di esecuzione di Query
- Il rapporto di aggregazione di esecuzione di Query
- Il rapporto di aggregazione di contatore di sistema

Il Report di esecuzione di Query contiene informazioni sull'esecuzione di query dettagliate. Per realizzare gli attributi seguenti:

|Attributo |Descrizione |
| ---- | ---- |
|**GatewayObjectId** |Identificatore univoco per il gateway. |
|**RequestId** |Identificatore univoco per una richiesta del gateway. È possibile lo stesso per più query. |
|**DataSource** |Contiene il tipo di origine dati e origine dati. |
|**QueryTrackingId** |Identificatore univoco per una query. |  
|**QueryExecutionEndTimeUTC** |Ora di completamento dell'esecuzione della query. |
|**QueryExecutionDuration**(ms) |Durata di esecuzione di una query. |
|**QueryType** |Tipo di query: ad esempio, la query passata è un aggiornamento di Power BI/DirectQuery o le query da PowerApps e Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Ora quando le attività di elaborazione dei dati, ad esempio lo spooling, il recupero dei dati, la compressione, l'elaborazione dati e così via completata. |
|**DataProcessingDuration**(ms) |Durata per le attività di elaborazione dei dati, come lo spooling, il recupero dei dati, la compressione, l'elaborazione dati e così via. |
|**Operazione riuscita** |Indica se la query ha avuto esito positivo o negativo. |
|**ErrorMessage** |Se la query non riuscita, indica il messaggio di errore. |
| | |

Il rapporto di aggregazione di esecuzione di Query contiene informazioni sulle query aggregati in un intervallo di tempo dal **GatewayObjectId**, **DataSource**, **successo**e **QueryType**. Il valore predefinito è 5 minuti, ma è possibile modificarlo come descritto di seguito. Per realizzare gli attributi seguenti:

|Attributo |Descrizione |
| ---- | ---- |
|**GatewayObjectId** |Identificatore univoco per il gateway. |
|**AggregationStartTimeUTC** |Inizio del periodo di tempo per cui sono stati aggregati query sugli attributi. |
|**AggregationEndTimeUTC** |Fine del periodo di tempo per la query che sono stati aggregati gli attributi. |
|**DataSource** |Contiene il tipo di origine dati e origine dati. |
|**Operazione riuscita** |Indica se la query ha avuto esito positivo o negativo. |
|**AverageQueryExecutionDuration**(ms) |Media di tempo di esecuzione di query per l'intervallo di tempo di aggregazione. |
|**MaxQueryExecutionDuration**(ms) |Tempo di esecuzione massimo per le query per l'intervallo di tempo di aggregazione. |
|**MinQueryExecutionDuration**(ms) |Tempo di esecuzione minima per le query per l'intervallo di tempo di aggregazione. |
|**QueryType** |Tipo di query: ad esempio, la query passata è un aggiornamento di Power BI/DirectQuery o le query da PowerApps e Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Tempo medio per le attività di elaborazione dei dati come lo spooling, il recupero dei dati, la compressione, l'elaborazione dei dati, e così via per l'intervallo di tempo di aggregazione. |
|**MaxDataProcessingDuration**(ms) |Tempo massimo per l'intervallo di tempo di aggregazione per le attività di elaborazione dei dati come lo spooling, il recupero dei dati, la compressione, l'elaborazione dati e così via. |
|**MinDataProcessingDuration**(ms) |Tempo minimo per l'intervallo di tempo di aggregazione per le attività di elaborazione dei dati come lo spooling, il recupero dei dati, la compressione, l'elaborazione dati e così via. |
|**Conteggio** |Numero di query. |
| | |

Il rapporto di aggregazione di contatore di sistema contiene i valori dei contatori del sistema aggregati in un intervallo di tempo. Il valore predefinito è 5 minuti, ma è possibile modificarlo come descritto di seguito. Per realizzare gli attributi seguenti:

|Attributo |Descrizione |
| ---- | ---- |
|**GatewayObjectId** |Identificatore univoco per il gateway. |
|**AggregationStartTimeUTC** |Inizio del periodo di tempo per cui sono stati aggregati contatori del sistema. |
|**AggregationEndTimeUTC** |Fine del periodo di tempo per cui system contatori sono stati aggregati. |
|**CounterName** |Contatori di sistema, tra cui utilizzo della memoria e CPU da parte del gateway, creare mashup e globale da un computer che ospita il gateway. |
|**Max** |Valore massimo per il contatore di sistema per l'intervallo di tempo di aggregazione. |
|**Min** |Valore minimo per il contatore di sistema per l'intervallo di tempo di aggregazione. |
|**Media** |Valore medio per il contatore di sistema per l'intervallo di tempo di aggregazione. |
| | |

## <a name="visualize-gateway-performance"></a>Visualizzare le prestazioni del gateway

A questo punto, è possibile visualizzare i dati nei file di log.

1. Scaricare il [modello di Gateway prestazioni PBI](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) e aprirlo con Power BI desktop.

1. Nella finestra di dialogo visualizzata, verificare che il percorso della cartella corrisponde al valore nella **ReportFilePath**.

    ![Finestra popup per il percorso della cartella](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Selezionare **carico**, e il file del modello viene avviato il caricamento dei dati dai file di log. Tutti gli oggetti visivi devono quindi essere popolati usando i dati nei report.

1. Facoltativamente, salvare questo file come un file PBIX e pubblicarlo nel servizio per gli aggiornamenti automatici.

Inoltre, è possibile personalizzare questo file di modello in base alle esigenze. Per altre informazioni sui modelli di Power BI, vedere questo [post di Blog di Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).