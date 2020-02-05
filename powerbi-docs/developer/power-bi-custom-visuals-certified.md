---
title: Oggetti visivi di Power BI certificati
description: Requisiti e processo di invio di un oggetto visivo personalizzato per la certificazione ed elenco di oggetti visivi di Power BI certificati.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2019
ms.openlocfilehash: 4ffab3913560498dd57103f0a25c39f7a03a42ec
ms.sourcegitcommit: 75300b3f53f438ed7d3bd4edc93b9eb5925bf3af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2020
ms.locfileid: "77026670"
---
# <a name="get-a-power-bi-visual-certified"></a>Ottenere un oggetto visivo Power BI certificato

Gli oggetti visivi di Power BI certificati sono oggetti visivi di Power BI disponibili in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) che soddisfano i [requisiti di codice](#certification-requirements) del team di Microsoft Power BI. Questi oggetti visivi vengono testati per verificare che non accedano a servizi o risorse esterni e che seguano criteri e linee guida di scrittura del codice protetti.

Dopo la certificazione, un oggetto visivo di Power BI offre più funzionalità. È ad esempio possibile [esportarlo in PowerPoint](../consumer/end-user-powerpoint.md) o visualizzare l'oggetto visivo nei messaggi di posta elettronica ricevuti quando un utente [sottoscrive pagine di report](../consumer/end-user-subscribe.md).

Il processo di certificazione è facoltativo. Gli oggetti visivi di Power BI non certificati, non sono necessariamente oggetti visivi di Power BI non sicuri. Alcuni oggetti visivi di Power BI non vengono certificati perché non sono conformi a uno o più [requisiti di certificazione](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements), ad esempio un oggetto visivo mappa di Power BI che si connette a un servizio esterno o un oggetto visivo di Power BI che usa librerie commerciali.

> [!NOTE]
> Microsoft non è l'autore di oggetti visivi di Power BI di terze parti. Per verificare la funzionalità degli oggetti visivi di terze parti, contattare direttamente l'autore.

## <a name="certification-requirements"></a>Requisiti di certificazione

Per ottenere la [certificazione](#get-a-power-bi-visual-certified), l'oggetto visivo di Power BI deve soddisfare i requisiti elencati in questa sezione. 

### <a name="general-requirements"></a>Requisiti generali

L'oggetto visivo di Power BI deve essere approvato dal Dashboard venditori o dal Centro per i partner. È consigliabile che l'oggetto visivo di Power BI sia già disponibile in [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Per informazioni su come pubblicare un oggetto visivo di Power BI in AppSource, vedere [Pubblicare oggetti visivi di Power BI nel Centro per i partner](office-store.md).

Prima di inviare l'oggetto visivo di Power BI da certificare, verificare che sia conforme alle [linee guida per gli oggetti visivi di Power BI](./guidelines-powerbi-visuals.md).

Quando si invia l'oggetto visivo di Power BI, assicurarsi che il pacchetto compilato corrisponda esattamente al pacchetto inviato.

### <a name="code-repository-requirements"></a>Requisiti del repository di codice

Sebbene il codice non debba essere condiviso pubblicamente in GitHub, è necessario che il repository di codice sia disponibile per essere rivisto dal team di Power BI. A tal proposito è consigliabile mettere a disposizione il codice sorgente JavaScript o TypeScript in GitHub.

Il repository deve contenere solo il codice per un oggetto visivo di Power BI. Non può contenere codice per più oggetti visivi di Power BI o codice non correlato.

Il repository deve contenere un ramo denominato **certificazione** (in minuscolo). Il codice sorgente in questo ramo deve corrispondere al pacchetto inviato. Questo codice può essere aggiornato solo durante il processo di invio successivo, se si invia nuovamente l'oggetto visivo di Power BI.

Se l'oggetto visivo di Power BI usa pacchetti npm privati o moduli secondari GIT, è necessario specificare l'accesso ai repository aggiuntivi che contengono questo codice.

### <a name="file-requirements"></a>Requisiti dei file

Usare la versione più recente dell'API per scrivere l'oggetto visivo di Power BI.

Il repository deve includere i file seguenti:
* **.gitignore**: aggiungere `node_modules` a questo file. Il codice non può includere la cartella *node_modules*.
* **capabilities.json**: se si invia una versione più recente dell'oggetto visivo di Power BI con le modifiche apportate alle proprietà in questo file, assicurarsi di non interrompere i report per gli utenti esistenti.
* **pbiviz.json**
* **package.json**
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Requisiti dei comandi

Verificare che i comandi seguenti non restituiscano errori.

* `npm install`
* `pbiviz package`
* `npm audit`: non deve restituire avvisi con livello elevato o moderato.
* [TSlint Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) senza override di configurazione. Questo comando non deve restituire alcun errore lint.

### <a name="compiling-requirements"></a>Requisiti di compilazione

Usare la versione più recente di [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) per scrivere l'oggetto visivo di Power BI.

È necessario compilare l'oggetto visivo di Power BI con `pbiviz package`. Se si usano script di compilazione personalizzati, specificare un comando di compilazione `npm run package` personalizzato.



### <a name="source-code-requirements"></a>Requisiti del codice sorgente

Verificare di attenersi all'elenco dei criteri per la [certificazione aggiuntiva degli oggetti visivi di Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Se l'invio non rispetta queste linee guida, il Centro per i partner invierà un messaggio di posta elettronica di rifiuto includendo i numeri dei criteri elencati in questo collegamento.

Seguire i requisiti di codice elencati di seguito per assicurarsi che il codice sia in linea con i criteri di certificazione di Power BI.  

**Obbligatorio**
* Usare solo componenti OSS pubblicabili, ad esempio librerie JavaScript o TypeScript pubbliche.
* Il codice deve supportare l'[API per gli eventi di rendering](./visuals/event-service.md).
* Assicurarsi che il modello DOM venga modificato in modo sicuro. Usare la purificazione per i dati o l'input dell'utente, prima di aggiungerli al modello DOM.
* Usare il [report di esempio](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) come set di dati di test.

**Non consentito**
* Accesso a servizi o risorse esterni. Nessuna richiesta HTTP/S o WebSocket, ad esempio, può uscire da Power BI verso alcun servizio.
* Uso di `innerHTML` o `D3.html(user data or user input)`.
* Errori o eccezioni JavaScript nella console del browser per i dati di input.
* Codice arbitrario o dinamico, ad esempio `eval()`, uso non sicuro di `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` e dati o input dell'utente.
* File o progetti JavaScript minimizzati.

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

## <a name="certified-power-bi-visuals"></a>Oggetti visivi di Power BI certificati

Gli oggetti visivi di Power BI certificati sono elencati di seguito. Fare clic sul collegamento per aprire l'oggetto visivo di Power BI in AppSource. Se è disponibile un video, è possibile fare clic sul collegamento al video per guardarlo.

* [3AG Systems - Bar Chart With Absolute Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [Sistemi 3AG: grafico a barre con varianza relativa](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [Sistemi 3AG: istogramma con varianza relativa](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems - Column Chart with Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Advanced Donut Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Advanced Donut Visual (Light Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Advanced Graph Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) (Visualizzazione di rete avanzata)
*  [Advanced TimeSeries Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Box and Whisker chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755),  **[collegamento al video](https://youtu.be/AOlsFYkfkcw)**
* [Grafico bullet](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[collegamento al video](https://youtu.be/mtvUNl9bMjA)**
* [Calendar by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Calendar di Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[collegamento al video](https://youtu.be/nT_18gyRxPo)**
*  [Scheda con stati di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[collegamento al video](https://youtu.be/AQvd2FhRyCI)**
*  [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Custom Calendar by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Cylindrical Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[collegamento al video](https://youtu.be/By16pX9KT40)**
*  [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Drill-down column chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[collegamento al video](https://youtu.be/lBy2gQQ5YsQ)**
*  [Drill-down column chart for time based data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[collegamento al video](https://youtu.be/T_mRou18vx0)**
*  [Drill-down donut chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[collegamento al video](https://youtu.be/AUVFrSHmPeo)**
*  [Indicatore KPI doppio](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Descrizione comando dinamica di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[collegamento al video](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filter by List by Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[collegamento al video](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[collegamento al video](https://youtu.be/YsTa7uyJ4sg)**
*  [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[collegamento al video](https://youtu.be/qJ7s_KrGiUU)**
* [Gantt Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Griglia di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[collegamento al video](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histogram with points by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Horizontal bar chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [KPI Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [Colonna KPI di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [Griglia indicatore KPI di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [Indicatore KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [Ticker KPI di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[collegamento al video](https://youtu.be/90FLCKpgicA)**
*  [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Overview di CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Asse di riproduzione (filtro dei dati dinamico)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [collegamento al video](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[collegamento al video](https://youtu.be/1enze8pcGzY)**
*  [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[collegamento al video](https://youtu.be/DQWdcQtjDVw)**
*  [Diagramma di Gantt di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[collegamento al video](https://youtu.be/WWP9wVUHGaA)**
*  [Grafico a dispersione di Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Griglia di navigazione](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[collegamento al video](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[collegamento al video](https://youtu.be/0m3Vnvso9tY)**
*  [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Grafico radiale](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Synoptic Panel by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Mappa termina con tabella](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[collegamento al video](https://youtu.be/C3OXdETbS9o)**
*  [Filtro del testo](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[collegamento al video](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [collegamento al video](https://youtu.be/szNi9YgXFJc)
*  [Tornado chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[collegamento al video](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI Card](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[collegamento al video](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[collegamento al video](https://youtu.be/0BZsVCQdEkc)**
*  [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Diagramma di Venn di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Violin Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[collegamento al video](https://youtu.be/1vRqYUsm3Vk)**
*  [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[collegamento al video](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Domande frequenti

Per altre informazioni sugli oggetti visivi, vedere le [domande frequenti sugli oggetti visivi certificati](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Passaggi successivi

* [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (Sviluppo di un oggetto visivo personalizzato di Power BI)
* [Playlist degli oggetti visivi personalizzati di Microsoft su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualizzazioni in Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualizzazioni personalizzate in Power BI](power-bi-custom-visuals.md)  
* [Pubblicare oggetti visivi di Power BI in Microsoft AppSource](../developer/office-store.md) 
* Gli sviluppatori Web interessati a creare oggetti visivi Power BI personalizzati e ad aggiungerli a  [Microsoft AppSource](https://appsource.microsoft.com) possono iniziare con l'esercitazione  [Sviluppo di un oggetto visivo di Power BI](visuals/custom-visual-develop-tutorial.md). 

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
