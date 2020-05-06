---
title: Connettersi all'app Regional Emergency Response Dashboard
description: Come ottenere e installare l'app modello COVID-19 Decision Support Dashboard per gli interventi di emergenza locali e come connettersi ai dati
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82149671"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Connettersi all'app Regional Emergency Response Dashboard
Regional Emergency Response Dashboard è il componente per la creazione di report della [soluzione Microsoft Power Platform per gli interventi di emergenza locali](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Gli amministratori delle organizzazioni locali possono visualizzare il dashboard nel tenant di Power BI, dove potranno visualizzare rapidamente dati e metriche importanti che permetteranno loro di prendere decisioni efficaci.

![Report dell'app Regional Emergency Response Dashboard](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

Questo articolo illustra come installare l'app Regional Emergency Response usando l'app modello Regional Emergency Response Dashboard e come connettersi alle origini dati.

Per informazioni dettagliate sugli elementi presentati nel dashboard, vedere [Ottenere informazioni dettagliate](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

Dopo aver installato l'app modello e aver effettuato la connessione alle origini dati, è possibile personalizzare il report in base alle esigenze specifiche. È quindi possibile distribuirlo come app ai colleghi dell'organizzazione.

## <a name="prerequisites"></a>Prerequisiti

Prima di installare questa app modello, è necessario installare e configurare la [soluzione Regional Emergency Response](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy). L'installazione di questa soluzione crea i riferimenti alle origini dati necessari per popolare l'app con i dati.

Durante l'installazione della soluzione Regional Emergency Response, prendere nota dell'[URL dell'istanza dell'ambiente Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). Sarà necessario per connettere l'app modello ai dati.

## <a name="install-the-app"></a>Installare l'app

1. Per ottenere l'app, fare clic sul collegamento seguente: [App modello Regional Emergency Response Dashboard](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Nella pagina di AppSource per l'app selezionare [**Scarica adesso**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response).

    [![App Regional Emergency Response Dashboard in AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Selezionare **Installa**. 

    ![Installare l'app Regional Emergency Response Dashboard](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Dopo l'installazione, l'app sarà visualizzata nella pagina App.

   ![App Regional Emergency Response Dashboard nella pagina App](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Connettersi alle origini dati

1. Selezionare l'icona nella pagina App per aprire l'app.

1. Nella schermata iniziale selezionare **Esplora app**.

   ![Schermata iniziale dell'app modello](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   L'app viene aperta e visualizza dati di esempio.

1. Selezionare il collegamento **Connettere i dati** nel banner nella parte superiore della pagina.

   ![Collegamento Connettere i dati per l'app Regional Emergency Response Dashboard](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. Nella finestra di dialogo visualizzata digitare l'[URL dell'istanza dell'ambiente Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Ad esempio: https://[ambiente].crm.dynamics.com. Al termine fare clic su **Avanti**.

   ![Finestra di dialogo con l'URL dell'app Regional Emergency Response Dashboard](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. Nella finestra di dialogo successiva visualizzata impostare il metodo di autenticazione su **OAuth2**. Non è necessario eseguire alcuna operazione per l'impostazione del livello di privacy.

   Fare clic su **Accedi**.

   ![Finestra di dialogo di autenticazione dell'app Regional Emergency Response Dashboard](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Nella schermata di accesso di Microsoft accedere a Power BI.

   ![Schermata di accesso di Microsoft](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Dopo aver eseguito l'accesso, il report si connette alle origini dati e viene popolato con dati aggiornati. Durante questo periodo viene attivato il monitoraggio attività.

   ![Aggiornamento in corso dell'app Regional Emergency Response Dashboard](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Pianificare l'aggiornamento del report

Al termine dell'aggiornamento dei dati [configurare una pianificazione dell'aggiornamento](../refresh-scheduled-refresh.md) per mantenete aggiornati i dati del report.

1. Nella barra delle intestazioni superiore selezionare **Power BI**.

   ![Barra di navigazione di Power BI](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. Nel riquadro di spostamento a sinistra cercare l'area di lavoro Regional Emergency Response Dashboard in **Aree di lavoro** e seguire le istruzioni descritte nell'articolo [Configurare l'aggiornamento pianificato](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizza e condividi

Per informazioni dettagliate, vedere [Personalizzare e condividere l'app](../service-template-apps-install-distribute.md#customize-and-share-the-app). Assicurarsi di leggere le [dichiarazioni di non responsabilità](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) prima di pubblicare o distribuire l'app.

## <a name="next-steps"></a>Passaggi successivi
* [Informazioni sull'app Regional Emergency Response Dashboard](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Configurare e ottenere informazioni sul modello di esempio Crisis Communication in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Domande? [Contattare la community di Power BI](https://community.powerbi.com/)
* [Che cosa sono le app modello di Power BI?](../service-template-apps-overview.md)
* [Installare e distribuire le app modello nell'organizzazione](../service-template-apps-install-distribute.md)
