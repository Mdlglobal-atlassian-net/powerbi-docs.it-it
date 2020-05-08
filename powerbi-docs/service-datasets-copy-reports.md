---
title: Copiare report da altre app o aree di lavoro (anteprima) - Power BI
description: Informazioni su come creare una copia di un report e salvarla nella propria area di lavoro.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/16/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 8716a304e5b117c027d75db149ebcc8d95efebfe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "76268931"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copiare report da altre aree di lavoro (anteprima)

Quando si trova un report interessante in un'area di lavoro oppure in un'app, è possibile crearne una copia e salvarlo in un'area di lavoro diversa. È poi possibile modificare la copia del report, aggiungendo o eliminando oggetti visivi e altri elementi. Non è necessario creare il modello di dati, perché è già stato creato. È molto più semplice modificare un report esistente anziché crearlo da zero. Tuttavia, quando si crea un'app dall'area di lavoro, a volte non è possibile pubblicare la copia del report nell'app. Per informazioni dettagliate, vedere [Considerazioni e limitazioni nell'articolo "Usare set di dati in aree di lavoro diverse"](service-datasets-across-workspaces.md#considerations-and-limitations).

> [!NOTE]
> Per creare una copia, è necessaria una licenza Pro, anche se il report originale si trova in un'area di lavoro in una capacità Premium.

## <a name="save-a-copy-of-a-report-in-a-workspace"></a>Salvare una copia di un report in un'area di lavoro

1. In un'area di lavoro passare alla visualizzazione elenco Report.

    ![Visualizzazione elenco Report](media/service-datasets-copy-reports/power-bi-report-list-view.png)

1. In **Azioni** selezionare **Salva una copia**.

    ![Salvare una copia di un report](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    L'icona **Salva una copia** viene visualizzata solo se il report si trova in un'area di lavoro della nuova esperienza e l'utente ha l'[autorizzazione per creazione report](service-datasets-build-permissions.md). Anche se si ha accesso all'area di lavoro, è necessario avere l'autorizzazione per creazione report per il set di dati.

3. In **Salva una copia di questo report** assegnare un nome al report e selezionare l'area di lavoro di destinazione.

    ![Finestra di dialogo Salva una copia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    È possibile salvare il report nell'area di lavoro corrente o in un'area di lavoro diversa nel servizio Power BI. È possibile visualizzare solo le aree di lavoro della nuova esperienza, di cui si è membri. 
  
4. Selezionare **Salva**.

    Power BI crea automaticamente una copia del report e una voce nell'elenco dei set di dati se il report è basato su un set di dati esterno all'area di lavoro. L'icona per questo tipo di set di dati è diversa dall'icona per i set di dati che si trovano nell'area di lavoro: ![Icona Set di dati condiviso](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)
    
    In questo modo, i membri dell'area di lavoro possono indicare quali report e dashboard usano i set di dati esterni all'area di lavoro. Questa voce offre informazioni sul set di dati e alcune azioni di selezione.

    ![Azioni del set di dati](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

    Per altre informazioni sul report e sul set di dati correlato, vedere [Copia del report](#your-copy-of-the-report) in questo articolo.

## <a name="copy-a-report-in-an-app"></a>Copiare un report in un'app

1. In un'app aprire il report che si vuole copiare.
2. Nella barra dei menu selezionare **Altre opzioni** ( **...** ) > **Salva una copia**.

    ![Salvare una copia del report](media/service-datasets-copy-reports/power-bi-save-copy.png)

    L'opzione **Salva una copia** viene visualizzata solo se il report si trova in un'area di lavoro della nuova esperienza e si ha l'[autorizzazione per la creazione](service-datasets-build-permissions.md).

3. Assegnare un nome al report e fare clic su **Salva**.

    ![Assegnare un nome alla copia del report](media/service-datasets-copy-reports/power-bi-save-report-from-app.png)

    La copia viene salvata automaticamente nell'area di lavoro personale.

4. Selezionare **Vai al report** per aprire la copia.

## <a name="your-copy-of-the-report"></a>Copia del report

Quando si salva una copia del report, si crea una connessione dinamica al set di dati. Si può aprire l'esperienza di creazione di report con l'intero set di dati disponibile. 

![Modificare la copia del report](media/service-datasets-copy-reports/power-bi-edit-report-copy.png)

In questo modo non è stata creata una copia del set di dati. Il set di dati rimane nel rispettivo percorso originale. È possibile usare tutte le tabelle e le misure del set di dati nel report personalizzato. Le restrizioni di sicurezza a livello di riga nel set di dati sono attive, pertanto è possibile visualizzare solo i dati per cui si dispone di autorizzazioni in base al ruolo nella sicurezza a livello di riga.

## <a name="view-related-datasets"></a>Visualizzare i set di dati correlati

Quando si usa un report in un'area di lavoro e il report è basato su un set di dati in un'altra area di lavoro, potrebbe essere necessario avere altre informazioni sul set di dati su cui è basato.

1. Nella visualizzazione elenco Report selezionare **Visualizza elementi correlati**.

    ![Icona Visualizza elementi correlati](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. Nella finestra di dialogo **Contenuto correlato** vengono visualizzati tutti gli elementi correlati. In questo elenco il set di dati è uguale a tutti gli altri. Non è possibile stabilire se si trova in un'area di lavoro diversa. Si tratta di un problema noto.
 
    ![Finestra di dialogo Contenuto correlato](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>Eliminare un report e il relativo set di dati condiviso

Si potrebbe decidere che il report e il set di dati condiviso associato nell'area di lavoro non sono più necessari.

1. Eliminare il report. Nell'elenco dei report nell'area di lavoro selezionare l'icona **Elimina**.

    ![Icona per eliminare il report](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. Nell'elenco dei set di dati si può notare che l'icona **Elimina** non è disponibile per i set di dati condivisi. Aggiornare la pagina o passare a una pagina diversa e tornare. Il set di dati non sarà più incluso nell'elenco. In caso contrario, selezionare **Visualizza elementi correlati**. Potrebbe essere correlato a un'altra tabella nell'area di lavoro.

    ![Icona Visualizza elementi correlati](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > L'eliminazione del set di dati condiviso in questa area di lavoro non elimina il set di dati, ma elimina solo il riferimento a esso.


## <a name="next-steps"></a>Passaggi successivi

- [Usare set di dati in aree di lavoro diverse (anteprima)](service-datasets-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
