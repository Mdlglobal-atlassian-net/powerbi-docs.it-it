---
title: Oggetti visivi indicatore di prestazioni chiave (KPI)
description: Creare oggetti visivi indicatore di prestazioni chiave (KPI) in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/30/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 7f865c53a1a47ad53137f0e7659917689243b914
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865174"
---
# <a name="create-key-performance-indicator-kpi-visualizations"></a>Creare oggetti visivi indicatore di prestazioni chiave (KPI) in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un indicatore di prestazioni chiave (KPI) è un segnale visivo che comunica lo stato di avanzamento verso un obiettivo misurabile. Per altre informazioni sugli indicatori KPI, vedere [Indicatori di prestazioni chiave (KPI) in PowerPivot](/previous-versions/sql/sql-server-2012/hh272050(v=sql.110)).


## <a name="when-to-use-a-kpi"></a>Quando usare un indicatore KPI

Gli indicatori KPI rappresentano un'ottima scelta nelle seguenti situazioni:

* Per misurare lo stato di avanzamento. Risponde alla domanda "per cosa sono avanti o indietro?"

* Per misurare la distanza da un obiettivo. Risponde alla domanda "quanto sono avanti o indietro?"

## <a name="kpi-requirements"></a>Requisiti degli indicatori di prestazioni chiave

I progettisti basano gli oggetti visivi per gli indicatori KPI su una misura specifica. Lo scopo dell'indicatore KPI è agevolare la valutazione del valore e dello stato corrente di una metrica rispetto a un valore di destinazione definito. Un oggetto visivo indicatore KPI richiede una misura *di base* che restituisca un valore e una misura o un valore di *destinazione*, nonché una *soglia* o un *obiettivo*.

I set di dati degli indicatori KPI devono contenere valori obiettivo per gli indicatori KPI. Se il set di dati non contiene i valori obiettivo, è possibile crearli aggiungendo un foglio di Excel con obiettivi al modello di dati o al file PBIX.

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione usa il [file Retail Analysis Sample PBIX](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Nella sezione in alto a sinistra della barra dei menu selezionare **File** > **Apri**

1. Trovare la copia del **file Retail Analysis Sample PBIX**

1. Aprire il **file PBIX di Retail Analysis Sample** in visualizzazione report. ![Screenshot dell'icona della visualizzazione report.](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. Selezionare **+** per aggiungere una nuova pagina. ![Screenshot della scheda gialla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png)

> [!NOTE]
> Per condividere il report con un collega di Power BI, è necessario che entrambi gli utenti abbiano licenze di Power BI Pro individuali o che il report venga salvato nella capacità Premium.    

## <a name="how-to-create-a-kpi"></a>Come creare un indicatore KPI

In questo esempio verrà creato un indicatore KPI che misura lo stato di avanzamento verso il raggiungimento di un obiettivo di vendita.

1. Nel riquadro **Campi** selezionare **Sales > Total Units This Year**.  Questo valore sarà l'indicatore.

1. Aggiungere **Time > FiscalMonth**.  Questo valore rappresenterà la tendenza.

1. Nell'angolo superiore destro dell'oggetto visivo selezionare i puntini di sospensione e verificare che Power BI abbia disposto le colonne in ordine crescente per **FiscalMonth**.

    > [!IMPORTANT]
    > Dopo la conversione della visualizzazione in un indicatore KPI, **non** sono disponibili opzioni di ordinamento. È necessario applicare ora l'ordinamento corretto.

    ![Screenshot del menu con i puntini di sospensione espanso con le opzioni Ordinamento crescente e FiscalMonth selezionate.](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    Dopo aver applicato l'ordine corretto, l'oggetto visivo avrà un aspetto simile al seguente:

    ![Screenshot dell'oggetto visivo ordinato in modo corretto.](media/power-bi-visualization-kpi/power-bi-chart.png)

1. Convertire l'oggetto visivo in un indicatore KPI selezionando l'icona dell'indicatore **KPI** nel riquadro **Visualizzazioni**.

    ![Screenshot del riquadro Visualizzazioni con l'icona KPI evidenziata.](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. Per aggiungere un obiettivo, trascinare **Total Units Last Year** nel campo **Obiettivi target**.

    ![Screenshot dell'oggetto visivo indicatore KPI completato e del riquadro Campi con i valori.](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. È facoltativamente possibile formattare l'indicatore KPI selezionando l'icona del rullo per aprire il riquadro formattazione.

    * **Indicatore**: controlla l'unità di visualizzazione dell'indicatore e i decimali.

    * **Asse tendenza**: se impostato su **Attiva**, l'oggetto visivo mostra l'asse della tendenza come sfondo dell'oggetto visivo indicatore KPI.  

    * **Obiettivi**: se impostato su **Attiva**, l'oggetto visivo mostra l'obiettivo e la distanza dall'obiettivo in percentuale.

    * **Codifica a colori > Direzione**: alcuni indicatori KPI sono considerati migliori per i valori *più alti*, altri sono considerati migliori per i valori *più bassi*. Ad esempio, gli utili piuttosto che i tempi di attesa. In genere un valore di utili più elevato è migliore rispetto a un valore maggiore del tempo di attesa. Selezionare **Massimo è corretto** e modificare facoltativamente le impostazioni dei colori.

Gli indicatori KPI sono disponibili anche nel servizio Power BI e nei dispositivi mobili. Offrono la possibilità di essere sempre aggiornati sulle prestazioni dell'azienda.

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

Se l'indicatore KPI non è simile al precedente, è possibile che non sia stato applicato l'ordinamento in base a **FiscalMonth**. Gli indicatori KPI non hanno un'opzione di ordinamento. È necessario iniziare di nuovo e impostare l'ordinamento in base a **FiscalMonth** *prima* di convertire la visualizzazione in indicatore KPI.

## <a name="next-steps"></a>Passaggi successivi

* [Suggerimenti e consigli per le visualizzazioni mappa di Power BI](power-bi-map-tips-and-tricks.md)

* [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
