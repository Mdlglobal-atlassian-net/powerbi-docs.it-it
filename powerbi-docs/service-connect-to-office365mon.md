---
title: Connettersi a Office365Mon con Power BI
description: Office365Mon per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 18093772232d119a24e76437d3f62a145a0a7153
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-office365mon-with-power-bi"></a>Connettersi a Office365Mon con Power BI
Con Power BI e il pacchetto di contenuto Office365Mon è facile analizzare i dati sulle prestazioni, sull'integrità e sulle interruzioni di servizio di Office 365. Power BI recupera i dati, inclusi i probe di integrità e interruzione del servizio, quindi crea il dashboard e i report predefiniti in base a tali dati.

Connettersi al [Pacchetto di contenuto Office365Mon](https://app.powerbi.com/groups/me/getdata/services/office365mon) per Power BI.

>[!NOTE]
>È necessario un account di amministratore Office365Mon per connettersi e caricare il pacchetto di contenuto di Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selezionare **Office365Mon** \> **Recupera**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. In Metodo di autenticazione selezionare **oAuth2** \> **Accedi**.
   
   Quando richiesto, immettere le credenziali dell'account amministratore di Office365Mon e seguire il processo di autenticazione.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. I nuovi elementi vengono contrassegnati con un asterisco giallo \*, selezionare la voce Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="troubleshooting"></a>Risoluzione dei problemi
Se si verifica un errore **"Accesso non riuscito"** dopo aver usato le credenziali di sottoscrizione di Office365Mon per eseguire accesso, significa che l'account in uso non ha le autorizzazioni per recuperare i dati di Office365Mon dall'account. Verificare che sia un account amministratore e riprovare.

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati per Power BI](service-get-data.md)

