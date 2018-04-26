---
title: Uso delle tabelle calcolate in Power BI Desktop
description: Tabelle calcolate in Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 3b7e3204d918c84acaff1b98bbab0fc09c6f0b87
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Uso delle tabelle calcolate in Power BI Desktop
Con le tabelle calcolate è possibile aggiungere una nuova tabella al modello. Tuttavia, invece di eseguire query e caricare i valori nelle colonne della nuova tabella da un'origine dati, viene creata una formula Data Analysis Expressions (DAX) che definisce i valori della tabella. In Power BI Desktop, le tabelle calcolate vengono create usando la funzionalità Nuova tabella in Visualizzazione Report o Vista dati.

I dati vengono importati nel modello quasi sempre da un'origine dati esterna. Tuttavia, le tabelle calcolate offrono dei vantaggi. Le tabelle calcolate sono in genere preferibili per i dati e i calcoli intermedi da archiviare come parte del modello anziché da calcolare automaticamente o come parte di una query.

Diversamente dalle tabelle create come parte di una query, le tabelle calcolate create in Visualizzazione Report o Vista dati sono basate sui dati già caricati nel modello. Ad esempio, è possibile scegliere di usare union o cross join per gestire la relazione tra due tabelle.

Analogamente alle normali tabelle, le tabelle calcolate possono avere relazioni con altre tabelle. Le colonne nella tabella calcolata contengono i tipi di dati, la formattazione e possono appartenere a una categoria di dati. È possibile assegnare qualsiasi nome alle colonne e aggiungerle a una visualizzazione del report con le normali procedure usate per gli altri campi. Le tabelle calcolate vengono ricalcolate se una delle tabelle da cui vengono estratti i dati viene in qualche modo aggiornata.

Le tabelle calcolate calcolano i risultati usando [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX), un linguaggio delle formule pensato per essere usato con dati relazionali, come quelli in Power BI Desktop. DAX include una libreria con oltre 200 funzioni, operatori e costrutti che fornisce un'enorme flessibilità per la creazione di formule di calcolo dei risultati per quasi tutte le esigenze di analisi dei dati.

## <a name="lets-look-at-an-example"></a>Esempio
Jeff, responsabile di progetto in Contoso, ha una tabella con i dipendenti dell'area nordoccidentale e un'altra tabella con i dipendenti dell'area sudoccidentale. Jeff vuole unire le due tabelle in un'unica tabella.

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SoutwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Unire queste due tabelle con una tabella calcolate è piuttosto semplice. Sebbene Jeff possa creare una tabella calcolata in Visualizzazione Report o Vista dati, è un po' più semplice crearla in Vista dati perché è possibile visualizzare immediatamente la nuova tabella calcolata.

Nella scheda **Creazione di modelli**di **Vista dati** Jeff fa clic su **Nuova tabella**. Viene visualizzata una barra della formula.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff immette quindi la formula seguente:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

Viene creata una nuova tabella denominata Western Region Employees.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

La nuova tabella Western Region Employees di Jeff viene visualizzata nell'elenco Campi proprio come qualsiasi altra tabella. Jeff può creare relazioni ad altre tabelle, aggiungere misure e colonne calcolate nonché aggiungere uno dei campi della tabella ai report analogamente a qualsiasi altra tabella.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funzioni per le tabelle calcolate
Le tabelle calcolate possono essere definite da qualsiasi espressione DAX che restituisca una tabella, compreso un semplice riferimento a un'altra tabella. Ad esempio:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

È possibile usare le tabelle calcolate con DAX per risolvere molti problemi analitici. In questo articolo è stata fornita solo una rapida introduzione alle tabelle calcolate. Di seguito sono riportate alcune delle funzioni di tabella DAX più comuni che potrebbero risultare utili quando si inizia a lavorare con le tabelle calcolate:

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Per le [funzioni DAX che restituiscono queste e altre tabelle, vedere Riferimento ](https://msdn.microsoft.com/ee634396.aspx)alle funzioni DAX.

