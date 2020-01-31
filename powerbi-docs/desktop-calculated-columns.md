---
title: Uso delle colonne calcolate in Power BI Desktop
description: Colonne calcolate in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 425bf50ad6eb4da9b50f7d9cdc760ef71cb7bff2
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753295"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Creare colonne calcolate in Power BI Desktop
Con le colonne calcolate, è possibile aggiungere nuovi dati a una tabella già presente nel modello. Tuttavia, invece di eseguire query e caricare i valori nella nuova colonna da un'origine dati, viene creata una formula Data Analysis Expressions (DAX) che definisce i valori della colonna. In Power BI Desktop le colonne calcolate vengono create usando la funzionalità Nuova colonna nella visualizzazione **Report**.

A differenza delle colonne personalizzate, che vengono create come parte di una query usando **Aggiungi colonna personalizzata** in Editor di query, le colonne calcolate, che vengono create nella visualizzazione **Report** o nella visualizzazione **Dati**, si basano sui dati già caricati nel modello. Ad esempio, è possibile scegliere di concatenare i valori di due colonne diverse in due tabelle diverse ma correlate, eseguire addizioni o estrarre le sottostringhe.

Le colonne calcolate create vengono visualizzate nell'elenco **Campi** come qualsiasi altro campo, ma hanno un'icona speciale che indica che i valori sono il risultato di una formula. È possibile assegnare qualsiasi nome alle colonne e aggiungerle a una visualizzazione del report con le normali procedure usate per gli altri campi.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Le colonne calcolate calcolano i risultati usando DAX, un linguaggio delle formule pensato per essere usato con dati relazionali, come quelli in Power BI Desktop. DAX include una libreria con oltre 200 funzioni, operatori e costrutti. Questa libreria offre un'enorme flessibilità per la creazione di formule di calcolo dei risultati per quasi tutte le esigenze di analisi dei dati. Per altre informazioni su DAX, vedere [Nozioni di DAX in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Le formule DAX somigliano alle formule di Excel. In effetti, DAX ha molte funzioni analoghe ad Excel. Le funzioni DAX, tuttavia, sono concepite per funzionare su dati suddivisi in modo interattivo o filtrati in un report, come in Power BI Desktop. In Excel è possibile avere una formula diversa per ogni riga di una tabella. In Power BI, quando si crea una formula DAX per una nuova colonna, viene calcolato un risultato per ogni riga della tabella. I valori della colonna vengono ricalcolati in base alle esigenze, ad esempio quando vengono aggiornati i dati sottostanti e vengono modificati i valori.

## <a name="lets-look-at-an-example"></a>Esempio
Jeff è un responsabile delle spedizioni di Contoso e vuole creare un report che mostri il numero di spedizioni nelle diverse città. Ha una tabella **Geography** con campi separati per città e stato. Jeff vuole tuttavia che i report visualizzino i valori relativi alla città e allo stato come un unico valore sulla stessa riga. Al momento, la tabella **Geography** di Jeff non contiene il campo desiderato.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Con una colonna calcolata, tuttavia, Jeff può unire le città della colonna **City** con gli stati della colonna **State**.

Jeff fa clic con il pulsante destro del mouse sulla tabella **Geography**, quindi sceglie **Nuova colonna**. Immette quindi la formula DAX seguente nella barra della formula:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Questa formula crea semplicemente una nuova colonna denominata **CityState**. Per ogni riga della tabella **Geography**, acquisisce i valori dalla colonna **City**, aggiunge una virgola e uno spazio, quindi concatena i valori della colonna **State**.

Ora Jeff ha il campo che vuole.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Può aggiungerlo all'area di disegno report insieme al numero di spedizioni. Con il minimo sforzo, ora Jeff ha un campo **CityState** che può aggiungere a quasi tutti i tipi di visualizzazione. Quando Jeff crea una nuova mappa, Power BI Desktop riesce già a leggere i valori relativi alla città e allo stato nella nuova colonna.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Passaggi successivi
In questo articolo è stata fornita solo una rapida introduzione alle colonne calcolate. Per altre informazioni, vedere le risorse seguenti:

* Per scaricare un file di esempio e acquisire così informazioni dettagliate su come creare altre colonne, vedere [Esercitazione: Creare colonne calcolate in Power BI Desktop](desktop-tutorial-create-calculated-columns.md)

* Per altre informazioni su DAX, vedere [Nozioni di DAX in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

* Per altre informazioni sulle colonne create come parte di una query, vedere la sezione **Creare colonne personalizzate** in [Attività di query comuni in Power BI Desktop](desktop-common-query-tasks.md).  

