---
title: Grafici a misuratore radiale in Power BI
description: Grafici a misuratore radiale in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b0db9aebe72d54aa464ec012e614ae0ec5bc723
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390646"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Grafici a misuratore radiale in Power BI

Un grafico a misuratore radiale è contraddistinto da un arco circolare e mostra un unico valore che misura lo stato rispetto al raggiungimento di un obiettivo o a un indicatore di prestazioni chiave (KPI). La linea (o *lancetta*) rappresenta il valore dell'obiettivo o di destinazione. L'ombreggiatura rappresenta lo stato di avanzamento rispetto al raggiungimento di tale obiettivo. Il valore all'interno dell'arco rappresenta il valore dello stato di avanzamento. Power BI distribuisce uniformemente tutti i valori possibili lungo l'arco, da quello minimo (all'estrema sinistra) a quello massimo (all'estrema destra).

![Screenshot del misuratore radiale.](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

In questo esempio un rivenditore di auto vuole tenere traccia delle vendite medie mensili del team di vendita. La lancetta rappresenta un obiettivo di vendita di 140 auto. Il valore minimo possibile per le vendite medie è pari a 0, mentre quello massimo è 200.  L'ombreggiatura blu mostra che per il mese corrente la media del team è pari all'incirca a 120 vendite, ma manca ancora una settimana per raggiungere l'obiettivo.

Il video seguente mostra come creare singoli oggetti visivi di metrica: misuratori, schede e indicatori KPI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Quando usare un misuratore radiale

I misuratori radiali sono ideali per:

* Mostrare lo stato rispetto al raggiungimento di un obiettivo.

* Rappresentare una misura percentile, ad esempio un indicatore KPI.

* Mostrare l'integrità di una singola misura.

* Visualizzare informazioni che possono essere esaminate e comprese rapidamente.

## <a name="prerequisites"></a>Prerequisiti

* Servizio Power BI o Power BI Desktop

* Cartella di lavoro di Excel di esempio Financial: [scaricare l'esempio direttamente](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Creare un misuratore radiale di base

Queste istruzioni usano il servizio Power BI. Per seguire la procedura, accedere a Power BI e aprire il file di Excel relativo all'esempio Financial.

### <a name="step-1-open-the-financial-sample-excel-file"></a>Passaggio 1: Aprire il file di Excel relativo all'esempio Financial

1. Se non è già disponibile, scaricare il [file di Excel Financial Sample](../sample-financial-download.md). Ricordare il percorso in cui viene salvato.

1. All'interno del servizio Power BI, selezionare **Recupera dati** > **File**.

1. Selezionare **File locale** e passare al percorso del file di esempio.

1. Selezionare **Importa**. Power BI aggiunge Financial Sample all'area di lavoro personale come set di dati.

1. Nell'elenco di contenuto **Set di dati** selezionare l'icona **Crea report** per  **Financial Sample**.

    ![Screenshot dell'elenco Set di dati con una freccia rivolta verso l'icona Crea report per Financial Sample.](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Passaggio 2: Creare un misuratore per tenere traccia delle vendite lorde

Quando è stata selezionata l'icona **Crea report** nella sezione precedente, Power BI ha creato un report vuoto nella visualizzazione di modifica.

1. Nel riquadro **Campi** selezionare **Gross Sales**.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)

1. Modificare l'aggregazione impostandola su **Media**.

   ![Screenshot del riquadro Campi con Gross Sales e l'aggregazione Media evidenziati.](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)

1. Selezionare l'icona del misuratore ![Screenshot dell'icona del misuratore.](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) per convertire l'istogramma in un grafico a misuratore.

    ![Screenshot del grafico a misuratore.](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

    A seconda di quando si scarica il file **Financial Sample**, è possibile che i numerosi visualizzati non corrispondano a quelli in questo articolo.

    > [!TIP]
    > Per impostazione predefinita, Power BI crea un grafico a misuratore in cui si presuppone che il valore corrente (in questo caso **Average of Gross Sales**) sia a metà strada nel misuratore. Dal momento che il valore di **Average Gross Sales** è pari a 182.760 dollari, il valore iniziale (minimo) è impostato su 0 e quello finale (massimo) sul doppio del valore corrente.

### <a name="step-3-set-a-target-value"></a>Passaggio 3: Impostare un valore di destinazione

1. Trascinare **COGS** dal riquadro **Campi** all'area **Valore di destinazione**.

1. Modificare l'aggregazione impostandola su **Media**.

   Power BI aggiunge una lancetta che rappresenta il valore target pari a **145.480 dollari**.

   ![Screenshot del grafico a misuratore con il campo Media di COGS aggiunto.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)

    Notare che il valore di destinazione è stato superato.

   > [!NOTE]
   > È anche possibile immettere manualmente un valore target. Vedere la sezione [Usare le opzioni di formattazione manuale per impostare i valori minimo, massimo e di destinazione](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Passaggio 4: Impostare un valore massimo

Nel passaggio 2 Power BI ha usato il campo **Valore** per impostare automaticamente i valori minimo e massimo. Potrebbe però essere necessario, ad esempio, impostare un valore massimo personalizzato. Si supponga che invece di usare un valore doppio di quello corrente come valore massimo possibile, si voglia impostarlo sul valore massimo di Gross Sales nel set di dati.

1. Trascinare **Gross Sales** dal riquadro **Campi** nell'area **Valore massimo**.

1. Modificare l'aggregazione impostandola su **Max**.

   ![Screenshot del riquadro Campi con Gross Sales e l'aggregazione Massimo evidenziati.](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)

   Il misuratore viene ridisegnato con un nuovo valore finale, pari a 1,21 milioni di vendite lorde.

   ![Screenshot del grafico a misuratore completato.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Passaggio 5: Salva il report

1. [Salvare il report](../service-report-save.md).

1. [Aggiungere il grafico a misuratore come riquadro del dashboard](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Usare le opzioni di formattazione manuale per impostare i valori minimo, massimo e di destinazione

1. Rimuovere **Max of Gross Sales** dall’area **Maximum value** .

1. Selezionare l'icona del rullo per aprire il riquadro **Formato**.

   ![Screenshot del grafico a misuratore e del riquadro Formato con l'icona del rullo evidenziata.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Espandere **Asse misuratore** e immettere i valori per **Minimo** e **Massimo**.

    ![Screenshot delle opzioni per Asse misuratore.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Deselezionare l'opzione **COGS** nel riquadro **Campi** per rimuovere il valore di destinazione.

    ![Screenshot dell'opzione COGS deselezionata.](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)

1. Quando il campo **Target** viene visualizzato sotto **Asse del misuratore**, immettere un valore.

     ![Screenshot delle opzioni per Asse misuratore con Target evidenziato.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Facoltativamente, continuare la formattazione del grafico del misuratore.

Dopo aver completato questi passaggi si otterrà un grafico a misuratore simile al seguente:

![Screenshot del grafico a misuratore finale.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Passaggio successivo

* [Oggetti visivi indicatore di prestazioni chiave (KPI)](power-bi-visualization-kpi.md)

* [Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)