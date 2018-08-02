---
title: Connettersi a Lithium con Power BI
description: Lithium per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6cbd67a9c35726830fc862326d9a015b96952b83
ms.sourcegitcommit: fbb7924603f8915d07b5e6fc8f4d0c7f70c1a1e1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "37136296"
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
4. Specificare l'URL della community Lithium. Usare il formato *https://community.yoursite.com*.
   
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
[Che cos'è Power BI?](power-bi-overview.md)

[Power BI - Concetti di base](service-basic-concepts.md)

