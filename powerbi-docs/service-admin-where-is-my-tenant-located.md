---
title: Dove si trova il tenant di Power BI?
description: Informazioni sulla posizione del tenant di Power BI e come viene selezionata la località. È importante comprendere questo aspetto, perché può influire sulle interazioni con il servizio.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 08536d412796b1516b689ed728af0126330edf93
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580139"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Dove si trova il tenant di Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Informazioni sulla posizione del tenant di Power BI e come viene selezionata la località. Conoscere la posizione è importante, perché può influire sulle interazioni con il servizio.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Come determinare la posizione del tenant di Power BI

Per trovare l'area del tenant, seguire questa procedura.

1. Nel servizio Power BI selezionare Guida (**?**) nel menu in alto, quindi **Informazioni su Power BI**.

1. Cercare il valore accanto a **I dati sono archiviati in**. Questa è l'area in cui si trova il tenant. È anche l'area in cui sono memorizzati i dati, a meno che non si usino capacità dedicate in aree diverse per le proprie aree di lavoro.

    ![Area del data center](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Modalità di selezione dell'area dati

L'area dati si basa sul paese che si seleziona quando si crea il tenant. Questo vale per l'iscrizione a Office 365, oltre a Power BI, perché queste informazioni sono condivise. Se si tratta di un nuovo tenant, selezionare il paese appropriato dall'elenco quando si effettua l'iscrizione.

![Selezione del paese](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI seleziona l'area dati più vicina a questa selezione, determinando così dove vengono archiviati i dati per il tenant.

> [!IMPORTANT]
> Dopo aver creato il tenant, non è possibile modificare questa selezione.

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

