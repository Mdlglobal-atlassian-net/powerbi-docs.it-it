---
title: Connettersi a Hospital Emergency Response Decision Support Dashboard
description: Come ottenere e installare l'app modello per le emergenze sanitarie COVID-19 Decision Support Dashboard e come connettersi ai dati
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: b951e96a5d81603dc91e4fc47a2b412d4140f85d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "80752051"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>Connettersi a Hospital Emergency Response Decision Support Dashboard
L'app modello Hospital Emergency Response Decision Support Dashboard è il componente per la creazione di report della [soluzione Microsoft Power Platform per la risposta alle emergenze sanitarie](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/). Il dashboard mostra i dati aggregati dei responsabili della gestione dell'emergenza nel rispettivo sistema sanitario per consentire loro di prendere decisioni tempestive e corrette.

![Report dell'app Hospital Emergency Response Decision Support Dashboard](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

Questo articolo descrive come installare l'app e come connettersi alle origini dati. Per informazioni su come usare il report che verrà visualizzato con questa app, vedere la [documentazione dell'app Hospital Emergency Response Decision Support Dashboard](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard).

Dopo aver installato l'app modello e aver effettuato la connessione alle origini dati, è possibile personalizzare il report in base alle esigenze specifiche. È quindi possibile distribuirlo come app ai colleghi dell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

Prima di installare questa app modello, è necessario installare e configurare la [soluzione Hospital Emergency Response Power Platform](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure). L'installazione di questa soluzione crea i riferimenti alle origini dati necessari per popolare l'app con i dati.

Quando si installa la soluzione Hospital Emergency Response Power Platform, prendere nota dell'[URL dell'istanza dell'ambiente Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Sarà necessario per connettere l'app modello ai dati.

## <a name="install-the-app"></a>Installare l'app

1. Per ottenere l'app, fare clic sul collegamento seguente: [App modello Hospital Emergency Response Decision Support Dashboard](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare)

1. Nella pagina di AppSource per l'app selezionare [**Scarica adesso**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare).

    [![App Hospital Emergency Response Decision Support Dashboard in AppSource](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare)

1. Leggere le informazioni in **Per finire** e selezionare **Continua**.

    ![App Hospital Emergency Response Decision Support Dashboard, Per finire](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. Selezionare **Installa**. 

    ![Installare l'app Hospital Emergency Response Decision Support Dashboard](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    Dopo l'installazione, l'app sarà visualizzata nella pagina App.

   ![App Hospital Emergency Response Decision Support Dashboard nella pagina App](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Connettersi alle origini dati

1. Selezionare l'icona nella pagina App per aprire l'app.

1. Nella schermata iniziale selezionare **Esplora app**.

   ![Schermata iniziale dell'app modello](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   L'app viene aperta e visualizza dati di esempio.

1. Selezionare il collegamento **Connettere i dati** nel banner nella parte superiore della pagina.

   ![Collegamento Connettere i dati per l'app Hospital Emergency Response Decision Support Dashboard](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. Nella finestra di dialogo visualizzata:
   1. Nel campo del nome dell'organizzazione immettere il nome dell'organizzazione, ad esempio, "Sistemi per la sanità Contoso". Questo campo è facoltativo. Questo nome viene visualizzato nel lato superiore sinistro del dashboard.
   1. Nel campo CDS_base_solution digitare l'[URL dell'istanza dell'ambiente Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Ad esempio: https://[ambiente].crm.dynamics.com. Al termine fare clic su **Avanti**.

   ![Finestra di dialogo dell'URL dell'app Hospital Emergency Response Decision Support Dashboard](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. Nella finestra di dialogo successiva visualizzata impostare il metodo di autenticazione su **OAuth2**. Non è necessario eseguire alcuna operazione per l'impostazione del livello di privacy.

   Fare clic su **Accedi**.

   ![Finestra di dialogo di autenticazione dell'app Hospital Emergency Response Decision Support Dashboard](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. Nella schermata di accesso di Microsoft accedere a Power BI.

   ![Schermata di accesso di Microsoft](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   Dopo aver eseguito l'accesso, il report si connette alle origini dati e viene popolato con dati aggiornati. Durante questo periodo viene attivato il monitoraggio attività.

   ![Aggiornamento dell'app Hospital Emergency Response Decision Support Dashboard in corso](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Pianificare l'aggiornamento del report

Al termine dell'aggiornamento dei dati [configurare una pianificazione dell'aggiornamento](../refresh-scheduled-refresh.md) per mantenete aggiornati i dati del report.

1. Nella barra delle intestazioni superiore selezionare **Power BI**.

   ![Barra di navigazione di Power BI](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. Nel riquadro di spostamento a sinistra cercare l'area di lavoro Hospital Emergency Response Decision Support Dashboard in **Aree di lavoro** e seguire le istruzioni descritte nell'articolo [Configurare l'aggiornamento pianificato](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizza e condividi

Per informazioni dettagliate, vedere [Personalizzare e condividere l'app](../service-template-apps-install-distribute.md#customize-and-share-the-app). Assicurarsi di leggere le [dichiarazioni di non responsabilità](../create-reports/sample-covid-19-us.md#disclaimers) prima di pubblicare o distribuire l'app.

## <a name="next-steps"></a>Passaggi successivi
* [Informazioni sul report Hospital Emergency Response](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [Configurare e ottenere informazioni sul modello di esempio Crisis Communication in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
* [Che cosa sono le app modello di Power BI?](../service-template-apps-overview.md)
* [Installare e distribuire le app modello nell'organizzazione](../service-template-apps-install-distribute.md)
