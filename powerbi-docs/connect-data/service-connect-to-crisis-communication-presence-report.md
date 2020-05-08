---
title: Connettersi all'app Crisis Communication Presence Report
description: Come ottenere e installare l'app modello COVID-19 Crisis Communication Presence Report e come connettersi ai dati
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: f637bb10ed7ec27dcb3da07fc04cae39328ffebe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80752258"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Connettersi all'app Crisis Communication Presence Report

Questa app di Power BI è l'elemento report/dashboard nella soluzione Microsoft Power Platform per le comunicazioni in tempo di crisi. Tiene traccia della posizione del personale per gli utenti dell'app Crisis Communication. La soluzione combina funzionalità di Power Apps, Power Automate, Teams, SharePoint e Power BI. Può essere usata nel Web, in dispositivi mobili o in Teams.

![Report dell'app Crisis Communication Presence Report](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

Il dashboard mostra i dati aggregati dei responsabili della gestione dell'emergenza nel rispettivo sistema sanitario per consentire loro di prendere decisioni tempestive e corrette.

Questo articolo descrive come installare l'app e come connettersi alle origini dati. Per altre informazioni sull'app Crisis Communication, vedere [Configurare e ottenere informazioni sul modello di esempio Crisis Communication in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)

Dopo aver installato l'app modello e aver effettuato la connessione alle origini dati, è possibile personalizzare il report in base alle esigenze specifiche. È quindi possibile distribuirlo come app ai colleghi dell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

Prima di installare questa app modello, è necessario installare e configurare l'[esempio Crisis Communication](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app). L'installazione di questa soluzione crea i riferimenti alle origini dati necessari per popolare l'app con i dati.

Quando si installa l'esempio Crisis Communication, prendere nota del [percorso della cartella dell'elenco di SharePoint di "CI_Employee Status" e dell'ID dell'elenco](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>Installare l'app

1. Per ottenere l'app, fare clic sul collegamento seguente: [App modello Crisis Communication Presence Report](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Nella pagina di AppSource per l'app selezionare [**Scarica adesso**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms).

    [![App Crisis Communication Presence Report in AppSource](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Leggere le informazioni in **Per finire** e selezionare **Continua**.

    ![App Crisis Communication Presence Report, Per finire](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Selezionare **Installa**. 

    ![Installare l'app Crisis Communication Presence Report](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    Dopo l'installazione, l'app sarà visualizzata nella pagina App.

   ![App Crisis Communication Presence Report nella pagina App](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Connettersi alle origini dati

1. Selezionare l'icona nella pagina App per aprire l'app.

1. Nella schermata iniziale selezionare **Esplora app**.

   ![Schermata iniziale dell'app modello](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   L'app viene aperta e visualizza dati di esempio.

1. Selezionare il collegamento **Connettere i dati** nel banner nella parte superiore della pagina.

   ![Collegamento Connettere i dati per l'app Crisis Communication Presence Report](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. Nella finestra di dialogo visualizzata:
   1. Nel campo SharePoint_Folder immettere il [percorso dell'elenco di SharePoint "CI_Employee Status"](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).
   1. Nel campo List_ID immettere l'ID dell'elenco ottenuto dalle impostazioni dell'elenco. Al termine fare clic su **Avanti**.

   ![Finestra di dialogo dell'URL per l'app Crisis Communication Presence Report](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. Nella finestra di dialogo successiva visualizzata impostare il metodo di autenticazione su **OAuth2**. Non è necessario eseguire alcuna operazione per l'impostazione del livello di privacy.

   Fare clic su **Accedi**.

   ![Finestra di dialogo di autenticazione dell'app Crisis Communication Presence Report](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Nella schermata di accesso di Microsoft accedere a Power BI.

   ![Schermata di accesso di Microsoft](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Dopo aver eseguito l'accesso, il report si connette alle origini dati e viene popolato con dati aggiornati. Durante questo periodo viene attivato il monitoraggio attività.

   ![Aggiornamento dell'app Crisis Communication Presence Report in corso](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Pianificare l'aggiornamento del report

Al termine dell'aggiornamento dei dati [configurare una pianificazione dell'aggiornamento](../refresh-scheduled-refresh.md) per mantenete aggiornati i dati del report.

1. Nella barra delle intestazioni superiore selezionare **Power BI**.

   ![Barra di navigazione di Power BI](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. Nel riquadro di spostamento a sinistra cercare l'area di lavoro Hospital Emergency Response Decision Support Dashboard in **Aree di lavoro** e seguire le istruzioni descritte nell'articolo [Configurare l'aggiornamento pianificato](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizza e condividi

Per informazioni dettagliate, vedere [Personalizzare e condividere l'app](../service-template-apps-install-distribute.md#customize-and-share-the-app). Assicurarsi di leggere le [dichiarazioni di non responsabilità](../create-reports/sample-covid-19-us.md#disclaimers) prima di pubblicare o distribuire l'app.

## <a name="next-steps"></a>Passaggi successivi
* [Configurare e ottenere informazioni sul modello di esempio Crisis Communication in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
* [Che cosa sono le app modello di Power BI?](../service-template-apps-overview.md)
* [Installare e distribuire le app modello nell'organizzazione](../service-template-apps-install-distribute.md)
