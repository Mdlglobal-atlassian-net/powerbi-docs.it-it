---
title: Usare correttamente i dati di Excel con Domande e risposte di Power BI
description: Come preparare correttamente i dati per l'uso di Domande e risposte in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 102145e8c5b2fd3ad19b6703710405d06da5a93a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83323230"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Usare correttamente i dati di Excel con Domande e risposte di Power BI
Le persone che creano i modelli di dati o le cartelle di lavoro di Excel usati con Power BI devono leggere la sezione seguente.

Domande e risposte in Power BI è in grado di cercare i dati strutturati e scegliere la visualizzazione più adatta per la domanda. Ecco cosa lo rende uno strumento eccezionale.   

Domande e risposte può usare qualsiasi file Excel caricato contenente tabelle, intervalli o un modello PowerPivot, ma offre prestazioni migliori se i dati vengono ottimizzati e ripuliti.  Se si prevede di condividere report e dashboard basati su un set di dati, è possibile semplificare ai colleghi la formulazione delle domande per ottenere risposte di qualità.

## <a name="how-qa-works-with-excel"></a>Come funziona Domande e risposte con Excel
Domande e risposte ha un set di capacità di base per la comprensione del linguaggio naturale che funziona con tutti i dati. Ha una ricerca per parola chiave dipendente dal contesto per i nomi delle tabelle, delle colonne e dei campi calcolati di Excel. Inoltre, contiene informazioni predefinite su come filtrare, ordinare, aggregare, raggruppare e visualizzare i dati. 

Ad esempio, in una tabella di Excel denominata "Sales", con le colonne "Product", "Month", "Units Sold", "Gross Sales" e "Profit" si possono porre domande su una qualsiasi di queste entità.  Si può chiedere di mostrare le vendite, il profitto totale per mese, ordinare i prodotti per unità vendute e così via. Altre informazioni sull'[uso di Domande e risposte in dashboard e report](power-bi-tutorial-q-and-a.md) e sui [tipi di visualizzazione che è possibile specificare in una query di Domande e risposte](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Preparare un set di dati di Excel per Domande e risposte
Domande e risposte si basa sui nomi delle tabelle, delle colonne e dei campi calcolati per rispondere a domande specifiche sui dati. Questo implica che le entità contenute nella cartella di lavoro sono importanti.

Ecco alcuni suggerimenti per utilizzare al meglio Domande e risposte nella cartella di lavoro.

* Verificare che i dati siano in una tabella di Excel. Ecco [come creare una tabella di Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Verificare che i nomi di tabelle, colonne e campi calcolati siano significativi nel linguaggio naturale.
  
  Ad esempio, se una tabella contiene dati sulle vendite, denominarla "Sales". I nomi di colonna come "Year", "Product", "Sales Rep" e "Amount" non funzionano in modo efficace con Domande e risposte.

* Se la cartella di lavoro ha un modello di dati Power Pivot, è possibile eseguire ancora altre ottimizzazioni. In questo collegamento sono disponibili altre informazioni sulla [Demistificazione di Domande e risposte di Power BI - Parte 2](https://powerbi.microsoft.com/blog/demystifying-power-bi-q-amp-a-part-2/) elaborate dal team interno di esperti di linguaggio naturale.

* Aprire il set di dati in Power BI Desktop e creare nuove colonne, creare nuove misure calcolate, concatenare i campi per creare valori univoci, classificare i dati per tipo, ad esempio date, stringhe, informazioni geografiche, immagini, URL, e altro ancora.

## <a name="next-steps"></a>Passaggi successivi

- [Domande e risposte per i consumer](../consumer/end-user-q-and-a.md)  
- [Usare Domande e risposte in dashboard e report](power-bi-tutorial-q-and-a.md)
- [Preparare i set di dati locali per Domande e risposte](service-q-and-a-direct-query.md)   
- [Recuperare dati per Power BI](../connect-data/service-get-data.md)  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
