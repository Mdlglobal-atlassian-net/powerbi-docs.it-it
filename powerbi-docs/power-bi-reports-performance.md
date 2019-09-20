---
title: Procedure consigliate per le prestazioni di Power BI
description: Questo articolo fornisce indicazioni per creare report veloci e affidabili in Power BI
author: Bhavik-MSFT
ms.author: bhmerc
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/30/2018
LocalizationGroup: Reports
ms.openlocfilehash: 736c1ee1b1998ec7f991167352313a05061b3f3c
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841494"
---
# <a name="power-bi-performance-best-practices"></a>Procedure consigliate per le prestazioni di Power BI

Questo articolo offre indicazioni per creare report veloci e affidabili in Power BI.  

## <a name="choose-an-appropriate-storage-mode-import-directquery"></a>Scegliere una modalità di archiviazione appropriata: importazione, DirectQuery

Nella maggior parte dei casi la modalità di importazione è la scelta migliore poiché offre la massima velocità sfruttando i dati memorizzati in locale nella cache compressi con l'archiviazione a colonne. La modalità di importazione consente anche la funzionalità DAX completa. Valutare DirectQuery (e i modelli compositi) quando il volume dei dati di origine è troppo grande per adattarsi alla capacità di Power BI. DirectQuery è utile anche quando è necessario recuperare i dati più recenti dall'origine ogni volta che viene caricato un report. Se non si hanno questi requisiti e gli utenti devono solo visualizzare i dati aggiornati qualche volta al giorno o meno (ad esempio, da un data warehouse aziendale), è consigliabile usare l'importazione. In modalità DirectQuery, gli utenti possono provare ad aggiornare il report senza rendersi conto di recuperare esattamente gli stessi dati dall'origine.      

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Usare i filtri per limitare gli oggetti visivi nei report e visualizzare solo gli elementi necessari 

Maggiore è il numero dei dati da visualizzare in un oggetto visivo, più lento sarà il caricamento dell'oggetto stesso. Sebbene questo principio possa sembrare ovvio, spesso lo si dimentica. Si supponga ad esempio di avere un set di dati di grandi dimensioni. su cui si crea un report con una tabella della tabella. Gli utenti finali usano i filtri dei dati nella pagina per visualizzare le righe desiderate, in genere qualche decina.

Un errore comune è lasciare la visualizzazione predefinita della tabella non filtrata, ovvero con oltre 100 milioni di righe. I dati di queste righe vengono caricati nella memoria e decompressi a ogni aggiornamento, provocando un notevole sovraccarico della memoria. Soluzione: usare il filtro "Primi N" per ridurre il numero massimo di elementi visualizzati dalla tabella. È possibile impostare il numero massimo di elementi su un valore maggiore rispetto a quello necessario per gli utenti, ad esempio 10.000. L'esperienza dell'utente finale non cambia, ma l'uso della memoria diminuisce in modo significativo e le prestazioni migliorano.

Un approccio simile a quello precedente è consigliato per tutti gli oggetti visivi dei report. È importante chiedersi se tutti i dati presenti nell'oggetto visivo sono effettivamente necessari e se è possibile filtrare la quantità di dati visualizzati nell'oggetto visivo con un impatto minimo sull'esperienza dell'utente finale. Le tabelle, in particolare, possono far uso di una quantità considerevole di memoria.

## <a name="limit-visuals-on-report-pages"></a>Limitare gli oggetti visivi nelle pagine dei report

Il principio precedente si applica allo stesso modo al numero di oggetti visivi in un report specifico. È consigliabile limitare il numero di oggetti visivi in un report specifico al minimo necessario. Le pagine drill-through sono un'ottima soluzione per fornire dettagli aggiuntivi senza sovraccaricare il report di oggetti visivi.  

## <a name="optimize-your-model"></a>Ottimizzare il modello

Procedure consigliate:

