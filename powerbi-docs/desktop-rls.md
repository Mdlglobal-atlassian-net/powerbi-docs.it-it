---
title: Informazioni sulla sicurezza a livello di riga con Power BI Desktop
description: Come configurare la sicurezza a livello di riga per i set di dati importati e DirectQuery con Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 12/05/2019
LocalizationGroup: Create reports
ms.openlocfilehash: abbd8f34f42bdcfdca6e65df58c78bf394f00d91
ms.sourcegitcommit: 9a265d8117cc202f5f700286b5ff42a631aacdb4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2019
ms.locfileid: "74882800"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Sicurezza a livello di riga con Power BI Desktop

È possibile usare la sicurezza a livello di riga con Power BI Desktop per limitare l'accesso ai dati per determinati utenti. I filtri limitano l'accesso ai dati a livello di riga. È possibile definire i filtri nei ruoli.

È ora possibile configurare la sicurezza a livello di riga per i modelli di dati importati in Power BI con Power BI Desktop. È anche possibile configurare la sicurezza a livello di riga nei set di dati che usano [DirectQuery](desktop-use-directquery.md), ad esempio SQL Server. In precedenza, era possibile implementare la sicurezza a livello di riga solo nei modelli di Analysis Services locali all'esterno di Power BI. Per le connessioni dinamiche ad Analysis Services è possibile configurare la sicurezza a livello di riga nel modello locale. L'opzione di sicurezza non viene visualizzata per i set di dati di connessione dinamica.

> [!IMPORTANT]
> Se sono stati definiti ruoli e regole all'interno del servizio Power BI, è necessario creare di nuovo tali ruoli all'interno di Power BI Desktop e pubblicare il report nel servizio.

Altre informazioni sulle opzioni per la [sicurezza a livello di riga all'interno del servizio Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Passaggi successivi

[Sicurezza a livello di riga con il servizio Power BI](service-admin-rls.md)  

Altre domande? [Provare a rivolgersi alla community di Power BI](https://community.powerbi.com/)