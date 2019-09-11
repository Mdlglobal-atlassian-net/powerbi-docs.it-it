---
title: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure
description: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4bc14b9a3d863732c581e8a144d612d864d65af8
ms.sourcegitcommit: c799941c8169cd5b6b6d63f609db66ab2af93891
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70391858"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI

Per informazioni dettagliate sull'aggiornamento, vedere [Aggiornare i dati in Power BI](refresh-data.md) e [Configurare l'aggiornamento pianificato](refresh-scheduled-refresh.md).

Se quando si configura l'aggiornamento pianificato per il database SQL di Azure viene visualizzato il codice di errore 400 durante la modifica delle credenziali, eseguire le operazioni seguenti per configurare la regola del firewall appropriata:

1. Accedere al [portale di Azure](https://portal.azure.com).

1. Passare al database SQL di Azure per cui si sta configurando l'aggiornamento.

1. Nella parte superiore del pannello **Panoramica** selezionare **Imposta firewall server**.

1. Nel pannello **Impostazioni del firewall** assicurarsi che l'impostazione **Consenti l'accesso a servizi di Azure** sia impostata su **Sì**.

    ![Servizi consentiti di Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
