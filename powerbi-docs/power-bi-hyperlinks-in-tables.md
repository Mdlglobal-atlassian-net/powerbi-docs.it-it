---
title: Aggiungere i collegamenti ipertestuali (URL) a una tabella o una matrice
description: Questo argomento illustra come aggiungere i collegamenti ipertestuali (URL) a una tabella. Per aggiungere i collegamenti ipertestuali (URL) a un set di dati, usare Power BI Desktop. Con Power BI Desktop o il servizio Power BI è quindi possibile aggiungere tali collegamenti ipertestuali alle tabelle e alle matrici dei report.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: ddb54ca91936626b4870b51b86b7fc7f0ac6b2c9
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "75954149"
---
# <a name="add-hyperlinks-urls-to-a-table-or-matrix"></a>Aggiungere i collegamenti ipertestuali (URL) a una tabella o una matrice
Questo argomento illustra come aggiungere i collegamenti ipertestuali (URL) a una tabella. Per aggiungere i collegamenti ipertestuali (URL) a un set di dati, usare Power BI Desktop. Con Power BI Desktop o il servizio Power BI è possibile aggiungere tali collegamenti ipertestuali alle tabelle e alle matrici dei report. È poi possibile visualizzare l'URL o un'icona del collegamento oppure formattare un'altra colonna come testo del collegamento.

