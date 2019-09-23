---
title: Power BI ed ExpressRoute
description: Power BI ed ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c7d12bf6a1a2a02c988f8351a1844be1080ad2b8
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074789"
---
# <a name="power-bi-and-expressroute"></a>Power BI ed ExpressRoute

**ExpressRoute** è un servizio di Azure che consente di creare connessioni private tra i data center di Azure (in cui risiede Power BI) e l'infrastruttura locale oppure creare connessioni private tra i data center di Azure e l'ambiente di condivisione del percorso.

Per creare una connessione di rete privata dell'organizzazione a Power BI è possibile usare **Power BI** ed **ExpressRoute** (oppure la funzionalità di condivisione del percorso di un ISP), escludendo Internet per meglio proteggere i dati riservati e le connessioni di Power BI.

Per altre informazioni, vedere [Panoramica di ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI è compatibile con ExpressRoute, con alcune eccezioni, in cui Power BI ottiene o invia dati attraverso la rete Internet pubblica. Per un elenco degli URL usati da Power BI, vedere [URL di Power BI](power-bi-whitelist-urls.md).

![Diagramma di ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)