- Rimuovere le tabelle o le colonne inutilizzate, dove possibile. 
- Evitare valori Distinct Count nei campi con cardinalità elevata, ovvero con milioni di valori distinti.  
- Evitare di usare campi con precisione non necessaria e cardinalità elevata. È possibile ad esempio dividere valori datetime univoci in colonne separate, come mese, anno, data e così via. In alternativa, nei campi con precisione elevata usare l'arrotondamento per ridurre la cardinalità, ad esempio 13,29889 -> 13,3, se possibile.
- Usare valori integer anziché stringhe, se possibile.
- Prestare attenzione alle funzioni DAX, che devono testare ogni riga in una tabella, ad esempio RANKX. Nel peggiore dei casi, queste funzioni possono aumentare in modo esponenziale i requisiti di runtime e memoria a causa degli aumenti lineari nelle dimensioni della tabella.
- Quando ci si connette alle origini dati tramite DirectQuery, è consigliabile indicizzare le colonne a cui in genere viene applicato il filtro o il sezionamento. L'indicizzazione migliora notevolmente la velocità di risposta del report.  

Per altre informazioni su come ottimizzare le origini dati per DirectQuery, vedere [DirectQuery in SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/).

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery e connessione dinamica: informazioni sulle prestazioni dell'origine dati sottostante

Nel caso di DirectQuery o delle connessioni dinamiche, quando gli utenti visitano un report di Power BI, Power BI invia query in tempo reale all'origine dati sottostante. Dopo che l'origine dati viene restituita con i dati della query, viene eseguito il rendering del report. Di conseguenza, le prestazioni del report dipendono in gran parte dalle prestazioni dell'origine dati sottostante.

In questi casi è importante determinare le prestazioni dell'origine dati sottostante. Per ogni origine dati sono disponibili strumenti diversi per stabilire le prestazioni delle query. Ad esempio, in SQL Server e Azure SQL è disponibile Query Store, che acquisisce una cronologia delle query e le statistiche di runtime corrispondenti.

Quando si distribuiscono report di Power BI basati su DirectQuery e sulla connessione dinamica, provare le operazioni che gli utenti finali eseguiranno in Power BI Desktop. Se il caricamento del report è lento in Power BI Desktop, è probabile che anche il caricamento nel servizio sia lento per gli utenti finali. 

## <a name="directquery-best-practices"></a>Procedure consigliate per DirectQuery

La sezione seguente descrive le procedure consigliate generali per la connessione tramite DirectQuery.

### <a name="db-design-guidance"></a>Indicazioni per la progettazione del database

- Inserire le colonne calcolate e le misure nell'origine, dove possibile. Maggiore è la vicinanza all'origine, maggiore è la probabilità di prestazioni.
- Ottimizzare Provare a determinare i piani di esecuzione delle query, aggiungere indici per le colonne filtrate di frequente e così via.

### <a name="modeling-guidance"></a>Indicazioni per la modellazione

- Partire da Power BI Desktop.
- Evitare query complesse nell'editor di query.
- Non usare filtri data relativi in Editor di query.  
- Mantenere le misure inizialmente semplici e aggiungere complessità in modo incrementale.
- Evitare le relazioni su colonne calcolate e colonne di identificatori univoci.
- Provare a impostare l'opzione "Considera integrità referenziale" sulle relazioni. Nella maggior parte dei casi, tale impostazione consente di migliorare le prestazioni in modo significativo.  

### <a name="general"></a>Generale

- Applicare prima i filtri.
- Provare a disattivare l'interazione tra oggetti visivi per ridurre il carico della query nelle operazioni di evidenziazione incrociata degli utenti.
- Limitare il numero di oggetti visivi e di dati per oggetto visivo, come descritto in precedenza.
- L'applicazione della sicurezza a livello di riga può comportare un notevole miglioramento delle prestazioni. Assicurarsi di testare i diversi ruoli di sicurezza a livello di riga che usati dagli utenti.
- Il servizio impone un timeout a livello di query per garantire che le query con esecuzione prolungata non monopolizzino le risorse del sistema. Le query con una durata maggiore di 225 secondi raggiungono il timeout e restituiscono un errore a livello dell'oggetto visivo.

## <a name="understand-dashboards-and-query-caches"></a>Informazioni sulle cache di query e dashboard

