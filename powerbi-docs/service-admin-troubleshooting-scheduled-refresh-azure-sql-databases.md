---
title: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure
description: Risoluzione dei problemi relativi all'aggiornamento pianificato per i database SQL di Azure in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d71a1202ba996b70c7477a33ccab936bebbfc5e
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542788"
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
