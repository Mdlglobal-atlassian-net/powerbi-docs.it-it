---
title: Usare collegamenti OneDrive for Business in Power BI Desktop
description: Usare collegamenti OneDrive for Business in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 706703985242284725fb4fc2d42bf46e54c605c7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83285809"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Usare collegamenti OneDrive for Business in Power BI Desktop
Molti utenti archiviano le cartelle di lavoro di Excel in OneDrive for Business, che offre un'ottima soluzione di interazione con Power BI Desktop. In Power BI Desktop si possono usare collegamenti online ai file di Excel archiviati in OneDrive for Business per creare report e oggetti visivi. È possibile usare un account di gruppo di OneDrive for Business oppure l'account OneDrive for Business personale.

Per ottenere un collegamento online da OneDrive for Business sono necessari alcuni passaggi specifici. Le sezioni seguenti illustrano i passaggi che consentono di condividere il collegamento del file tra gruppi, tra computer e con i colleghi.

## <a name="get-a-link-from-excel"></a>Ottenere un collegamento da Excel
1. Passare a OneDrive for Business usando un browser. Fare clic con il pulsante destro del mouse sul file da usare e quindi scegliere **Apri in Excel**.
   
   > [!NOTE]
   > L'interfaccia del browser potrebbe non apparire esattamente come nell'immagine seguente. Esistono diversi modi per selezionare **Apri in Excel** per i file nell'interfaccia del browser di OneDrive for Business. È possibile usare qualsiasi opzione che consenta di aprire il file in Excel.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. In Excel selezionare **File** > **Informazioni** e quindi selezionare **Copia percorso** sopra **Proteggi cartella di lavoro**.
   
   ![](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Usare il collegamento in Power BI Desktop
In Power BI Desktop è possibile usare il collegamento che è stato appena copiato negli Appunti. Eseguire queste operazioni:

1. In Power BI Desktop selezionare **Recupera dati** > **Web**.
   
   ![](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. Con l'opzione **Di base** selezionata, incollare il collegamento nella finestra di dialogo **Da Web**.
3. Rimuovere la stringa *?web=1* alla fine del collegamento, in modo che Power BI Desktop possa accedere correttamente al file, e quindi selezionare **OK**.
   
    ![](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. Se Power BI Desktop richiede le credenziali, scegliere **Windows** per i siti SharePoint locali o **Account aziendale** per i siti Office 365 o OneDrive for Business.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

   Verrà visualizzata la finestra **Strumento di navigazione** che consente di eseguire operazioni di selezione dall'elenco di tabelle, fogli e intervalli disponibili nella cartella di lavoro di Excel. Da qui è possibile usare il file di OneDrive for Business esattamente come qualsiasi altro file di Excel. Si possono creare report e usarli nei set di dati proprio come per qualsiasi altra origine dati.

> [!NOTE]
> Per usare un file di OneDrive for Business come origine dati nel servizio Power BI, con l'**aggiornamento del servizio** abilitato per tale file, assicurarsi di selezionare **OAuth2** come **metodo di autenticazione** quando si configurano le impostazioni di aggiornamento. In caso contrario, è possibile che venga restituito un errore (ad esempio *L'aggiornamento delle credenziali dell'origine dati non è riuscito.* ) quando si prova a eseguire la connessione o l'aggiornamento. Selezionare **OAuth2** come metodo di autenticazione per risolvere l'errore delle credenziali.
> 
> 

