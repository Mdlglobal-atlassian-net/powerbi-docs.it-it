---
title: Uso dello stesso account per Power BI e Azure
description: Come usare lo stesso account di accesso per Power BI e Azure
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: fac2faac6ddd62bbc5f8a74ba1764b10e597f58d
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>Uso dello stesso account per Power BI e Azure
Se si usa sia Power BI che Azure, è preferibile usare lo stesso account di accesso per entrambi i servizi in modo da non dover digitare la password per due volte.

Per accedere a Power BI viene usato l'account aziendale, associato all'indirizzo di posta elettronica aziendale o dell'istituto di istruzione.  Per accedere ad Azure viene invece usato un account Microsoft o l'account aziendale.

Se si vuole usare lo stesso account di accesso sia per Azure che per Power BI, assicurarsi di accedere ad Azure con l'account aziendale.

**Che succede se per l'accesso ad Azure si usa già l'account Microsoft?**

È possibile aggiungere l'account aziendale come co-amministratore in Azure.  Ecco come:

1. Accedere al [portale di gestione di Azure](http://manage.windowsazure.com/). Se si è utente di più directory di Azure, fare clic su **Sottoscrizioni** e quindi filtrare in modo da visualizzare solo la directory e le sottoscrizioni da modificare.
2. Nel riquadro di spostamento fare clic su **Impostazioni**, **Amministratori**e infine su **Aggiungi**.
3. Immettere l'indirizzo di posta elettronica associato all'account aziendale.
4. Selezionare le sottoscrizioni cui accedere con l'account aziendale e fare clic sul segno di spunta.

Al successivo accesso al portale di gestione di Azure usare l'indirizzo di posta elettronica aziendale.

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

