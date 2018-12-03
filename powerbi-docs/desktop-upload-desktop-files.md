---
title: Pubblicare da Power BI Desktop
description: Pubblicare da Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: bbfb4a33c8413fe47f1c7749b001bf602dd4956c
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578130"
---
# <a name="publish-from-power-bi-desktop"></a>Pubblicare da Power BI Desktop
Quando si pubblica un file di **Power BI Desktop** nel **servizio Power BI**, i dati nel modello e i report creati nella visualizzazione **Report** vengono pubblicati nell'area di lavoro di Power BI. Viene visualizzato un nuovo set di dati con lo stesso nome e tutti i report nello strumento di navigazione dell'area di lavoro.

La pubblicazione da **Power BI Desktop** consente di raggiungere lo stesso risultato di **Recupera dati** in Power BI per connettersi e caricare il file di **Power BI Desktop**.

> [!NOTE]
> Le modifiche apportate al report in Power BI, ad esempio l'aggiunta, l'eliminazione o la modifica di visualizzazioni nel report, non vengono salvate nel file originale di **Power BI Desktop**.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Per pubblicare un set di dati e i report di Power BI Desktop
1. In Power BI Desktop selezionare \>**File**\>**Pubblica**\>**Pubblica in Power BI** oppure fare clic su **Pubblica** nella barra multifunzione.  

   ![Pulsante Pubblica](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Accedere a Power BI.
3. Selezionare la destinazione.

   ![Selezionare la destinazione di pubblicazione](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Al termine viene visualizzato un collegamento al report. Fare clic sul collegamento per aprire il report nel sito di Power BI.

![Finestra di dialogo Operazione riuscita per la pubblicazione](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Ripubblicare o sostituire un set di dati pubblicato da Power BI Desktop
Quando si pubblica un file di **Power BI Desktop**, il set di dati e i report creati in **Power BI Desktop** vengono caricati nel sito Power BI. Quando si ripubblica il file di **Power BI Desktop**, il set di dati nel sito Power BI viene sostituito con il set di dati caricato dal file di **Power BI Desktop**.

La procedura è molto semplice, ma è necessario tenere presenti alcuni aspetti:

* Se si hanno già due o più set di dati in Power BI con lo stesso nome del file di **Power BI Desktop**, la pubblicazione potrebbe non riuscire. Verificare che in Power BI sia presente solo un set di dati con lo stesso nome. È anche possibile rinominare il file e pubblicarlo, creando un nuovo set di dati con lo stesso nome del file.
* Se si rinomina o si elimina una colonna o una misura, le visualizzazioni già presenti in Power BI che contengono questo campo potrebbero essere interrotte. 
* Power BI ignora alcune modifiche al formato delle colonne esistenti, ad esempio quando si modifica il formato di una colonna da 0,25 a 25%.
* Se è configurata una pianificazione degli aggiornamenti per il set di dati esistente in Power BI e si aggiungono nuove origini dati al file e lo si ripubblica, sarà necessario accedere a tali origini dati in *Gestisci origini dati* prima dell'aggiornamento pianificato successivo.

