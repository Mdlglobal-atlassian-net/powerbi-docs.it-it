---
title: Copiare report da altre aree di lavoro (anteprima) - Power BI
description: Di seguito viene descritto come è possibile condividere un set di dati con utenti in tutta l'organizzazione, che possono poi compilare report basati sul set di dati nelle proprie aree di lavoro.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461466"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copiare report da altre aree di lavoro (anteprima)

Di seguito viene descritto come copiare un report da un'area di lavoro e salvarlo in un'area di lavoro diversa. È poi possibile modificare tale report, aggiungendo o eliminando oggetti visivi e altri elementi.

Quando si individua un report interessante, che si trovi in un'area di lavoro oppure in un'app, è possibile crearne una copia e modificarlo in base alle esigenze. Non è necessario creare il modello di dati, perché è già stato creato. È molto più semplice modificare un report esistente anziché crearlo da zero.

## <a name="save-a-copy-of-a-report"></a>Salvare una copia di un report

1. Passare alla visualizzazione elenco Report in un'app o in un'area di lavoro.

1. In **Azioni** selezionare **Salva una copia**.

    ![Salvare una copia di un report](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    L'icona **Salva una copia** viene visualizzata solo se il report si trova nell'area di lavoro della nuova esperienza e l'utente ha le [autorizzazioni di compilazione](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Anche se si ha accesso all'area di lavoro, è necessario avere le autorizzazioni di compilazione per il set di dati.

3. In **Salva una copia di questo report** assegnare un nome al report e selezionare l'area di lavoro di destinazione.

    ![Finestra di dialogo Salva una copia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    È possibile salvare il report nell'area di lavoro corrente o in un'area di lavoro diversa nel servizio Power BI. È possibile visualizzare solo le aree di lavoro della nuova esperienza, di cui si è membri.
  
4. Selezionare **Salva**.

    Quando si salva una copia del report, si crea una connessione dinamica al set di dati. Si può aprire l'esperienza di creazione di report con l'intero set di dati disponibile. In questo modo non è stata creata una copia del set di dati. Il set di dati rimane nel rispettivo percorso originale. È possibile usare tutte le tabelle e le misure del set di dati nel report personalizzato. Le restrizioni di sicurezza a livello di riga nel set di dati sono attive, pertanto è possibile visualizzare solo i dati per cui si dispone di autorizzazioni in base al ruolo nella sicurezza a livello di riga.

    Power BI crea automaticamente una voce nell'elenco dei set di dati, se il report si basa su un set di dati esterno all'area di lavoro. L'icona per questo tipo di set di dati è diversa dall'icona per i set di dati che si trovano nell'area di lavoro: ![Icona Set di dati condiviso](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    In questo modo, i membri dell'area di lavoro possono indicare quali report e dashboard usano i set di dati esterni all'area di lavoro. Questa voce offre informazioni sul set di dati e alcune azioni di selezione.

    ![Azioni del set di dati](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Visualizzare i set di dati correlati

Quando un report si trova in un'area di lavoro, si potrebbe volere sapere su quale set di dati si basa.

1. Nella visualizzazione elenco Report selezionare **Visualizza elementi correlati**.

    ![Icona Visualizza elementi correlati](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. Nella finestra di dialogo **Contenuto correlato** vengono visualizzati tutti gli elementi correlati. In questo elenco il set di dati è uguale a tutti gli altri. Non è possibile stabilire se si trova in un'area di lavoro diversa. Si tratta di un problema noto.
 
    ![Finestra di dialogo Contenuto correlato](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Passaggi successivi

- [Usare set di dati in aree di lavoro diverse (anteprima)](service-datasets-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)
