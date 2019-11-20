---
title: Gestire l'archiviazione dei dati nelle aree di lavoro
description: Informazioni su come è possibile gestire l'archiviazione dei dati nell'area di lavoro personale o in un'area di lavoro per assicurarsi che sia possibile continuare a pubblicare report e set di dati.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: f8e7240b34e20a3d18443cadb5265c5d0d870790
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873653"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gestire l'archiviazione dei dati nelle aree di lavoro di Power BI

Informazioni su come è possibile gestire l'archiviazione dei dati nell'area di lavoro personale o in un'area di lavoro per assicurarsi che sia possibile continuare a pubblicare report e set di dati.

Per gli utenti e le aree di lavoro esistono capacità di dati specifiche:

* A tutti gli utenti viene assegnato uno spazio di archiviazione dati massimo di 10 GB.
* Gli utenti con licenza di Power BI Pro possono creare aree di lavoro con al massimo 10 GB di spazio di archiviazione dati ognuna.
* Un'area di lavoro in una capacità Premium non viene conteggiata nello spazio di archiviazione di un utente di Power BI Pro.

A livello di tenant l'utilizzo totale non può superare 10 GB per utente della licenza Pro tra tutti gli utenti e le aree di lavoro nel tenant.

Per informazioni sulle altre funzionalità, vedere l'articolo sui [prezzi di Power BI](https://powerbi.microsoft.com/pricing).

Nel limite delle risorse di archiviazione dati rientrano i set di dati e i report di Excel personalizzati e gli elementi condivisi da altri utenti. I set di dati sono una delle origini dati caricate o a cui ci si è connessi. Queste origini dati includono i file di Power BI Desktop e le cartelle di lavoro di Excel in uso. Inoltre, sono inclusi nella capacità dei dati:

* Intervalli di Excel aggiunti al dashboard.
* Visualizzazioni locali di Reporting Services aggiunte al dashboard di Power BI
* Immagini caricate.

Le dimensioni di un dashboard da condividere variano a seconda di ciò che è stato aggiunto. Ad esempio, se si aggiungono elementi da due report che fanno parte di due set di dati diversi, le dimensioni includono entrambi i set di dati.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Gestire gli elementi di cui si è proprietari

È possibile sapere quante risorse di archiviazione dati si stanno usando nell'account di Power BI e gestire l'account.

1. Per gestire le risorse di archiviazione personali passare ad **Area di lavoro personale** nel riquadro di spostamento.
   
    ![Area di lavoro personale](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) nell'angolo in alto a destra \> **Gestisci archivio personale**.
   
    La barra in alto mostra il valore dello spazio di archiviazione utente usato rispetto al limite.
   
    ![Gestire il limite per l'archiviazione](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    I set di dati e i report sono separati in due schede:
   
    **Di mia proprietà:** questi report e set di dati sono stati caricati dall'utente nell'account di Power BI, inclusi i set di dati dei servizi, ad esempio di Salesforce e Dynamics CRM.  
    **Di proprietà di altri:** si tratta dei report e dei set di dati che altri utenti hanno condiviso con l'utente.
1. Per eliminare un set di dati o un report, selezionare l'icona del Cestino ![icona del Cestino](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tenere presente che potrebbero esserci utenti che usano report e dashboard basati su un set di dati. Se quindi si elimina il set di dati, i report e i dashboard non funzioneranno più.

## <a name="manage-your-workspace"></a>Gestire l'area di lavoro
1. Selezionare la freccia accanto ad **Aree di lavoro** \> selezionare il nome dell'area di lavoro.
   
    ![Selezionare un'area di lavoro](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selezionare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) nell'angolo in alto a destra \>  **Gestisci archiviazione gruppo**.
   
    La barra in alto mostra il valore dello spazio di archiviazione del gruppo usato rispetto al limite.
   
    ![Gestire l'archiviazione dell'area di lavoro](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    I set di dati e i report sono separati in due schede:
   
    **Di nostra proprietà:** questi report e set di dati caricati sono stati caricati dall'utente o da qualcun altro nell'account di Power BI del gruppo, inclusi i set di dati dei servizi, ad esempio di Salesforce e Dynamics CRM.
    **Di proprietà di altri:** si tratta dei report e dei set di dati che altri utenti hanno condiviso con il gruppo.
3. Per eliminare un set di dati o un report, selezionare l'icona del Cestino ![icona del Cestino](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Tutti i membri di un'area di lavoro che hanno le autorizzazioni di modifica sono autorizzati a eliminare dalla stessa i set di dati e i report.
   > 
   > 

Tenere presente che nel gruppo potrebbero esserci utenti che usano report e dashboard basati su un set di dati. Se quindi si elimina il set di dati, i report e i dashboard non funzioneranno più.

## <a name="dataset-limits"></a>Limiti per i set di dati
È previsto un limite di 1 GB per ogni set di dati importato in Power BI. Se si è scelto di mantenere l'esperienza di Excel, invece di importare i dati, il limite per il set di dati sarà è di 250 MB.

## <a name="what-happens-when-you-reach-a-limit"></a>Conseguenze del raggiungimento di un limite
Quando si raggiunge il limite della capacità dei dati concesso, il servizio offre le dovute istruzioni. 

Quando si seleziona l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), viene visualizzata una barra rossa che indica che è stato superato il limite per la capacità dei dati.

![Limite di archiviazione raggiunto](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Questo limite è indicato anche all'interno di **Gestisci archivio personale**.

 ![Gestire l'archivio personale, limite di archiviazione raggiunto](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Quando si tenta di eseguire un'azione che comporta il raggiungimento di uno dei limiti, viene visualizzato un messaggio che informa che è stato superato il limite. È possibile [gestire](#manage) lo spazio di archiviazione in modo da ridurre la quantità di archiviazione e superare il limite.

 ![Limite di archiviazione superato](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)

