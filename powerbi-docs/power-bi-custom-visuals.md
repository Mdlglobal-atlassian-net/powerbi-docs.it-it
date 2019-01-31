---
title: Oggetti visivi personalizzati in Power BI
description: Visualizzazioni personalizzate in Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 1ebb9633451ab8e2f1b8cbf8ada743ce6c42692e
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55431132"
---
# <a name="custom-visuals-in-power-bi"></a>Oggetti visivi personalizzati in Power BI

Quando si crea o si modifica un report di Power BI, sono disponibili vari tipi di oggetti visivi. Gli oggetti visivi sono visualizzati nel riquadro **Visualizzazioni**. Quando si scarica [Power BI Desktop](https://powerbi.microsoft.com/desktop/) o si apre il [servizio Power BI](https://app.powerbi.com) questo set di oggetti visivi è incluso per impostazione predefinita.

![visualizzazioni](media/power-bi-custom-visuals/power-bi-visualizations.png)

Tuttavia, le possibilità non sono limitate a questo set preconfezionato. Selezionando i puntini di sospensione è possibile aprire un'altra origine di oggetti visivi per i report, gli *oggetti visivi personalizzati*.

Gli oggetti visivi personalizzati vengono creati dagli sviluppatori tramite l'SDK corrispondente per consentire agli utenti aziendali di visualizzare i dati in modo ottimale per le esigenze dell'azienda. Gli autori di report possono quindi importare i file degli oggetti visivi personalizzati nei report e usarli come qualsiasi altro oggetto visivo di Power BI. Gli oggetti visivi personalizzati sono elementi di primaria importanza in Power BI e possono essere filtrati, evidenziati, modificati, condivisi e così via.

Gli oggetti visivi personalizzati supportano tre tipi di canali di distribuzione:

* File di oggetti visivi personalizzati
* Oggetti visivi organizzazione
* Oggetti visivi del Marketplace

## <a name="custom-visual-files"></a>File di oggetti visivi personalizzati

Gli oggetti visivi personalizzati sono pacchetti che includono il codice per il rendering dei dati a loro passati. Chiunque può creare un oggetto visivo personalizzato e assemblarlo in un pacchetto come singolo file con estensione `.pbiviz`, che può essere importato in un report di Power BI.

> [!WARNING]
> Un oggetto visivo personalizzato può contenere codice rischioso a livello di sicurezza o privacy. Verificare che l'autore e l'origine dell'oggetto visivo personalizzato siano attendibili prima di importarlo nel report.

## <a name="organizational-visuals"></a>Oggetti visivi organizzazione

Gli amministratori di Power BI possono distribuire oggetti visivi personalizzati nella propria organizzazione, in modo che gli autori di report possano facilmente individuare e usare gli oggetti visivi personalizzati approvati dall'amministratore per l'uso all'interno dell'organizzazione. L'amministratore ha quindi il controllo e può scegliere gli oggetti visivi personalizzati specifici da distribuire nell'organizzazione, oltre ad avere a disposizione un modo semplice per gestire questi oggetti (ad esempio aggiornare la versione o abilitarli e disabilitarli). Per gli autori di report questo è un modo semplice per individuare gli oggetti visivi univoci per l'organizzazione, oltre a supportare l'aggiornamento semplice di tali oggetti visivi.

Per altri dettagli sugli oggetti visivi personalizzati dell'organizzazione, [leggere altre informazioni sugli oggetti visivi dell'organizzazione](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Oggetti visivi del Marketplace

I membri della community, così come Microsoft, offrono il loro contributo pubblicando oggetti visivi personalizzati nel Marketplace [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), da dove è possibile scaricarli e aggiungerli ai report in Power BI. Tutti questi oggetti visivi personalizzati sono stati testati e approvati da Microsoft per funzionalità e qualità.

Informazioni su [AppSource](developer/office-store.md) In breve, è il posto in cui è possibile trovare app, componenti aggiuntivi ed estensioni per il software Microsoft. [AppSource](https://appsource.microsoft.com/) connette milioni di utenti di prodotti come Office 365, Azure, Dynamics 365, Cortana e Power BI a soluzioni che li aiutano a lavorare in modo più efficiente, più intelligente o migliore rispetto a prima.

### <a name="certified-visuals"></a>Oggetti visivi certificati

Gli oggetti visivi certificati di Power BI sono oggetti visivi del Marketplace che hanno superato test di qualità rigorosi e sono supportati in ulteriori scenari, quali [sottoscrizioni di messaggi di posta elettronica](https://docs.microsoft.com/power-bi/service-report-subscribe) ed [esportazione in PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
Per visualizzare l'elenco di oggetti visivi personalizzati certificati o per inviare il proprio, vedere [Oggetti visivi personalizzati certificati](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified).

Gli sviluppatori Web interessati a creare visualizzazioni personalizzate e ad aggiungerle in AppSource, possono Vedere [Developing a Power BI custom visual](developer/custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI) e le informazioni su come [Pubblicare oggetti visivi personalizzati in AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals).

### <a name="import-a-custom-visual-from-a-file"></a>Importare un oggetto visivo personalizzato da un file

1. Nel riquadro Visualizzazioni selezionare i puntini di sospensione.

    ![visualizzazioni2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Nell'elenco a discesa selezionare **Importa da file**.

    ![importa da file](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. Nel menu Apri file selezionare il file con estensione `.pbiviz` che si vuole importare e quindi selezionare Apri. L'icona per l'oggetto visivo personalizzato viene aggiunta nella parte inferiore del riquadro Visualizzazioni e può essere usata nei report.

    ![cv importato](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importare oggetti visivi dell'organizzazione

1. Nel riquadro Visualizzazioni selezionare i puntini di sospensione.

    ![oggetto visivo org 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. Nell'elenco a discesa selezionare Importa dal Marketplace.

    ![oggetto visivo org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selezionare **ORGANIZZAZIONE PERSONALE** dal menu della scheda superiore.

    ![oggetto visivo org 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Scorrere l'elenco per trovare l'oggetto visivo da importare.

    ![oggetto visivo org 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Selezionare **Aggiungi** per importare l'oggetto visivo personalizzato. L'icona per l'oggetto visivo personalizzato viene aggiunta nella parte inferiore del riquadro Visualizzazioni e può essere usata nei report.

    ![oggetto visivo org 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Scaricare o importare oggetti visivi personalizzati da Microsoft AppSource

Sono disponibili due opzioni per scaricare e importare gli oggetti visivi personalizza, da Power BI e dal sito Web di AppSource.

### <a name="import-custom-visuals-from-within-power-bi"></a>Importare oggetti visivi personalizzati da Power BI

1. Nel riquadro Visualizzazioni selezionare i puntini di sospensione.

    ![visualizzazioni 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Nell'elenco a discesa selezionare **Importa dal Marketplace**.

    ![oggetto visivo org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Scorrere l'elenco per trovare l'oggetto visivo da importare.

    ![importare l'oggetto visivo](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Per altre informazioni su uno degli oggetti visivi, evidenziarlo e selezionarlo.

    ![Seleziona](media/power-bi-custom-visuals/power-bi-select.png)

5. Nella pagina dei dettagli è possibile visualizzare schermate, video, una descrizione dettagliata e altro ancora.

    ![Sinottico](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Scorrere verso il basso per visualizzare i commenti.

    ![Recensioni](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Selezionare Aggiungi per importare l'oggetto visivo personalizzato. L'icona per l'oggetto visivo personalizzato viene aggiunta nella parte inferiore del riquadro Visualizzazioni e può essere usata nei report.

    ![oggetto visivo importato](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Scaricare e importare oggetti visivi personalizzati da Microsoft AppSource

1. Accedere a [Microsoft AppSource](https://appsource.microsoft.com) e selezionare la scheda **App**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Andare alla [pagina dei risultati per le app](https://appsource.microsoft.com/marketplace/apps) in cui sono mostrate le app più popolari per ogni categoria, incluse le *app di Power BI*. Poiché occorre visualizzare gli oggetti visivi personalizzati, è necessario limitare i risultati selezionando **Oggetti visivi personalizzati** nell'elenco di spostamento a sinistra.

    ![Oggetti visivi di AppSource](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource mostra un riquadro per ogni oggetto visivo personalizzato.  Ogni riquadro presenta uno snapshot dell'oggetto visivo personalizzato, una breve descrizione e un collegamento per il download. Per visualizzare altri dettagli, selezionare il riquadro.

    ![Oggetto visivo selezionato personalizzato](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Nella pagina dei dettagli è possibile visualizzare schermate, video, una descrizione dettagliata e altro ancora. Per scaricare l'oggetto visivo personalizzato, selezionare **Scarica adesso** e accettare le Condizioni per l'utilizzo.

    ![Ottieni AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selezionare il collegamento per scaricare l'oggetto visivo personalizzato.

    ![Download](media/power-bi-custom-visuals/powerbi-custom-download.png)

    La pagina di download include anche le istruzioni su come importare l'oggetto visivo personalizzato in Power BI Desktop e nel servizio Power BI.

    È possibile scaricare anche un report di esempio che include l'oggetto visivo personalizzato e ne illustra le funzionalità.

    ![Esempio di prova](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Salvare il file '.pbiviz' e quindi aprire Power BI.

7. Importare il file '.pbiviz' nel report (vedere la sezione precedente [Importare un oggetto visivo personalizzato da un file](#import-a-custom-visuals-from-a-file)).

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Un oggetto visivo personalizzato viene aggiunto a un determinato report durante l'importazione. Se si vuole usare l'oggetto visivo in un altro report, è necessario importarlo anche in tale report. Quando un report con un oggetto visivo personalizzato viene salvato usando l'opzione **Salva con nome** , una copia dell'oggetto visivo personalizzato viene salvata con il nuovo report.

* Se il riquadro **Visualizzazioni** non è visualizzato, significa che l'utente non dispone delle autorizzazioni di modifica per il report.  È possibile aggiungere oggetti visivi personalizzati solo ai report che si è autorizzati a modificare e non ai report che sono stati semplicemente condivisi.

## <a name="troubleshoot"></a>Risoluzione dei problemi

Per informazioni sulla risoluzione dei problemi, consultare la pagina [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Risoluzione dei problemi degli oggetti visivi personalizzati di Power BI).

## <a name="faq"></a>DOMANDE FREQUENTI

Per altre informazioni e risposte, vedere le [Frequently asked questions about Power BI custom visuals](power-bi-custom-visuals-faq.md#organizational-custom-visuals) (Domande frequenti sugli oggetti visivi personalizzati di Power BI).

## <a name="next-steps"></a>Passaggi successivi

* [Visualizzazioni in Power BI](visuals/power-bi-report-visualizations.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/).
