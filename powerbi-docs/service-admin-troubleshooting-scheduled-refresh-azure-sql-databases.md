---
title: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure
description: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
author: mgblythe
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9846f65951c9cd45f011a2b5ec81852df10b063f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855850"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI

Per informazioni dettagliate sull'aggiornamento, vedere [Aggiornare i dati in Power BI](refresh-data.md) e [Configurare l'aggiornamento pianificato](refresh-scheduled-refresh.md).

Se quando si configura l'aggiornamento pianificato per il database SQL di Azure viene visualizzato il codice di errore 400 durante la modifica delle credenziali, eseguire le operazioni seguenti per configurare la regola del firewall appropriata:

1. Accedere al [portale di Azure](https://portal.azure.com).

1. Passare al database SQL di Azure per cui si sta configurando l'aggiornamento.

1. Nella parte superiore del pannello **Panoramica** selezionare **Imposta firewall server**.

1. Nel pannello **Impostazioni del firewall** assicurarsi che l'impostazione **Consenti l'accesso a servizi di Azure** sia impostata su **Sì**.

    ![Servizi consentiti di Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
