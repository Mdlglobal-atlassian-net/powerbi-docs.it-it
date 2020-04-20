---
title: Esportare l'API dei report di Power BI
description: Informazioni su come esportare un report impaginato di Power BI incorporato
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: acb13a70ea4693f447b70aa59da07cd91639de25
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2020
ms.locfileid: "81268766"
---
# <a name="export-paginated-report-to-file-preview"></a>Esportare il report impaginato in un file (anteprima)

L'API `exportToFile` consente di esportare un report impaginato di Power BI tramite una chiamata REST. Sono supportati i formati di file seguenti:
* **PPTX** (PowerPoint)
* **PDF**
* **XLSX** (Excel)
* **DOX** (Word)
* **CSV**
* **XML**
* **MHTML**
* **Immagine**
    * Quando si esegue l'esportazione in un'immagine, impostare il formato dell'immagine tramite l'impostazione del formato `OutputFormat`
    * I valori di OutputFormat supportati sono: .bmp, .emf, .gif, .jpeg, .png o .tiff (impostazione predefinita)

## <a name="usage-examples"></a>Esempi di utilizzo

La funzionalità di esportazione può essere usata in diversi modi. Ecco alcuni esempi:

* **Pulsante di invio alla stampa**: creare un pulsante nell'applicazione che, se selezionato, attiva un processo di esportazione. Il processo può esportare il report visualizzato in formato PDF o PPTX e, al termine, l'utente può ricevere il file come download. Usando i parametri del report e le impostazioni del formato è possibile esportare il report in uno stato specifico, inclusi i dati filtrati, le dimensioni di pagina personalizzate e altre impostazioni specifiche del formato. Poiché l'API è asincrona, la disponibilità del file potrebbe richiedere tempo.

* **Allegato di posta elettronica**: inviare un messaggio di posta elettronica automatizzato a intervalli prestabiliti con un report PDF allegato. Questo scenario può essere utile se si vuole automatizzare l'invio di un report settimanale ai dirigenti.

## <a name="using-the-api"></a>Uso dell'API

L'API è asincrona. Quando viene chiamata l'API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile), viene attivato un processo di esportazione. Dopo l'attivazione di un processo di esportazione, usare il [polling](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) per tenere traccia del processo fino al suo completamento.

Al termine dell'esportazione, la chiamata API di polling restituisce un [URL di Power BI](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) per recuperare il file. L'URL sarà disponibile per 24 ore.

## <a name="supported-features"></a>Caratteristiche supportate

### <a name="format-settings"></a>Impostazioni del formato

Specificare diverse impostazioni per ogni formato di file. Le proprietà e i valori supportati sono equivalenti ai [parametri delle informazioni sul dispositivo](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) per i parametri URL del report impaginato.

Di seguito sono riportati due esempi, uno per l'esportazione delle prime quattro pagine di un report con le dimensioni della pagina del report in un file con estensione pptx e l'altro per l'esportazione della terza pagina di un report in un file con estensione jpeg.

**Esportazione delle prime quattro pagine in un file con estensione pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Esportazione della terza pagina in un file con estensione jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Parametri di report

È possibile usare l'API `exportToFile` per esportare un report a livello di codice con un set di parametri del report. Questa operazione viene eseguita usando le funzionalità dei [parametri del report](../../paginated-reports/paginated-reports-parameters.md).

Di seguito è riportato un esempio per l'impostazione dei valori dei parametri del report.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Autenticazione

È possibile eseguire l'autenticazione con un utente (o utente master) o un'[entità servizio](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sicurezza a livello di riga

Quando si usa un set di dati di Power BI con la sicurezza a livello di riga definita come origine dati, è possibile esportare un report che mostra i dati visibili solo a determinati utenti. Se ad esempio si esporta un report sulle vendite definito con ruoli regionali, è possibile filtrare il report a livello di codice in modo che venga visualizzata solo una determinata area.

Per eseguire l'esportazione usando la sicurezza a livello di riga, è necessaria l'autorizzazione di lettura per il set di dati di Power BI usato dal report come origine dati.

Di seguito è riportato un esempio di come fornire un nome utente valido per la sicurezza a livello di riga.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Esempi di codice

Il Power BI API SDK usato negli esempi di codice può essere scaricato [qui](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

Quando si crea un processo di esportazione, è necessario seguire tre passaggi:

1. Invio di una richiesta di esportazione.
2. Polling.
3. Recupero del file.

Questa sezione presenta esempi per ogni passaggio.

### <a name="step-1---sending-an-export-request"></a>Passaggio 1: invio di una richiesta di esportazione

Il primo passaggio consiste nell'invio di una richiesta di esportazione. In questo esempio viene inviata una richiesta di esportazione per un intervallo di pagine, dimensioni e valori dei parametri del report specifici.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
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
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
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
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Esempio end-to-end

Ecco un esempio end-to-end per l'esportazione di un report. Questo esempio include le fasi seguenti:
1. [Invio della richiesta di esportazione](#step-1---sending-an-export-request).
2. [Polling](#step-2---polling).
3. [Recupero del file](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

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
>[Esportare il report nel file](export-to.md)

> [!div class="nextstepaction"]
>[Incorporamento per i clienti](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)