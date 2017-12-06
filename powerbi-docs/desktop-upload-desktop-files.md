---
title: Pubblicare da Power BI Desktop
description: Pubblicare da Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: ccf3f2a544276f3a641be3734fb2c48387706e69
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2017
---
# <a name="publish-from-power-bi-desktop"></a>Pubblicare da Power BI Desktop
Quando si pubblica un file di **Power BI Desktop** nel **servizio Power BI**, i dati nel modello e i report creati nella visualizzazione **Report** vengono pubblicati nell'area di lavoro di Power BI. Viene visualizzato un nuovo set di dati con lo stesso nome e tutti i report nello strumento di navigazione dell'area di lavoro.

La pubblicazione da **Power BI Desktop** consente di raggiungere lo stesso risultato di **Recupera dati** in Power BI per connettersi e caricare il file di **Power BI Desktop**.

> [!NOTE]
> Tutte le modifiche apportate ai report in Power BI, quando ad esempio si aggiungono, eliminano o modificano le visualizzazioni nei report, non verranno salvate nel file originale di **Power BI Desktop**.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Per pubblicare un set di dati e i report di Power BI Desktop
1. In Power BI Desktop selezionare \>**File**\>**Pubblica**\>**Pubblica in Power BI** oppure fare clic su **Pubblica** nella barra multifunzione.  
   ![](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)
2. Accedere a Power BI.

Al termine viene visualizzato un collegamento per aprire il report nel sito di Power BI.  
    ![](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Ripubblicare o sostituire un set di dati pubblicato da Power BI Desktop
Quando si pubblica un file di **Power BI Desktop**, il set di dati e i report creati in **Power BI Desktop** vengono caricati nel sito Power BI. Quando si ripubblica il file di **Power BI Desktop**, il set di dati nel sito Power BI viene sostituito con il set di dati caricato dal file di **Power BI Desktop**.

La procedura è molto semplice, ma ci sono delle cose da sapere:

* Se si hanno già due o più set di dati in Power BI con lo stesso nome del file di **Power BI Desktop**, la pubblicazione potrebbe non riuscire. Verificare che in Power BI sia presente solo un set di dati con lo stesso nome. È anche possibile rinominare il file e pubblicarlo, creando un nuovo set di dati con lo stesso nome del file.
* Se si rinomina o si elimina una colonna o una misura, le visualizzazioni già presenti in Power BI che contengono questo campo potrebbero essere interrotte. 
* Power BI ignora alcune modifiche al formato delle colonne esistenti, ad esempio quando si modifica il formato di una colonna da 0,25 a 25%.
* Se è configurata una pianificazione degli aggiornamenti per il set di dati esistente in Power BI e si aggiungono nuove origini dati al file e lo si ripubblica, sarà necessario accedere a tali origini dati in *Gestisci origini dati* prima dell'aggiornamento pianificato successivo.