Le richieste relative agli oggetti visivi aggiunti ai dashboard vengono gestite dalla cache della query quando viene caricato il dashboard. Al contrario, quando si visita un report, le query vengono inviate in tempo reale all'origine dati, ovvero il servizio Power BI (in caso di importazione) o l'origine dati specificata (nel caso di DirectQyery o connessione dinamica).  

> [!NOTE]
> Quando a un dashboard vengono aggiunti riquadri animati del report, questi non sono gestiti dalla cache della query, ma si comportano come i report e inviano le query ai core back-end in tempo reale.

Come indicato dal nome, il recupero dei dati dalla cache della query offre prestazioni migliori e più coerenti rispetto al recupero dall'origine dati. Per sfruttare al meglio questa funzionalità, è consigliabile impostare i dashboard come prima pagina di destinazione per gli utenti. Aggiungere gli oggetti visivi più richiesti e usati di frequente ai dashboard. In questo modo, i dashboard diventano una "prima linea di difesa" che offre prestazioni coerenti con un minor carico sulla capacità. Gli utenti possono comunque fare clic sul report per visualizzare i dettagli.  
 

Per DirectQuery e le connessioni dinamiche, la cache della query viene aggiornata su base periodica tramite l'esecuzione di query sull'origine dati. Per impostazione predefinita, l'aggiornamento avviene ogni ora, ma è possibile configurare il valore nelle impostazioni del set di dati. Ogni aggiornamento della cache della query invierà query all'origine dati sottostante per aggiornare la cache. Il numero di query generate dipende dal numero di oggetti visivi aggiunti ai dashboard che si basano sull'origine dati. Tenere presente che se è abilitata la sicurezza a livello di riga, vengono generate query per ogni contesto di sicurezza diverso. Se ad esempio si dispone di due ruoli diversi che categorizzano gli utenti e a cui sono associate due visualizzazioni diverse dei dati, durante l'aggiornamento della cache di query Power BI genera due set di query. 

## <a name="understand-custom-visual-performance"></a>Informazioni sulle prestazioni degli oggetti visivi 

Assicurarsi di testare ogni oggetti visivo personalizzato per garantirne le prestazioni elevate. Gli oggetti visivi personalizzati non ottimizzati possono influire negativamente sulle prestazioni dell'intero report. 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>Esaminare in modo approfondito le prestazioni delle query con SQL Profiler e Power BI Desktop

Per un esame approfondito sugli oggetti visivi che utilizzano la maggior quantità di risorse e tempo, è possibile connettere SQL Profiler a Power BI Desktop per ottenere una panoramica completa sulle prestazioni delle query.

> [!NOTE]
> Power BI Desktop supporta la connessione a una porta di diagnostica. La porta di diagnostica offre altri strumenti a cui connettersi e consente di eseguire analisi per scopi diagnostici. *Le modifiche al modello non sono supportate. Le modifiche al modello potrebbero causare danneggiamento e perdita dei dati.*

Istruzioni:
  
1. **Installare SQL Server Profiler ed eseguire Power BI Desktop**

   SQL Server Profiler è disponibile come parte di SQL Server Management Studio.

2. **Determinare la porta usata da Power BI Desktop**

   Eseguire il prompt dei comandi o PowerShell con privilegi di amministratore. Usare netstat per individuare la porta usata da Power BI Desktop per l'analisi:

   `> netstat -b -n`

   L'output sarà costituito da un elenco di applicazioni e le corrispondenti porte aperte, ad esempio:  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   Cercare la porta usata da msmdsrv.exe e prenderne nota per un secondo momento. In questo caso, si usa la porta 55786.
3. **Connettere SQL Server Profiler a Power BI Desktop**

   - Avviare SQL Server Profiler dal menu **Start**
   - **File** > **Nuova traccia**
   - Tipo di server: Analysis Services
   - Nome server: localhost:[numero di porta trovato sopra]
   - Nella schermata successiva selezionare **Esegui**
   - A questo punto, SQL Profiler è attivo ed esegue la profilatura delle query inviate da Power BI Desktop. 
   - Quando le query vengono eseguite, è possibile visualizzare la durata e i tempi di CPU. Queste informazioni consentono di determinare quali query costituiscono un collo di bottiglia.  

