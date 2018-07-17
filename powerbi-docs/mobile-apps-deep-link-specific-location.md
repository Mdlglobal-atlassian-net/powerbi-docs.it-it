---
title: Creare un collegamento a una posizione specifica nelle app Power BI per dispositivi mobili
description: Informazioni su come creare un collegamento diretto a un dashboard, un riquadro o un report specifico nell'app Power BI per dispositivi mobili con un collegamento Uniform Resource Identifier (URI).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: maggies
ms.openlocfilehash: fb05b6fd2378c8fe2b6dec35250df31d227b7760
ms.sourcegitcommit: e8d924ca25e060f2e1bc753e8e762b88066a0344
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37135445"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Creare un collegamento a una posizione specifica nelle app Power BI per dispositivi mobili
È possibile creare e usare un collegamento Uniform Resource Identifier (URI) per collegarsi a una posizione specifica (un *collegamento diretto*) all'interno delle app Power BI per dispositivi mobili su tutte le piattaforme per dispositivi mobili: iOS, dispositivi Android e Windows 10.

I collegamenti URI possono puntare direttamente a dashboard, riquadri e report.

La destinazione del collegamento diretto determina il formato dell'URI. Seguire questi passaggi per creare collegamenti diretti a diverse posizioni. 

## <a name="open-the-power-bi-mobile-app"></a>Aprire l'app Power BI per dispositivi mobili
Usare questo URI per aprire l'app Power BI per dispositivi mobili in qualsiasi dispositivo:

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>Aprire un dashboard specifico
Questo URI aprirà un dashboard specifico nell'app Power BI per dispositivi mobili:

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

Per trovare l'ID oggetto del dashboard con 36 caratteri, passare al dashboard specifico nel servizio Power BI (https://powerbi.com). Ad esempio, vedere la sezione evidenziata dell'URL:

https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**

Se il dashboard si trova in un gruppo diverso da Area di lavoro, aggiungere `&GroupObjectId=<36-character-group-id>` prima o dopo l'ID del dashboard. Ad esempio: 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Si noti la e commerciale (&) tra i due ID.

## <a name="open-to-a-specific-tile-in-focus"></a>Aprire un riquadro specifico in modalità messa a fuoco
Questo URI aprirà un riquadro specifico in modalità messa a fuoco nell'app Power BI per dispositivi mobili:

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

Per trovare gli ID oggetto del dashboard e del riquadro con 36 caratteri, passare al dashboard specifico nel servizio Power BI (https://powerbi.com) e aprire il riquadro in modalità messa a fuoco. Ad esempio, vedere le sezioni evidenziate dell'URL:

https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

Per questo riquadro, l'URI sarà:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

Si noti la e commerciale (&) tra i due ID.

Se il dashboard si trova in un gruppo diverso da Area di lavoro, aggiungere `&GroupObjectId=<36-character-group-id>`.

## <a name="open-to-a-specific-report"></a>Aprire un report specifico
Questo URI aprirà un report specifico nell'app Power BI per dispositivi mobili:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

Per trovare l'ID oggetto del report con 36 caratteri, passare al report specifico nel servizio Power BI (https://powerbi.com). Ad esempio, vedere la sezione evidenziata dell'URL:

https://powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

## <a name="open-to-a-specific-report-page"></a>Aprire un pagina del report specifica
Questo URI aprirà una pagina del report specifica nell'app Power BI per dispositivi mobili:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

Il titolo della pagina del report è "ReportSection", seguito da un numero. Ancora una volta, aprire il report nel servizio Power BI (https://powerbi.com) e passare alla pagina del report specifica. 

Ad esempio, vedere la sezione evidenziata dell'URL:

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**ReportSection11**

## <a name="open-in-full-screen-mode"></a>Apri in modalità schermo intero
Aggiungere il parametro in grassetto per aprire un report specifico in modalità schermo intero:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

ad esempio: 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>Aggiungere contesto (facoltativo)
È anche possibile aggiungere contesto nella stringa. In tal modo, se è necessario contattare Microsoft, è possibile usare tale contesto per filtrare i dati all'applicazione in uso. Aggiungere `&context=<app-name>` al collegamento

Ad esempio, vedere la sezione evidenziata dell'URL: 

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**&context=SlackDeepLink**

## <a name="next-steps"></a>Passaggi successivi
I vostri commenti e suggerimenti ci aiutano a decidere quali funzioni implementare in futuro, quindi non perdete l'occasione di votare quali funzionalità vorreste avere a disposizione nelle app per dispositivi mobili di Power BI. 

* [App Power BI per dispositivi mobili](mobile-apps-for-mobile-devices.md)
* Seguire @MSPowerBI su Twitter
* Partecipare alla conversazione nella [community di Power BI](http://community.powerbi.com/)
* [Che cos'è Power BI?](power-bi-overview.md)

