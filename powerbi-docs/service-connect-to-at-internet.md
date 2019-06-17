---
title: Connettersi ad AT Internet Bridge con Power BI
description: AT Internet Bridge per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 41b390190f8ce3c071f790edcdf86f0e3bd4a0c2
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721313"
---
# <a name="connect-to-at-internet-bridge-with-power-bi"></a>Connettersi ad AT Internet Bridge con Power BI
AT Internet consente di estrarre un valore immediato dai dati tramite la piattaforma di analisi digitale unificata, la suite di analisi. Il pacchetto di contenuto AT Internet Bridge per Power BI include dati su visite, origini, localizzazione e dispositivi per il sito.

Connettersi al [pacchetto di contenuto AT Internet Bridge](https://app.powerbi.com/getdata/services/at-internet-bridge) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-at-internet/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-at-internet/pbi_getservices.png) 
3. Selezionare **AT Internet Bridge** \> **Recupera**.
   
   ![](media/service-connect-to-at-internet/atinternet.png)
4. Specificare il numero di sito Web AT Internet a cui ci si vuole connettere.
   
   ![](media/service-connect-to-at-internet/params.png)
5. Selezionare **Basic** come meccanismo di autenticazione, specificare nome utente e password AT Internet e fare clic su **Accedi**.
   
   ![](media/service-connect-to-at-internet/creds.png)
6. Fare clic su **Connetti** per avviare il processo di importazione. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
    ![](media/service-connect-to-at-internet/atinternet.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Questo pacchetto di contenuto contiene i dati degli ultimi 45 giorni nelle tabelle seguenti:  

    - Conversion  
    - Devices  
    - Localization  
    - Sources  
    - Global Visits  

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](power-bi-overview.md)

[Concetti di base sulle finestre di progettazione del servizio Power BI](service-basic-concepts.md)

