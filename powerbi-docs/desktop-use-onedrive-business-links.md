---
title: Usare collegamenti OneDrive for Business in Power BI Desktop
description: Usare collegamenti OneDrive for Business in Power BI Desktop
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
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: davidi
ms.openlocfilehash: 2c249cac17e8fe6da35634c78837e3ca16e70a5c
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2017
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Usare collegamenti OneDrive for Business in Power BI Desktop
Molti utenti archiviano le cartelle di lavoro di Excel nell'unità OneDrive for Business, ottima per l'uso con Power BI Desktop. Con **Power BI Desktop** è possibile usare collegamenti online per file **Excel** archiviati in **OneDrive for Business** per creare report e oggetti visivi. È possibile usare un account di gruppo di **OneDrive for Business** oppure il proprio account **OneDrive for Business** personale.

Per ottenere un collegamento online da **OneDrive for Business** sono necessari alcuni passaggi specifici. Le sezioni seguenti illustrano i passaggi che consentono di condividere il collegamento del file tra gruppi, tra computer e con i colleghi.

## <a name="get-a-link-from-excel-starting-in-the-browser"></a>Ottenere un collegamento da Excel, iniziando nel browser
1. Passare a OneDrive for Business usando un browser. Fare clic con il pulsante destro del mouse sul file da usare e quindi scegliere **Apri in Excel**.
   
   > [!NOTE]
> L'interfaccia del browser potrebbe non apparire esattamente come nell'immagine seguente. Esistono diversi modi per selezionare **Apri in Excel** per i file nell'interfaccia del browser di **OneDrive for Business**. È possibile usare qualsiasi opzione che consenta di aprire il file in Excel.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. In **Excel** selezionare **File > Informazioni** e quindi selezionare il collegamento sopra il pulsante **Proteggi cartella di lavoro**. Selezionare **Copia link negli Appunti**. È possibile che nella versione in uso venga visualizzato **Copia percorso negli Appunti**.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_03.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Usare il collegamento in Power BI Desktop
In Power BI Desktop è possibile usare il collegamento che è stato appena copiato negli Appunti. Eseguire queste operazioni:

1. In Power BI Desktop selezionare **Recupera dati > Web**.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_04.png)
2. Incollare il collegamento nella finestra di dialogo **Da Web**. **Non** selezionare ancora OK.
   
    ![](media/desktop-use-onedrive-business-links/odb-links_05.png)
3. Si noti la stringa *?web=1* alla fine del collegamento. È necessario *rimuovere quella parte della stringa dell'URL Web* **prima** di selezionare **OK** per far sì che **Power BI Desktop** passi al file.
4. Se **Power BI Desktop** richiede le credenziali, scegliere **Windows** per i siti SharePoint locali o **Account aziendale** per i siti Office 365 o OneDrive for Business.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

Verrà visualizzata la finestra **Strumento di navigazione** che consente di selezionare dall'elenco di tabelle, fogli e intervalli disponibili nella cartella di lavoro di Excel. Da qui è possibile usare il file di OneDrive for Business come qualsiasi altro file di Excel, creare report e usarli nei set di dati come con qualsiasi altra origine dati.

> [!NOTE]
> Per usare un file di **OneDrive for Business** come origine dati nel servizio Power BI, con l'**aggiornamento del servizio** abilitato per tale file, assicurarsi di selezionare **OAuth2** come **metodo di autenticazione** quando si configurano le impostazioni di aggiornamento. In caso contrario è possibile riscontrare un errore (ad esempio *L'aggiornamento delle credenziali dell'origine dati non è riuscito.*) quando si prova a connettersi o ad aggiornare. Selezionare **OAuth2** come metodo di autenticazione per risolvere l'errore delle credenziali.
> 
> 

