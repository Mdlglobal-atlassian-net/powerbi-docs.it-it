---
title: Connettersi ad Adobe Analytics in Power BI Desktop (anteprima)
description: "Connettersi con facilità e usare Adobe Analytics in Power BI Desktop"
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
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: efd6d066e2f98f86248730917c2f4aa0c8a39983
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop-preview"></a>Connettersi ad Adobe Analytics in Power BI Desktop (anteprima)
In **Power BI Desktop** è possibile connettersi ad **Adobe Analytics** e usare i dati sottostanti esattamente come qualsiasi altra origine dati in Power BI Desktop. 

![Ottenere i dati da Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="enable-the-adobe-analytics-connector-preview"></a>Abilitare l'anteprima del connettore di Adobe Analytics 
Poiché il connettore di **Adobe Analytics** è attualmente in versione di anteprima, è necessario abilitare la funzionalità di anteprima perché il connettore sia disponibile nella finestra **Recupera dati**. Per abilitare l'anteprima del connettore, selezionare **File > Opzioni e impostazioni > Opzioni > Funzionalità in anteprima** in Power BI Desktop, quindi selezionare la casella di controllo accanto a **Segnalibri**. 

![Abilitare l'anteprima del connettore di Adobe Analytics in Opzioni](media/desktop-connect-adobe-analytics/connect-adobe-analytics_02.png)

Dopo aver effettuato la selezione è necessario riavviare **Power BI Desktop** per abilitare l'anteprima del connettore di Adobe Analytics.

## <a name="connect-to-adobe-analytics-data"></a>Connettersi ai dati di Adobe Analytics
Per connettersi ai dati di **Adobe Analytics**, selezionare **Recupera dati** nella barra multifunzione **Home** in Power BI Desktop. Selezionare **Servizi online** nelle categorie a sinistra per visualizzare **Connettore di Adobe Analytics**.

![Ottenere i dati da Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

Nella finestra di **Adobe Analytics** visualizzata selezionare il pulsante **Accedi** e specificare le credenziali per accedere all'account di Adobe Analytics. Sarà visualizzata la finestra di accesso di Adobe, come illustrato nella figura seguente.

![Accedere ad Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

Quando richiesto, inserire il nome utente e la password. Dopo aver stabilito la connessione, è possibile visualizzare in anteprima e selezionare più dimensioni e misure all'interno della finestra di dialogo **Strumento di navigazione** di Power BI per creare un unico output in formato tabulare. È anche possibile specificare tutti i parametri di input necessari per gli elementi selezionati. 

![Selezionare i dati con lo strumento di navigazione](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

È possibile **caricare** la tabella selezionata, che importa l'intera tabella in **Power BI Desktop**, oppure è possibile **modificare** la query, che consente di aprire **Editor di query** in modo da filtrare e perfezionare il set di dati da usare e quindi caricare il set di dati perfezionato in **Power BI Desktop**.

![Caricare o modificare i dati nello strumento di navigazione](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>Passaggi successivi
È possibile connettersi a molti tipi di dati usando Power BI Desktop. Per altre informazioni sulle origini dati, vedere le risorse seguenti:

* [Introduzione a Power BI Desktop](desktop-getting-started.md)
* [Origini dati in Power BI Desktop](desktop-data-sources.md)
* [Effettuare il data shaping e combinare i dati con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connettersi a cartelle di lavoro di Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Immettere dati direttamente in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

