---
title: Visualizzare report per dispositivi mobili e indicatori KPI di SSRS nell'app per dispositivi mobili Windows 10 - Power BI
description: L'app Power BI per dispositivi mobili per Windows 10 consente di accedere in tempo reale a informazioni aziendali importanti in locale usando dispositivi mobili abilitati per il tocco.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: maggies
ms.openlocfilehash: b7435aa7cda68854409c4be7981a06a70d999f09
ms.sourcegitcommit: e8d924ca25e060f2e1bc753e8e762b88066a0344
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37136227"
---
# <a name="view-reporting-services-ssrs-mobile-reports-and-kpis-in-the-windows-10-power-bi-mobile-app"></a>Visualizzare report per dispositivi mobili e indicatori KPI di Reporting Services (SSRS) nell'app Power BI per dispositivi mobili per Windows 10
L'app Power BI per dispositivi mobili per Windows 10 consente di accedere in tempo reale a informazioni aziendali importanti in locale usando dispositivi mobili abilitati per il tocco in SQL Server 2016 Reporting Services. 

![Report per dispositivi mobili di Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>Operazioni preliminari
[Creare report per dispositivi mobili di Reporting Services](https://msdn.microsoft.com/library/mt652547.aspx) con SQL Server 2016 Enterprise Edition Mobile Report Publisher e pubblicarli nel [portale Web di Reporting Services](https://msdn.microsoft.com/library/mt637133.aspx). Creare gli indicatori KPI direttamente nel portale Web. Organizzarli in cartelle e contrassegnare i Preferiti, per poterli trovare facilmente. 

Nell'app Power BI per dispositivi mobili per Windows 10 visualizzare quindi i report per dispositivi mobili e gli indicatori KPI, organizzati in cartelle o raccolti come Preferiti. 

> [!NOTE]
> Il dispositivo deve eseguire Windows 10. L'app funziona meglio su dispositivi con almeno 1 GB di RAM e 8 GB di memoria interna.
> 
> 

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Esaminare gli esempi senza un server SQL Server 2016 Reporting Services
Anche se non si ha accesso a un portale Web di Reporting Services, è comunque possibile esplorare le funzionalità dei report per dispositivi mobili di Reporting Services.

1. Aprire l'app Power BI nel dispositivo Windows 10.
2. Toccare il pulsante di spostamento globale ![pulsante di spostamento globale](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) nell'angolo in alto a sinistra.
3. Toccare l'icona **Impostazioni** ![Icona Impostazioni](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), fare clic con il pulsante destro del mouse oppure toccare e tenere premuto **Connetti al server**, quindi toccare **Visualizza esempi**.
   
   ![Visualizzare esempi SSRS](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Aprire la cartella dei report sulle vendite al dettaglio o dei report sulle vendite per analizzare gli indicatori KPI e i report per dispositivi mobili.
   
   ![Indicatori KPI e report per dispositivi mobili di esempio](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Esplorare gli esempi per interagire con gli indicatori KPI e i report per dispositivi mobili.

## <a name="connect-to-a-reporting-services-report-server"></a>Connettersi al server di report di SQL Server Reporting Services
1. Nella parte inferiore della barra di spostamento a sinistra toccare **Impostazioni** ![Icona Impostazioni](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)
2. Toccare **Connetti al server**.
3. Specificare l'indirizzo del server, il nome utente e la password. Usare questo formato per l'indirizzo del server:
   
     `http://<servername>/reports` OPPURE `https://<servername>/reports`
   
   > [!NOTE]
   > Includere **http** o **https** all'inizio della stringa di connessione.
   > 
   > 
   
    Toccare **Opzione avanzata** per assegnare un nome al server se si vuole.
4. Toccare il segno di spunta per connettersi. 
   
   È ora possibile visualizzare il server nella barra di spostamento a sinistra.
   
   ![Server nella barra di spostamento a sinistra](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Toccare il pulsante di spostamento ![Pulsante di spostamento](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) in qualsiasi momento per passare dai report per dispositivi mobili di Reporting Services ai dashboard e viceversa nel servizio Power BI. 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Visualizzare gli indicatori KPI e i report per dispositivi mobili di Reporting Services nell'app Power BI
I report per dispositivi mobili e gli indicatori KPI di Reporting Services vengono visualizzati nelle stesse cartelle in cui si trovano nel portale Web di Reporting Services.

![Cartelle dei report](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Toccare un indicatore KPI per visualizzarlo in modalità messa a fuoco.
  
    ![Indicatore KPI in modalità messa a fuoco](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Toccare un report per dispositivi mobili per aprirlo e interagire con esso nell'app Power BI.
  
    ![Report per dispositivi mobili di Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Visualizzare i report e gli indicatori KPI preferiti
È possibile contrassegnare gli indicatori KPI e i report per dispositivi mobili come preferiti nel portale Web di Reporting Services e quindi visualizzarli in un'unica cartella nel dispositivo Windows 10, assieme ai dashboard e ai report di Power BI preferiti.

* Toccare **Preferiti**.
  
   ![Icona Preferiti](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   I Preferiti nel portale Web vengono visualizzati tutti in questa pagina.
  
   ![Pagina Preferiti](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-favorites.png)

Altre informazioni sui [dashboard preferiti nelle app Power BI per dispositivi mobili](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Rimuovere una connessione a un server di report
È possibile essere connessi a un solo server di report alla volta dall'app Power BI per dispositivi mobili. Se ci si vuole connettere a un altro server, è necessario disconnettersi dal server corrente.

1. Nella parte inferiore della barra di spostamento a sinistra toccare **Impostazioni** ![Icona Impostazioni](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Toccare e tenere premuto il nome del server a cui non si vuole essere connessi.
3. Toccare **Rimuovi server**.
   
    ![Rimuovi server](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Creare Report per dispositivi mobili e indicatori KPI di Reporting Services
Non creare gli indicatori KPI e i report per dispositivi mobili di Reporting Services nell'app Power BI per dispositivi mobili. ma crearli in SQL Server Mobile Report Publisher e un portale Web di SQL Server 2016 Reporting Services 

* [Creare report per dispositivi mobili personalizzati di Reporting Services](https://msdn.microsoft.com/library/mt652547.aspx) e pubblicarli in un portale Web di Reporting Services.
* Creare [indicatori KPI in un portale Web di Reporting Services](https://msdn.microsoft.com/library/mt683632.aspx)

## <a name="next-steps"></a>Passaggi successivi
* [Introduzione all'app Power BI per dispositivi mobili per Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [Che cos'è Power BI?](power-bi-overview.md)  
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

