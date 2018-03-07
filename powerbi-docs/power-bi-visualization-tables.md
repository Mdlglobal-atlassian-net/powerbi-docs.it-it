---
title: Esercitazione - Visualizzazioni tabella nei report e nei dashboard di Power BI (esercitazione)
description: Suggerimenti per l'utilizzo di visualizzazioni tabella nei report e nei dashboard di Power BI, tra cui come ridimensionare la larghezza delle colonne.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/22/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d41fd5085912ec74312fa4a4b25060cbd4afba94
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="working-with-tables-in-power-bi-reports-and-dashboards-tutorial"></a>Utilizzo di tabelle nei report e nei dashboard di Power BI (esercitazione)
Una tabella è una griglia contenente dati correlati in una serie logica di righe e colonne. Può anche contenere intestazioni e una riga per i totali. Le tabelle funzionano bene con confronti quantitativi in cui si analizzano molti valori per una singola categoria. Ad esempio, questa tabella mostra 5 diverse misure per **Categoria**.

![](media/power-bi-visualization-tables/table.png)

## <a name="when-to-use-a-table"></a>Quando usare una tabella
Le tabelle rappresentano un'ottima scelta nelle seguenti situazioni:

* visualizzare e confrontare dati dettagliati e valori esatti (anziché rappresentazioni visive)
* visualizzare i dati in un formato tabulare
* visualizzare i dati numerici per categorie   

> [!NOTE]
> Se una tabella contiene troppi valori, è consigliabile convertirla in una matrice e/o usare il drill-down.
> 
> 
## <a name="prerequisites"></a>Prerequisiti
 - Servizio Power BI o Power BI Desktop
 - Esempio di analisi delle vendite al dettaglio


## <a name="create-a-table"></a>Creare una tabella
Verrà creata la tabella raffigurata nell'immagine precedente per visualizzare i valori delle vendite per categoria di elemento. Per seguire la procedura, accedere al servizio Power BI e selezionare **Recupera dati \> Esempi \> Esempio di analisi delle vendite al dettaglio > Connetti** e scegliere **Passa al dashboard. Per creare una visualizzazione sono necessarie autorizzazioni di modifica per il set di dati e per il report. Fortunatamente, gli esempi di Power BI sono tutti modificabili. Nei report condivisi da altri utenti non sarà possibile creare visualizzazioni.

1. Dal riquadro di spostamento a sinistra selezionare **Aree di lavoro > Area di lavoro personale**.    
2. Selezionare la scheda Set di dati e scorrere in basso fino al set di dati Esempio di analisi delle vendite al dettaglio appena aggiunto.  Selezionare l'icona **Crea report**.
   
    ![](media/power-bi-visualization-tables/power-bi-create-report.png)
2. Nell'editor di report, selezionare **Elemento** > **Categoria**.  Power BI crea automaticamente una tabella che elenca tutte le categorie.
   
    ![](media/power-bi-visualization-tables/power-bi-table1.png)
3. Selezionare **Sales > Average Unit Price** e **Sales > Last Year Sales** e **Sales > This Year Sales** e scegliere tutte e tre le opzioni (Value, Goal, Status).   
4. Nel riquadro Visualizzazioni, trovare l'area **Valori** e trascinare i valori fino a quando l'ordine delle colonne del grafico corrisponde alla prima immagine in questa pagina.  L'area Valori dovrebbe essere simile alla seguente.
   
    ![](media/power-bi-visualization-tables/power-bi-table2.png)
5. Aggiungere la tabella al dashboard selezionando l'icona Aggiungi  
   
     ![](media/power-bi-visualization-tables/pbi_pintile.png)

## <a name="format-the-table"></a>Formattare la tabella
Esistono molti modi per formattare una tabella e in questa sede ci si occuperà solo di alcuni di essi. Un ottimo modo per apprendere le altre opzioni di formattazione consiste nell'aprire il riquadro Formattazione (icona del rullo ![](media/power-bi-visualization-tables/power-bi-format.png)) ed esplorare.

