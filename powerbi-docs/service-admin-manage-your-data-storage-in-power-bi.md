---
title: Gestire l'archiviazione dei dati
description: Informazioni su come è possibile gestire l'archiviazione dei dati individuale o dell'area di lavoro per le app per assicurarsi che sia possibile continuare a pubblicare report e set di dati.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e7c0399072bfef35a1103a5db448da183f64f74c
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="manage-your-data-storage"></a>Gestire l'archiviazione dei dati
Informazioni su come è possibile gestire l'archiviazione dei dati individuale o dell'area di lavoro per le app per assicurarsi che sia possibile continuare a pubblicare report e set di dati.

Gli utenti e le aree di lavoro app hanno capacità di dati personalizzate

* Ai clienti che scelgono le licenze gratuita e Pro viene assegnato uno spazio di archiviazione dati massimo di 10 GB.
* Gli utenti con licenza Pro possono creare aree di lavoro per le app con 10 GB di archiviazione dati ciascuna.

A livello di tenant l'utilizzo totale non può superare 10 GB per utente della licenza Pro tra tutti gli utenti e le aree di lavoro per le app nel tenant.

Per informazioni sulle altre funzionalità, vedere l'articolo sui [prezzi di Power BI](https://powerbi.microsoft.com/pricing).

Nel limite delle risorse di archiviazione dati rientrano i set di dati e i report di Excel personalizzati e quelli condivisi da altri utenti. I set di dati sono origini dati che sono state caricate o a cui si è connessi, inclusi i file di Power BI Desktop e le cartelle di lavoro di Excel usate. Inoltre, sono inclusi nella capacità dei dati:

* Intervalli di Excel aggiunti al dashboard.
* Visualizzazioni locali di Reporting Services aggiunte al dashboard di Power BI
* Immagini caricate.

Le dimensioni di un dashboard da condividere variano a seconda di ciò che è stato aggiunto. Ad esempio, se si aggiungono elementi da due report che fanno parte di due set di dati diversi, le dimensioni includeranno entrambi i set di dati.

<a name="manage"/>

## <a name="manage-items-owned-by-you"></a>Gestire i propri elementi 
È possibile sapere quante risorse di archiviazione dati si stanno usando nell'account di Power BI e gestire l'account.

1. Per gestire lo spazio di archiviazione personale, passare a **Area di lavoro personale** nel riquadro di spostamento sinistro.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Selezionare l'icona a forma di ingranaggio ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) nell'angolo in alto a destra e quindi selezionare \> **Gestisci archivio personale**.
   
    La barra in alto mostra il valore dello spazio di archiviazione utente usato rispetto al limite.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    I set di dati e i report sono separati in due schede:
   
    **Di mia proprietà:** si tratta dei report e dei set di dati caricati nell'account di Power BI, inclusi i set di dati dei servizi, ad esempio di Salesforce e Dynamics CRM.  
    **Di proprietà di altri:** si tratta dei report e dei set di dati che altri utenti hanno condiviso con l'utente.
3. Per eliminare un set di dati o un report, selezionare l'icona del cestino ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tenere presente che potrebbero esserci utenti che usano report e dashboard basati su un set di dati. Se quindi si elimina il set di dati, i report e i dashboard non funzioneranno più.

## <a name="manage-your-app-workspace"></a>Gestire la propria area di lavoro per le app
1. Selezionare la freccia accanto ad **Aree di lavoro** \>e quindi selezionare il nome dell'area di lavoro per le app.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selezionare l'icona a forma di ingranaggio ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) nell'angolo in alto a destra e quindi selezionare \> **Gestisci archiviazione gruppo**.
   
    La barra in alto mostra il valore dello spazio di archiviazione del gruppo usato rispetto al limite.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    I set di dati e i report sono separati in due schede:
   
    **Di nostra proprietà:** si tratta dei report e dei set di dati caricati nell'account di Power BI del gruppo, inclusi i set di dati dei servizi, ad esempio di Salesforce e Dynamics CRM.
    **Di proprietà di altri:** si tratta dei report e dei set di dati che altri utenti hanno condiviso con il gruppo.
3. Per eliminare un set di dati o un report, selezionare l'icona del cestino ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Tutti i membri di un'area di lavoro per le app che hanno le autorizzazioni di modifica sono autorizzati a eliminare dalla stessa i set di dati e i report.
   > 
   > 

Tenere presente che nel gruppo potrebbero esserci utenti che usano report e dashboard basati su un set di dati. Se quindi si elimina il set di dati, i report e i dashboard non funzioneranno più.

## <a name="dataset-limits"></a>Limiti per i set di dati
È previsto un limite di 1 GB per ogni set di dati importato in Power BI. Se si è scelto di mantenere l'esperienza di Excel, invece di importare i dati, il limite per il set di dati sarà di 250 MB.

## <a name="what-happens-when-you-hit-a-limit"></a>Conseguenze del raggiungimento di un limite
Quando si raggiunge il limite della capacità dei dati concesso, il servizio fornisce le dovute istruzioni. 

Quando si seleziona l'icona dell'ingranaggio ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), viene visualizzata una barra rossa che indica che è stato superato il limite per la capacità dei dati.

![](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

All'interno di **Gestisci archiviazione personale**viene inoltre visualizzato quanto segue:

 ![](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Quando si tenta di eseguire un'azione che comporta il raggiungimento di uno dei limiti, viene visualizzato un messaggio che indica che è stato superato il limite. Sarà possibile [gestire](#manage) lo spazio di archiviazione in modo da ridurre la quantità di archiviazione e superare il limite.

 ![](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

