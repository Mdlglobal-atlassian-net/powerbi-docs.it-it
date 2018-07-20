---
title: Come preparare correttamente i dati di Excel per l'uso di Domande e risposte in Power BI
description: Come preparare correttamente i dati per l'uso di Domande e risposte in Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: a6216169eb50ca535b73b07f5553c9b3d5e17470
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34240963"
---
# <a name="how-to-make-your-excel-data-work-well-with-qa-in-power-bi"></a>Come preparare correttamente i dati di Excel per l'uso di Domande e risposte in Power BI
Le persone che creano i modelli di dati o le cartelle di lavoro di Excel usati con Power BI devono leggere la sezione seguente.

Domande e risposte in Power BI è in grado di cercare i dati strutturati e scegliere la visualizzazione più adatta per la domanda. Ecco cosa lo rende uno strumento eccezionale.   

Domande e risposte può usare qualsiasi file Excel caricato contenente tabelle, intervalli o un modello PowerPivot, ma offre prestazioni migliori se i dati vengono ottimizzati e ripuliti.  Se si prevede di condividere report e dashboard basati su un set di dati, è possibile semplificare ai colleghi la formulazione delle domande per ottenere risposte di qualità.

### <a name="how-qa-works-with-excel"></a>Come funziona Domande e risposte con Excel
Domande e risposte ha un set di capacità di base per la comprensione del linguaggio naturale che funziona con tutti i dati. Ha una ricerca per parola chiave dipendente dal contesto per i nomi delle tabelle, delle colonne e dei campi calcolati di Excel. Inoltre, contiene informazioni predefinite su come filtrare, ordinare, aggregare, raggruppare e visualizzare i dati. 

Ad esempio, in una tabella di Excel denominata "Sales", con le colonne "Product", "Month", "Units Sold", "Gross Sales" e "Profit" si possono porre domande su una qualsiasi di queste entità.  Si può chiedere di mostrare le vendite, il profitto totale per mese, ordinare i prodotti per unità vendute e così via. Vedere altre informazioni sulla [tipologia di domande che è possibile porre](power-bi-q-and-a.md) e sui [tipi di visualizzazione che è possibile specificare in una query di Domande e risposte](power-bi-visualization-types-for-reports-and-q-and-a.md).

### <a name="prepare-an-excel-dataset-for-qa"></a>Preparare un set di dati di Excel per Domande e risposte
Domande e risposte si basa sui nomi delle tabelle, delle colonne e dei campi calcolati per rispondere a domande specifiche sui dati. Questo implica che le entità contenute nella cartella di lavoro sono importanti.

Ecco alcuni suggerimenti per utilizzare al meglio Domande e risposte nella cartella di lavoro.

* Verificare che i dati siano in una tabella di Excel. Ecco [come creare una tabella di Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Verificare che i nomi di tabelle, colonne e campi calcolati siano significativi nel linguaggio naturale.
  
  Ad esempio, se una tabella contiene dati sulle vendite, denominarla "Sales". I nomi di colonna come "Year", "Product", "Sales Rep" e "Amount" non funzionano in modo efficace con Domande e risposte.

* Se la cartella di lavoro ha un modello di dati Power Pivot, è possibile eseguire ancora altre ottimizzazioni. In questo collegamento sono disponibili altre informazioni sulla [Demistificazione di Domande e risposte di Power BI - Parte 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) elaborate dal team interno di esperti di linguaggio naturale.

* Aprire il set di dati in Power BI Desktop e creare nuove colonne, creare nuove misure calcolate, concatenare i campi per creare valori univoci, classificare i dati per tipo, ad esempio date, stringhe, informazioni geografiche, immagini, URL, e altro ancora.

## <a name="next-steps"></a>Passaggi successivi
Tornare a [Domande e risposte in Power BI](power-bi-q-and-a.md)  
[Preparare i set di dati locali per Domande e risposte](service-q-and-a-direct-query.md)   
[Guida introduttiva a Domande e risposte](power-bi-visualization-introduction-to-q-and-a.md)  
[Recuperare dati per Power BI](service-get-data.md)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

