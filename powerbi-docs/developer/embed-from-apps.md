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
ms.openlocfilehash: 53803c77dec8eb35c10db7f19a82f58144f88414
ms.sourcegitcommit: b45134887a452f816a97e384f4333db9e1d8b798
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237986"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Incorporare report o dashboard dalle app

In Power BI, è possibile creare app per riunire dashboard e report correlati, tutti in un'unica posizione. Quindi vengono pubblicate in ampi gruppi di persone all'interno dell'organizzazione. L'utilizzo di tali app è pertinente quando tutti gli utenti sono utenti di Power BI. Pertanto, è possibile condividere contenuto con loro usando le app di Power BI. In questo articolo sono riportati alcuni rapidi passaggi per incorporare contenuti in un'applicazione di terze parti da un'app di Power BI pubblicata.

## <a name="grab-a-report-embedurl-for-embedding"></a>Catturare un URL di incorporamento di report per l'incorporamento

1. Creare un'istanza di applicazione in un'area di lavoro utente, **Area di lavoro personale**. Condividere per il proprio utilizzo o guidare un altro utente a passare attraverso questo flusso.

2. Aprire il report desiderato nel servizio Power BI.

3. Passare a **File** > **Incorpora In SharePoint Online** e catturare l'URL di incorporamento di report da questa posizione. Viene visualizzato nello snapshot seguente. Oppure chiamare l'API REST GetReports/GetReport ed estrarre il campo URL di incorporamento di report corrispondente dalla risposta. La chiamata REST non deve avere un identificatore di area di lavoro come componente dell'URL perché è stata creata un'istanza dell'app nell'area di lavoro dell'utente.

4. Usare l'URL di incorporamento recuperato nel passaggio 3 con JavaScript SDK.

    ![Incorporare contenuti dalle app](media/embed-from-apps/embed-from-app.png)

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Catturare un URL di incorporamento di dashboard per l'incorporamento

1. Creare un'istanza di applicazione in un'area di lavoro utente, **Area di lavoro personale**. Condividere per il proprio utilizzo o guidare un altro utente a passare attraverso questo flusso.

2. Chiamare l'API REST GetDashboards ed estrarre il campo URL di incorporamento di dashboard corrispondente dalla risposta. La chiamata REST non deve avere un identificatore di area di lavoro come componente dell'URL perché è stata creata un'istanza dell'app nell'area di lavoro dell'utente.

3. Usare l'URL di incorporamento recuperato nel passaggio 2 con JavaScript SDK.

## <a name="next-steps"></a>Passaggi successivi

Vedere le procedure di incorporamento dalle aree di lavoro per le app per i clienti di terze parti e l'organizzazione:

> [!div class="nextstepaction"]
>[Incorporare contenuto per i clienti di terze parti](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporare contenuto per l'organizzazione](embed-sample-for-your-organization.md)