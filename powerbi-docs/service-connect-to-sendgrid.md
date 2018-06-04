---
title: Connettersi a SendGrid con Power BI
description: SendGrid per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a08d9d10725a5c135ef6732b8397a57833463f4c
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34247827"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Connettersi a SendGrid con Power BI
Il pacchetto di contenuto di Power BI per SendGrid consente di estrarre informazioni dettagliate e statistiche dal account di SendGrid. Grazie al pacchetto di contenuto SendGrid è possibile visualizzare le statistiche di SendGrid in un dashboard.

Connettersi al [pacchetto di contenuto SendGrid](https://app.powerbi.com/getdata/services/sendgrid) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. Selezionare il pacchetto di contenuto **SendGrid** e fare clic su **Recupera**.
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. Quando richiesto, specificare nome utente e password di SendGrid. Selezionare **Accedi**.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati, popolato con le statistiche relative ai messaggi di posta elettronica degli ultimi 90 giorni. I nuovi elementi sono contrassegnati con un asterisco giallo \*.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Nel dashboard di SendGrid vengono visualizzate le statistiche seguenti:

* Statistiche generali sulla posta elettronica, ovvero richieste, messaggi recapitati e non recapitati, messaggi di posta indesiderata bloccati, rapporti sui messaggi di posta indesiderata e così via.
* Statistiche sulla posta elettronica ordinate per categoria
* Statistiche sulla posta elettronica ordinate per area geografica
* Statistiche sulla posta elettronica ordinate per ISP
* Statistiche sulla posta elettronica ordinate per dispositivo, client e browser

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare i dati](service-get-data.md)

