---
title: Grafici ad anello in Power BI (esercitazione)
description: 'Esercitazione: Grafici ad anello in Power BI'
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 2f428095eb57c5358770f1d6d8572316d2b84c37
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Grafici ad anello in Power BI (esercitazione)
Un grafico ad anello è simile a un grafico a torta perché mostra la relazione delle parti rispetto a un intero. L'unica differenza è data dal fatto che il centro è vuoto e consente di inserire un'etichetta o un'icona.

## <a name="create-a-doughnut-chart"></a>Creare un grafico ad anello
Per seguire la procedura, accedere a Power BI e selezionare **Recupera dati** \> **Esempi** \> **Esempio di analisi delle vendite al dettaglio** \> **Connetti**. 

1. Dal dashboard selezionare il riquadro **Total Stores** per aprire il report "Esempio di analisi delle vendite al dettaglio".
2. Selezionare **Modifica report** per aprire il report in Visualizzazione di modifica.
3. [Aggiungere una nuova pagina del report](power-bi-report-add-page.md).
4. Creare un grafico ad anello che visualizzi le vendite dell'anno per categoria.
   
   * Dal riquadro **Campi** selezionare **Vendite**\>**Vendite dello scorso anno**.
   * Convertire in un grafico ad anello. Se Last Year Sales non è nell'area **Valori** , trascinarlo in tale area.
     
       ![](media/power-bi-visualization-doughnut-charts/convertdonut.png)
   * Selezionare **Elemento** \> **Categoria** per aggiungerlo all'area **Legenda**. 
     
       ![](media/power-bi-visualization-doughnut-charts/doughnuttutorial.png)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
* La somma dei valori del grafico ad anello deve essere pari al 100%.
* Un eccessivo numero di categorie ne rende difficile la lettura e l'interpretazione.
* I grafici ad anello sono particolarmente indicati per confrontare una specifica sezione con l'intero, invece di confrontare singole sezioni reciprocamente. 

## <a name="next-steps"></a>Passaggi successivi
[Report in Power BI](service-reports.md)

[Tipi di visualizzazione in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualizzazioni nei report di Power BI](power-bi-report-visualizations.md)

[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

