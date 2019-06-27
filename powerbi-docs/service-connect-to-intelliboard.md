---
title: Connettersi a IntelliBoard con Power BI
description: IntelliBoard per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ab5ded52c6d8d8bfa150ce3f53e89516dc025cb2
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "66838907"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Connettersi a IntelliBoard con Power BI
IntelliBoard offre un accesso semplificato ai dati del sistema LMS di Moodle in Reporting Services. Il pacchetto di contenuto IntelliBoard per Power BI offre altre funzionalità di analisi, incluse le metriche per i corsi, gli utenti registrati, le prestazioni complessive e l'attività del sistema LMS.

Connettersi al [pacchetto di contenuto IntelliBoard](https://app.powerbi.com/getdata/services/intelliboard) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Selezionare **IntelliBoard**, quindi **Recupera**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Selezionare **OAuth 2**, quindi **Accedi**. Quando richiesto, fornire le credenziali di IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Dopo la connessione vengono caricati automaticamente un dashboard, un report e un set di dati. Al termine, i riquadri vengono aggiornati con i dati dell'account IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto include i dati delle tabelle seguenti:  

    - Activity  
    - Agents  
    - Auth  
    - Countries  
    - CoursesProgress  
    - Enrollments
    - Lang  
    - Platform  
    - Totals  
    - UsersProgress    

## <a name="system-requirements"></a>Requisiti di sistema
È necessario un account IntelliBoard con le autorizzazioni per le tabelle precedenti per creare un'istanza di questo pacchetto di contenuto.

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](power-bi-overview.md)

[Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md)

