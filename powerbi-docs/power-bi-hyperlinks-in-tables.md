---
title: Aggiungere collegamenti ipertestuali a una tabella
description: Usare Power BI Desktop per creare collegamenti ipertestuali. Usare quindi Power BI Desktop o il servizio Power BI per aggiungere tali collegamenti ipertestuali alle tabelle e alle matrici di report.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 972abb3781cbaaff8a9617b70988c21f7389d4f9
ms.sourcegitcommit: 658b0de4f5a544d0906665b40925552804a61880
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2019
ms.locfileid: "54406662"
---
# <a name="add-hyperlinks-to-a-table"></a>Aggiungere collegamenti ipertestuali a una tabella
Questo argomento illustra come usare Power BI Desktop per creare collegamenti ipertestuali. Usare quindi Power BI Desktop o il servizio Power BI per aggiungere tali collegamenti ipertestuali alle tabelle e alle matrici di report. 

![Tabella con collegamenti ipertestuali](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> I collegamenti ipertestuali nei [riquadri dei dashboard](service-dashboard-edit-tile.md) e le [caselle di testo nei dashboard](service-dashboard-add-widget.md) possono essere creati in tempo reale con il servizio Power BI. I collegamenti ipertestuali nelle [caselle di testo nei report](service-add-hyperlink-to-text-box.md) può creato in volo utilizzare servizio Power BI e Power BI Desktop.
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Per creare un collegamento ipertestuale in una tabella o in una matrice con Power BI Desktop
È possibile creare collegamenti ipertestuali in tabelle e matrici in Power BI Desktop ma non dal servizio Power BI. I collegamenti ipertestuali possono anche essere creati in Excel Power Pivot prima dell'importazione della cartella di lavoro in Power BI. Entrambi i metodi sono descritti di seguito.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Creare un collegamento ipertestuale alla tabella o alla matrice in Power BI Desktop
La procedura per aggiungere un collegamento ipertestuale varia a seconda che i dati siano stati importati o connessi al server con DirectQuery. Entrambi gli scenari sono descritti di seguito.

### <a name="for-data-imported-into-power-bi"></a>Per i dati importati in Power BI
1. Se il collegamento ipertestuale non esiste già come campo nel set di dati, aggiungerlo come [colonna personalizzata](desktop-common-query-tasks.md) con Power BI Desktop.
2. In Vista dati selezionare la colonna e, nella scheda **Modellazione** scegliere l'elenco a discesa per **Categoria dati**.
   
    ![Elenco a discesa Categoria dati](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Selezionare un **URL Web**.
4. Passare alla Visualizzazione Report e creare una tabella o una matrice usando il campo stato categorizzato come URL Web. I collegamenti ipertestuali saranno di colore blu e sottolineati.

    ![Collegamenti di colore blu e sottolineati](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > Gli URL devono iniziare con **http:// , https://** o **www**.
    >
   
1. Se non si vuole visualizzare un URL lungo in una tabella, è possibile visualizzare un'icona di collegamento ipertestuale  ![Icona di collegamento ipertestuale](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) . Si noti che non è possibile visualizzare le icone nelle matrici.
   
   * Selezionare il grafico per attivarlo.
   * Selezionare l'icona del rullo ![Icona del rullo](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) per aprire la scheda Formattazione.
   * Espandere **Valori**, trovare **Icona URL** e selezionare **Sì**.
6. (Facoltativo) [Pubblicare il report dal Desktop a Servizio Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) e aprire il report nel Servizio Power BI. I collegamenti ipertestuali funzioneranno anche qui.

### <a name="for-data-connected-with-directquery"></a>Per i dati connessi con DirectQuery
Non è possibile creare una nuova colonna in modalità DirectQuery.  Se tuttavia i dati contengono già gli URL, è possibile attivarli nei collegamenti ipertestuali.

1. In Visualizzazione Report, creare una tabella usando un campo che contiene gli URL.
2. Selezionare la colonna e, nella scheda **Modellazione**, scegliere l'elenco a discesa per **Categoria dati**.
3. Selezionare un **URL Web**. I collegamenti ipertestuali saranno di colore blu e sottolineati.
4. (Facoltativo) [Pubblicare il report dal Desktop a Servizio Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) e aprire il report nel Servizio Power BI. I collegamenti ipertestuali funzioneranno anche qui.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Creare un collegamento ipertestuale alla tabella o alla matrice in Excel Power Pivot
Un altro modo per aggiungere collegamenti ipertestuali alle tabelle e matrici di Power BI consiste nel creare i collegamenti ipertestuali nel set di dati prima di importare o connettersi a tale set di dati da Power BI. Questo esempio usa una cartella di lavoro di Excel.

1. Aprire la cartella di lavoro in Excel.
2. Selezionare la scheda **PowerPivot** e quindi scegliere **Gestisci**.
   
   ![Aprire PowerPivot in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Quando PowerPivot viene aperto, selezionare la scheda **Avanzate**.
   
   ![Scheda Avanzate di PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Posizionare il cursore nella colonna che contiene gli URL da trasformare in collegamenti ipertestuali nelle tabelle di Power BI.
   
   > [!NOTE]
   > Gli URL devono iniziare con **http:// , https://** o **www**.
   > 
5. Nel gruppo **Proprietà report** selezionare l'elenco a discesa **Categoria di dati** e scegliere **URL Web**. 
   
   ![Elenco a discesa Categoria di dati in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Dal servizio Power BI o da Power BI Desktop connettersi a questa cartella di lavoro o importarla.
7. Creare una visualizzazione tabella che includa il campo URL.
   
   ![Creare una tabella in Power BI con il campo URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi
D: è possibile usare un URL personalizzato come collegamento ipertestuale in una tabella o matrice?    
R: No. È possibile usare un'icona di collegamento. Se è necessario testo personalizzato per i collegamenti ipertestuali e l'elenco di URL è breve, valutare la possibilità di usare una casella di testo.


## <a name="next-steps"></a>Passaggi successivi
[Visualizzazioni nei report di Power BI](visuals/power-bi-report-visualizations.md)

[Power BI - Concetti di base](consumer/end-user-basic-concepts.md)

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

