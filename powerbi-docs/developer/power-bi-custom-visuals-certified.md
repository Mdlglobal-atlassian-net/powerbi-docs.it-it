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
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999745"
---
# <a name="get-a-power-bi-visual-certified"></a>Ottenere un oggetto visivo Power BI certificato

Gli oggetti visivi di Power BI certificati sono oggetti visivi nel *Marketplace* che soddisfano determinati requisiti di *codice specifico* e sono stati testati e approvati dal *team di Microsoft Power BI*. I test sono studiati per verificare che l'oggetto visivo non abbia accesso a risorse o servizi esterni.

Gli oggetti visivi di Power BI certificati e gli [oggetti visivi di Power BI standard](power-bi-custom-visuals.md) vengono usati nello stesso modo. Possono essere aggiunti a [Power BI Desktop](../desktop-what-is-desktop.md) e al [servizio Power BI](../power-bi-service-overview.md), e visualizzati con [Power BI per dispositivi mobili](../consumer/mobile/mobile-apps-for-mobile-devices.md) e [Power BI Embedded](embedding.md).

Il processo di certificazione è un processo facoltativo. Spetta agli sviluppatori decidere se far certificare i propri oggetti visivi di Power BI nel Marketplace. Dopo la certificazione, un oggetto visivo di Power BI offre più funzionalità. È ad esempio possibile [esportarlo in PowerPoint](../consumer/end-user-powerpoint.md) o visualizzare l'oggetto visivo nei messaggi di posta elettronica ricevuti quando un utente [sottoscrive pagine di report](../consumer/end-user-subscribe.md).

Gli oggetti visivi di Power BI non certificati non sono necessariamente oggetti visivi non sicuri. Alcuni oggetti visivi non vengono certificati perché non sono conformi a uno o più [requisiti di certificazione](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements), accedono ad esempio a un servizio esterno, come oggetti visivi mappa oppure oggetti visivi che usano librerie commerciali.

Gli sviluppatori Web interessati a creare oggetti visivi Power BI personalizzati e ad aggiungerli a  [Microsoft AppSource](https://appsource.microsoft.com) possono iniziare con l'esercitazione  [Sviluppo di un oggetto visivo di Power BI](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> **Microsoft** *non* è l'autore di oggetti visivi di Power BI di terze parti. Per verificare la funzionalità degli oggetti visivi di terze parti, è consigliabile contattare l'autore direttamente.

> [!IMPORTANT]
> Microsoft, a propria discrezione, può rimuovere un oggetto visivo di Power BI dall'[elenco degli oggetti visivi certificati](#list-of-power-bi-visuals-that-have-been-certified).

## <a name="certification-requirements"></a>Requisiti di certificazione

Per ottenere la [certificazione](#get-a-power-bi-visual-certified) per il proprio oggetto visivo di Power BI, assicurarsi che soddisfi i requisiti elencati in questa sezione. 

> [!TIP]
> È consigliabile usare EsLint con il set di regole di sicurezza predefinito per eseguire una convalida anticipata del codice prima dell'invio.

* L'oggetto visivo di Power BI deve essere approvato dal Dashboard venditori Microsoft o dal Centro per i partner. L'oggetto visivo di Power BI deve essere disponibile in Microsoft [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* L'oggetto visivo di Power BI deve essere scritto con l'*API v2.5* o versione successiva.
* Il repository del codice deve essere disponibile per l'esame da parte del team di Power BI. Ad esempio, il codice sorgente deve essere disponibile per il team in un formato leggibile (JavaScript o TypeScript) tramite GitHub.

    >[!NOTE]
    > Il codice non deve essere condiviso pubblicamente in Github.

* Requisiti del repository di codice:
  * Deve includere questi file:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Non deve includere la cartella *node_modules* (aggiungere *node_modules* al file con estensione .gitingore*).
  * Il comando *npm install* non deve restituire alcun errore.
  * Il comando *npm audit* non deve restituire avvisi di livello elevato o moderato.
  * Il comando *pbiviz package* non deve restituire alcun errore.
  * Deve includere [TSlint da Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) senza alcun override di configurazione. Questo comando non deve restituire alcun errore lint.
   * Il pacchetto compilato dell'oggetto visivo di Power BI deve corrispondere al pacchetto inviato, ovvero l'hash MD5 di entrambi i file deve essere uguale.
* Requisiti del codice sorgente:
   * L'oggetto visivo di Power BI deve supportare l'[API per gli eventi di rendering](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Assicurarsi che non venga eseguito alcun codice arbitrario/dinamico (bad: eval(), unsafe to use of settimeout(), requestAnimationFrame(), setinterval(some function with user input), running user input/data).
   * Assicurarsi che il codice DOM venga modificato in modo sicuro (bad: innerHTML, D3.html(<some user/data input>), usare la bonifica per input/dati utente prima di aggiungerla al codice DOM.
   * Assicurarsi che non siano presenti errori o eccezioni JavaScript nella console del browser per i dati di input. È possibile che gli utenti usino l'oggetto visivo di Power BI con un intervallo diverso di dati imprevisti, pertanto l'oggetto visivo non deve generare errori. È possibile usare questo [report di esempio](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) come set di dati di test.

* Se vengono modificate le proprietà all'interno del file *capabilities.json*, assicurarsi che le modifiche non causino interruzioni nei report dell'utente.

* Assicurarsi che l'oggetto visivo di Power BI sia conforme alle [linee guida per gli oggetti visivi di Power BI](./guidelines-powerbi-visuals.md).
    
* Il codice può usare solo componenti OSS pubblicabili, ad esempio librerie JavaScript o TypeScript pubbliche. Il codice sorgente deve essere disponibile per la revisione e non presentare vulnerabilità note. Non è possibile verificare oggetti visivi personalizzati che usano un componente commerciale.

* L'oggetto visivo di Power BI non deve accedere a servizi o risorse esterni. Nessuna richiesta HTTP/S o WebSocket, ad esempio, può uscire da Power BI verso alcun servizio. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Invio di un oggetto visivo di Power BI per la certificazione

È possibile richiedere la certificazione dell'oggetto visivo di Power BI da parte del team di Power BI tramite il Centro per i partner.

>[!TIP]
>Il processo di certificazione di Power BI può richiedere tempo. Se si sta creando un nuovo oggetto visivo di Power BI, è consigliabile pubblicarlo attraverso il Centro per i partner prima di richiedere la certificazione di Power BI. In questo modo si garantisce che la pubblicazione dell'oggetto visivo non subisca ritardi.

Per richiedere la certificazione di Power BI:

1. Accedere al Centro per i partner.
2. Nella **pagina Panoramica** scegliere l'oggetto visivo di Power BI e passare alla pagina **Configurazione prodotto**.
3. Selezionare la casella di controllo **Richiedere la certificazione di Power BI**.
4. Nella casella di testo **Note per la certificazione** della pagina **Rivedi e pubblica** indicare un collegamento al codice sorgente e le credenziali necessarie per accedervi.

>[!NOTE]
> Se è in corso il processo di invio di un oggetto visivo di Power BI ed è necessario usare il [Dashboard venditori](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (lo strumento di gestione precedente), rivedere le istruzioni del [processo di invio per la certificazione tramite il Dashboard venditori](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Elenco degli oggetti visivi di Power BI certificati

| Collegamento | Video |
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
