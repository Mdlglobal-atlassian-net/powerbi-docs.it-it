---
title: Esportare dati da una visualizzazione di Power BI
description: Esportare dati da una visualizzazione di report e da una visualizzazione di dashboard e visualizzarli in Excel.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: jtlLGRKBvXY
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/20/2018
ms.author: mihart
ms.openlocfilehash: 8567326cb685a03fd1af618aad5310234677ab6d
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="export-data-from-visualizations"></a>Esportare dati dalle visualizzazioni
È possibile [visualizzare in Power BI i dati](service-reports-show-data.md) usati per creare una visualizzazione o esportarli in Excel come file con estensione xlsx o csv.   

Osservare in che modo i dati vengono esportati da una delle visualizzazioni nel report, salvati come file XLSX e aperti in Excel. Seguire quindi le istruzioni successive per sotto il video per fare una prova in prima persona.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="from-a-visualization-on-a-power-bi-dashboard"></a>Da una visualizzazione in un dashboard di Power BI
1. Selezionare i puntini di sospensione nell'angolo in alto a destra della visualizzazione.
   
    ![](media/power-bi-visualization-export-data/pbi-export-tile3.png)
2. Scegliere l’icona  **Esporta dati** .
   
    ![](media/power-bi-visualization-export-data/pbi_export_dash.png)
3. I dati vengono esportati in un file CSV. Se l'oggetto visivo è filtrato, verranno filtrati anche i dati scaricati.
4. Il browser richiederà di salvare il file.  Una volta salvato, aprire il file con estensione csv in Excel.
   
    ![](media/power-bi-visualization-export-data/pbi-export-to-excel.png)

## <a name="from-a-visualization-in-a-report"></a>Da una visualizzazione in un report
Per iniziare, aprire il [report dell'esempio di analisi dell'approvvigionamento](sample-procurement.md) in [Visualizzazione di modifica](service-reading-view-and-editing-view.md). [Aggiungere una nuova pagina del report vuota](power-bi-report-add-page.md). Seguire quindi questa procedura per aggiungere un'aggregazione e un filtro a livello di visualizzazione.

1. Creare un nuovo grafico a colonne.  Nel riquadro Campi, selezionare **Location > City** e **Invoice > Discount Percent**.  Potrebbe essere necessario spostare **Discount Percent** nell'area Value. 
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data3.png)
2. Modificare l'aggregazione per **Discount Percent** da **Count** a **Average**. Nell'area Value, selezionare la freccia a destra di **Discount Percent** (o altrimenti **Count of Discount Percent**) e scegliere **Average**.
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data6.png)
3. Aggiungere un filtro a **City** per rimuovere **Atlanta**.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data4.png)
   
   È ora possibile provare a usare entrambe le opzioni di esportazione dei dati.
4. Selezionare i puntini di sospensione nell'angolo in alto a destra della visualizzazione. Scegliere  **Esporta dati**.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data2.png)
5. Se la visualizzazione contiene un'aggregazione (ad esempio se si modifica **Count** in *average*, **sum** o *minimum*), si avranno due opzioni: **Riepilogo dati** e **Dati sottostanti**. Per altre informazioni sulle aggregazioni, vedere [Aggregazioni in Power BI](service-aggregates.md).
   
    ![](media/power-bi-visualization-export-data/power-bi-export-data5.png)
