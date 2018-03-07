---
title: Database SQL di Azure con DirectQuery
description: Database SQL di Azure con DirectQuery
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 12/18/2017
ms.author: maghan
LocalizationGroup: Data from databases
ms.openlocfilehash: a32326c089c50ef4913f6d646d68d66e31efdbfc
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2018
---
# <a name="azure-sql-database-with-directquery"></a>Database SQL di Azure con DirectQuery
Informazioni su come connettersi direttamente al database SQL di Azure e creare report che usano dati in tempo reale. È possibile mantenere i dati nell'origine invece che in Power BI.

Con DirectQuery, le query vengono inviate nuovamente al database SQL di Azure durante l'esplorazione dei dati nella visualizzazione report. Si tratta di un'esperienza consigliata per gli utenti che hanno familiarità con i database e le entità cui si connettono.

**Note:**

* Specificare il nome completo del server durante la connessione (vedere di seguito per altri dettagli).
* Verificare che le regole del firewall per il database siano impostate su "[Consenti l'accesso a Servizi di Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx)"
* A ogni azione, come la selezione di una colonna o l'aggiunta di un filtro, verrà inviata una query al database.
* I riquadri vengono aggiornati ogni ora. L'aggiornamento non deve essere pianificato. È possibile regolare questo intervallo nelle impostazioni avanzate al momento della connessione.
* La funzione Domande e risposte non è disponibile per i set di dati di DirectQuery
* Le modifiche allo schema non vengono selezionate automaticamente

Queste restrizioni e note possono cambiare dal momento che le esperienze vengono costantemente migliorate. La procedura per la connessione è illustrata di seguito. 

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop e DirectQuery
Per connettersi al database SQL di Azure tramite DirectQuery, è necessario usare Power BI Desktop. Questo approccio offre capacità e flessibilità aggiuntive. I report creati con Power BI Desktop potranno successivamente essere pubblicati nel servizio Power BI. Sono disponibili altre informazioni su come connettersi al [database SQL di Azure tramite DirectQuery](desktop-use-directquery.md) in Power BI Desktop. 

## <a name="single-sign-on"></a>Accesso Single Sign-On

Dopo aver pubblicato un set di dati DirectQuery di Azure nel servizio, è possibile abilitare l'accesso Single Sign-On tramite OAuth2 in Azure Active Directory (Azure AD) per gli utenti finali. 

Per abilitare l'accesso Single Sign-On, passare alle impostazioni per il set di dati, aprire la scheda **Origini dati** e selezionare la casella SSO.

![Finestra di dialogo Configura Azure SQL DirectQuery](media/service-azure-sql-database-with-direct-connect/sso-dialog.png)

Quando l'opzione SSO è abilitata e gli utenti accedono ai report generati dall'origine dati, Power BI invia le relative credenziali di Azure AD autenticate nelle query al database SQL di Azure. Questo consente a Power BI di rispettare le impostazioni di sicurezza configurate al livello dell'origine dati.

L'opzione SSO interessa tutti i set di dati che usano l'origine dati specifica. Non interessa il metodo di autenticazione usato per gli scenari di importazione.

## <a name="finding-parameter-values"></a>Trovare i valori dei parametri
I nomi completi del server e del database sono disponibili nel portale di Azure.

![](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Passaggi successivi
[Usare DirectQuery in Power BI Desktop](desktop-use-directquery.md)  
[Introduzione a Power BI](service-get-started.md)  
[Recuperare dati per Power BI](service-get-data.md)  
Altre domande? [Provare la community di Power BI](http://community.powerbi.com/)
