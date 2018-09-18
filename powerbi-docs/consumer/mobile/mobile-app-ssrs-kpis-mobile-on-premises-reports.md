---
title: Visualizzare report e indicatori KPI locali nelle app per dispositivi mobili di Power BI
description: L'app Power BI per dispositivi mobili consente di accedere in tempo reale a informazioni aziendali in locale usando dispositivi mobili abilitati per il tocco in SQL Server Reporting Services e nel server di report di Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/13/2018
ms.author: maggies
ms.openlocfilehash: fcc548829ae5a1a661ae55603544e25a51b0204c
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44743185"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Visualizzare report e indicatori KPI locali dei server di report nelle app Power BI per dispositivi mobili

L'app Power BI per dispositivi mobili consente di accedere in tempo reale a informazioni aziendali in locale usando dispositivi mobili abilitati per il tocco nel server di report di Power BI e in SQL Server 2016 Reporting Services (SSRS).

Si applica a:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Telefono Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Tablet Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone |iPad |Telefoni Android |Tablet Android |


![Home page del server di report nelle app per dispositivi mobili](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Operazioni preliminari
**Le app per dispositivi mobili in cui visualizzare il contenuto di Power BI, non in cui crearlo.**

* Tutti gli autori di contenuti nell'organizzazione [creano report di Power BI con Power BI Desktop, quindi li pubblicano nel portale Web del server di report di Power BI](../../report-server/quickstart-create-powerbi-report.md). 
* È possibile creare [indicatori KPI nel portale Web](https://docs.microsoft.com/sql/reporting-services/working-with-kpis-in-reporting-services), organizzarli in cartelle e contrassegnare i Preferiti, per poterli trovare facilmente. 
* [Creare report per dispositivi mobili di Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) con SQL Server 2016 Enterprise Edition Mobile Report Publisher e pubblicarli nel [portale Web di Reporting Services](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).  

Quindi, nell'app Power BI per dispositivi mobili, connettersi a un massimo di cinque server di report per visualizzare i report e gli indicatori KPI di Power BI, organizzati in cartelle o raccolti come Preferiti. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Esplorare gli esempi nelle app per dispositivi mobili senza una connessione al server
Anche se non si ha accesso a un portale Web di Reporting Services, è comunque possibile esplorare le funzionalità dei report per dispositivi mobili e agli indicatori KPI di Reporting Services. 

1. Toccare il pulsante di spostamento globale ![pulsante di spostamento globale](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-global-nav-button.png) nell'angolo superiore sinistro, quindi toccare l'icona a forma di ingranaggio in alto a destra ![Icona a forma di ingranaggio](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-settings-icon.png).
2. Toccare **Esempi per Reporting Services** quindi esplorare per interagire con gli indicatori KPI e i report per dispositivi mobili di esempio.
   
   ![Esempi di Reporting Services](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Connettersi a un server di report locale
È possibile visualizzare report di Power BI locali, report per dispositivi mobili di Reporting Services e indicatori KPI nelle app Power BI per dispositivi mobili. 

1. Nel dispositivo mobile aprire l'app Power BI.
2. Se non è ancora stato effettuato l'accesso a Power BI, toccare **Server di report**.
   
   ![Accedere a un server di report](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Se è già stato effettuato l'accesso all'app Power BI, toccare il pulsante di spostamento globale ![pulsante di spostamento globale](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-global-nav-button.png), quindi toccare l'icona a forma di ingranaggio ![Icona a forma di ingranaggio](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-settings-icon.png) in alto a destra.
3. Toccare **Connetti al server**.
   
    ![Connetti al server](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

     L'app per dispositivi mobili deve accedere al server in qualche modo. Sono disponibili alcune modalità:

    - L'uso della stessa rete o della stessa VPN è la modalità più semplice.
    - È possibile usare un proxy applicazione Web per connettersi dall'esterno dell'organizzazione. Per informazioni dettagliate, vedere [Uso di OAuth per connettersi a Reporting Services](mobile-oauth-ssrs.md). 
    - Aprire una connessione (porta) nel firewall.

1. Specificare l'indirizzo del server, il nome utente e la password. Usare questo formato per l'indirizzo del server:
   
     `http://<servername>/reports`
   
     OR
   
     `https://<servername>/reports`
   
   Includere **http** o **https** davanti alla stringa di connessione.
   
    ![Finestra di dialogo Connetti al server](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. (Facoltativo) in **Opzioni avanzate** è possibile assegnare un nome descrittivo al server, se si vuole.
6. È ora possibile visualizzare il server nella barra di spostamento a sinistra (chiamato "server di report di power bi" in questo esempio).
   
   ![Server di report nel riquadro di spostamento a sinistra](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios"></a>Connettersi a un server di report locale in iOS

Se si sta visualizzando Power BI nell'app per dispositivi mobili iOS, l'amministratore IT potrebbe aver definito un criterio di configurazione dell'app. In tal caso, l'esperienza di connessione al server di report risulta semplificata e non sarà necessario specificare molte informazioni quando ci si connette a un server di report. 

1. Viene visualizzato un messaggio che informa che l'app per dispositivi mobili è configurata con un server di report. Toccare **Accedi**.

    ![Accedere al server di report](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  Nella pagina **Connetti al server** il server di report è già compilato. Toccare **Connetti**.

    ![Dettagli del server di report compilati](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Digitare una password per l'autenticazione e quindi toccare **Accedi**. 

    ![Dettagli del server di report compilati](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

È ora possibile visualizzare e interagire con gli indicatori KPI e i report di Power BI archiviati nel server di report.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Visualizzare report e indicatori KPI di Power BI nell'app Power BI
I report di Power BI, i report per dispositivi mobili di Reporting Services e gli indicatori KPI vengono visualizzati nelle stesse cartelle in cui si trovano nel portale Web di Reporting Services. 

* Toccare un report di Power BI ![Icona del report di Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). per aprirlo in modalità orizzontale e interagire con esso nell'app Power BI.

    > [!NOTE]
  > Attualmente l'esecuzione di drill-down e drill-up non è abilitata nei report di Power BI in un Server di report di Power BI.
  
    ![Report di Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* In Power BI Desktop, i proprietario dei report possono [ottimizzare un report](../../desktop-create-phone-report.md) per le app Power BI per dispositivi mobili. Sul telefono cellulare, i report ottimizzati hanno un layout e un'icona speciale, ![Icona del report ottimizzato di Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png).
  
    ![Report ottimizzato di Power BI per dispositivi mobili](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Toccare un indicatore KPI per visualizzarlo in modalità messa a fuoco.
  
    ![Indicatore KPI in modalità messa a fuoco](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Visualizzare i report e gli indicatori KPI preferiti
È possibile contrassegnare gli indicatori KPI e i report come preferiti nel portale Web e quindi visualizzarli in un'unica cartella nel dispositivo mobile, assieme ai dashboard di Power BI preferiti.

* Toccare **Preferiti**.
  
   ![Preferiti nel riquadro di spostamento a sinistra](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Gli indicatori KPI e i report preferiti dal portale Web si trovano tutti in questa pagina, assieme ai dashboard di Power BI nel servizio Power BI:
  
   ![Report e dashboard di Power BI nella pagina Preferiti](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Rimuovere una connessione a un server di report
1. Nella parte inferiore della barra di spostamento a sinistra toccare **Impostazioni**.
2. Toccare il nome del server a cui non si vuole essere connessi.
3. Toccare **Rimuovi server**.

## <a name="next-steps"></a>Passaggi successivi
* [Che cos'è Power BI?](../../power-bi-overview.md)  
* Domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