![Tabella con collegamenti ipertestuali](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

Con il servizio Power BI e Power BI Desktop è anche possibile creare i collegamenti ipertestuali nelle [caselle di testo dei report](service-add-hyperlink-to-text-box.md). Nel servizio Power BI è possibile aggiungere i collegamenti ipertestuali ai [riquadri nei dashboard](service-dashboard-edit-tile.md) e alle [caselle di testo nei dashboard](service-dashboard-add-widget.md). 


## <a name="format-a-url-as-a-hyperlink-in-power-bi-desktop"></a>Formattare un URL come collegamento ipertestuale in Power BI Desktop

È possibile formattare un campo con URL come collegamenti ipertestuali in Power BI Desktop ma non nel servizio Power BI. I [collegamenti ipertestuali possono essere formattati in Power Pivot per Excel](#create-a-table-or-matrix-hyperlink-in-excel-power-pivot) anche prima di importare la cartella di lavoro in Power BI.

1. Se non esiste già un campo con un collegamento ipertestuale nel set di dati, aggiungerlo come [colonna personalizzata](desktop-common-query-tasks.md) in Power BI Desktop.

    > [!NOTE]
    > Non è possibile creare una colonna in modalità DirectQuery.  Se tuttavia i dati contengono già gli URL, è possibile attivarli nei collegamenti ipertestuali.

2. In Vista dati selezionare la colonna. 

3. Nella scheda **Creazione di modelli** selezionare **Categoria di dati** > **URL Web**.
   
    ![Elenco a discesa Categoria dati](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url.png)

    > [!NOTE]
    > Gli URL devono iniziare con determinati prefissi. Per l'elenco completo, vedere [Considerazioni e risoluzione dei problemi](#considerations-and-troubleshooting) in questo articolo.

## <a name="create-a-table-or-matrix-with-a-hyperlink"></a>Creare una tabella o una matrice con un collegamento ipertestuale

1. Dopo aver [formattato un collegamento ipertestuale come URL](#format-a-url-as-a-hyperlink-in-power-bi-desktop), passare alla vista Report.
2. Creare una tabella o una matrice con il campo categorizzato come URL Web. I collegamenti ipertestuali sono di colore blu e sottolineati.

    ![Collegamenti di colore blu e sottolineati](media/power-bi-hyperlinks-in-tables/power-bi-url-blue-underline.png)


## <a name="display-a-hyperlink-icon-instead-of-a-url"></a>Visualizzare un'icona del collegamento ipertestuale anziché un URL

Se non si vuole visualizzare un URL lungo in una tabella, è possibile visualizzare un'icona di collegamento ipertestuale ![Icona di collegamento ipertestuale](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) . 

> [!NOTE]
> Non è possibile visualizzare le icone in una matrice.
   
1. Prima di tutto [creare una tabella con un collegamento ipertestuale](#create-a-table-or-matrix-with-a-hyperlink).

2. Selezionare la tabella per attivarla.

    Selezionare l'icona **Formato** ![icona del rullo](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) per aprire la scheda Formattazione.

    Espandere **Valori**, trovare **Icona URL** e **attivarla**.

    ![Attivare l'icona URL](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Facoltativo) [Pubblicare il report](desktop-upload-desktop-files.md) da Power BI Desktop nel servizio Power BI. Quando si apre il report nel servizio Power BI, i collegamenti ipertestuali funzioneranno anche in questo caso.

## <a name="format-link-text-as-a-hyperlink"></a>Formattare il testo del collegamento come collegamento ipertestuale

È anche possibile formattare un altro campo di una tabella come collegamento ipertestuale e non un'intera colonna come URL. In questo caso la colonna non viene formattata come URL Web.

> [!NOTE]
> Non è possibile formattare un altro campo come collegamento ipertestuale in una matrice.

1. Se un campo con un collegamento ipertestuale non esiste già nel set di dati, aggiungerlo come [colonna personalizzata](desktop-common-query-tasks.md) in Power BI Desktop. Anche in questo caso non è possibile creare una colonna in modalità DirectQuery.  Se tuttavia i dati contengono già gli URL, è possibile attivarli nei collegamenti ipertestuali.

2. Nella vista Report creare una tabella o una matrice con la colonna che si vuole formattare come testo del collegamento.

3. Dopo aver selezionato la tabella, selezionare l'icona **Formato** ![icona del rullo](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) per aprire la scheda Formattazione.

4. Espandere **Formattazione condizionale** assicurandosi che il nome nella casella corrisponda alla colonna che si vuole come testo del collegamento. Trovare **Icona URL** e **attivarla**.

    ![URL Web della formattazione condizionale](media/power-bi-hyperlinks-in-tables/power-bi-format-conditional-web-url.png)

5. Nella finestra di dialogo **URL Web** selezionare il campo che contiene l'URL nella casella **In base al campo** > **OK**.

    ![Finestra di dialogo URL Web](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url-dialog.png)

    A questo punto il testo nella colonna viene formattato come collegamento.

    ![Testo formattato come collegamento ipertestuale](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

1. (Facoltativo) [Pubblicare il report](desktop-upload-desktop-files.md) da Power BI Desktop nel servizio Power BI. Quando si apre il report nel servizio Power BI, i collegamenti ipertestuali funzioneranno anche in questo caso.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Creare un collegamento ipertestuale alla tabella o alla matrice in Excel Power Pivot

Un altro modo per aggiungere collegamenti ipertestuali alle tabelle e matrici di Power BI consiste nel creare i collegamenti ipertestuali nel set di dati prima di importare o connettersi a tale set di dati da Power BI. Questo esempio usa una cartella di lavoro di Excel.

1. Aprire la cartella di lavoro in Excel.
2. Selezionare la scheda **PowerPivot** e quindi scegliere **Gestisci**.
   
   ![Aprire PowerPivot in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Quando PowerPivot viene aperto, selezionare la scheda **Avanzate**.
   
   ![Scheda Avanzate di PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Posizionare il cursore nella colonna che contiene gli URL da trasformare in collegamenti ipertestuali nelle tabelle di Power BI.
   
   > [!NOTE]
   > Gli URL devono iniziare con determinati prefissi. Per l'elenco completo, vedere [Considerazioni e risoluzione dei problemi](#considerations-and-troubleshooting).
   > 
   
5. Nel gruppo **Proprietà report** selezionare l'elenco a discesa **Categoria di dati** e scegliere **URL Web**. 
   
   ![Elenco a discesa Categoria di dati in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Dal servizio Power BI o da Power BI Desktop connettersi a questa cartella di lavoro o importarla.
7. Creare una visualizzazione tabella che includa il campo URL.
   
   ![Creare una tabella in Power BI con il campo URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Considerazioni e risoluzione dei problemi

Gli URL devono iniziare con uno degli elementi seguenti:
- http
- https
- -mailto
- file
- ftp
- news
- telnet

D: è possibile usare un URL personalizzato come collegamento ipertestuale in una tabella o matrice?    
R: No. È possibile usare un'icona di collegamento. Se è necessario testo personalizzato per i collegamenti ipertestuali e l'elenco di URL è breve, valutare la possibilità di usare una casella di testo.


## <a name="next-steps"></a>Passaggi successivi
[Visualizzazioni nei report di Power BI](visuals/power-bi-report-visualizations.md)

[Concetti di base del servizio Power BI](service-basic-concepts.md)

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)

