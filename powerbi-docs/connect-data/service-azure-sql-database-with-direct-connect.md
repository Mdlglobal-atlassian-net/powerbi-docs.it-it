---
title: Database SQL di Azure con DirectQuery
description: Database SQL di Azure con DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.date: 04/28/2020
LocalizationGroup: Data from databases
ms.openlocfilehash: aa1ae57d928633ce61ab66a8e0e905118c3a7877
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302162"
---
# <a name="azure-sql-database-with-directquery"></a>Database SQL di Azure con DirectQuery

Informazioni su come connettersi direttamente al database SQL di Azure e creare report che usano dati in tempo reale. È possibile mantenere i dati nell'origine invece che in Power BI.

Con DirectQuery, le query vengono inviate nuovamente al database SQL di Azure durante l'esplorazione dei dati nella visualizzazione report. Si tratta di un'esperienza consigliata per gli utenti che hanno familiarità con i database e le entità cui si connettono.

**Note:**

* Specificare il nome completo del server al momento della connessione (vedere di seguito per altri dettagli).
* Assicurarsi che le regole del firewall per il database siano impostate su "[Consenti l'accesso a Servizi di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services)".
* Ogni azione, come la selezione di una colonna o l'aggiunta di un filtro, restituirà una query al database.
* I riquadri vengono aggiornati ogni ora. L'aggiornamento non deve essere pianificato. È possibile regolare la frequenza di aggiornamento nelle impostazioni avanzate al momento della connessione.
* La funzione Domande e risposte non è disponibile per i set di dati di DirectQuery.
* Le modifiche allo schema non vengono selezionate automaticamente.

Queste restrizioni e note possono cambiare dal momento che le esperienze vengono costantemente migliorate. La procedura per la connessione è illustrata di seguito.

> [!Important]
> La connettività al database SQL di Azure è stata migliorata.  Per connettersi in modo ottimale all'origine dati del database SQL di Azure, usare Power BI Desktop.  Dopo aver compilato il modello e il report, è possibile pubblicarlo nel servizio Power BI.  Il connettore diretto per il database SQL di Azure nel servizio Power BI ora è deprecato.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop e DirectQuery

Per connettersi al database SQL di Azure tramite DirectQuery, è necessario usare Power BI Desktop. Questo approccio offre capacità e flessibilità aggiuntive. I report creati con Power BI Desktop potranno successivamente essere pubblicati nel servizio Power BI. Sono disponibili altre informazioni su come connettersi al [database SQL di Azure tramite DirectQuery](desktop-use-directquery.md) in Power BI Desktop.

## <a name="find-parameter-values"></a>Trovare i valori dei parametri

È possibile trovare il nome completo del server e il nome del database nel portale di Azure.

![Nuovo aggiornamento del portale di Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Aggiornamento del portale di Azure](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](../includes/direct-query-sso.md)]

## <a name="next-steps"></a>Passaggi successivi

* [Usare DirectQuery in Power BI Desktop](desktop-use-directquery.md)  
* [Che cos'è Power BI?](../fundamentals/power-bi-overview.md)  
* [Recuperare dati per Power BI](service-get-data.md)  

Altre domande? [Provare la community di Power BI](https://community.powerbi.com/)
