---
title: Connettersi a Stripe con Power BI
description: Stripe per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b0e8739e93d24ba10b0ffc72042b847cce1d5fe9
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060759"
---
# <a name="connect-to-stripe-with-power-bi"></a>Connettersi a Stripe con Power BI
Visualizzare ed esplorare i dati di Stripe in Power BI con il pacchetto di contenuto Power BI. Il pacchetto di contenuto Stripe di Power BI esegue il pull dei dati su clienti, spese, eventi e fatture. I dati includono i diecimila eventi più recenti e le cinquemila spese effettuate negli ultimi 30 giorni. Il contenuto verrà aggiornato automaticamente una volta al giorno secondo una pianificazione controllata dall'utente. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Connettersi al [pacchetto di contenuto Stripe per Power BI](https://app.powerbi.com/getdata/services/stripe).

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare Recupera dati nella parte inferiore del riquadro di spostamento sinistro.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Selezionare **Stripe** &gt; **Recupera**.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. Specificare la [chiave API](https://dashboard.stripe.com/account/apikeys) di Stripe per la connessione.  
   
    ![](media/service-connect-to-stripe/creds.png)
5. Il processo di importazione inizierà automaticamente. Al termine nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati, contrassegnato con un asterisco. Selezionare il dashboard per visualizzare i dati importati.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="next-steps"></a>Passaggi successivi
[Che cos'è Power BI?](fundamentals/power-bi-overview.md)

[Recuperare dati per Power BI](service-get-data.md)

