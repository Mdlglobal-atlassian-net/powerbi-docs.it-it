---
title: Visualizzazioni personalizzate certificate di Power BI
description: "Requisiti e processo per l'invio di un oggetto visivo personalizzato per la certificazione. Elenco di oggetti visivi personalizzati già certificati."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/12/2018
ms.author: mihart
ms.openlocfilehash: 955435ee526c6acae8f478539641529515e2e0a8
ms.sourcegitcommit: 259d7689bcb1683d4d63a245a9b02becea072139
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="getting-a-custom-visual-certified"></a>*Certificare* un oggetto visivo personalizzato
## <a name="what-is-meant-by-certified"></a>Cosa si intende per *certificato*?
Un *oggetto visivo personalizzato certificato* è un oggetto che ha soddisfatto una serie di requisiti di codifica e ha superato rigorosi test di sicurezza.  Dopo che gli oggetti visivi personalizzati hanno ricevuto la certificazione, possono essere [esportati in PowerPoint](service-publish-to-powerpoint.md) e possono essere visualizzati nei messaggi di posta elettronica ricevuti quando un utente [effettua la sottoscrizione alle pagine del report](service-report-subscribe.md). Possono anche essere usati come [oggetti visivi personalizzati standard](power-bi-custom-visuals.md), aggiunti al servizio Power BI service e ai report di Power BI Desktop o visualizzati in Power BI Embedded e per dispositivi mobili.

