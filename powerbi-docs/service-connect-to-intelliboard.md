---
title: Connettersi a IntelliBoard con Power BI
description: IntelliBoard per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c397ec0f302ec558e0277c92a871a94dd7f28e87
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Connettersi a IntelliBoard con Power BI
IntelliBoard offre un accesso semplificato ai dati del sistema LMS di Moodle con Reporting Services. Il pacchetto di contenuto IntelliBoard per Power BI offre altre funzionalità di analisi, incluse le metriche per i corsi, gli utenti registrati, le prestazioni complessive e l'attività del sistema LMS.

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

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

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
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

