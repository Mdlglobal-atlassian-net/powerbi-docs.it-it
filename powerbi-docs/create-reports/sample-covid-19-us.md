---
title: Esempio di rilevamento del COVID-19 per enti locali e statali degli Stati Uniti
description: Scaricare e modificare il report di esempio con dati a livello locale e statale per la pandemia di COVID-19.
author: LukaszPawlowski-MS
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/28/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 8cdc4a9a78c20c7c4e6986b63a3af61a319df1b6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82584918"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>Esempio di rilevamento del COVID-19 per enti locali e statali degli Stati Uniti

Il team di Power BI ha creato un esempio di rilevamento del COVID-19 che consente alle istituzioni statali e locali degli Stati Uniti di pubblicare o personalizzare un report interattivo sul COVID-19. Con Power BI Desktop è possibile analizzare e visualizzare i dati sul COVID-19 per tenere la comunità informata a livello di città, contee, stati e a livello nazionale. Usando l'opzione Pubblica sul Web da Power BI, è quindi possibile condividere il report pubblicamente per informare i cittadini. L'articolo presenta diverse opzioni per l'uso delle visualizzazioni interattive di Power BI nelle storie pubblicate, in blog o siti Web.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="Esempio di rilevamento del COVID-19 con dati USA":::

Questo articolo illustra come:

- Copiare il codice di incorporamento e inserirlo nel proprio sito. 
- Eseguire personalizzazioni, come ad esempio la formattazione di uno stato specifico.
- Pubblicare nel servizio Power BI.
- Pubblicare sul Web. 
- Unire questi dati con i dati provenienti da un'altra origine. 

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare a usare Power BI per pubblicare questo tipo di dati, è necessario soddisfare i prerequisiti seguenti:

- Scaricare la versione gratuita dell'app [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Iscriversi al [servizio Power BI](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Opzione 1: codice di incorporamento predefinito

Microsoft ha pubblicato il report di esempio e ha creato un codice di incorporamento per la pubblicazione sul Web. È possibile usare il codice di incorporamento per incorporare l'esempio completo, inclusa la vista a livello nazionale, ed eseguire il drill-down a livello di stato e di contea nel proprio sito Web. Prima di pubblicare questi dati, è consigliabile esaminare le [dichiarazioni di non responsabilità](#disclaimers) in questo articolo.

Per includere il grafico interattivo nel sito, copiare e incollare il codice di incorporamento seguente nel punto della pagina Web in cui si vuole che il grafico venga visualizzato.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

