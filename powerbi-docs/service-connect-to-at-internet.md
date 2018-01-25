---
title: Connettersi ad AT Internet Bridge con Power BI
description: AT Internet Bridge per Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 67ed59961ca5bc4b382adf105bbc5c97ff470118
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
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

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Questo pacchetto di contenuto contiene i dati degli ultimi 45 giorni nelle tabelle seguenti:  

    - Conversion  
    - Devices  
    - Localization  
    - Sources  
    - Global Visits  

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

