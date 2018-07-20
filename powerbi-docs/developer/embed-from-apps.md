---
title: Incorporare report o dashboard dalle app
description: Informazioni su come integrare o incorporare un report o un dashboard da un'app Power BI e non da un'area di lavoro per le app.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2817ccb25fc9aa6d3e8150c776558366dcf0ccb6
ms.sourcegitcommit: 0c870a006e525447497e678484874a2f137b9abd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088840"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Incorporare report o dashboard dalle app

In **Power BI** è possibile creare app per riunire in un'unica posizione **dashboard** e **report** correlati e quindi pubblicarli a gruppi di molte persone nell'organizzazione. L'uso di queste app è utile quando tutti gli utenti sono utenti di Power BI ed è quindi possibile condividere i contenuti tramite le app di Power BI. Di seguito sono riportati alcuni rapidi passaggi per incorporare contenuti in un'applicazione di terze parti da un'app di Power BI pubblicata.

## <a name="how-to-grab-report-embed-url-for-embedding"></a>Come acquisire l'URL di incorporamento di un report per l'incorporamento

1. Creare un'istanza dell'applicazione nell'area di lavoro di un utente ("Area di lavoro personale") condividendola o guidando un altro utente nell'esecuzione di questo flusso.

2. Aprire il report desiderato nel servizio Power BI.

3. Passare a File->Incorpora in SharePoint Online e acquisire da qui l'URL di incorporamento del report (vedere lo snapshot riportato di seguito) oppure chiamare l'API REST GetReports/GetReport ed estrarre dalla risposta il campo embedURL del report corrispondente. Si noti che la chiamata REST non deve includere nell'URL un identificatore dell'area di lavoro poiché l'istanza dell'app è stata creata nell'area di lavoro dell'utente.

4. Usare l'URL di incorporamento recuperato al passaggio 3 con JS SDK.

    ![Incorporare contenuti dalle app](media/embed-from-apps/embed-from-app.png)

## <a name="how-to-grab-dashboard-embed-url-for-embedding"></a>Come acquisire l'URL di incorporamento di un dashboard per l'incorporamento

1. Creare un'istanza dell'applicazione nell'area di lavoro di un utente ("Area di lavoro personale") condividendola o guidando un altro utente nell'esecuzione di questo flusso.

2. Chiamare l'API REST GetDashboards ed estrarre dalla risposta il campo embedURL del dashboard corrispondente. Si noti che la chiamata REST non deve includere nell'URL un identificatore dell'area di lavoro poiché l'istanza dell'app è stata creata nell'area di lavoro dell'utente.

3. Usare l'URL di incorporamento recuperato al passaggio 4 con JS SDK.

## <a name="next-steps"></a>Passaggi successivi

Vedere anche le procedure di incorporamento dalle aree di lavoro per le app per i clienti di terze parti e l'organizzazione.

> [!div class="nextstepaction"]
>[Incorporare contenuto per i clienti di terze parti](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)