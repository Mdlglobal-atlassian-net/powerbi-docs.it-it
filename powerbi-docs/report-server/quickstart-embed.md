---
title: Incorporare un report di Server di report di Power BI in SharePoint Server usando un iFrame
description: Questo articolo mostra come incorporare un report di Server di report di Power BI in un iFrame in SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 4e7616ec3ce6552130848bc0508bf8b9ac8ac965
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762601"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Incorporare un report di Server di report di Power BI in SharePoint Server usando un iFrame

Questo articolo illustra come incorporare un report di Server di report di Power BI in una pagina di SharePoint usando un iFrame. Se si usa SharePoint Online, Server di report di Power BI deve essere accessibile pubblicamente. In SharePoint Online, la Web part Power BI che funziona con il servizio Power BI non funziona con Server di report di Power BI.  

![Esempio di iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Prerequisiti
* [Server di report di Power BI](https://powerbi.microsoft.com/report-server/) installato e configurato.
* [Power BI Desktop ottimizzato per Server di report di Power BI](install-powerbi-desktop.md) installato.
* Ambiente [SharePoint](https://docs.microsoft.com/sharepoint/install/install) installato e configurato.
* Internet Explorer 11 è supportato solo se la modalità documento è impostata sulla modalità IE11 (Edge) o se si usa SharePoint Online. È possibile usare altri browser supportati con SharePoint locale e SharePoint Online.

## <a name="create-the-power-bi-report-url"></a>Creare l'URL del report Power BI

1. Scaricare l'esempio da GitHub: [Demo del blog](https://github.com/Microsoft/powerbi-desktop-samples). Selezionare **Clone or download** (Clona o scarica) e quindi **Download ZIP** (Scarica ZIP).

    ![Scaricare il file PBIX di esempio](media/quickstart-embed/quickstart_embed_14.png)

2. Decomprimere il file, aprire il file di esempio con estensione pbix in Power BI Desktop ottimizzato per Server di report di Power BI.

    ![File PBI in Power BI Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Salvare il file in **Server di report di Power BI**. 

    ![Salvataggio in Server di report di Power BI](media/quickstart-embed/quickstart_embed_03.png)

4. Visualizzare il report nel portale Web di Server di report di Power BI.

    ![Portale Web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Acquisire il parametro URL

Dopo aver acquisito l'URL, è possibile creare un iFrame all'interno di una pagina di SharePoint per ospitare il report. Per qualsiasi URL di report di Server di report di Power BI, aggiungere il parametro della stringa di query seguente per incorporare il report in un iFrame di SharePoint: `?rs:embed=true`.

   ad esempio:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Incorporare il report in un iFrame di SharePoint

1. Passare a una pagina **Contenuto del sito** di SharePoint.

    ![Pagina Contenuto del sito](media/quickstart-embed/quickstart_embed_05.png)

2. Scegliere la pagina in cui si vuole aggiungere il report.

    ![App nella pagina Contenuto del sito](media/quickstart-embed/quickstart_embed_06.png)

3. Selezionare l'icona dell'ingranaggio in alto a destra e quindi selezionare **Modifica pagina**.

    ![Opzione Modifica pagina](media/quickstart-embed/quickstart_embed_07.png)

4. Selezionare **Aggiungi web part**.

5. In **Categorie** selezionare **Elementi multimediali e contenuto**. In **Parti** selezionare **Editor contenuto** e quindi **Aggiungi**.

    ![Selezionare la Web part Editor contenuto](media/quickstart-embed/quickstart_embed_09.png)

6. Selezionare **Fare clic qui per aggiungere nuovo contenuto**.

7. Dal menu in alto selezionare **Formatta testo** e quindi **Modifica origine**.

     ![Modifica origine](media/quickstart-embed/quickstart_embed_11.png)

8. Nella finestra **Modifica origine** incollare il codice iFrame in **HTML** e quindi selezionare **OK**.

    ![Codice iFrame](media/quickstart-embed/quickstart_embed_12.png)

     ad esempio:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Dal menu in alto selezionare **Pagina** e quindi **Interrompi modifica**.

    ![Interrompi modifica](media/quickstart-embed/quickstart_embed_13.png)

    Il report viene visualizzato nella pagina.

    ![Esempio di iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Passaggi successivi

- [Creare un report di Power BI per Server di report di Power BI](quickstart-create-powerbi-report.md).  
- [Creare un report impaginato per Server di report di Power BI](quickstart-create-paginated-report.md).  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/). 
