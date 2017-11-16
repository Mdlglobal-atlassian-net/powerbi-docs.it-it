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
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: 27af387a6d789b00837e6bbf8c6be9aa219c7198
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="getting-a-custom-visual-certified"></a>*Certificare* un oggetto visivo personalizzato
## <a name="what-is-meant-by-certified"></a>Cosa si intende per *certificato*?
Un *oggetto visivo personalizzato certificato* è un oggetto che ha soddisfatto una serie di requisiti di codifica e ha superato rigorosi test di sicurezza.  Dopo che gli oggetti visivi personalizzati hanno ricevuto la certificazione, possono essere [esportati in PowerPoint](service-publish-to-powerpoint.md) e possono essere visualizzati nei messaggi di posta elettronica ricevuti quando un utente [effettua la sottoscrizione alle pagine del report](service-report-subscribe.md).

* Se si è sviluppatori Web interessati a creare visualizzazioni personalizzate e ad aggiungerle allo Store, Per informazioni sulla procedura, vedere [Creare un oggetto visivo con Strumenti di sviluppo](service-custom-visuals-getting-started-with-developer-tools.md) e visitare [Office Store](service-custom-visuals-office-store.md).
* Se si usa regolarmente un oggetto visivo di Office Store, chiedere allo sviluppatore dell'oggetto di certificarlo con Microsoft.  Le informazioni di contatto dello sviluppatore sono disponibili nella pagina **Scopri di più** dell'oggetto visivo e sono elencate come **Provider**.

## <a name="certification-requirements"></a>Requisiti di certificazione
* Approvato da Office Store    
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
| Collegamento a Office Store | Collegamento al video |
| --- | --- |
| [Regole di associazione](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380815) | |
| [Aster plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [BciCalendar] presto disponibile | |
| [Scatola e baffi](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Grafico bullet](https://store.office.com/en-us/app.aspx?assetid=WA104380755) |[Video1](https://youtu.be/AOlsFYkfkcw)[Video2   ](https://youtu.be/AQvd2FhRyCI) |
| [Grafico a barre di OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Video](https://youtu.be/mtvUNl9bMjA) |
| [Scheda con stati di OKViz](https://store.office.com/card-with-states-by-okviz-WA104380967.aspx) |[Video 1  ](https://youtu.be/myiX0BmZd8U) [Video 2](https://youtu.be/AOlsFYkfkcw) |
| [Filtro dei dati chiclet](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Video](https://youtu.be/iYOkJ1APueY) |
| [Misuratore circolare di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Misuratore cilindrico](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | |
| [Comparatore](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) |[Video](https://youtu.be/AOlsFYkfkcw) |
| [Grafico ad anello di MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Video](https://youtu.be/pDToHDFHnq8) |
| [Grafico ad anello con drill-down](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | |
| [Indicatore KPI doppio](https://store.office.com/dual-kpi-WA104380774.aspx) |[Video](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| Volano - presto disponibile | |
| [Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Video](https://youtu.be/qJ7s_KrGiUU) |
| [Istogramma](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Grafico a imbuto orizzontale](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) |[Video](https://youtu.be/SudZei68PPo) |
| [Sequenza temporale delle immagini](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381254) | |
| [Indicatore KPI](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| Grafico in formato di misuratore di riempimento - presto disponibile |[Video](https://youtu.be/wQ51TTqIZc4) |
| [Misuratore lineare di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Video](https://youtu.be/AOlsFYkfkcw) |
| Visualizzatore testo lungo - presto disponibile | |
| [Asse di riproduzione (filtro dei dati dinamico)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Video](https://youtu.be/IvfIP3E6-1Q) |
| [Grafico degli impulsi](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006?src=office&tab=Overview) |[Video](https://www.youtube.com/watch?v=DQWdcQtjDVw) |
| [Grafico radar](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Diagramma di Sankey](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Video](https://youtu.be/WWP9wVUHGaA) |
| [Grafico ad anello di MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) |[Video](https://youtu.be/pDToHDFHnq8) |
| [Griglia di navigazione](https://store.office.com/scroller-WA104381018.aspx) |[Video](https://youtu.be/uhRFQF2cGSY) |
| [Filtro avanzato di OKViz](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Video](https://youtu.be/gcJsDDRQq28) |
| [Grafico sparkline di OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Video](https://youtu.be/0m3Vnvso9tY) |
| [Grafico radiale](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Tachimetro](https://store.office.com/tachometer-WA104380937.aspx?) |[Video](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Decomposizione sequenza temporale](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380897) | |
| [Mappa termina con tabella](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Wrapper di testo](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Filtro dei dati sequenza temporale](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Video](https://youtu.be/ozMtZ4_NZ10) |
| [Grafico Tornado](https://store.office.com/tornado-chart-WA104380768.aspx) |[Video](https://youtu.be/AQvd2FhRyCI) |
| [Oggetto visivo Visio (anteprima)](https://store.office.com/visio-visual-preview-WA104381132.aspx) |[Video](https://www.youtube.com/watch?v=dCcd7rftjZA&list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x&index=2) |
| [Waffle chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Video](https://youtu.be/1vRqYUsm3Vk) |
| [Cloud di parole](https://store.office.com/word-cloud-WA104380752.aspx?) |[Video](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Passaggi successivi
[Scaricare e usare oggetti visivi personalizzati da Office Store](service-custom-visuals-office-store.md)  
[Introduzione agli strumenti di sviluppo per oggetti visivi personalizzati (Anteprima)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Playlist degli oggetti visivi personalizzati di Microsoft su YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualizzazioni in Power BI](power-bi-report-visualizations.md)  
[Visualizzazioni personalizzate in Power BI](power-bi-custom-visuals.md)  
[Usare le visualizzazioni personalizzate in Power BI Desktop](power-bi-custom-visuals-use.md)  
[Pubblicare oggetti visivi personalizzati in Office Store](developer/office-store.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

