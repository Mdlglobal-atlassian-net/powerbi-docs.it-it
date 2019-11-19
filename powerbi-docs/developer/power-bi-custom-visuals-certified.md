---
title: Oggetti visivi di Power BI certificati
description: Requisiti e processo per l'invio di un oggetto visivo personalizzato per la certificazione. Elenco degli oggetti visivi di Power BI già certificati.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 05/9/2019
ms.openlocfilehash: c6ecb2eb2346940a22bbd6b7bff5ca0138faa290
ms.sourcegitcommit: 08b73af260ded51daaa6749338cb85db2eab587f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74102595"
---
# <a name="get-a-power-bi-visual-certified"></a>Ottenere un oggetto visivo Power BI certificato

## <a name="what-are-_certified_-power-bi-visuals"></a>Che cosa sono gli oggetti visivi di Power BI **_certificati_** ?

Gli oggetti visivi di Power BI certificati sono oggetti visivi nel **Marketplace** che soddisfano determinati requisiti di **codice specifico** e sono stati testati e approvati dal **team di Microsoft Power BI**. Quando un oggetto visivo viene certificato, offre più funzionalità. È ad esempio possibile [esportare in PowerPoint](../consumer/end-user-powerpoint.md) e visualizzare l'oggetto visivo nei messaggi di posta elettronica ricevuti quando un utente [sottoscrive le pagine del report](../consumer/end-user-subscribe.md).

Gli **oggetti visivi di Power BI certificati** vengono usati come [oggetti visivi di Power BI standard](power-bi-custom-visuals.md). Gli oggetti visivi di Power BI certificati possono essere aggiunti al **servizio Power BI**, a un **report di Power BI Desktop** e possono essere visualizzati con **Power BI per dispositivi mobili** e **Power BI Embedded**.

I test eseguiti sono studiati per verificare che l'oggetto visivo non abbia accesso a risorse o servizi esterni. **Microsoft** non è l'*autore* di oggetti visivi di Power BI di terze parti. È quindi consigliabile contattare l'autore direttamente per verificare la funzionalità degli oggetti.

Il processo di certificazione è facoltativo. Spetta agli sviluppatori decidere se l'oggetto visivo nel Marketplace deve essere certificato.  

Gli **oggetti visivi di Power BI non certificati** non sono necessariamente oggetti visivi non sicuri. Alcuni oggetti visivi non vengono certificati perché non sono conformi a uno o più [requisiti di certificazione](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements), accedono ad esempio a un servizio esterno, come oggetti visivi mappa oppure oggetti visivi che usano librerie commerciali.

