---
title: Usare i modelli compositi in Power BI Desktop (anteprima)
description: Creare modelli di dati con più connessioni dati e relazioni molti-a-molti in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 4e7692be8ec78c79076408635a75dbf0ab9080d2
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974047"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Modelli compositi in Power BI Desktop (anteprima)

In precedenza, quando si usava DirectQuery in un report in **Power BI Desktop**, non erano consentite altre connessioni dati se per tale report era consentita la modalità DirectQuery o Importa. Con i **modelli compositi** questa limitazione è stata eliminata e un report può includere senza problemi connessioni dati da più di una connessione dati DirectQuery o Importa, in qualsiasi combinazione scelta.

![modelli compositi in Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

La funzionalità dei **modelli compositi** in **Power BI Desktop** è costituita da tre funzionalità correlate:

* **Modelli compositi** - Consente a un report di avere più connessioni dati, tra cui connessioni DirectQuery o importazione, in qualsiasi combinazione.
* **Relazioni molti-a-molti** - Con i **modelli compositi** è possibile stabilire **relazioni molti-a-molti** tra tabelle, rimuovendo i requisiti per i valori univoci nelle tabelle e annullando soluzioni alternative precedenti, come l'introduzione di nuove tabelle solo per stabilire relazioni. 
* **Modalità di archiviazione** - È ora possibile specificare gli oggetti visivi che richiedono una query per origini dati back-end e quelli che non la richiedono vengono importati anche se basati su DirectQuery, con conseguente miglioramento delle prestazioni e riduzione del carico per il back-end. In precedenza, anche oggetti visivi semplici, come i filtri dei dati, attivavano l'invio di query alle origini di back-end. 

Questa raccolta delle tre funzionalità correlate per i **modelli compositi** è descritta in articoli separati:

* I **modelli compositi** sono descritti in dettaglio in questo articolo.
* Le **relazioni molti-a-molti** sono descritte nell'articolo specifico [Relazioni molti-a-molti in Power BI Desktop (anteprima)](desktop-many-to-many-relationships.md).
* La **modalità di archiviazione** è descritta in un articolo a parte, [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md).

## <a name="enabling-the-composite-models-preview-feature"></a>Abilitazione della funzionalità in anteprima dei modelli compositi

La funzionalità dei **modelli compositi** è disponibile in anteprima e deve essere abilitata in **Power BI Desktop**. Per abilitare i **modelli compositi**, selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità di anteprima** e quindi selezionare la casella di controllo **Modelli compositi**. 

![abilitazione delle funzionalità in anteprima](media/desktop-composite-models/composite-models_02.png)

È necessario riavviare **Power BI Desktop** per rendere effettiva la modifica.

![riavvio richiesto per rendere effettive le modifiche](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>Uso dei modelli compositi

Con i **modelli compositi** è possibile connettersi a tutti i tipi di origini dati ed effettuare tali connessioni dati in modi diversi quando si usa **Power BI Desktop** o il **servizio Power BI**. È possibile importare dati in Power BI, operazione che rappresenta il modo più comune per ottenere i dati, oppure connettersi direttamente ai dati nel relativo repository di origine tramite DirectQuery. Altre informazioni dettagliate su DirectQuery sono disponibili nell'articolo [Uso di DirectQuery in Power BI](desktop-directquery-about.md).

Quando si usa DirectQuery, con i **modelli compositi** è possibile creare un modello di Power BI (ad esempio un singolo file di Power BI Desktop con estensione pbix) che esegue le operazioni seguenti:

* Combina i dati da una o più origini DirectQuery, e/o
* Combina i dati da origini DirectQuery e dati importati

Ad esempio, con I **modelli compositi** è possibile creare un modello che combina i dati di vendita da un data warehouse aziendale con i dati sugli obiettivi di vendita in un database di SQL Server di reparto, insieme ad alcuni dati importati da un foglio di calcolo. Un modello che combina dati da più di un'origine DirectQuery o combina origini DirectQuery con dati importati è noto come *modello composito*.

> [!NOTE]
> Durante la fase di anteprima, non è possibile pubblicare modelli compositi nel servizio Power BI. 

È possibile creare relazioni tra tabelle come sempre, anche quando le tabelle provengono da origini diverse, con la restrizione seguente: le relazioni tra origini diverse devono essere definite con la cardinalità **molti-a-molti**, indipendentemente dalla cardinalità effettiva. Il comportamento per queste relazioni è quindi uguale al normale per le relazioni **molti-a-molti**, come descritto in [Relazioni molti-a-molti in Power BI Desktop (anteprima)](desktop-many-to-many-relationships.md). Si noti che nel contesto dei modelli compositi, tutte le tabelle importate rappresentano in effetti una singola origine, indipendentemente dall'effettiva origine dati sottostante da cui vengono importate.   

## <a name="example-of-using-composite-models"></a>Esempio di uso dei modelli compositi

Come esempio di un **modello composito**, si consideri un report connesso a un data warehouse aziendale (in SQL Server) con DirectQuery, in cui il data warehouse contiene dati *Sales by Country*, *Quarter* e *Bike (Product)*, come illustrato nell'immagine seguente.

![visualizzazione delle relazioni per i modelli compositi](media/desktop-composite-models/composite-models_04.png)

A questo punto è possibile creare oggetti visivi semplici usando i campi dall'origine. Ad esempio, l'oggetto visivo seguente mostra l'importo delle vendite totale per *ProductName*, per un trimestre selezionato. 

![oggetto visivo basato sui dati](media/desktop-composite-models/composite-models_05.png)

Ma se invece fossero disponibili informazioni sul Product Manager assegnato a ogni prodotto, insieme alla priorità per il marketing, in forma di dati mantenuti aggiornati in un foglio di calcolo di Excel? Potrebbe essere utile visualizzare i valori *Sales Amount* in base a *Product Manager* e allo stesso tempo aggiungere questi dati locali al data warehouse aziendale probabilmente potrebbe non essere fattibile o nella migliore delle ipotesi richiederebbe mesi. Sebbene sia possibile importare i dati di vendita dal data warehouse (anziché tramite DirectQuery), e a questo punto potrebbero essere combinati con i dati importati dal foglio di calcolo, tale approccio non è ragionevole a causa di motivi che hanno portato prima di tutto a usare DirectQuery, come una qualche combinazione di regole di sicurezza applicata nell'origine sottostante, la necessità di essere in grado di visualizzare i dati più recenti e le dimensioni estese dei dati. 

Questi sono le scenari in cui entrano in gioco i **modelli compositi**. I modelli compositi offrono la possibilità di connettersi al data warehouse usando DirectQuery e quindi anche di usare GetData per le origini aggiuntive. In questo caso viene stabilita la connessione DirectQuery al data warehouse aziendale e quindi si usa GetData e si sceglie Excel, si passa al foglio di calcolo che contiene i dati locali e si può importare il foglio contenente i valori *ProductName*, oltre ai dati *SalesManager* e *Priority* assegnati.  

![Finestra Strumento di navigazione](media/desktop-composite-models/composite-models_06.png)

Nell'elenco **Campi** sono ora visibili la tabella *Bike* originale (da SQL Server) e una nuova tabella *Product Managers* (con i dati importati da Excel). 

![Visualizzazione dei campi delle tabelle](media/desktop-composite-models/composite-models_07.png)

Allo stesso modo, osservando la **visualizzazione Relazioni** in **Power BI Desktop** è ora disponibile una tabella aggiuntiva denominata *Product Managers*. 

![visualizzazione delle relazioni delle tabelle](media/desktop-composite-models/composite-models_08.png)

È ora necessario correlare queste tabelle con le altre nel modello, procedendo come al solito, creando una relazione tra la tabella *Bike* (in SQL Server) e la tabella *Product Managers* (importata), come tra *Bike[ProductName]* e *ProductManagers[ProductName]*. Come illustrato in precedenza in questo articolo, tutte le relazioni attraverso l'origine devono avere la cardinalità **molti-a-molti** e di conseguenza, questa è la cardinalità predefinita selezionata. 

![finestra di dialogo per creare la relazione](media/desktop-composite-models/composite-models_09.png)

Dopo averla creata, questa relazione viene visualizzata nella **visualizzazione Relazioni** in **Power BI Desktop**, come previsto.

![visualizzazione della nuova relazione](media/desktop-composite-models/composite-models_10.png)

Dopo aver stabilito queste relazioni è ora possibile creare oggetti visivi usando uno dei campi nell'elenco **Campi** per combinare facilmente i dati da più origini. Ad esempio, l'oggetto visivo seguente mostra il valore totale di *Sales Amount* per ogni *Product Manager*. 

![oggetto visivo con il riquadro dei campi visualizzato](media/desktop-composite-models/composite-models_11.png)

Questo esempio illustra un caso comune di tabella delle *dimensioni* (come *Product* o *Customer*) estesa con alcuni dati aggiuntivi importati da un'altra posizione. È anche possibile usare DirectQuery nelle tabelle con una connessione a origini diverse. Per ampliare questo esempio, si immagini che i valori di *SalesTargets* per ogni *Country* e *Period* siano archiviati in un database di reparto separato. È possibile usare **GetData** per connettersi a tali dati come si consueto, come illustrato nell'immagine seguente. 

![Finestra di dialogo Strumento di navigazione](media/desktop-composite-models/composite-models_12.png)

Quindi, in modo analogo a come si è proceduto in precedenza in questo esempio, è possibile creare relazioni tra la nuova tabella e altre tabelle nel modello e creare oggetti visivi che combinano i dati. La figura seguente mostra ancora una volta la **visualizzazione Relazioni**, con nuove relazioni stabilite nello scenario di esempio esteso.

![visualizzazione delle relazioni con molte tabelle](media/desktop-composite-models/composite-models_13.png)

Come illustrato nell'immagine seguente, che si basa sui nuovi dati e le relazioni appena create, l'oggetto visivo nell'angolo in basso a sinistra mostra i valori totali per *Sales Amount* rispetto a *Target*, con il calcolo della varianza che mostra la differenza, in cui *Sales Amount* e *Target* provengono da due database di SQL Server diversi. 

![oggetto visivo che mostra altri dati](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>Impostazione della modalità di archiviazione

Ogni tabella in un **modello composito** ha una **modalità di archiviazione** che indica se la tabella è basata su DirectQuery o importazione. La **modalità di archiviazione** può essere visualizzata e modificata nel riquadro **Proprietà**. Per visualizzare questo riquadro, scegliere **Proprietà** dal menu di scelta rapida dell'elenco **Campi**. L'immagine seguente mostra la **modalità di archiviazione** (abbreviata in **Modalità...**  nell'immagine, a causa della larghezza del riquadro).

![Impostazione della modalità di archiviazione](media/desktop-composite-models/composite-models_15.png)

La **modalità di archiviazione** è anche visibile nella descrizione comando per ogni tabella.

![descrizione comando con la modalità di archiviazione](media/desktop-composite-models/composite-models_16.png)

Per qualsiasi file di **Power BI Desktop** (con estensione pbix) che contiene alcune tabelle da DirectQuery e alcune tabelle importate, la barra di stato mostra la **modalità di archiviazione** **Mista**. È possibile fare clic su tale termine nella barra di stato e passare facilmente a tutte le tabelle da importare.

Informazioni dettagliate e complete sulla **modalità di archiviazione** sono disponibili nell'articolo [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md).  

## <a name="calculated-tables"></a>Tabelle calcolate

Le tabelle calcolate possono essere aggiunte a un modello che usa DirectQuery e le espressioni DAX che definiscono la tabella calcolata possono fare riferimento a tabelle importate o DirectQuery oppure a una combinazione di entrambe. 

Le tabelle calcolate vengono sempre importate e i dati in queste tabelle vengono aggiornati quando viene aggiornata la tabella. Per questo motivo, se una tabella calcolata fa riferimento a una tabella DirectQuery, gli oggetti visivi che fanno riferimento alla tabella DirectQuery mostrano sempre i valori più recenti nella tabella sottostante, ma gli oggetti visivi che fanno riferimento alla tabella calcolata mostrano i valori al momento dell'ultimo aggiornamento della tabella calcolata.

## <a name="security-implications"></a>Implicazioni per la sicurezza 

Per i modelli compositi esistono alcune implicazioni per la sicurezza. Una query inviata a un'origine dati può includere valori di dati che sono stati recuperati da un'altra origine diversa. Con riferimento all'esempio descritto in precedenza in questo articolo, l'oggetto visivo che mostra i valori *Sales Amount* in base a *Product Manager* causerà l'invio di una query SQL al database relazionale **Sales** e tale query SQL potrebbe contenere i nomi di *Product Manager* e i valori *Product* associati. 

![script che mostra le implicazioni per la sicurezza](media/desktop-composite-models/composite-models_17.png)

Per questo motivo, le informazioni archiviate nel foglio di calcolo vengono ora incluse in una query inviata al database relazionale. Se queste informazioni sono riservate, occorre tenere conto delle implicazioni per la sicurezza. In particolare, è necessario considerare le implicazioni seguenti:

* Qualsiasi amministratore del database che può visualizzare le tracce o i log di controllo sarà in grado di visualizzare queste informazioni, anche se non ha le autorizzazioni per questi dati nell'origine (in questo caso, le autorizzazioni per il file di Excel).

* Devono essere considerate le impostazioni di crittografia per ogni origine, per evitare che le informazioni vengano recuperate da un'origine tramite una connessione crittografata, ma vengano poi incluse inavvertitamente in una query inviata a un'altra origine usando una connessione non crittografata. 

**Power BI Desktop** visualizza un messaggio di avviso quando viene eseguita un'azione per creare un modello composito, per ottenere una conferma che sono state prese in considerazione le implicazioni per la sicurezza.  

Per motivi analoghi, è necessario prestare attenzione quando si apre un file di **Power BI Desktop** inviato da un'origine non attendibile. Se tale file contiene modelli compositi, significa che le informazioni recuperate da un'origine (usando le credenziali dell'utente che apre il file) vengono inviate a un'altra origine dati come parte della query (in cui sono potenzialmente visibili per l'autore malintenzionato del file di Power BI Desktop). Per questo motivo, quando si apre un file di Power BI Desktop per la prima volta, se contiene più origini, viene visualizzato un avviso. Questo avviso è simile a quello visualizzato quando si apre un file che contiene query SQL native.  

## <a name="performance-implications"></a>Implicazioni per le prestazioni  

Quando si usa DirectQuery, occorre tenere sempre conto delle prestazioni, principalmente per garantire che l'origine back-end abbia risorse sufficienti per offrire una buona esperienza agli utenti. Con buona esperienza si intende che gli oggetti visivi dovrebbero essere aggiornati entro 5 secondi. È anche necessario attenersi ai consigli per le prestazioni nell'articolo [Uso di DirectQuery in Power BI](desktop-directquery-about.md). L'uso dei modelli compositi comporta altre considerazioni per le prestazioni, perché un singolo oggetto visivo può causare l'invio di query a più origini, spesso con il passaggio dei risultati da una query a una seconda origine. Questa situazione può portare alle possibili forme di esecuzione seguenti:

* **Una query SQL che include un numero elevato di valori letterali** - Ad esempio, un oggetto visivo che richiede il totale di *Sales Amount* (dal database SQL) per un set di *Product Managers* selezionati (dalla tabella correlata importata da un foglio di calcolo) deve prima di tutto individuare quali *Product* sono gestiti dai Product Manager selezionati, prima di inviare una query SQL che include tutti gli ID di prodotto in una clausola *WHERE*.

* **Una query SQL eseguita a un livello inferiore di granularità, con i dati che vengono aggregati in locale** - L'uso dello stesso esempio come nel punto precedente di questo elenco, quando il numero di *Product* che soddisfano il filtro per *Product Managers* diventa molto elevato, a un certo punto diventa inefficiente o non fattibile includerli tutti in una clausola *WHERE*. È invece necessario eseguire una query sull'origine relazionale al livello inferiore di *Product* e quindi aggregare i risultati in locale. Se la cardinalità di *Product* supera il limite di 1 milione, la query avrà esito negativo.

* **Più query SQL, una per ogni valore di raggruppamento** - Quando l'aggregazione usa **DistinctCount**, con raggruppamento in base a una colonna dall'altra origine, se l'origine esterna non supporta il passaggio efficiente di molti valori letterali che definiscono il raggruppamento, è necessario inviare una query SQL per ogni valore di raggruppamento. Ad esempio, un oggetto visivo che richiede il conteggio di valori univoci per *CustomerAccountNumber* (dalla tabella di SQL Server) in base a *Product Manager* (dalla tabella correlata importata da un foglio di calcolo) dovrebbe passare i dettagli dalla tabella *Product Managers* nella query inviata a SQL Server. Su altre origini, ad esempio Redshift, questo non è fattibile e ci sarebbe invece una sola query SQL inviata per ogni *Sales Manager* (fino a un limite pratico e a tal punto la query avrebbe esito negativo). 

Per ognuno di questi casi esistono implicazioni specifiche per le prestazioni e i dettagli esatti variano per ogni origine dati. È buona norma tenere presente che mentre la cardinalità delle colonne usate nella relazione di join tra due origini rimane bassa (poche migliaia), non dovrebbero esserci effetti significativi sulle prestazioni. Con l'aumento della cardinalità, è consigliabile prestare maggiore attenzione agli effetti sulle prestazioni risultanti. 

Inoltre, l'uso delle relazioni **molti-a-molti** significa che è necessario inviare query separate all'origine sottostante per ogni livello totale/subtotale, anziché aggregare i valori dettagliati in locale. Per questo motivo, un oggetto visivo tabella semplice con totali invierebbe due query SQL, anziché una. 

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni

Esistono alcune limitazioni per questa versione dei **modelli compositi**.

Non è possibile usare **modelli compositi** con le origini Live Connect (multidimensionali) seguenti:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Set di dati Power BI
* Azure Analysis Services

Quando ci si connette a tali origini multidimensionali tramite DirectQuery, non è neanche possibile connettersi a un'altra origine DirectQuery o attuare combinazioni con dati importati.

Le limitazioni esistenti per l'uso di DirectQuery sono valide anche quando si usano i **modelli compositi**. Molte di queste limitazioni si riferiscono attualmente a ogni singola tabella, a seconda della **modalità di archiviazione** della tabella. Ad esempio, una colonna calcolata per una tabella importata può fare riferimento ad altre tabelle, ma una colonna calcolata per una tabella di DirectQuery è ancora limitata e può fare riferimento solo alle colonne nella stessa tabella. Altre limitazioni si applicano al modello nel suo complesso, se una qualsiasi delle tabelle all'interno del modello è in modalità DirectQuery. Ad esempio, le funzionalità **Informazioni rapide** e **Domande e risposte** non sono disponibili per un modello se per una delle tabelle all'interno di esso è impostata la **modalità di archiviazione** DirectQuery. 

## <a name="next-steps"></a>Passaggi successivi

Gli articoli seguenti includono ulteriori informazioni sui modelli compositi e descrivono anche la modalità DirectQuery in modo dettagliato.

* [Relazioni molti-a-molti in Power BI Desktop (anteprima)](desktop-many-to-many-relationships.md)
* [Modalità di archiviazione in Power BI Desktop (anteprima)](desktop-storage-mode.md)

Articoli su DirectQuery:

* [Uso di DirectQuery in Power BI](desktop-directquery-about.md)
* [Origini dati supportate da DirectQuery in Power BI](desktop-directquery-data-sources.md)

