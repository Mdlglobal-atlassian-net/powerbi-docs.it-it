---
title: Dove si trova il tenant di Power BI?
description: Informazioni sulla posizione del tenant di Power BI e come viene selezionata la località. È importante comprendere questo aspetto, perché può influire sulle interazioni con il servizio.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c0c6de63292d3087aaa78dd97b73f868ef9d804e
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293652"
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

