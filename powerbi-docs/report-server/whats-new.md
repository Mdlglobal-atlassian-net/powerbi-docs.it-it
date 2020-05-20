---
title: Novità del Server di report di Power BI
description: Informazioni sulle novità del Server di report di Power BI. Questo articolo riguarda le funzionalità principali e viene aggiornato con il rilascio di nuovi elementi.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/27/2020
ms.openlocfilehash: f4585e4c1eb629b4676b74157c0520d70540da7b
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565147"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novità del Server di report di Power BI

Informazioni sulle novità di Server di report di Power BI e Power BI Desktop ottimizzato per Server di report di Power BI. Questo articolo riguarda le funzionalità principali e viene aggiornato per ogni nuova versione.

Scaricare [Server di report di Power BI e Power BI Desktop ottimizzato per Server di report di Power BI](https://powerbi.microsoft.com/report-server/).

Per informazioni sulle "Novità" di Power BI, vedere:

* [Novità del servizio Power BI](../fundamentals/service-whats-new.md)
* [Novità di Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Novità delle app per dispositivi mobili per Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>Gennaio 2020

Per altri dettagli, vedere il post di blog di gennaio 2020 dedicato a Server di report di Power BI.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop ottimizzato per Server di report di Power BI

Questa versione offre molte nuove funzionalità, ad esempio la formattazione condizionale per i pulsanti, miglioramenti del profiling dei dati e altre impostazioni di formattazione per gli indicatori KPI e gli oggetti visivi tabella. Ecco un elenco riepilogativo degli aggiornamenti:

**Creazione di report**

- Impostazione di una colonna della tabella o del valore della matrice come URL personalizzato
- Impostazioni di formattazione dell'oggetto visivo indicatore KPI
- Aggiornamenti dell'esperienza del riquadro filtro

**Analisi**

- Pulsanti per la formattazione condizionale
- Caricare altri dati per l'analisi delle informazioni dettagliate
- Nuove funzioni DAX: Quarter

**Preparazione dei dati**

- Miglioramenti del profiling dei dati

**Altro**

- Nuovo formato di file: pbids
- Miglioramenti delle prestazioni per le operazioni di modellazione

**Creazione di report**

*Impostare una colonna di tabella o un valore di matrice come URL personalizzato*

È possibile impostare una colonna di tabella o un valore di matrice come URL personalizzato. Questa nuova opzione è disponibile nella scheda Formattazione condizionale nel riquadro di formattazione.

*Impostazioni di formattazione dell'oggetto visivo indicatore KPI*

Con la versione di questo mese, per gli indicatori KPI sono disponibili nuove opzioni di formattazione:

- Formattazione del testo dell'indicatore (famiglia di caratteri, colore e allineamento)
- Trasparenza dell'asse tendenza
- Formattazione del testo per obiettivo e distanza (testo dell'etichetta, famiglia di caratteri, colore e dimensioni)
- Formattazione del testo della distanza (testo dell'etichetta, direzione positiva, famiglia di caratteri, colore e dimensioni)
- Aggiunta di un'etichetta di data con formattazione (famiglia di caratteri, colore e dimensioni)

È possibile formattare in modo condizionale alcune di queste nuove opzioni di formattazione:

- Colore del carattere dell'indicatore
- Colore del carattere dell'obiettivo e della distanza dell'obiettivo
- Colori di stato buono/non valido/neutro
- Colore del carattere della data

*Aggiornamenti dell'esperienza del riquadro filtro*

Come parte della disponibilità generale della nuova esperienza di filtro dall'[ultima versione](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane), è stato semplificato il processo di transizione dei report correnti al nuovo riquadro. Quando si apre Server di report di Power BI per la prima volta, viene visualizzata una finestra di dialogo di aggiornamento automatico del riquadro filtro. Questi aggiornamenti includono anche banner nel server di report quando è necessario eseguire la migrazione dei report alla nuova esperienza.

**Analisi**

*Formattazione condizionale per i pulsanti*

Questi aggiornamenti della formattazione condizionale sono tutti correlati ai pulsanti. È ora possibile impostare dinamicamente la formattazione per le proprietà seguenti:

- Colore carattere del testo del pulsante
- Testo del pulsante
- Colore linea dell'icona
- Outline color
- Colore riempimento
- Descrizione comando per il pulsante (sotto la scheda azione)

*Caricare altri dati per l'analisi delle informazioni dettagliate*

Quando si esegue la funzionalità Analizza per trovare informazioni dettagliate nei dati, ad esempio Spiega l'aumento, i modelli di Machine Learning vengono eseguiti solo per un determinato periodo di tempo per mostrare le informazioni dettagliate in modo tempestivo. In presenza di una grande quantità di dati da analizzare, è ora possibile scegliere di continuare a eseguire l'analisi dopo il timeout iniziale.

*Nuove funzioni DAX: Quarter*

Questo mese è stata introdotta una nuova funzione DAX, Quarter. La funzione Quarter restituisce il trimestre corrispondente a una data specificata.

**Preparazione dei dati**

*Miglioramenti del profiling dei dati*

Questo mese sono stati introdotti alcuni miglioramenti significativi per le funzionalità di profiling dei dati all'interno dell'editor di Power Query, tra cui:

- Più opzioni di raggruppamento per l'oggetto visivo Distribuzione dei valori del riquadro Profilo colonna, specifico per tipo di colonna, oltre ai criteri "Per valore" esistenti.
- Testo: per lunghezza del testo (numero di caratteri).
- Numero: per segno (positivo/negativo) e parità (pari/dispari).
- Date/DateTime: per anno, mese, giorno, settimana dell'anno, giorno della settimana, ora AM/PM e ora in un giorno.
- E altro ancora per altri tipi di dati, ad esempio vero/falso logico.

*Opzioni di filtro*

Era già possibile usare diversi criteri di raggruppamento specifici del tipo all'interno del riquadro di distribuzione dei profili di colonna. Ora è anche possibile filtrare dall'interno dei callout per ogni valore nel grafico di distribuzione quando sono applicati criteri di raggruppamento. Dal riquadro dei profili dati per una colonna Date/DateTime, ad esempio, è possibile escludere tutti i valori che rientrano in un determinato mese.

**Altro**

*Nuovo formato di file: pbids*

Questo mese viene rilasciato un nuovo formato di file con estensione pbids, per semplificare l'esperienza "Recupera dati" per gli autori di report nell'organizzazione. Si consiglia agli amministratori di creare questi file per le connessioni di uso comune.

Quando un autore di report apre un file con estensione pbids, Power BI Desktop richiede l'autenticazione per la connessione all'origine dati specificata nel file. L'utente seleziona quindi le tabelle da caricare nel modello. È anche possibile che gli utenti debbano selezionare un database, se non ne è stato specificato alcuno nel file. Da qui, l'autore del report può iniziare a creare visualizzazioni.

Per informazioni dettagliate ed esempi, vedere la sezione [Uso di file PBIDS per ottenere i dati](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) dell'articolo "Origini dati in Power BI Desktop".

*Miglioramenti delle prestazioni per le operazioni di modellazione*

Sono state migliorate le prestazioni nel motore di Analysis Services per velocizzare le operazioni di modellazione, ad esempio l'aggiunta di misure o colonne calcolate e la creazione di relazioni. Il livello di miglioramento che si sperimenterà dipende dal modello, ma alcuni clienti hanno riscontrato un miglioramento delle prestazioni di 20 volte per azioni quali l'apertura di un file e l'aggiunta di una misura.

Questo è tutto per la versione di Server di report di Power BI di gennaio 2020. Continuare a inviare commenti e suggerimenti e non dimenticare di [votare le funzionalità che si vorrebbe vedere incluse in Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Server di report Power BI

#### <a name="export-to-excel-from-power-bi-reports"></a>Esportare in Excel da report di Power BI

L'esportazione in Excel da un report di Power BI in Server di report di Power BI ora funziona allo stesso modo dell'esportazione in Excel da un report Power BI nel servizio Power BI. È possibile esportare direttamente nel formato XLSX di Excel e il limite di esportazione è di 150.000 righe.

#### <a name="azure-sql-managed-instance-support"></a>Supporto per Istanza gestita di database SQL di Azure

È ora possibile ospitare un catalogo di database usato per Server di report di Power BI in un'istanza gestita di database SQL di Azure ospitata in una macchina virtuale o nel data center. Il supporto è limitato all'uso delle credenziali del database per la connessione all'istanza gestita di database SQL.

#### <a name="power-bi-premium-dataset-support"></a>Supporto di set di dati di Power BI Premium

È possibile connettersi a set di dati di Power BI usando Generatore report Microsoft o SQL Server Data Tools (SSDT). È quindi possibile pubblicare questi report in Server di report di Power BI usando la connettività a SQL Server Analysis Services. Per abilitare lo scenario, gli utenti devono usare un nome utente e una password archiviati di Windows.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Supporto di AltText (testo alternativo) per gli elementi del report

Durante la creazione di report è possibile usare descrizioni comando per specificare il testo per ogni elemento nel report. Queste descrizioni comando verranno usate dalle utilità per la lettura dello schermo.

#### <a name="azure-active-directory-application-proxy-support"></a>Supporto per Azure Active Directory Application Proxy

Con Azure Active Directory Application Proxy non è più necessario gestire il proxy applicazione Web per consentire l'accesso sicuro tramite le app Web o per dispositivi mobili. Per altre informazioni, vedere [Accesso remoto ad applicazioni locali tramite Azure Active Directory Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="custom-headers"></a>Intestazioni personalizzate

Impostare i valori di intestazione per tutti gli URL che corrispondono al modello regex specificato. Gli utenti possono aggiornare il valore dell'intestazione personalizzata con XML valido per impostare i valori di intestazione per gli URL di richiesta selezionati. Gli amministratori possono aggiungere un numero qualsiasi di intestazioni nel codice XML. Per informazioni dettagliate, vedere [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) nell'articolo **Pagina Avanzate delle proprietà del server** di Reporting Services.

#### <a name="transparent-database-encryption"></a>Crittografia trasparente del database

Server di report di Power BI supporta ora Transparent Data Encryption per il database del catalogo di Server di report di Power BI per le edizioni Enterprise e Standard.

#### <a name="power-bi-visuals-api"></a>API per gli oggetti visivi di Power BI

La versione dell'API disponibile in questa versione è 2.6.

#### <a name="microsoft-report-builder-update"></a>Aggiornamento di Generatore report Microsoft

La nuova versione rilasciata di Generatore report è completamente compatibile con le versioni 2016, 2017 e 2019 di Reporting Services. È compatibile anche con tutte le versioni rilasciate e supportate di Server di report di Power BI.

## <a name="september-2019"></a>Settembre 2019

Per informazioni dettagliate su tutte le nuove funzionalità, vedere il post di bIog di [riepilogo delle funzionalità di Server di report di Microsoft Power BI per settembre 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/).

L'aggiornamento di settembre 2019 di Server di report di Power BI offre numerose funzionalità per i report di Power BI. Ecco alcune delle principali:

- **Filtri a livello di oggetto visivo per i filtri dei dati**  È possibile aggiungere un filtro a livello di oggetto visivo ai filtri dei dati. Funziona in modo analogo a qualsiasi altro filtro a livello di oggetto visivo, limitando l'applicazione dei filtri al filtro dei dati stesso e non ad altri oggetti visivi. Questo filtro è utile per escludere i dati vuoti o se si vogliono usare i filtri di misura.
- **Set di icone per tabella e matrice** Con le icone KPI è possibile impostare regole per la visualizzazione di set di icone diversi nella tabella e nella matrice, in modo analogo ai set di icone in Excel.
- **Raggruppamento di oggetti visivi** È ora possibile raggruppare gli oggetti visivi, le forme, le caselle di testo, le immagini e i pulsanti in una pagina del report come in PowerPoint. Quando si raggruppano gli oggetti, è possibile spostarli e ridimensionarli tutti insieme. Il raggruppamento semplifica la gestione in un report con molti oggetti disposti su vari livelli in ogni pagina.
- **Nuovi temi predefiniti** Per coerenza con le nuove opzioni JSON per i temi, verranno aggiornati i temi disponibili per i report e verrà modificato il tema predefinito per i nuovi report. Il nuovo tema predefinito è più allineato al linguaggio di progettazione di Microsoft e segue le procedure di progettazione consigliate per gli oggetti visivi. 
- **Progettazione dei riquadri aggiornata** È stata aggiornata gran parte dell'interfaccia. Sono stati aggiornati tutti i riquadri, il piè di pagina e il selettore di visualizzazione con un colore più chiaro e una diversa spaziatura e sono state introdotte nuove icone. La nuova progettazione è il primo passo pe l'aggiornamento dell'intera interfaccia.

Ecco l'elenco completo delle funzionalità. 

### <a name="reporting"></a>Reporting

- Progettazione dei riquadri aggiornata
- Filtri a livello di oggetto visivo per i filtri dei dati
- Ordinamento per il riquadro Analizzatore prestazioni
- Descrizioni comando di intestazione dell'oggetto visivo
- Personalizzazione dell'intera etichetta di tabella e matrice
- Supporto per la sincronizzazione per il filtro dei dati della gerarchia
- Dimensioni dei caratteri coerenti tra gli oggetti visivi
- Set di icone per tabella e matrice
- Supporto delle percentuali per la formattazione condizionale in base a regole
- Il nuovo riquadro dei filtri è ora disponibile a livello generale
- Supporto dei colori dei dati quando si usa l'asse di riproduzione nei grafici a dispersione
- Miglioramenti delle prestazioni quando si usano i filtri dei dati per la data relativa e quelli a discesa
- Raggruppamento di oggetti visivi
- Classi di colore e testo nei temi
- Nuovi temi predefiniti

### <a name="analytics"></a>Analisi

- Stringhe di formato personalizzate
- Aggiornamenti di formattazione condizionale per opzioni di formattazione

    - Colori per sfondo e titolo degli oggetti visivi
    - Colori delle schede
    - Riempimento e colori del misuratore
    - Testo alternativo
    - Colore bordo

- Avvisi relativi alla formattazione condizionale
- Miglioramento dell'individuabilità di drill-through
- Nuove espressioni DAX: REMOVEFILTERS e CONVERT
- Nuovo operatore di confronto DAX: ==

### <a name="data-preparation"></a>Preparazione dei dati

- Miglioramenti a M Intellisense
- Nuova trasformazione: Suddividi colonna in base alle posizioni
- Copia negli Appunti dal profiling dei dati


## <a name="may-2019"></a>Maggio 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop per Server di report di Power BI

Per informazioni dettagliate su tutte le nuove funzionalità, vedere il post di bIog di [riepilogo delle funzionalità di Server di report di Microsoft Power BI per maggio 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/).

Ecco alcune delle principali:

#### <a name="performance-analyzer"></a>Analizzatore prestazioni 

Se il report viene eseguito più lentamente del previsto, provare l'analizzatore prestazioni in Power BI Desktop. All'avvio viene creato un file di log con informazioni su ogni azione eseguita nel report. Leggere altre informazioni sull'[analizzatore prestazioni](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Nuova visualizzazione di modellazione

Nella nuova visualizzazione di modellazione in Power BI Desktop è possibile visualizzare e usare set di dati complessi contenenti molte tabelle. Tra le novità più interessanti vi sono più layout di diagramma e la modifica in blocco di colonne, misure e tabelle. Vedere altre informazioni sulla [visualizzazione di modellazione](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Accessibilità per le interazioni con gli oggetti visivi

È ora possibile accedere ai punti dati in molti degli oggetti visivi predefiniti spostandosi tramite la tastiera. Vedere altre informazioni sull'[accessibilità nei report di Power BI](../create-reports/desktop-accessibility-overview.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Titoli di formattazione condizionale e azioni URL Web

I report di Power BI sono interattivi. Ha senso che i titoli di un report siano dinamici, in modo da riflettere lo stato corrente del report. È possibile usare la stessa formattazione associata a espressioni per rendere dinamici gli URL di pulsanti, forme e immagini. Vedere altre informazioni sui [titoli basati su espressioni](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Evidenziazione incrociata in base alle etichette dell'asse

Selezionare le etichette delle categorie dell'asse in un oggetto visivo per evidenziare in modo incrociato gli altri elementi in una pagina, così come con la selezione dei punti dati in un oggetto visivo. Vedere altre informazioni sull'[evidenziazione incrociata](../create-reports/power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Tutte le nuove funzionalità

Ecco l'elenco di tutte le nuove funzionalità:

#### <a name="reporting"></a>Reporting

- Evidenziazione incrociata in un singolo punto nei grafici a linee 
- Ritorno a capo automatico nei titoli 
- Aggiornamento dell'interazione predefinita di oggetti visivi con il filtro incrociato
- Angoli arrotondati per i bordi degli oggetti visivi 
- Filtro dei dati a selezione singola  
- Supporto delle mappe termiche per Mappe di Bing  
- Evidenziazione incrociata in base alle etichette dell'asse  
- Formattazione della descrizione comando predefinita  
- Supporto degli URL Web statici per pulsanti, forme e immagini  
- Opzioni di allineamento pagina   
- Miglioramenti al riquadro di selezione  
- Accessibilità per le interazioni con gli oggetti visivi  
- Formattazione condizionale per i titoli degli oggetti visivi  
- Formattazione condizionale per le azioni URL di pulsanti, forme e immagini
- Riquadro dell'analizzatore prestazioni
- Spostamenti tramite tastiera in tabella e matrice
- Controllo di posizione dell'etichetta dati in una riga
- Controllo delle dimensioni del testo dell'indicatore per l'oggetto visivo KPI

#### <a name="analytics"></a>Analisi

- Visualizzazione delle date come gerarchia ora disponibile a livello generale  

#### <a name="modeling"></a>Modellazione

- Nuova visualizzazione di modellazione ora disponibile a livello generale
- Nuove funzioni DAX
- Aggiornamento alla funzione DAX ALLSELECTED
- Disabilitare le tabelle data generate automaticamente per i nuovi report

### <a name="power-bi-report-server"></a>Server di report Power BI

#### <a name="support-for-trusted-visuals"></a>Supporto per gli oggetti visivi attendibili

È stato aggiunto il supporto per gli oggetti visivi attendibili per Server di report di Power BI. Attualmente sono supportati gli oggetti visivi Mapbox e PowerOn. Esri, Visio e PowerApps non sono supportati in questa versione.

#### <a name="improved-security-features"></a>Funzionalità di sicurezza migliorate

**RestrictedResourceMimeTypeForUpload**, che può essere usato dagli amministratori per specificare un elenco delimitato da virgole di tipi MIME vietati, ad esempio text/html.

## <a name="january-2019"></a>Gennaio 2019

Supporto delle funzionalità seguenti nei report di Power BI:

[**Sicurezza a livello di riga**](row-level-security-report-server.md) L'impostazione della sicurezza a livello di riga con il server di report di Power BI può limitare l'accesso ai dati per determinati utenti. I filtri limitano l'accesso ai dati a livello di riga ed è possibile definirli all'interno dei ruoli.

[**Espandere e comprimere le intestazioni di riga di matrice**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) È stata aggiunta la possibilità di espandere e comprimere le singole intestazioni di riga, una delle funzionalità più richieste per gli oggetti visivi.

[**Copia e incolla tra file con estensione pbix**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) È possibile copiare gli oggetti visivi tra file con estensione pbix mediante il menu di scelta rapida dell'oggetto visivo o con la scelta rapida da tastiera standard Ctrl+C e quindi incollarli in un altro report con Ctrl+V.

[**Guide intelligenti per l'allineamento**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Le guide intelligenti per l'allineamento vengono visualizzate durante lo spostamento di oggetti nella pagina del report, come in PowerPoint, per facilitare l'allineamento di tutti gli elementi della pagina. Le guide intelligenti vengono visualizzate ogni volta che si trascina o ridimensiona un elemento nella pagina. Quando si sposta un oggetto vicino a un altro, l'oggetto viene ancorato in una posizione allineata con l'altro oggetto.

**Funzionalità di accessibilità** Le funzionalità di accessibilità sono troppe per elencarle tutte: ad esempio il [supporto per l'accessibilità al riquadro elenco campi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Il riquadro elenco di campi è completamente accessibile. È possibile spostarsi nel riquadro solo con la tastiera e un'utilità per la lettura dello schermo e usare il menu di scelta rapida per aggiungere campi alla pagina del report.

#### <a name="power-bi-visuals"></a>Oggetti visivi di Power BI

- La versione dell'API fornita con questa versione è 2.3.

### <a name="administrator-settings"></a>Impostazioni dell'amministratore

Gli amministratori possono configurare le proprietà seguenti in Proprietà avanzate di SSMS per la server farm:

**AllowedResourceExtensionsForUpload** Possibilità di impostare le estensioni delle risorse caricabili nel server di report. Non è obbligatorio includere le estensioni per i tipi di file predefiniti, ad esempio &ast;.rdl e &ast;.pbix. L'impostazione predefinita è "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx". 

**SupportedHyperlinkSchemes** Consente di impostare un elenco delimitato da virgole degli schemi URI definibili nelle azioni CollegamentoIpertestuale autorizzate per il rendering o "&ast;" per abilitare tutti gli schemi di collegamento ipertestuale. Ad esempio, se si imposta "http,https" sono consentiti i collegamenti ipertestuali a "https://www. contoso.com", ma vengono rimossi i collegamenti ipertestuali a "mailto:bill@contoso.com" o "javascript:window.open('www.contoso.com', '_blank')". L'impostazione predefinita è "&ast;".

## <a name="august-2018"></a>Agosto 2018

La versione di agosto 2018 presenta molte nuove funzionalità aggiunte alla versione di Power BI Desktop ottimizzate per Server di report di Power BI. Sono riportate di seguito, suddivise per area:

- [Creazione di report](#reporting)
- [Analisi](#analytics)
- [Modellazione](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Caratteristiche principali della versione di agosto 2018

Nel lungo elenco di nuove funzionalità emergono quelle riportate di seguito, particolarmente interessanti. Per altre informazioni, vedere questo [post di blog](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Temi per i report

Nella versione di agosto 2018 di Server di report di Power BI sono stati aggiunti temi per i report, che consentono di applicare velocemente colori all'intero report in base a un tema o a un marchio aziendale. Quando si importa un tema, tutti i grafici vengono aggiornati automaticamente per usare i colori del tema, che diventano accessibili nella tavolozza dei colori. È possibile caricare un file di tema con l'opzione **Importa tema** sotto il pulsante **Cambia tema**.

Un file di tema è un file JSON che include tutti i colori che si vuole usare nel report, oltre a qualsiasi formattazione predefinita da applicare agli oggetti visivi.
Ecco un tema JSON di esempio semplice che aggiorna i colori predefiniti del report:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Formattazione condizionale da un campo diverso

La possibilità di formattare una colonna in base a un campo diverso nel modello è uno dei miglioramenti significativi per la formattazione condizionale.

#### <a name="conditional-formatting-by-values"></a>Formattazione condizionale in base ai valori

Un altro nuovo tipo di formattazione condizionale è **Formatta per valore del campo**. L'opzione Formatta per valore del campo consente di usare una misura o una colonna che specifica un colore, tramite un codice esadecimale o un nome, e applicare tale colore allo sfondo o come colore del carattere.

#### <a name="report-page-tooltips"></a>Descrizioni comando per le pagine del report

La funzionalità delle descrizioni comando per le pagine del report è inclusa nell'aggiornamento di agosto 2018 di Server di report di Power BI. Questa funzionalità consente di progettare una pagina del report da usare come descrizione comando personalizzata per gli altri oggetti visivi nel report.

#### <a name="log-axis-improvements"></a>Miglioramenti dell'asse logaritmico

È stato notevolmente migliorato l'asse logaritmico nei grafici cartesiani. È ora possibile selezionare la scala logaritmica per l'asse numerico di qualsiasi grafico cartesiano, incluso un grafico combinato, in presenza di dati completamente positivi o completamente negativi.

#### <a name="sap-hana-sso-direct-query"></a>DirectQuery SSO SAP HANA

È ora disponibile il supporto di DirectQuery SSO SAP HANA per i report di Power BI.

>[!Note]
>Questo scenario è supportato solo quando SAP HANA viene considerato come origine dati relazionale con i report creati in Power BI Desktop.  Per abilitare questa opzione in Power BI Desktop, nel menu DirectQuery in Opzioni selezionare "Considerare SAP HANA come origine relazionale" e fare clic su OK.

#### <a name="power-bi-visuals"></a>Oggetti visivi di Power BI

- La versione dell'API fornita con questa versione è 1.13.0.

- Per gli oggetti visivi di Power BI è ora possibile eseguire il fallback a una versione precedente compatibile con la versione corrente dell'API server (se disponibile).

### <a name="reporting"></a>Reporting 

- [Temi per i report](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Pulsanti per l'attivazione di azioni](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Stili di linea dei grafici combinati](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Ordinamento predefinito degli oggetti visivi migliorato](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Filtro dei dati numerico](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Sincronizzazione avanzata del filtro dei dati](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Miglioramenti dell'asse logaritmico](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Opzioni etichette dati per il grafico a imbuto](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Impostazione dello spessore tratto su zero](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Supporto del contrasto elevato per i report](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Controllo radiale ad anello](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Controllo posizione delle etichette nei grafici a torta e ad anello](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Formattazione separata delle etichette dati per ogni misura in un grafico combinato](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Nuova intestazione degli oggetti visivi con maggiore flessibilità e più opzioni di formattazione](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Formattazione dello sfondo](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Descrizioni comando per tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Disattivare le descrizioni comando per gli oggetti visivi](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Accessibilità per i filtri dei dati](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Miglioramenti al riquadro Formattazione](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Supporto di linee con rientri per i grafici a linee e i grafici combinati](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Miglioramenti dell'esperienza di ordinamento](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Stampare i report tramite Esporta in PDF (in Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Creare gruppi di segnalibro](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Riformulazione dei filtri dei dati](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Descrizioni comando per le pagine del report](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Analisi

- [Nuove funzioni DAX: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Drill-through con misure](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Formattazione condizionale da un campo diverso](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Formattazione condizionale in base ai valori](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modellazione

- [Filtro e ordinamento nella vista dati](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Miglioramento della formattazione delle impostazioni locali](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Categorie di dati per le misure](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Funzioni statistiche DAX](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>Maggio 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Configurare le app per dispositivi mobili iOS di Power BI per server di report in modalità remota

In qualità di amministratori IT, è ora possibile usare lo strumento MDM dell'organizzazione per configurare in modalità remota l'accesso delle app per dispositivi mobili iOS di Power BI a un server di report. Per informazioni dettagliate, vedere [Configurare l'accesso delle app per dispositivi mobili iOS di Power BI in modalità remota](configure-powerbi-mobile-apps-remote.md).

## <a name="march-2018"></a>Marzo 2018

La versione di marzo 2018 presenta molte nuove funzionalità aggiunte alla versione di Power BI Desktop ottimizzate per Server di report di Power BI. Sono riportate di seguito, suddivise per area:

- [Oggetti visivi](#visuals-updates)
- [Creazione di report](#reporting)
- [Analisi](#analytics)
- [Prestazioni](#performance)
- [Server di report](#report-server)
- [Altro](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Caratteristiche principali della versione di marzo 2018

Nel lungo elenco di nuove funzionalità emergono quelle riportate di seguito, particolarmente interessanti.

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Formattazione condizionale basata su regole per oggetti visivi tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Permette di creare regole per applicare colore in modo condizionale allo sfondo o al carattere di una colonna in base a una specifica logica di business in una tabella o matrice.

#### <a name="show-and-hide-pages"></a>[Mostrare e nascondere pagine](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Talvolta si desidera che i lettori accedano al report, ma alcune delle pagine non sono ancora finite; ora è possibile nasconderle fino a quando non saranno pronte. In alternativa, è possibile nascondere le pagine dalla consultazione normale e i lettori potranno accedere alla pagina tramite segnalibri o drill-through.

#### <a name="bookmarking"></a>[Aggiunta di segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Per quanto riguarda i segnalibri, è possibile creare segnalibri in modo da fare una sintesi con i dati del report.

- [Evidenziazione incrociata per i segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): i segnalibri gestiscono e visualizzano lo stato di evidenziazione incrociata della pagina del report nel momento in cui è stato creato il segnalibro.
- [Più flessibilità nei segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): i segnalibri riflettono le proprietà impostate nel report e influiscono solo sugli oggetti visivi scelti.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Selezione multipla di punti dati in più grafici](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selezionare più punti dati in più grafici e applicare il filtro incrociato all'intera pagina.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Sincronizzazione dei filtri dei dati tra più pagine di un report](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

È possibile applicare un filtro dei dati a una, due o più pagine in un report.

#### <a name="quick-measures"></a>[Misure rapide](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Creare nuove misure basate su misure e colonne numeriche esistenti in una tabella.

#### <a name="drilling-down-filters-other-visuals"></a>[Drill-down di filtri su altri oggetti visivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Quando si esegue il drill-down in una categoria specificata in un oggetto visivo, è possibile che filtri tutti gli oggetti visivi nella pagina in base alla stessa categoria.

### <a name="visuals-updates"></a>Aggiornamenti di oggetti visivi

- [Allineamento delle celle per tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Visualizzazione di unità e controllo di precisione per colonne tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Overflow delle etichette dati per gli oggetti visivi grafici a barre e istogrammi](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Controllo del colore di sfondo delle etichette dati per oggetti visivi cartesiani e mappe](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Controllo del riempimento di barre/colonne](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Incremento dell'area usata per le etichette degli assi nei grafici](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Oggetto visivo a dispersione da raggruppamenti dell'asse x e y](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Campionamento ad alta densità per le mappe in base a latitudine e longitudine](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Filtri dei dati reattivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Aggiunta di una data di ancoraggio a un filtro dei dati per la data relativa](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Reporting

- [Disattivare l'intestazione dell'oggetto visivo in modalità di lettura per un report](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Opzioni del report per le origini dati lente](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Posizionamento migliorato degli oggetti visivi predefiniti](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Controllo dell'ordinamento degli oggetti visivi attraverso il riquadro di selezione](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Blocco di oggetti nel report](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Ricerca nei riquadri formattazione e analisi](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Riquadro delle proprietà del campo e descrizioni del campo](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Analisi

- [UTCNOW() e UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Contrassegnare una tabella con data personalizzata](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Applicare filtri di drill su altri oggetti visivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formattazione a livello di cella per modelli multidimensionali di Analysis Services (AS) per schede con più righe](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Prestazioni

- [Miglioramenti delle prestazioni del filtro](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Miglioramenti delle prestazioni di DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Miglioramenti delle prestazioni di apertura e salvataggio](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Miglioramenti per "Mostra elementi senza dati"](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Server di report

#### <a name="export-to-accessible-pdf"></a>Esportare in formato PDF accessibile

Quando si esporta un report impaginato (RDL) in formato PDF, è possibile ottenere un file PDF accessibile/con tag. Ha dimensioni maggiori ma è più agevole la sua lettura e consultazione tramite lettori a schermo e altre tecnologie per l'accesso facilitato. Il PDF accessibile si abilita impostando le informazioni sul dispositivo **PDF accessibile** su **True**. Vedere [Impostazioni relative alle informazioni sul dispositivo PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) e [Changing Device Information Settings](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings) (Modifica delle impostazioni sul dispositivo).

### <a name="other-improvements"></a>Altri miglioramenti

- [Aggiungere una colonna da miglioramenti di esempi](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Collegamento veloce a Servizi di consulenza](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Segnalazione errori migliorata](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Visualizzare gli errori precedentemente riscontrati](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Ottobre 2017

### <a name="power-bi-report-data-sources"></a>Origini dati dei report di Power BI

I report di Power BI nel server di report di Power BI possono connettersi a diverse origini dati. È possibile importare i dati e pianificare l'aggiornamento dei dati oppure eseguire direttamente query sui dati usando DirectQuery o una connessione dinamica a SQL Server Analysis Services. Per un elenco delle origini dati che supportano gli aggiornamenti pianificati e delle origini dati che supportano DirectQuery, vedere "Origini dati dei report di Power BI nel server di report di Power BI".

### <a name="scheduled-data-refresh-for-imported-data"></a>Aggiornamento pianificato dei dati per i dati importati

In Server di report di Power BI è possibile configurare un aggiornamento pianificato dei dati per mantenere aggiornati i dati dei report di Power BI con un modello incorporato, invece che tramite una connessione dinamica o DirectQuery. Con un modello incorporato i dati vengono importati, quindi risultano disconnessi dall'origine dati originale. È quindi necessario aggiornare i dati per assicurarsi che siano recenti e un aggiornamento pianificato è l'approccio ottimale. Per altre informazioni, vedere "Aggiornamento pianificato per i report di Power BI nel server di report di Microsoft Power BI".

### <a name="editing-power-bi-reports-from-the-server"></a>Modifica dei report di Power BI dal server

È possibile aprire e modificare i file di report di Power BI (con estensione pbix) dal server, ma viene restituito il file originale caricato. **Se i dati sono stati aggiornati dal server, non verranno aggiornati alla prima apertura del file**. È necessario eseguire l'aggiornamento manuale in locale per visualizzare le modifiche.

### <a name="large-file-uploaddownload"></a>Caricamento/Download di file di grandi dimensioni

È possibile caricare file di dimensioni massime di 2 GB, anche se per impostazione predefinita questo limite è impostato su 1 GB in nelle impostazioni del server di report in SQL Server Management Studio (SSMS).  Questi file vengono archiviati nel database, analogamente a SharePoint, e non è necessaria alcuna configurazione speciale per il catalogo di SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Accesso ai set di dati condivisi come feed OData

È possibile accedere ai set di dati condivisi da Power BI Desktop con un feed OData. Per altre informazioni, vedere [Accessing shared datasets as OData feeds in Power BI Report Server](access-dataset-odata.md) (Accesso ai set di dati condivisi come feed OData nel server di report di Power BI).

### <a name="scale-out"></a>Aumento delle istanze

Questa versione supporta l'aumento delle istanze. Usare un servizio di bilanciamento del carico e configurare l'affinità del server per ottenere un'esperienza ottimale. Questo scenario non è stato ancora ottimizzato per l'aumento delle istanze, quindi è possibile che i modelli vengano replicati in più nodi. Lo scenario funziona senza il servizio di bilanciamento del carico di rete e le sessioni permanenti. Si noterà tuttavia un uso eccessivo della memoria nei nodi, perché il modello viene caricato N volte, e le prestazioni risulteranno rallentate tra le connessioni, poiché il modello viene sottoposto a streaming quando raggiunge un nuovo nodo tra le richieste.  

### <a name="administrator-settings"></a>Impostazioni dell'amministratore

Gli amministratori possono configurare le proprietà seguenti in Proprietà avanzate di SSMS per la server farm:

* EnableCustomVisuals: Vero/Falso
* EnablePowerBIReportEmbeddedModels: Vero/Falso
* EnablePowerBIReportExportData: Vero/Falso
* MaxFileSizeMb: il valore predefinito è ora 1000
* ModelCleanupCycleMinutes: frequenza della verifica per la rimozione dei modelli dalla memoria
* ModelExpirationMinutes: tempo di attesa prima della scadenza e della rimozione del modello in base all'ora dell'ultimo uso
* ScheduleRefreshTimeoutMinutes: tempo necessario per l'aggiornamento dei dati per un modello. Il valore predefinito è due ore.  Non è previsto alcun limite rigido massimo.

**File di configurazione rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API Developer

L'API Developer (API REST) introdotta per SSRS 2017 è stata estesa per consentire il funzionamento del Server di report di Power BI con i file di Excel e i file con estensione pbix. Un caso d'uso possibile consiste nello scaricare i file dal server a livello di codice, aggiornarli e quindi pubblicarli di nuovo. Questo è l'unico modo per aggiornare le cartelle di lavoro di Excel con i modelli PowerPivot, ad esempio.

È disponibile una nuova API separata per file di grandi dimensioni, che verrà aggiornata nella versione di Server di report di Power BI di Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>Footprint di memoria di SQL Server Analysis Services (SSAS) e del server di report di Power BI

Il server di report di Power BI ospita ora internamente SQL Server Analysis Services (SSAS). Ciò non riguarda in modo specifico l'aggiornamento pianificato. L'hosting di SSAS può espandere notevolmente il footprint di memoria del server di report. Il file di configurazione AS.ini è disponibile nei nodi del server. Se quindi si ha familiarità con SSAS, è consigliabile aggiornare le impostazioni, inclusi il limite massimo di memoria, la memorizzazione nella cache del disco e così via. Per informazioni dettagliate, vedere [Proprietà del server in Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services).

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Visualizzazione e interazione con le cartelle di lavoro di Excel

Excel e Power BI includono strumenti unici nel settore. Insieme consentono ai business analyst di raccogliere, strutturare, analizzare ed esplorare visivamente i dati con maggiore facilità. Oltre a visualizzare i report di Power BI nel portale Web, gli utenti aziendali possono ora visualizzare le cartelle di lavoro di Excel nel Server di report di Power BI e hanno quindi ha disposizione un'unica posizione per la pubblicazione e la visualizzazione del proprio contenuto self-service di Microsoft BI.

È stata pubblicata una [procedura dettagliata per l'aggiunta di Office Online Server (OOS) all'ambiente di anteprima del Server di report di Power BI](excel-oos.md). I clienti con un account per contratti multilicenza possono scaricare Office Online Server dal Volume License Servicing Center senza costi aggiuntivi e con funzionalità di sola visualizzazione. Dopo la configurazione, gli utenti possono visualizzare e interagire con le cartelle di lavoro di Excel che hanno le caratteristiche seguenti:

* Nessuna dipendenza da origini dati esterne
* Connessione dinamica a un'origine dati esterna di SQL Server Analysis Services
* Modello di dati di PowerPivot

### <a name="support-for-new-table-and-matrix-visuals"></a>Supporto per nuovi oggetti visivi di tipo tabella e matrice

Il server di report di Power BI supporta ora i nuovi oggetti visivi di tipo tabella e matrice di Power BI. Per creare report con tali oggetti visivi, sarà necessaria una versione aggiornata di Power BI Desktop per la versione di ottobre 2017. Non è possibile installarla side-by-side con la versione di Power BI Desktop di giugno 2017. Per la versione più aggiornata di Power BI Desktop, nella [pagina di download del server di report di Power BI](https://powerbi.microsoft.com/report-server/) selezionare **Opzioni avanzate di download**.

## <a name="june-2017"></a>Giugno 2017

* Il server di report di Power BI è disponibile a livello generale (GA).

## <a name="may-2017"></a>Maggio 2017

* L'anteprima di server di report di Power BI è stata resa disponibile
* Possibilità di pubblicare report di Power BI locali
  * Supporto per gli oggetti visivi di Power BI
  * Supporto solo per **connessioni dinamiche di Analysis Services** con altre origini dati previste.
  * App Power BI per dispositivi mobili aggiornata in modo da visualizzare i report di Power BI ospitati nel Server di Report di Power BI
* Miglioramento della collaborazione nei report con commenti

## <a name="next-steps"></a>Passaggi successivi

Vedere queste fonti per tenersi aggiornati sulle nuove funzionalità di Server di report di Power BI.

* [Blog di Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* Il [canale YouTube Guy in a Cube](https://aka.ms/guyinacube)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
