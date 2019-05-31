---
title: Creare un collegamento a una posizione specifica nelle app Power BI per dispositivi mobili
description: Informazioni su come creare un collegamento diretto a un dashboard, un riquadro o un report specifico nell'app Power BI per dispositivi mobili con un collegamento Uniform Resource Identifier (URI).
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906521"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Creare un collegamento a una posizione specifica nelle app Power BI per dispositivi mobili
È possibile utilizzare i collegamenti per accedere direttamente a elementi specifici in Power BI: Report, Dashboard e riquadro.

Esistono essenzialmente due scenari per l'uso di collegamenti in Power BI per dispositivi mobili: 

* Per aprire Power BI dal **all'esterno dell'app**e di accedere a contenuto specifico (report/dashboard/app). Si tratta in genere uno scenario di integrazione, quando si desidera aprire Power BI per dispositivi mobili da altre app. 
* Per **spostarsi** all'interno di Power BI. Si tratta in genere quando si desidera creare una navigazione personalizzata in Power BI.


## <a name="use-links-from-outside-of-power-bi"></a>Usare i collegamenti di fuori di Power BI
Quando si usa un collegamento all'esterno di app di Power BI, si desidera assicurarsi che verrà aperta dall'app, e se l'app non è installato nel dispositivo, quindi offrendo all'utente per installarlo. È stato creato un formato di collegamento speciale per supportare tale. Questo formato di collegamento, garantirà che il dispositivo usa l'app per aprire il collegamento, e se l'app non è installato nel dispositivo, verrà richiesto all'utente di Vai allo store per ottenerla.

Il collegamento deve iniziare con il codice seguente  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> Se il contenuto è ospitato nel Data Center speciali, ad esempio con governi, Cina, e così via. Il collegamento deve iniziare con l'indirizzo di Power BI a destra, ad esempio `app.powerbigov.us` o `app.powerbi.cn`.   
>


Il **PARAMS QUERY** sono:
* **azione** (obbligatorio) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **appId** = se si vuole aprire un report o un dashboard che fanno parte di un'app 
* **groupObjectId** = se si vuole aprire un report o un dashboard che fanno parte dell'area di lavoro (ma non l'area di lavoro)
* **dashboardObjectId** = ID oggetto del dashboard (se l'azione è OpenDashboard o OpenTile)
* **reportObjectId** = ID oggetto del report (se l'azione è ApriReport)
* **tileObjectId** = ID dell'oggetto riquadro (se azione OpenTile)
* **reportPage** = se si desidera aprire sezione del report specifica (se l'azione è ApriReport)
* **CTID** = ID dell'elemento organizzazione (rilevanti per uno scenario B2B. Ciò può essere omesso se l'elemento appartiene all'organizzazione dell'utente).

**Esempi:**

* Collegamento app aperte 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* Aprire il dashboard che fa parte di un'app 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* Apri report che fa parte di un'area di lavoro
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>Come ottenere il formato di collegamento a destra

#### <a name="links-of-apps-and-items-in-app"></a>Collegamenti di App e gli elementi nell'app

Per la **le App e i report e dashboard che fanno parte di un'app**, è il modo più semplice per ottenere il collegamento per tornare all'area di lavoro di app e scegliere "Aggiorna app". Verrà aperto l'esperienza "Publish app", e nella scheda accesso, si noterà una **collegamenti** sezione. Espansione di sezione e si verrà visualizzato l'elenco di app e tutti i relativi contenuti i collegamenti che è utilizzabile per l'accesso diretto.

![Pubblica i collegamenti di app di Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>Collegamenti di elementi non nell'app 

Per i report e dashboard che non fanno parte di un'app, è necessario estrarre l'ID dall'URL dell'elemento.

Ad esempio, per trovare il carattere di 36 **dashboard** ID di oggetto, passare al dashboard specifico nel servizio Power BI 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

Per trovare il carattere di 36 **report** ID di oggetto, passare al report specifico nel servizio Power BI.
Questo è un esempio di report da "Area di lavoro personale"

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
L'URL precedente contiene anche pagina del report specifica **"ReportSection3"** .

Questo è un esempio di un report da un'area di lavoro (non area di lavoro personale)

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Usare i collegamenti all'interno di Power BI

Collegamenti all'interno di Power BI Usa l'App per dispositivi mobili esattamente come nel servizio Power BI.

Se si desidera aggiungere un collegamento al report che punta a un altro elemento di Power BI, è possibile copiare solo tale URL dell'elemento dalla barra degli indirizzi del browser. Altre informazioni, vedere [come aggiungere un collegamento ipertestuale a una casella di testo in un report](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="use-report-url-with-filter"></a>Usare l'URL del report con filtro
Uguale a servizio Power BI, le app di Power BI per dispositivi mobili supportano anche URL di report che contiene un parametro di query di filtro. È possibile aprire un report nell'app Power BI per dispositivi mobili e filtrarlo per uno stato specifico. Ad esempio, questo URL verrà aperto il report Sales e filtrarla by Territory

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

Altre informazioni, Leggi [come creare parametri di query per filtrare i report](https://docs.microsoft.com/power-bi/service-url-filters).

## <a name="next-steps"></a>Passaggi successivi
I vostri commenti e suggerimenti ci aiutano a decidere quali funzioni implementare in futuro, quindi non perdete l'occasione di votare quali funzionalità vorreste avere a disposizione nelle app per dispositivi mobili di Power BI. 

* [App Power BI per dispositivi mobili](mobile-apps-for-mobile-devices.md)
* Seguire @MSPowerBI su Twitter
* Partecipare alla conversazione nella [community di Power BI](http://community.powerbi.com/)
* [Che cos'è Power BI?](../../power-bi-overview.md)

