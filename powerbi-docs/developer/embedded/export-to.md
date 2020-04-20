---
title: Esportare l'API dei report di Power BI
description: Informazioni su come esportare un report di Power BI incorporato
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/24/2020
ms.openlocfilehash: 472797cf30d6b88a59af5b3846e9b710bf4607c7
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267504"
---
# <a name="export-power-bi-report-to-file-preview"></a>Esportare report di Power BI in un file (anteprima)

L'API `exportToFile` consente di esportare un report di Power BI tramite una chiamata REST. Sono supportati i formati di file seguenti:
* **PPTX** (PowerPoint)
* **PDF**
* **PNG**
    * Quando si esegue l'esportazione in un file PNG, un report con più pagine viene compresso in un file ZIP
    * Ogni file all'interno del file ZIP rappresenta una pagina del report
    * I nomi di pagina corrispondono ai valori restituiti delle API [Get Pages](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) o [Get Pages in Group](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Esempi di utilizzo

La funzionalità di esportazione può essere usata in diversi modi. Ecco alcuni esempi:

* **Pulsante di invio alla stampa**: creare un pulsante nell'applicazione che, se selezionato, attiva un processo di esportazione. Il processo può esportare il report visualizzato in formato PDF o PPTX e, al termine, l'utente può ricevere il file come download. Con i segnalibri è possibile esportare il report in uno stato specifico, inclusi i filtri configurati, i filtri dei dati e le impostazioni aggiuntive. Poiché l'API è asincrona, la disponibilità del file potrebbe richiedere tempo.

* **Allegato di posta elettronica**: inviare un messaggio di posta elettronica automatizzato a intervalli prestabiliti con un report PDF allegato. Questo scenario può essere utile se si vuole automatizzare l'invio di un report settimanale ai dirigenti.

## <a name="using-the-api"></a>Uso dell'API

Prima di usare l'API, verificare che siano abilitate le [impostazioni del tenant amministratore](../../service-admin-portal.md#tenant-settings) seguenti:
* **Esporta report come presentazioni di PowerPoint o documenti PDF**: abilitata per impostazione predefinita.
* **Esporta report come file di immagine**: impostazione obbligatoria solo per i file *PNG* e disabilitata per impostazione predefinita.

L'API è asincrona. Quando viene chiamata l'API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile), viene attivato un processo di esportazione. Dopo l'attivazione di un processo di esportazione, usare il [polling](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) per tenere traccia del processo fino al suo completamento.

Durante il polling, l'API restituisce un numero che rappresenta la quantità di lavoro completata. Il lavoro in ogni processo di esportazione viene calcolato in base al numero di pagine del report. Tutte le pagine hanno lo stesso peso. Se ad esempio si sta esportando un report di 10 pagine e il polling restituisce 70, significa che l'API ha elaborato 7 delle 10 pagine del processo di esportazione.

Al termine dell'esportazione, la chiamata API di polling restituisce un [URL di Power BI](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) per recuperare il file. L'URL sarà disponibile per 24 ore.

## <a name="supported-features"></a>Caratteristiche supportate

### <a name="selecting-which-pages-to-print"></a>Selezione delle pagine da stampare

Specificare le pagine da stampare in base al valore restituito dalle API [Get Pages](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) o [Get Pages in Group](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup). È anche possibile specificare l'ordine delle pagine esportate.

