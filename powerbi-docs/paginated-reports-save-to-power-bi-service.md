---
title: Pubblicare un report impaginato nel servizio Power BI
description: Questa esercitazione illustra come pubblicare un report impaginato nel servizio Power BI caricandolo dal computer locale.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: a7f0e6f08f25d47cd50789a3c8f296ae20c4cab0
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831207"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Pubblicare un report impaginato nel servizio Power BI

Questo articolo illustra come pubblicare un report impaginato nel servizio Power BI caricandolo dal computer locale. È possibile caricare report impaginati nell'Area di lavoro personale o in qualsiasi altra area di lavoro se l'area di lavoro è assegnata a una capacità Premium. Cercare l'icona a forma di diamante ![Icona a forma di diamante della capacità di Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) accanto al nome dell'area di lavoro. 

Se l'origine dati del report è in locale, sarà necessario [creare un gateway](#create-a-gateway) dopo aver caricato il report.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Aggiungere un'area di lavoro a una capacità Premium

Se accanto al nome dell'area di lavoro non è presente l'icona a forma di diamante ![Icona a forma di diamante della capacità di Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) , è necessario aggiungere l'area di lavoro a una capacità Premium. 

1. Selezionare **Aree di lavoro**, selezionare i puntini di sospensione ( **...** ) accanto al nome dell'area di lavoro e quindi scegliere **Modifica area di lavoro**.

    ![Selezionare Modifica area di lavoro](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Nella finestra di dialogo **Modifica area di lavoro** espandere **Avanzate** e quindi far scorrere **Capacità dedicata** su **On**.

    ![Selezionare Capacità dedicata](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   È possibile che questa impostazione non sia modificabile. In questo caso, contattare l'amministratore delle capacità di Power BI Premium per ottenere i diritti di assegnazione necessari per poter aggiungere l'area di lavoro a una capacità Premium.


## <a name="upload-a-paginated-report"></a>Caricare un report impaginato

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

   Il report è ora visibile nell'elenco di report.

    ![Report impaginato nell'elenco dei report](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selezionarlo per aprirlo nel servizio Power BI. Se nel report sono presenti parametri, è necessario selezionarli prima di poter visualizzare il report.
 
    ![Selezionare i parametri](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

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