Il codice di incorporamento è un elemento iFrame HTML che può essere inserito in qualsiasi pagina HTML. Modificare la larghezza e l'altezza dell'iFrame per adattarlo all'interno del sito. Il report di esempio viene creato in 16:9, è quindi necessario scegliere delle dimensioni che rispettino tale proporzione. Una volta implementato correttamente, l'elemento grafico viene visualizzato senza bordi grigi aggiuntivi. Quando si apportano queste modifiche, è utile [rivedere i suggerimenti per il ridimensionamento dell'iFrame](../service-publish-to-web.md#tips-for-iframe-height-and-width).

## <a name="option-2-customize-the-sample-power-bi-file"></a>Opzione 2: personalizzare il file di Power BI di esempio

Il file di Power BI contiene i dati e le immagini interattive in un formato di file con estensione pbix che è possibile modificare in Power BI Desktop.  

Una personalizzazione tipica consiste nel filtrare il report in base a uno stato specifico e quindi creare il proprio codice di incorporamento per la pubblicazione sul Web per il report personalizzato.

I dati di USAFacts sono disponibili con una licenza Creative Commons che richiede l'attribuzione. Prima di pubblicare questi dati, esaminare le [dichiarazioni di non responsabilità](#disclaimers).

Per iniziare, [scaricare il file con estensione pbix (qui)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Modificare il report 

1. Scaricare la versione più recente dell'app gratuita [Power BI Desktop](https://powerbi.microsoft.com/desktop/), se non è già stato fatto. 

2. Scaricare il [file con estensione pbix](https://go.microsoft.com/fwlink/?linkid=2125058), se non è già stato fatto, e aprirlo in Power BI Desktop.

3. Per filtrare il report in base a uno stato specifico, selezionare la freccia per espandere il riquadro Filtri.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Espandere il riquadro Filtri":::

4. Selezionare lo stato a cui si è interessati. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Selezionare uno stato":::

5. Per salvare il file, selezionare **File** > **Salva**. 

### <a name="refresh-your-report"></a>Aggiornare il report 

1. Selezionare il pulsante **Aggiorna**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Pulsante Aggiorna":::

2. Selezionare **Accesso anonimo** > **Connetti**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Selezionare Accesso anonimo":::

 
3. Selezionare **Ignora i controlli dei livelli di privacy per questo file**, se visualizzato > **Salva**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Selezionare i livelli di privacy":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Pubblicare il report nel servizio Power BI

Una volta personalizzato il report, [seguire la procedura descritta qui per pubblicarlo](../desktop-upload-desktop-files.md) nel servizio Power BI.

### <a name="configure-scheduled-refresh"></a>Configurare l'aggiornamento pianificato

Per mantenere aggiornati i dati del report, è possibile [configurare l'aggiornamento pianificato](../refresh-scheduled-refresh.md) dopo la pubblicazione del report.

Quando si segue la procedura, scegliere le opzioni seguenti:

1. Metodo di autenticazione delle credenziali dell'origine dati: Anonima
2. Impostazione del livello di privacy per questa origine dati: Pubblico

Per testare l'impostazione di aggiornamento, selezionare l'opzione [Aggiorna ora](../refresh-data.md#data-refresh) disponibile nell'elemento del set di dati.

I dati aggiornati vengono caricati ogni volta che viene eseguita la pianificazione. I dati sottostanti sono resi disponibili da USAFacts e potrebbero non essere aggiornati con la stessa frequenza specificata per l'aggiornamento del report. Per informazioni sull'ultimo aggiornamento dei dati sottostanti, vedere il [sito Web USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

Se si vuole pubblicare il report personalizzato nel proprio sito Web, è consigliabile configurare l'aggiornamento pianificato in modo che venga eseguito almeno con la frequenza con cui vengono aggiornati i dati USAFacts. Poiché USAFacts può aggiornare i dati in momenti diversi ogni giorno, è consigliabile configurare diversi aggiornamenti nell'arco della giornata. 

### <a name="create-a-publish-to-web-embed-code"></a>Creare un codice di incorporamento per la pubblicazione sul Web 

Per incorporare il report personalizzato nel proprio sito Web, seguire le istruzioni per [creare il codice di incorporamento per la pubblicazione sul Web](../service-publish-to-web.md#create-embed-codes-with-publish-to-web).

Una volta inserito il codice di incorporamento, inserire nel sito Web l'elemento iFrame della finestra di dialogo di conferma.

Se si apportano modifiche al report in Power BI Desktop, è possibile pubblicare il nuovo report sostituendo il precedente nel servizio Power BI. Il codice di incorporamento non cambia. Le modifiche al report o i dati aggiornati vengono visualizzati nel sito Web dopo circa un'ora. 

## <a name="option-3-mash-up-data-from-another-source"></a>Opzione 3: unire i dati provenienti da un'altra origine 

È anche possibile combinare i dati di questo report con i dati di un'altra origine. L'esempio seguente si basa sui dati della [Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19). Prima di pubblicare questi dati, è consigliabile esaminare le [dichiarazioni di non responsabilità](#disclaimers) in questo articolo.

1. Selezionare **Recupera dati** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Pulsante Recupera dati":::

2. Immettere l'URL seguente:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Selezionare i dati dal Web":::

3. Selezionare **OK**. 

    > [!NOTE]
    > Il collegamento pubblicato dalla Johns Hopkins University può cambiare. Per informazioni aggiornate, vedere la [pagina di GitHub della Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19).

4. Selezionare **Carica** per caricare il set di dati per il totale dei casi confermati in tutto il mondo.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Caricare i dati dal Web":::

    L'articolo [Connettersi a pagine Web da Power BI Desktop](../desktop-connect-to-web.md) offre altre informazioni sul caricamento dei dati dal Web.
    
È quindi possibile usare Power BI Desktop per visualizzare i dati. Infine, attenersi alla procedura descritta in **Opzione 2:** [Pubblicare il report nel servizio Power BI](#publish-your-report-to-the-power-bi-service) per pubblicare il report e creare un codice di incorporamento personalizzato. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Opzione 4: usare l'app modello COVID-19 US Tracking

Per offrire un'altra opzione, il team di Power BI ha creato l'*app modello* COVID-19 US Tracking per iniziare immediatamente. Le app modello sono bundle di report, dashboard e set di dati per un'origine dati specifica. È possibile scaricarle da AppSource, usarle o modificarle in base alle proprie esigenze e distribuirle ai colleghi. 

Questa app modello COVID-19 US Tracking contiene un report predefinito di metriche COVID-19 che è possibile usare così come sono, personalizzare direttamente nel servizio Power BI o scaricare per aggiungere altre origini dati, se necessario. Informazioni su come installare l'[app modello COVID-19 US Tracking](../connect-data/service-connect-to-covid-19-tracking.md) e iniziare subito.

## <a name="about-the-data-source-for-this-report"></a>Informazioni sull'origine dati per il report
Questo report interattivo combina i dati del Centers for Disease Control and Prevention (CDC) e delle agenzie sanitarie locali e statali. I dati a livello di contea vengono confermati facendo riferimento direttamente (tramite collegamento) ad agenzie locali e statali.

I dati provengono da USAFacts. A causa della frequenza degli aggiornamenti dei dati, è possibile che questi non riflettano i numeri esatti segnalati dalle organizzazioni governative o dai media. Per altre informazioni o per scaricare i dati, visitare il [sito Web USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Dichiarazioni di non responsabilità

Questo report e i dati sono forniti "come sono", "con tutti i difetti" e senza garanzia di alcun tipo. Microsoft non riconosce garanzie espresse né garanzie implicite di commerciabilità, idoneità a uno scopo specifico e non violazione.

I dati di USAFacts sono disponibili con una licenza Creative Commons. Per poterla usare è necessario citare USAFacts come provider di dati e pubblicare il collegamento a USAFacts. Per la procedura di attribuzione esatta, vedere la sezione **#MadewithUSAFacts** della pagina USAFacts, [Coronavirus negli Stati Uniti: mappatura del contagio da COVID-19 in stati e contee](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

I dati della Johns Hopkins University sono protetti da copyright 2020 della Johns Hopkins University, tutti i diritti riservati. Vengono forniti al pubblico esclusivamente a scopo didattico e di ricerca. Di seguito sono riportate le [condizioni complete per l'utilizzo](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) dei dati illustrati nell'esempio di unione dei dati. Sono disponibili altre informazioni sul [sito Web Johns Hopkins University](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Passaggi successivi

[Ottenere esempi per Power BI](../sample-datasets.md)