---
title: Power BI ed ExpressRoute
description: Power BI ed ExpressRoute
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 59ddddcf1b02f07b850294fa314b7508f7f9fcdc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856960"
---
# <a name="power-bi-and-expressroute"></a>Power BI ed ExpressRoute

**ExpressRoute** è un servizio di Azure che consente di creare connessioni private tra i data center di Azure (in cui risiede Power BI) e l'infrastruttura locale oppure creare connessioni private tra i data center di Azure e l'ambiente di condivisione del percorso.

Per creare una connessione di rete privata dell'organizzazione a Power BI è possibile usare **Power BI** ed **ExpressRoute** (oppure la funzionalità di condivisione del percorso di un ISP), escludendo Internet per meglio proteggere i dati riservati e le connessioni di Power BI.

Per altre informazioni, vedere [Panoramica di ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI è compatibile con ExpressRoute, con alcune eccezioni, in cui Power BI ottiene o invia dati attraverso la rete Internet pubblica. Per un elenco degli URL usati da Power BI, vedere [URL di Power BI](power-bi-whitelist-urls.md).

![Diagramma di ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)