Gli sviluppatori Web interessati a creare visualizzazioni personalizzate e ad aggiungerle in [Microsoft AppSource](https://appsource.microsoft.com), possono vedere [Usare gli strumenti di sviluppo per la creazione di oggetti visivi personalizzati](service-custom-visuals-getting-started-with-developer-tools.md).


## <a name="certification-requirements"></a>Requisiti di certificazione
* Approvato per Microsoft AppSource    
* L'oggetto visivo personalizzato è scritto con l'API 1.2 con versione o successiva    
* Repository di codice disponibile per la revisione (ad esempio, Visual Code disponibile attraverso GitHub)    
* Usa solo componenti OSS rivedibili pubblici    
* Non accede a servizi o risorse esterni    

> **SUGGERIMENTO**: è consigliabile usare EsLint con il set di regole di sicurezza predefinito, per convalidare il codice prima dell'invio.
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processo per l'invio di un oggetto visivo personalizzato per la certificazione
Per inviare un oggetto visivo personalizzato per la certificazione:

1. Inviare un messaggio di posta elettronica al supporto tecnico degli oggetti visivi personalizzati di Power BI (pbicvsupport@microsoft.com). Nel messaggio di posta elettronica, includere le seguenti informazioni:    
   
   * Titolo: Richiesta di certificazione oggetto visivo    
   * Collegamento al repository GitHub in cui è ospitato il codice sorgente dell'oggetto visivo    
   * Adesione ai requisiti (vedere sopra)    
   * Superamento della revisione di sicurezza e codice    
2. Il team Oggetti visivi personalizzati in Microsoft informerà quando l'oggetto visivo personalizzato è certificato e aggiunto all'elenco Certificati (in basso) o rifiutato con un report dei problemi che devono essere corretti. È responsabilità dello sviluppatore mantenere una linea di comunicazione aperta con Microsoft e aggiornare gli oggetti visivi Certificati in base alle esigenze.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Rimozione di oggetti visivi personalizzati di Power BI certificati
Microsoft, a propria discrezione, può rimuovere un oggetto visivo dall'elenco Certificati.  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>Elenco di oggetti visivi personalizzati che sono stati certificati
| Collegamento ad AppSource | Collegamento al video |
| --- | --- |
| [Regole di associazione](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380815) | |
| [Aster plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [BciCalendar (Beyondsoft Calendar)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Grafico a farfalla di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) |[Video](https://youtu.be/So5xKMSpVJI) |
| [Scatola e baffi](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Grafico a quadri di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | |
| [Grafico a bolle di Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340?src=office) | |
| [Grafico bullet](https://store.office.com/app.aspx?assetid=WA104380755) |[Video1](https://youtu.be/AOlsFYkfkcw)[Video2   ](https://youtu.be/AQvd2FhRyCI) |
| [Grafico a barre di OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Video](https://youtu.be/mtvUNl9bMjA) |
| [Calendar di Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) | |
| [Candlestick di OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | |
| [Filtro dei dati chiclet](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Video](https://youtu.be/iYOkJ1APueY) |
| [Grafico a griglia armonica](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) |[Video](https://youtu.be/AQvd2FhRyCI) |
| [Misuratore circolare di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Misuratore cilindrico](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Comparatore](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) |[Video](https://youtu.be/AOlsFYkfkcw) |
| [Grafico ad anello di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Video](https://youtu.be/pDToHDFHnq8) |
| [Tracciato a punti di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381101) | |
| [Tracciato a punti di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) |[Video](https://youtu.be/4lskRgcpFJY) |
| [Tracciato a punti di Microsoft](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760?src=office) | |
| [Grafico ad anello drill-down di ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | |
| [Drilldown Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045?src=office) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044?src=office) | |
| [Grafico a colonne drill-down di ZoomCharts](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881?src=office) | |
| [Grafico a colonne drill-down per dati temporali di ZoomCharts](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | |
| [Grafico ad anello drill-down di ZoomCharts](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | |
| [Indicatore KPI doppio](https://store.office.com/dual-kpi-WA104380774.aspx) |[Video](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Grafico a dispersione migliorato](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) | |
| [Enlighten Bubble Stack](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380868) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Enlighten World Flags](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380923) | |
| [Flywheel]() | |
| [Forecasting TBATS](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381326?src=office) | |
| [Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Video](https://youtu.be/qJ7s_KrGiUU) |
| [Grafico gerarchico di Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333?src=office) | |
| [Istogramma](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Grafico a imbuto orizzontale](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[Video](https://youtu.be/SudZei68PPo) |
| [Image Timeline](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381254) | |
| [Infographic Designer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898?src=office) | |
| [Indicatore KPI](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Ticker KPI di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | |
| [Grafico LineDot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766?src=office) | |
| [Misuratore lineare di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Video](https://youtu.be/AOlsFYkfkcw) |
| [Grafico Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview)  | [Video](https://youtu.be/90FLCKpgicA)|
| [Asse di riproduzione (filtro dei dati dinamico)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Video](https://youtu.be/IvfIP3E6-1Q) |
| [Grafico degli impulsi](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | |
| [Grafico radar](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Grafico ad anello di MAQSoftware](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) | [Video](https://youtu.be/pDToHDFHnq8)|
| [Grafico rotante di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007?src=office) |  |
| [Diagramma di Sankey](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Video](https://youtu.be/WWP9wVUHGaA) |
| [Griglia di navigazione](https://store.office.com/scroller-WA104381018.aspx) |[Video](https://youtu.be/uhRFQF2cGSY) |
| [Filtro avanzato di SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Video](https://youtu.be/gcJsDDRQq28) |
| [Grafico sparkline di OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Video](https://youtu.be/0m3Vnvso9tY) |
| [Grafico radiale](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Mappa termina con tabella](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Tachimetro](https://store.office.com/tachometer-WA104380937.aspx?) |[Video](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Wrapper di testo](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Termometro](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) | [Video](https://youtu.be/SPX9mgrAdBc)|
| [Decomposizione sequenza temporale](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Filtro dei dati sequenza temporale](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Video](https://youtu.be/ozMtZ4_NZ10) |
| [Grafico Tornado](https://store.office.com/tornado-chart-WA104380768.aspx) |[Video](https://youtu.be/AQvd2FhRyCI) |
| [Grafico Ultimate Variance di Klaus Birringer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140?src=office) | |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | |
| [Diagramma di Venn di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381231) | |
| [VitaraCharts - MicroChart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381165) | |
| [Waffle chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Video](https://youtu.be/1vRqYUsm3Vk) |
| [Cloud di parole](https://store.office.com/word-cloud-WA104380752.aspx?) |[Video](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Passaggi successivi
[Introduzione agli strumenti di sviluppo per oggetti visivi personalizzati (Anteprima)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Playlist degli oggetti visivi personalizzati di Microsoft su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizzazioni in Power BI](power-bi-report-visualizations.md)  
[Visualizzazioni personalizzate in Power BI](power-bi-custom-visuals.md)  
[Pubblicare oggetti visivi personalizzati in Microsoft AppSource](developer/office-store.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

