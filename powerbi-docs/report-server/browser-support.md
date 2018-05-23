---
title: Supporto del browser per il server di report di Power BI
description: Informazioni su quali versioni del browser sono supportate per la gestione e la visualizzazione del server di report di Power BI e i controlli del Visualizzatore report.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 01/25/2018
ms.author: maghan
ms.openlocfilehash: 23eea014ca4554a2df676cf1fe0be54c2b69d15a
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="browser-support-for-power-bi-report-server"></a>Supporto del browser per il server di report di Power BI
Informazioni su quali versioni del browser sono supportate per la gestione e la visualizzazione del server di report di Power BI e i controlli del Visualizzatore report.

## <a name="browser-requirements-for-the-web-portal"></a>Requisiti del browser per il portale Web
Di seguito è riportato l'elenco corrente dei browser supportati per il portale Web.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone e iPad con iOS 10*

* Apple Safari (+)

**Google Android**  
*Telefoni e tablet con Android 4.4 (KitKat) o versione successiva*

* Google Chrome (+)
  
  **(+)**  Ultima versione pubblicamente rilasciata

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Requisiti del browser per il controllo Web Visualizzatore report (2015)
Di seguito è riportato l'elenco corrente dei browser supportati con il controllo Web Visualizzatore report. Il visualizzatore di report supporta la visualizzazione di report dal portale Web.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)**  Ultima versione pubblicamente rilasciata

### <a name="authentication-requirements"></a>Requisiti di autenticazione
I browser supportano schemi di autenticazione specifici che devono essere gestiti dal server di report perché la richiesta del client riesca. La tabella seguente identifica i tipi di autenticazione predefiniti supportati da ogni browser eseguito in un sistema operativo Windows.

| **Tipo di browser** | **Supporta** | **Impostazione predefinita del browser** | **Impostazione predefinita del server** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, Basic |Negotiate |Sì. Le impostazioni di autenticazione predefinite funzionano con Microsoft Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, Basic |Negotiate |Sì. Le impostazioni di autenticazione predefinite funzionano con Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, Basic |Negotiate |Sì. Le impostazioni di autenticazione predefinite funzionano con Chrome. |
| **Mozilla Firefox**(+) |NTLM, Basic |NTLM |Sì. Le impostazioni di autenticazione predefinite funzionano con Firefox. |
| **Apple Safari**(+) |NTLM, Basic |Basic |Sì. Le impostazioni di autenticazione predefinite funzionano con Safari. |

 **(+)**  Ultima versione pubblicamente rilasciata

### <a name="script-requirements-for-viewing-reports"></a>Requisiti di script per la visualizzazione dei report
Per usare il visualizzatore di report, configurare il browser per eseguire script.

Se lo scripting non è abilitato, verrà visualizzato un messaggio di errore simile al seguente quando si apre un report:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Se si sceglie di visualizzare il report senza il supporto degli script, viene eseguito il rendering del report in HTML senza le funzionalità di visualizzatore report, ad esempio la barra degli strumenti dei report e la mappa documento.

> [!NOTE]
> La barra degli strumenti dei report fa parte del componente Visualizzatore HTML. Per impostazione predefinita la barra degli strumenti viene visualizzata nella parte superiore di ogni report di cui viene eseguito il rendering in una finestra del browser. Il visualizzatore di report fornisce funzionalità che includono la possibilità di cercare informazioni nel report, scorrere fino a una pagina specifica e adattare le dimensioni della pagina per la visualizzazione. Per altre informazioni sulla barra degli strumenti dei report o sul visualizzatore HTML, vedere questo articolo sul [visualizzatore HTML e la barra degli strumenti dei report](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Supporto browser per controlli del server Web Visualizzatore report in Visual Studio
Il controllo server Web Visualizzatore report viene usato per incorporare la funzionalità di report in un'applicazione Web ASP.NET. Per altre informazioni su come ottenere il controllo Visualizzatore report, vedere l'[introduzione all'integrazione di Reporting Services con i controlli Visualizzatore report](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Usare un browser con il supporto script abilitato. Se il browser non può eseguire script, non è possibile visualizzare il report.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)**  Ultima versione pubblicamente rilasciata

## <a name="next-steps"></a>Passaggi successivi
[Manuale per l'amministratore](admin-handbook-overview.md)  
[Installare il server di report di Power BI](install-report-server.md)  
[Installare Generatore report](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Scaricare SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