6. Selezionare **Riepilogo dati** > **Esporta** e scegliere xlsx o csv. Power BI esporta i dati.  Se sono stati applicati i filtri per la visualizzazione, i dati verranno esportati come filtrati. Quando si seleziona **Esporta**, il browser richiede di salvare il file. Una volta salvato, aprire il file in Excel.
   
   **Riepilogo dati**: selezionare questa opzione se non si ha un'aggregazione oppure se si ha un'aggregazione, ma non si vuole visualizzare la suddivisione completa. Ad esempio, se è presente un grafico a barre che mostra quattro barre, si otterranno quattro righe di dati. Il riepilogo dati è disponibile in formato XLSX e CSV.
   
   In questo esempio, l'esportazione di Excel mostra un totale per ogni città. Poiché è stata filtrata Atlanta, non è inclusa nei risultati.  La prima riga il foglio del calcolo illustra i filtri che sono stati usati durante l'estrazione dei dati da Power BI.
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data7.png)
7. Ora provare a selezionare **Dati sottostanti** > **Esporta** e scegliere xlsx. Power BI esporta i dati. Se sono stati applicati i filtri per la visualizzazione, i dati verranno esportati come filtrati. Quando si seleziona **Esporta**, il browser richiede di salvare il file. Una volta salvato, aprire il file in Excel.
   
   >[!WARNING]
   >L'esportazione dei dati sottostanti consente agli utenti di visualizzare tutti i dati dettagliati, cioè ogni colonna nei dati. Gli amministratori del servizio Power BI possono disattivare questa funzionalità per l'organizzazione. Se dispone di un set di dati, è possibile impostare le colonne proprietarie su "nascosto" in modo che non vengono visualizzate nell'elenco Campi nel servizio Power BI o Desktop.
   
   
   **Dati sottostanti**: selezionare questa opzione se la visualizzazione ha un'aggregazione e si vogliono visualizzare tutti i dettagli sottostanti. In sostanza, selezionando *Dati sottostanti* viene rimossa l'aggregazione. Quando si seleziona **Esporta**, i dati vengono esportati in un file con estensione xlsx e il browser richiede di salvare il file. Una volta salvato, aprire il file in Excel.
   
   In questo esempio, l'esportazione Excel mostra una riga per ogni singola riga City nel set di dati e la percentuale di sconto per quella voce singola. In altre parole, i dati sono in formato flat e non aggregati. La prima riga il foglio del calcolo illustra i filtri che sono stati usati durante l'estrazione dei dati da Power BI.  
   
   ![](media/power-bi-visualization-export-data/power-bi-export-data8.png)

## <a name="limitations-and-considerations"></a>Limitazioni e considerazioni
* Il numero massimo di righe che possono essere esportate da **Power BI Desktop** e dal **servizio Power BI** a un file con estensione csv è 30.000.
* Il numero massimo di righe che possono essere esportati in formato XLSX è 150.000.
* L'esportazione tramite *Dati sottostanti* non funzionerà se l'origine dati è una connessione di Analysis Services in tempo reale con una versione precedente alla versione 2016 e se le tabelle nel modello non hanno una chiave univoca.  
* L'esportazione tramite *Dati sottostanti* non funzionerà se l'opzione *Mostra elementi senza dati* è abilitata per la visualizzazione esportata.
* Quando si usa DirectQuery, è possibile esportare al massimo 16 MB di dati. È quindi possibile che venga esportata una quantità di dati inferiore al numero massimo di righe, in particolare se sono presenti molte colonne, se i dati sono difficili da comprimere o se sono presenti altri fattori che incrementano le dimensioni del file e riducono il numero di righe esportate.
* Power BI supporta solo l'esportazione negli oggetti visivi che usano le aggregazioni di base. L'esportazione non è disponibile per gli oggettivi visivi con misure di modello o del report.
* Gli oggetti visivi personalizzati e gli oggetti visivi R non sono attualmente supportati.
* L'esportazione dei dati non è disponibile per utenti esterni all'organizzazione che usano un dashboard non condiviso con tali utenti. 
* Se nel file con estensione CSV è presente il carattere unicode, il testo in Excel potrebbe non essere visualizzato correttamente, ma aprendolo in Blocco note apparirà correttamente. Esempi di carattere unicode sono i simboli di valuta e parole straniere. La soluzione alternativa consiste nell'importare il file con estensione CSV in Excel, invece di aprirlo direttamente. A tale scopo:
  
  1. Apri Excel
  2. Dalla scheda **Dati** selezionare **Carica dati esterni** > **da testo**.
* Gli amministratori di Power BI hanno la possibilità di disabilitare l'esportazione dei dati.

## <a name="next-steps"></a>Passaggi successivi
[Dashboard in Power BI](service-dashboards.md)  
[Report in Power BI](service-reports.md)  
[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

