---
title: Ordinare per colonna in Power BI Desktop
description: In Power BI è possibile modificare l'aspetto di un oggetto visivo ordinandolo in base a campi dati diversi.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: db5bc2566e4711873629522d08a2d0c818071b81
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83334040"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Ordinare per colonna in Power BI Desktop
In Power BI Desktop e nel servizio Power BI è possibile modificare l'aspetto di un oggetto visivo ordinandolo in base a campi dati diversi. La modifica dell'ordinamento di un oggetto visivo consente di dare risalto alle informazioni da comunicare e di garantire che l'oggetto visivo evidenzi la tendenza prevista.

Che si usino dati numerici (come cifre di vendita) o dati di tipo testo (come nomi di stati), è possibile ordinare le visualizzazioni in modo da ottenere l'aspetto desiderato. In Power BI sono disponibili funzionalità molto flessibili per l'ordinamento e menu rapidi. Per ordinare un oggetto visivo, selezionare il menu **Altre opzioni** (...), scegliere **Ordina per** e quindi selezionare il campo in base al quale eseguire l'ordinamento.

![Menu Altre opzioni](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>Esempio di ordinamento
In questa sezione verrà usato un esempio caratterizzato da maggiore profondità e ne verrà illustrato il funzionamento in Power BI Desktop.

La visualizzazione seguente indica i costi, le quantità e gli importi per nome del produttore. Ecco come si presenta la visualizzazione prima di qualsiasi operazione di ordinamento:

![Visualizzazione iniziale](media/desktop-sort-by-column/sortbycolumn_1.png)

L'oggetto visivo è attualmente ordinato in base alla colonna **SalesQuantity**. È possibile determinare la colonna di ordinamento abbinando il colore delle barre ascendenti alla legenda, ma esiste un modo migliore: il menu **Altre opzioni** a cui si accede selezionando i puntini di sospensione (...).

![Menu Altre opzioni](media/desktop-sort-by-column/sortbycolumn_2.png)

Le selezioni di ordinamento sono le seguenti:

* Il campo di ordinamento corrente è **SalesQuantity**, indicato dalla voce **SalesQuantity** in grassetto, preceduta da una barra gialla. 

* La direzione di ordinamento corrente è crescente, come illustrato dalla voce **Ordinamento crescente** in grassetto, preceduta da una barra gialla.

Il campo e la direzione di ordinamento vengono analizzati in dettaglio nelle due sezioni successive.

## <a name="select-which-column-to-use-for-sorting"></a>Selezionare la colonna da usare per l'ordinamento
Si è notato che la barra gialla visualizzata prima di **SalesQuantity** nel menu **Altre opzioni** indica che l'oggetto visivo è ordinato in base alla colonna **SalesQuantity**. L'ordinamento in base a un'altra colonna è semplice. Basta selezionare i puntini di sospensione (...) per visualizzare il menu **Altre opzioni**, scegliere **Ordina per** e quindi selezionare una colonna diversa.

Nell'immagine seguente la colonna selezionata come base per l'ordinamento è **DiscountAmount**, che corrisponde a una delle linee nell'oggetto visivo anziché a una delle barre. 

![Ordinare in base a DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Si noti come è stato modificato l'oggetto visivo. I valori vengono ora ordinati dal valore massimo **DiscountAmount**, Fabrikam Inc., fino al valore minimo, Northwind Traders. 

Se si vuole un ordinamento crescente anziché decrescente, la sezione seguente illustra come è possibile ottenere facilmente tale risultato.

## <a name="select-the-sort-order"></a>Selezionare l'ordinamento
Osservando più da vicino il menu **Altre opzioni** dell'immagine precedente, si noterà che la voce **Ordinamento decrescente** è visualizzata in grassetto, preceduta da una barra gialla.

![Ordina dal più grande al più piccolo](media/desktop-sort-by-column/sortbycolumn_4.png)

Quando l'opzione **Ordinamento decrescente** è selezionata, l'oggetto visivo è ordinato in base alla colonna selezionata, dal valore più grande al più piccolo. Se si vuole modificare tale ordinamento, è sufficiente selezionare **Ordinamento crescente**. Il tipo di ordinamento della colonna selezionata cambierà dal valore più piccolo al più grande.

Di seguito è riportato lo stesso oggetto visivo, dopo la modifica dell'ordinamento di **DiscountAmount**. Si noti che ora Northwind Traders è il primo produttore nell'elenco e Fabrikam Inc. è l'ultimo, con un ordinamento opposto rispetto al precedente.

![Ordina dal più piccolo al più grande](media/desktop-sort-by-column/sortbycolumn_5.png)

È possibile eseguire l'ordinamento in base a qualsiasi colonna inclusa nell'oggetto visivo, ad esempio selezionare **SalesQuantity** come colonna base dell'ordinamento per visualizzare per primi i produttori con il volume di vendite maggiore, mantenendo comunque nell'oggetto visivo le altre colonne nel modo in cui si applicano al produttore. Ecco come si presenta l'oggetto visivo con tali impostazioni:

![Ordina per Quantità vendite](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Ordinamento con il pulsante Ordina per colonna
È possibile ordinare i dati in un altro modo, ovvero usando il pulsante **Ordina per colonna** nella scheda **Creazione di modelli** della barra multifunzione.

![Pulsante Ordina per colonna](media/desktop-sort-by-column/sortbycolumn_8.png)

Per questo approccio all'ordinamento è necessario selezionare prima la colonna (campo) da ordinare dal riquadro **Campi** e quindi selezionare **Creazione di modelli** > **Ordina per colonna** per ordinare l'oggetto visivo. Se non si seleziona una colonna, il pulsante **Ordina per colonna** è inattivo.

Si prenda ad esempio un caso comune. Sono disponibili i dati relativi a ogni mese dell'anno e si vuole ordinarli in ordine cronologico. La procedura seguente illustra come fare:

1. Prima di tutto, si noti che quando l'oggetto visivo è selezionato, ma non è selezionata alcuna colonna nel riquadro **Campi**, il pulsante **Ordina per colonna** è inattivo (in grigio).
   
   ![Pulsante Ordina per colonna inattivo](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Quando si seleziona la colonna in base alla quale si vuole eseguire l'ordinamento, nel riquadro **Campi** il pulsante **Ordina per colonna** diventa attivo.
   
   ![Pulsante Ordina per colonna attivo](media/desktop-sort-by-column/sortbycolumn_10.png)
3. A questo punto, con l'oggetto visivo selezionato, è possibile selezionare **MonthOfYear**, anziché il valore predefinito **MonthName**, e l'oggetto visivo viene ordinato in base al criterio desiderato, ovvero in base al mese dell'anno.
   
   ![Menu Ordina per colonna](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>Passaggi successivi

Potrebbero essere interessanti anche gli articoli seguenti:

* [Usare il drill-through tra report in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Filtri dei dati in Power BI](../visuals/power-bi-visualization-slicers.md)
