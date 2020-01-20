---
title: Pubblicare un report impaginato nel servizio Power BI
description: Questa esercitazione illustra come pubblicare un report impaginato nel servizio Power BI caricandolo dal computer locale.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: 5f77e17eccf4c99e7a391ea310a34848c604e01d
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75732085"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Pubblicare un report impaginato nel servizio Power BI

Questo articolo illustra come pubblicare un report impaginato nel servizio Power BI caricandolo dal computer locale. È possibile caricare report impaginati nell'Area di lavoro personale o in qualsiasi altra area di lavoro se l'area di lavoro è assegnata a una capacità Premium. Cercare l'icona a forma di diamante ![Icona a forma di diamante della capacità di Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) accanto al nome dell'area di lavoro. 

Se l'origine dati del report è in locale, è necessario creare un gateway dopo aver caricato il report. Vedere la sezione [Creare un gateway](#create-a-gateway) più avanti in questo articolo.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Aggiungere un'area di lavoro a una capacità Premium

Se accanto al nome dell'area di lavoro non è presente l'icona a forma di diamante ![Icona a forma di diamante della capacità di Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) , è necessario aggiungere l'area di lavoro a una capacità Premium. 

1. Selezionare **Aree di lavoro**, selezionare i puntini di sospensione ( **...** ) accanto al nome dell'area di lavoro e quindi scegliere **Modifica area di lavoro**.

    ![Selezionare Modifica area di lavoro](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Nella finestra di dialogo **Modifica area di lavoro** espandere **Avanzate** e quindi far scorrere **Capacità dedicata** su **On**.

    ![Selezionare Capacità dedicata](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   È possibile che questa impostazione non sia modificabile. In questo caso, contattare l'amministratore delle capacità di Power BI Premium per ottenere i diritti di assegnazione necessari per poter aggiungere l'area di lavoro a una capacità Premium.

## <a name="from-report-builder-publish-a-paginated-report"></a>Pubblicare un report impaginato da Report Builder

1. Creare un report impaginato in Generatore Report e salvarlo nel computer locale.

1. Dal menu **File** di Report Builder scegliere **Salva con nome**.

    ![Menu File > Salva > Salva con nome](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Se non è ancora stato eseguito l'accesso a Power BI, eseguirlo ora oppure creare un account. Nell'angolo in alto a destra di Report Builder selezionare **Accedi** e completare i passaggi.

2. Nell'elenco delle aree di lavoro a sinistra selezionare un'area di lavoro con l'icona a forma di diamante ![Icona a forma di diamante della capacità Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) accanto al nome. Digitare un nome nella casella **Nome file** > **Salva**. 

    ![Selezionare un'area di lavoro Premium](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Aprire il servizio Power BI in un browser e passare all'area di lavoro Premium in cui è stato pubblicato il report impaginato. Il report verrà visualizzato nella scheda **Report**.

    ![Report impaginato nell'elenco dei report](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Selezionare il report impaginato per aprirlo nel servizio Power BI. Se nel report sono presenti parametri, è necessario selezionarli prima di poter visualizzare il report.

    ![Selezionare i parametri](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Se l'origine dati del report è locale, leggere le informazioni nella sezione [Creare un gateway](#create-a-gateway) in questo articolo per accedere all'origine dati.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Caricare un report impaginato dal servizio Power BI

È anche possibile partire dal servizio Power BI e caricare un report impaginato.

1. Creare un report impaginato in Generatore Report e salvarlo nel computer locale.

1. Aprire il servizio Power BI in un browser e passare all'area di lavoro Premium in cui si vuole pubblicare il report. Osservare l'icona a forma di diamante ![Icona a forma di diamante della capacità di Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) accanto al nome. 

1. Selezionare **Recupera dati**.

    ![Recuperare dati in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Nella casella **File** selezionare **Recupera**.

    ![Recuperare file in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Selezionare **File locale** > passare al report impaginato > **Apri**.

    ![Selezionare File locale](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Selezionare **Continua** > **Modifica credenziali**.

    ![Selezionare Modifica credenziali](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configurare le credenziali > **Accedi**.

    ![Modifica credenziali](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Il report verrà visualizzato nella scheda **Report**.

    ![Report impaginato nell'elenco dei report](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selezionarlo per aprirlo nel servizio Power BI. Se nel report sono presenti parametri, è necessario selezionarli prima di poter visualizzare il report.
 
    ![Selezionare i parametri](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Se l'origine dati del report è locale, leggere le informazioni nella sezione [Creare un gateway](#create-a-gateway) in questo articolo per accedere all'origine dati.

## <a name="create-a-gateway"></a>Creare un gateway

Come qualsiasi altro report di Power BI, se l'origine dati del report è in locale, è necessario creare o connettersi a un gateway per accedere ai dati.

1. Accanto al nome del report selezionare **Gestisci**.

   ![Gestire il report impaginato](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Per informazioni dettagliate e i passaggi successivi, vedere l'articolo sul servizio Power BI [Informazioni sul gateway dati locale](service-gateway-onprem.md).

### <a name="gateway-limitations"></a>Limitazioni dei gateway

Attualmente i gateway non supportano parametri multivalore.


## <a name="next-steps"></a>Passaggi successivi

- [Visualizzare un report impaginato nel servizio Power BI](consumer/paginated-reports-view-power-bi-service.md)
- [Che cosa sono i report impaginati in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Esercitazione: Incorporare report impaginati di Power BI in un'applicazione per i clienti](developer/embed-paginated-reports-customers.md)

