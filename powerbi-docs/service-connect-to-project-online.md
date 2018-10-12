---
title: Connettersi a Project Online con Power BI
description: Project Online per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 75017eed249b7ec3c4eaab5931a4c1be80770ab1
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46548857"
---
# <a name="connect-to-project-online-with-power-bi"></a>Connettersi a Project Online con Power BI
Microsoft Project Online è una soluzione online flessibile per la gestione del portfolio di progetti (PPM) e il lavoro quotidiano. Progetto Online consente alle organizzazioni di iniziare, definire le priorità degli investimenti nel portfolio di progetti e offrire i vantaggi aziendali previsti. Il pacchetto di contenuto Project Online per Power BI consente di recuperare informazioni dettagliate da Project Online e di usarle per facilitare la gestione di progetti, raccolte e risorse.

Connettersi al [pacchetto di contenuto Project Online](https://app.powerbi.com/getdata/services/project-online) per Power BI.

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![](media/service-connect-to-project-online/getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
   ![](media/service-connect-to-project-online/services.png)
3. Selezionare **Microsoft Project Online** \> **Recupera**.
   
   ![](media/service-connect-to-project-online/mproject.png)
4. Nella casella di testo **URL Project Web App** immettere l'URL di Project Web App a cui connettersi e selezionare **Avanti**. Si noti che questo può differire dall'esempio se è presente un dominio personalizzato. Nella casella di testo **Lingua sito PWA**, digitare il numero corrispondente alla lingua scelta per il sito Project Web Access. Digitare la cifra "1" per l'inglese, "2" per il francese, "3" per il tedesco, "4" per il portoghese (Brasile), " 5" per portoghese (Portogallo) e "6" per lo spagnolo. 
   
    ![](media/service-connect-to-project-online/params.png)
5. In Metodo di autenticazione selezionare **oAuth2** \> **Accedi**. Quando richiesto, immettere le credenziali di Project Online e seguire il processo di autenticazione.
   
    ![](media/service-connect-to-project-online/creds.png)
    
Si noti che è necessario disporre di Visualizzatore portfolio, Program Manager o delle autorizzazioni di amministratore per l'istanza di Project Web App a cui ci si connette.

6. Una notifica indicherà che è in corso il caricamento dei dati. A seconda delle dimensioni dell'account l'operazione potrebbe richiedere alcuni minuti. Dopo l'importazione dei dati in Power BI, nel riquadro di spostamento sinistro vengono visualizzati il nuovo dashboard, 13 report e il nuovo set di dati. Si tratta del dashboard predefinito creato da Power BI per visualizzare i dati, che è possibile modificare per visualizzare i dati nel modo desiderato.

   ![](media/service-connect-to-project-online/dashboard2.png)

7. Una volta pronti i dashboard e i report, si può iniziare a esplorare i dati di Project Online. Il pacchetto di contenuto contiene 13 report avanzati e dettagliati per la panoramica portfolio (6 pagine di report), panoramica risorse (5 pagine di report) e stato progetto (2 pagine di report). 

   ![](media/service-connect-to-project-online/report1.png)
   
   ![](media/service-connect-to-project-online/report3.png)
   
   ![](media/service-connect-to-project-online/report2.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

**Espandere il pacchetto di contenuto**

Scaricare il [file PBIT GitHub](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) per personalizzare e aggiornare ulteriormente il pacchetto di contenuto

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

