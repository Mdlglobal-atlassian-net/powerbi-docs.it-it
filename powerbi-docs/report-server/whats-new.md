---
title: Novità del Server di report di Power BI
description: Informazioni sulle novità del Server di report di Power BI. Questa sezione riguarda le funzionalità principali e viene aggiornata con il rilascio di nuovi elementi.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2019
ms.openlocfilehash: 2a65baf94abcb79dac7bb9419ad67124f2b65bb8
ms.sourcegitcommit: 2c49a7cee9c77f46830ddfa59fdedbf30186d389
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54488938"
---
# <a name="whats-new-in-power-bi-report-server"></a>Novità del Server di report di Power BI

Informazioni sulle novità del Server di report di Power BI. Questo articolo riguarda le funzionalità principali e viene aggiornato con il rilascio di nuovi elementi.

Per scaricare le versioni più recenti del server di report di Power BI e di Power BI Desktop ottimizzato per il server di report di Power BI, visitare [Creazione di report in locale con il server di report di Power BI](https://powerbi.microsoft.com/report-server/).

Per informazioni sulle "Novità" di Power BI, vedere:

* [Novità del servizio Power BI](../service-whats-new.md)
* [Novità di Power BI Desktop](../desktop-latest-update.md)
* [Novità delle app per dispositivi mobili per Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2019"></a>Gennaio 2019

Supporto delle funzionalità seguenti nei report di Power BI:

[**Sicurezza a livello di riga**](row-level-security-report-server.md) L'impostazione della sicurezza a livello di riga con il server di report di Power BI può limitare l'accesso ai dati per determinati utenti. I filtri limitano l'accesso ai dati a livello di riga ed è possibile definirli all'interno dei ruoli.

[**Espandere e comprimere le intestazioni di riga di matrice**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) È stata aggiunta la possibilità di espandere e comprimere le singole intestazioni di riga, una delle funzionalità più richieste per gli oggetti visivi.

[**Copia e incolla tra file con estensione pbix**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) È possibile copiare gli oggetti visivi tra file con estensione pbix mediante il menu di scelta rapida dell'oggetto visivo o con la scelta rapida da tastiera standard Ctrl+C e quindi incollarli in un altro report con Ctrl+V.

[**Guide intelligenti per l'allineamento**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Le guide intelligenti per l'allineamento vengono visualizzate durante lo spostamento di oggetti nella pagina del report, come in PowerPoint, per facilitare l'allineamento di tutti gli elementi della pagina. Le guide intelligenti vengono visualizzate ogni volta che si trascina o ridimensiona un elemento nella pagina. Quando si sposta un oggetto vicino a un altro, l'oggetto viene ancorato in una posizione allineata con l'altro oggetto.

**Funzionalità di accessibilità** Le funzionalità di accessibilità sono troppe per elencarle tutte: ad esempio il [supporto per l'accessibilità al riquadro elenco campi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Il riquadro elenco di campi è completamente accessibile. È possibile spostarsi nel riquadro solo con la tastiera e un'utilità per la lettura dello schermo e usare il menu di scelta rapida per aggiungere campi alla pagina del report.

### <a name="administrator-settings"></a>Impostazioni dell'amministratore

Gli amministratori possono configurare le proprietà seguenti in Proprietà avanzate di SSMS per la server farm:

**AllowedResourceExtensionsForUpload** Possibilità di impostare le estensioni delle risorse caricabili nel server di report. Non è obbligatorio includere le estensioni per i tipi di file predefiniti, ad esempio &ast;.rdl e &ast;.pbix. L'impostazione predefinita è "&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx". 

**SupportedHyperlinkSchemes** Consente di impostare un elenco delimitato da virgole degli schemi URI definibili nelle azioni CollegamentoIpertestuale autorizzate per il rendering o "&ast;" per abilitare tutti gli schemi di collegamento ipertestuale. Se ad esempio si imposta "http,https" sono consentiti i collegamenti ipertestuali a "https://www. contoso.com", ma vengono rimossi i collegamenti ipertestuali a "mailto:bill@contoso.com" o "javascript:window.open('www.contoso.com', '_blank')". L'impostazione predefinita è "&ast;".

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

#### <a name="custom-visuals"></a>Elementi visivi personalizzati

- La versione dell'API fornita con questa versione è 1.13.0.

- Per gli oggetti visivi personalizzati è ora possibile eseguire il fallback a una versione precedente compatibile con la versione corrente dell'API server (se disponibile).

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

### <a name="modeling"></a>Creazione di modelli

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

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Formattazione condizionale basata su regole per oggetti visivi tabella e matrice](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Permette di creare regole per applicare colore in modo condizionale allo sfondo o al carattere di una colonna in base a una specifica logica di business in una tabella o matrice.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Mostrare e nascondere pagine](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Talvolta si desidera che i lettori accedano al report, ma alcune delle pagine non sono ancora finite; ora è possibile nasconderle fino a quando non saranno pronte. In alternativa, è possibile nascondere le pagine dalla consultazione normale e i lettori potranno accedere alla pagina tramite segnalibri o drill-through.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Aggiunta di segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Per quanto riguarda i segnalibri, è possibile creare segnalibri in modo da fare una sintesi con i dati del report.

- [Evidenziazione incrociata per i segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): i segnalibri gestiscono e visualizzano lo stato di evidenziazione incrociata della pagina del report nel momento in cui è stato creato il segnalibro.
- [Più flessibilità nei segnalibri](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): i segnalibri riflettono le proprietà impostate nel report e influiscono solo sugli oggetti visivi scelti.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Selezione multipla di punti dati in più grafici](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selezionare più punti dati in più grafici e applicare il filtro incrociato all'intera pagina.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Sincronizzazione dei filtri dei dati tra più pagine di un report](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

È possibile applicare un filtro dei dati a una, due o più pagine in un report.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Misure rapide](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Creare nuove misure basate su misure e colonne numeriche esistenti in una tabella.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[Drill-down di filtri su altri oggetti visivi](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

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

È possibile aprire e modificare i file di report di Power BI (con estensione pbix) dal server, ma viene restituito il file originale caricato.  Quindi, **se i dati sono stati aggiornati dal server, non verranno aggiornati alla prima apertura del file**. È necessario eseguire l'aggiornamento manuale in locale per visualizzare le modifiche.

### <a name="large-file-uploaddownload"></a>Caricamento/Download di file di grandi dimensioni

È possibile caricare file di dimensioni massime di 2 GB, anche se per impostazione predefinita questo limite è impostato su 1 GB in nelle impostazioni del server di report in SQL Server Management Studio (SSMS).  Questi file vengono archiviati nel database, analogamente a SharePoint, e non è necessaria alcuna configurazione speciale per il catalogo di SQL Server.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Accesso ai set di dati condivisi come feed OData

È possibile accedere ai set di dati condivisi da Power BI Desktop con un feed OData. Per altre informazioni, vedere [Accessing shared datasets as OData feeds in Power BI Report Server](access-dataset-odata.md) (Accesso ai set di dati condivisi come feed OData nel server di report di Power BI).

### <a name="scale-out"></a>Aumento delle istanze

Questa versione supporta l'aumento delle istanze. Usare un servizio di bilanciamento del carico e configurare l'affinità del server per ottenere un'esperienza ottimale. Si noti che questo scenario non è stato ancora ottimizzato per l'aumento delle istanze, quindi è possibile che i modelli vengano replicati in più nodi. Lo scenario funziona senza il servizio di bilanciamento del carico di rete e le sessioni permanenti. Si noterà tuttavia un uso eccessivo della memoria nei nodi, perché il modello viene caricato N volte, e le prestazioni risulteranno rallentate tra le connessioni, poiché il modello viene sottoposto a streaming quando raggiunge un nuovo nodo tra le richieste.  

### <a name="administrator-settings"></a>Impostazioni dell'amministratore

Gli amministratori possono configurare le proprietà seguenti in Proprietà avanzate di SSMS per la server farm:

* EnableCustomVisuals: Vero/Falso
* EnablePowerBIReportEmbeddedModels: Vero/Falso
* EnablePowerBIReportExportData: Vero/Falso
* MaxFileSizeMb: il valore predefinito è ora 1000
* ModelCleanupCycleMinutes: frequenza della verifica per la rimozione dei modelli dalla memoria
* ModelExpirationMinutes: tempo di attesa prima della scadenza e della rimozione del modello in base all'ora dell'ultimo uso
* ScheduleRefreshTimeoutMinutes: tempo necessario per l'aggiornamento dei dati per un modello. L'impostazione predefinita è due ore.  Non è previsto alcun limite rigido massimo.

**File di configurazione rsreportserver.config**

```
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

Si noti che è disponibile una nuova API separata per file di grandi dimensioni, che verrà aggiornata nella versione del server di report di Power BI di Swagger. 

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
  * Supporto per oggetti visivi personalizzati
  * Supporto solo per **connessioni dinamiche di Analysis Services** con altre origini dati previste.
  * App Power BI per dispositivi mobili aggiornata in modo da visualizzare i report di Power BI ospitati nel Server di Report di Power BI
* Miglioramento della collaborazione nei report con commenti

## <a name="next-steps"></a>Passaggi successivi

Vedere queste fonti per tenersi aggiornati sulle nuove funzionalità di Server di report di Power BI.

* [Blog di Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blog del team Server SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* Il [canale YouTube Guy in a Cube](https://aka.ms/guyinacube)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)