* Provare a formattare la griglia della tabella. In questo caso è stata aggiunta una griglia blu verticale, è stato aggiunto spazio alle righe e sono state lievemente aumentate le dimensioni di profilo e testo.
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid2-new.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-grid3.png)
* Per le intestazioni di colonna è stato modificato il colore di sfondo, aggiunto un profilo e sono state aumentate le dimensioni del carattere. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-column.png)
  
    ![](media/power-bi-visualization-tables/power-bi-table-column2.png)
* Dopo alcune operazioni di formattazione aggiuntive, ecco la tabella definitiva. Poiché sono presenti numerose opzioni di formattazione, il modo migliore per imparare consiste nell'iniziare da una normale tabella, aprire il riquadro Formattazione ![](media/power-bi-visualization-tables/power-bi-format.png) e iniziare a esplorare. 
  
    ![](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Formattazione condizionale
Un tipo di formattazione è detto *formattazione condizionale* e viene applicata ai campi nell'area **Valori** del riquadro **Visualizzazioni** nel servizio Power BI o in Power BI Desktop. 

Con la formattazione condizionale per le tabelle, è possibile specificare i colori di sfondo e dei caratteri della cella personalizzati in base ai relativi valori, incluse le sfumature. 

1. Nel riquadro **Visualizzazioni** in Power BI Desktop o nel servizio Power BI selezionare la freccia rivolta verso il basso accanto al valore nell'area **Valori** che si vuole formattare o fare clic con il pulsante destro del mouse sul campo. È possibile gestire la formattazione condizionale solo per i campi nell'area **Valori** dell'area **Campi**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)
2. Selezionare **Scale dei colori di sfondo**. Nella finestra di dialogo visualizzata, è possibile configurare il colore, così come il valore *minimo* e *massimo*. Se si seleziona la casella **Divergente**, è possibile configurare anche un valore *Centro* facoltativo.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)
   
    Di seguito saranno applicate alcune regole di formattazione personalizzata ai valori del prezzo unitario medio (Average Unit Price). Selezionare **Divergente**, aggiungere alcuni colori e scegliere **OK**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
3. Aggiungere un nuovo campo alla tabella che contiene valori sia positivi sia negativi.  Selezionare **Sales > Total Sales Variance**. 
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)
4. Aggiungere la formattazione condizionale della barra dei dati selezionando la freccia giù accanto a **Total Sales Variance** e scegliendo **Formattazione condizionale > Barre dei dati**.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)
5. Nella finestra di dialogo visualizzata, impostare i colori di **Barra positiva**, **Barra negativa**, inserire un segno di spunta accanto a **Mostra solo barra** e apportare le modifiche desiderate.
   
    ![](media/power-bi-visualization-tables/power-bi-data-bars.png)
   
    Quando si seleziona **OK**, le barre dei dati sostituiscono i valori numerici nella tabella, rendendo più semplice l'analisi.
   
    ![](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)
6. Per rimuovere la formattazione condizionale da una visualizzazione, è sufficiente fare nuovamente clic con il pulsante destro del mouse sul campo e selezionare **Rimuovi formattazione condizionale**.

> [!TIP]
> La formattazione condizionale è disponibile anche nel riquadro di formattazione (icona del rullo). Selezionare il valore da formattare e quindi impostare **Scale di colori** o **Barre dei dati** su Attiva per applicare le impostazioni predefinite; per personalizzare le impostazioni, selezionare **Controlli avanzati**.
> 
> 

## <a name="adjust-the-column-width-of-a-table"></a>Regolare la larghezza della colonna di una tabella
A volte Power BI tronca un'intestazione di colonna in un report o un dashboard. Per visualizzare il nome dell'intera colonna, passare il mouse sullo spazio a destra dell'intestazione per visualizzare le doppie frecce, selezionare e trascinare.

![](media/power-bi-visualization-tables/resizetable.gif)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