Con SQL Profiler è possibile identificare le query che usano il tempo di CPU più a lungo e che quindi costituiscono un collo di bottiglia per le prestazioni. Gli oggetti visivi che eseguono tali query dovranno essere sottoposti a un'ottimizzazione continua.

## <a name="gateway-best-practices"></a>Procedure consigliate per il gateway

Il gateway di gestione dati locale è un ottimo strumento per connettere il servizio Power BI ai dati locali. Allo stesso tempo, se la pianificazione non è adeguata, può trasformarsi in un collo di bottiglia per le prestazioni del report, in particolare per i set di dati DirectQuery/connessione dinamica, in cui tutte le query e le risposte delle query transitano attraverso il gateway. Di seguito sono riportate alcune procedure consigliate per garantire le prestazioni elevate dei gateway: 

- **Usare la modalità Enterprise**, rispetto alla modalità personale.
- **Specifiche hardware consigliate per il gateway**: otto core CPU, 16 GB di RAM.
- **Configurare il monitoraggio**: configurare il monitoraggio delle prestazioni nel computer del gateway per verificare l'eventuale sovraccarico del gateway ed evitare i colli di bottiglia. Per altre informazioni, vedere [Risoluzione dei problemi del gateway dati locale](service-gateway-onprem-tshoot.md).
- **Aumentare le prestazioni o il numero di istanze**: se il gateway costituisce un collo di bottiglia, provare ad aumentare le prestazioni, ovvero spostare il gateway in un computer più potente con maggiore capacità di CPU e RAM, o ad aumentare il numero di istanze, ovvero dividere i set di dati in più gateway. 
- **Separare l'importazione da DirectQuery**: se si sceglie di aumentare il numero di istanze, separare i gateway per l'importazione da quelli dedicati a DirectQuery.

## <a name="network-latency"></a>Latenza di rete

La latenza di rete può influire sulle prestazioni dei report allungando i tempi necessari alle richieste per raggiungere il servizio Power BI e per restituire le risposte. Ai tenant in Power BI è assegnata un'area specifica. Per visualizzare l'area del proprio tenant, passare a powerbi.com e selezionare **?** nell'angolo in alto a destra e quindi selezionare **Informazioni su Power BI**. Quando gli utenti in un tenant accedono al servizio Power BI, le richieste vengono sempre indirizzate a quest'area. Quando le richieste raggiungono il servizio Power BI, il servizio può inviare richieste aggiuntive, ad esempio al gateway o all'origine dati sottostante, a loro volta soggette alla latenza di rete.

Alcuni strumenti, come il [test di velocità di Azure](http://azurespeedtest.azurewebsites.net/), forniscono un'indicazione della latenza di rete tra il client e l'area di Azure. In generale, per ridurre al minimo l'impatto della latenza di rete, cercare di tenere le origini dati, i gateway e il cluster di Power BI il più vicini possibile. Se la latenza di rete costituisce un problema, provare a cambiare l'area di gateway e origini dati collocandoli in macchine virtuali in un'area più vicina al cluster di Power BI.

Per migliorare ulteriormente la latenza di rete, provare a usare [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/) che consente di creare connessioni di rete più veloci e affidabili tra i client e i data center di Azure.

## <a name="next-steps"></a>Passaggi successivi

- [Pianificazione della distribuzione aziendale di Power BI](https://aka.ms/pbienterprisedeploy), con indicazioni a tutto campo per le distribuzioni di Power BI su vasta scala
- [DirectQuery in SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] Building Fast and Reliable Reports in Power BI](https://www.youtube.com/watch?v=GhiJABR7XX0) (Creazione di report veloci e affidabili in Power BI)
- [[YouTube] Power BI Enterprise Deployments](https://www.youtube.com/watch?v=K-zEWICvICM) (Distribuzioni aziendali di Power BI)
