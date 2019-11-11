---
title: Creare report basati su set di dati di aree di lavoro diverse (anteprima) - Power BI
description: Di seguito viene descritto come è possibile condividere un set di dati con utenti in tutta l'organizzazione, che possono poi compilare report basati sul set di dati nelle proprie aree di lavoro.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 371507eb86e1b68225e9d66ee3a1363b0e163d4f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877183"
---
# <a name="create-reports-based-on-datasets-from-different-workspaces-preview"></a>Creare report basati su set di dati di aree di lavoro diverse (anteprima)

Di seguito viene descritto come è possibile creare report nelle proprie aree di lavoro basati su set di dati di aree di lavoro diverse. Per compilare un report basato su un set di dati esistente, è possibile iniziare da Power BI Desktop oppure dal servizio Power BI, nell'area di lavoro personale o in un [nuova esperienza delle aree di lavoro](service-create-the-new-workspaces.md).

- Nel servizio Power BI: **Recupera dati** > **Set di dati pubblicati**.
- In Power BI Desktop: **Recupera dati** > **Set di dati Power BI**.

    ![Connettersi a un set di dati esistente](media/service-datasets-across-workspaces/power-bi-connect-dataset-pk.png)
   
In entrambi i casi l'esperienza di individuazione del set di dati inizia nella finestra di dialogo **Seleziona un set di dati per creare un report**. Saranno visualizzati tutti i set di dati a cui si ha accesso, indipendentemente dalla posizione in cui si trovano:

![Selezionare un set di dati](media/service-datasets-across-workspaces/power-bi-select-dataset.png)

Si noti che il primo set ha l'etichetta **Innalzata**. Questo argomento sarà trattato più avanti nella sezione [Trovare un set di dati approvato](#find-an-endorsed-dataset) in questo articolo.

I set di dati visualizzati in questo elenco soddisfano almeno una delle condizioni seguenti:

- Il set di dati si trova in una delle aree di lavoro della nuova esperienza e l'utente è membro di tale area di lavoro. Vedere [Considerazioni e limitazioni](service-datasets-across-workspaces.md#considerations-and-limitations).
- Si dispone dell'autorizzazione di compilazione per il set di dati che si trova in un'area di lavoro della nuova esperienza.
- Il set di dati si trova nell'area di lavoro personale.

> [!NOTE]
> Gli utenti del piano gratuito possono visualizzare solo i set di dati dell'area di lavoro personale o i set di dati che si trovano nelle aree di lavoro con capacità Premium per i quali hanno l'autorizzazione di compilazione.

Quando si fa clic su **Crea**, si crea una connessione dinamica al set di dati. L'esperienza di creazione report si apre con l'intero set di dati disponibile. In questo modo non è stata creata una copia del set di dati. Il set di dati rimane nel rispettivo percorso originale. È possibile usare tutte le tabelle e le misure del set di dati per compilare report personalizzati. Le restrizioni di sicurezza a livello di riga nel set di dati sono attive, pertanto è possibile visualizzare solo i dati per cui si dispone di autorizzazioni in base al ruolo nella sicurezza a livello di riga.

È possibile salvare il report nell'area di lavoro corrente nel servizio Power BI oppure pubblicare il report in un'area di lavoro da Power BI Desktop. Power BI crea automaticamente una voce nell'elenco dei set di dati, se il report si basa su un set di dati esterno all'area di lavoro. L'icona per questo tipo di set di dati è diversa dall'icona per i set di dati che si trovano nell'area di lavoro: ![Icona Set di dati condiviso](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)

In questo modo, i membri dell'area di lavoro possono indicare quali report e dashboard usano i set di dati esterni all'area di lavoro. Questa voce offre informazioni sul set di dati e alcune azioni di selezione.

![Azioni del set di dati](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="find-an-endorsed-dataset"></a>Trovare un set di dati approvato

Esistono due tipi diversi di set di dati approvati. I proprietari di set di dati possono *promuovere* un set di dati consigliato. Gli amministratori tenant di Power BI possono anche designare esperti nell'organizzazione per *certificare* i set di dati che tutti possono usare. Sia i set di dati promossi sia quelli certificati visualizzano *notifiche* che vengono visualizzate durante la ricerca di un set di dati e nell'elenco dei set di dati in un'area di lavoro. Il nome della persona che certifica un set di dati viene visualizzato in una descrizione comando durante l'esperienza di individuazione di set di dati. Per visualizzarlo è sufficiente passare il mouse sull'etichetta **Certificato**.

- Nel servizio Power BI: **Recupera dati** > **Set di dati pubblicati**.
- In Power BI Desktop: **Recupera dati** > **Set di dati Power BI**.

    Nella finestra di dialogo **Seleziona un set di dati**, i set di dati approvati sono i primi visualizzati nell'elenco per impostazione predefinita. 

    ![Set di dati promosso](media/service-datasets-certify-promote/power-bi-dataset-promoted.png)

## <a name="next-steps"></a>Passaggi successivi

- [Usare set di dati in aree di lavoro diverse (anteprima)](service-datasets-across-workspaces.md)
- Domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)
