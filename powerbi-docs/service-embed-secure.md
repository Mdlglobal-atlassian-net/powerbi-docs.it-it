---
title: Incorporare un report in un portale o un sito Web sicuro
description: Power BI consente di incorporare con facilità funzionalità consente agli utenti di e incorporare in modo sicuro i report nei portali web interni.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222249"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Incorporare un report in un portale o un sito Web sicuro

Con la nuova **incorporamento** opzione per Power BI i report, è possibile in modo sicuro e facilmente incorporare report nei portali web interni. Questi portali possono essere **basati sul cloud** oppure **ospitate in locale**, ad esempio SharePoint 2019. I report incorporati rispettano tutti i dati e le autorizzazioni di sicurezza degli elementi dei attraverso [a livello di riga (RLS) security](service-admin-rls.md). Forniscono senza codice di incorporamento in qualsiasi portale che accetta un URL o un iFrame. 

Il **incorporamento** opzione supporta [filtri URL](service-url-filters.md) e impostazioni dell'URL. Permette l'integrazione con portali usando un approccio di poco codice che richiedono solo HTML e JavaScript conoscenza di base.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Come **incorporare** report di Power BI nei portali

1. La nuova opzione **Incorpora** è disponibile nel menu **File** per i report nel servizio Power BI.

    ![Opzione dell'elenco per l'incorporamento sicuro](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Selezionare il **incorporamento** opzione per aprire una finestra di dialogo che fornisce un collegamento e un iFrame, è possibile usare per incorporare il report in modo sicuro.

    ![Finestra di dialogo dell'opzione Incorpora](media/service-embed-secure/secure-embed-code-dialog.png)

3. Se un utente apre direttamente un URL del report o uno incorporati in un portale web, l'accesso a report richiede l'autenticazione. Se un utente ha non firmati di partecipare a Power BI nella sessione del browser, viene visualizzata la schermata seguente. Quando si seleziona **Accedi**, è stato possibile aprire una nuova finestra del browser o scheda. È possibile cercare i blocchi popup se essi non ottenere chiesto di accedere.

    ![Eseguire l'accesso per visualizzare questo report](media/service-embed-secure/secure-embed-sign-in.png)

4. Dopo che l'utente ha eseguito l'accesso, si apre il report, che mostra i dati e consentendo la navigazione e impostazione del filtro. Solo gli utenti che dispongono dell'autorizzazione view per visualizzare il report in Power BI. Tutti i [a livello di riga (RLS) security](service-admin-rls.md) vengono anche applicate regole. Infine, l'utente deve disporre di una licenza corretta, ovvero avere una licenza di Power BI Pro oppure il report deve essere in un'area di lavoro inclusa in una capacità di Power BI Premium. L'utente deve eseguire l'accesso ogni volta che aprono una nuova finestra del browser. Tuttavia, una volta effettuato l'accesso, altri report caricato automaticamente.

    ![Incorporare un report](media/service-embed-secure/secure-embed-report.png)

5. Quando si usa un iFrame, potrebbe essere necessario modificare il **altezza** e **larghezza** in modo che rientrano in una pagina web del portale.

    ![Impostare altezza e larghezza](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Concessione dell'accesso al report

Il **incorporamento** opzione non consente automaticamente agli utenti di visualizzare il report. Visualizzare le autorizzazioni vengono impostate nel servizio Power BI.

Nel servizio Power BI, è possibile condividere i report incorporati con gli utenti che richiedono l'accesso. Se si usa un gruppo di Office 365, è possibile elencare l'utente come membro dell'area di lavoro di app. Per altre informazioni, vedere come [gestire l'area di lavoro di app in Power BI e Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Gestione delle licenze

Per visualizzare il report incorporato, gli utenti devono avere entrambi una licenza Power BI Pro o il contenuto deve essere in un'area di lavoro che si trova in una [capacità di Power BI Premium (EM o SKU P)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Personalizzare l'esperienza di incorporamento usando le impostazioni per l'URL

È possibile personalizzare l'esperienza dell'utente usando le impostazioni di input dell'URL di incorporamento. L'iFrame fornito, è possibile aggiornare l'URL **src** impostazioni.

| Property  | Descrizione  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | È possibile usare la **pageName** eseguire query sui parametri di stringa per impostare la pagina di report da aprire. È possibile trovare questo valore alla fine dell'URL di report quando si visualizza un report nel servizio Power BI, come illustrato di seguito. |  |  |  |
| Filtri URL  | È possibile usare [filtri URL](service-url-filters.md) nell'URL di incorporamento ricevuto dall'interfaccia utente Power BI per filtrare il contenuto di incorporamento. In questo modo è possibile realizzare integrazioni con poco codice e conoscenze di base di HTML e JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Set consente di aprire la pagina per un report incorporato 

È possibile trovare il **pageName** valore alla fine dell'URL di report quando si visualizza un report nel servizio Power BI.

1. Aprire il report dal servizio Power BI nel web browser e quindi copiare l'URL dell'indirizzo.

    ![Sezione del report](media/service-embed-secure/secure-embed-report-section.png)

2. Aggiungere l'impostazione **pageName** all'URL.

    ![Aggiungere pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrare il contenuto del report con i filtri URL 

È possibile usare [filtri URL](service-url-filters.md) per fornire visualizzazioni diverse dei report. Ad esempio, l'URL seguente filtra il report in modo da visualizzare i dati per il settore energetico.

L'uso combinato di **pageName** e [filtri URL](service-url-filters.md) offre grandi potenzialità. È possibile creare esperienze con codice HTML e JavaScript molto semplice.

Ecco ad esempio, un pulsante che è possibile aggiungere a una pagina HTML:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Se selezionata, il pulsante chiama una funzione per aggiornare l'iFrame con un URL aggiornato, che include il filtro del settore energetico.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtro](media/service-embed-secure/secure-embed-filter.png)

È possibile aggiungere tutti i pulsanti desiderati per creare un'esperienza personalizzata con poco codice. 

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* Non supporta utenti guest esterni con Azure Business To Business (B2B).

* L'incorporamento sicuro è disponibile per i report pubblicati nel servizio Power BI.

* L'utente deve eseguire l'accesso per visualizzare il report, ogni volta che aprono una nuova finestra del browser.

* Alcuni browser richiedono di aggiornare la pagina dopo l'iscrizione, soprattutto quando si usa la modalità InPrivate o in Incognito.

* Per ottenere un'esperienza single sign-on, usare l'incorporamento in SharePoint Online opzione o compilare un'integrazione personalizzata con il [utente è proprietario data](developer/embed-sample-for-your-organization.md) incorporamento (metodo). 

* La funzionalità di autenticazione automatica fornita con l'opzione **Incorpora** non funziona con l'API JavaScript di Power BI. Per l'API JavaScript di Power BI, usare il [utente è proprietario data](developer/embed-sample-for-your-organization.md) incorporamento (metodo). 

## <a name="next-steps"></a>Passaggi successivi

* [Modalità di condivisione del lavoro in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrare un report usando i parametri della stringa di query nell'URL](service-url-filters.md)

* [Incorporare con web part report in SharePoint Online](service-embed-report-spo.md)

* [Pubblica sul Web da Power BI](service-publish-to-web.md)