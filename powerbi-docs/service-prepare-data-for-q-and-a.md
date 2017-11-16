---
title: Usare correttamente i dati con Domande e risposte di Power BI
description: Usare correttamente i dati con Domande e risposte di Power BI
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 499c3beca9046af9336de6dfec96994004050986
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="make-your-data-work-well-with-qa-in-power-bi"></a>Usare correttamente i dati con Domande e risposte di Power BI
Le persone che creano i modelli di dati o le cartelle di lavoro di Excel usati con Power BI devono leggere la sezione seguente.

Domande e risposte in Power BI è in grado di cercare i dati strutturati e scegliere la visualizzazione più adatta per la domanda. Ecco cosa lo rende uno strumento eccezionale.   

Domande e risposte può usare qualsiasi file Excel caricato contenente tabelle, intervalli o un modello PowerPivot, ma offre prestazioni migliori se i dati vengono ottimizzati e ripuliti. 

## <a name="how-qa-works"></a>Come funziona Domande e risposte
Domande e risposte ha un set di capacità di base per la comprensione del linguaggio naturale che funziona con tutti i dati. Ha una ricerca per parola chiave dipendente dal contesto per i nomi delle tabelle, delle colonne e dei campi calcolati di Excel. Inoltre, contiene informazioni predefinite su come filtrare, ordinare, aggregare, raggruppare e visualizzare i dati. 

Ad esempio, in una tabella di Excel denominata "Sales", con le colonne "Product", "Month", "Units Sold", "Gross Sales" e "Profit" si possono porre domande su una qualsiasi di queste entità.  Si può chiedere di mostrare le vendite, il profitto totale per mese, ordinare i prodotti per unità vendute e così via. In questi collegamenti sono disponibili altre informazioni sul [tipo di domande che è possibile porre](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-1.aspx), su come [porre domande usando un modello di domanda](service-q-and-a.md) e sui [tipi di visualizzazione che è possibile specificare in una query di Domande e risposte](power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-a-workbook-for-qa"></a>Preparare una cartella di lavoro per Domande e risposte
Domande e risposte si basa sui nomi delle tabelle, delle colonne e dei campi calcolati per rispondere a domande specifiche sui dati. Questo implica che le entità contenute nella cartella di lavoro sono importanti.

Ecco alcuni suggerimenti per utilizzare al meglio Domande e risposte nella cartella di lavoro.

* Verificare che i dati siano in una tabella di Excel. Ecco [come creare una tabella di Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Verificare che i nomi delle tabelle, delle colonne e dei campi calcolati siano significativi in inglese.
  
  Ad esempio, se una tabella contiene dati sulle vendite, denominarla "Sales". I nomi di colonna come "Year", "Product", "Sales Rep" e "Amount" non funzionano in modo efficace con Domande e risposte.

> [!NOTE]
> Se la cartella di lavoro ha un modello di dati Power Pivot, è possibile eseguire ancora altre ottimizzazioni. In questo collegamento sono disponibili altre informazioni sulla [Demistificazione di Domande e risposte di Power BI - Parte 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) elaborate dal team interno di esperti di linguaggio naturale.
> 
> 

## <a name="next-steps"></a>Passaggi successivi
[Domande e risposte in Power BI](service-q-and-a.md)  
[Esercitazione: Introduzione a Domande e risposte di Power BI](power-bi-visualization-introduction-to-q-and-a.md)  
[Recuperare dati per Power BI](service-get-data.md)  
[Power BI - Concetti di base](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

