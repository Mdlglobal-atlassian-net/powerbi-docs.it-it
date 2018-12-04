---
title: Oggetti visivi degli indicatori KPI
description: Creare oggetto visivi indicatore KPI in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0492390ae47c8d5aa0930a063370712c80d61de2
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829643"
---
# <a name="kpi-visuals"></a>Oggetti visivi degli indicatori KPI
Un indicatore di prestazioni chiave (KPI) è un segnale visivo che comunica lo stato di avanzamento verso un obiettivo misurabile. Per altre informazioni sugli indicatori KPI, vedere [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050).

Se non si è ancora iscritti a Power BI, [iscriversi per ottenere una versione di prova gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) prima di iniziare.

## <a name="prerequisites"></a>Prerequisiti
* [Power BI Desktop è gratuito.](https://powerbi.microsoft.com/en-us/get-started/)
* [File con estensione pbix dell'esempio di analisi delle vendite al dettaglio](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="when-to-use-a-kpi"></a>Quando usare un indicatore KPI
Gli indicatori KPI rappresentano un'ottima scelta nelle seguenti situazioni:

* per misurare lo stato di avanzamento, in modo da stabilire se si è avanti o indietro
* per misurare la distanza da un obiettivo, e stabilire quindi quanto manca alla fine   

## <a name="kpi-requirements"></a>Requisiti degli indicatori di prestazioni chiave
Un indicatore di prestazioni chiave (KPI) si basa su una misura specifica e consente di valutare il valore corrente e lo stato di una metrica rispetto a un target definito. Gli indicatori KPI richiedono pertanto una misura *di base* che restituisca un valore e una misura o un valore *di destinazione*, nonché una *soglia* o un *obiettivo*.

Attualmente, i set di dati degli indicatori KPI devono contenere valori obiettivo per i KPI. Se il set di dati non ne contiene uno, è possibile creare obiettivi aggiungendo un foglio di Excel con obiettivi al modello di dati o al file PBIX.


## <a name="how-to-create-a-kpi"></a>Come creare un indicatore KPI
Per seguire la procedura, aprire il [file con estensione pbix dell'esempio di analisi delle vendite al dettaglio](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) in Power BI Desktop. Verrà creato un indicatore KPI che misura lo stato di avanzamento verso un obiettivo di vendita.

In alternativa, il video seguente mostra come creare singoli oggetti visivi di metrica: misuratori, schede e indicatori KPI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Aprire il report nella visualizzazione Report e selezionare la scheda di colore giallo per aggiungere una nuova pagina.    
2. Nel riquadro Campi selezionare **Sales > Total Units This Year**.  Questo sarà l'indicatore.
3. Aggiungere **Time > FiscalMonth**.  Questi rappresenteranno la tendenza.
4. IMPORTANTE: ordinare il grafico per **FiscalMonth**. Dopo la conversione della visualizzazione in un indicatore KPI, non sono disponibili opzioni di ordinamento.

    ![](media/power-bi-visualization-kpi/power-bi-chart.png)
5. Convertire l'oggetto visivo in un indicatore KPI selezionando l'icona dell'indicatore KPI nel riquadro di visualizzazione.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-template.png)
6. Aggiungere un obiettivo. Aggiungere le vendite dell'ultimo anno come obiettivo. Trascinare **Total Units Last Year** nel campo **Obiettivi target**.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-done.png)
7. È facoltativamente possibile formattare l'indicatore KPI selezionando l'icona del rullo per aprire il riquadro formattazione.
   
   * **Indicatore**: controlla l'unità di visualizzazione dell'indicatore e i decimali.
   * **Asse tendenza**: se impostato su **On**, l'asse di tendenza viene visualizzato come sfondo dell'oggetto visivo degli indicatori KPI.  
   * **Obiettivi**: se impostato su **On**, l'oggetto visivo visualizza l'obiettivo e la distanza dall'obiettivo in percentuale.
   * **Codifica a colori > Direzione**: alcuni indicatori KPI sono considerati *migliori* per i valori superiori, altri sono considerati *migliori* per i valori più bassi. Ad esempio, gli utili piuttosto che i tempi di attesa. In genere un valore di utili più elevato è migliore rispetto a un valore maggiore del tempo di attesa. Selezionare **un valore elevato è migliore** e facoltativamente modificare le impostazioni dei colori.


Gli indicatori KPI sono disponibili anche nel servizio Power BI e nei dispositivi mobili, in modo che sia possibile essere sempre connessi al cuore della propria attività.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* Se l'indicatore KPI non è simile al precedente, può essere necessario eseguire l'ordinamento in base a FiscalMonth. Poiché gli indicatori KPI non includono alcuna opzione di ordinamento, sarà necessario ordinare in base a FiscalMonth *prima* di convertire la visualizzazione in un indicatore KPI.

## <a name="next-steps"></a>Passaggi successivi

[Mappe di base in Power BI](power-bi-map-tips-and-tricks.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)