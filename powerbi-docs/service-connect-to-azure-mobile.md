---
title: Connettersi ad Azure Mobile Engagement con Power BI
description: Azure Mobile Engagement per Power BI
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
ms.openlocfilehash: ff7ff30874d4038547a0db94ae8c285081acc8eb
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-azure-mobile-engagement-with-power-bi"></a>Connettersi ad Azure Mobile Engagement con Power BI
Il pacchetto di contenuto Azure Mobile Engagement di Power BI consente di ottenere rapidamente informazioni sui dati dell'app.

Connettersi al [pacchetto di contenuto Azure Mobile Engagement](https://app.powerbi.com/groups/me/getdata/services/azme) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-azure-mobile/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
    ![](media/service-connect-to-azure-mobile/services.png)
3. Selezionare **Azure Mobile Engagement** \> **Recupera**.
   
    ![](media/service-connect-to-azure-mobile/azme.png) 
4. Specificare Raccolta di app e Nome app. Queste informazioni sono disponibili nell'account Azure Mobile Engagement.
   
    ![](media/service-connect-to-azure-mobile/parameters.png) 
5. In Metodo di autenticazione immettere la chiave e fare clic su Accedi.
   
    ![](media/service-connect-to-azure-mobile/creds.png)
6. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. I nuovi elementi vengono contrassegnati con un asterisco giallo, \*, che scompare dopo la selezione:
   
    ![](media/service-connect-to-azure-mobile/dashboard.png)

 **Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

