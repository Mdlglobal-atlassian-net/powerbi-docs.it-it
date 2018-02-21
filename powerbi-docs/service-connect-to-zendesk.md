---
title: Connettersi a Zendesk con Power BI
description: Zendesk per Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
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
ms.author: sarinas
ms.openlocfilehash: 447f400136f9678cad068f215ee82522253fc0d5
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-zendesk-with-power-bi"></a>Connettersi a Zendesk con Power BI
Il pacchetto di contenuto Zendesk offre un dashboard di Power BI e un set di report di Power BI che forniscono informazioni dettagliate sul numero di ticket e sulle prestazioni degli agenti. È possibile usare il dashboard e i report forniti oppure personalizzarli per evidenziare le informazioni a cui si è maggiormente interessati.  I dati verranno aggiornati automaticamente una volta al giorno. 

Connettersi al [pacchetto di contenuto Zendesk](https://app.powerbi.com/getdata/services/zendesk) oppure leggere altre informazioni sull'[integrazione di Zendesk](https://powerbi.microsoft.com/integrations/zendesk) con Power BI.

>[!NOTE]
>Per la connessione, è necessario un account amministratore di Zendesk. Altre informazioni sui [requisiti](#Requirements) sono disponibili più avanti.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
   ![](media/service-connect-to-zendesk/pbi_getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-zendesk/pbi_getservices.png) 
3. Selezionare **Zendesk** \> **Recupera**.
   
   ![](media/service-connect-to-zendesk/zendesk.png)
4. Specificare l'URL associato all'account. Il formato dell'URL sarà **https://company.zendesk.com**. Per informazioni dettagliate su [come trovare questi parametri](#FindingParams), vedere più avanti.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskconnect.png)
5. Quando richiesto, immettere le credenziali di Zendesk.  Selezionare **oAuth 2** come meccanismo di autenticazione e fare clic su **Accedi**. Seguire il flusso di autenticazione di Zendesk. Se è già stato effettuato l'accesso a Zendesk nel browser, le credenziali potrebbero non essere richieste.
   
   > [!NOTE]
   > Questo pacchetto di contenuto richiede la connessione a un account amministratore Zendesk. 
   > 
   > 
   
   ![](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Fare clic su **Consenti** per consentire a Power BI di accedere ai dati Zendesk.
   
   ![](media/service-connect-to-zendesk/zendesk2.jpg)
7. Fare clic su **Connetti** per avviare il processo di importazione. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, il nuovo report e il nuovo set di dati. I nuovi elementi sono contrassegnati con un asterisco giallo \*.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskdash.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](power-bi-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](service-dashboard-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificare la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto di Power BI include i dati relativi a:  

* Utenti (utenti finali e agenti)  
* Organizzazioni  
* Gruppi  
* Ticket  

Sono anche disponibili diverse misure calcolate, ad esempio per quanto riguarda il tempo medio di attesa e il numero di ticket risolti negli ultimi 7 giorni. Nel pacchetto di contenuto è incluso un elenco completo.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Requisiti di sistema
Per accedere al pacchetto di contenuto Zendesk, è necessario un account amministratore di Zendesk. Gli agenti o gli utenti finali interessati a visualizzare i dati di Zendesk possono aggiungere un suggerimento ed esaminare il connettore di Zendesk in [Power BI Desktop](desktop-connect-to-data.md).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
L'URL di Zendesk corrisponderà a quello usato per accedere all'account Zendesk. Se non si è certi di quale sia l'URL di Zendesk, è possibile vedere la [Guida di accesso](https://www.zendesk.com/login/) di Zendesk.

## <a name="troubleshooting"></a>Risoluzione dei problemi
In caso di problemi di connessione, verificare l'URL di Zendesk e assicurarsi che si stia usando un account amministratore di Zendesk.

## <a name="next-steps"></a>Passaggi successivi
* [Introduzione a Power BI](service-get-started.md)
* [Recuperare i dati](service-get-data.md)

