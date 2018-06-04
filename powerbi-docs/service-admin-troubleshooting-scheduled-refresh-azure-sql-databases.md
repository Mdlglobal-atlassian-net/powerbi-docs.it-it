---
title: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure
description: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9439ac6bd0b4df568b964f548372fb94d2fd0b26
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34238527"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
Per la procedura dettagliata di configurazione dell'aggiornamento pianificato, vedere [Aggiornare i dati in Power BI](refresh-data.md).

Se quando si configura l'aggiornamento pianificato per il database SQL di Azure viene visualizzato il codice errore 400 durante la modifica delle credenziali, eseguire le operazioni seguenti per configurare la regola del firewall appropriata:

1. Accedere al portale di gestione di Azure.
2. Passare all'istanza di SQL Server in Azure per cui configurare l'aggiornamento.
3. Attivare 'Servizi di Microsoft Azure' nella sezione Servizi consentiti.

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

