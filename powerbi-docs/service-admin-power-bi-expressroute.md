---
title: Power BI ed ExpressRoute
description: Power BI ed ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 62289c974e25207f3a991e7f17a0ee965c729b8a
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900130"
---
# <a name="power-bi-and-expressroute"></a>Power BI ed ExpressRoute

**ExpressRoute** è un servizio di Azure che consente di creare connessioni private tra i data center di Azure (in cui risiede Power BI) e l'infrastruttura locale oppure creare connessioni private tra i data center di Azure e l'ambiente di condivisione del percorso.

Per creare una connessione di rete privata dell'organizzazione a Power BI è possibile usare **Power BI** ed **ExpressRoute** (oppure la funzionalità di condivisione del percorso di un ISP), escludendo Internet per meglio proteggere i dati riservati e le connessioni di Power BI.

Per altre informazioni, vedere [Panoramica di ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI è compatibile con ExpressRoute, con alcune eccezioni, in cui Power BI ottiene o invia dati attraverso la rete Internet pubblica. Per un elenco degli URL usati da Power BI, vedere [URL di Power BI](power-bi-whitelist-urls.md).

![Diagramma di ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)