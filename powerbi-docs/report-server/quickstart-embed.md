---
title: Incorporare un report usando un iFrame
description: "L'installazione del server di report di Power BI è molto rapida. Dal download, all'installazione e alla configurazione, si sarà operativi in pochi minuti."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/09/2017
ms.author: maghan
ms.openlocfilehash: 56835bfb25c8c930099fadf710137f69fa89fc2e
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="quickstart-embed-a-power-bi-report-using-an-iframe-and-url-parameters"></a>Guida introduttiva: incorporare un report di Power BI usando un iFrame e parametri dell'URL

È possibile incorporare qualsiasi report usando un iFrame nell'applicazione. 

## <a name="url-parameter"></a>Parametro dell'URL

Per tutti gli URL di un report, è possibile aggiungere un parametro della stringa di query di `?rs:Embed=true`.

ad esempio:

```
http://myserver/reports/powerbi/Sales?rs:embed=true
```

Questo funziona in tutti i tipi di report in un server di report di Power BI.

## <a name="iframe"></a>iFrame

Dopo aver creato l'URL, è possibile creare un iFrame all'interno di una pagina Web che ospiti il report.

ad esempio:

```
<iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
```

## <a name="url-filter"></a>Filtro URL

È possibile aggiungere un parametro di stringa di query all'URL per filtrare i dati restituiti nel report di Power BI.

La sintassi è semplice: iniziare con l'URL del report, aggiungere un punto interrogativo e quindi la sintassi del filtro.

URL?filter=***Tabella***/***Campo*** eq '***valore***'

Tenere presente quanto segue:

- i nomi **Tabella** e **Campo** rispettano la distinzione tra maiuscole e minuscole, **valore** non la rispetta.
- È possibile filtrare un report con campi che sono nascosti dalla visualizzazione Report.
- **Valore** deve essere racchiuso tra virgolette singole.
- Il tipo di campo deve essere una stringa.
- I nomi di tabella e campo non possono contenere spazi.

###  <a name="example-filter-on-a-field"></a>Esempio: filtrare in base a un campo

Si prenda in considerazione l’[Esempio di analisi delle vendite al dettaglio](../sample-datasets.md). Si supponga che si tratti dell'URL al report sul server di report in una cartella denominata "power-bi":

```
https://report-server/reports/power-bi/Retail-Analysis-Sample
```

Si noterà che la visualizzazione mappa nell'Esempio di analisi delle vendite al dettaglio mostra negozi nella Carolina del Nord e gli altri Stati.

![Visualizzazione mappa dell'Esempio di analisi delle vendite al dettaglio](media/quickstart-embed/report-server-retail-analysis-sample-map.png)

*NC* è il valore per la Carolina del Nord memorizzato nel campo **Territory** (Territorio) della tabella **Store** (Negozio). Dunque, per filtrare il report in modo da visualizzare solo i dati relativi ai negozi in Carolina del Nord, aggiungere all'URL quanto segue:

?filter=Store/Territory eq 'NC'

Ora il report viene filtrato in base alla Carolina del Nord; tutte le visualizzazioni nella pagina del report mostrano solo i dati relativi alla Carolina del Nord.

![Visualizzazioni filtrate dell'Esempio di analisi delle vendite al dettaglio](media/quickstart-embed/report-server-retail-analysis-sample-filtered-map.png)

### <a name="create-a-dax-formula-to-filter-on-multiple-values"></a>Creare una formula DAX per filtrare più valori

Un altro modo per filtrare in base a più campi consiste nel creare una colonna calcolata in Power BI Desktop che concateni due campi in un unico valore. quindi filtrare in base a tale valore.

L'Esempio di analisi delle vendite al dettaglio contiene due campi: Territory (Territorio) e Chain (Catena). In Power BI Desktop è possibile [creare una colonna calcolata](../desktop-tutorial-create-calculated-columns.md) (Campo) denominata TerritoryChain. Tenere presente che il nome **Campo** non può contenere spazi. Ecco la formula DAX per tale colonna.

TerritoryChain = [Territory] & "-" & [Chain]

Pubblicare il report nel Server di report di Power BI, quindi usare la stringa di query dell'URL per filtrare e visualizzare solo i dati relativi ai negozi Lindseys nella Carolina del Nord.

```
https://report-server/reports/power-bi/Retail-Analysis-Sample?filter=Store/TerritoryChain eq 'NC-Lindseys'

```

## <a name="next-steps"></a>Passaggi successivi

[Avvio rapido: Creare un report di Power BI per il server di report di Power BI](quickstart-create-powerbi-report.md)  
[Guida rapida: creare un report impaginato per il server di report di Power BI](quickstart-create-paginated-report.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)