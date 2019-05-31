---
title: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure
description: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0c22d005044c0ebddc242eb35908e26689fee597
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "61186899"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
Per la procedura dettagliata di configurazione dell'aggiornamento pianificato, vedere [Aggiornare i dati in Power BI](refresh-data.md).

Se quando si configura l'aggiornamento pianificato per il database SQL di Azure viene visualizzato il codice errore 400 durante la modifica delle credenziali, eseguire le operazioni seguenti per configurare la regola del firewall appropriata:

1. Accedere al portale di gestione di Azure.
2. Passare all'istanza di SQL Server in Azure per cui configurare l'aggiornamento.
3. Attivare 'Servizi di Microsoft Azure' nella sezione Servizi consentiti.

![Servizi consentiti di Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)