### <a name="bookmarks"></a>Segnalibri

 È possibile usare l'API `exportToFile` per esportare a livello di codice un report in uno stato specifico, dopo aver applicato i filtri. Questa operazione viene eseguita con le funzionalità dei [segnalibri](../../consumer/end-user-bookmarks.md). Per esportare un report usando i segnalibri, usare l'[API JavaScript per i segnalibri](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 È ad esempio possibile usare il metodo `capturedBookmark.state` del segnalibro per acquisire le modifiche apportate da un utente specifico a un report e quindi esportarlo nello stato corrente.

I [segnalibri personali](../../consumer/end-user-bookmarks.md#personal-bookmarks) e i [filtri permanenti](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) non sono supportati.

### <a name="authentication"></a>Autenticazione

È possibile eseguire l'autenticazione con un utente (o utente master) o un'[entità servizio](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sicurezza a livello di riga

Con la [sicurezza a livello di riga](embedded-row-level-security.md) è possibile esportare un report in cui sono visualizzati i dati visibili solo a determinati utenti. Se ad esempio si esporta un report sulle vendite definito con ruoli regionali, è possibile filtrare il report a livello di codice in modo che venga visualizzata solo una determinata area.

Per esportare con la sicurezza a livello di riga, è necessario avere le autorizzazioni seguenti:
* Autorizzazioni di scrittura e ricondivisione per il set di dati a cui è connesso il report
* Se il report si trova in un'area di lavoro v1, è necessario essere l'amministratore dell'area di lavoro
* Se il report si trova in un'area di lavoro v2, è necessario essere un membro o un amministratore dell'area di lavoro

### <a name="data-protection"></a>Protezione dei dati

I formati PDF e PPTX supportano le [etichette di riservatezza](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi). Se si esporta un report con un'etichetta di riservatezza in un file PDF o PPTX, il file esportato visualizzerà il report con la relativa etichetta di riservatezza.

Un report con un'etichetta di riservatezza non può essere esportato in un file PDF o PPTX usando un'[entità servizio](embed-service-principal.md).

### <a name="localization"></a>Localizzazione

Quando si usa l'API `exportToFile`, è possibile passare le impostazioni internazionali desiderate. Le impostazioni di localizzazione influiscono sul modo in cui viene visualizzato il report, ad esempio modificando la formattazione in base alle impostazioni internazionali selezionate.

## <a name="concurrent-requests"></a>Richieste simultanee

`exportToFile` supporta le richieste di processi di esportazione simultanee. La tabella seguente illustra il numero di processi che è possibile eseguire contemporaneamente, a seconda dello SKU in cui si trova il report. Le richieste simultanee fanno riferimento alle pagine del report. Ad esempio, 20 pagine in una richiesta di esportazione in uno SKU A6 verranno elaborate simultaneamente. Questa operazione richiederà approssimativamente lo stesso tempo necessario per l'invio di 20 richieste di esportazione di una sola pagina.

Se un processo supera il numero di richieste simultanee, non viene completato. Se ad esempio si esportano tre pagine in uno SKU A1, il primo processo verrà eseguito e gli ultimi due attenderanno i successivi due cicli di esecuzione.

|SKU di Azure  |SKU di Office  |Numero massimo di richieste simultanee  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Limitazioni

* Il report che si sta esportando deve trovarsi all'interno di una capacità Premium o Embedded.
* Il set di dati del report che si sta esportando deve essere incluso in una capacità Premium o Embedded.
* Per le anteprime pubbliche, il numero di pagine di report di Power BI esportate all'ora è attualmente limitato a 50 per ogni capacità.
* I report esportati non possono avere una dimensione file superiore a 250 MB.
* Quando si esegue l'esportazione in formato PNG, le etichette di riservatezza non sono supportate.
* Un report con un'etichetta di riservatezza non può essere esportato in un file PDF o PPTX usando un'[entità servizio](embed-service-principal.md).
* Il numero di pagine che è possibile includere in un report esportato è 30. Se il report include più pagine, l'API restituisce un errore e il processo di esportazione viene annullato.
* I [segnalibri personali](../../consumer/end-user-bookmarks.md#personal-bookmarks) e i [filtri permanenti](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) non sono supportati.
* Gli oggetti visivi di Power BI elencati di seguito non sono supportati. Quando viene esportato un report contenente questi oggetti visivi, il rendering delle parti del report che contengono tali oggetti visivi non viene eseguito correttamente e viene visualizzato un simbolo di errore.
    * Oggetti visivi di Power BI non certificati
    * Oggetti visivi R
    * PowerApps
    * Oggetti visivi Python
    * Visio

## <a name="code-examples"></a>Esempi di codice

Quando si crea un processo di esportazione, è necessario seguire tre passaggi:

1. Invio di una richiesta di esportazione.
2. Polling.
3. Recupero del file.

Questa sezione presenta esempi per ogni passaggio.

### <a name="step-1---sending-an-export-request"></a>Passaggio 1: invio di una richiesta di esportazione

Il primo passaggio consiste nell'invio di una richiesta di esportazione. In questo esempio viene inviata una richiesta di esportazione per una pagina specifica.

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names.
        // To get the page names use the GetPages API.
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };
    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);
    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Passaggio 2: polling

Dopo aver inviato una richiesta di esportazione, usare il polling per definire quando il file di esportazione che si sta aspettando è pronto.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }
        var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;
        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);
    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Passaggio 3: recupero del file

Quando il polling restituisce un URL, usare questo esempio per recuperare il file ricevuto.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}
public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>Esempio end-to-end

Ecco un esempio end-to-end per l'esportazione di un report. Questo esempio include le fasi seguenti:
1. [Invio della richiesta di esportazione](#step-1---sending-an-export-request).
2. [Polling](#step-2---polling).
3. [Recupero del file](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }
        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Passaggi successivi

Vedere come incorporare contenuto per i clienti e l'organizzazione:

> [!div class="nextstepaction"]
>[Esportare il report impaginato in un file](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Incorporamento per i clienti](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)
