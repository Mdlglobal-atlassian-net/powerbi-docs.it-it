---
title: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure
description: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: ff219e3032837e91f3c63e0c08f3abd1121e72ff
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2017
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
Per la procedura dettagliata di configurazione dell'aggiornamento pianificato, vedere [Aggiornare i dati in Power BI](refresh-data.md).

Se quando si configura l'aggiornamento pianificato per il database SQL di Azure viene visualizzato il codice errore 400 durante la modifica delle credenziali, eseguire le operazioni seguenti per configurare la regola del firewall appropriata:

1. Accedere al portale di gestione di Azure.
2. Passare all'istanza di SQL Server in Azure per cui configurare l'aggiornamento.
3. Attivare 'Servizi di Microsoft Azure' nella sezione Servizi consentiti.

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