Gli sviluppatori Web interessati a creare visualizzazioni personalizzate e ad aggiungerle in  **[Microsoft AppSource](https://appsource.microsoft.com)** , possono vedere  **[Sviluppare un oggetto visivo personalizzato di Power BI](visuals/custom-visual-develop-tutorial.md)** per altre informazioni.

## <a name="removal-of-power-bi-certified-power-bi-visuals"></a>Rimozione di oggetti visivi di Power BI certificati

Microsoft, a propria discrezione, può rimuovere un oggetto visivo dall'[elenco degli oggetti visivi certificati](#list-of-power-bi-visuals-that-have-been-certified).

## <a name="getting-a-custom-visualcertified"></a>Certificazione di un oggetto visivo personalizzato

### <a name="certification-requirements"></a>Requisiti di certificazione

Per ottenere la [certificazione](#get-a-power-bi-visual-certified) dell'oggetto visivo personalizzato, assicurarsi che l'oggetto visivo personalizzato sia conforme ai requisiti seguenti:  

* Approvato per Microsoft AppSource. L'oggetto visivo personalizzato deve essere disponibile in Microsoft [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* L'oggetto visivo personalizzato è scritto con l'**API v2.5** o versione successiva.
* Il repository di codice è disponibile per la revisione da parte del team di Power BI, ad esempio, il codice sorgente JavaScript o TypeScript in formato leggibile è disponibile tramite GitHub.

    >[!Note]
    > Il codice non deve essere condiviso pubblicamente in Github.
* Requisiti del repository di codice:
   * Deve includere il set minimo di file obbligatori:
      * .gitignore
      * capabilities.json
      * pbiviz.json
      * package.json
      * package-lock.json
      * tsconfig.json
   * Non deve includere la cartella node_modules (aggiungere node_modules al file con estensione gitingore)
   * Il comando **npm install** non deve restituire alcun errore.
   * Il comando **npm audit** non deve restituire avvisi con livello elevato o moderato.
   * Il comando **pbiviz package** non deve restituire alcun errore.
   * Deve includere [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) senza configurazione sottoposta a override e questo comando non deve restituire alcun errore di lint.
   * Il pacchetto compilato dell'oggetto visivo personalizzato deve corrispondere al pacchetto inviato, ovvero l'hash MD5 di entrambi i file deve essere uguale.
* Requisiti del codice sorgente:
   * L'oggetto visivo deve supportare l'[API per gli eventi di rendering](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Assicurarsi che non venga eseguito alcun codice arbitrario/dinamico (bad: eval(), unsafe to use of settimeout(), requestAnimationFrame(), setinterval(some function with user input), running user input/data).
   * Assicurarsi che il codice DOM venga modificato in modo sicuro (bad: innerHTML, D3.html(<some user/data input>), usare la bonifica per input/dati utente prima di aggiungerla al codice DOM.
   * Assicurarsi che non siano presenti errori/eccezioni JavaScript nella console del browser per i dati di input. È possibile che gli utenti usino l'oggetto visivo con un intervallo diverso di dati imprevisti, quindi l'oggetto visivo non deve dare errore. È possibile usare [questo report di esempio](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) come set di dati di test.

* Se vengono modificate le proprietà in capabilities.json, assicurarsi che non interrompano i report dell'utente.

* Assicurarsi che l'oggetto visivo sia conforme alle [linee guida per gli oggetti visivi di Power BI](./guidelines-powerbi-visuals.md#guidelines-for-power-bi-visuals-with-additional-purchases). **Non sono consentite filigrane**.

* Usa solo componenti OSS revisionabili pubblici (librerie JS o TypeScript pubbliche. Il codice sorgente è disponibile per la revisione e non presenta vulnerabilità note). Non è possibile verificare oggetti visivi personalizzati che usano un componente commerciale.

* Non ha accesso a risorse o servizi esterni. Non devono tra l'altro verificarsi richieste HTTP/S o WebSocket dirette a un qualsiasi altro servizio partendo da Power BI. 

> [!TIP]
> È consigliabile usare EsLint applicando il set di regola di sicurezza predefinito per eseguire una convalida anticipata del codice prima dell'invio.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processo di invio di un oggetto visivo personalizzato per richiederne la certificazione

Per inviare un oggetto visivo personalizzato per la certificazione:

1. Inviare un messaggio di posta elettronica al team del supporto tecnico degli oggetti visivi di Power BI (pbicvsupport@microsoft.com). Nel messaggio di posta elettronica, includere le seguenti informazioni:
    * Titolo: Richiesta di certificazione oggetto visivo
    * Collegamento al repository GitHub in cui è ospitato il codice sorgente leggibile dell'oggetto visivo
    * [Adesione ai requisiti](#certification-requirements)
    * Revisione del codice superata

2. Il team degli oggetti visivi di Power BI Microsoft invia una notifica quando l'oggetto visivo personalizzato viene certificato e aggiunto all'[elenco degli oggetti visivi certificati](#list-of-power-bi-visuals-that-have-been-certified) o rifiutato con un report dei problemi che devono essere corretti. È responsabilità dello sviluppatore mantenere una linea di comunicazione aperta con Microsoft e aggiornare gli oggetti visivi certificati in base alle esigenze.

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Elenco degli oggetti visivi di Power BI certificati

| Collegamento ad AppSource | Collegamento al video |
| --- | --- |
| [Sistemi 3AG: grafico a barre con varianza relativa](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [Sistemi 3AG: istogramma con varianza relativa](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [Advanced Donut Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) (Oggetto visivo ad anello avanzato) | |
| [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) (Visualizzazione di rete avanzata) | |
| [Advanced TimeSeries Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) (Oggetto visivo TimeSeries avanzato) | |
| [Advanced Combo Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) (Oggetto visivo casella combinata avanzato) | |
| [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [Video](https://youtu.be/So5xKMSpVJI) |
| [Box and Whisker chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [Video](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [Video](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [Grafico bullet](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [Video](https://youtu.be/AOlsFYkfkcw) |
| [Grafico a barre di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [Video](https://youtu.be/mtvUNl9bMjA) |
| [Calendar di Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [Candlestick di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [Video](https://youtu.be/nT_18gyRxPo) |
| [Scheda con stati di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [Video](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [Video](https://youtu.be/9NHXALkBXuY) |
| [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [Video](https://youtu.be/DgdoWi7Gcxo) |
| [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Tracciato a punti di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [Video](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [Drill-down column chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [Video](https://youtu.be/lBy2gQQ5YsQ) |
| [Drill-down column chart for time based data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [Video](https://youtu.be/T_mRou18vx0) |
| [Drill-down donut chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [Video](https://youtu.be/AUVFrSHmPeo) |
| [Indicatore KPI doppio](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Descrizione comando dinamica di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [Video](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [Video](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Filter by List by Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [Video](https://youtu.be/RetEWGwBu0I) |
| [Grafico Force-Directed](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [Video](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [Video](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [Video](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [Video](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [Griglia di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [Video](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [Video](https://youtu.be/0ZGzJaq_KT4) |
| [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [Histogram with points by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [Video](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [Video](https://youtu.be/SudZei68PPo) |
| [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [KPI Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [Colonna KPI di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [Video](https://youtu.be/rU0xoOlIq1U) |
| [Griglia indicatore KPI di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [Video](https://youtu.be/dM4PvZh71V0) |
| [Indicatore KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [Ticker KPI di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [Video](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [Video](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [Video](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [Overview di CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Asse di riproduzione (filtro dei dati dinamico)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [Video](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [Video](https://youtu.be/1enze8pcGzY) |
| [Grafico degli impulsi](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [Video](https://youtu.be/DQWdcQtjDVw) |
| [Diagramma di Gantt di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [Video](https://youtu.be/ppBnyhqWNC0) |
| [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [Video](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [Video](https://youtu.be/d5xBCMmb3hU) |
| [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [Video](https://youtu.be/WWP9wVUHGaA) |
| [Grafico a dispersione di Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [Griglia di navigazione](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Filtro avanzato di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [Video](https://youtu.be/gcJsDDRQq28) |
| [Grafico sparkline di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [Video](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Grafico radiale](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [Synoptic Panel by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [Mappa termina con tabella](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [Tachimetro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [Video](https://youtu.be/C3OXdETbS9o) |
| [Filtro del testo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [Video](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [Video](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline di CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [Video](https://youtu.be/szNi9YgXFJc) |
| [Grafico Tornado](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [Video](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [Video](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [Video](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [Video](https://youtu.be/0BZsVCQdEkc) |
| [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [Video](https://youtu.be/1vRqYUsm3Vk) |
| [Cloud di parole](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [Video](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>DOMANDE FREQUENTI

Per altre informazioni sugli oggetti visivi, vedere le [domande frequenti sugli oggetti visivi certificati](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Passaggi successivi

* [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI)
* [Playlist degli oggetti visivi personalizzati di Microsoft su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizzazioni in Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizzazioni personalizzate in Power BI](power-bi-custom-visuals.md)  
* [Pubblicare oggetti visivi di Power BI in Microsoft AppSource](../developer/office-store.md)  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)