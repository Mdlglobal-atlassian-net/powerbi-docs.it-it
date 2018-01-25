---
title: Connettersi a SendGrid con Power BI
description: SendGrid per Power BI
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
ms.openlocfilehash: d077bedcc1faa10af79cf3eba258b1dac969ae10
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
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

