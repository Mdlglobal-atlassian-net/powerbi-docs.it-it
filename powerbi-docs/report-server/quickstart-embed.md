---
title: Incorporare un report usando un iFrame
description: Incorporamento di report di Server di report di Power BI in un iFrame in SharePoint Server
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.component: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 802107ce9c12075ffc51461375ca3e9a313f2be1
ms.sourcegitcommit: 9c3a9ec14c111d766ef5703366c316e72f6e588f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558425"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Guida rapida: Incorporare un report di Server di report di Power BI in SharePoint Server usando un iFrame

Questa guida introduttiva illustra come incorporare un report di Server di report di Power BI in una pagina di SharePoint usando un iFrame. Se si usa SharePoint Online, Server di report di Power BI deve essere accessibile pubblicamente. In SharePoint Online, la web part Power BI che funziona con il servizio Power BI non funziona con Server di report di Power BI. 

![Esempio di iFrame](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Prerequisiti
* È necessario aver installato e configurato [Server di report di Power BI](https://powerbi.microsoft.com/en-us/report-server/).
* È necessario aver installato [Power BI Desktop ottimizzato per Server di report di Power BI](install-powerbi-desktop.md).
* È necessario disporre di un ambiente [SharePoint](https://docs.microsoft.com/sharepoint/install/install) installato e configurato.

## <a name="creating-the-power-bi-report-server-report-url"></a>Creazione dell'URL del report di Server di report di Power BI

1. Scaricare l'esempio [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) da GitHub.

    ![Scaricare il file PBIX di esempio](media/quickstart-embed/quickstart_embed_14.png)

2. Aprire il file PBIX di esempio da GitHub in **Power BI Desktop ottimizzato per Server di report di Power BI**.

    ![File PBI in Power BI Desktop](media/quickstart-embed/quickstart_embed_02.png)

3. Salvare il file in **Server di report di Power BI**. 

    ![Salvataggio in Server di report di Power BI](media/quickstart-embed/quickstart_embed_03.png)

4. Visualizzare il report nel **portale Web**.

    ![Portale Web](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>Acquisizione del parametro URL

Dopo aver creato l'URL, è possibile creare un iFrame all'interno di una pagina di SharePoint che ospiti il report. Per qualsiasi report di Server di report di Power BI, è possibile aggiungere all'URL un parametro della stringa di query `?rs:embed=true` per incorporare il report in un iFrame. 

   ad esempio:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Incorporamento di un report di Server di report di Power BI in un iFrame di SharePoint

1. Passare a una pagina **Contenuto del sito** di SharePoint.

    ![Pagina Contenuto del sito](media/quickstart-embed/quickstart_embed_05.png)

2. Scegliere la pagina in cui si vuole aggiungere il report.

    ![App della pagina Contenuto del sito](media/quickstart-embed/quickstart_embed_06.png)

3. Selezionare l'icona dell'ingranaggio in alto a destra e selezionare **Modifica pagina**.

    ![Opzione Modifica pagina](media/quickstart-embed/quickstart_embed_07.png)

4. Selezionare **Aggiungi web part**.

    ![Aggiungi web part](media/quickstart-embed/quickstart_embed_08.png)

5. In **Categorie** selezionare **Elementi multimediali e contenuto**, in **Parti** selezionare **Editor contenuto**, quindi selezionare **Aggiungi** .

    ![Selezionare la Web part Editor contenuto](media/quickstart-embed/quickstart_embed_09.png) ![Selezionare Aggiungi](media/quickstart-embed/quickstart_embed_091.png)

6. Selezionare **Fare clic qui per aggiungere nuovo contenuto**.

    ![Aggiunta di nuovo contenuto](media/quickstart-embed/quickstart_embed_10.png)

7. Nella barra multifunzione selezionare la scheda **Formato testo** e quindi selezionare **Modifica origine**.

     ![Modifica origine](media/quickstart-embed/quickstart_embed_11.png)

8. Nella finestra Modifica origine incollare il codice iFrame e selezionare OK.

    ![Codice iFrame](media/quickstart-embed/quickstart_embed_12.png)

     ad esempio:
     ```
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Nella barra multifunzione selezionare la scheda **Pagina** e selezionare **Interrompi modifica**.

    ![Interrompi modifica](media/quickstart-embed/quickstart_embed_13.png)

10. Il report dovrebbe essere visualizzato nella pagina.

    ![Esempio di iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Passaggi successivi

[Avvio rapido: Creare un report di Power BI per il server di report di Power BI](quickstart-create-powerbi-report.md)  
[Guida rapida: creare un report impaginato per il server di report di Power BI](quickstart-create-paginated-report.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/) 