---
title: Connettersi a Lithium con Power BI
description: Lithium per Power BI
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
ms.openlocfilehash: cac92465e36b87d2a59420f5a6265c219371ceba
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-lithium-with-power-bi"></a>Connettersi a Lithium con Power BI
Lithium sviluppa relazioni affidabili tra i migliori marchi del mondo e i rispettivi clienti, consentendo alle persone di ottenere risposte e condividere le proprie esperienze. Connettendo il pacchetto di contenuto Lithium a Power BI, è possibile misurare le metriche chiave relative alla community online per migliorare le vendite, ridurre i costi di assistenza e incrementare la fidelizzazione. 

Connettersi al [pacchetto di contenuto Lithium](https://app.powerbi.com/getdata/services/lithium) per Power BI.

>[!NOTE]
>Il pacchetto di contenuto per Power BI usa l'API Lithium. Un numero eccessivo di chiamate all'API potrebbe comportare addebiti aggiuntivi da parte di Lithium. Consultare l'amministratore di Lithium.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-lithium/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-lithium/pbi_getservices.png) 
3. Selezionare **Lithium** \> **Recupera**.
   
   ![](media/service-connect-to-lithium/lithiumconnect.png)
4. Specificare l'URL della community Lithium. Sarà nel formato *https://community.sitopersonale.com*.
   
   ![](media/service-connect-to-lithium/params.png)
5. Quando richiesto, immettere le credenziali di Lithium. Selezionare **oAuth 2** come meccanismo di autenticazione, fare clic su **Accesso** e seguire il flusso di autenticazione di Lithium.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. Al termine del flusso di accesso, verrà avviato il processo di importazione. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati. Selezionare il dashboard per visualizzare i dati importati.
   
    ![](media/service-connect-to-lithium/lithium.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="system-requirements"></a>Requisiti di sistema
Il pacchetto di contenuto Lithium richiede una community Lithium versione 15.9 o successive. Contattare l'amministratore di Lithium per controllare.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Power BI - Concetti di base](service-basic-concepts.md)

