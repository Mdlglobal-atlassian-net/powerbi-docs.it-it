---
title: Informazioni sulla sicurezza a livello di riga con Power BI Desktop
description: Come configurare la sicurezza a livello di riga per i set di dati importati e DirectQuery con Power BI Desktop.
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maghan
LocalizationGroup: Create reports
ms.openlocfilehash: febe8cafb7be578be0dcf23a151f28deb544a4c8
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Sicurezza a livello di riga con Power BI Desktop
La sicurezza a livello di riga con Power BI Desktop può essere usata per limitare l'accesso ai dati per determinati utenti. I filtri limitano l'accesso ai dati a livello di riga. È possibile definire i filtri nei ruoli.

È ora possibile configurare la sicurezza a livello di riga per i modelli di dati importati in Power BI con Power BI Desktop. È anche possibile configurare la sicurezza a livello di riga nei set di dati che usano DirectQuery, ad esempio SQL Server. In precedenza, era possibile implementare la sicurezza a livello di riga solo nei modelli di Analysis Services all'esterno di Power BI. Per le connessioni dinamiche ad Analysis Services è possibile configurare la sicurezza a livello di riga nel modello locale. L'opzione di sicurezza non verrà visualizzata per i set di dati di connessione dinamica.

> [!IMPORTANT]
> Se sono stati definiti ruoli/regole all'interno del servizio Power BI, sarà necessario creare di nuovo tali ruoli all'interno di Power BI Desktop e pubblicare il report nel servizio.
> 
> 

Altre informazioni sulle opzioni per la [sicurezza a livello di riga all'interno del servizio Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Passaggi successivi
[Sicurezza a livello di riga con il servizio Power BI](service-admin-rls.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](http://community.powerbi.com/)

