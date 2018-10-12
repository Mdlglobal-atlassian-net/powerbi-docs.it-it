---
title: Connettersi ad Application Insights per Power BI
description: Application Insights per Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 00a42a3ffcc92ca7bc48459635359acb9da8da82
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46548351"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Connettersi ad Application Insights con Power BI
Usare Power BI per creare potenti dashboard personalizzati in base ai dati di telemetria di [Application Insights](https://azure.microsoft.com/documentation/articles/app-insights-overview/). Concepire i dati di telemetria dell'app in nuovi modi. Combinare metriche da più app o servizi componenti in un unico dashboard. Questa prima versione del pacchetto di contenuto Power BI per Application Insights include widget per metriche relative all'uso comune, ad esempio utenti attivi, visualizzazione della pagina, sessioni, versione del browser e del sistema operativo e la distribuzione geografica degli utenti in una mappa.

Connettersi al [Pacchetto di contenuto Application Insights per Power BI](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>Questo metodo di integrazione è ora **deprecato**. Per altre informazioni sul metodo preferito per la connessione di Application Insights a Power BI, usare la [funzionalità di esportazione delle query di analisi](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries).

## <a name="how-to-connect"></a>Come connettersi
1. Selezionare **Recupera dati** nella parte inferiore del riquadro di spostamento sinistro.
   
    ![Pulsante Recupera dati](media/service-connect-to-application-insights/pbi_getdata.png)
2. Nella casella **Servizi** selezionare **Recupera**.
   
    ![Pulsante Ottieni servizi](media/service-connect-to-application-insights/pbi_getservices.png)
3. Selezionare **Application Insights** > **Recupera**.
   
    ![Pacchetto di contenuto Application Insights](media/service-connect-to-application-insights/appinsights.png)
4. Fornire i dettagli dell'applicazione a cui ci si vuole connettere, tra cui il **nome della risorsa di Application Insights**, il **gruppo di risorse**e l' **ID sottoscrizione**. Per altre informazioni, vedere [Ricerca dei parametri di Application Insights](#FindingAppInsightsParams) qui di seguito.
   
    ![Finestra di dialogo di connessione di Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Selezionare **Accedi** e seguire le istruzioni per la connessione.
   
    ![Accesso alla connessione di Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. Il processo di importazione inizia automaticamente. Al termine viene visualizzata una notifica e nel riquadro di spostamento verranno visualizzati un nuovo dashboard, un nuovo report e un nuovo set di dati, contrassegnati con un asterisco.  Selezionare il dashboard per visualizzare i dati importati.
   
    ![Dashboard di Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**Altre operazioni**

* Provare a [porre una domanda nella casella Domande e risposte](consumer/end-user-q-and-a.md) nella parte superiore del dashboard
* [Cambiare i riquadri](service-dashboard-edit-tile.md) nel dashboard.
* [Selezionare un riquadro](consumer/end-user-tiles.md) per aprire il report sottostante.
* Anche se la pianificazione prevede che il set di dati venga aggiornato quotidianamente, è possibile modificarne la frequenza di aggiornamento o provare ad aggiornarlo su richiesta usando **Aggiorna ora**

## <a name="whats-included"></a>Cosa è incluso
Il pacchetto di contenuto Application Insights include le tabelle e le metriche seguenti:  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Individuazione dei parametri
Il nome della risorsa, il gruppo di risorse e l'ID sottoscrizione sono reperibili nel portale di Azure. Selezionando il nome verrà aperta una visualizzazione dettagliata; sarà possibile usare l'elenco a discesa Essentials per trovare tutti i valori necessari.

![Parametri di Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Copiare e incollare i dati nei campi in Power BI:

![Parametri di Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Passaggi successivi
[Introduzione a Power BI](service-get-started.md)

[Recuperare dati in Power BI](service-get-data.md)

