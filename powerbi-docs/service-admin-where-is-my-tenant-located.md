---
title: Dove si trova il tenant di Power BI?
description: "Informazioni sulla posizione del tenant di Power BI e come viene selezionata la località. È importante comprendere questo aspetto, perché può influire sulle interazioni con il servizio."
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: 51d54d0ee8f21eec076389c1370f7bad415fa412
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2018
---
# <a name="where-is-my-power-bi-tenant-located"></a>Dove si trova il tenant di Power BI?
<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Informazioni sulla posizione del tenant di Power BI e come viene selezionata la località. È importante comprendere questo aspetto, perché può influire sulle interazioni con il servizio.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Come determinare la posizione del tenant di Power BI
Per trovare l'area in cui risiede il tenant, è possibile seguire questa procedura.

1. Selezionare **?** nel servizio Power BI.
2. Selezionare **Informazioni su Power BI**.
3. Cercare il valore accanto a **I dati sono archiviati in**. Questa è l'area in cui si trova il tenant.

![](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Modalità di selezione dell'area dati
L'area dati si basa sul paese selezionato al momento della creazione iniziale del tenant. Questo vale per l'iscrizione a Office 365, oltre a Power BI, perché queste informazioni sono condivise. Se si tratta di un nuovo tenant, quando si effettua l'iscrizione viene visualizzato un elenco a discesa di paesi.

![](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

La località in cui verranno archiviati i dati si basa su questa selezione. Power BI sceglierà l'area dati più vicina alla selezione.

> [!WARNING]
> Questa selezione non può essere modificata.
> 
> 

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

